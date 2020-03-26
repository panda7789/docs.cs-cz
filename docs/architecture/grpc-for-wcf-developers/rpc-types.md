---
title: Typy RPC - gRPC pro vývojáře WCF
description: Přezkum typů volání vzdálených procedur podporovaných WCF a jejich ekvivalenty v gRPC
ms.date: 09/02/2019
ms.openlocfilehash: 40c0779dc015904e9dabbb448075e3c5aa5dc49a
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111085"
---
# <a name="types-of-rpc"></a><span data-ttu-id="2a749-103">Typy RPC</span><span class="sxs-lookup"><span data-stu-id="2a749-103">Types of RPC</span></span>

<span data-ttu-id="2a749-104">Jako vývojář Windows Communication Foundation (WCF) jste pravděpodobně zvyklí na práci s následujícími typy vzdáleného volání procedur (RPC):</span><span class="sxs-lookup"><span data-stu-id="2a749-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="2a749-105">Žádost/odpověď</span><span class="sxs-lookup"><span data-stu-id="2a749-105">Request/reply</span></span>
- <span data-ttu-id="2a749-106">Duplexní:</span><span class="sxs-lookup"><span data-stu-id="2a749-106">Duplex:</span></span>
  - <span data-ttu-id="2a749-107">Jednosměrný oboustranný tisk s relací</span><span class="sxs-lookup"><span data-stu-id="2a749-107">One-way duplex with session</span></span>
  - <span data-ttu-id="2a749-108">Plně duplexní s relací</span><span class="sxs-lookup"><span data-stu-id="2a749-108">Full duplex with session</span></span>
- <span data-ttu-id="2a749-109">Jednosměrné</span><span class="sxs-lookup"><span data-stu-id="2a749-109">One-way</span></span>

<span data-ttu-id="2a749-110">Tyto typy RPC je možné mapovat poměrně přirozeně na existující koncepty gRPC.</span><span class="sxs-lookup"><span data-stu-id="2a749-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="2a749-111">Tato kapitola se bude zabývat každou z těchto oblastí.</span><span class="sxs-lookup"><span data-stu-id="2a749-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="2a749-112">[Kapitola 5](migrate-wcf-to-grpc.md) se bude podrobněji zabývat podobnými příklady.</span><span class="sxs-lookup"><span data-stu-id="2a749-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="2a749-113">WCF</span><span class="sxs-lookup"><span data-stu-id="2a749-113">WCF</span></span> | <span data-ttu-id="2a749-114">gRPC</span><span class="sxs-lookup"><span data-stu-id="2a749-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="2a749-115">Pravidelný požadavek/odpověď</span><span class="sxs-lookup"><span data-stu-id="2a749-115">Regular request/reply</span></span> | <span data-ttu-id="2a749-116">Unární</span><span class="sxs-lookup"><span data-stu-id="2a749-116">Unary</span></span> |
| <span data-ttu-id="2a749-117">Duplexní služba s relací pomocí rozhraní zpětného volání klienta</span><span class="sxs-lookup"><span data-stu-id="2a749-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="2a749-118">Serverové vysílání</span><span class="sxs-lookup"><span data-stu-id="2a749-118">Server streaming</span></span> |
| <span data-ttu-id="2a749-119">Plně duplexní služba s relací</span><span class="sxs-lookup"><span data-stu-id="2a749-119">Full duplex service with session</span></span> | <span data-ttu-id="2a749-120">Obousměrné streamování</span><span class="sxs-lookup"><span data-stu-id="2a749-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="2a749-121">Jednosměrné operace</span><span class="sxs-lookup"><span data-stu-id="2a749-121">One-way operations</span></span> | <span data-ttu-id="2a749-122">Streamování klientů</span><span class="sxs-lookup"><span data-stu-id="2a749-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="2a749-123">Žádost/odpověď</span><span class="sxs-lookup"><span data-stu-id="2a749-123">Request/reply</span></span>

<span data-ttu-id="2a749-124">Pro jednoduché metody požadavku/odpovědi, které berou a vracejí malé množství dat, použijte nejjednodušší gRPC vzor, unární RPC.</span><span class="sxs-lookup"><span data-stu-id="2a749-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

<span data-ttu-id="2a749-125">Jak můžete vidět, implementace metody služby gRPC unární služby RPC je podobná implementaci operace WCF.</span><span class="sxs-lookup"><span data-stu-id="2a749-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="2a749-126">Rozdíl je, že s gRPC přepsat metodu základní třídy namísto implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a749-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="2a749-127">Na serveru gRPC základní metody <xref:System.Threading.Tasks.Task%601>vždy vrátit , i když klient poskytuje asynchronní a blokování metody pro volání služby.</span><span class="sxs-lookup"><span data-stu-id="2a749-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="2a749-128">WCF duplex, jedna cesta ke klientovi</span><span class="sxs-lookup"><span data-stu-id="2a749-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="2a749-129">WCF aplikace (s určitými vazbami) můžete vytvořit trvalé připojení mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="2a749-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="2a749-130">Server může asynchronně odesílat data klientovi, dokud není připojení ukončeno, pomocí <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> *rozhraní zpětného volání* určeného ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2a749-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="2a749-131">služby gRPC poskytují podobné funkce s datovými proudy zpráv.</span><span class="sxs-lookup"><span data-stu-id="2a749-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="2a749-132">Datové proudy nejsou *mapovat přesně* WCF duplexní služby z hlediska implementace, ale můžete dosáhnout stejných výsledků.</span><span class="sxs-lookup"><span data-stu-id="2a749-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="2a749-133">gRPC streamování</span><span class="sxs-lookup"><span data-stu-id="2a749-133">gRPC streaming</span></span>

<span data-ttu-id="2a749-134">gRPC podporuje vytváření trvalých datových proudů z klienta na server a ze serveru na klienta.</span><span class="sxs-lookup"><span data-stu-id="2a749-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="2a749-135">Oba typy datového proudu může být aktivní současně.</span><span class="sxs-lookup"><span data-stu-id="2a749-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="2a749-136">Tato schopnost se nazývá obousměrné streamování.</span><span class="sxs-lookup"><span data-stu-id="2a749-136">This ability is called bidirectional streaming.</span></span>

<span data-ttu-id="2a749-137">Datové proudy můžete použít pro libovolné asynchronní zasílání zpráv v průběhu času.</span><span class="sxs-lookup"><span data-stu-id="2a749-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="2a749-138">Nebo je můžete použít pro předávání velkých datových sad, které jsou příliš velké pro generování a odesílání v jednom požadavku nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="2a749-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="2a749-139">Následující příklad ukazuje server-streaming RPC.</span><span class="sxs-lookup"><span data-stu-id="2a749-139">The following example shows a server-streaming RPC.</span></span>

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

<span data-ttu-id="2a749-140">Tento datový proud serveru lze spotřebovávat z klientské aplikace, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="2a749-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> <span data-ttu-id="2a749-141">Server-streaming RPC jsou užitečné pro služby ve stylu předplatného.</span><span class="sxs-lookup"><span data-stu-id="2a749-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="2a749-142">Jsou také užitečné pro odesílání velkých datových sad, když by bylo neefektivní nebo nemožné vytvořit celou datovou sadu v paměti.</span><span class="sxs-lookup"><span data-stu-id="2a749-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="2a749-143">Odpovědi na streamování však nejsou tak `repeated` rychlé jako odesílání polí v jedné zprávě.</span><span class="sxs-lookup"><span data-stu-id="2a749-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="2a749-144">Streamování by se zpravidla nemělo používat pro malé datové sady.</span><span class="sxs-lookup"><span data-stu-id="2a749-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="2a749-145">Rozdíly od WCF</span><span class="sxs-lookup"><span data-stu-id="2a749-145">Differences from WCF</span></span>

<span data-ttu-id="2a749-146">Duplexní služba WCF používá rozhraní pro zpětné volání klienta, které může mít více metod.</span><span class="sxs-lookup"><span data-stu-id="2a749-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="2a749-147">Služba streamování serveru gRPC může odesílat zprávy pouze přes jeden datový proud.</span><span class="sxs-lookup"><span data-stu-id="2a749-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="2a749-148">Pokud potřebujete více metod, použijte typ zprávy s [polem Any nebo polem](protobuf-any-oneof.md) pro odesílání různých zpráv a zapisujte kód do klienta, který je zpracovává.</span><span class="sxs-lookup"><span data-stu-id="2a749-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="2a749-149">V WCF [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) třídy s relace je udržována naživu, dokud není připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="2a749-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="2a749-150">V rámci relace lze volat více metod.</span><span class="sxs-lookup"><span data-stu-id="2a749-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="2a749-151">V gRPC, `Task` že metoda implementace vrátí by neměl dokončit, dokud připojení je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="2a749-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="2a749-152">WCF jednosměrné operace a gRPC klientstreaming</span><span class="sxs-lookup"><span data-stu-id="2a749-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="2a749-153">WCF poskytuje jednosměrné operace `[OperationContract(IsOneWay = true)]`(označené ) které vracejí potvrzení specifické pro přenos.</span><span class="sxs-lookup"><span data-stu-id="2a749-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgment.</span></span> <span data-ttu-id="2a749-154">metody služby gRPC vždy vrátí odpověď, i když je prázdná.</span><span class="sxs-lookup"><span data-stu-id="2a749-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="2a749-155">Klient by měl vždy čekat na tuto odpověď.</span><span class="sxs-lookup"><span data-stu-id="2a749-155">The client should always await that response.</span></span> <span data-ttu-id="2a749-156">Pro "fire-and-forget" styl zasílání zpráv v gRPC, můžete vytvořit klientstreaming služby.</span><span class="sxs-lookup"><span data-stu-id="2a749-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="2a749-157">thing_log.proto</span><span class="sxs-lookup"><span data-stu-id="2a749-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="2a749-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="2a749-158">ThingLogService.cs</span></span>

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a><span data-ttu-id="2a749-159">Příklad klienta ThingLog</span><span class="sxs-lookup"><span data-stu-id="2a749-159">ThingLog client example</span></span>

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

<span data-ttu-id="2a749-160">K zasílání zpráv fire-and-forget můžete použít klient-streaming, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2a749-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="2a749-161">Můžete je také použít pro odesílání velmi velkých datových sad na server.</span><span class="sxs-lookup"><span data-stu-id="2a749-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="2a749-162">Platí stejné upozornění na výkon: pro menší `repeated` datové sady použijte pole v pravidelných zprávách.</span><span class="sxs-lookup"><span data-stu-id="2a749-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="2a749-163">WCF plně duplexní služby</span><span class="sxs-lookup"><span data-stu-id="2a749-163">WCF full-duplex services</span></span>

<span data-ttu-id="2a749-164">Duplexní vazba WCF podporuje více jednosměrných operací v rozhraní služby i v rozhraní zpětného volání klienta.</span><span class="sxs-lookup"><span data-stu-id="2a749-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="2a749-165">Tato podpora umožňuje probíhající konverzace mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="2a749-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="2a749-166">gRPC podporuje něco podobného s obousměrnými streamovacími RPC, kde jsou oba parametry označeny modifikátorem. `stream`</span><span class="sxs-lookup"><span data-stu-id="2a749-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="2a749-167">chat.proto</span><span class="sxs-lookup"><span data-stu-id="2a749-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="2a749-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="2a749-168">ChatterService.cs</span></span>

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

<span data-ttu-id="2a749-169">V předchozím příkladu uvidíte, že metoda implementace přijímá`IAsyncStreamReader<MessageRequest>`datový proud požadavku`IServerStreamWriter<MessageResponse>`( ) i datový proud odpovědí ( ).</span><span class="sxs-lookup"><span data-stu-id="2a749-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="2a749-170">Metoda může číst a zapisovat zprávy, dokud není připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="2a749-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="2a749-171">Klient chatteru</span><span class="sxs-lookup"><span data-stu-id="2a749-171">Chatter client</span></span>

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
><span data-ttu-id="2a749-172">[Předchozí](wcf-bindings.md)
>[další](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="2a749-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
