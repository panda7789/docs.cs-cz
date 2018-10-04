---
title: Použití HttpClientFactory k implementaci odolných požadavky HTTP
description: HttpClientFactory je sebevědomý factory, dostupné od verze rozhraní .NET Core 2.1 pro vytváření `HttpClient` instancí, který se má použít ve svých aplikacích.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 800dc410d0cc49aecb7d936d50f9e575389cf278
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778494"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="7f88d-103">Použití HttpClientFactory k implementaci odolných požadavky HTTP</span><span class="sxs-lookup"><span data-stu-id="7f88d-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="7f88d-104">`HttpClientFactory` je sebevědomý factory, dostupné od verze rozhraní .NET Core 2.1 pro vytváření `HttpClient` instancí, který se má použít ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="7f88d-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating `HttpClient` instances to be used in your applications.</span></span> 

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="7f88d-105">Problémy s původní třídy HttpClient, která je k dispozici v .NET Core</span><span class="sxs-lookup"><span data-stu-id="7f88d-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="7f88d-106">Původní a dobře známých [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) třídu lze snadno použít, ale v některých případech se nepoužívá správně celá řada vývojářů.</span><span class="sxs-lookup"><span data-stu-id="7f88d-106">The original and well-known [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it is not being properly used by many developers.</span></span> 

<span data-ttu-id="7f88d-107">Jako první problém, i když tato třída je jedno použití, používat s `using` příkaz není nejlepší volbou protože i při vyřazení `HttpClient` objekt základního soketu neuvolní okamžitě a může způsobit závažné potíže s názvem "sockets vyčerpání ".</span><span class="sxs-lookup"><span data-stu-id="7f88d-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="7f88d-108">Další informace o tomto problému najdete v tématu [používáte HttpClient nesprávné a je to destabilizing váš software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blogový příspěvek.</span><span class="sxs-lookup"><span data-stu-id="7f88d-108">For more information about this issue, see [You're using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="7f88d-109">Proto `HttpClient` by se měly vytvořit jednou a opětovně používat v rámci životnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f88d-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="7f88d-110">Vytvoření instance `HttpClient` třídy pro každý požadavek že počet soketů, které jsou k dispozici pod velkým zatížením.</span><span class="sxs-lookup"><span data-stu-id="7f88d-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="7f88d-111">Bude mít za následek problém `SocketException` chyby.</span><span class="sxs-lookup"><span data-stu-id="7f88d-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="7f88d-112">Je to možné přístupy k vyřešení tohoto problému jsou založeny na vytváření `HttpClient` objekt typu singleton nebo static, jak je popsáno v tomto [článku znalostní báze Microsoft HttpClient využití](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="7f88d-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="7f88d-113">Druhý problém s, ale `HttpClient` mají při použití jako singleton nebo statický objekt.</span><span class="sxs-lookup"><span data-stu-id="7f88d-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="7f88d-114">V tomto případě, typu singleton nebo statické `HttpClient` nerespektuje změny DNS, jak je popsáno v tomto [problém na úložiště .NET Core GitHub](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="7f88d-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="7f88d-115">Pro vyřešení těchto problémů jsme už zmínili a správu `HttpClient` instance jednodušší, .NET Core 2.1 nabízí nový `HttpClientFactory` také, který lze použít k implementaci odolných volání HTTP integrací Polly s ním.</span><span class="sxs-lookup"><span data-stu-id="7f88d-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 offers a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="7f88d-116">Co je HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="7f88d-116">What is HttpClientFactory</span></span>

<span data-ttu-id="7f88d-117">`HttpClientFactory` je navržené pro:</span><span class="sxs-lookup"><span data-stu-id="7f88d-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="7f88d-118">Poskytují centrální umístění pro pojmenování a konfiguraci logické HttpClients.</span><span class="sxs-lookup"><span data-stu-id="7f88d-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="7f88d-119">Můžete například nakonfigurovat klienta (Služba agenta), který je předem nakonfigurovaná pro přístup k určité mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="7f88d-119">For example, you may configure a client (Service Agent) that is pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="7f88d-120">Kodifikovat koncept odchozí middleware prostřednictvím delegování obslužné rutiny ve `HttpClient` a implementace middleware založený na Polly využít zásady společnosti Polly pro odolnost proti chybám.</span><span class="sxs-lookup"><span data-stu-id="7f88d-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="7f88d-121">`HttpClient` již obsahuje koncept delegování obslužné rutiny, které by mohly být propojeny pro odchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="7f88d-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="7f88d-122">Registrace klientů protokolu http na objekt pro vytváření a můžete pomocí knihovny Polly obslužnou rutinu, která umožňuje Polly zásad se použije pro opakování, CircuitBreakers atd.</span><span class="sxs-lookup"><span data-stu-id="7f88d-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="7f88d-123">Spravovat dobu života HttpClientMessageHandlers, aby se zabránilo uvedené problémy nebo problémy, které mohou nastat při správě `HttpClient` životnosti sami.</span><span class="sxs-lookup"><span data-stu-id="7f88d-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="7f88d-124">Několik způsobů, jak používat HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="7f88d-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="7f88d-125">Existuje několik způsobů, které můžete použít `HttpClientFactory` ve vaší aplikaci:</span><span class="sxs-lookup"><span data-stu-id="7f88d-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="7f88d-126">Použití `HttpClientFactory` přímo</span><span class="sxs-lookup"><span data-stu-id="7f88d-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="7f88d-127">Použití s názvem klientů</span><span class="sxs-lookup"><span data-stu-id="7f88d-127">Use Named Clients</span></span>
- <span data-ttu-id="7f88d-128">Použijte zadaný klientů</span><span class="sxs-lookup"><span data-stu-id="7f88d-128">Use Typed Clients</span></span>
- <span data-ttu-id="7f88d-129">Pomocí vygenerovaných klientů</span><span class="sxs-lookup"><span data-stu-id="7f88d-129">Use Generated Clients</span></span>

<span data-ttu-id="7f88d-130">Pro účely jako stručný výtah tento návod ukazuje největší strukturovaný způsob, jak používat `HttpClientFactory` , který má používat zadaný klienty (model služby Agent), ale všechny možnosti jsou popsány a nejsou teď uvedená v tomto [článku pokrývající HttpClientFactory využití ](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="7f88d-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that is to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="7f88d-131">Jak používat klienty typem s HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="7f88d-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="7f88d-132">Následující diagram znázorňuje používání typu klientů s HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="7f88d-132">The following diagram shows how Typed Clients are used with HttpClientFactory.</span></span>

![Diagram s kontroler MVC s použitím vloženého ClientService, který interně používá nakonfigurované HttpClient zásadami HttpClientFactory a Polly.](./media/image3.5.png)

<span data-ttu-id="7f88d-134">**Obrázek 10-4**.</span><span class="sxs-lookup"><span data-stu-id="7f88d-134">**Figure 10-4**.</span></span> <span data-ttu-id="7f88d-135">Pomocí `HttpClientFactory`pomocí třídy typu klienta.</span><span class="sxs-lookup"><span data-stu-id="7f88d-135">Using `HttpClientFactory`with Typed Client classes.</span></span>

<span data-ttu-id="7f88d-136">Nejprve nastavte `HttpClientFactory` ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7f88d-136">First, setup `HttpClientFactory` in your application.</span></span> <span data-ttu-id="7f88d-137">Přidejte odkaz na `Microsoft.Extensions.Http` balíček, který zahrnuje `AddHttpClient()` rozšiřující metodu pro `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="7f88d-137">Add a reference to the `Microsoft.Extensions.Http` package which includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="7f88d-138">Metoda rozšíření registruje `DefaultHttpClientFactory` má být použit jako jednotlivý prvek pro rozhraní `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="7f88d-138">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="7f88d-139">Definuje přechodné konfiguraci `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="7f88d-139">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="7f88d-140">Tento popisovač zpráv (`HttpMessageHandler` objektu), je přijatá z fondu, používá `HttpClient` vrácený objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="7f88d-140">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="7f88d-141">V další kód, uvidíte jak `AddHttpClient()` slouží k registraci zadané klienty (agenty služby), které potřebují použít `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="7f88d-141">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="7f88d-142">Pouhým přidáním tříd typový klient s AddHttpClient(), vždy, když použijete `HttpClient` objekt, který budou vloženy do vaší třídy pomocí jeho konstruktoru, který `HttpClient` objekt budou používat všechny konfigurace a zásad, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7f88d-142">Just by adding your typed client classes with AddHttpClient(), whenever you use the `HttpClient` object that will be injected to your class through its constructor, that `HttpClient` object will be using all the configuration and policies provided.</span></span> <span data-ttu-id="7f88d-143">V následujících částech se zobrazí tyto zásady, jako je Polly pro opakování nebo jističů.</span><span class="sxs-lookup"><span data-stu-id="7f88d-143">In the next sections, you will see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="7f88d-144">Životnost HttpClient</span><span class="sxs-lookup"><span data-stu-id="7f88d-144">HttpClient lifetimes</span></span>

<span data-ttu-id="7f88d-145">Pokaždé, když dojde `HttpClient` objekt z IHttpClientFactory, novou instanci třídy `HttpClient` je vrácena.</span><span class="sxs-lookup"><span data-stu-id="7f88d-145">Each time you get an `HttpClient` object from IHttpClientFactory, a new instance of an `HttpClient` is returned.</span></span> <span data-ttu-id="7f88d-146">Bude existovat objekt HttpMessageHandler \*\* za názvem typu klienta.</span><span class="sxs-lookup"><span data-stu-id="7f88d-146">There will be an HttpMessageHandler\*\* per named of typed client.</span></span> <span data-ttu-id="7f88d-147">`IHttpClientFactory` objekt HttpMessageHandler instance vytvořené výrobou ke snížení spotřeby prostředků se fondu.</span><span class="sxs-lookup"><span data-stu-id="7f88d-147">`IHttpClientFactory` will pool the HttpMessageHandler instances created by the factory to reduce resource consumption.</span></span> <span data-ttu-id="7f88d-148">Objekt HttpMessageHandler instance mohou být znovu použity z fondu při vytváření nového `HttpClient` instance Pokud nevypršela platnost svého životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="7f88d-148">An HttpMessageHandler instance may be reused from the pool when creating a new `HttpClient` instance if its lifetime hasn't expired.</span></span>

<span data-ttu-id="7f88d-149">Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje svou vlastní základní připojení protokolu HTTP; vytváření více obslužných rutin, než je nezbytné, může způsobit zpoždění připojení.</span><span class="sxs-lookup"><span data-stu-id="7f88d-149">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="7f88d-150">Některé obslužné rutiny také zachovat připojení otevřené po neomezenou dobu, což může zabránit obslužnou rutinu reakce na změny DNS.</span><span class="sxs-lookup"><span data-stu-id="7f88d-150">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="7f88d-151">Objekt HttpMessageHandler objekty ve fondu mají životnost, který je doba, která instance objekt HttpMessageHandler ve fondu je možné využít znovu.</span><span class="sxs-lookup"><span data-stu-id="7f88d-151">The HttpMessageHandler objects in the pool have a lifetime that is the length of time that an HttpMessageHandler instance in the pool can be reused.</span></span> <span data-ttu-id="7f88d-152">Výchozí hodnota je dvě minuty, ale může být potlačen za klienta s názvem nebo zadaný základ.</span><span class="sxs-lookup"><span data-stu-id="7f88d-152">The default value is two minutes, but it can be overridden per named or typed client basis.</span></span> <span data-ttu-id="7f88d-153">Pokud chcete ho přepsat, volejte SetHandlerLifetime() IHttpClientBuilder, která je vrácena při vytváření klienta, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7f88d-153">To override it, call SetHandlerLifetime() on the IHttpClientBuilder that is returned when creating the client, as shown in the following code.</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="7f88d-154">Každý typový klient nebo pojmenované klienta může mít svou vlastní hodnotu doby života nakonfigurované obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="7f88d-154">Each typed client or named client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="7f88d-155">Nastavení doby platnosti na InfiniteTimeSpan zakázání obslužné rutiny ukončení.</span><span class="sxs-lookup"><span data-stu-id="7f88d-155">Set the lifetime to InfiniteTimeSpan to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="7f88d-156">Implementace tříd typu klienta, které používají HttpClient vloženého a nakonfigurované</span><span class="sxs-lookup"><span data-stu-id="7f88d-156">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="7f88d-157">V předchozím kroku je potřeba mít zadané klienta tříd definovány, jako jsou třídy ve vzorovém kódu, jako je "BasketService", "CatalogService", "OrderingService" atd. – typový klient je třída, která přijímá `HttpClient` objektu (vloženého prostřednictvím jeho Konstruktor) a použije ho k volání některých vzdálené služby HTTP.</span><span class="sxs-lookup"><span data-stu-id="7f88d-157">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A typed client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="7f88d-158">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7f88d-158">For example:</span></span>

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

<span data-ttu-id="7f88d-159">Typový klient (v příkladu CatalogService) je aktivován DI (injektáž závislostí), což znamená, že může přijmout libovolný registrovanou službu 've svém konstruktoru, kromě HttpClient.</span><span class="sxs-lookup"><span data-stu-id="7f88d-159">The typed client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="7f88d-160">Typový klient je, efektivně, přechodný objekt, což znamená, že je vytvořena nová instance pokaždé, když je zapotřebí, obdrží novou `HttpClient` pokaždé, když je vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="7f88d-160">A typed client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it is constructed.</span></span> <span data-ttu-id="7f88d-161">Objekt HttpMessageHandler objekty ve fondu jsou však objekty, které jsou opakovaně využívat více požadavků protokolu Http.</span><span class="sxs-lookup"><span data-stu-id="7f88d-161">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="7f88d-162">Použití třídy typu klienta</span><span class="sxs-lookup"><span data-stu-id="7f88d-162">Use your Typed Client classes</span></span>

<span data-ttu-id="7f88d-163">Nakonec po implementovat typ třídy a jejich zaregistrovaného AddHttpClient(), můžete použít nezakódovávejte ho máte vloženy DI, například v jakékoli kódu stránky Razor nebo libovolného řadiče webové aplikace MVC, stejně jako v následujícím kódu ze služby aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="7f88d-163">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="7f88d-164">Až do této chvíle právě uvedeném kódu provádí pravidelné požadavky Http, ale "kouzla" spočívá v následujících částech, kde pouze přidáním zásady a delegování obslužné rutiny pro registrované zadali klientů, požadavky Http udělat `HttpClient` bude s ohledem na odolné zásady účtů, jako je například opakování pomocí exponenciálního omezení rychlosti, jističe nebo jiné vlastní delegování rutinu k implementaci další bezpečnostní funkce, jako je pomocí ověřovacích tokenů nebo jakékoli jiné vlastní funkce se chovají.</span><span class="sxs-lookup"><span data-stu-id="7f88d-164">Until this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered typed clients, all the Http requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 


## <a name="additional-resources"></a><span data-ttu-id="7f88d-165">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="7f88d-165">Additional resources</span></span>

-   <span data-ttu-id="7f88d-166">**Použití HttpClientFactory v .NET Core 2.1**
    [*https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)</span><span class="sxs-lookup"><span data-stu-id="7f88d-166">**Using HttpClientFactory in .NET Core 2.1**
[*https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)</span></span>


-   <span data-ttu-id="7f88d-167">**Úložiště HttpClientFactory GitHub**</span><span class="sxs-lookup"><span data-stu-id="7f88d-167">**HttpClientFactory GitHub repo**</span></span>

    [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)



>[!div class="step-by-step"]
<span data-ttu-id="7f88d-168">[Předchozí] (explore-custom-http-call-retries-exponential-backoff.md) [Další] (implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="7f88d-168">[Previous] (explore-custom-http-call-retries-exponential-backoff.md) [Next] (implement-http-call-retries-exponential-backoff-polly.md)</span></span>
