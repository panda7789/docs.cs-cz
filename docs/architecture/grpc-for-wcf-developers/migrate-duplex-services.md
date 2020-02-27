---
title: Migrace duplexních služeb WCF na gRPC-gRPC pro vývojáře WCF
description: Naučte se migrovat různé formy duplexních služeb WCF na služby gRPC streaming.
ms.date: 09/02/2019
ms.openlocfilehash: 5737f02044ab9e4064f632164db764541a9c4d31
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628537"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="c4ca1-103">Migrace duplexních služeb WCF do gRPC</span><span class="sxs-lookup"><span data-stu-id="c4ca1-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="c4ca1-104">Teď, když máte představu o základních konceptech, v této části se podíváte na složitější *streamování* gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-104">Now that you have a sense of the basic concepts, in this section, you'll look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="c4ca1-105">V Windows Communication Foundation (WCF) existuje několik způsobů použití duplexních služeb.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c4ca1-106">Některé služby jsou iniciovány klientem a poté jsou z tohoto serveru streamovaná data.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="c4ca1-107">Jiné plně duplexní služby můžou zahrnovat nepřetržitou obousměrnou komunikaci, jako je například klasický Kalkulačka v dokumentaci k WCF.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-107">Other full-duplex services might involve more ongoing two-way communication, like the classic Calculator example in the WCF documentation.</span></span> <span data-ttu-id="c4ca1-108">Tato kapitola bude trvat dvě možné implementace burzovních impulsů WCF a migrovat je na gRPC: jeden, který používá rozhraní RPC pro streamování serveru, a druhý, který používá protokol RPC s obousměrným datovým proudem.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-108">This chapter will take two possible WCF stock ticker implementations and migrate them to gRPC: one that uses a server streaming RPC and another one that uses a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="c4ca1-109">RPC streamování serveru</span><span class="sxs-lookup"><span data-stu-id="c4ca1-109">Server streaming RPC</span></span>

<span data-ttu-id="c4ca1-110">V [ukázkovém řešení SIMPLESTOCKTICKER WCF](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)je SimpleStockPriceTicker duplexní služba, pro kterou klient spouští připojení se seznamem burzovních symbolů a server používá *rozhraní zpětného volání* k odesílání aktualizací, jakmile budou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, there's a duplex service for which the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="c4ca1-111">Klient implementuje rozhraní, aby reagoval na volání ze serveru.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="c4ca1-112">Řešení WCF</span><span class="sxs-lookup"><span data-stu-id="c4ca1-112">The WCF solution</span></span>

<span data-ttu-id="c4ca1-113">Řešení WCF je implementováno jako hostitelský server NET. TCP ve .NET Framework 4. Konzolová aplikace *x* .</span><span class="sxs-lookup"><span data-stu-id="c4ca1-113">The WCF solution is implemented as a self-hosted Net.TCP server in a .NET Framework 4.*x* console application.</span></span>

#### <a name="servicecontract"></a><span data-ttu-id="c4ca1-114">ServiceContract</span><span class="sxs-lookup"><span data-stu-id="c4ca1-114">ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="c4ca1-115">Služba má jedinou metodu bez návratového typu, protože používá rozhraní zpětného volání `ISimpleStockTickerCallback` k posílání dat klientovi v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-115">The service has a single method with no return type because it uses the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="c4ca1-116">Rozhraní zpětného volání</span><span class="sxs-lookup"><span data-stu-id="c4ca1-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="c4ca1-117">Implementace těchto rozhraní můžete v řešení najít společně s falešným externími závislostmi k poskytnutí testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-117">You can find the implementations of these interfaces in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="c4ca1-118">streamování gRPC</span><span class="sxs-lookup"><span data-stu-id="c4ca1-118">gRPC streaming</span></span>

<span data-ttu-id="c4ca1-119">Proces gRPC pro zpracování dat v reálném čase se liší od procesu WCF.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-119">The gRPC process for handling real-time data is different from the WCF process.</span></span> <span data-ttu-id="c4ca1-120">Volání z klienta na server může vytvořit trvalý datový proud, který lze monitorovat pro zprávy, které přicházejí asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-120">A call from client to server can create a persistent stream, which can be monitored for messages that arrive asynchronously.</span></span> <span data-ttu-id="c4ca1-121">Navzdory rozdílům může být datový proud intuitivnější způsob, jak se s těmito daty pracovat a které jsou pro moderní programování důležitější, což zdůrazňuje LINQ, reaktivní streamy, funkční programování atd.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming, which emphasizes LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="c4ca1-122">Definice služby potřebuje dvě zprávy: jednu pro požadavek a jednu pro datový proud.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-122">The service definition needs two messages: one for the request and one for the stream.</span></span> <span data-ttu-id="c4ca1-123">Služba vrátí datový proud zprávy `StockTickerUpdate` s klíčovým slovem `stream` ve své deklaraci `return`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-123">The service returns a stream of the `StockTickerUpdate` message with the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="c4ca1-124">Doporučujeme, abyste do aktualizace přidali `Timestamp`, abyste zobrazili přesný čas změny ceny.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-124">We recommend that you add a `Timestamp` to the update to show the exact time of the price change.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="c4ca1-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="c4ca1-125">simple_stock_ticker.proto</span></span>

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
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-simplestockticker"></a><span data-ttu-id="c4ca1-126">Implementovat SimpleStockTicker</span><span class="sxs-lookup"><span data-stu-id="c4ca1-126">Implement SimpleStockTicker</span></span>

<span data-ttu-id="c4ca1-127">Opětovným použitím falešného `StockPriceSubscriber` z projektu WCF zkopírujte tři třídy z knihovny tříd `TraderSys.StockMarket` do nové .NET Standard knihovny tříd v cílovém řešení.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="c4ca1-128">Chcete-li lépe dodržovat osvědčené postupy, přidejte `Factory` typ pro vytvoření instancí IT a zaregistrujte `IStockPriceSubscriberFactory` pomocí služby pro vkládání závislostí ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-128">To better follow best practices, add a `Factory` type to create instances of it, and register the `IStockPriceSubscriberFactory` with the ASP.NET Core dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="c4ca1-129">Implementace továrny</span><span class="sxs-lookup"><span data-stu-id="c4ca1-129">The factory implementation</span></span>

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

#### <a name="register-the-factory"></a><span data-ttu-id="c4ca1-130">Registrace továrny</span><span class="sxs-lookup"><span data-stu-id="c4ca1-130">Register the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="c4ca1-131">Tato třída se teď dá použít k implementaci `StockTickerService`gRPC.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-131">This class can now be used to implement the gRPC `StockTickerService`.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="c4ca1-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="c4ca1-132">StockTickerService.cs</span></span>

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
            // Handle any errors caused by broken connection, etc.
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

<span data-ttu-id="c4ca1-133">Jak vidíte, i když deklarace v souboru `.proto` říká, že metoda vrátí datový proud `StockTickerUpdate` zprávy, ve skutečnosti vrátí `Task`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-133">As you can see, although the declaration in the `.proto` file says the method returns a stream of `StockTickerUpdate` messages, it actually returns a `Task`.</span></span> <span data-ttu-id="c4ca1-134">Úloha vytvoření datového proudu je zpracována generovaným kódem a běhovými knihovnami gRPC, které poskytují datový proud odpovědí `IServerStreamWriter<StockTickerUpdate>` připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="c4ca1-135">Na rozdíl od služby duplexní služba WCF, kde je instance třídy služby aktivní, když je připojení otevřené, služba gRPC použije vrácenou úlohu, aby službu udržovala aktivní.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned task to keep the service alive.</span></span> <span data-ttu-id="c4ca1-136">Úloha by neměla být dokončena, dokud nebude připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-136">The task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="c4ca1-137">Služba může zjistit, kdy klient ukončil připojení pomocí `CancellationToken` z `ServerCallContext`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="c4ca1-138">Jednoduchá statická metoda, `AwaitCancellation`, se používá k vytvoření úlohy, která se dokončí při zrušení tokenu.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-138">A simple static method, `AwaitCancellation`, is used to create a task that completes when the token is canceled.</span></span>

<span data-ttu-id="c4ca1-139">V metodě `Subscribe` pak Získejte `StockPriceSubscriber` a přidejte obslužnou rutinu události, která zapisuje do datového proudu odpovědí.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="c4ca1-140">Pak počkejte, než se připojení zavře, a poté okamžitě odstraňte `subscriber`, aby nedošlo k pokusu o zápis dat do zavřeného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-140">Then wait for the connection to be closed before immediately disposing the `subscriber` to prevent it from trying to write data to the closed stream.</span></span>

<span data-ttu-id="c4ca1-141">Metoda `WriteUpdateAsync` má `try`/`catch` blok pro zpracování chyb, které mohou nastat při zápisu zprávy do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when a message is written to the stream.</span></span> <span data-ttu-id="c4ca1-142">Toto posouzení je důležité v trvalých připojeních přes sítě, která by mohla být v jakémkoli milisekundě přerušená, ať už úmyslně nebo z důvodu selhání.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-142">This consideration is important in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="use-stocktickerservice-from-a-client-application"></a><span data-ttu-id="c4ca1-143">Použití StockTickerService z klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="c4ca1-143">Use StockTickerService from a client application</span></span>

<span data-ttu-id="c4ca1-144">Použijte stejný postup v předchozí části a vytvořte knihovnu klientských tříd klienta ze souboru `.proto` ke sdílení.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="c4ca1-145">V ukázce je k dispozici Konzolová aplikace .NET Core 3,0, která ukazuje, jak používat klienta.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-145">In the sample, there's a .NET Core 3.0 console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="c4ca1-146">Příklad Program.cs</span><span class="sxs-lookup"><span data-stu-id="c4ca1-146">Example Program.cs</span></span>

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

<span data-ttu-id="c4ca1-147">V tomto případě není metoda `Subscribe` v generovaném klientovi asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="c4ca1-148">Datový proud se vytvoří a dá se použít hned, protože jeho `MoveNext` metoda je asynchronní a při prvním volání ho nebude možné dokončit, dokud nebude připojení aktivní.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-148">The stream is created and usable right away because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="c4ca1-149">Datový proud je předán asynchronní metodě `DisplayAsync`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-149">The stream is passed to an asynchronous `DisplayAsync` method.</span></span> <span data-ttu-id="c4ca1-150">Aplikace potom počká, až uživatel stiskne klávesu, a poté zruší metodu `DisplayAsync` a před ukončením počká, než se úkol dokončí.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-150">The application then waits for the user to press a key, and then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="c4ca1-151">Tento kód používá novou C# syntaxi syntaxe 8 `using` k Dispose datového proudu a kanálu, když se metoda `Main` ukončí.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-151">This code uses the new C# 8 `using` declaration syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="c4ca1-152">Jedná se o malou změnu, ale je to dobrý čas, který omezí odsazení a prázdné řádky.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-152">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="c4ca1-153">Využití streamu</span><span class="sxs-lookup"><span data-stu-id="c4ca1-153">Consume the stream</span></span>

<span data-ttu-id="c4ca1-154">WCF používá rozhraní zpětného volání, aby mohl server volat metody přímo na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-154">WCF uses callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="c4ca1-155">datové proudy gRPC fungují jinak.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-155">gRPC streams work differently.</span></span> <span data-ttu-id="c4ca1-156">Klient prochází vráceným datovým proudem a zpracovává zprávy stejným způsobem, jako kdyby byly vráceny z místní metody vracející `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-156">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="c4ca1-157">Typ `IAsyncStreamReader<T>` funguje podobně jako `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-157">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`.</span></span> <span data-ttu-id="c4ca1-158">Existuje `MoveNext` metoda, která vrací hodnotu true, pokud jsou k dispozici další data a vlastnost `Current`, která vrací nejnovější hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-158">There's a `MoveNext` method that returns true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="c4ca1-159">Jediným rozdílem je, že metoda `MoveNext` vrátí `Task<bool>` namísto pouze `bool`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-159">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="c4ca1-160">Metoda rozšíření `ReadAllAsync` zalomí datový proud ve standardu C# 8 `IAsyncEnumerable`, který lze použít s novou syntaxí `await foreach`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-160">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

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
> <span data-ttu-id="c4ca1-161">Pro vývojáře, kteří používají reaktivní programové vzory, část na [klientských knihovnách](client-libraries.md#iobservable) na konci této kapitoly ukazuje, jak přidat rozšiřující metodu a třídy pro zabalení `IAsyncStreamReader<T>` v `IObservable<T>`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-161">For developers using reactive programming patterns, the section on [client libraries](client-libraries.md#iobservable) at the end of this chapter shows how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>`.</span></span>

<span data-ttu-id="c4ca1-162">Znovu nezapomeňte zachytit výjimky z důvodu možnosti selhání sítě a kvůli <xref:System.OperationCanceledException>, která bude nevyhnutelně vyvolána, protože kód používá <xref:System.Threading.CancellationToken> k přerušení smyčky.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-162">Again, be sure to catch exceptions here because of the possibility of network failure, and because of the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="c4ca1-163">`RpcException` typ obsahuje spoustu užitečných informací o chybách běhového prostředí gRPC, včetně `StatusCode`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-163">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="c4ca1-164">Další informace najdete v části [ *zpracování chyb* v kapitole 4](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="c4ca1-164">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="c4ca1-165">Obousměrný streamování</span><span class="sxs-lookup"><span data-stu-id="c4ca1-165">Bidirectional streaming</span></span>

<span data-ttu-id="c4ca1-166">Plně duplexní služba WCF umožňuje asynchronní zasílání zpráv v reálném čase v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-166">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="c4ca1-167">V příkladu streamování serveru spustí klient požadavek a potom obdrží datový proud aktualizací.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-167">In the server streaming example, the client starts a request and then receives a stream of updates.</span></span> <span data-ttu-id="c4ca1-168">Lepší verze této služby umožňuje klientovi přidávat a odebírat zásoby ze seznamu bez nutnosti zastavit a vytvořit nové předplatné.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-168">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="c4ca1-169">Tato funkce je implementovaná v [ukázkovém řešení FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="c4ca1-169">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="c4ca1-170">Rozhraní `IFullStockTickerService` poskytuje tři metody:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-170">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="c4ca1-171">`Subscribe` spustí připojení.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-171">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="c4ca1-172">`AddSymbol` přidá burzovní symbol, který se má sledovat.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-172">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="c4ca1-173">`RemoveSymbol` odebere symbol ze sledovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-173">`RemoveSymbol` removes a symbol from the watched list.</span></span>

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

<span data-ttu-id="c4ca1-174">Rozhraní zpětného volání zůstává stejné.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-174">The callback interface remains the same.</span></span>

<span data-ttu-id="c4ca1-175">Implementace tohoto modelu v gRPC je méně jednoduchá, protože nyní existují dva proudy dat s předávanými zprávami: jeden od klienta k serveru a druhý ze serveru do klienta.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-175">Implementing this pattern in gRPC is less straightforward because there are now two streams of data with messages being passed: one from client to server and another from server to client.</span></span> <span data-ttu-id="c4ca1-176">Není možné použít více metod k implementaci operací přidání a odebrání, ale můžete předat více než jeden typ zprávy v jednom datovém proudu pomocí typu `Any` nebo klíčového slova `oneof`, které bylo pokryto v [kapitole 3](protobuf-any-oneof.md).</span><span class="sxs-lookup"><span data-stu-id="c4ca1-176">It isn't possible to use multiple methods to implement the add and remove operations, but you can pass more than one type of message on a single stream by using either the `Any` type or the `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="c4ca1-177">V případě, že existuje určitá sada typů, které jsou přijatelné, `oneof` představuje lepší způsob, jak jít.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-177">In a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="c4ca1-178">Použijte `ActionMessage`, který může obsahovat `AddSymbolRequest` nebo `RemoveSymbolRequest`:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-178">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`:</span></span>

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

<span data-ttu-id="c4ca1-179">Deklarovat službu obousměrného streamování, která přebírá proud `ActionMessage`ch zpráv:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-179">Declare a bidirectional streaming service that takes a stream of `ActionMessage` messages:</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="c4ca1-180">Implementace této služby je podobná jako v předchozím příkladu, s výjimkou prvního parametru metody `Subscribe` je teď `IAsyncStreamReader<ActionMessage>`, která se dá použít ke zpracování `Add` a `Remove` požadavků:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-180">The implementation for this service is similar to that of the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests:</span></span>

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
        // Handle any errors caused by broken connection, etc.
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

<span data-ttu-id="c4ca1-181">Třída `ActionMessage`, kterou gRPC vygenerovala, zaručuje, že lze nastavit pouze jeden z vlastností `Add` a `Remove`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-181">The `ActionMessage` class that gRPC has generated guarantees that only one of the `Add` and `Remove` properties can be set.</span></span> <span data-ttu-id="c4ca1-182">Zjištění, které z nich není `null`, představuje platný způsob, jak určit typ zprávy, který se používá, ale lepší způsob je.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-182">Finding which one isn't `null` is a valid way to determine which type of message is used, but there's a better way.</span></span> <span data-ttu-id="c4ca1-183">Generování kódu také vytvořilo `enum ActionOneOfCase` ve třídě `ActionMessage`, která vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-183">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="c4ca1-184">Vlastnost `ActionCase` na objektu `ActionMessage` lze použít s příkazem `switch` k určení, které pole je nastaveno:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-184">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set:</span></span>

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
> <span data-ttu-id="c4ca1-185">Příkaz `switch` má `default` případ, který zaznamená upozornění, pokud nalezne neznámou hodnotu `ActionOneOfCase`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-185">The `switch` statement has a `default` case that logs a warning if it encounters an unknown `ActionOneOfCase` value.</span></span> <span data-ttu-id="c4ca1-186">To může být užitečné pro indikaci, že klient používá novější verzi `.proto` souboru, který přidal další akce.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-186">This could be useful to indicate that a client is using a later version of the `.proto` file that has added more actions.</span></span> <span data-ttu-id="c4ca1-187">Je to jeden z důvodů, proč je použití `switch` lepší než testování pro `null` ve známých polích.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-187">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="c4ca1-188">Použití FullStockTickerService z klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="c4ca1-188">Use FullStockTickerService from a client application</span></span>

<span data-ttu-id="c4ca1-189">Existuje jednoduchá aplikace .NET Core 3,0 WPF, která demonstruje použití tohoto složitějšího klienta.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-189">There's a simple .NET Core 3.0 WPF application that demonstrates the use of this more complex client.</span></span> <span data-ttu-id="c4ca1-190">Celou aplikaci můžete najít na [GitHubu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="c4ca1-190">You can find the full application on [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="c4ca1-191">Klient se používá ve třídě `MainWindowViewModel`, která získá instanci `FullStockTicker.FullStockTickerClient` typu z injektáže vložením závislosti:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-191">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection:</span></span>

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

<span data-ttu-id="c4ca1-192">Objekt vrácený metodou `client.Subscribe()` je nyní instancí typu knihovny gRPC `AsyncDuplexStreamingCall<TRequest, TResponse>`, která poskytuje `RequestStream` pro odesílání požadavků na server a `ResponseStream` pro zpracování odpovědí.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-192">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="c4ca1-193">Datový proud žádosti se používá z některých metod `ICommand` WPF k přidávání a odebírání symbolů.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-193">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="c4ca1-194">Pro každou operaci nastavte příslušné pole objektu `ActionMessage`:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-194">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

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
> <span data-ttu-id="c4ca1-195">Nastavením hodnoty `oneof` pole na zprávu automaticky vymažete všechna pole, která byla nastavena dříve.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-195">Setting a `oneof` field's value on a message automatically clears any fields that have been set previously.</span></span>

<span data-ttu-id="c4ca1-196">Proud odpovědí je zpracováván v metodě `async`.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-196">The stream of responses is handled in an `async` method.</span></span> <span data-ttu-id="c4ca1-197">`Task`, kterou vrátí, je držena, aby byla uvolněna při zavření okna:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-197">The `Task` it returns is held to be disposed when the window is closed:</span></span>

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

### <a name="client-cleanup"></a><span data-ttu-id="c4ca1-198">Vyčištění klienta</span><span class="sxs-lookup"><span data-stu-id="c4ca1-198">Client cleanup</span></span>

<span data-ttu-id="c4ca1-199">Po zavření okna a `MainWindowViewModel` je uvolněna (z `Closed` události `MainWindow`), doporučujeme, abyste správně odstranili `AsyncDuplexStreamingCall` objekt.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-199">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), we recommend that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="c4ca1-200">Konkrétně by měla být volána metoda `CompleteAsync` v `RequestStream`, aby se řádně zavřel datový proud na serveru.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-200">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="c4ca1-201">Tento příklad ukazuje metodu `DisposeAsync` z ukázkového zobrazení-model:</span><span class="sxs-lookup"><span data-stu-id="c4ca1-201">This example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public async ValueTask DisposeAsync()
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

<span data-ttu-id="c4ca1-202">Uzavírání datových proudů požadavků umožňuje serveru včas nakládat své vlastní prostředky.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-202">Closing request streams enables the server to dispose of its own resources in a timely way.</span></span> <span data-ttu-id="c4ca1-203">To zlepšuje efektivitu a škálovatelnost služeb a zabraňuje výjimkám.</span><span class="sxs-lookup"><span data-stu-id="c4ca1-203">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c4ca1-204">[Předchozí](migrate-request-reply.md)
>[Další](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="c4ca1-204">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
