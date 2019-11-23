---
title: Typy RPC-gRPC pro vývojáře WCF
description: Kontrola typů vzdáleného volání procedur podporovaného službou WCF a jejich ekvivalenty v gRPC
ms.date: 09/02/2019
ms.openlocfilehash: 64375236da17c0aedbafe1cb441e72a144203358
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967274"
---
# <a name="types-of-rpc"></a><span data-ttu-id="ccc24-103">Typy RPC</span><span class="sxs-lookup"><span data-stu-id="ccc24-103">Types of RPC</span></span>

<span data-ttu-id="ccc24-104">Jako vývojář Windows Communication Foundation (WCF) se pravděpodobně používá pro zvládnutí následujících typů vzdáleného volání procedur (RPC):</span><span class="sxs-lookup"><span data-stu-id="ccc24-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of Remote Procedure Call (RPC):</span></span>

- <span data-ttu-id="ccc24-105">Požadavek nebo odpověď</span><span class="sxs-lookup"><span data-stu-id="ccc24-105">Request/Reply</span></span>
- <span data-ttu-id="ccc24-106">Přenos</span><span class="sxs-lookup"><span data-stu-id="ccc24-106">Duplex:</span></span>
  - <span data-ttu-id="ccc24-107">Obousměrný Duplex s relací</span><span class="sxs-lookup"><span data-stu-id="ccc24-107">One-way duplex with session</span></span>
  - <span data-ttu-id="ccc24-108">Plně duplexní s relací</span><span class="sxs-lookup"><span data-stu-id="ccc24-108">Full duplex with session</span></span>
- <span data-ttu-id="ccc24-109">Jednosměrnou metodou</span><span class="sxs-lookup"><span data-stu-id="ccc24-109">One-way</span></span>

<span data-ttu-id="ccc24-110">Tyto typy RPC je možné namapovat poměrně přirozeně na stávající gRPC koncepty a tato kapitola se pak bude pohlížet na každou z těchto oblastí.</span><span class="sxs-lookup"><span data-stu-id="ccc24-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts and this chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="ccc24-111">Podobné příklady se prozkoumají v mnohem větší hloubce v [kapitole 5](migrate-wcf-to-grpc.md).</span><span class="sxs-lookup"><span data-stu-id="ccc24-111">Similar examples will be explored in much greater depth in [Chapter 5](migrate-wcf-to-grpc.md).</span></span>

| <span data-ttu-id="ccc24-112">WCF</span><span class="sxs-lookup"><span data-stu-id="ccc24-112">WCF</span></span> | <span data-ttu-id="ccc24-113">gRPC</span><span class="sxs-lookup"><span data-stu-id="ccc24-113">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="ccc24-114">Pravidelný požadavek nebo odpověď</span><span class="sxs-lookup"><span data-stu-id="ccc24-114">Regular request/reply</span></span> | <span data-ttu-id="ccc24-115">Unární</span><span class="sxs-lookup"><span data-stu-id="ccc24-115">Unary</span></span> |
| <span data-ttu-id="ccc24-116">Duplexní služba s relací pomocí rozhraní zpětného volání klienta</span><span class="sxs-lookup"><span data-stu-id="ccc24-116">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="ccc24-117">Streamování serveru</span><span class="sxs-lookup"><span data-stu-id="ccc24-117">Server streaming</span></span> |
| <span data-ttu-id="ccc24-118">Plně duplexní služba s relací</span><span class="sxs-lookup"><span data-stu-id="ccc24-118">Full duplex service with session</span></span> | <span data-ttu-id="ccc24-119">Obousměrný streamování</span><span class="sxs-lookup"><span data-stu-id="ccc24-119">Bidirectional streaming</span></span> |
| <span data-ttu-id="ccc24-120">Jednosměrné operace</span><span class="sxs-lookup"><span data-stu-id="ccc24-120">One-way operations</span></span> | <span data-ttu-id="ccc24-121">Streamování klientů</span><span class="sxs-lookup"><span data-stu-id="ccc24-121">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="ccc24-122">Požadavek nebo odpověď</span><span class="sxs-lookup"><span data-stu-id="ccc24-122">Request/reply</span></span>

<span data-ttu-id="ccc24-123">Pro jednoduché metody žádosti a odpovědi, které přijímají a vracejí malé objemy dat, použijte nejjednodušší vzor gRPC, unární RPC.</span><span class="sxs-lookup"><span data-stu-id="ccc24-123">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

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

<span data-ttu-id="ccc24-124">Jak vidíte, implementace gRPC unární metody služby RPC je velmi podobná implementaci operace WCF, s výjimkou toho, že u gRPC přepíšete metodu základní třídy namísto implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ccc24-124">As you can see, implementing a gRPC unary RPC service method is very similar to implementing a WCF operation, except that with gRPC you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="ccc24-125">Všimněte si, že na serveru gRPC základní metody vždycky vrací <xref:System.Threading.Tasks.Task%601>, i když klient poskytne asynchronní a blokující metody pro volání služby.</span><span class="sxs-lookup"><span data-stu-id="ccc24-125">Note that on the server, gRPC base methods always return a <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="ccc24-126">Obousměrný a jednosměrný klient služby WCF</span><span class="sxs-lookup"><span data-stu-id="ccc24-126">WCF duplex, one-way to client</span></span>

<span data-ttu-id="ccc24-127">Aplikace WCF (s určitými vazbami) mohou vytvořit trvalé připojení mezi klientem a serverem a server může asynchronně odeslat data klientovi, dokud nebude připojení ukončeno, pomocí *rozhraní zpětného volání* , které je zadáno ve vlastnosti <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ccc24-127">WCF applications (with certain bindings) can create a persistent connection between client and server, and the server can asynchronously send data to the client until the connection is closed, using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="ccc24-128">služby gRPC Services poskytují podobné funkce jako datové proudy zpráv.</span><span class="sxs-lookup"><span data-stu-id="ccc24-128">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="ccc24-129">Datové proudy se nemapují *přesně* na duplexní služby WCF v souvislosti s implementací, ale je možné dosáhnout stejných výsledků.</span><span class="sxs-lookup"><span data-stu-id="ccc24-129">Streams don't map *exactly* to WCF duplex services in terms of implementation, but the same results can be achieved.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="ccc24-130">streamování gRPC</span><span class="sxs-lookup"><span data-stu-id="ccc24-130">gRPC streaming</span></span>

<span data-ttu-id="ccc24-131">gRPC podporuje vytváření trvalých datových proudů z klienta na server a ze serveru na klienta.</span><span class="sxs-lookup"><span data-stu-id="ccc24-131">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="ccc24-132">Oba typy datových proudů mohou být souběžně aktivní; označuje se jako obousměrný streamování.</span><span class="sxs-lookup"><span data-stu-id="ccc24-132">Both types of stream may be active concurrently; this is called bidirectional streaming.</span></span> <span data-ttu-id="ccc24-133">Datové proudy lze použít pro libovolný, asynchronní zasílání zpráv v čase nebo pro předávání velkých datových sad, které jsou příliš velké pro generování a posílání v jednom požadavku nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ccc24-133">Streams can be used for arbitrary, asynchronous messaging over time, or for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="ccc24-134">Následující příklad ukazuje streamování serveru RPC.</span><span class="sxs-lookup"><span data-stu-id="ccc24-134">The following example shows a server streaming RPC.</span></span>

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

<span data-ttu-id="ccc24-135">Tento datový proud serveru lze spotřebovat z klientské aplikace, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="ccc24-135">This server stream could be consumed from a client application as shown in the following code:</span></span>

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
> <span data-ttu-id="ccc24-136">Služba RPCSS pro streamování serveru je užitečná pro služby ve stylu předplatného a také pro posílání velmi rozsáhlých datových sad, pokud by bylo neefektivní nebo nemožné sestavit celou datovou sadu v paměti.</span><span class="sxs-lookup"><span data-stu-id="ccc24-136">Server streaming RPCs are useful for subscription-style services, and also for sending very large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="ccc24-137">Odezvy streamování se ale nemění tak rychle, jako když posíláte `repeated` pole v jedné zprávě, takže pro malé datové sady by se neměla používat streamování pravidla.</span><span class="sxs-lookup"><span data-stu-id="ccc24-137">However, streaming responses isn't as fast as sending `repeated` fields in a single message, so as a rule streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-to-wcf"></a><span data-ttu-id="ccc24-138">Rozdíly na WCF</span><span class="sxs-lookup"><span data-stu-id="ccc24-138">Differences to WCF</span></span>

<span data-ttu-id="ccc24-139">Duplexní služba WCF používá rozhraní zpětného volání klienta, které může mít více metod.</span><span class="sxs-lookup"><span data-stu-id="ccc24-139">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="ccc24-140">Služba streamování serveru gRPC může odesílat zprávy jenom přes jeden datový proud.</span><span class="sxs-lookup"><span data-stu-id="ccc24-140">A gRPC server streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="ccc24-141">Pokud potřebujete více metod, použijte typ zprávy s [libovolným polem nebo jedním polem](protobuf-any-oneof.md) pro odeslání různých zpráv a napište kód v klientovi, který je zpracovává.</span><span class="sxs-lookup"><span data-stu-id="ccc24-141">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="ccc24-142">Ve službě WCF je třída [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) s relací udržována v neaktivním stavu, dokud se připojení nezavře a v rámci relace může být voláno více metod.</span><span class="sxs-lookup"><span data-stu-id="ccc24-142">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed, and multiple methods may be called within the session.</span></span> <span data-ttu-id="ccc24-143">V gRPC je `Task` vrácená metodou implementace by neměl být dokončena, dokud nebude připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="ccc24-143">In gRPC, the `Task` returned by the implementation method shouldn't complete until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="ccc24-144">Jednosměrné operace WCF a streamování klienta gRPC</span><span class="sxs-lookup"><span data-stu-id="ccc24-144">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="ccc24-145">WCF poskytuje jednosměrné operace (označené `[OperationContract(IsOneWay = true)]`), které vracejí potvrzení specifické pro přenos.</span><span class="sxs-lookup"><span data-stu-id="ccc24-145">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="ccc24-146">metody služby gRPC vždycky vrátí odpověď, i když je prázdná, a klient by měl vždycky očekávat tuto odpověď.</span><span class="sxs-lookup"><span data-stu-id="ccc24-146">gRPC service methods always return a response, even if it's empty, and the client should always await that response.</span></span> <span data-ttu-id="ccc24-147">Pro zasílání zpráv ve stylu "požár a zapomenuté zprávy" v gRPC můžete vytvořit službu streamování klientů.</span><span class="sxs-lookup"><span data-stu-id="ccc24-147">For "fire-and-forget" style messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="ccc24-148">thing_log. proto</span><span class="sxs-lookup"><span data-stu-id="ccc24-148">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="ccc24-149">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="ccc24-149">ThingLogService.cs</span></span>

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

### <a name="thinglog-client-example"></a><span data-ttu-id="ccc24-150">Příklad klienta ThingLog</span><span class="sxs-lookup"><span data-stu-id="ccc24-150">ThingLog client example</span></span>

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

<span data-ttu-id="ccc24-151">Znovu platí, že služba RPCSS pro streamování klientů se dá použít pro zasílání zpráv s požárem a proti zapomenutí, jak je znázorněno v předchozím příkladu, ale také pro posílání velkých datových sad na server.</span><span class="sxs-lookup"><span data-stu-id="ccc24-151">Again, client streaming RPCs can be used for fire-and-forget messaging as shown in the previous example, but also for sending very large datasets to the server.</span></span> <span data-ttu-id="ccc24-152">Platí stejné upozornění na výkon: pro menší datové sady použijte pole `repeated` v pravidelných zprávách.</span><span class="sxs-lookup"><span data-stu-id="ccc24-152">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="ccc24-153">Plně duplexní služby WCF</span><span class="sxs-lookup"><span data-stu-id="ccc24-153">WCF full duplex services</span></span>

<span data-ttu-id="ccc24-154">Duplexní vazba WCF podporuje více jednosměrných operací na rozhraní služby a rozhraní zpětného volání klienta, což umožňuje průběžné konverzace mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="ccc24-154">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface, allowing ongoing conversations between client and server.</span></span> <span data-ttu-id="ccc24-155">gRPC podporuje něco podobného jako obousměrný datový proud RPCSS, kde jsou oba parametry označeny modifikátorem `stream`.</span><span class="sxs-lookup"><span data-stu-id="ccc24-155">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="ccc24-156">chat. proto</span><span class="sxs-lookup"><span data-stu-id="ccc24-156">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="ccc24-157">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="ccc24-157">ChatterService.cs</span></span>

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

<span data-ttu-id="ccc24-158">V předchozím příkladu vidíte, že metoda implementace přijímá datový proud požadavku (`IAsyncStreamReader<MessageRequest>`) i datový proud odpovědí (`IServerStreamWriter<MessageResponse>`) a může číst a zapisovat zprávy, dokud není připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="ccc24-158">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`), and can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="ccc24-159">Klient chatu</span><span class="sxs-lookup"><span data-stu-id="ccc24-159">Chatter client</span></span>

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
><span data-ttu-id="ccc24-160">[Předchozí](wcf-bindings.md)
>[Další](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="ccc24-160">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
