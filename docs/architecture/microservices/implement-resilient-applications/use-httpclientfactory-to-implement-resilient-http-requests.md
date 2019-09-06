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
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="2ff4e-103">Použití HttpClientFactory k implementaci odolných požadavků HTTP</span><span class="sxs-lookup"><span data-stu-id="2ff4e-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="2ff4e-104">`HttpClientFactory`je dogmatickým továrna, která je k dispozici od .NET Core <xref:System.Net.Http.HttpClient> 2,1, pro vytváření instancí, které se mají použít ve vašich aplikacích.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="2ff4e-105">Problémy s původní třídou HttpClient dostupnou v .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ff4e-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="2ff4e-106">Původní a dobře známou třídu [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) lze snadno použít, ale v některých případech ji nepoužívá mnoho vývojářů.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-106">The original and well-known [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span> 

<span data-ttu-id="2ff4e-107">Jako první problém, zatímco tato třída je na jedno použití, není při použití `using` s příkazem nejvhodnější volbou, protože i když `HttpClient` vyřadíte objekt, základní soket není hned uvolněn a může způsobit vážný problém s názvem ' Sockets vyčerpání.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="2ff4e-108">Další informace o tomto problému najdete v tématu o tom, [že používáte HttpClient špatné a že se destabilizující váš Blogový příspěvek k vašemu softwaru](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) .</span><span class="sxs-lookup"><span data-stu-id="2ff4e-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="2ff4e-109">`HttpClient` Proto má být vytvořena instance jednou a znovu použita po celou dobu životnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="2ff4e-110">Vytvoření instance třídy pro každý požadavek vyčerpá počet soketů, které jsou k dispozici v případě velkého zatížení. `HttpClient`</span><span class="sxs-lookup"><span data-stu-id="2ff4e-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="2ff4e-111">K tomuto problému dojde v `SocketException` důsledku chyb.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="2ff4e-112">Možné přístupy k vyřešení tohoto problému jsou založené na vytvoření `HttpClient` objektu jako singleton nebo static, jak je vysvětleno v tomto [článku o použití HttpClient](/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="2ff4e-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="2ff4e-113">Ale existuje druhý problém s `HttpClient` tím, že ho můžete mít, když ho použijete jako singleton nebo statický objekt.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="2ff4e-114">V tomto případě typ singleton nebo static `HttpClient` nerespektuje změny DNS, jak je vysvětleno v tomto problému v [úložišti GitHub .NET Core](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="2ff4e-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="2ff4e-115">Za účelem vyřešení těchto zmíněných problémů a zjednodušení správy `HttpClient` instancí .NET Core 2,1 zavádí nový `HttpClientFactory` , který lze použít také k implementaci odolných volání http integrací Polly s IT.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="2ff4e-116">Co je HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="2ff4e-116">What is HttpClientFactory</span></span>

<span data-ttu-id="2ff4e-117">`HttpClientFactory`je navrženo pro:</span><span class="sxs-lookup"><span data-stu-id="2ff4e-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="2ff4e-118">Poskytněte centrální umístění pro pojmenovávání a konfiguraci logických HttpClients.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="2ff4e-119">Můžete například nakonfigurovat klienta (agenta služeb), který je předem nakonfigurovaný pro přístup k určité mikroslužbě.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-119">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="2ff4e-120">Codify koncept odchozího middleware prostřednictvím delegování obslužných rutin `HttpClient` v a implementace middleware založeného na Polly, který využívá zásady Polly pro zajištění odolnosti.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="2ff4e-121">`HttpClient`již má koncepci delegování obslužných rutin, které by mohly být propojeny pro odchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="2ff4e-122">Do továrny zaregistrujete klienty http a můžete použít obslužnou rutinu Polly, která umožňuje použití zásad Polly pro opakování, CircuitBreakers atd.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="2ff4e-123">Spravujte dobu života HttpClientMessageHandlers, abyste se vyhnuli uvedeným problémům nebo problémům, ke `HttpClient` kterým může dojít při správě životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="2ff4e-124">Několik způsobů použití HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="2ff4e-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="2ff4e-125">V aplikaci můžete použít `HttpClientFactory` několik způsobů:</span><span class="sxs-lookup"><span data-stu-id="2ff4e-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="2ff4e-126">Použít `HttpClientFactory` přímo</span><span class="sxs-lookup"><span data-stu-id="2ff4e-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="2ff4e-127">Použití pojmenovaných klientů</span><span class="sxs-lookup"><span data-stu-id="2ff4e-127">Use Named Clients</span></span>
- <span data-ttu-id="2ff4e-128">Použití typových klientů</span><span class="sxs-lookup"><span data-stu-id="2ff4e-128">Use Typed Clients</span></span>
- <span data-ttu-id="2ff4e-129">Použít vygenerované klienty</span><span class="sxs-lookup"><span data-stu-id="2ff4e-129">Use Generated Clients</span></span>

<span data-ttu-id="2ff4e-130">Pro účely zkrácení tento návod ukazuje, jak používat `HttpClientFactory` , aby používal typové klienty (vzor agenta služby), ale všechny možnosti jsou zdokumentovány a jsou aktuálně uvedeny v tomto [článku týkajícím se použití HttpClientFactory](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="2ff4e-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that's to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="2ff4e-131">Jak používat typové klienty s HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="2ff4e-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="2ff4e-132">Co je to "Typový klient"?</span><span class="sxs-lookup"><span data-stu-id="2ff4e-132">So, what's a "Typed Client"?</span></span> <span data-ttu-id="2ff4e-133">Je to jenom `HttpClient` ta, která je nakonfigurovaná při vložení `DefaultHttpClientFactory`pomocí.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-133">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="2ff4e-134">Následující diagram znázorňuje, jak se používají typové klienty s `HttpClientFactory`:</span><span class="sxs-lookup"><span data-stu-id="2ff4e-134">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![ClientService vynuťte u (používaný řadičem nebo klientským kódem) používá HttpClient vytvořené registrovaným IHttpClientFactory.](./media/image3.5.png)

<span data-ttu-id="2ff4e-138">**Obrázek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-138">**Figure 8-4**.</span></span> <span data-ttu-id="2ff4e-139">Použití HttpClientFactory se zadanými klientskými třídami.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-139">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="2ff4e-140">Nejprve v aplikaci `HttpClientFactory` nastavte a přidejte odkaz `Microsoft.Extensions.Http` na balíček, který obsahuje `AddHttpClient()` metodu rozšíření pro `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-140">First, setup `HttpClientFactory` in your application, adding a reference to the `Microsoft.Extensions.Http` package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="2ff4e-141">Tato metoda rozšíření registruje `DefaultHttpClientFactory` , aby se použil jako typ singleton pro rozhraní `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-141">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="2ff4e-142">Definuje přechodnou konfiguraci pro `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-142">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="2ff4e-143">Tato obslužná rutina`HttpMessageHandler` zprávy (objekt), která je pořízena z fondu `HttpClient` , je používána vrácenou z továrny.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-143">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="2ff4e-144">V dalším kódu vidíte, jak `AddHttpClient()` se dá použít k registraci typových klientů (agentů služeb), které je potřeba použít. `HttpClient`</span><span class="sxs-lookup"><span data-stu-id="2ff4e-144">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="2ff4e-145">Registrace služeb klienta, jak je znázorněno v předchozím kódu, vytvoří `DefaultClientFactory` `HttpClient` konfiguraci specificky pro každou službu, jak je vysvětleno v dalším odstavci.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-145">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create an `HttpClient` configured specifically for each service, as we'll explain in the next paragraph.</span></span>

<span data-ttu-id="2ff4e-146">Stejně jako při registraci třídy služby klienta s `AddHttpClient()` `HttpClient` , objekt, který bude vložen do vaší třídy, bude používat konfiguraci a zásady poskytované při registraci.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-146">Just by registering your client service class with `AddHttpClient()`, the `HttpClient` object that will be injected into your class will use the configuration and policies provided upon registration.</span></span> <span data-ttu-id="2ff4e-147">V dalších částech uvidíte tyto zásady, jako jsou opakování Polly nebo přepínací moduly okruhů.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-147">In the next sections, you'll see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="2ff4e-148">HttpClient doby života</span><span class="sxs-lookup"><span data-stu-id="2ff4e-148">HttpClient lifetimes</span></span>

<span data-ttu-id="2ff4e-149">Pokaždé `IHttpClientFactory`, když získáte `HttpClient` objekt z, je vrácena nová instance.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-149">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="2ff4e-150">Každá z `HttpClient` `HttpMessageHandler` `HttpMessageHandler`nich ale používá fond a znovu ho používá ke snížení spotřeby prostředků, pokud doba života ještě nevypršela. `IHttpClientFactory`</span><span class="sxs-lookup"><span data-stu-id="2ff4e-150">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="2ff4e-151">Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje vlastní podkladová připojení HTTP; vytváření dalších obslužných rutin, než je potřeba, může způsobit zpoždění připojení.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-151">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="2ff4e-152">Některé obslužné rutiny také udržují připojení otevřené po neomezenou dobu, což může zabránit obslužné rutině v rekomunikaci se změnami DNS.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-152">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="2ff4e-153">Objekty ve fondu mají dobu života, která je doba `HttpMessageHandler` , po kterou lze instanci ve fondu znovu použít. `HttpMessageHandler`</span><span class="sxs-lookup"><span data-stu-id="2ff4e-153">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="2ff4e-154">Výchozí hodnota je dvě minuty, ale je možné ji přepsat na typového klienta.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-154">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="2ff4e-155">Chcete-li ho přepsat `SetHandlerLifetime()` , zavolejte `IHttpClientBuilder` na to, které je vráceno při vytváření klienta, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="2ff4e-155">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="2ff4e-156">Každý typový klient může mít svou vlastní nakonfigurovanou hodnotu životnosti obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-156">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="2ff4e-157">Nastavte dobu života na `InfiniteTimeSpan` zakázat vypršení platnosti obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-157">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="2ff4e-158">Implementujte typové klientské třídy, které používají vložené a nakonfigurované HttpClient</span><span class="sxs-lookup"><span data-stu-id="2ff4e-158">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="2ff4e-159">Jako předchozí krok musíte mít definované vaše typové klientské třídy, například třídy v ukázkovém kódu, jako je například "BasketService", "CatalogService", "OrderingService" atd. – typový klient je třída, která přijímá `HttpClient` objekt (vložený prostřednictvím jeho konstruktor) a používá ho k volání některé vzdálené služby HTTP.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-159">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="2ff4e-160">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2ff4e-160">For example:</span></span>

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

<span data-ttu-id="2ff4e-161">Typový klient (CatalogService v příkladu) je aktivován pomocí příkazu DI (vkládání závislostí), což znamená, že může přijmout jakoukoli registrovanou službu ve svém konstruktoru kromě HttpClient.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-161">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="2ff4e-162">Typový klient je efektivně přechodný objekt, což znamená, že se vytvoří nová instance pokaždé, když je potřeba, a při každém sestavení dostane novou `HttpClient` instanci.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-162">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="2ff4e-163">Objekty HttpMessageHandler ve fondu však jsou objekty, které jsou opakovaně používány více požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-163">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="2ff4e-164">Použití typových klientských tříd</span><span class="sxs-lookup"><span data-stu-id="2ff4e-164">Use your Typed Client classes</span></span>

<span data-ttu-id="2ff4e-165">Nakonec, po implementaci tříd typů a jejich registraci v AddHttpClient (), je můžete použít všude, kde můžete mít služby, které jsou vloženy do DI, například v jakémkoli kódu stránky Razor nebo jakémkoli řadiči webové aplikace MVC, jako v následujícím kódu z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-165">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="2ff4e-166">V tomto okamžiku je zobrazený kód právě provádí běžné požadavky HTTP, ale hodnota Magic přichází v následujících částech, kde stačí přidat zásady a delegovat obslužné rutiny zaregistrovaným typovým klientům. všechny požadavky HTTP, které je třeba provést `HttpClient` , budou chová se s ohledem na odolné zásady, jako jsou třeba opakované pokusy pomocí exponenciálního omezení rychlostiu, přepínacích okruhů nebo jakékoli jiné vlastní obslužné rutiny, které implementují další funkce zabezpečení, jako je použití ověřovacích tokenů nebo jakékoli jiné vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="2ff4e-166">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="2ff4e-167">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2ff4e-167">Additional resources</span></span>

- <span data-ttu-id="2ff4e-168">**Používání HttpClientFactory v .NET Core**</span><span class="sxs-lookup"><span data-stu-id="2ff4e-168">**Using HttpClientFactory in .NET Core**</span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- <span data-ttu-id="2ff4e-169">**Úložiště GitHub HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="2ff4e-169">**HttpClientFactory GitHub repo**</span></span>\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

>[!div class="step-by-step"]
><span data-ttu-id="2ff4e-170">[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)Další
>[](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="2ff4e-170">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
