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
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="b3f46-103">Vytváření klientských knihoven gRPC</span><span class="sxs-lookup"><span data-stu-id="b3f46-103">Create gRPC client libraries</span></span>

<span data-ttu-id="b3f46-104">Není nutné distribuovat klientské knihovny pro aplikaci gRPC.</span><span class="sxs-lookup"><span data-stu-id="b3f46-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="b3f46-105">Můžete vytvořit sdílenou knihovnu `.proto` souborů v rámci vaší organizace a jiné týmy můžou tyto soubory použít k vygenerování kódu klienta ve svých vlastních projektech.</span><span class="sxs-lookup"><span data-stu-id="b3f46-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="b3f46-106">Pokud ale máte soukromé úložiště NuGet a spousta dalších týmů používá .NET Core, můžete vytvořit a publikovat klientské balíčky NuGet jako součást projektu služby.</span><span class="sxs-lookup"><span data-stu-id="b3f46-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="b3f46-107">To může být dobrý způsob, jak sdílet a propagovat vaši službu.</span><span class="sxs-lookup"><span data-stu-id="b3f46-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="b3f46-108">Jednou z výhod distribuce klientské knihovny je, že můžete vylepšit vygenerované třídy gRPC a Protobuf s využitím užitečných metod a vlastností "pohodlí".</span><span class="sxs-lookup"><span data-stu-id="b3f46-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="b3f46-109">V klientském kódu, jako na serveru, jsou všechny třídy deklarovány jako `partial`, takže je můžete roztáhnout bez úprav generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b3f46-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="b3f46-110">To znamená, že je snadné přidat konstruktory, metody a počítané vlastnosti do základních typů.</span><span class="sxs-lookup"><span data-stu-id="b3f46-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="b3f46-111">Nepoužívejte vlastní kód k poskytování základních funkcí.</span><span class="sxs-lookup"><span data-stu-id="b3f46-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="b3f46-112">Nechcete omezit tyto základní funkce na týmy .NET, které používají sdílenou knihovnu, a Neposkytněte je týmům, které používají jiné jazyky nebo platformy, jako je Python nebo Java.</span><span class="sxs-lookup"><span data-stu-id="b3f46-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="b3f46-113">Zajistěte, aby ke službě gRPC mohli přistupovat co nejvíce týmů.</span><span class="sxs-lookup"><span data-stu-id="b3f46-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="b3f46-114">Nejlepším způsobem, jak to provést, je sdílet soubory `.proto`, aby vývojáři mohli vygenerovat své vlastní klienty.</span><span class="sxs-lookup"><span data-stu-id="b3f46-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="b3f46-115">To platí zejména v prostředí s více platformami, kde různé týmy často používají různé programovací jazyky a architektury nebo kde je vaše rozhraní API externě přístupné.</span><span class="sxs-lookup"><span data-stu-id="b3f46-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="b3f46-116">Užitečná rozšíření</span><span class="sxs-lookup"><span data-stu-id="b3f46-116">Useful extensions</span></span>

<span data-ttu-id="b3f46-117">V rozhraní .NET existují dvě běžně používaná rozhraní pro práci s datovými proudy objektů: <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IObservable%601>.</span><span class="sxs-lookup"><span data-stu-id="b3f46-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="b3f46-118">Počínaje .NET Core 3,0 a C# 8,0 je k dispozici <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní pro asynchronní zpracování datových proudů a syntaxi `await foreach` pro použití rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3f46-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="b3f46-119">V této části najdete opakovaně použitelný kód pro použití těchto rozhraní pro gRPC streamy.</span><span class="sxs-lookup"><span data-stu-id="b3f46-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="b3f46-120">S klientskými knihovnami .NET Core gRPC existuje metoda rozšíření `ReadAllAsync` pro `IAsyncStreamReader<T>`, která vytvoří rozhraní `IAsyncEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="b3f46-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="b3f46-121">Pro vývojáře, kteří používají reaktivní programování, může ekvivalentní metoda rozšíření vytvořit `IObservable<T>` rozhraní vypadat jako v příkladu v následující části.</span><span class="sxs-lookup"><span data-stu-id="b3f46-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="b3f46-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="b3f46-122">IObservable</span></span>

<span data-ttu-id="b3f46-123">Rozhraní `IObservable<T>` je "reaktivní" inverzní `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="b3f46-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="b3f46-124">Místo přijímání položek z datového proudu umožňuje reaktivní přístup streamování nabízených položek odběrateli.</span><span class="sxs-lookup"><span data-stu-id="b3f46-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="b3f46-125">To je velmi podobné datovým proudům gRPC a je snadné zabalit `IObservable<T>` rozhraní kolem `IAsyncStreamReader<T>`ho rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3f46-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="b3f46-126">Tento kód je delší než `IAsyncEnumerable<T>` kód, protože C# nemá integrovanou podporu pro práci s observables.</span><span class="sxs-lookup"><span data-stu-id="b3f46-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="b3f46-127">Je nutné vytvořit třídu implementace ručně.</span><span class="sxs-lookup"><span data-stu-id="b3f46-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="b3f46-128">Je to ale obecná třída, takže jediná implementace funguje napříč všemi typy.</span><span class="sxs-lookup"><span data-stu-id="b3f46-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="b3f46-129">Tato možná implementace umožňuje, aby byla metoda `Subscribe` volána pouze jednou, protože více odběratelů, kteří se pokoušejí o čtení z datového proudu, by způsobilo chaos.</span><span class="sxs-lookup"><span data-stu-id="b3f46-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="b3f46-130">Existují operátory, například `Replay` v [System. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq), které umožňují ukládání do vyrovnávací paměti a opakované sdílení observables, které lze použít s touto implementací.</span><span class="sxs-lookup"><span data-stu-id="b3f46-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="b3f46-131">Třída `GrpcStreamSubscription` zpracovává výčet `IAsyncStreamReader`:</span><span class="sxs-lookup"><span data-stu-id="b3f46-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="b3f46-132">Vše, co je potřeba, je teď jednoduchá rozšiřující metoda, která umožňuje vytvořit pozorovatelnou z čtecího modulu streamu.</span><span class="sxs-lookup"><span data-stu-id="b3f46-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="b3f46-133">Přehled</span><span class="sxs-lookup"><span data-stu-id="b3f46-133">Summary</span></span>

<span data-ttu-id="b3f46-134">Modely `IAsyncEnumerable` a `IObservable` jsou dobře podporované a dobře dokumentované způsoby práce s asynchronními datovými proudy dat v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="b3f46-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="b3f46-135">gRPC datové proudy se dobře mapují na oba paradigma, nabízí těsnou integraci s .NET Core a reaktivním a asynchronním programováním stylů.</span><span class="sxs-lookup"><span data-stu-id="b3f46-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b3f46-136">[Předchozí](streaming-versus-repeated.md)
>[Další](security.md)</span><span class="sxs-lookup"><span data-stu-id="b3f46-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
