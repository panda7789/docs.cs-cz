---
title: Použití HttpClientFactory k implementaci odolných požadavky HTTP
description: Další informace o použití HttpClientFactory dostupné od verze rozhraní .NET Core 2.1 pro vytvoření `HttpClient` instancí, usnadňuje použít ve svých aplikacích.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 73faa847dae2f844784ae5d85ce905b7e1e64cd0
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479812"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="8ecf0-103">Použití HttpClientFactory k implementaci odolných požadavky HTTP</span><span class="sxs-lookup"><span data-stu-id="8ecf0-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="8ecf0-104">`HttpClientFactory` je sebevědomý factory, dostupné od verze rozhraní .NET Core 2.1 pro vytváření <xref:System.Net.Http.HttpClient> instancí, který se má použít ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="8ecf0-105">Problémy s původní třídy HttpClient, která je k dispozici v .NET Core</span><span class="sxs-lookup"><span data-stu-id="8ecf0-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="8ecf0-106">Původní a dobře známých [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) třídu lze snadno použít, ale v některých případech se nepoužívá správně celá řada vývojářů.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-106">The original and well-known [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span> 

<span data-ttu-id="8ecf0-107">Jako první problém, i když tato třída je jedno použití, používat s `using` příkaz není nejlepší volbou protože i při vyřazení `HttpClient` objekt základního soketu neuvolní okamžitě a může způsobit závažné potíže s názvem "sockets vyčerpání ".</span><span class="sxs-lookup"><span data-stu-id="8ecf0-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="8ecf0-108">Další informace o tomto problému najdete v tématu [používáte HttpClient nesprávné a je to destabilizing váš software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blogový příspěvek.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="8ecf0-109">Proto `HttpClient` by se měly vytvořit jednou a opětovně používat v rámci životnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="8ecf0-110">Vytvoření instance `HttpClient` třídy pro každý požadavek že počet soketů, které jsou k dispozici pod velkým zatížením.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="8ecf0-111">Bude mít za následek problém `SocketException` chyby.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="8ecf0-112">Je to možné přístupy k vyřešení tohoto problému jsou založeny na vytváření `HttpClient` objekt typu singleton nebo static, jak je popsáno v tomto [článku znalostní báze Microsoft HttpClient využití](/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="8ecf0-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="8ecf0-113">Druhý problém s, ale `HttpClient` mají při použití jako singleton nebo statický objekt.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="8ecf0-114">V tomto případě, typu singleton nebo statické `HttpClient` nerespektuje změny DNS, jak je popsáno v tomto [problém na úložiště .NET Core GitHub](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="8ecf0-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="8ecf0-115">Pro vyřešení těchto problémů jsme už zmínili a správu `HttpClient` instance jednodušší, .NET Core 2.1 zavedl nový `HttpClientFactory` také, který lze použít k implementaci odolných volání HTTP integrací Polly s ním.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="8ecf0-116">Co je HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="8ecf0-116">What is HttpClientFactory</span></span>

<span data-ttu-id="8ecf0-117">`HttpClientFactory` je navržené pro:</span><span class="sxs-lookup"><span data-stu-id="8ecf0-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="8ecf0-118">Poskytují centrální umístění pro pojmenování a konfiguraci logické HttpClients.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="8ecf0-119">Můžete například nakonfigurovat klienta (Agent služby), který je předem nakonfigurovaná pro přístup k určité mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-119">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="8ecf0-120">Kodifikovat koncept odchozí middleware prostřednictvím delegování obslužné rutiny ve `HttpClient` a implementace middleware založený na Polly využít zásady společnosti Polly pro odolnost proti chybám.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="8ecf0-121">`HttpClient` již obsahuje koncept delegování obslužné rutiny, které by mohly být propojeny pro odchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="8ecf0-122">Registrace klientů protokolu http na objekt pro vytváření a můžete pomocí knihovny Polly obslužnou rutinu, která umožňuje Polly zásad se použije pro opakování, CircuitBreakers atd.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="8ecf0-123">Spravovat dobu života HttpClientMessageHandlers, aby se zabránilo uvedené problémy nebo problémy, které mohou nastat při správě `HttpClient` životnosti sami.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="8ecf0-124">Několik způsobů, jak používat HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="8ecf0-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="8ecf0-125">Existuje několik způsobů, které můžete použít `HttpClientFactory` ve vaší aplikaci:</span><span class="sxs-lookup"><span data-stu-id="8ecf0-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="8ecf0-126">Použití `HttpClientFactory` přímo</span><span class="sxs-lookup"><span data-stu-id="8ecf0-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="8ecf0-127">Použití s názvem klientů</span><span class="sxs-lookup"><span data-stu-id="8ecf0-127">Use Named Clients</span></span>
- <span data-ttu-id="8ecf0-128">Použijte zadaný klientů</span><span class="sxs-lookup"><span data-stu-id="8ecf0-128">Use Typed Clients</span></span>
- <span data-ttu-id="8ecf0-129">Pomocí vygenerovaných klientů</span><span class="sxs-lookup"><span data-stu-id="8ecf0-129">Use Generated Clients</span></span>

<span data-ttu-id="8ecf0-130">Pro účely jako stručný výtah tento návod ukazuje největší strukturovaný způsob, jak používat `HttpClientFactory` , který má používat zadaný klienty (model služby Agent), ale všechny možnosti jsou popsány a nejsou teď uvedená v tomto [článku pokrývající HttpClientFactory využití ](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="8ecf0-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that's to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="8ecf0-131">Jak používat klienty typem s HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="8ecf0-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="8ecf0-132">Co je "Typový klient"?</span><span class="sxs-lookup"><span data-stu-id="8ecf0-132">So, what's a "Typed Client"?</span></span> <span data-ttu-id="8ecf0-133">Jsou tam jen `HttpClient` , který je nakonfigurovaný na injektáži `DefaultHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-133">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="8ecf0-134">Následující diagram znázorňuje používání typu klientů s `HttpClientFactory`:</span><span class="sxs-lookup"><span data-stu-id="8ecf0-134">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![ClientService (používané kódu kontroleru nebo klienta) používá vytvořené registrované IHttpClientFactory HttpClient.](./media/image3.5.png)

<span data-ttu-id="8ecf0-138">**Obrázek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-138">**Figure 8-4**.</span></span> <span data-ttu-id="8ecf0-139">HttpClientFactory pomocí třídy typu klienta.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-139">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="8ecf0-140">Nejprve nastavte `HttpClientFactory` ve vaší aplikaci, přidejte odkaz na `Microsoft.Extensions.Http` balíček, který obsahuje `AddHttpClient()` rozšiřující metodu pro `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-140">First, setup `HttpClientFactory` in your application, adding a reference to the `Microsoft.Extensions.Http` package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="8ecf0-141">Metoda rozšíření registruje `DefaultHttpClientFactory` má být použit jako jednotlivý prvek pro rozhraní `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-141">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="8ecf0-142">Definuje přechodné konfiguraci `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-142">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="8ecf0-143">Tento popisovač zpráv (`HttpMessageHandler` objektu), je přijatá z fondu, používá `HttpClient` vrácený objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-143">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="8ecf0-144">V další kód, uvidíte jak `AddHttpClient()` slouží k registraci zadané klienty (agenty služby), které potřebují použít `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-144">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="8ecf0-145">Registrace služeb klienta, jak je znázorněno v předchozím kódu je `DefaultClientFactory` vytvořit `HttpClient` konfigurována vysvětlíme v další odstavci speciálně pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-145">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create an `HttpClient` configured specifically for each service, as we'll explain in the next paragraph.</span></span>

<span data-ttu-id="8ecf0-146">Stačí, když si zaregistrujete třída klienta služby s `AddHttpClient()`, `HttpClient` použije objekt, který budou vloženy do vaší třídy, konfigurace a zásad, které jsou k dispozici při registraci.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-146">Just by registering your client service class with `AddHttpClient()`, the `HttpClient` object that will be injected into your class will use the configuration and policies provided upon registration.</span></span> <span data-ttu-id="8ecf0-147">V následujících částech zobrazí se vám těchto zásad, jako je například Polly pro opakování nebo jističů.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-147">In the next sections, you'll see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="8ecf0-148">Životnost HttpClient</span><span class="sxs-lookup"><span data-stu-id="8ecf0-148">HttpClient lifetimes</span></span>

<span data-ttu-id="8ecf0-149">Pokaždé, když dojde `HttpClient` objektu z `IHttpClientFactory`, se vrátí novou instanci.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-149">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="8ecf0-150">Ale každý `HttpClient` používá `HttpMessageHandler` , který má ve fondu a využívat `IHttpClientFactory` ke snížení spotřeby prostředků, pokud `HttpMessageHandler`na životnost nevypršela platnost.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-150">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="8ecf0-151">Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje svou vlastní základní připojení protokolu HTTP; vytváření více obslužných rutin, než je nezbytné, může způsobit zpoždění připojení.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-151">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="8ecf0-152">Některé obslužné rutiny také zachovat připojení otevřené po neomezenou dobu, což může zabránit obslužnou rutinu reakce na změny DNS.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-152">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="8ecf0-153">`HttpMessageHandler` Objekty ve fondu mají životnost, který je doba, která `HttpMessageHandler` instance ve fondu je možné využít znovu.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-153">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="8ecf0-154">Výchozí hodnota je dvě minuty, ale může být potlačen za typu klienta.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-154">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="8ecf0-155">Chcete-li přepsat, zavolejte `SetHandlerLifetime()` na `IHttpClientBuilder` , který je vrácen při vytváření klienta, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8ecf0-155">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="8ecf0-156">Každý klient typu může mít svou vlastní hodnotu doby života nakonfigurované obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-156">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="8ecf0-157">Nastavení doby platnosti `InfiniteTimeSpan` zakázání obslužné rutiny ukončení.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-157">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="8ecf0-158">Implementace tříd typu klienta, které používají HttpClient vloženého a nakonfigurované</span><span class="sxs-lookup"><span data-stu-id="8ecf0-158">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="8ecf0-159">V předchozím kroku je potřeba mít zadané klienta tříd definovány, jako jsou třídy ve vzorovém kódu, jako je "BasketService", "CatalogService", "OrderingService" atd. – A typem klienta je třída, která přijímá `HttpClient` objektu (vloženého prostřednictvím jeho Konstruktor) a použije ho k volání některých vzdálené služby HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-159">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="8ecf0-160">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8ecf0-160">For example:</span></span>

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

<span data-ttu-id="8ecf0-161">Klient typu (CatalogService v příkladu) je aktivován DI (injektáž závislostí), což znamená, že může přijmout libovolný registrovanou službu 've svém konstruktoru, kromě HttpClient.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-161">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="8ecf0-162">Typem je klient, efektivně, přechodný objekt, což znamená, že je vytvořena nová instance pokaždé, když je zapotřebí, obdrží novou `HttpClient` pokaždé, když je vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-162">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="8ecf0-163">Objekt HttpMessageHandler objekty ve fondu jsou však objekty, které jsou opakovaně využívat více požadavků protokolu Http.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-163">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="8ecf0-164">Použití třídy typu klienta</span><span class="sxs-lookup"><span data-stu-id="8ecf0-164">Use your Typed Client classes</span></span>

<span data-ttu-id="8ecf0-165">Nakonec po implementovat typ třídy a jejich zaregistrovaného AddHttpClient(), můžete použít nezakódovávejte ho máte vloženy DI, například v jakékoli kódu stránky Razor nebo libovolného řadiče webové aplikace MVC, stejně jako v následujícím kódu ze služby aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-165">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="8ecf0-166">Do této chvíle právě uvedeném kódu provádí pravidelné požadavky Http, ale "kouzla" spočívá v následujících částech, kde právě přidáním zásady a delegování obslužné rutiny vašim klientům registrovaného typu, provádí požadavky HTTP `HttpClient` bude s ohledem na odolné zásady účtů, jako je například opakování pomocí exponenciálního omezení rychlosti, jističe nebo jiné vlastní delegování rutinu k implementaci další bezpečnostní funkce, jako je pomocí ověřovacích tokenů nebo jakékoli jiné vlastní funkce se chovají.</span><span class="sxs-lookup"><span data-stu-id="8ecf0-166">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="8ecf0-167">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8ecf0-167">Additional resources</span></span>

- <span data-ttu-id="8ecf0-168">**Použití HttpClientFactory v .NET Core**\\</span><span class="sxs-lookup"><span data-stu-id="8ecf0-168">**Using HttpClientFactory in .NET Core**\\</span></span>
  [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- <span data-ttu-id="8ecf0-169">**Úložiště HttpClientFactory GitHub**\\</span><span class="sxs-lookup"><span data-stu-id="8ecf0-169">**HttpClientFactory GitHub repo**\\</span></span>
  [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)

>[!div class="step-by-step"]
><span data-ttu-id="8ecf0-170">[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)
>[další](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="8ecf0-170">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>