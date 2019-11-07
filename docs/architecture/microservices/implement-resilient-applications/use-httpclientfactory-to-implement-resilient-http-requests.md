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
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="f6977-103">Použití HttpClientFactory k implementaci odolných požadavků HTTP</span><span class="sxs-lookup"><span data-stu-id="f6977-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="f6977-104">`HttpClientFactory` je objekt pro vytváření dogmatickým, který je k dispozici od .NET Core 2,1, aby se vytvořily <xref:System.Net.Http.HttpClient> instance pro použití ve vašich aplikacích.</span><span class="sxs-lookup"><span data-stu-id="f6977-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="f6977-105">Problémy s původní třídou HttpClient dostupnou v .NET Core</span><span class="sxs-lookup"><span data-stu-id="f6977-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="f6977-106">Původní a dobře známá <xref:System.Net.Http.HttpClient> třída lze snadno použít, ale v některých případech ji nepoužívá mnoho vývojářů.</span><span class="sxs-lookup"><span data-stu-id="f6977-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="f6977-107">Jako první problém, zatímco tato třída je na jedno použití, není při použití s příkazem `using` nejlepší volbou, protože i když vyřadíte `HttpClient` objekt, základní soket není hned uvolněn a může způsobit vážný problém s názvem "vyčerpání soketů".</span><span class="sxs-lookup"><span data-stu-id="f6977-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="f6977-108">Další informace o tomto problému najdete v tématu o tom, [že používáte HttpClient špatné a že se destabilizující váš Blogový příspěvek k vašemu softwaru](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) .</span><span class="sxs-lookup"><span data-stu-id="f6977-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="f6977-109">Proto je `HttpClient`, aby se vytvořila instance jednou a znovu používala po celou dobu životnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6977-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="f6977-110">Vytvoření instance `HttpClient` třídy pro každý požadavek vyčerpá počet soketů, které jsou k dispozici v případě velkého zatížení.</span><span class="sxs-lookup"><span data-stu-id="f6977-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="f6977-111">Tento problém bude mít za následek `SocketException` chyby.</span><span class="sxs-lookup"><span data-stu-id="f6977-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="f6977-112">Možné přístupy k vyřešení tohoto problému jsou založené na vytvoření objektu `HttpClient` jako singleton nebo static, jak je vysvětleno v tomto [článku o použití HttpClient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="f6977-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span>

<span data-ttu-id="f6977-113">Ale existuje druhý problém s `HttpClient`, který můžete mít, když ho použijete jako singleton nebo statický objekt.</span><span class="sxs-lookup"><span data-stu-id="f6977-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="f6977-114">V tomto případě typ singleton nebo statický `HttpClient` nerespektuje změny DNS, jak je vysvětleno v tomto [problému](https://github.com/dotnet/corefx/issues/11224) v úložišti GitHub/corefx GitHub.</span><span class="sxs-lookup"><span data-stu-id="f6977-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue](https://github.com/dotnet/corefx/issues/11224) at the dotnet/corefx GitHub repository.</span></span>

<span data-ttu-id="f6977-115">Rozhraní .NET Core 2,1 zavedlo nové `HttpClientFactory`, které lze použít také k implementaci odolných volání HTTP integrací Polly s tím, aby vyřešila zmíněné problémy a zjednodušila správu instancí `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="f6977-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>

<span data-ttu-id="f6977-116">[Polly](http://www.thepollyproject.org/) je přechodná knihovna pro zpracování chyb, která vývojářům pomáhá přidat odolnost do svých aplikací s využitím některých předdefinovaných zásad v rámci procesu, který je bezpečný pro práci v Fluent a vlákně.</span><span class="sxs-lookup"><span data-stu-id="f6977-116">[Polly](http://www.thepollyproject.org/) is transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="f6977-117">Co je HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="f6977-117">What is HttpClientFactory</span></span>

<span data-ttu-id="f6977-118">`HttpClientFactory` je navržený tak, aby:</span><span class="sxs-lookup"><span data-stu-id="f6977-118">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="f6977-119">Poskytněte centrální umístění pro pojmenovávání a konfiguraci logických `HttpClient` objektů.</span><span class="sxs-lookup"><span data-stu-id="f6977-119">Provide a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="f6977-120">Můžete například nakonfigurovat klienta (agenta služeb), který je předem nakonfigurovaný pro přístup k určité mikroslužbě.</span><span class="sxs-lookup"><span data-stu-id="f6977-120">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="f6977-121">Codify koncept odchozího middleware prostřednictvím delegování obslužných rutin v `HttpClient` a implementace middleware založeného na Polly, který využívá zásady Polly pro zajištění odolnosti.</span><span class="sxs-lookup"><span data-stu-id="f6977-121">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="f6977-122">`HttpClient` už má koncept delegování obslužných rutin, které by se daly propojit pro odchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="f6977-122">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="f6977-123">Do továrny zaregistrujete klienty HTTP a pomocí obslužné rutiny Polly můžete použít zásady Polly pro opakování, CircuitBreakers a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f6977-123">You register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="f6977-124">Spravujte dobu života `HttpClientMessageHandlers`, abyste se vyhnuli uvedeným problémům nebo problémům, ke kterým může dojít při správě `HttpClient`ch životních cyklů.</span><span class="sxs-lookup"><span data-stu-id="f6977-124">Manage the lifetime of `HttpClientMessageHandlers` to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="f6977-125">`HttpClientFactory` je úzce spjat s implementací (DI) pro vkládání závislostí v balíčku NuGet `Microsoft.Extensions.DependencyInjection`.</span><span class="sxs-lookup"><span data-stu-id="f6977-125">`HttpClientFactory` is tightly tied to the dependency injection (DI) implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="f6977-126">Další informace o používání dalších kontejnerů vkládání závislostí naleznete v této [diskuzi GitHubu](https://github.com/aspnet/Extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="f6977-126">For more information about using other dependency injection containers, see this [GitHub discussion](https://github.com/aspnet/Extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="f6977-127">Několik způsobů použití HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="f6977-127">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="f6977-128">Existuje několik způsobů, jak můžete v aplikaci `HttpClientFactory` použít:</span><span class="sxs-lookup"><span data-stu-id="f6977-128">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="f6977-129">Použít `HttpClientFactory` přímo</span><span class="sxs-lookup"><span data-stu-id="f6977-129">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="f6977-130">Použití pojmenovaných klientů</span><span class="sxs-lookup"><span data-stu-id="f6977-130">Use Named Clients</span></span>
- <span data-ttu-id="f6977-131">Použití typových klientů</span><span class="sxs-lookup"><span data-stu-id="f6977-131">Use Typed Clients</span></span>
- <span data-ttu-id="f6977-132">Použít vygenerované klienty</span><span class="sxs-lookup"><span data-stu-id="f6977-132">Use Generated Clients</span></span>

<span data-ttu-id="f6977-133">V zájmu zkrácení vám tento návod ukáže i strukturovaný způsob použití `HttpClientFactory`, který se používá pro typové klienty (model agenta služby).</span><span class="sxs-lookup"><span data-stu-id="f6977-133">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="f6977-134">Všechny možnosti jsou ale zdokumentováné a aktuálně jsou uvedené v tomto [článku, které pokrývají HttpClientFactory využití](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="f6977-134">However, all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="f6977-135">Jak používat typové klienty s HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="f6977-135">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="f6977-136">Co je to "Typový klient"?</span><span class="sxs-lookup"><span data-stu-id="f6977-136">So, what's a "Typed Client"?</span></span> <span data-ttu-id="f6977-137">Je to jen `HttpClient`, která je nakonfigurovaná při vkládání pomocí `DefaultHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="f6977-137">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="f6977-138">Následující diagram znázorňuje, jak se používají typové klienty s `HttpClientFactory`:</span><span class="sxs-lookup"><span data-stu-id="f6977-138">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![Diagram znázorňující, jak se používají typové klienty s HttpClientFactory](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="f6977-140">**Obrázek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="f6977-140">**Figure 8-4**.</span></span> <span data-ttu-id="f6977-141">Použití HttpClientFactory se zadanými klientskými třídami.</span><span class="sxs-lookup"><span data-stu-id="f6977-141">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="f6977-142">Na výše uvedeném obrázku ClientService vynuťte u (používaný řadičem nebo klientským kódem) používá `HttpClient` vytvořené pomocí registrované `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="f6977-142">In the above image, a ClientService (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="f6977-143">Tato továrna přiřadí `HttpClient` `HttpMessageHandler` z fondu, který spravuje.</span><span class="sxs-lookup"><span data-stu-id="f6977-143">This factory assigns the `HttpClient` an `HttpMessageHandler` from a pool it manages.</span></span> <span data-ttu-id="f6977-144">`HttpClient` lze nakonfigurovat pomocí zásad Polly při registraci `IHttpClientFactory` v kontejneru DI pomocí metody rozšíření `AddHttpClient`.</span><span class="sxs-lookup"><span data-stu-id="f6977-144">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method `AddHttpClient`.</span></span>

<span data-ttu-id="f6977-145">Pokud chcete nakonfigurovat výše uvedenou strukturu, přidejte `HttpClientFactory` do své aplikace tak, že nainstalujete balíček NuGet `Microsoft.Extensions.Http`, který obsahuje metodu rozšíření `AddHttpClient()` pro `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="f6977-145">To configure the above structure, add `HttpClientFactory` in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="f6977-146">Tato metoda rozšíření registruje `DefaultHttpClientFactory` pro použití jako typ singleton pro `IHttpClientFactory` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f6977-146">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="f6977-147">Definuje přechodnou konfiguraci `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="f6977-147">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="f6977-148">Tato obslužná rutina zprávy (objekt `HttpMessageHandler`), která je pořízená z fondu, se používá `HttpClient` vrácená z továrny.</span><span class="sxs-lookup"><span data-stu-id="f6977-148">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="f6977-149">V dalším kódu vidíte, jak `AddHttpClient()` lze použít k registraci typových klientů (agentů služeb), kteří potřebují používat `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="f6977-149">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="f6977-150">Registrace služeb klienta, jak je znázorněno v předchozím kódu, vytvoří `DefaultClientFactory` pro každou službu vytvořit standardní `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="f6977-150">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="f6977-151">Můžete také přidat konfiguraci specifickou pro instanci v registraci, například nakonfigurovat základní adresu a přidat některé zásady odolnosti, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="f6977-151">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="f6977-152">Podobně jako v tomto příkladu vidíte jednu z výše uvedených zásad v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="f6977-152">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="f6977-153">Další podrobnosti o používání Polly najdete v [dalším článku](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="f6977-153">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="f6977-154">HttpClient doby života</span><span class="sxs-lookup"><span data-stu-id="f6977-154">HttpClient lifetimes</span></span>

<span data-ttu-id="f6977-155">Pokaždé, když dostanete objekt `HttpClient` z `IHttpClientFactory`, vrátí se nová instance.</span><span class="sxs-lookup"><span data-stu-id="f6977-155">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="f6977-156">Každý `HttpClient` ale používá `HttpMessageHandler`, který `IHttpClientFactory` se ve fondu a znovu používá, aby se snížila spotřeba prostředků, pokud doba platnosti `HttpMessageHandler` vypršela.</span><span class="sxs-lookup"><span data-stu-id="f6977-156">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="f6977-157">Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje vlastní podkladová připojení HTTP; vytváření dalších obslužných rutin, než je potřeba, může způsobit zpoždění připojení.</span><span class="sxs-lookup"><span data-stu-id="f6977-157">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="f6977-158">Některé obslužné rutiny také udržují připojení otevřené po neomezenou dobu, což může zabránit obslužné rutině v rekomunikaci se změnami DNS.</span><span class="sxs-lookup"><span data-stu-id="f6977-158">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="f6977-159">Objekty `HttpMessageHandler` ve fondu mají dobu života, která je doba, po kterou lze znovu použít instanci `HttpMessageHandler` ve fondu.</span><span class="sxs-lookup"><span data-stu-id="f6977-159">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="f6977-160">Výchozí hodnota je dvě minuty, ale je možné ji přepsat na typového klienta.</span><span class="sxs-lookup"><span data-stu-id="f6977-160">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="f6977-161">Chcete-li jej přepsat, zavolejte `SetHandlerLifetime()` na `IHttpClientBuilder`, který je vrácen při vytváření klienta, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="f6977-161">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="f6977-162">Každý typový klient může mít svou vlastní nakonfigurovanou hodnotu životnosti obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="f6977-162">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="f6977-163">Nastavte dobu života na `InfiniteTimeSpan`, aby se zakázala vypršení platnosti obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="f6977-163">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="f6977-164">Implementujte typové klientské třídy, které používají vložené a nakonfigurované HttpClient</span><span class="sxs-lookup"><span data-stu-id="f6977-164">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="f6977-165">Jako předchozí krok musíte mít definované vaše typové klientské třídy, jako jsou třídy v ukázkovém kódu, jako je například "BasketService", "CatalogService", "OrderingService" atd. – typový klient je třída, která přijímá objekt `HttpClient` (vložený prostřednictvím jeho konstruktor) a používá ho k volání některé vzdálené služby HTTP.</span><span class="sxs-lookup"><span data-stu-id="f6977-165">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="f6977-166">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f6977-166">For example:</span></span>

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

<span data-ttu-id="f6977-167">Typový klient (CatalogService v příkladu) je aktivován pomocí příkazu DI (vkládání závislostí), což znamená, že může přijmout jakoukoli registrovanou službu ve svém konstruktoru kromě HttpClient.</span><span class="sxs-lookup"><span data-stu-id="f6977-167">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="f6977-168">Typový klient je efektivně přechodný objekt, což znamená, že se vytvoří nová instance pokaždé, když je potřeba, a dostane novou `HttpClient` instanci pokaždé, když je vytvořená.</span><span class="sxs-lookup"><span data-stu-id="f6977-168">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="f6977-169">Objekty HttpMessageHandler ve fondu však jsou objekty, které jsou opakovaně používány více požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="f6977-169">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="f6977-170">Použití typových klientských tříd</span><span class="sxs-lookup"><span data-stu-id="f6977-170">Use your Typed Client classes</span></span>

<span data-ttu-id="f6977-171">Nakonec, když máte implementované typové třídy a máte je zaregistrované ve `AddHttpClient()`, můžete je použít všude, kde můžete mít služby, které jsou vloženy do DI.</span><span class="sxs-lookup"><span data-stu-id="f6977-171">Finally, once you have your typed classes implemented and have them registered with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="f6977-172">Například v kódu stránky Razor nebo kontroleru webové aplikace MVC, jako v následujícím kódu z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="f6977-172">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="f6977-173">V tomto okamžiku je zobrazený kód pouze provádění běžných požadavků protokolu HTTP, ale hodnota Magic přichází v následujících částech, kde stačí přidat zásady a delegovat obslužné rutiny zaregistrovaným typovým klientům. všechny požadavky HTTP, které je třeba provést `HttpClient` se budou chovat s ohledem na odolné zásady, jako jsou třeba opakované pokusy pomocí exponenciálního omezení rychlostiu, vypínačů okruhu nebo jakékoli jiné vlastní obslužné rutiny, které implementují další funkce zabezpečení, jako je například použití ověřovacích tokenů nebo jakékoli jiné vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="f6977-173">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f6977-174">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="f6977-174">Additional resources</span></span>

- <span data-ttu-id="f6977-175">**Používání HttpClientFactory v .NET Core**</span><span class="sxs-lookup"><span data-stu-id="f6977-175">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="f6977-176">**Zdrojový kód HttpClientFactory v úložišti GitHub `aspnet/Extensions`**</span><span class="sxs-lookup"><span data-stu-id="f6977-176">**HttpClientFactory source code in the `aspnet/Extensions` GitHub repository**</span></span>  
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="f6977-177">**Polly (odolnost proti chybám .NET a knihovna pro zpracování s přechodnými chybami)**</span><span class="sxs-lookup"><span data-stu-id="f6977-177">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="f6977-178">**Použití HttpClientFactory bez injektáže závislosti (problém GitHubu)**</span><span class="sxs-lookup"><span data-stu-id="f6977-178">**Using HttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/aspnet/Extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="f6977-179">[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)
>[Další](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="f6977-179">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
