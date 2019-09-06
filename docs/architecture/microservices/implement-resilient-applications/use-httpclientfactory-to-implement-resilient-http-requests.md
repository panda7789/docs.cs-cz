---
title: Použití HttpClientFactory k implementaci odolných požadavků HTTP
description: Naučte se používat HttpClientFactory, k dispozici od .NET Core 2,1 pro `HttpClient` vytváření instancí, což usnadňuje jejich použití ve svých aplikacích.
ms.date: 01/07/2019
ms.openlocfilehash: 68c841a6ba69a94eff420233124cf00fec506502
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296038"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Použití HttpClientFactory k implementaci odolných požadavků HTTP

`HttpClientFactory`je dogmatickým továrna, která je k dispozici od .NET Core <xref:System.Net.Http.HttpClient> 2,1, pro vytváření instancí, které se mají použít ve vašich aplikacích.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problémy s původní třídou HttpClient dostupnou v .NET Core

Původní a dobře známou třídu [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) lze snadno použít, ale v některých případech ji nepoužívá mnoho vývojářů. 

Jako první problém, zatímco tato třída je na jedno použití, není při použití `using` s příkazem nejvhodnější volbou, protože i když `HttpClient` vyřadíte objekt, základní soket není hned uvolněn a může způsobit vážný problém s názvem ' Sockets vyčerpání. Další informace o tomto problému najdete v tématu o tom, [že používáte HttpClient špatné a že se destabilizující váš Blogový příspěvek k vašemu softwaru](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) .

`HttpClient` Proto má být vytvořena instance jednou a znovu použita po celou dobu životnosti aplikace. Vytvoření instance třídy pro každý požadavek vyčerpá počet soketů, které jsou k dispozici v případě velkého zatížení. `HttpClient` K tomuto problému dojde v `SocketException` důsledku chyb. Možné přístupy k vyřešení tohoto problému jsou založené na vytvoření `HttpClient` objektu jako singleton nebo static, jak je vysvětleno v tomto [článku o použití HttpClient](/dotnet/csharp/tutorials/console-webapiclient). 

Ale existuje druhý problém s `HttpClient` tím, že ho můžete mít, když ho použijete jako singleton nebo statický objekt. V tomto případě typ singleton nebo static `HttpClient` nerespektuje změny DNS, jak je vysvětleno v tomto problému v [úložišti GitHub .NET Core](https://github.com/dotnet/corefx/issues/11224). 

Za účelem vyřešení těchto zmíněných problémů a zjednodušení správy `HttpClient` instancí .NET Core 2,1 zavádí nový `HttpClientFactory` , který lze použít také k implementaci odolných volání http integrací Polly s IT.   

## <a name="what-is-httpclientfactory"></a>Co je HttpClientFactory

`HttpClientFactory`je navrženo pro:

- Poskytněte centrální umístění pro pojmenovávání a konfiguraci logických HttpClients. Můžete například nakonfigurovat klienta (agenta služeb), který je předem nakonfigurovaný pro přístup k určité mikroslužbě.
- Codify koncept odchozího middleware prostřednictvím delegování obslužných rutin `HttpClient` v a implementace middleware založeného na Polly, který využívá zásady Polly pro zajištění odolnosti.
- `HttpClient`již má koncepci delegování obslužných rutin, které by mohly být propojeny pro odchozí požadavky HTTP. Do továrny zaregistrujete klienty http a můžete použít obslužnou rutinu Polly, která umožňuje použití zásad Polly pro opakování, CircuitBreakers atd.
- Spravujte dobu života HttpClientMessageHandlers, abyste se vyhnuli uvedeným problémům nebo problémům, ke `HttpClient` kterým může dojít při správě životního cyklu. 

## <a name="multiple-ways-to-use-httpclientfactory"></a>Několik způsobů použití HttpClientFactory

V aplikaci můžete použít `HttpClientFactory` několik způsobů:

- Použít `HttpClientFactory` přímo
- Použití pojmenovaných klientů
- Použití typových klientů
- Použít vygenerované klienty

Pro účely zkrácení tento návod ukazuje, jak používat `HttpClientFactory` , aby používal typové klienty (vzor agenta služby), ale všechny možnosti jsou zdokumentovány a jsou aktuálně uvedeny v tomto [článku týkajícím se použití HttpClientFactory](/aspnet/core/fundamentals/http-requests?#consumption-patterns).  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Jak používat typové klienty s HttpClientFactory

Co je to "Typový klient"? Je to jenom `HttpClient` ta, která je nakonfigurovaná při vložení `DefaultHttpClientFactory`pomocí.

Následující diagram znázorňuje, jak se používají typové klienty s `HttpClientFactory`:

![ClientService vynuťte u (používaný řadičem nebo klientským kódem) používá HttpClient vytvořené registrovaným IHttpClientFactory. Tato továrna přiřadí HttpClient a HttpMessageHandler z fondu, který spravuje. HttpClient se dá nakonfigurovat pomocí zásad Polly při registraci IHttpClientFactory v kontejneru DI pomocí metody rozšíření AddHttpClient.](./media/image3.5.png)

**Obrázek 8-4**. Použití HttpClientFactory se zadanými klientskými třídami.

Nejprve v aplikaci `HttpClientFactory` nastavte a přidejte odkaz `Microsoft.Extensions.Http` na balíček, který obsahuje `AddHttpClient()` metodu rozšíření pro `IServiceCollection`. Tato metoda rozšíření registruje `DefaultHttpClientFactory` , aby se použil jako typ singleton pro rozhraní `IHttpClientFactory`. Definuje přechodnou konfiguraci pro `HttpMessageHandlerBuilder`. Tato obslužná rutina`HttpMessageHandler` zprávy (objekt), která je pořízena z fondu `HttpClient` , je používána vrácenou z továrny.

V dalším kódu vidíte, jak `AddHttpClient()` se dá použít k registraci typových klientů (agentů služeb), které je potřeba použít. `HttpClient`

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Registrace služeb klienta, jak je znázorněno v předchozím kódu, vytvoří `DefaultClientFactory` `HttpClient` konfiguraci specificky pro každou službu, jak je vysvětleno v dalším odstavci.

Stejně jako při registraci třídy služby klienta s `AddHttpClient()` `HttpClient` , objekt, který bude vložen do vaší třídy, bude používat konfiguraci a zásady poskytované při registraci. V dalších částech uvidíte tyto zásady, jako jsou opakování Polly nebo přepínací moduly okruhů.

### <a name="httpclient-lifetimes"></a>HttpClient doby života

Pokaždé `IHttpClientFactory`, když získáte `HttpClient` objekt z, je vrácena nová instance. Každá z `HttpClient` `HttpMessageHandler` `HttpMessageHandler`nich ale používá fond a znovu ho používá ke snížení spotřeby prostředků, pokud doba života ještě nevypršela. `IHttpClientFactory`

Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje vlastní podkladová připojení HTTP; vytváření dalších obslužných rutin, než je potřeba, může způsobit zpoždění připojení. Některé obslužné rutiny také udržují připojení otevřené po neomezenou dobu, což může zabránit obslužné rutině v rekomunikaci se změnami DNS.

Objekty ve fondu mají dobu života, která je doba `HttpMessageHandler` , po kterou lze instanci ve fondu znovu použít. `HttpMessageHandler` Výchozí hodnota je dvě minuty, ale je možné ji přepsat na typového klienta. Chcete-li ho přepsat `SetHandlerLifetime()` , zavolejte `IHttpClientBuilder` na to, které je vráceno při vytváření klienta, jak je znázorněno v následujícím kódu:

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

Každý typový klient může mít svou vlastní nakonfigurovanou hodnotu životnosti obslužných rutin. Nastavte dobu života na `InfiniteTimeSpan` zakázat vypršení platnosti obslužné rutiny.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implementujte typové klientské třídy, které používají vložené a nakonfigurované HttpClient

Jako předchozí krok musíte mít definované vaše typové klientské třídy, například třídy v ukázkovém kódu, jako je například "BasketService", "CatalogService", "OrderingService" atd. – typový klient je třída, která přijímá `HttpClient` objekt (vložený prostřednictvím jeho konstruktor) a používá ho k volání některé vzdálené služby HTTP. Příklad:

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

Typový klient je efektivně přechodný objekt, což znamená, že se vytvoří nová instance pokaždé, když je potřeba, a při každém sestavení dostane novou `HttpClient` instanci. Objekty HttpMessageHandler ve fondu však jsou objekty, které jsou opakovaně používány více požadavky HTTP.

### <a name="use-your-typed-client-classes"></a>Použití typových klientských tříd

Nakonec, po implementaci tříd typů a jejich registraci v AddHttpClient (), je můžete použít všude, kde můžete mít služby, které jsou vloženy do DI, například v jakémkoli kódu stránky Razor nebo jakémkoli řadiči webové aplikace MVC, jako v následujícím kódu z eShopOnContainers.

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

V tomto okamžiku je zobrazený kód právě provádí běžné požadavky HTTP, ale hodnota Magic přichází v následujících částech, kde stačí přidat zásady a delegovat obslužné rutiny zaregistrovaným typovým klientům. všechny požadavky HTTP, které je třeba provést `HttpClient` , budou chová se s ohledem na odolné zásady, jako jsou třeba opakované pokusy pomocí exponenciálního omezení rychlostiu, přepínacích okruhů nebo jakékoli jiné vlastní obslužné rutiny, které implementují další funkce zabezpečení, jako je použití ověřovacích tokenů nebo jakékoli jiné vlastní funkce. 

## <a name="additional-resources"></a>Další zdroje

- **Používání HttpClientFactory v .NET Core**\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- **Úložiště GitHub HttpClientFactory**\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

>[!div class="step-by-step"]
>[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)Další
>[](implement-http-call-retries-exponential-backoff-polly.md)
