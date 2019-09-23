---
title: Migrace duplexních služeb WCF na gRPC-gRPC pro vývojáře WCF
description: Naučte se migrovat různé formy duplexní služby WCF na služby gRPC streaming.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 06ac784a31df43fd270f7ef0475bcdc282efad8f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184335"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="ec40c-103">Migrace duplexních služeb WCF na gRPC</span><span class="sxs-lookup"><span data-stu-id="ec40c-103">Migrate WCF duplex services to gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ec40c-104">Teď, když jsou na začátku základní koncepty, Tato část se bude pohlížet na složitější *streamování* gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="ec40c-104">Now that the basic concepts are in place, this section will look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="ec40c-105">V Windows Communication Foundation (WCF) existuje několik způsobů použití duplexních služeb.</span><span class="sxs-lookup"><span data-stu-id="ec40c-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ec40c-106">Některé služby jsou iniciovány klientem a poté jsou z tohoto serveru streamovaná data.</span><span class="sxs-lookup"><span data-stu-id="ec40c-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="ec40c-107">Jiné plně duplexní služby můžou v dokumentaci WCF zahrnovat nepřetržitou obousměrnou komunikaci, například klasický příklad kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="ec40c-107">Other full-duplex services might involve more ongoing two-way communication like the classic "Calculator" example from the WCF documentation.</span></span> <span data-ttu-id="ec40c-108">Tato kapitola bude mít dvě možné implementace služby WCF "burzovních impulsů" a migruje je do gRPC: jedno pomocí služby RPC pro streamování serveru a druhý pomocí protokolu RPC s obousměrným datovým proudem.</span><span class="sxs-lookup"><span data-stu-id="ec40c-108">This chapter will take two possible WCF "Stock Ticker" implementations and migrate them to gRPC: one using a server streaming RPC, and the other one using a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="ec40c-109">RPC streamování serveru</span><span class="sxs-lookup"><span data-stu-id="ec40c-109">Server streaming RPC</span></span>

<span data-ttu-id="ec40c-110">V [ukázkovém řešení SIMPLESTOCKTICKER WCF](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)je *SimpleStockPriceTicker*duplexní služba, kde klient spouští připojení se seznamem burzovních symbolů a server používá *rozhraní zpětného volání* k posílání aktualizací. bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ec40c-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), *SimpleStockPriceTicker*, there's a duplex service where the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="ec40c-111">Klient implementuje rozhraní, aby reagoval na volání ze serveru.</span><span class="sxs-lookup"><span data-stu-id="ec40c-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="ec40c-112">Řešení WCF</span><span class="sxs-lookup"><span data-stu-id="ec40c-112">The WCF solution</span></span>

<span data-ttu-id="ec40c-113">Řešení WCF je implementováno jako server NetTCP v místním prostředí v konzolové aplikaci .NET Framework 4. x.</span><span class="sxs-lookup"><span data-stu-id="ec40c-113">The WCF solution is implemented as a self-hosted NetTCP server in a .NET Framework 4.x console application.</span></span>

#### <a name="the-servicecontract"></a><span data-ttu-id="ec40c-114">Třída ServiceContract</span><span class="sxs-lookup"><span data-stu-id="ec40c-114">The ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="ec40c-115">Služba má jedinou metodu bez návratového typu, protože bude používat rozhraní `ISimpleStockTickerCallback` zpětného volání k posílání dat klientovi v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="ec40c-115">The service has a single method with no return type, because it will be using the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="ec40c-116">Rozhraní zpětného volání</span><span class="sxs-lookup"><span data-stu-id="ec40c-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="ec40c-117">Implementace těchto rozhraní se dají najít v řešení společně s falešným externími závislostmi k poskytnutí testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="ec40c-117">The implementations of these interfaces can be found in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="ec40c-118">streamování gRPC</span><span class="sxs-lookup"><span data-stu-id="ec40c-118">gRPC streaming</span></span>

<span data-ttu-id="ec40c-119">GRPC způsob zpracování dat v reálném čase se liší.</span><span class="sxs-lookup"><span data-stu-id="ec40c-119">The gRPC way of handling real-time data is different.</span></span> <span data-ttu-id="ec40c-120">Volání z klienta na server může vytvořit trvalý datový proud, který lze monitorovat pro zprávy přicházející asynchronně.</span><span class="sxs-lookup"><span data-stu-id="ec40c-120">A call from client to server can create a persistent stream, which can be monitored for messages arriving asynchronously.</span></span> <span data-ttu-id="ec40c-121">Navzdory rozdílům může být datový proud intuitivnější způsob, jak se s těmito daty pracovat a které jsou důležitější při moderním programování s důrazem na LINQ, reaktivní streamy, funkční programování atd.</span><span class="sxs-lookup"><span data-stu-id="ec40c-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming with the emphasis on LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="ec40c-122">Definice služby potřebuje dvě zprávy: jednu pro požadavek a jednu pro datový proud.</span><span class="sxs-lookup"><span data-stu-id="ec40c-122">The service definition needs two messages: one for the request, and one for the stream.</span></span> <span data-ttu-id="ec40c-123">Služba vrátí datový proud `StockTickerUpdate` zprávy `stream` pomocí klíčového slova ve své `return` deklaraci.</span><span class="sxs-lookup"><span data-stu-id="ec40c-123">The service returns a stream of the `StockTickerUpdate` message using the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="ec40c-124">Doporučuje se přidat `Timestamp` do aktualizace, abyste zobrazili přesný čas změny ceny.</span><span class="sxs-lookup"><span data-stu-id="ec40c-124">It's recommended that you add a `Timestamp` to the update to show the exact time the price changed.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="ec40c-125">simple_stock_ticker.</span><span class="sxs-lookup"><span data-stu-id="ec40c-125">simple_stock_ticker.proto</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 priceCents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-the-simplestockticker"></a><span data-ttu-id="ec40c-126">Implementace rozhraní SimpleStockTicker</span><span class="sxs-lookup"><span data-stu-id="ec40c-126">Implement the SimpleStockTicker</span></span>

<span data-ttu-id="ec40c-127">Znovu použijte napodobeninu `StockPriceSubscriber` z projektu WCF zkopírováním tří tříd `TraderSys.StockMarket` z knihovny tříd do nové knihovny tříd .NET Standard v cílovém řešení.</span><span class="sxs-lookup"><span data-stu-id="ec40c-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="ec40c-128">Chcete-li lépe dodržovat osvědčené postupy `Factory` , přidejte typ pro vytvoření instancí a `IStockPriceSubscriberFactory` Zaregistrujte se službou pro vkládání závislostí ve ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ec40c-128">To better follow best practices, add a `Factory` type to create instances of it and register the `IStockPriceSubscriberFactory` with ASP.NET Core's dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="ec40c-129">Implementace továrny</span><span class="sxs-lookup"><span data-stu-id="ec40c-129">The factory implementation</span></span>

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="registering-the-factory"></a><span data-ttu-id="ec40c-130">Registrace továrny</span><span class="sxs-lookup"><span data-stu-id="ec40c-130">Registering the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="ec40c-131">Nyní lze tuto třídu použít k implementaci služby gRPC StockTicker.</span><span class="sxs-lookup"><span data-stu-id="ec40c-131">Now, this class can be used to implement the gRPC StockTicker service.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="ec40c-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="ec40c-132">StockTickerService.cs</span></span>

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors due to broken connection etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

<span data-ttu-id="ec40c-133">Jak vidíte, i když deklarace v `.proto` souboru říká, že metoda vrátí `StockTickerUpdate` datový proud zpráv, ve skutečnosti vrátí Vanilla `Task`.</span><span class="sxs-lookup"><span data-stu-id="ec40c-133">As you can see, although the declaration in the `.proto` file says the method "returns" a stream of `StockTickerUpdate` messages, in fact it returns a vanilla `Task`.</span></span> <span data-ttu-id="ec40c-134">Úloha vytvoření datového proudu je zpracována generovaným kódem a běhovými knihovnami gRPC, které poskytují `IServerStreamWriter<StockTickerUpdate>` datový proud odpovědí připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="ec40c-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="ec40c-135">Na rozdíl od služby duplexní služba WCF, kde je instance třídy služby aktivní, když je připojení otevřené, služba gRPC použije vrácenou úlohu, aby službu udržovala aktivní.</span><span class="sxs-lookup"><span data-stu-id="ec40c-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned Task to keep the service alive.</span></span> <span data-ttu-id="ec40c-136">Úloha by neměla být dokončena, dokud nebude připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="ec40c-136">The Task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="ec40c-137">Služba může říct, že klient uzavřel připojení pomocí `CancellationToken` `ServerCallContext`z.</span><span class="sxs-lookup"><span data-stu-id="ec40c-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="ec40c-138">Jednoduchá statická metoda, `AwaitCancellation`která se používá k vytvoření úlohy, která se dokončí při zrušení tokenu.</span><span class="sxs-lookup"><span data-stu-id="ec40c-138">A simple static method, `AwaitCancellation`, is used to create a Task that completes when the token is canceled.</span></span>

<span data-ttu-id="ec40c-139">V metodě, potom Get a přidejte obslužnou rutinu události, která zapisuje do datového proudu odpovědí. `StockPriceSubscriber` `Subscribe`</span><span class="sxs-lookup"><span data-stu-id="ec40c-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="ec40c-140">Pak počkejte, než se připojení zavře, a teprve `subscriber` potom ho vyodstraňte, aby nedošlo k pokusu o zápis dat do zavřeného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="ec40c-140">Then wait for the connection to be closed, before immediately disposing the `subscriber` to prevent it trying to write data to the closed stream.</span></span>

<span data-ttu-id="ec40c-141">`WriteUpdateAsync` Metoda máblok,který`try` zpracovává všechny chyby, ke kterým může dojít při zápisu zprávy do datového proudu. / `catch`</span><span class="sxs-lookup"><span data-stu-id="ec40c-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when writing a message to the stream.</span></span> <span data-ttu-id="ec40c-142">To je důležitý aspekt trvalého připojení přes sítě, které by mohlo být v jakémkoli milisekundě přerušeno, ať už úmyslně nebo z důvodu selhání.</span><span class="sxs-lookup"><span data-stu-id="ec40c-142">This is an important consideration in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="using-the-stocktickerservice-from-a-client-application"></a><span data-ttu-id="ec40c-143">Použití rozhraní StockTickerService z klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="ec40c-143">Using the StockTickerService from a client application</span></span>

<span data-ttu-id="ec40c-144">Použijte stejný postup v předchozí části a vytvořte ze `.proto` souboru knihovnu klientských tříd sdílení.</span><span class="sxs-lookup"><span data-stu-id="ec40c-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="ec40c-145">V ukázce je k dispozici Konzolová aplikace .NET Core 3,0, která ukazuje, jak používat klienta.</span><span class="sxs-lookup"><span data-stu-id="ec40c-145">In the sample, there's a .NET Core 3.0 console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="ec40c-146">Příklad Program.cs</span><span class="sxs-lookup"><span data-stu-id="ec40c-146">Example Program.cs</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

<span data-ttu-id="ec40c-147">V tomto případě `Subscribe` není metoda na vygenerovaném klientovi asynchronní.</span><span class="sxs-lookup"><span data-stu-id="ec40c-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="ec40c-148">Stream se vytvoří a dá se použít hned, protože jeho `MoveNext` metoda je asynchronní a při prvním volání se nebudete moct dokončit, dokud připojení není aktivní.</span><span class="sxs-lookup"><span data-stu-id="ec40c-148">The stream is created and usable right away, because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="ec40c-149">Datový proud se předává asynchronní `DisplayAsync` metodě. aplikace pak počká, až uživatel stiskne klávesu, a pak tuto `DisplayAsync` metodu zruší a před ukončením počká, než se úkol dokončí.</span><span class="sxs-lookup"><span data-stu-id="ec40c-149">The stream is passed to an async `DisplayAsync` method; the application then waits for the user to press a key, then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="ec40c-150">Tento kód používá novou C# syntaxi 8 "using Declaration" k Dispose datového proudu a kanálu při `Main` ukončení metody.</span><span class="sxs-lookup"><span data-stu-id="ec40c-150">This code is using the new C# 8 "using declaration" syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="ec40c-151">Jedná se o malou změnu, ale je to dobrý čas, který omezí odsazení a prázdné řádky.</span><span class="sxs-lookup"><span data-stu-id="ec40c-151">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="ec40c-152">Využití streamu</span><span class="sxs-lookup"><span data-stu-id="ec40c-152">Consume the stream</span></span>

<span data-ttu-id="ec40c-153">WCF používá rozhraní zpětného volání, aby mohl server volat metody přímo na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="ec40c-153">WCF used callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="ec40c-154">datové proudy gRPC fungují jinak.</span><span class="sxs-lookup"><span data-stu-id="ec40c-154">gRPC streams work differently.</span></span> <span data-ttu-id="ec40c-155">Klient prochází vráceným datovým proudem a zpracovává zprávy stejným způsobem, jako kdyby byly vráceny z místní metody vracející `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="ec40c-155">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="ec40c-156">Typ funguje `MoveNext` podobně jako `Current` : existuje metoda, která vrátí hodnotu true, dokud bude existovat více dat, a vlastnost, která vrací nejnovější hodnotu. `IEnumerator<T>` `IAsyncStreamReader<T>`</span><span class="sxs-lookup"><span data-stu-id="ec40c-156">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`: there's a `MoveNext` method that will return true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="ec40c-157">Jediným rozdílem je, že `MoveNext` metoda `Task<bool>` vrací místo pouze a `bool`.</span><span class="sxs-lookup"><span data-stu-id="ec40c-157">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="ec40c-158">Metoda rozšíření zalomí datový proud C# ve standardu 8 `IAsyncEnumerable` , který lze použít s novou `await foreach` syntaxí. `ReadAllAsync`</span><span class="sxs-lookup"><span data-stu-id="ec40c-158">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> <span data-ttu-id="ec40c-159">Oddíl na [klientských knihovnách](client-libraries.md#iobservable) na konci této kapitoly vyhledá, jak přidat rozšiřující metodu a třídy, které se zabalí `IAsyncStreamReader<T>` do `IObservable<T>` pro vývojáře pomocí reaktivních programovacích vzorů.</span><span class="sxs-lookup"><span data-stu-id="ec40c-159">The section on [client libraries](client-libraries.md#iobservable) at the end of this chapter looks at how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>` for developers using reactive programming patterns.</span></span>

<span data-ttu-id="ec40c-160">Znovu buďte opatrní, abyste zachytili výjimky z důvodu možnosti selhání sítě a také <xref:System.OperationCanceledException> to, že bude nevyhnutelně vyvoláno, protože kód <xref:System.Threading.CancellationToken> používá k přerušení smyčky.</span><span class="sxs-lookup"><span data-stu-id="ec40c-160">Again, be careful to catch exceptions here because of the possibility of network failure, as well as the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="ec40c-161">Typ má spoustu užitečných informací o chybách modulu runtime gRPC, `StatusCode`včetně. `RpcException`</span><span class="sxs-lookup"><span data-stu-id="ec40c-161">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="ec40c-162">Další informace najdete v části [ *zpracování chyb* v části 4.](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="ec40c-162">For more information, see [*Error handling* in Chapter 4](error-handling.md)</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="ec40c-163">Obousměrný streamování</span><span class="sxs-lookup"><span data-stu-id="ec40c-163">Bidirectional streaming</span></span>

<span data-ttu-id="ec40c-164">Plně duplexní služba WCF umožňuje asynchronní zasílání zpráv v reálném čase v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="ec40c-164">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="ec40c-165">V příkladu streamování serveru spustí klient požadavek a potom obdrží datový proud aktualizací.</span><span class="sxs-lookup"><span data-stu-id="ec40c-165">In the server streaming example, the client starts a request, then receives a stream of updates.</span></span> <span data-ttu-id="ec40c-166">Lepší verze této služby umožňuje klientovi přidávat a odebírat zásoby ze seznamu bez nutnosti zastavit a vytvořit nové předplatné.</span><span class="sxs-lookup"><span data-stu-id="ec40c-166">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="ec40c-167">Tato funkce je implementovaná v [ukázkovém řešení FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="ec40c-167">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="ec40c-168">`IFullStockTickerService` Rozhraní poskytuje tři metody:</span><span class="sxs-lookup"><span data-stu-id="ec40c-168">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="ec40c-169">`Subscribe`spustí připojení.</span><span class="sxs-lookup"><span data-stu-id="ec40c-169">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="ec40c-170">`AddSymbol`Přidá burzovní symbol, který se má sledovat.</span><span class="sxs-lookup"><span data-stu-id="ec40c-170">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="ec40c-171">`RemoveSymbol`Odebere symbol ze sledovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="ec40c-171">`RemoveSymbol` removes a symbol from the watched list.</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

<span data-ttu-id="ec40c-172">Rozhraní zpětného volání zůstává stejné.</span><span class="sxs-lookup"><span data-stu-id="ec40c-172">The callback interface remains the same.</span></span>

<span data-ttu-id="ec40c-173">Implementace tohoto modelu v gRPC je méně jednoduchá, protože nyní existují dva proudy dat s předávanými zprávami: jeden od klienta k serveru a druhý ze serveru do klienta.</span><span class="sxs-lookup"><span data-stu-id="ec40c-173">Implementing this pattern in gRPC is less straightforward, because there are now two streams of data with messages being passed: one from client to server, and another from server to client.</span></span> <span data-ttu-id="ec40c-174">Nelze použít více metod pro implementaci operace přidání a odebrání, ale více než jeden typ zprávy lze předat jednomu datovému proudu pomocí `Any` typu nebo `oneof` klíčového slova, které bylo pokryto v [kapitole 3](protobuf-any-oneof.md).</span><span class="sxs-lookup"><span data-stu-id="ec40c-174">It isn't possible to use multiple methods to implement the Add and Remove operation, but more than one type of message can be passed on a single stream, using either the `Any` type or `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="ec40c-175">V případě, že existuje určitá sada typů, které jsou přijatelné, představuje lepší `oneof` způsob, jak jít.</span><span class="sxs-lookup"><span data-stu-id="ec40c-175">For a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="ec40c-176">Použijte, který může obsahovat `AddSymbolRequest` buď nebo `RemoveSymbolRequest`. `ActionMessage`</span><span class="sxs-lookup"><span data-stu-id="ec40c-176">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`.</span></span>

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

<span data-ttu-id="ec40c-177">Deklarace služby streamování obousměrného přenosu dat, která přebírá `ActionMessage` proud zpráv</span><span class="sxs-lookup"><span data-stu-id="ec40c-177">Declare a bi-directional streaming service that takes a stream of `ActionMessage` messages.</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="ec40c-178">Implementace této služby je podobná předchozímu příkladu, s výjimkou `Subscribe` prvního parametru metody je `IAsyncStreamReader<ActionMessage>`nyní, který lze použít ke zpracování `Add` požadavků a `Remove` .</span><span class="sxs-lookup"><span data-stu-id="ec40c-178">The implementation for this service is similar to the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests.</span></span>

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors due to broken connection etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

<span data-ttu-id="ec40c-179">Třída, kterou gRPC vygenerovala pro nás garantuje, že je možné `Add` nastavit `Remove` jenom jednu z vlastností a a najít, která z `null` nich není platným způsobem, jak zjistit, který typ zprávy se používá, ale existuje lepší způsob, jak to najít. `ActionMessage` .</span><span class="sxs-lookup"><span data-stu-id="ec40c-179">The `ActionMessage` class that gRPC has generated for us guarantees that only one of the `Add` and `Remove` properties can be set, and finding which one isn't `null` is a valid way of finding which type of message is used, but there's a better way.</span></span> <span data-ttu-id="ec40c-180">Generování kódu také vytvořilo `enum ActionOneOfCase` `ActionMessage` ve třídě, což vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="ec40c-180">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="ec40c-181">Vlastnost `ActionCase` objektu`ActionMessage` lzepoužítspříkazemkurčení,které`switch` pole je nastaveno.</span><span class="sxs-lookup"><span data-stu-id="ec40c-181">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set.</span></span>

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> <span data-ttu-id="ec40c-182">Příkaz obsahuje případ, který zaznamená upozornění, pokud je zjištěna neznámá `ActionOneOfCase` hodnota. `default` `switch`</span><span class="sxs-lookup"><span data-stu-id="ec40c-182">The `switch` statement has a `default` case that logs a warning if an unknown `ActionOneOfCase` value is encountered.</span></span> <span data-ttu-id="ec40c-183">To může být užitečné v případě, že klient používá novější verzi `.proto` souboru, která přidala další akce.</span><span class="sxs-lookup"><span data-stu-id="ec40c-183">This could be useful in indicating that a client is using a later version of the `.proto` file which has added more actions.</span></span> <span data-ttu-id="ec40c-184">To je jeden z důvodů, proč `switch` použití je lepší než `null` testování u známých polí.</span><span class="sxs-lookup"><span data-stu-id="ec40c-184">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="ec40c-185">Použití FullStockTickerService z klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="ec40c-185">Use the FullStockTickerService from a client application</span></span>

<span data-ttu-id="ec40c-186">Existuje jednoduchá aplikace .NET Core 3,0 WPF, která předvádí použití tohoto složitějšího klienta.</span><span class="sxs-lookup"><span data-stu-id="ec40c-186">There's a simple .NET Core 3.0 WPF application to demonstrate use of this more complex client.</span></span> <span data-ttu-id="ec40c-187">Úplnou aplikaci najdete [na GitHubu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="ec40c-187">The full application can be found [on GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="ec40c-188">Klient se používá ve `MainWindowViewModel` třídě, která získá instanci `FullStockTicker.FullStockTickerClient` typu z injektáže závislosti.</span><span class="sxs-lookup"><span data-stu-id="ec40c-188">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection.</span></span>

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

<span data-ttu-id="ec40c-189">Objekt vrácený `client.Subscribe()` metodou je nyní instancí typu `AsyncDuplexStreamingCall<TRequest, TResponse>`knihovny gRPC, která poskytuje `RequestStream` pro `ResponseStream` odeslání požadavků na server a pro zpracování odpovědí.</span><span class="sxs-lookup"><span data-stu-id="ec40c-189">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server, and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="ec40c-190">Datový proud požadavku se používá z některých metod `ICommand` WPF k přidávání a odebírání symbolů.</span><span class="sxs-lookup"><span data-stu-id="ec40c-190">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="ec40c-191">Pro každou operaci nastavte příslušné pole `ActionMessage` objektu:</span><span class="sxs-lookup"><span data-stu-id="ec40c-191">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> <span data-ttu-id="ec40c-192">Nastavení hodnoty `oneof` pole u zprávy automaticky vymaže všechna pole, která byla dříve nastavena.</span><span class="sxs-lookup"><span data-stu-id="ec40c-192">Setting a `oneof` field's value on a message automatically clears any fields that have been previously set.</span></span>

<span data-ttu-id="ec40c-193">Proud odpovědí je zpracováván v `async` metodě `Task` a vrátí se, aby byla uvolněna při zavření okna.</span><span class="sxs-lookup"><span data-stu-id="ec40c-193">The stream of responses is handled in an `async` method, and the `Task` it returns is held to be disposed when the window is closed.</span></span>

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-clean-up"></a><span data-ttu-id="ec40c-194">Vyčištění klienta</span><span class="sxs-lookup"><span data-stu-id="ec40c-194">Client clean-up</span></span>

<span data-ttu-id="ec40c-195">`MainWindowViewModel` Když je okno zavřeno a je vyřazeno ( `Closed` z události `MainWindow`), doporučujeme, abyste `AsyncDuplexStreamingCall` objekt správně odstranili.</span><span class="sxs-lookup"><span data-stu-id="ec40c-195">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), it's recommended that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="ec40c-196">Konkrétně `CompleteAsync` `RequestStream` by měla být volána metoda na, aby se řádně zavřel datový proud na serveru.</span><span class="sxs-lookup"><span data-stu-id="ec40c-196">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="ec40c-197">Následující příklad ukazuje `DisposeAsync` metodu z ukázkového zobrazení-model:</span><span class="sxs-lookup"><span data-stu-id="ec40c-197">The following example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

<span data-ttu-id="ec40c-198">Uzavírání datových proudů požadavků umožňuje serveru včas vyřadit vlastní prostředky.</span><span class="sxs-lookup"><span data-stu-id="ec40c-198">Closing request streams enables the server to dispose of its own resources in a timely manner.</span></span> <span data-ttu-id="ec40c-199">To zlepšuje efektivitu a škálovatelnost služeb a zabraňuje výjimkám.</span><span class="sxs-lookup"><span data-stu-id="ec40c-199">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ec40c-200">[Předchozí](migrate-request-reply.md)
>[Další](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="ec40c-200">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
