---
title: Použití nástroje IHttpClientFactory k implementaci odolných požadavků HTTP
description: Naučte se používat IHttpClientFactory, který je k `HttpClient` dispozici od .NET Core 2.1, pro vytváření instancí, což usnadňuje použití ve vašich aplikacích.
ms.date: 03/03/2020
ms.openlocfilehash: 088fb6c7e10ad656247ee4065da5c13d383b2cf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847216"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Použití nástroje IHttpClientFactory k implementaci odolných požadavků HTTP

<xref:System.Net.Http.IHttpClientFactory>je smlouva implementovaná společností `DefaultHttpClientFactory`, umíněnou továrnou, která je <xref:System.Net.Http.HttpClient> k dispozici od rozhraní .NET Core 2.1, pro vytváření instancí, které mají být použity ve vašich aplikacích.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problémy s původní třídou HttpClient dostupnou v jádru rozhraní .NET

Původní a dobře <xref:System.Net.Http.HttpClient> známé třídy lze snadno použít, ale v některých případech není správně používán mnoha vývojáři.

Zatímco tato třída `IDisposable`implementuje , deklarování `using` a vytváření instancí v rámci příkazu není upřednostňována, protože když `HttpClient` je objekt vyřazen, základní soket není okamžitě uvolněna, což může vést k problému vyčerpání _soketu._ Další informace o tomto problému naleznete v příspěvku blogu [Používáte httpclient špatně a destabilizuje váš software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Proto `HttpClient` je určen k vytvoření instance jednou a znovu použít po celou dobu životnosti aplikace. Vytvoření instance `HttpClient` třídy pro každý požadavek vyčerpá počet zásuvek, které jsou k dispozici při velkém zatížení. Tento problém bude `SocketException` mít za následek chyby. Možné přístupy k řešení tohoto problému `HttpClient` jsou založeny na vytvoření objektu jako singleton nebo statické, jak je vysvětleno v tomto [článku společnosti Microsoft o využití httpclient](../../../csharp/tutorials/console-webapiclient.md). To může být dobrým řešením pro krátkodobé konzolové aplikace nebo podobné aplikace, které jsou spuštěny několikrát denně.

Dalším problémem, který vývojáři spustit `HttpClient` je při použití sdílené instance v dlouho běžící procesy. V situaci, kdy httpclient je vytvořena instance jako singleton nebo statický objekt, nedokáže zpracovat změny DNS, jak je popsáno v tomto [vydání](https://github.com/dotnet/corefx/issues/11224) úložiště Dotnet/corefx GitHub.

Problém však není ve `HttpClient` skutečnosti s sám o sobě, ale s [výchozím konstruktorem pro HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), protože vytvoří novou konkrétní instanci <xref:System.Net.Http.HttpMessageHandler>, což je ten, který má vyčerpání *soketů* a dns změny problémy uvedené výše.

Chcete-li řešit výše uvedené `HttpClient` problémy a aby instance spravovatelné, .NET Core 2.1 <xref:System.Net.Http.IHttpClientFactory> představil `HttpClient` rozhraní, které lze použít ke konfiguraci a vytvoření instance v aplikaci prostřednictvím vkládání závislostí (DI). Poskytuje také rozšíření pro middleware založené na Polly využít delegování obslužné rutiny v HttpClient.

[Polly](http://www.thepollyproject.org/) je knihovna pro zpracování přechodných chyb, která vývojářům pomáhá přidávat odolnost k aplikacím pomocí některých předdefinovaných zásad plynulým způsobem a bezpečným pro přístup z více vláken.

## <a name="benefits-of-using-ihttpclientfactory"></a>Výhody používání ihttpclientfactory

Současná implementace <xref:System.Net.Http.IHttpClientFactory>, která <xref:System.Net.Http.IHttpMessageHandlerFactory>také implementuje , nabízí následující výhody:

- Poskytuje centrální umístění pro pojmenování `HttpClient` a konfiguraci logických objektů. Můžete například nakonfigurovat klienta (agenta služby), který je předem nakonfigurován pro přístup k určité mikroslužbě.
- Kodifikovat koncept odchozí middleware prostřednictvím delegování manipulátory a `HttpClient` provádění Polly-založené middleware využít polly politiky pro odolnost.
- `HttpClient`již má koncept delegování obslužné rutiny, které by mohly být propojeny pro odchozí požadavky HTTP. Klienty HTTP můžete zaregistrovat do továrny a můžete použít polly obslužnou rutinu k použití polly zásad pro opakování, jističe a tak dále.
- Spravujte životnost, <xref:System.Net.Http.HttpMessageHandler> abyste se vyhnuli uvedeným problémům `HttpClient` nebo problémům, které mohou nastat při správě životnosti sami.

> [!TIP]
> Instance `HttpClient` injekčně DI, lze zlikvidovat bezpečně, protože přidružené `HttpMessageHandler` je spravována factory. Jako ve skutečnosti injekčně `HttpClient` instance jsou *Scoped* z hlediska DI.

> [!NOTE]
> Implementace `IHttpClientFactory` (`DefaultHttpClientFactory`) je úzce vázána na `Microsoft.Extensions.DependencyInjection` implementaci DI v balíčku NuGet. Další informace o používání jiných kontejnerů DI najdete v této [diskusi githubu](https://github.com/dotnet/extensions/issues/1345).

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Více způsobů použití ihttpclientfactory

Existuje několik způsobů, které `IHttpClientFactory` můžete použít v aplikaci:

- Základní použití
- Použít pojmenované klienty
- Použít zadané klienty
- Použít generované klienty

Z důvodu stručnosti tento návod ukazuje nejstrukturovanější způsob `IHttpClientFactory`použití , který je použití zadali klienty (Service Agent vzor). Všechny možnosti jsou však zdokumentovány a jsou aktuálně uvedeny v tomto [článku týkající se `IHttpClientFactory` použití](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Použití zadalicích klientů s iHttpClientFactory

Takže, co je "napsaná klientka"? Je to `HttpClient` jen, který je předem nakonfigurován pro určité konkrétní použití. Tato konfigurace může obsahovat určité hodnoty, jako je například základní server, hlavičky HTTP nebo časové výběhy.

Následující diagram znázorňuje, jak `IHttpClientFactory`jsou klienti typem používáni s :

![Diagram znázorňující, jak jsou zadali klienti s IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Obrázek 8-4**. Použití `IHttpClientFactory` s třídami Typed Client.

Ve výše uvedenébitové bitové `ClientService` kopii používá (používaný řadičem nebo klientským kódem) `HttpClient` vytvořený registrovaným `IHttpClientFactory`. Tato továrna `HttpMessageHandler` přiřadí z `HttpClient`fondu do . Lze `HttpClient` nakonfigurovat s polly zásady při `IHttpClientFactory` registraci v kontejneru <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>DI s metodou rozšíření .

Chcete-li nakonfigurovat <xref:System.Net.Http.IHttpClientFactory> výše uvedenou strukturu, přidejte do aplikace instalací balíčku `Microsoft.Extensions.Http` NuGet, který obsahuje metodu <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> rozšíření pro <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>aplikaci . Tato metoda rozšíření registruje vnitřní `DefaultHttpClientFactory` třídy, které mají `IHttpClientFactory`být použity jako singleton pro rozhraní . Definuje přechodnou konfiguraci pro <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>. Tato obslužná rutina zprávy (<xref:System.Net.Http.HttpMessageHandler> `HttpClient` objekt), převzata z fondu, se používá vrácené z výroby.

V dalším kódu můžete vidět, jak `AddHttpClient()` lze zaregistrovat zadané klienty (service `HttpClient`agents), které je třeba použít .

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Registrace klientských služeb, jak je znázorněno `DefaultClientFactory` v `HttpClient` předchozím kódu, vytvoří vytvořit standard pro každou službu.

Můžete také přidat konfiguraci specifickou pro instanci v registraci, například ke konfiguraci základní adresy a přidat některé zásady odolnosti proti chybám, jak je znázorněno v následujícím kódu:

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Jen pro příklad, můžete vidět jednu z výše uvedených zásad v dalším kódu:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

Další podrobnosti o používání Polly najdete v [dalším článku](implement-http-call-retries-exponential-backoff-polly.md).

### <a name="httpclient-lifetimes"></a>Životnost httpclientu

Pokaždé, když `HttpClient` získáte objekt `IHttpClientFactory`z , je vrácena nová instance. Ale `HttpClient` každý `HttpMessageHandler` používá, který je sdružený a znovu použít `IHttpClientFactory` `HttpMessageHandler`ke snížení spotřeby prostředků, tak dlouho, dokud 's životnost nevypršela.

Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje vlastní základní připojení HTTP; vytvoření více obslužných rutin, než je nutné, může mít za následek zpoždění připojení. Některé obslužné rutiny také udržují připojení otevřená po neomezenou dobu, což může zabránit tomu, aby obslužná rutina reagovala na změny DNS.

Objekty `HttpMessageHandler` ve fondu mají životnost, která je doba, po kterou lze `HttpMessageHandler` znovu použít instanci ve fondu. Výchozí hodnota je dvě minuty, ale může být přepsána na zadaného klienta. Chcete-li jej `SetHandlerLifetime()` přepsat, <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> volejte na to, který je vrácen při vytváření klienta, jak je znázorněno v následujícím kódu:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Každý zadaný klient může mít vlastní nakonfigurovanou hodnotu životnosti obslužné rutiny. Nastavte životnost `InfiniteTimeSpan` zakázat vypršení platnosti obslužné rutiny.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implementace tříd zadaného klienta, které používají vložený a nakonfigurovaný httpclient

Jako předchozí krok musíte mít zadané třídy klienta definované, jako jsou třídy v ukázkovém kódu, jako je "BasketService", "CatalogService", "OrderingService", atd. – Typovaný klient je třída, která přijímá `HttpClient` objekt (vložený prostřednictvím jeho konstruktoru) a používá jej k volání některé vzdálené služby HTTP. Například:

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take,
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl,
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

Typed Client`CatalogService` ( v příkladu) je aktivován DI (Vkládání závislostí), což znamená, že může `HttpClient`přijmout všechny registrované služby v jeho konstruktoru, kromě .

Typed Client je efektivně přechodný objekt, což znamená, že nová instance je vytvořena pokaždé, `HttpClient` když je potřeba, a obdrží novou instanci pokaždé, když je vytvořena. Objekty `HttpMessageHandler` ve fondu jsou však objekty, `HttpClient` které jsou znovu použity více instancí.

### <a name="use-your-typed-client-classes"></a>Použití tříd Zadaného klienta

Nakonec, jakmile budete mít zadané třídy implementovány `AddHttpClient()`a mít je registrovány a nakonfigurovány s , můžete je použít všude tam, kde můžete mít služby injekčně DI. Například v kódu stránky Razor nebo řadiči webové aplikace MVC, jako v následujícím kódu z eShopOnContainers:

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) =>
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied,
                                               int? TypesFilterApplied,
                                               int? page,
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0,
                                                            itemsPage,
                                                            BrandFilterApplied,
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

Až do tohoto okamžiku, zobrazený kód je pouze provádění pravidelných požadavků http, ale 'magie' přichází v následujících částech, kde pouhým přidáním zásad a delegování obslužné rutiny na registrované zadané klienty, všechny požadavky HTTP, které `HttpClient` mají být provedeny, se budou chovat s ohledem na odolné zásady, jako jsou opakované pokusy s exponenciálním vypnutím, jističi nebo jinými vlastními delegujícími obslužnými rutinami pro implementaci dalších funkcí zabezpečení, jako je použití auth tokenů nebo jakékoli jiné vlastní funkce.

## <a name="additional-resources"></a>Další zdroje

- **Použití httpclientfactory v jádru rozhraní .NET**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Zdrojový kód HttpClientFactory `dotnet/extensions` v úložišti GitHub**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (knihovna odolnosti a zpracování přechodných chyb)**  
  <http://www.thepollyproject.org/>
  
- **Použití IHttpClientFactory bez vkládání závislostí (problém GitHubu)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Předchozí](implement-resilient-entity-framework-core-sql-connections.md)
>[další](implement-http-call-retries-exponential-backoff-polly.md)
