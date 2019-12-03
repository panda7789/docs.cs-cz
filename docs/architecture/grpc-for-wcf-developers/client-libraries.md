---
title: Vytváření klientských knihoven gRPC – gRPC pro vývojáře WCF
description: Diskuze za sdílené klientské knihovny/balíčky pro služby gRPC Services.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711460"
---
# <a name="create-grpc-client-libraries"></a>Vytváření klientských knihoven gRPC

Není nutné distribuovat klientské knihovny pro aplikaci gRPC. Můžete vytvořit sdílenou knihovnu `.proto` souborů v rámci vaší organizace a jiné týmy můžou tyto soubory použít k vygenerování kódu klienta ve svých vlastních projektech. Pokud ale máte soukromé úložiště NuGet a spousta dalších týmů používá .NET Core, můžete vytvořit a publikovat klientské balíčky NuGet jako součást projektu služby. To může být dobrý způsob, jak sdílet a propagovat vaši službu.

Jednou z výhod distribuce klientské knihovny je, že můžete vylepšit vygenerované třídy gRPC a Protobuf s využitím užitečných metod a vlastností "pohodlí". V klientském kódu, jako na serveru, jsou všechny třídy deklarovány jako `partial`, takže je můžete roztáhnout bez úprav generovaného kódu. To znamená, že je snadné přidat konstruktory, metody a počítané vlastnosti do základních typů.

> [!CAUTION]
> Nepoužívejte vlastní kód k poskytování základních funkcí. Nechcete omezit tyto základní funkce na týmy .NET, které používají sdílenou knihovnu, a Neposkytněte je týmům, které používají jiné jazyky nebo platformy, jako je Python nebo Java.

Zajistěte, aby ke službě gRPC mohli přistupovat co nejvíce týmů. Nejlepším způsobem, jak to provést, je sdílet soubory `.proto`, aby vývojáři mohli vygenerovat své vlastní klienty. To platí zejména v prostředí s více platformami, kde různé týmy často používají různé programovací jazyky a architektury nebo kde je vaše rozhraní API externě přístupné.

## <a name="useful-extensions"></a>Užitečná rozšíření

V rozhraní .NET existují dvě běžně používaná rozhraní pro práci s datovými proudy objektů: <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IObservable%601>. Počínaje .NET Core 3,0 a C# 8,0 je k dispozici <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní pro asynchronní zpracování datových proudů a syntaxi `await foreach` pro použití rozhraní. V této části najdete opakovaně použitelný kód pro použití těchto rozhraní pro gRPC streamy.

S klientskými knihovnami .NET Core gRPC existuje metoda rozšíření `ReadAllAsync` pro `IAsyncStreamReader<T>`, která vytvoří rozhraní `IAsyncEnumerable<T>`. Pro vývojáře, kteří používají reaktivní programování, může ekvivalentní metoda rozšíření vytvořit `IObservable<T>` rozhraní vypadat jako v příkladu v následující části.

### <a name="iobservable"></a>IObservable

Rozhraní `IObservable<T>` je "reaktivní" inverzní `IEnumerable<T>`. Místo přijímání položek z datového proudu umožňuje reaktivní přístup streamování nabízených položek odběrateli. To je velmi podobné datovým proudům gRPC a je snadné zabalit `IObservable<T>` rozhraní kolem `IAsyncStreamReader<T>`ho rozhraní.

Tento kód je delší než `IAsyncEnumerable<T>` kód, protože C# nemá integrovanou podporu pro práci s observables. Je nutné vytvořit třídu implementace ručně. Je to ale obecná třída, takže jediná implementace funguje napříč všemi typy.

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
> Tato možná implementace umožňuje, aby byla metoda `Subscribe` volána pouze jednou, protože více odběratelů, kteří se pokoušejí o čtení z datového proudu, by způsobilo chaos. Existují operátory, například `Replay` v [System. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq), které umožňují ukládání do vyrovnávací paměti a opakované sdílení observables, které lze použít s touto implementací.

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

Vše, co je potřeba, je teď jednoduchá rozšiřující metoda, která umožňuje vytvořit pozorovatelnou z čtecího modulu streamu.

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

## <a name="summary"></a>Přehled

Modely `IAsyncEnumerable` a `IObservable` jsou dobře podporované a dobře dokumentované způsoby práce s asynchronními datovými proudy dat v rozhraní .NET. gRPC datové proudy se dobře mapují na oba paradigma, nabízí těsnou integraci s .NET Core a reaktivním a asynchronním programováním stylů.

>[!div class="step-by-step"]
>[Předchozí](streaming-versus-repeated.md)
>[Další](security.md)
