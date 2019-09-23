---
title: Vytváření klientských knihoven gRPC – gRPC pro vývojáře WCF
description: Diskuze za sdílené klientské knihovny/balíčky pro služby gRPC Services.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 44a749c888528ca244f41b5b88354d7ed1db4190
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184587"
---
# <a name="create-grpc-client-libraries"></a>Vytváření klientských knihoven gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Není nutné distribuovat klientské knihovny pro aplikaci gPRC. Můžete vytvořit sdílenou knihovnu `.proto` souborů v rámci vaší organizace a jiné týmy můžou tyto soubory použít k vygenerování kódu klienta ve svých vlastních projektech. Pokud ale máte soukromé úložiště NuGet a spousta dalších týmů používá .NET Core, vytváření a publikování balíčků NuGet klienta jako součást projektu služby může být dobrým způsobem, jak sdílet a propagovat vaši službu.

Jednou z výhod distribuce klientské knihovny je, že můžete vylepšit vygenerované třídy gRPC a Protobuf s využitím užitečných metod a vlastností "pohodlí". V klientském kódu, jako na serveru, jsou deklarovány všechny třídy, jako `partial` by je bylo možné roztáhnout bez úprav generovaného kódu. To znamená, že je snadné přidat konstruktory, metody, počítané vlastnosti a další základní typy.

> [!CAUTION]
> **Neměli byste používat vlastní** kód pro poskytování základních funkcí, protože by to znamenalo, že by byla funkce omezena na týmy .NET pomocí sdílené knihovny, a ne pro týmy, které používají jiné jazyky nebo platformy, jako je Python nebo Java.

V prostředí s více platformami, kde různé týmy často používají různé programovací jazyky a rozhraní nebo kde je vaše rozhraní API externě přístupné, stačí sdílet `.proto` soubory, aby vývojáři mohli vygenerovat své vlastní klienty, je nejlepším způsobem, jak Ujistěte se, že máte přístup ke službě gRPC, abyste měli k dispozici co nejvíce týmů.

## <a name="useful-extensions"></a>Užitečná rozšíření

V rozhraní .NET existují dvě běžně používaná rozhraní pro práci s datovými proudy objektů <xref:System.Collections.Generic.IEnumerable%601> : <xref:System.IObservable%601>a. Počínaje .NET Core 3,0 a C# 8,0 je k dispozici <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní pro asynchronní zpracování datových proudů a `await foreach` syntaxi pro použití rozhraní. V této části najdete opakovaně použitelný kód pro použití těchto rozhraní pro gRPC streamy.

S klientskými knihovnami .NET Core gRPC existuje `ReadAllAsync` metoda rozšíření pro `IAsyncStreamReader<T>` , která vytvoří `IAsyncEnumerable<T>`. Pro vývojáře, kteří používají reaktivní programování, `IObservable<T>` může to vypadat stejně jako metoda rozšíření, která by mohla vypadat.

### <a name="iobservable"></a>IObservable

Rozhraní je "reaktivní" `IEnumerable<T>`inverzní. `IObservable<T>` Místo přijímání položek z datového proudu umožňuje reaktivní přístup streamování nabízených položek odběrateli. To je velmi podobné datovým proudům gRPC a snadno se zalomí `IObservable<T>` `IAsyncStreamReader<T>`kolem.

Tento kód je delší než `IAsyncEnumerable<T>` kód, protože C# nemá integrovanou podporu pro práci s observables, takže třídu implementace je třeba vytvořit ručně. Je to ale obecná třída, takže jediná implementace bude fungovat napříč všemi typy.

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
> Tato možná implementace umožňuje `Subscribe` pouze volání metody pouze jednou, protože více odběratelů, kteří se pokoušejí o čtení z datového proudu, by způsobilo chaos. Existují operátory, jako je `Replay` například v [System. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq) , které umožňují ukládání do vyrovnávací paměti a opakované sdílení observables, které lze použít s touto implementací.

Třída zpracovává výčet `IAsyncStreamReader`. `GrpcStreamSubscription`

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

## <a name="summary"></a>Souhrn

Modely `IAsyncEnumerable` a`IObservable` jsou dobře podporované a dobře dokumentované způsoby práce s asynchronními datovými proudy dat v rozhraní .NET. gRPC datové proudy jsou dobře namapované na obě paradigma, nabízí těsnou integraci s moderními rozhraními .NET Core a reaktivními nebo asynchronními programovacími styly.

>[!div class="step-by-step"]
>[Předchozí](streaming-versus-repeated.md)
>[Další](security.md)
