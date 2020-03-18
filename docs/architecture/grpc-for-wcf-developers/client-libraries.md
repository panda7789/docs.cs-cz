---
title: Vytvoření klientských knihoven gRPC - gRPC pro vývojáře WCF
description: Diskuse o sdílených klientských knihovnách/balíčcích pro gRPC služby.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401667"
---
# <a name="create-grpc-client-libraries"></a>Vytvoření klientských knihoven gRPC

Není nutné distribuovat klientské knihovny pro gRPC aplikace. Můžete vytvořit sdílenou `.proto` knihovnu souborů v rámci organizace a ostatní týmy mohou tyto soubory použít ke generování kódu klienta ve svých vlastních projektech. Ale pokud máte privátní úložiště NuGet a mnoho dalších týmů používá .NET Core, můžete vytvořit a publikovat balíčky klienta NuGet jako součást vašeho projektu služeb. To může být dobrý způsob sdílení a propagace vašich služeb.

Jednou z výhod distribuce klientské knihovny je, že můžete vylepšit generované třídy gRPC a Protobuf pomocí užitečných "pohodlí" metod a vlastností. V kódu klienta, stejně jako na serveru, jsou všechny třídy deklarovány jako `partial`, takže je můžete rozšířit bez úprav generovaného kódu. To znamená, že je snadné přidat konstruktory, metody a vypočtené vlastnosti do základních typů.

> [!CAUTION]
> Vlastní kód byste neměli používat k zajištění základních funkcí. Nechcete omezit tuto základní funkci na týmy .NET, které používají sdílenou knihovnu, a neposkytovat ji týmům, které používají jiné jazyky nebo platformy, jako je například Python nebo Java.

Ujistěte se, že co nejvíce týmů má přístup ke službě gRPC. Nejlepší způsob, jak to `.proto` udělat, je sdílet soubory, aby vývojáři mohli vytvářet své vlastní klienty. To platí zejména v prostředí s více platformami, kde různé týmy často používají různé programovací jazyky a architektury nebo kde je vaše rozhraní API externě přístupné.

## <a name="useful-extensions"></a>Užitečná rozšíření

Existují dvě běžně používaná rozhraní v rozhraní .NET pro <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IObservable%601>práci s datovými proudy objektů: a . Počínaje .NET Core 3.0 a C# 8.0, je <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní pro zpracování datových `await foreach` proudů asynchronně a syntaxe pro použití rozhraní. Tato část představuje opakovaně použitelný kód pro použití těchto rozhraní na gRPC proudy.

S klientskými knihovnami .NET Core gRPC existuje `IAsyncStreamReader<T>` metoda `IAsyncEnumerable<T>` `ReadAllAsync` rozšíření, která vytvoří rozhraní. Pro vývojáře, kteří používají reaktivní programování, ekvivalentní metoda rozšíření k vytvoření `IObservable<T>` rozhraní může vypadat jako příklad v následující části.

### <a name="iobservable"></a>Iobservable

Rozhraní `IObservable<T>` je "reaktivní" inverzní . `IEnumerable<T>` Spíše než tahání položek z datového proudu, reaktivní přístup umožňuje datový proud nabízené položky odběratele. To je velmi podobné gRPC proudy, a je `IObservable<T>` snadné `IAsyncStreamReader<T>` zabalit rozhraní kolem rozhraní.

Tento kód je `IAsyncEnumerable<T>` delší než kód, protože C# nemá integrovanou podporu pro práci s pozorovatelné. Je nutné vytvořit třídu implementace ručně. Je to obecná třída, i když, takže jedna implementace funguje napříč všemi typy.

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public Observable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> Tato pozorovatelná implementace `Subscribe` umožňuje metodu volat pouze jednou, protože s více odběratelé se snaží číst z datového proudu by mělo za následek chaos. Existují operátory, `Replay` například v [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), které umožňují ukládání do vyrovnávací paměti a opakovatelné sdílení pozorovatelné, které lze použít s touto implementací.

Třída `GrpcStreamSubscription` zpracovává výčet `IAsyncStreamReader`:

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public Subscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

Vše, co je nyní vyžadováno, je jednoduchá metoda rozšíření k vytvoření pozorovatelné z čtečky datového proudu.

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a>Souhrn

Modely `IAsyncEnumerable` `IObservable` a jsou dobře podporované a dobře zdokumentované způsoby práce s asynchronními datovými proudy dat v rozhraní .NET. gRPC streamy mapovat dobře na obě paradigmata, nabízí úzkou integraci s .NET Core, a reaktivní a asynchronní programovací styly.

>[!div class="step-by-step"]
>[Předchozí](streaming-versus-repeated.md)
>[další](security.md)
