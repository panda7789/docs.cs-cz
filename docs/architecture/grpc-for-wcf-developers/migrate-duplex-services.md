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
# <a name="migrate-wcf-duplex-services-to-grpc"></a>Migrace duplexních služeb WCF na gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Teď, když jsou na začátku základní koncepty, Tato část se bude pohlížet na složitější *streamování* gRPC Services.

V Windows Communication Foundation (WCF) existuje několik způsobů použití duplexních služeb. Některé služby jsou iniciovány klientem a poté jsou z tohoto serveru streamovaná data. Jiné plně duplexní služby můžou v dokumentaci WCF zahrnovat nepřetržitou obousměrnou komunikaci, například klasický příklad kalkulačky. Tato kapitola bude mít dvě možné implementace služby WCF "burzovních impulsů" a migruje je do gRPC: jedno pomocí služby RPC pro streamování serveru a druhý pomocí protokolu RPC s obousměrným datovým proudem.

## <a name="server-streaming-rpc"></a>RPC streamování serveru

V [ukázkovém řešení SIMPLESTOCKTICKER WCF](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)je *SimpleStockPriceTicker*duplexní služba, kde klient spouští připojení se seznamem burzovních symbolů a server používá *rozhraní zpětného volání* k posílání aktualizací. bude k dispozici. Klient implementuje rozhraní, aby reagoval na volání ze serveru.

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

Služba má jedinou metodu bez návratového typu, protože bude používat rozhraní `ISimpleStockTickerCallback` zpětného volání k posílání dat klientovi v reálném čase.

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

Definice služby potřebuje dvě zprávy: jednu pro požadavek a jednu pro datový proud. Služba vrátí datový proud `StockTickerUpdate` zprávy `stream` pomocí klíčového slova ve své `return` deklaraci. Doporučuje se přidat `Timestamp` do aktualizace, abyste zobrazili přesný čas změny ceny.

#### <a name="simple_stock_tickerproto"></a>simple_stock_ticker.

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

### <a name="implement-the-simplestockticker"></a>Implementace rozhraní SimpleStockTicker

Znovu použijte napodobeninu `StockPriceSubscriber` z projektu WCF zkopírováním tří tříd `TraderSys.StockMarket` z knihovny tříd do nové knihovny tříd .NET Standard v cílovém řešení. Chcete-li lépe dodržovat osvědčené postupy `Factory` , přidejte typ pro vytvoření instancí a `IStockPriceSubscriberFactory` Zaregistrujte se službou pro vkládání závislostí ve ASP.NET Core.

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

Jak vidíte, i když deklarace v `.proto` souboru říká, že metoda vrátí `StockTickerUpdate` datový proud zpráv, ve skutečnosti vrátí Vanilla `Task`. Úloha vytvoření datového proudu je zpracována generovaným kódem a běhovými knihovnami gRPC, které poskytují `IServerStreamWriter<StockTickerUpdate>` datový proud odpovědí připravený k použití.

Na rozdíl od služby duplexní služba WCF, kde je instance třídy služby aktivní, když je připojení otevřené, služba gRPC použije vrácenou úlohu, aby službu udržovala aktivní. Úloha by neměla být dokončena, dokud nebude připojení ukončeno.

Služba může říct, že klient uzavřel připojení pomocí `CancellationToken` `ServerCallContext`z. Jednoduchá statická metoda, `AwaitCancellation`která se používá k vytvoření úlohy, která se dokončí při zrušení tokenu.

V metodě, potom Get a přidejte obslužnou rutinu události, která zapisuje do datového proudu odpovědí. `StockPriceSubscriber` `Subscribe` Pak počkejte, než se připojení zavře, a teprve `subscriber` potom ho vyodstraňte, aby nedošlo k pokusu o zápis dat do zavřeného datového proudu.

`WriteUpdateAsync` Metoda máblok,který`try` zpracovává všechny chyby, ke kterým může dojít při zápisu zprávy do datového proudu. / `catch` To je důležitý aspekt trvalého připojení přes sítě, které by mohlo být v jakémkoli milisekundě přerušeno, ať už úmyslně nebo z důvodu selhání.

### <a name="using-the-stocktickerservice-from-a-client-application"></a>Použití rozhraní StockTickerService z klientské aplikace

Použijte stejný postup v předchozí části a vytvořte ze `.proto` souboru knihovnu klientských tříd sdílení. V ukázce je k dispozici Konzolová aplikace .NET Core 3,0, která ukazuje, jak používat klienta.

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

V tomto případě `Subscribe` není metoda na vygenerovaném klientovi asynchronní. Stream se vytvoří a dá se použít hned, protože jeho `MoveNext` metoda je asynchronní a při prvním volání se nebudete moct dokončit, dokud připojení není aktivní.

Datový proud se předává asynchronní `DisplayAsync` metodě. aplikace pak počká, až uživatel stiskne klávesu, a pak tuto `DisplayAsync` metodu zruší a před ukončením počká, než se úkol dokončí.

> [!NOTE]
> Tento kód používá novou C# syntaxi 8 "using Declaration" k Dispose datového proudu a kanálu při `Main` ukončení metody. Jedná se o malou změnu, ale je to dobrý čas, který omezí odsazení a prázdné řádky.

#### <a name="consume-the-stream"></a>Využití streamu

WCF používá rozhraní zpětného volání, aby mohl server volat metody přímo na straně klienta. datové proudy gRPC fungují jinak. Klient prochází vráceným datovým proudem a zpracovává zprávy stejným způsobem, jako kdyby byly vráceny z místní metody vracející `IEnumerable`.

Typ funguje `MoveNext` podobně jako `Current` : existuje metoda, která vrátí hodnotu true, dokud bude existovat více dat, a vlastnost, která vrací nejnovější hodnotu. `IEnumerator<T>` `IAsyncStreamReader<T>` Jediným rozdílem je, že `MoveNext` metoda `Task<bool>` vrací místo pouze a `bool`. Metoda rozšíření zalomí datový proud C# ve standardu 8 `IAsyncEnumerable` , který lze použít s novou `await foreach` syntaxí. `ReadAllAsync`

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
> Oddíl na [klientských knihovnách](client-libraries.md#iobservable) na konci této kapitoly vyhledá, jak přidat rozšiřující metodu a třídy, které se zabalí `IAsyncStreamReader<T>` do `IObservable<T>` pro vývojáře pomocí reaktivních programovacích vzorů.

Znovu buďte opatrní, abyste zachytili výjimky z důvodu možnosti selhání sítě a také <xref:System.OperationCanceledException> to, že bude nevyhnutelně vyvoláno, protože kód <xref:System.Threading.CancellationToken> používá k přerušení smyčky. Typ má spoustu užitečných informací o chybách modulu runtime gRPC, `StatusCode`včetně. `RpcException` Další informace najdete v části [ *zpracování chyb* v části 4.](error-handling.md)

## <a name="bidirectional-streaming"></a>Obousměrný streamování

Plně duplexní služba WCF umožňuje asynchronní zasílání zpráv v reálném čase v obou směrech. V příkladu streamování serveru spustí klient požadavek a potom obdrží datový proud aktualizací. Lepší verze této služby umožňuje klientovi přidávat a odebírat zásoby ze seznamu bez nutnosti zastavit a vytvořit nové předplatné. Tato funkce je implementovaná v [ukázkovém řešení FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).

`IFullStockTickerService` Rozhraní poskytuje tři metody:

- `Subscribe`spustí připojení.
- `AddSymbol`Přidá burzovní symbol, který se má sledovat.
- `RemoveSymbol`Odebere symbol ze sledovaného seznamu.

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

Implementace tohoto modelu v gRPC je méně jednoduchá, protože nyní existují dva proudy dat s předávanými zprávami: jeden od klienta k serveru a druhý ze serveru do klienta. Nelze použít více metod pro implementaci operace přidání a odebrání, ale více než jeden typ zprávy lze předat jednomu datovému proudu pomocí `Any` typu nebo `oneof` klíčového slova, které bylo pokryto v [kapitole 3](protobuf-any-oneof.md).

V případě, že existuje určitá sada typů, které jsou přijatelné, představuje lepší `oneof` způsob, jak jít. Použijte, který může obsahovat `AddSymbolRequest` buď nebo `RemoveSymbolRequest`. `ActionMessage`

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

Deklarace služby streamování obousměrného přenosu dat, která přebírá `ActionMessage` proud zpráv

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

Implementace této služby je podobná předchozímu příkladu, s výjimkou `Subscribe` prvního parametru metody je `IAsyncStreamReader<ActionMessage>`nyní, který lze použít ke zpracování `Add` požadavků a `Remove` .

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

Třída, kterou gRPC vygenerovala pro nás garantuje, že je možné `Add` nastavit `Remove` jenom jednu z vlastností a a najít, která z `null` nich není platným způsobem, jak zjistit, který typ zprávy se používá, ale existuje lepší způsob, jak to najít. `ActionMessage` . Generování kódu také vytvořilo `enum ActionOneOfCase` `ActionMessage` ve třídě, což vypadá takto:

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

Vlastnost `ActionCase` objektu`ActionMessage` lzepoužítspříkazemkurčení,které`switch` pole je nastaveno.

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
> Příkaz obsahuje případ, který zaznamená upozornění, pokud je zjištěna neznámá `ActionOneOfCase` hodnota. `default` `switch` To může být užitečné v případě, že klient používá novější verzi `.proto` souboru, která přidala další akce. To je jeden z důvodů, proč `switch` použití je lepší než `null` testování u známých polí.

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a>Použití FullStockTickerService z klientské aplikace

Existuje jednoduchá aplikace .NET Core 3,0 WPF, která předvádí použití tohoto složitějšího klienta. Úplnou aplikaci najdete [na GitHubu](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).

Klient se používá ve `MainWindowViewModel` třídě, která získá instanci `FullStockTicker.FullStockTickerClient` typu z injektáže závislosti.

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

Objekt vrácený `client.Subscribe()` metodou je nyní instancí typu `AsyncDuplexStreamingCall<TRequest, TResponse>`knihovny gRPC, která poskytuje `RequestStream` pro `ResponseStream` odeslání požadavků na server a pro zpracování odpovědí.

Datový proud požadavku se používá z některých metod `ICommand` WPF k přidávání a odebírání symbolů. Pro každou operaci nastavte příslušné pole `ActionMessage` objektu:

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
> Nastavení hodnoty `oneof` pole u zprávy automaticky vymaže všechna pole, která byla dříve nastavena.

Proud odpovědí je zpracováván v `async` metodě `Task` a vrátí se, aby byla uvolněna při zavření okna.

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

`MainWindowViewModel` Když je okno zavřeno a je vyřazeno ( `Closed` z události `MainWindow`), doporučujeme, abyste `AsyncDuplexStreamingCall` objekt správně odstranili. Konkrétně `CompleteAsync` `RequestStream` by měla být volána metoda na, aby se řádně zavřel datový proud na serveru. Následující příklad ukazuje `DisposeAsync` metodu z ukázkového zobrazení-model:

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
