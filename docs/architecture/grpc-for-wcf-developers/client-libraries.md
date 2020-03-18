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
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="30733-103">Vytvoření klientských knihoven gRPC</span><span class="sxs-lookup"><span data-stu-id="30733-103">Create gRPC client libraries</span></span>

<span data-ttu-id="30733-104">Není nutné distribuovat klientské knihovny pro gRPC aplikace.</span><span class="sxs-lookup"><span data-stu-id="30733-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="30733-105">Můžete vytvořit sdílenou `.proto` knihovnu souborů v rámci organizace a ostatní týmy mohou tyto soubory použít ke generování kódu klienta ve svých vlastních projektech.</span><span class="sxs-lookup"><span data-stu-id="30733-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="30733-106">Ale pokud máte privátní úložiště NuGet a mnoho dalších týmů používá .NET Core, můžete vytvořit a publikovat balíčky klienta NuGet jako součást vašeho projektu služeb.</span><span class="sxs-lookup"><span data-stu-id="30733-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="30733-107">To může být dobrý způsob sdílení a propagace vašich služeb.</span><span class="sxs-lookup"><span data-stu-id="30733-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="30733-108">Jednou z výhod distribuce klientské knihovny je, že můžete vylepšit generované třídy gRPC a Protobuf pomocí užitečných "pohodlí" metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="30733-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="30733-109">V kódu klienta, stejně jako na serveru, jsou všechny třídy deklarovány jako `partial`, takže je můžete rozšířit bez úprav generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="30733-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="30733-110">To znamená, že je snadné přidat konstruktory, metody a vypočtené vlastnosti do základních typů.</span><span class="sxs-lookup"><span data-stu-id="30733-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="30733-111">Vlastní kód byste neměli používat k zajištění základních funkcí.</span><span class="sxs-lookup"><span data-stu-id="30733-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="30733-112">Nechcete omezit tuto základní funkci na týmy .NET, které používají sdílenou knihovnu, a neposkytovat ji týmům, které používají jiné jazyky nebo platformy, jako je například Python nebo Java.</span><span class="sxs-lookup"><span data-stu-id="30733-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="30733-113">Ujistěte se, že co nejvíce týmů má přístup ke službě gRPC.</span><span class="sxs-lookup"><span data-stu-id="30733-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="30733-114">Nejlepší způsob, jak to `.proto` udělat, je sdílet soubory, aby vývojáři mohli vytvářet své vlastní klienty.</span><span class="sxs-lookup"><span data-stu-id="30733-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="30733-115">To platí zejména v prostředí s více platformami, kde různé týmy často používají různé programovací jazyky a architektury nebo kde je vaše rozhraní API externě přístupné.</span><span class="sxs-lookup"><span data-stu-id="30733-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="30733-116">Užitečná rozšíření</span><span class="sxs-lookup"><span data-stu-id="30733-116">Useful extensions</span></span>

<span data-ttu-id="30733-117">Existují dvě běžně používaná rozhraní v rozhraní .NET pro <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IObservable%601>práci s datovými proudy objektů: a .</span><span class="sxs-lookup"><span data-stu-id="30733-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="30733-118">Počínaje .NET Core 3.0 a C# 8.0, je <xref:System.Collections.Generic.IAsyncEnumerable%601> rozhraní pro zpracování datových `await foreach` proudů asynchronně a syntaxe pro použití rozhraní.</span><span class="sxs-lookup"><span data-stu-id="30733-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="30733-119">Tato část představuje opakovaně použitelný kód pro použití těchto rozhraní na gRPC proudy.</span><span class="sxs-lookup"><span data-stu-id="30733-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="30733-120">S klientskými knihovnami .NET Core gRPC existuje `IAsyncStreamReader<T>` metoda `IAsyncEnumerable<T>` `ReadAllAsync` rozšíření, která vytvoří rozhraní.</span><span class="sxs-lookup"><span data-stu-id="30733-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="30733-121">Pro vývojáře, kteří používají reaktivní programování, ekvivalentní metoda rozšíření k vytvoření `IObservable<T>` rozhraní může vypadat jako příklad v následující části.</span><span class="sxs-lookup"><span data-stu-id="30733-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="30733-122">Iobservable</span><span class="sxs-lookup"><span data-stu-id="30733-122">IObservable</span></span>

<span data-ttu-id="30733-123">Rozhraní `IObservable<T>` je "reaktivní" inverzní . `IEnumerable<T>`</span><span class="sxs-lookup"><span data-stu-id="30733-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="30733-124">Spíše než tahání položek z datového proudu, reaktivní přístup umožňuje datový proud nabízené položky odběratele.</span><span class="sxs-lookup"><span data-stu-id="30733-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="30733-125">To je velmi podobné gRPC proudy, a je `IObservable<T>` snadné `IAsyncStreamReader<T>` zabalit rozhraní kolem rozhraní.</span><span class="sxs-lookup"><span data-stu-id="30733-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="30733-126">Tento kód je `IAsyncEnumerable<T>` delší než kód, protože C# nemá integrovanou podporu pro práci s pozorovatelné.</span><span class="sxs-lookup"><span data-stu-id="30733-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="30733-127">Je nutné vytvořit třídu implementace ručně.</span><span class="sxs-lookup"><span data-stu-id="30733-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="30733-128">Je to obecná třída, i když, takže jedna implementace funguje napříč všemi typy.</span><span class="sxs-lookup"><span data-stu-id="30733-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="30733-129">Tato pozorovatelná implementace `Subscribe` umožňuje metodu volat pouze jednou, protože s více odběratelé se snaží číst z datového proudu by mělo za následek chaos.</span><span class="sxs-lookup"><span data-stu-id="30733-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="30733-130">Existují operátory, `Replay` například v [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), které umožňují ukládání do vyrovnávací paměti a opakovatelné sdílení pozorovatelné, které lze použít s touto implementací.</span><span class="sxs-lookup"><span data-stu-id="30733-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="30733-131">Třída `GrpcStreamSubscription` zpracovává výčet `IAsyncStreamReader`:</span><span class="sxs-lookup"><span data-stu-id="30733-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="30733-132">Vše, co je nyní vyžadováno, je jednoduchá metoda rozšíření k vytvoření pozorovatelné z čtečky datového proudu.</span><span class="sxs-lookup"><span data-stu-id="30733-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="30733-133">Souhrn</span><span class="sxs-lookup"><span data-stu-id="30733-133">Summary</span></span>

<span data-ttu-id="30733-134">Modely `IAsyncEnumerable` `IObservable` a jsou dobře podporované a dobře zdokumentované způsoby práce s asynchronními datovými proudy dat v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="30733-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="30733-135">gRPC streamy mapovat dobře na obě paradigmata, nabízí úzkou integraci s .NET Core, a reaktivní a asynchronní programovací styly.</span><span class="sxs-lookup"><span data-stu-id="30733-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="30733-136">[Předchozí](streaming-versus-repeated.md)
>[další](security.md)</span><span class="sxs-lookup"><span data-stu-id="30733-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
