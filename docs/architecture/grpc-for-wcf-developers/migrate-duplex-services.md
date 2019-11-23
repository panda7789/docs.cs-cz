---
title: Migrace duplexních služeb WCF na gRPC-gRPC pro vývojáře WCF
description: Naučte se migrovat různé formy duplexní služby WCF na služby gRPC streaming.
ms.date: 09/02/2019
ms.openlocfilehash: e2248df20e5c2d8f96055d42ba684749251154bd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971872"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a>Migrace duplexních služeb WCF do gRPC

Teď, když jsou na začátku základní koncepty, Tato část se bude pohlížet na složitější *streamování* gRPC Services.

V Windows Communication Foundation (WCF) existuje několik způsobů použití duplexních služeb. Některé služby jsou iniciovány klientem a poté jsou z tohoto serveru streamovaná data. Jiné plně duplexní služby můžou v dokumentaci WCF zahrnovat nepřetržitou obousměrnou komunikaci, například klasický příklad kalkulačky. Tato kapitola bude mít dvě možné implementace služby WCF "burzovních impulsů" a migruje je do gRPC: jedno pomocí služby RPC pro streamování serveru a druhý pomocí protokolu RPC s obousměrným datovým proudem.

## <a name="server-streaming-rpc"></a>RPC streamování serveru

V [ukázkovém řešení SIMPLESTOCKTICKER WCF](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)je *SimpleStockPriceTicker*duplexní služba, kde klient spouští připojení se seznamem burzovních symbolů a server používá *rozhraní zpětného volání* k posílání aktualizací, jakmile budou k dispozici. Klient implementuje rozhraní, aby reagoval na volání ze serveru.

### <a name="the-wcf-solution"></a>Řešení WCF

Řešení WCF je implementováno jako server NetTCP v místním prostředí v konzolové aplikaci .NET Framework 4. x.

#### <a name="the-servicecontract"></a>Třída ServiceContract

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

Služba má jedinou metodu bez návratového typu, protože bude používat rozhraní zpětného volání `ISimpleStockTickerCallback` k posílání dat klientovi v reálném čase.

#### <a name="the-callback-interface"></a>Rozhraní zpětného volání

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

Implementace těchto rozhraní se dají najít v řešení společně s falešným externími závislostmi k poskytnutí testovacích dat.

### <a name="grpc-streaming"></a>streamování gRPC

GRPC způsob zpracování dat v reálném čase se liší. Volání z klienta na server může vytvořit trvalý datový proud, který lze monitorovat pro zprávy přicházející asynchronně. Navzdory rozdílům může být datový proud intuitivnější způsob, jak se s těmito daty pracovat a které jsou důležitější při moderním programování s důrazem na LINQ, reaktivní streamy, funkční programování atd.

Definice služby potřebuje dvě zprávy: jednu pro požadavek a jednu pro datový proud. Služba vrátí datový proud `StockTickerUpdate` zprávy pomocí klíčového slova `stream` ve své deklaraci `return`. Doporučujeme, abyste do aktualizace přidali `Timestamp`, abyste zobrazili přesný čas změny ceny.

#### <a name="simple_stock_tickerproto"></a>simple_stock_ticker. proto

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

### <a name="implement-the-simplestockticker"></a>Implementace rozhraní SimpleStockTicker

Opětovným použitím falešného `StockPriceSubscriber` z projektu WCF zkopírujte tři třídy z knihovny tříd `TraderSys.StockMarket` do nové .NET Standard knihovny tříd v cílovém řešení. Chcete-li lépe dodržovat osvědčené postupy, přidejte `Factory` typ pro vytvoření instancí IT a zaregistrujte `IStockPriceSubscriberFactory` pomocí služby pro vkládání závislostí ASP.NET Core.

#### <a name="the-factory-implementation"></a>Implementace továrny

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

#### <a name="registering-the-factory"></a>Registrace továrny

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

Nyní lze tuto třídu použít k implementaci služby gRPC StockTicker.

#### <a name="stocktickerservicecs"></a>StockTickerService.cs

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

Jak vidíte, i když deklarace v souboru `.proto` říká, že metoda vrátí datový proud `StockTickerUpdate` zprávy, ve skutečnosti vrátí Vanilla `Task`. Úloha vytvoření datového proudu je zpracována generovaným kódem a běhovými knihovnami gRPC, které poskytují datový proud odpovědí `IServerStreamWriter<StockTickerUpdate>` připravený k použití.

Na rozdíl od služby duplexní služba WCF, kde je instance třídy služby aktivní, když je připojení otevřené, služba gRPC použije vrácenou úlohu, aby službu udržovala aktivní. Úloha by neměla být dokončena, dokud nebude připojení ukončeno.

Služba může zjistit, kdy klient ukončil připojení pomocí `CancellationToken` z `ServerCallContext`. Jednoduchá statická metoda, `AwaitCancellation`, se používá k vytvoření úlohy, která se dokončí při zrušení tokenu.

V metodě `Subscribe` pak Získejte `StockPriceSubscriber` a přidejte obslužnou rutinu události, která zapisuje do datového proudu odpovědí. Pak počkejte, než se připojení zavře, a teprve potom okamžitě odstraňte `subscriber`, aby se zabránilo zápisu dat do zavřeného datového proudu.

Metoda `WriteUpdateAsync` má `try`/`catch` blok pro zpracování případných chyb, ke kterým může dojít při zápisu zprávy do datového proudu. To je důležitý aspekt trvalého připojení přes sítě, které by mohlo být v jakémkoli milisekundě přerušeno, ať už úmyslně nebo z důvodu selhání.

### <a name="using-the-stocktickerservice-from-a-client-application"></a>Použití rozhraní StockTickerService z klientské aplikace

Použijte stejný postup v předchozí části a vytvořte knihovnu klientských tříd klienta ze souboru `.proto` ke sdílení. V ukázce je k dispozici Konzolová aplikace .NET Core 3,0, která ukazuje, jak používat klienta.

#### <a name="example-programcs"></a>Příklad Program.cs

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

V tomto případě není metoda `Subscribe` v generovaném klientovi asynchronní. Stream se vytvoří a dá se použít hned, protože jeho `MoveNext` metoda je asynchronní a při prvním volání se nespustí, dokud nebude připojení aktivní.

Datový proud je předán metodě asynchronního `DisplayAsync`; Aplikace potom počká, až uživatel stiskne klávesu, a pak zruší metodu `DisplayAsync` a před ukončením počká, než se úkol dokončí.

> [!NOTE]
> Tento kód používá novou C# syntaxi 8 "using Declaration" k Dispose datového proudu a kanálu při ukončení metody `Main`. Jedná se o malou změnu, ale je to dobrý čas, který omezí odsazení a prázdné řádky.

#### <a name="consume-the-stream"></a>Využití streamu

WCF používá rozhraní zpětného volání, aby mohl server volat metody přímo na straně klienta. datové proudy gRPC fungují jinak. Klient prochází vráceným datovým proudem a zpracovává zprávy stejným způsobem, jako kdyby byly vráceny z místní metody vracející `IEnumerable`.

Typ `IAsyncStreamReader<T>` funguje podobně jako `IEnumerator<T>`: existuje `MoveNext` metoda, která vrátí hodnotu true, dokud bude existovat více dat, a vlastnost `Current`, která vrací nejnovější hodnotu. Jediným rozdílem je, že metoda `MoveNext` vrátí `Task<bool>` namísto pouze `bool`. Metoda rozšíření `ReadAllAsync` zalomí datový proud ve standardu C# 8 `IAsyncEnumerable`, který lze použít s novou syntaxí `await foreach`.

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
> Oddíl na [klientských knihovnách](client-libraries.md#iobservable) na konci této kapitoly si vyhledá, jak přidat rozšiřující metodu a třídy pro zabalení `IAsyncStreamReader<T>` v `IObservable<T>` pro vývojáře pomocí reaktivních programovacích vzorů.

Znovu pečlivě Zachyťte výjimky z důvodu možnosti selhání sítě a <xref:System.OperationCanceledException>, které budou nevyhnutelně vyvolány, protože kód používá <xref:System.Threading.CancellationToken> k přerušení smyčky. `RpcException` typ obsahuje spoustu užitečných informací o chybách běhového prostředí gRPC, včetně `StatusCode`. Další informace najdete v části [ *zpracování chyb* v kapitole 4](error-handling.md).

## <a name="bidirectional-streaming"></a>Obousměrný streamování

Plně duplexní služba WCF umožňuje asynchronní zasílání zpráv v reálném čase v obou směrech. V příkladu streamování serveru spustí klient požadavek a potom obdrží datový proud aktualizací. Lepší verze této služby umožňuje klientovi přidávat a odebírat zásoby ze seznamu bez nutnosti zastavit a vytvořit nové předplatné. Tato funkce je implementovaná v [ukázkovém řešení FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).

Rozhraní `IFullStockTickerService` poskytuje tři metody:

- `Subscribe` spustí připojení.
- `AddSymbol` přidá burzovní symbol, který se má sledovat.
- `RemoveSymbol` odebere symbol ze sledovaného seznamu.

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

Rozhraní zpětného volání zůstává stejné.

Implementace tohoto modelu v gRPC je méně jednoduchá, protože nyní existují dva proudy dat s předávanými zprávami: jeden od klienta k serveru a druhý ze serveru do klienta. Nelze použít více metod pro implementaci operace přidání a odebrání, ale více než jeden typ zprávy lze předat jednomu datovému proudu pomocí typu `Any` nebo `oneof` klíčového slova, které bylo pokryto v [kapitole 3](protobuf-any-oneof.md).

V případě, že existuje určitá sada typů, které jsou přijatelné, `oneof` představuje lepší způsob, jak jít. Použijte `ActionMessage`, která může obsahovat buď `AddSymbolRequest`, nebo `RemoveSymbolRequest`.

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

Deklarace služby streamování na obousměrné streamování, která přebírá proud `ActionMessage`ch zpráv.

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

Implementace této služby je podobná předchozímu příkladu, s výjimkou prvního parametru `Subscribe` metody je nyní `IAsyncStreamReader<ActionMessage>`, které lze použít ke zpracování `Add` a `Remove` požadavků.

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

Třída `ActionMessage`, kterou gRPC pro USA vygenerovala, že je možné nastavit jenom jednu z vlastností `Add` a `Remove` a najít, která z nich není `null`, je platný způsob, jakým se používá typ zprávy, ale lepší způsob hledání. Generování kódu také vytvořilo `enum ActionOneOfCase` ve třídě `ActionMessage`, která vypadá takto:

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

Vlastnost `ActionCase` na objektu `ActionMessage` lze použít s příkazem `switch` k určení, které pole je nastaveno.

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
> Příkaz `switch` má `default` případ, který zaznamená upozornění, pokud je zjištěna neznámá `ActionOneOfCase` hodnota. To může být užitečné v případě, že klient používá novější verzi `.proto` souboru, který přidal další akce. Je to jeden z důvodů, proč je použití `switch` lepší než testování pro `null` ve známých polích.

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a>Použití FullStockTickerService z klientské aplikace

Existuje jednoduchá aplikace .NET Core 3,0 WPF, která předvádí použití tohoto složitějšího klienta. Úplnou aplikaci najdete [na GitHubu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).

Klient se používá ve třídě `MainWindowViewModel`, která získá instanci `FullStockTicker.FullStockTickerClient` typu z vkládání závislostí.

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

Objekt vrácený metodou `client.Subscribe()` je nyní instancí typu knihovny gRPC `AsyncDuplexStreamingCall<TRequest, TResponse>`, která poskytuje `RequestStream` pro odesílání požadavků na server a `ResponseStream` pro zpracování odpovědí.

Datový proud žádosti se používá z některých metod `ICommand` WPF k přidávání a odebírání symbolů. Pro každou operaci nastavte příslušné pole objektu `ActionMessage`:

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
> Nastavením hodnoty `oneof` pole u zprávy se automaticky vymaže všechna pole, která byla dříve nastavena.

Proud odpovědí je zpracováván v metodě `async` a `Task`, která se vrátí, je držena, aby byla uvolněna při zavření okna.

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

### <a name="client-clean-up"></a>Vyčištění klienta

Po zavření okna a `MainWindowViewModel` je uvolněna (z `Closed` události `MainWindow`), doporučujeme, abyste správně odstranili `AsyncDuplexStreamingCall` objekt. Konkrétně by měla být volána metoda `CompleteAsync` v `RequestStream`, aby se řádně zavřel datový proud na serveru. Následující příklad ukazuje metodu `DisposeAsync` z ukázkového zobrazení-model:

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

Uzavírání datových proudů požadavků umožňuje serveru včas vyřadit vlastní prostředky. To zlepšuje efektivitu a škálovatelnost služeb a zabraňuje výjimkám.

>[!div class="step-by-step"]
>[Předchozí](migrate-request-reply.md)
>[Další](streaming-versus-repeated.md)
