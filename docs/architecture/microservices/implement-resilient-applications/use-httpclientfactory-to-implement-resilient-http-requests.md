---
title: Použití HttpClientFactory k implementaci odolných požadavků HTTP
description: Naučte se používat HttpClientFactory, která je k dispozici od .NET Core 2,1, pro vytváření instancí `HttpClient`, což usnadňuje jejich použití ve svých aplikacích.
ms.date: 08/08/2019
ms.openlocfilehash: 9eff4a01361b3dc6f7471bc012c945d048b9a276
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737744"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Použití HttpClientFactory k implementaci odolných požadavků HTTP

`HttpClientFactory` je objekt pro vytváření dogmatickým, který je k dispozici od .NET Core 2,1, aby se vytvořily <xref:System.Net.Http.HttpClient> instance pro použití ve vašich aplikacích.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problémy s původní třídou HttpClient dostupnou v .NET Core

Původní a dobře známá <xref:System.Net.Http.HttpClient> třída lze snadno použít, ale v některých případech ji nepoužívá mnoho vývojářů.

Jako první problém, zatímco tato třída je na jedno použití, není při použití s příkazem `using` nejlepší volbou, protože i když vyřadíte `HttpClient` objekt, základní soket není hned uvolněn a může způsobit vážný problém s názvem "vyčerpání soketů". Další informace o tomto problému najdete v tématu o tom, [že používáte HttpClient špatné a že se destabilizující váš Blogový příspěvek k vašemu softwaru](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) .

Proto je `HttpClient`, aby se vytvořila instance jednou a znovu používala po celou dobu životnosti aplikace. Vytvoření instance `HttpClient` třídy pro každý požadavek vyčerpá počet soketů, které jsou k dispozici v případě velkého zatížení. Tento problém bude mít za následek `SocketException` chyby. Možné přístupy k vyřešení tohoto problému jsou založené na vytvoření objektu `HttpClient` jako singleton nebo static, jak je vysvětleno v tomto [článku o použití HttpClient](../../../csharp/tutorials/console-webapiclient.md).

Ale existuje druhý problém s `HttpClient`, který můžete mít, když ho použijete jako singleton nebo statický objekt. V tomto případě typ singleton nebo statický `HttpClient` nerespektuje změny DNS, jak je vysvětleno v tomto [problému](https://github.com/dotnet/corefx/issues/11224) v úložišti GitHub/corefx GitHub.

Rozhraní .NET Core 2,1 zavedlo nové `HttpClientFactory`, které lze použít také k implementaci odolných volání HTTP integrací Polly s tím, aby vyřešila zmíněné problémy a zjednodušila správu instancí `HttpClient`.

[Polly](http://www.thepollyproject.org/) je přechodná knihovna pro zpracování chyb, která vývojářům pomáhá přidat odolnost do svých aplikací s využitím některých předdefinovaných zásad v rámci procesu, který je bezpečný pro práci v Fluent a vlákně.

## <a name="what-is-httpclientfactory"></a>Co je HttpClientFactory

`HttpClientFactory` je navržený tak, aby:

- Poskytněte centrální umístění pro pojmenovávání a konfiguraci logických `HttpClient` objektů. Můžete například nakonfigurovat klienta (agenta služeb), který je předem nakonfigurovaný pro přístup k určité mikroslužbě.
- Codify koncept odchozího middleware prostřednictvím delegování obslužných rutin v `HttpClient` a implementace middleware založeného na Polly, který využívá zásady Polly pro zajištění odolnosti.
- `HttpClient` už má koncept delegování obslužných rutin, které by se daly propojit pro odchozí požadavky HTTP. Do továrny zaregistrujete klienty HTTP a pomocí obslužné rutiny Polly můžete použít zásady Polly pro opakování, CircuitBreakers a tak dále.
- Spravujte dobu života `HttpClientMessageHandlers`, abyste se vyhnuli uvedeným problémům nebo problémům, ke kterým může dojít při správě `HttpClient`ch životních cyklů.

> [!NOTE]
> `HttpClientFactory` je úzce spjat s implementací (DI) pro vkládání závislostí v balíčku NuGet `Microsoft.Extensions.DependencyInjection`. Další informace o používání dalších kontejnerů vkládání závislostí naleznete v této [diskuzi GitHubu](https://github.com/aspnet/Extensions/issues/1345).

## <a name="multiple-ways-to-use-httpclientfactory"></a>Několik způsobů použití HttpClientFactory

Existuje několik způsobů, jak můžete v aplikaci `HttpClientFactory` použít:

- Použít `HttpClientFactory` přímo
- Použití pojmenovaných klientů
- Použití typových klientů
- Použít vygenerované klienty

V zájmu zkrácení vám tento návod ukáže i strukturovaný způsob použití `HttpClientFactory`, který se používá pro typové klienty (model agenta služby). Všechny možnosti jsou ale zdokumentováné a aktuálně jsou uvedené v tomto [článku, které pokrývají HttpClientFactory využití](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Jak používat typové klienty s HttpClientFactory

Co je to "Typový klient"? Je to jen `HttpClient`, která je nakonfigurovaná při vkládání pomocí `DefaultHttpClientFactory`.

Následující diagram znázorňuje, jak se používají typové klienty s `HttpClientFactory`:

![Diagram znázorňující, jak se používají typové klienty s HttpClientFactory](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Obrázek 8-4**. Použití HttpClientFactory se zadanými klientskými třídami.

Na výše uvedeném obrázku ClientService vynuťte u (používaný řadičem nebo klientským kódem) používá `HttpClient` vytvořené pomocí registrované `IHttpClientFactory`. Tato továrna přiřadí `HttpClient` `HttpMessageHandler` z fondu, který spravuje. `HttpClient` lze nakonfigurovat pomocí zásad Polly při registraci `IHttpClientFactory` v kontejneru DI pomocí metody rozšíření `AddHttpClient`.

Pokud chcete nakonfigurovat výše uvedenou strukturu, přidejte `HttpClientFactory` do své aplikace tak, že nainstalujete balíček NuGet `Microsoft.Extensions.Http`, který obsahuje metodu rozšíření `AddHttpClient()` pro `IServiceCollection`. Tato metoda rozšíření registruje `DefaultHttpClientFactory` pro použití jako typ singleton pro `IHttpClientFactory`rozhraní. Definuje přechodnou konfiguraci `HttpMessageHandlerBuilder`. Tato obslužná rutina zprávy (objekt`HttpMessageHandler`), která je pořízená z fondu, se používá `HttpClient` vrácená z továrny.

V dalším kódu vidíte, jak `AddHttpClient()` lze použít k registraci typových klientů (agentů služeb), kteří potřebují používat `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Registrace služeb klienta, jak je znázorněno v předchozím kódu, vytvoří `DefaultClientFactory` pro každou službu vytvořit standardní `HttpClient`.

Můžete také přidat konfiguraci specifickou pro instanci v registraci, například nakonfigurovat základní adresu a přidat některé zásady odolnosti, jak je znázorněno v následujícím kódu:

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Podobně jako v tomto příkladu vidíte jednu z výše uvedených zásad v následujícím kódu:

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

### <a name="httpclient-lifetimes"></a>HttpClient doby života

Pokaždé, když dostanete objekt `HttpClient` z `IHttpClientFactory`, vrátí se nová instance. Každý `HttpClient` ale používá `HttpMessageHandler`, který `IHttpClientFactory` se ve fondu a znovu používá, aby se snížila spotřeba prostředků, pokud doba platnosti `HttpMessageHandler`vypršela.

Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje vlastní podkladová připojení HTTP; vytváření dalších obslužných rutin, než je potřeba, může způsobit zpoždění připojení. Některé obslužné rutiny také udržují připojení otevřené po neomezenou dobu, což může zabránit obslužné rutině v rekomunikaci se změnami DNS.

Objekty `HttpMessageHandler` ve fondu mají dobu života, která je doba, po kterou lze znovu použít instanci `HttpMessageHandler` ve fondu. Výchozí hodnota je dvě minuty, ale je možné ji přepsat na typového klienta. Chcete-li jej přepsat, zavolejte `SetHandlerLifetime()` na `IHttpClientBuilder`, který je vrácen při vytváření klienta, jak je znázorněno v následujícím kódu:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Každý typový klient může mít svou vlastní nakonfigurovanou hodnotu životnosti obslužných rutin. Nastavte dobu života na `InfiniteTimeSpan`, aby se zakázala vypršení platnosti obslužné rutiny.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implementujte typové klientské třídy, které používají vložené a nakonfigurované HttpClient

Jako předchozí krok musíte mít definované vaše typové klientské třídy, například třídy v ukázkovém kódu, jako je například "BasketService", "CatalogService", "OrderingService" atd. – typový klient je třída, která přijímá objekt `HttpClient` (vložený prostřednictvím jeho konstruktoru) a používá ho k volání některé vzdálené služby HTTP. Příklad:

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

Typový klient (CatalogService v příkladu) je aktivován pomocí příkazu DI (vkládání závislostí), což znamená, že může přijmout jakoukoli registrovanou službu ve svém konstruktoru kromě HttpClient.

Typový klient je efektivně přechodný objekt, což znamená, že se vytvoří nová instance pokaždé, když je potřeba, a dostane novou `HttpClient` instanci pokaždé, když je vytvořená. Objekty HttpMessageHandler ve fondu však jsou objekty, které jsou opakovaně používány více požadavky HTTP.

### <a name="use-your-typed-client-classes"></a>Použití typových klientských tříd

Nakonec, když máte implementované typové třídy a máte je zaregistrované ve `AddHttpClient()`, můžete je použít všude, kde můžete mít služby, které jsou vloženy do DI. Například v kódu stránky Razor nebo kontroleru webové aplikace MVC, jako v následujícím kódu z eShopOnContainers:

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

Až do tohoto okamžiku, zobrazený kód provádí pouze běžné požadavky HTTP, ale hodnota Magic přichází v následujících částech, kde, stačí, když přidáte zásady a delegujete obslužné rutiny na registrované typové klienty, všechny požadavky HTTP, které má `HttpClient` provádět, se budou chovat s ohledem na odolné zásady, jako jsou třeba opakované pokusy pomocí exponenciálního omezení rychlostiu, přepínacích cyklů nebo jakákoli jiná vlastní obslužná rutina, která implementuje další funkce zabezpečení, jako je například použití ověřovacích tokenů nebo jakékoli jiné vlastní funkce.

## <a name="additional-resources"></a>Další materiály a zdroje informací

- **Používání HttpClientFactory v .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Zdrojový kód HttpClientFactory v úložišti GitHub `aspnet/Extensions`**  
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

- **Polly (odolnost proti chybám .NET a knihovna pro zpracování s přechodnými chybami)**  
  <http://www.thepollyproject.org/>
  
- **Použití HttpClientFactory bez injektáže závislosti (problém GitHubu)**  
  <https://github.com/aspnet/Extensions/issues/1345>

>[!div class="step-by-step"]
>[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)
>[Další](implement-http-call-retries-exponential-backoff-polly.md)
