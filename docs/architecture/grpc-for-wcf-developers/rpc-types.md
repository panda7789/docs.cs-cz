---
title: Typy RPC-gRPC pro vývojáře WCF
description: Kontrola typů vzdáleného volání procedur podporovaného službou WCF a jejich ekvivalenty v gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ce5bf03b01dff3f7bb201ff08c9065abc2e58360
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846230"
---
# <a name="types-of-rpc"></a>Typy RPC

Jako vývojář Windows Communication Foundation (WCF) se pravděpodobně používá pro zvládnutí následujících typů vzdáleného volání procedur (RPC):

- Požadavek nebo odpověď
- Přenos
  - Obousměrný Duplex s relací
  - Plně duplexní s relací
- Jednosměrnou metodou

Tyto typy RPC je možné namapovat poměrně přirozeně na stávající gRPC koncepty a tato kapitola se pak bude pohlížet na každou z těchto oblastí. Podobné příklady se prozkoumají v mnohem větší hloubce v [kapitole 5](migrate-wcf-to-grpc.md).

| WCF | gRPC |
| --- | ---- |
| Pravidelný požadavek nebo odpověď | Unární |
| Duplexní služba s relací pomocí rozhraní zpětného volání klienta | Streamování serveru |
| Plně duplexní služba s relací | Obousměrný streamování |
| Jednosměrné operace | Streamování klientů |

## <a name="requestreply"></a>Požadavek nebo odpověď

Pro jednoduché metody žádosti a odpovědi, které přijímají a vracejí malé objemy dat, použijte nejjednodušší vzor gRPC, unární RPC.

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

Jak vidíte, implementace gRPC unární metody služby RPC je velmi podobná implementaci operace WCF, s výjimkou toho, že u gRPC přepíšete metodu základní třídy namísto implementace rozhraní. Všimněte si, že na serveru gRPC základní metody vždycky vrací <xref:System.Threading.Tasks.Task%601>, i když klient poskytne asynchronní a blokující metody pro volání služby.

## <a name="wcf-duplex-one-way-to-client"></a>Obousměrný a jednosměrný klient služby WCF

Aplikace WCF (s určitými vazbami) mohou vytvořit trvalé připojení mezi klientem a serverem a server může asynchronně odeslat data klientovi, dokud nebude připojení ukončeno, pomocí *rozhraní zpětného volání* , které je zadáno v <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> majetek.

služby gRPC Services poskytují podobné funkce jako datové proudy zpráv. Datové proudy se nemapují *přesně* na duplexní služby WCF v souvislosti s implementací, ale je možné dosáhnout stejných výsledků.

### <a name="grpc-streaming"></a>streamování gRPC

gRPC podporuje vytváření trvalých datových proudů z klienta na server a ze serveru na klienta. Oba typy datových proudů mohou být souběžně aktivní; označuje se jako obousměrný streamování. Datové proudy lze použít pro libovolný, asynchronní zasílání zpráv v čase nebo pro předávání velkých datových sad, které jsou příliš velké pro generování a posílání v jednom požadavku nebo odpovědi.

Následující příklad ukazuje streamování serveru RPC.

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

Tento datový proud serveru lze spotřebovat z klientské aplikace, jak je znázorněno v následujícím kódu:

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
> Služba RPCSS pro streamování serveru je užitečná pro služby ve stylu předplatného a také pro posílání velmi rozsáhlých datových sad, pokud by bylo neefektivní nebo nemožné sestavit celou datovou sadu v paměti. Odezvy streamování se ale nemění tak rychle, jako když posíláte `repeated` pole v jedné zprávě, takže pro malé datové sady by se neměla používat streamování pravidla.

### <a name="differences-to-wcf"></a>Rozdíly na WCF

Duplexní služba WCF používá rozhraní zpětného volání klienta, které může mít více metod. Služba streamování serveru gRPC může odesílat zprávy jenom přes jeden datový proud. Pokud potřebujete více metod, použijte typ zprávy s [libovolným polem nebo jedním polem](protobuf-any-oneof.md) pro odeslání různých zpráv a napište kód v klientovi, který je zpracovává.

Ve službě WCF je třída [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) s relací udržována v neaktivním stavu, dokud se připojení nezavře a v rámci relace může být voláno více metod. V gRPC je `Task` vrácená metodou implementace by neměl být dokončena, dokud nebude připojení ukončeno.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>Jednosměrné operace WCF a streamování klienta gRPC

WCF poskytuje jednosměrné operace (označené `[OperationContract(IsOneWay = true)]`), které vracejí potvrzení specifické pro přenos. metody služby gRPC vždycky vrátí odpověď, i když je prázdná, a klient by měl vždycky očekávat tuto odpověď. Pro zasílání zpráv ve stylu "požár a zapomenuté zprávy" v gRPC můžete vytvořit službu streamování klientů.

### <a name="thing_logproto"></a>thing_log.

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a>ThingLogService.cs

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

### <a name="thinglog-client-example"></a>Příklad klienta ThingLog

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

Znovu platí, že služba RPCSS pro streamování klientů se dá použít pro zasílání zpráv s požárem a proti zapomenutí, jak je znázorněno v předchozím příkladu, ale také pro posílání velkých datových sad na server. Platí stejné upozornění na výkon: pro menší datové sady použijte pole `repeated` v pravidelných zprávách.

## <a name="wcf-full-duplex-services"></a>Plně duplexní služby WCF

Duplexní vazba WCF podporuje více jednosměrných operací na rozhraní služby a rozhraní zpětného volání klienta, což umožňuje průběžné konverzace mezi klientem a serverem. gRPC podporuje něco podobného jako obousměrný datový proud RPCSS, kde jsou oba parametry označeny modifikátorem `stream`.

### <a name="chatproto"></a>chat. proto

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a>ChatterService.cs

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

V předchozím příkladu vidíte, že metoda implementace přijímá datový proud požadavku (`IAsyncStreamReader<MessageRequest>`) i datový proud odpovědí (`IServerStreamWriter<MessageResponse>`) a může číst a zapisovat zprávy, dokud není připojení ukončeno.

### <a name="chatter-client"></a>Klient chatu

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
>[Předchozí](wcf-bindings.md)
>[Další](metadata.md)
