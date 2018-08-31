---
title: Použití HttpClientFactory k implementaci odolných požadavky HTTP
description: HttpClientFactory je sebevědomý factory, dostupné od verze rozhraní .NET Core 2.1 pro vytváření `HttpClient` instancí, který se má použít ve svých aplikacích.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 6fd30a9358ca9c07b2a6e2ec591e4c5d7db54ccb
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43252821"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Použití HttpClientFactory k implementaci odolných požadavky HTTP

`HttpClientFactory` je sebevědomý factory, dostupné od verze rozhraní .NET Core 2.1 pro vytváření `HttpClient` instancí, který se má použít ve svých aplikacích. 

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problémy s původní třídy HttpClient, která je k dispozici v .NET Core

Původní a dobře vědět [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) třídu lze snadno použít, ale v některých případech se nepoužívá správně celá řada vývojářů. 

Jako první problém, i když tato třída je jedno použití, používat s `using` příkaz není nejlepší volbou protože i při vyřazení `HttpClient` objekt základního soketu neuvolní okamžitě a může způsobit závažné potíže s názvem "sockets vyčerpání ". Další informace o tomto problému najdete v tématu [používáte HttpClient nesprávné a je to destabilizing váš software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blogový příspěvek.

Proto `HttpClient` by se měly vytvořit jednou a opětovně používat v rámci životnosti aplikace. Vytvoření instance `HttpClient` třídy pro každý požadavek že počet soketů, které jsou k dispozici pod velkým zatížením. Bude mít za následek problém `SocketException` chyby. Je to možné přístupy k vyřešení tohoto problému jsou založeny na vytváření `HttpClient` objekt typu singleton nebo static, jak je popsáno v tomto [článku znalostní báze Microsoft HttpClient využití](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/console-webapiclient). 

Druhý problém s, ale `HttpClient` mají při použití jako singleton nebo statický objekt. V tomto případě, typu singleton nebo statické `HttpClient` nerespektuje změny DNS, jak je popsáno v tomto [problém na úložiště .NET Core GitHub](https://github.com/dotnet/corefx/issues/11224). 

Pro vyřešení těchto problémů jsme už zmínili a správu `HttpClient` instance jednodušší, .NET Core 2.1 nabízí nový `HttpClientFactory` také, který lze použít k implementaci odolných volání HTTP integrací Polly s ním.   

## <a name="what-is-httpclientfactory"></a>Co je HttpClientFactory

`HttpClientFactory` je navržené pro:

- Poskytují centrální umístění pro pojmenování a konfiguraci logické HttpClients. Můžete například nakonfigurovat klienta (Služba agenta), který je předem nakonfigurovaná pro přístup k určité mikroslužeb.
- Kodifikovat koncept odchozí middleware prostřednictvím delegování obslužné rutiny ve `HttpClient` a implementace middleware založený na Polly využít zásady společnosti Polly pro odolnost proti chybám.
- `HttpClient` již obsahuje koncept delegování obslužné rutiny, které by mohly být propojeny pro odchozí požadavky HTTP. Registrace klientů protokolu http na objekt pro vytváření a můžete pomocí knihovny Polly obslužnou rutinu, která umožňuje Polly zásad se použije pro opakování, CircuitBreakers atd.
- Spravovat dobu života HttpClientMessageHandlers, aby se zabránilo uvedené problémy nebo problémy, které mohou nastat při správě `HttpClient` životnosti sami. 

## <a name="multiple-ways-to-use-httpclientfactory"></a>Několik způsobů, jak používat HttpClientFactory

Existuje několik způsobů, které můžete použít `HttpClientFactory` ve vaší aplikaci:

- Použití `HttpClientFactory` přímo
- Použití s názvem klientů
- Použijte zadaný klientů
- Pomocí vygenerovaných klientů

Pro účely jako stručný výtah tento návod ukazuje největší strukturovaný způsob, jak používat `HttpClientFactory` , který má používat zadaný klienty (model služby Agent), ale všechny možnosti jsou popsány a nejsou teď uvedená v tomto [článku pokrývající HttpClientFactory využití ](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Jak používat klienty typem s HttpClientFactory

Následující diagram znázorňuje používání typu klientů s HttpClientFactory.

![Diagram s kontroler MVC s použitím vloženého ClientService, který interně používá nakonfigurované HttpClient zásadami HttpClientFactory a Polly.](./media/image3.5.png)

**Obrázek 10-4**. Pomocí `HttpClientFactory`pomocí třídy typu klienta.

Nejprve nastavte `HttpClientFactory` ve vaší aplikaci. Přidejte odkaz na `Microsoft.Extensions.Http` balíček, který zahrnuje `AddHttpClient()` rozšiřující metodu pro `IServiceCollection`. Metoda rozšíření registruje `DefaultHttpClientFactory` má být použit jako jednotlivý prvek pro rozhraní `IHttpClientFactory`. Definuje přechodné konfiguraci `HttpMessageHandlerBuilder`. Tento popisovač zpráv (`HttpMessageHandler` objektu), je přijatá z fondu, používá `HttpClient` vrácený objekt pro vytváření.

V další kód, uvidíte jak `AddHttpClient()` slouží k registraci zadané klienty (agenty služby), které potřebují použít `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Pouhým přidáním tříd typový klient s AddHttpClient(), vždy, když použijete `HttpClient` objekt, který budou vloženy do vaší třídy pomocí jeho konstruktoru, který `HttpClient` objekt budou používat všechny konfigurace a zásad, které jsou k dispozici. V následujících částech se zobrazí tyto zásady, jako je Polly pro opakování nebo jističů.

### <a name="httpclient-lifetimes"></a>Životnost HttpClient

Pokaždé, když dojde `HttpClient` objekt z IHttpClientFactory, novou instanci třídy `HttpClient` je vrácena. Bude existovat objekt HttpMessageHandler ** za názvem typu klienta. Můžu`HttpClientFactory` bude fond instancí objekt HttpMessageHandler vytvořeny procesem ke snížení spotřeby prostředků. Objekt HttpMessageHandler instance mohou být znovu použity z fondu při vytváření nového `HttpClient` instance Pokud nevypršela platnost svého životního cyklu.

Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje svou vlastní základní připojení protokolu HTTP; vytváření více obslužných rutin, než je nezbytné, může způsobit zpoždění připojení. Některé obslužné rutiny také zachovat připojení otevřené po neomezenou dobu, což může zabránit obslužnou rutinu reakce na změny DNS.

Objekt HttpMessageHandler objekty ve fondu mají životnost, který je doba, která instance objekt HttpMessageHandler ve fondu je možné využít znovu. Výchozí hodnota je dvě minuty, ale může být potlačen za klienta s názvem nebo zadaný základ. Pokud chcete ho přepsat, volejte SetHandlerLifetime() IHttpClientBuilder, která je vrácena při vytváření klienta, jak je znázorněno v následujícím kódu.

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

Každý typový klient nebo pojmenované klienta může mít svou vlastní hodnotu doby života nakonfigurované obslužné rutiny. Nastavení doby platnosti na InfiniteTimeSpan zakázání obslužné rutiny ukončení.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implementace tříd typu klienta, které používají HttpClient vloženého a nakonfigurované

V předchozím kroku je potřeba mít zadané klienta tříd definovány, jako jsou třídy ve vzorovém kódu, jako je "BasketService", "CatalogService", "OrderingService" atd. – typový klient je třída, která přijímá `HttpClient` objektu (vloženého prostřednictvím jeho Konstruktor) a použije ho k volání některých vzdálené služby HTTP. Příklad:

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

Typový klient (v příkladu CatalogService) je aktivován DI (injektáž závislostí), což znamená, že může přijmout libovolný registrovanou službu 've svém konstruktoru, kromě HttpClient.

Typový klient je, efektivně, přechodný objekt, což znamená, že je vytvořena nová instance pokaždé, když je zapotřebí, obdrží novou `HttpClient` pokaždé, když je vytvořena instance. Objekt HttpMessageHandler objekty ve fondu jsou však objekty, které jsou opakovaně využívat více požadavků protokolu Http.

### <a name="use-your-typed-client-classes"></a>Použití třídy typu klienta

Nakonec po implementovat typ třídy a jejich zaregistrovaného AddHttpClient(), můžete použít nezakódovávejte ho máte vloženy DI, například v jakékoli kódu stránky Razor nebo libovolného řadiče webové aplikace MVC, stejně jako v následujícím kódu ze služby aplikaci eShopOnContainers.

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

Až do této chvíle právě uvedeném kódu provádí pravidelné požadavky Http, ale "kouzla" spočívá v následujících částech, kde pouze přidáním zásady a delegování obslužné rutiny pro registrované zadali klientů, požadavky Http udělat `HttpClient` bude s ohledem na odolné zásady účtů, jako je například opakování pomocí exponenciálního omezení rychlosti, jističe nebo jiné vlastní delegování rutinu k implementaci další bezpečnostní funkce, jako je pomocí ověřovacích tokenů nebo jakékoli jiné vlastní funkce se chovají. 


## <a name="additional-resources"></a>Další zdroje

-   **Použití HttpClientFactory v .NET Core 2.1**
    [*https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)


-   **Úložiště HttpClientFactory GitHub**

    [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)



>[!div class="step-by-step"]
[Předchozí] (explore-custom-http-call-retries-exponential-backoff.md) [Další] (implement-http-call-retries-exponential-backoff-polly.md)
