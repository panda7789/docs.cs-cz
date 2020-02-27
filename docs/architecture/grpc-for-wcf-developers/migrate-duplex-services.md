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
# <a name="migrate-wcf-duplex-services-to-grpc"></a>Migrace duplexních služeb WCF do gRPC

Teď, když máte představu o základních konceptech, v této části se podíváte na složitější *streamování* gRPC Services.

V Windows Communication Foundation (WCF) existuje několik způsobů použití duplexních služeb. Některé služby jsou iniciovány klientem a poté jsou z tohoto serveru streamovaná data. Jiné plně duplexní služby můžou zahrnovat nepřetržitou obousměrnou komunikaci, jako je například klasický Kalkulačka v dokumentaci k WCF. Tato kapitola bude trvat dvě možné implementace burzovních impulsů WCF a migrovat je na gRPC: jeden, který používá rozhraní RPC pro streamování serveru, a druhý, který používá protokol RPC s obousměrným datovým proudem.

## <a name="server-streaming-rpc"></a>RPC streamování serveru

V [ukázkovém řešení SIMPLESTOCKTICKER WCF](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)je SimpleStockPriceTicker duplexní služba, pro kterou klient spouští připojení se seznamem burzovních symbolů a server používá *rozhraní zpětného volání* k odesílání aktualizací, jakmile budou k dispozici. Klient implementuje rozhraní, aby reagoval na volání ze serveru.

### <a name="the-wcf-solution"></a>Řešení WCF

Řešení WCF je implementováno jako hostitelský server NET. TCP ve .NET Framework 4. Konzolová aplikace *x* .

#### <a name="servicecontract"></a>ServiceContract

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

Služba má jedinou metodu bez návratového typu, protože používá rozhraní zpětného volání `ISimpleStockTickerCallback` k posílání dat klientovi v reálném čase.

#### <a name="the-callback-interface"></a>Rozhraní zpětného volání

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

Implementace těchto rozhraní můžete v řešení najít společně s falešným externími závislostmi k poskytnutí testovacích dat.

### <a name="grpc-streaming"></a>streamování gRPC

Proces gRPC pro zpracování dat v reálném čase se liší od procesu WCF. Volání z klienta na server může vytvořit trvalý datový proud, který lze monitorovat pro zprávy, které přicházejí asynchronně. Navzdory rozdílům může být datový proud intuitivnější způsob, jak se s těmito daty pracovat a které jsou pro moderní programování důležitější, což zdůrazňuje LINQ, reaktivní streamy, funkční programování atd.

Definice služby potřebuje dvě zprávy: jednu pro požadavek a jednu pro datový proud. Služba vrátí datový proud zprávy `StockTickerUpdate` s klíčovým slovem `stream` ve své deklaraci `return`. Doporučujeme, abyste do aktualizace přidali `Timestamp`, abyste zobrazili přesný čas změny ceny.

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

### <a name="implement-simplestockticker"></a>Implementovat SimpleStockTicker

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

#### <a name="register-the-factory"></a>Registrace továrny

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

Tato třída se teď dá použít k implementaci `StockTickerService`gRPC.

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

Jak vidíte, i když deklarace v souboru `.proto` říká, že metoda vrátí datový proud `StockTickerUpdate` zprávy, ve skutečnosti vrátí `Task`. Úloha vytvoření datového proudu je zpracována generovaným kódem a běhovými knihovnami gRPC, které poskytují datový proud odpovědí `IServerStreamWriter<StockTickerUpdate>` připravený k použití.

Na rozdíl od služby duplexní služba WCF, kde je instance třídy služby aktivní, když je připojení otevřené, služba gRPC použije vrácenou úlohu, aby službu udržovala aktivní. Úloha by neměla být dokončena, dokud nebude připojení ukončeno.

Služba může zjistit, kdy klient ukončil připojení pomocí `CancellationToken` z `ServerCallContext`. Jednoduchá statická metoda, `AwaitCancellation`, se používá k vytvoření úlohy, která se dokončí při zrušení tokenu.

V metodě `Subscribe` pak Získejte `StockPriceSubscriber` a přidejte obslužnou rutinu události, která zapisuje do datového proudu odpovědí. Pak počkejte, než se připojení zavře, a poté okamžitě odstraňte `subscriber`, aby nedošlo k pokusu o zápis dat do zavřeného datového proudu.

Metoda `WriteUpdateAsync` má `try`/`catch` blok pro zpracování chyb, které mohou nastat při zápisu zprávy do datového proudu. Toto posouzení je důležité v trvalých připojeních přes sítě, která by mohla být v jakémkoli milisekundě přerušená, ať už úmyslně nebo z důvodu selhání.

### <a name="use-stocktickerservice-from-a-client-application"></a>Použití StockTickerService z klientské aplikace

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

V tomto případě není metoda `Subscribe` v generovaném klientovi asynchronní. Datový proud se vytvoří a dá se použít hned, protože jeho `MoveNext` metoda je asynchronní a při prvním volání ho nebude možné dokončit, dokud nebude připojení aktivní.

Datový proud je předán asynchronní metodě `DisplayAsync`. Aplikace potom počká, až uživatel stiskne klávesu, a poté zruší metodu `DisplayAsync` a před ukončením počká, než se úkol dokončí.

> [!NOTE]
> Tento kód používá novou C# syntaxi syntaxe 8 `using` k Dispose datového proudu a kanálu, když se metoda `Main` ukončí. Jedná se o malou změnu, ale je to dobrý čas, který omezí odsazení a prázdné řádky.

#### <a name="consume-the-stream"></a>Využití streamu

WCF používá rozhraní zpětného volání, aby mohl server volat metody přímo na straně klienta. datové proudy gRPC fungují jinak. Klient prochází vráceným datovým proudem a zpracovává zprávy stejným způsobem, jako kdyby byly vráceny z místní metody vracející `IEnumerable`.

Typ `IAsyncStreamReader<T>` funguje podobně jako `IEnumerator<T>`. Existuje `MoveNext` metoda, která vrací hodnotu true, pokud jsou k dispozici další data a vlastnost `Current`, která vrací nejnovější hodnotu. Jediným rozdílem je, že metoda `MoveNext` vrátí `Task<bool>` namísto pouze `bool`. Metoda rozšíření `ReadAllAsync` zalomí datový proud ve standardu C# 8 `IAsyncEnumerable`, který lze použít s novou syntaxí `await foreach`.

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
> Pro vývojáře, kteří používají reaktivní programové vzory, část na [klientských knihovnách](client-libraries.md#iobservable) na konci této kapitoly ukazuje, jak přidat rozšiřující metodu a třídy pro zabalení `IAsyncStreamReader<T>` v `IObservable<T>`.

Znovu nezapomeňte zachytit výjimky z důvodu možnosti selhání sítě a kvůli <xref:System.OperationCanceledException>, která bude nevyhnutelně vyvolána, protože kód používá <xref:System.Threading.CancellationToken> k přerušení smyčky. `RpcException` typ obsahuje spoustu užitečných informací o chybách běhového prostředí gRPC, včetně `StatusCode`. Další informace najdete v části [ *zpracování chyb* v kapitole 4](error-handling.md).

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

Implementace tohoto modelu v gRPC je méně jednoduchá, protože nyní existují dva proudy dat s předávanými zprávami: jeden od klienta k serveru a druhý ze serveru do klienta. Není možné použít více metod k implementaci operací přidání a odebrání, ale můžete předat více než jeden typ zprávy v jednom datovém proudu pomocí typu `Any` nebo klíčového slova `oneof`, které bylo pokryto v [kapitole 3](protobuf-any-oneof.md).

V případě, že existuje určitá sada typů, které jsou přijatelné, `oneof` představuje lepší způsob, jak jít. Použijte `ActionMessage`, který může obsahovat `AddSymbolRequest` nebo `RemoveSymbolRequest`:

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

Deklarovat službu obousměrného streamování, která přebírá proud `ActionMessage`ch zpráv:

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

Implementace této služby je podobná jako v předchozím příkladu, s výjimkou prvního parametru metody `Subscribe` je teď `IAsyncStreamReader<ActionMessage>`, která se dá použít ke zpracování `Add` a `Remove` požadavků:

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

Třída `ActionMessage`, kterou gRPC vygenerovala, zaručuje, že lze nastavit pouze jeden z vlastností `Add` a `Remove`. Zjištění, které z nich není `null`, představuje platný způsob, jak určit typ zprávy, který se používá, ale lepší způsob je. Generování kódu také vytvořilo `enum ActionOneOfCase` ve třídě `ActionMessage`, která vypadá takto:

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

Vlastnost `ActionCase` na objektu `ActionMessage` lze použít s příkazem `switch` k určení, které pole je nastaveno:

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
> Příkaz `switch` má `default` případ, který zaznamená upozornění, pokud nalezne neznámou hodnotu `ActionOneOfCase`. To může být užitečné pro indikaci, že klient používá novější verzi `.proto` souboru, který přidal další akce. Je to jeden z důvodů, proč je použití `switch` lepší než testování pro `null` ve známých polích.

### <a name="use-fullstocktickerservice-from-a-client-application"></a>Použití FullStockTickerService z klientské aplikace

Existuje jednoduchá aplikace .NET Core 3,0 WPF, která demonstruje použití tohoto složitějšího klienta. Celou aplikaci můžete najít na [GitHubu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).

Klient se používá ve třídě `MainWindowViewModel`, která získá instanci `FullStockTicker.FullStockTickerClient` typu z injektáže vložením závislosti:

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
> Nastavením hodnoty `oneof` pole na zprávu automaticky vymažete všechna pole, která byla nastavena dříve.

Proud odpovědí je zpracováván v metodě `async`. `Task`, kterou vrátí, je držena, aby byla uvolněna při zavření okna:

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

### <a name="client-cleanup"></a>Vyčištění klienta

Po zavření okna a `MainWindowViewModel` je uvolněna (z `Closed` události `MainWindow`), doporučujeme, abyste správně odstranili `AsyncDuplexStreamingCall` objekt. Konkrétně by měla být volána metoda `CompleteAsync` v `RequestStream`, aby se řádně zavřel datový proud na serveru. Tento příklad ukazuje metodu `DisposeAsync` z ukázkového zobrazení-model:

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

Uzavírání datových proudů požadavků umožňuje serveru včas nakládat své vlastní prostředky. To zlepšuje efektivitu a škálovatelnost služeb a zabraňuje výjimkám.

>[!div class="step-by-step"]
>[Předchozí](migrate-request-reply.md)
>[Další](streaming-versus-repeated.md)
