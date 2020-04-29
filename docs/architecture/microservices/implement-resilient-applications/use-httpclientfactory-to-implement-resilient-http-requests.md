---
title: Použití IHttpClientFactory k implementaci odolných požadavků HTTP
description: Naučte se používat IHttpClientFactory, k dispozici od .NET Core 2,1 pro `HttpClient` vytváření instancí, což usnadňuje jejich použití ve svých aplikacích.
ms.date: 03/03/2020
ms.openlocfilehash: ade26208a931faa456c8e267def2caef7a3f32de
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507296"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Použití IHttpClientFactory k implementaci odolných požadavků HTTP

<xref:System.Net.Http.IHttpClientFactory>je kontraktem `DefaultHttpClientFactory`, který implementuje nástroj dogmatickým Factory, který je k dispozici od .net Core <xref:System.Net.Http.HttpClient> 2,1 pro vytváření instancí, které se mají použít ve vašich aplikacích.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problémy s původní třídou HttpClient dostupnou v .NET Core

Původní a dobře známou <xref:System.Net.Http.HttpClient> třídu lze snadno použít, ale v některých případech ji nepoužívá mnoho vývojářů.

I když tato třída `IDisposable`implementuje, deklaraci a vytvoření instance v `using` rámci příkazu není preferována, protože `HttpClient` když dojde k uvolnění objektu, základní soket není okamžitě uvolněn, což může vést k problému s _vyčerpáním soketu_ . Další informace o tomto problému najdete v blogovém příspěvku, [který používáte HttpClient, a který je destabilizující vašemu softwaru](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Proto `HttpClient` má být vytvořena instance jednou a znovu použita po celou dobu životnosti aplikace. Vytvoření instance `HttpClient` třídy pro každý požadavek vyčerpá počet soketů, které jsou k dispozici v případě velkého zatížení. K tomuto problému dojde v `SocketException` důsledku chyb. Možné přístupy k vyřešení tohoto problému jsou založené na vytvoření `HttpClient` objektu jako singleton nebo static, jak je vysvětleno v tomto [článku o použití HttpClient](../../../csharp/tutorials/console-webapiclient.md). Může to být dobré řešení pro krátkodobé konzolové aplikace nebo podobné, které se spouští několikrát denně.

Dalším problémem, ve kterém se vývojáři spouštějí, je použití sdílené instance `HttpClient` v dlouhotrvajících procesech. V situaci, kdy je instance HttpClient vytvořena jako typ singleton nebo statický objekt, se nedokáže zpracovat změny DNS, jak je popsáno v tomto [problému](https://github.com/dotnet/runtime/issues/18348) úložiště GitHub pro dotnet/modul runtime.

Problém ale není `HttpClient` v zásadě za se, ale s [výchozím konstruktorem pro HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), protože vytvoří novou konkrétní instanci <xref:System.Net.Http.HttpMessageHandler>, která je v tom, který má *vyčerpání soketů* a DNS změny výše uvedené.

Rozhraní .NET Core 2,1 představilo `HttpClient` <xref:System.Net.Http.IHttpClientFactory> rozhraní, které se dá použít ke konfiguraci a vytváření `HttpClient` instancí v aplikaci prostřednictvím injektáže závislostí (di), aby vyřešilo výše uvedené problémy a aby bylo možné spravovat instance. Poskytuje také rozšíření pro middleware založené na Polly, která umožňují využít výhod delegování obslužných rutin v HttpClient.

[Polly](http://www.thepollyproject.org/) je dočasná knihovna pro zpracování chyb, která vývojářům pomáhá zajistit odolnost proti svým aplikacím pomocí některých předdefinovaných zásad, které jsou bezpečné pro práci v Fluent a vlákně.

## <a name="benefits-of-using-ihttpclientfactory"></a>Výhody použití IHttpClientFactory

Aktuální implementace <xref:System.Net.Http.IHttpClientFactory>, která také implementuje <xref:System.Net.Http.IHttpMessageHandlerFactory>, nabízí následující výhody:

- Poskytuje centrální umístění pro pojmenovávání a konfiguraci `HttpClient` logických objektů. Můžete například nakonfigurovat klienta (agenta služeb), který je předem nakonfigurovaný pro přístup k určité mikroslužbě.
- Codify koncept odchozího middleware prostřednictvím delegování obslužných rutin `HttpClient` v a implementace middleware založeného na Polly, který využívá zásady Polly pro zajištění odolnosti.
- `HttpClient`již má koncepci delegování obslužných rutin, které by mohly být propojeny pro odchozí požadavky HTTP. Můžete zaregistrovat klienty HTTP do továrny a pomocí obslužné rutiny Polly použít zásady Polly pro opakování, CircuitBreakers a tak dále.
- Spravujte dobu života, <xref:System.Net.Http.HttpMessageHandler> abyste se vyhnuli uvedeným problémům nebo problémům, ke `HttpClient` kterým může dojít při správě životního cyklu.

> [!TIP]
> `HttpClient` Instance vložené pomocí di mohou být odstraněny bezpečně, protože přidružený `HttpMessageHandler` je spravováno objektem pro vytváření. Vzhledem k tomu, že vložené `HttpClient` instance jsou *vymezené* z di perspektivy.

> [!NOTE]
> Implementace `IHttpClientFactory` (`DefaultHttpClientFactory`) je úzce svázána s implementací di v balíčku `Microsoft.Extensions.DependencyInjection` NuGet. Další informace o použití jiných kontejnerů DI najdete v této [diskuzi na GitHubu](https://github.com/dotnet/extensions/issues/1345).

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Několik způsobů použití IHttpClientFactory

V aplikaci můžete použít `IHttpClientFactory` několik způsobů:

- Základní použití
- Použití pojmenovaných klientů
- Použití typových klientů
- Použít vygenerované klienty

Pro účely zkrácení vám tento návod ukáže, jak se používá `IHttpClientFactory`, aby bylo možné použít typové klienty (model agenta služby). Všechny možnosti jsou však zdokumentovány a jsou aktuálně uvedeny v tomto [článku, který `IHttpClientFactory` se týká využití](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Jak používat typové klienty s IHttpClientFactory

Co je to "Typový klient"? Je to jenom ta `HttpClient` , která je předem nakonfigurovaná pro konkrétní použití. Tato konfigurace může zahrnovat konkrétní hodnoty, jako je základní server, hlavičky protokolu HTTP nebo časové limity.

Následující diagram znázorňuje, jak se používají typové klienty s `IHttpClientFactory`:

![Diagram znázorňující, jak se používají typové klienty s IHttpClientFactory](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Obrázek 8-4**. Použití `IHttpClientFactory` s typovými třídami klienta.

Na výše uvedeném obrázku, a `ClientService` (používá ho řadič nebo kód klienta), používá `HttpClient` vytvořenou registrovanou. `IHttpClientFactory` Tento objekt pro vytváření `HttpMessageHandler` přiřadí z fondu do `HttpClient`. `HttpClient` Lze nakonfigurovat zásady Polly při registraci `IHttpClientFactory` v kontejneru di s metodou <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>rozšíření.

Pokud chcete nakonfigurovat výše uvedenou strukturu, <xref:System.Net.Http.IHttpClientFactory> přidejte ji do své aplikace tak `Microsoft.Extensions.Http` , že nainstalujete balíček <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> NuGet, který <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>obsahuje metodu rozšíření pro. Tato metoda rozšíření registruje interní `DefaultHttpClientFactory` třídu, která se má použít jako typ singleton pro `IHttpClientFactory`rozhraní. Definuje přechodnou konfiguraci pro <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>. Tato obslužná rutina<xref:System.Net.Http.HttpMessageHandler> zprávy (objekt), která je pořízena z fondu `HttpClient` , je používána vrácenou z továrny.

V dalším kódu vidíte, jak `AddHttpClient()` se dá použít k registraci typových klientů (agentů služeb), které je potřeba použít `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Registrace služeb klienta, jak je znázorněno v předchozím kódu, vytvoří `DefaultClientFactory` pro každou službu `HttpClient` Standard.

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

Pokaždé `IHttpClientFactory`, když získáte `HttpClient` objekt z, je vrácena nová instance. Každá z `HttpClient` `HttpMessageHandler` `IHttpClientFactory` nich ale používá fond a znovu ho používá ke snížení spotřeby prostředků, pokud `HttpMessageHandler`doba života ještě nevypršela.

Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje vlastní podkladová připojení HTTP; vytváření dalších obslužných rutin, než je potřeba, může způsobit zpoždění připojení. Některé obslužné rutiny také udržují připojení otevřené po neomezenou dobu, což může zabránit obslužné rutině v rekomunikaci se změnami DNS.

`HttpMessageHandler` Objekty ve fondu mají dobu života, která je doba, po kterou lze `HttpMessageHandler` instanci ve fondu znovu použít. Výchozí hodnota je dvě minuty, ale je možné ji přepsat na typového klienta. Chcete-li ho přepsat `SetHandlerLifetime()` , zavolejte <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> na to, které je vráceno při vytváření klienta, jak je znázorněno v následujícím kódu:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Každý typový klient může mít svou vlastní nakonfigurovanou hodnotu životnosti obslužných rutin. Nastavte dobu života na `InfiniteTimeSpan` zakázat vypršení platnosti obslužné rutiny.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implementujte typové klientské třídy, které používají vložené a nakonfigurované HttpClient

Jako předchozí krok musíte mít definované vaše typové klientské třídy, například třídy v ukázkovém kódu, jako je například "BasketService", "CatalogService", "OrderingService" atd. – typový klient je třída, která přijímá `HttpClient` objekt (vložený prostřednictvím jeho konstruktoru) a používá ho k volání některé vzdálené služby HTTP. Příklad:

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

Typový klient (`CatalogService` v příkladu) je aktivován pomocí příkazu di (vkládání závislostí), což znamená, že může přijmout jakoukoli registrovanou službu ve svém konstruktoru, kromě `HttpClient`.

Typový klient je efektivně přechodný objekt, což znamená, že se vytvoří nová instance pokaždé, když je potřeba, a při každém sestavení dostane novou `HttpClient` instanci. `HttpMessageHandler` Objekty ve fondu však jsou objekty, které jsou opakovaně používány více `HttpClient` instancemi.

### <a name="use-your-typed-client-classes"></a>Použití typových klientských tříd

Nakonec, když máte implementované typové třídy a máte je zaregistrované a nakonfigurované `AddHttpClient()`pomocí, můžete je použít všude, kde můžete mít služby, které jsou vloženy do di. Například v kódu stránky Razor nebo kontroleru webové aplikace MVC, jako v následujícím kódu z eShopOnContainers:

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

Až do tohoto okamžiku, zobrazený kód provádí pouze běžné požadavky HTTP, ale hodnota Magic přichází v následujících částech, kde, stačí, když přidáte zásady a delegujete obslužné rutiny na registrované typové klienty, všechny požadavky HTTP, které se mají provést, `HttpClient` se budou chovat s ohledem na odolné zásady, jako jsou opakované pokusy pomocí exponenciálního omezení rychlostiu, vypínačů okruhu nebo jakákoli jiná vlastní obslužná rutina pro implementaci dalších funkcí zabezpečení, jako je například použití ověřovacích tokenů nebo jakékoli jiné vlastní funkce.

## <a name="additional-resources"></a>Další materiály a zdroje informací

- **Používání HttpClientFactory v .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Zdrojový kód HttpClientFactory v úložišti `dotnet/extensions` GitHubu**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (odolnost proti chybám .NET a knihovna pro zpracování s přechodnými chybami)**  
  <http://www.thepollyproject.org/>
  
- **Použití IHttpClientFactory bez injektáže závislosti (problém GitHubu)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Předchozí](implement-resilient-entity-framework-core-sql-connections.md)
>[Další](implement-http-call-retries-exponential-backoff-polly.md)
