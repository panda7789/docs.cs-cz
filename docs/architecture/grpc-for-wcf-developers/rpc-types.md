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
# <a name="types-of-rpc"></a>Typy RPC

Jako vývojář Windows Communication Foundation (WCF) jste pravděpodobně zvyklí na práci s následujícími typy vzdáleného volání procedur (RPC):

- Žádost/odpověď
- Duplexní:
  - Jednosměrný oboustranný tisk s relací
  - Plně duplexní s relací
- Jednosměrné

Tyto typy RPC je možné mapovat poměrně přirozeně na existující koncepty gRPC. Tato kapitola se bude zabývat každou z těchto oblastí. [Kapitola 5](migrate-wcf-to-grpc.md) se bude podrobněji zabývat podobnými příklady.

| WCF | gRPC |
| --- | ---- |
| Pravidelný požadavek/odpověď | Unární |
| Duplexní služba s relací pomocí rozhraní zpětného volání klienta | Serverové vysílání |
| Plně duplexní služba s relací | Obousměrné streamování |
| Jednosměrné operace | Streamování klientů |

## <a name="requestreply"></a>Žádost/odpověď

Pro jednoduché metody požadavku/odpovědi, které berou a vracejí malé množství dat, použijte nejjednodušší gRPC vzor, unární RPC.

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

Jak můžete vidět, implementace metody služby gRPC unární služby RPC je podobná implementaci operace WCF. Rozdíl je, že s gRPC přepsat metodu základní třídy namísto implementace rozhraní. Na serveru gRPC základní metody <xref:System.Threading.Tasks.Task%601>vždy vrátit , i když klient poskytuje asynchronní a blokování metody pro volání služby.

## <a name="wcf-duplex-one-way-to-client"></a>WCF duplex, jedna cesta ke klientovi

WCF aplikace (s určitými vazbami) můžete vytvořit trvalé připojení mezi klientem a serverem. Server může asynchronně odesílat data klientovi, dokud není připojení ukončeno, pomocí <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> *rozhraní zpětného volání* určeného ve vlastnosti.

služby gRPC poskytují podobné funkce s datovými proudy zpráv. Datové proudy nejsou *mapovat přesně* WCF duplexní služby z hlediska implementace, ale můžete dosáhnout stejných výsledků.

### <a name="grpc-streaming"></a>gRPC streamování

gRPC podporuje vytváření trvalých datových proudů z klienta na server a ze serveru na klienta. Oba typy datového proudu může být aktivní současně. Tato schopnost se nazývá obousměrné streamování.

Datové proudy můžete použít pro libovolné asynchronní zasílání zpráv v průběhu času. Nebo je můžete použít pro předávání velkých datových sad, které jsou příliš velké pro generování a odesílání v jednom požadavku nebo odpovědi.

Následující příklad ukazuje server-streaming RPC.

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

Tento datový proud serveru lze spotřebovávat z klientské aplikace, jak je znázorněno v následujícím kódu:

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
> Server-streaming RPC jsou užitečné pro služby ve stylu předplatného. Jsou také užitečné pro odesílání velkých datových sad, když by bylo neefektivní nebo nemožné vytvořit celou datovou sadu v paměti. Odpovědi na streamování však nejsou tak `repeated` rychlé jako odesílání polí v jedné zprávě. Streamování by se zpravidla nemělo používat pro malé datové sady.

### <a name="differences-from-wcf"></a>Rozdíly od WCF

Duplexní služba WCF používá rozhraní pro zpětné volání klienta, které může mít více metod. Služba streamování serveru gRPC může odesílat zprávy pouze přes jeden datový proud. Pokud potřebujete více metod, použijte typ zprávy s [polem Any nebo polem](protobuf-any-oneof.md) pro odesílání různých zpráv a zapisujte kód do klienta, který je zpracovává.

V WCF [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) třídy s relace je udržována naživu, dokud není připojení ukončeno. V rámci relace lze volat více metod. V gRPC, `Task` že metoda implementace vrátí by neměl dokončit, dokud připojení je uzavřen.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>WCF jednosměrné operace a gRPC klientstreaming

WCF poskytuje jednosměrné operace `[OperationContract(IsOneWay = true)]`(označené ) které vracejí potvrzení specifické pro přenos. metody služby gRPC vždy vrátí odpověď, i když je prázdná. Klient by měl vždy čekat na tuto odpověď. Pro "fire-and-forget" styl zasílání zpráv v gRPC, můžete vytvořit klientstreaming služby.

### <a name="thing_logproto"></a>thing_log.proto

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

K zasílání zpráv fire-and-forget můžete použít klient-streaming, jak je znázorněno v předchozím příkladu. Můžete je také použít pro odesílání velmi velkých datových sad na server. Platí stejné upozornění na výkon: pro menší `repeated` datové sady použijte pole v pravidelných zprávách.

## <a name="wcf-full-duplex-services"></a>WCF plně duplexní služby

Duplexní vazba WCF podporuje více jednosměrných operací v rozhraní služby i v rozhraní zpětného volání klienta. Tato podpora umožňuje probíhající konverzace mezi klientem a serverem. gRPC podporuje něco podobného s obousměrnými streamovacími RPC, kde jsou oba parametry označeny modifikátorem. `stream`

### <a name="chatproto"></a>chat.proto

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

V předchozím příkladu uvidíte, že metoda implementace přijímá`IAsyncStreamReader<MessageRequest>`datový proud požadavku`IServerStreamWriter<MessageResponse>`( ) i datový proud odpovědí ( ). Metoda může číst a zapisovat zprávy, dokud není připojení ukončeno.

### <a name="chatter-client"></a>Klient chatteru

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
>[další](metadata.md)
