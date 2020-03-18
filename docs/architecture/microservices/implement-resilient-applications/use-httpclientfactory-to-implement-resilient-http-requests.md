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
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="1675d-103">Použití nástroje IHttpClientFactory k implementaci odolných požadavků HTTP</span><span class="sxs-lookup"><span data-stu-id="1675d-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="1675d-104"><xref:System.Net.Http.IHttpClientFactory>je smlouva implementovaná společností `DefaultHttpClientFactory`, umíněnou továrnou, která je <xref:System.Net.Http.HttpClient> k dispozici od rozhraní .NET Core 2.1, pro vytváření instancí, které mají být použity ve vašich aplikacích.</span><span class="sxs-lookup"><span data-stu-id="1675d-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="1675d-105">Problémy s původní třídou HttpClient dostupnou v jádru rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="1675d-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="1675d-106">Původní a dobře <xref:System.Net.Http.HttpClient> známé třídy lze snadno použít, ale v některých případech není správně používán mnoha vývojáři.</span><span class="sxs-lookup"><span data-stu-id="1675d-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="1675d-107">Zatímco tato třída `IDisposable`implementuje , deklarování `using` a vytváření instancí v rámci příkazu není upřednostňována, protože když `HttpClient` je objekt vyřazen, základní soket není okamžitě uvolněna, což může vést k problému vyčerpání _soketu._</span><span class="sxs-lookup"><span data-stu-id="1675d-107">While this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="1675d-108">Další informace o tomto problému naleznete v příspěvku blogu [Používáte httpclient špatně a destabilizuje váš software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span><span class="sxs-lookup"><span data-stu-id="1675d-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="1675d-109">Proto `HttpClient` je určen k vytvoření instance jednou a znovu použít po celou dobu životnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="1675d-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="1675d-110">Vytvoření instance `HttpClient` třídy pro každý požadavek vyčerpá počet zásuvek, které jsou k dispozici při velkém zatížení.</span><span class="sxs-lookup"><span data-stu-id="1675d-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="1675d-111">Tento problém bude `SocketException` mít za následek chyby.</span><span class="sxs-lookup"><span data-stu-id="1675d-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="1675d-112">Možné přístupy k řešení tohoto problému `HttpClient` jsou založeny na vytvoření objektu jako singleton nebo statické, jak je vysvětleno v tomto [článku společnosti Microsoft o využití httpclient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="1675d-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="1675d-113">To může být dobrým řešením pro krátkodobé konzolové aplikace nebo podobné aplikace, které jsou spuštěny několikrát denně.</span><span class="sxs-lookup"><span data-stu-id="1675d-113">This can be a good solution for short-lived console apps or similar that are run a few times a day.</span></span>

<span data-ttu-id="1675d-114">Dalším problémem, který vývojáři spustit `HttpClient` je při použití sdílené instance v dlouho běžící procesy.</span><span class="sxs-lookup"><span data-stu-id="1675d-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long running processes.</span></span> <span data-ttu-id="1675d-115">V situaci, kdy httpclient je vytvořena instance jako singleton nebo statický objekt, nedokáže zpracovat změny DNS, jak je popsáno v tomto [vydání](https://github.com/dotnet/corefx/issues/11224) úložiště Dotnet/corefx GitHub.</span><span class="sxs-lookup"><span data-stu-id="1675d-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/corefx/issues/11224) of the dotnet/corefx GitHub repository.</span></span>

<span data-ttu-id="1675d-116">Problém však není ve `HttpClient` skutečnosti s sám o sobě, ale s [výchozím konstruktorem pro HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), protože vytvoří novou konkrétní instanci <xref:System.Net.Http.HttpMessageHandler>, což je ten, který má vyčerpání *soketů* a dns změny problémy uvedené výše.</span><span class="sxs-lookup"><span data-stu-id="1675d-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="1675d-117">Chcete-li řešit výše uvedené `HttpClient` problémy a aby instance spravovatelné, .NET Core 2.1 <xref:System.Net.Http.IHttpClientFactory> představil `HttpClient` rozhraní, které lze použít ke konfiguraci a vytvoření instance v aplikaci prostřednictvím vkládání závislostí (DI).</span><span class="sxs-lookup"><span data-stu-id="1675d-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="1675d-118">Poskytuje také rozšíření pro middleware založené na Polly využít delegování obslužné rutiny v HttpClient.</span><span class="sxs-lookup"><span data-stu-id="1675d-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="1675d-119">[Polly](http://www.thepollyproject.org/) je knihovna pro zpracování přechodných chyb, která vývojářům pomáhá přidávat odolnost k aplikacím pomocí některých předdefinovaných zásad plynulým způsobem a bezpečným pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="1675d-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="1675d-120">Výhody používání ihttpclientfactory</span><span class="sxs-lookup"><span data-stu-id="1675d-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="1675d-121">Současná implementace <xref:System.Net.Http.IHttpClientFactory>, která <xref:System.Net.Http.IHttpMessageHandlerFactory>také implementuje , nabízí následující výhody:</span><span class="sxs-lookup"><span data-stu-id="1675d-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="1675d-122">Poskytuje centrální umístění pro pojmenování `HttpClient` a konfiguraci logických objektů.</span><span class="sxs-lookup"><span data-stu-id="1675d-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="1675d-123">Můžete například nakonfigurovat klienta (agenta služby), který je předem nakonfigurován pro přístup k určité mikroslužbě.</span><span class="sxs-lookup"><span data-stu-id="1675d-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="1675d-124">Kodifikovat koncept odchozí middleware prostřednictvím delegování manipulátory a `HttpClient` provádění Polly-založené middleware využít polly politiky pro odolnost.</span><span class="sxs-lookup"><span data-stu-id="1675d-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="1675d-125">`HttpClient`již má koncept delegování obslužné rutiny, které by mohly být propojeny pro odchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="1675d-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="1675d-126">Klienty HTTP můžete zaregistrovat do továrny a můžete použít polly obslužnou rutinu k použití polly zásad pro opakování, jističe a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1675d-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="1675d-127">Spravujte životnost, <xref:System.Net.Http.HttpMessageHandler> abyste se vyhnuli uvedeným problémům `HttpClient` nebo problémům, které mohou nastat při správě životnosti sami.</span><span class="sxs-lookup"><span data-stu-id="1675d-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="1675d-128">Instance `HttpClient` injekčně DI, lze zlikvidovat bezpečně, protože přidružené `HttpMessageHandler` je spravována factory.</span><span class="sxs-lookup"><span data-stu-id="1675d-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="1675d-129">Jako ve skutečnosti injekčně `HttpClient` instance jsou *Scoped* z hlediska DI.</span><span class="sxs-lookup"><span data-stu-id="1675d-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="1675d-130">Implementace `IHttpClientFactory` (`DefaultHttpClientFactory`) je úzce vázána na `Microsoft.Extensions.DependencyInjection` implementaci DI v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="1675d-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="1675d-131">Další informace o používání jiných kontejnerů DI najdete v této [diskusi githubu](https://github.com/dotnet/extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="1675d-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="1675d-132">Více způsobů použití ihttpclientfactory</span><span class="sxs-lookup"><span data-stu-id="1675d-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="1675d-133">Existuje několik způsobů, které `IHttpClientFactory` můžete použít v aplikaci:</span><span class="sxs-lookup"><span data-stu-id="1675d-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="1675d-134">Základní použití</span><span class="sxs-lookup"><span data-stu-id="1675d-134">Basic usage</span></span>
- <span data-ttu-id="1675d-135">Použít pojmenované klienty</span><span class="sxs-lookup"><span data-stu-id="1675d-135">Use Named Clients</span></span>
- <span data-ttu-id="1675d-136">Použít zadané klienty</span><span class="sxs-lookup"><span data-stu-id="1675d-136">Use Typed Clients</span></span>
- <span data-ttu-id="1675d-137">Použít generované klienty</span><span class="sxs-lookup"><span data-stu-id="1675d-137">Use Generated Clients</span></span>

<span data-ttu-id="1675d-138">Z důvodu stručnosti tento návod ukazuje nejstrukturovanější způsob `IHttpClientFactory`použití , který je použití zadali klienty (Service Agent vzor).</span><span class="sxs-lookup"><span data-stu-id="1675d-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="1675d-139">Všechny možnosti jsou však zdokumentovány a jsou aktuálně uvedeny v tomto [článku týkající se `IHttpClientFactory` použití](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="1675d-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="1675d-140">Použití zadalicích klientů s iHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="1675d-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="1675d-141">Takže, co je "napsaná klientka"?</span><span class="sxs-lookup"><span data-stu-id="1675d-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="1675d-142">Je to `HttpClient` jen, který je předem nakonfigurován pro určité konkrétní použití.</span><span class="sxs-lookup"><span data-stu-id="1675d-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="1675d-143">Tato konfigurace může obsahovat určité hodnoty, jako je například základní server, hlavičky HTTP nebo časové výběhy.</span><span class="sxs-lookup"><span data-stu-id="1675d-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="1675d-144">Následující diagram znázorňuje, jak `IHttpClientFactory`jsou klienti typem používáni s :</span><span class="sxs-lookup"><span data-stu-id="1675d-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![Diagram znázorňující, jak jsou zadali klienti s IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="1675d-146">**Obrázek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="1675d-146">**Figure 8-4**.</span></span> <span data-ttu-id="1675d-147">Použití `IHttpClientFactory` s třídami Typed Client.</span><span class="sxs-lookup"><span data-stu-id="1675d-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="1675d-148">Ve výše uvedenébitové bitové `ClientService` kopii používá (používaný řadičem nebo klientským kódem) `HttpClient` vytvořený registrovaným `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="1675d-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="1675d-149">Tato továrna `HttpMessageHandler` přiřadí z `HttpClient`fondu do .</span><span class="sxs-lookup"><span data-stu-id="1675d-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="1675d-150">Lze `HttpClient` nakonfigurovat s polly zásady při `IHttpClientFactory` registraci v kontejneru <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>DI s metodou rozšíření .</span><span class="sxs-lookup"><span data-stu-id="1675d-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>.</span></span>

<span data-ttu-id="1675d-151">Chcete-li nakonfigurovat <xref:System.Net.Http.IHttpClientFactory> výše uvedenou strukturu, přidejte do aplikace instalací balíčku `Microsoft.Extensions.Http` NuGet, který obsahuje metodu <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> rozšíření pro <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>aplikaci .</span><span class="sxs-lookup"><span data-stu-id="1675d-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="1675d-152">Tato metoda rozšíření registruje vnitřní `DefaultHttpClientFactory` třídy, které mají `IHttpClientFactory`být použity jako singleton pro rozhraní .</span><span class="sxs-lookup"><span data-stu-id="1675d-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="1675d-153">Definuje přechodnou konfiguraci pro <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span><span class="sxs-lookup"><span data-stu-id="1675d-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="1675d-154">Tato obslužná rutina zprávy (<xref:System.Net.Http.HttpMessageHandler> `HttpClient` objekt), převzata z fondu, se používá vrácené z výroby.</span><span class="sxs-lookup"><span data-stu-id="1675d-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="1675d-155">V dalším kódu můžete vidět, jak `AddHttpClient()` lze zaregistrovat zadané klienty (service `HttpClient`agents), které je třeba použít .</span><span class="sxs-lookup"><span data-stu-id="1675d-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="1675d-156">Registrace klientských služeb, jak je znázorněno `DefaultClientFactory` v `HttpClient` předchozím kódu, vytvoří vytvořit standard pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="1675d-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="1675d-157">Můžete také přidat konfiguraci specifickou pro instanci v registraci, například ke konfiguraci základní adresy a přidat některé zásady odolnosti proti chybám, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1675d-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="1675d-158">Jen pro příklad, můžete vidět jednu z výše uvedených zásad v dalším kódu:</span><span class="sxs-lookup"><span data-stu-id="1675d-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="1675d-159">Další podrobnosti o používání Polly najdete v [dalším článku](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="1675d-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="1675d-160">Životnost httpclientu</span><span class="sxs-lookup"><span data-stu-id="1675d-160">HttpClient lifetimes</span></span>

<span data-ttu-id="1675d-161">Pokaždé, když `HttpClient` získáte objekt `IHttpClientFactory`z , je vrácena nová instance.</span><span class="sxs-lookup"><span data-stu-id="1675d-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="1675d-162">Ale `HttpClient` každý `HttpMessageHandler` používá, který je sdružený a znovu použít `IHttpClientFactory` `HttpMessageHandler`ke snížení spotřeby prostředků, tak dlouho, dokud 's životnost nevypršela.</span><span class="sxs-lookup"><span data-stu-id="1675d-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="1675d-163">Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje vlastní základní připojení HTTP; vytvoření více obslužných rutin, než je nutné, může mít za následek zpoždění připojení.</span><span class="sxs-lookup"><span data-stu-id="1675d-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="1675d-164">Některé obslužné rutiny také udržují připojení otevřená po neomezenou dobu, což může zabránit tomu, aby obslužná rutina reagovala na změny DNS.</span><span class="sxs-lookup"><span data-stu-id="1675d-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="1675d-165">Objekty `HttpMessageHandler` ve fondu mají životnost, která je doba, po kterou lze `HttpMessageHandler` znovu použít instanci ve fondu.</span><span class="sxs-lookup"><span data-stu-id="1675d-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="1675d-166">Výchozí hodnota je dvě minuty, ale může být přepsána na zadaného klienta.</span><span class="sxs-lookup"><span data-stu-id="1675d-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="1675d-167">Chcete-li jej `SetHandlerLifetime()` přepsat, <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> volejte na to, který je vrácen při vytváření klienta, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1675d-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="1675d-168">Každý zadaný klient může mít vlastní nakonfigurovanou hodnotu životnosti obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="1675d-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="1675d-169">Nastavte životnost `InfiniteTimeSpan` zakázat vypršení platnosti obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="1675d-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="1675d-170">Implementace tříd zadaného klienta, které používají vložený a nakonfigurovaný httpclient</span><span class="sxs-lookup"><span data-stu-id="1675d-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="1675d-171">Jako předchozí krok musíte mít zadané třídy klienta definované, jako jsou třídy v ukázkovém kódu, jako je "BasketService", "CatalogService", "OrderingService", atd. – Typovaný klient je třída, která přijímá `HttpClient` objekt (vložený prostřednictvím jeho konstruktoru) a používá jej k volání některé vzdálené služby HTTP.</span><span class="sxs-lookup"><span data-stu-id="1675d-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="1675d-172">Například:</span><span class="sxs-lookup"><span data-stu-id="1675d-172">For example:</span></span>

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

<span data-ttu-id="1675d-173">Typed Client`CatalogService` ( v příkladu) je aktivován DI (Vkládání závislostí), což znamená, že může `HttpClient`přijmout všechny registrované služby v jeho konstruktoru, kromě .</span><span class="sxs-lookup"><span data-stu-id="1675d-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="1675d-174">Typed Client je efektivně přechodný objekt, což znamená, že nová instance je vytvořena pokaždé, `HttpClient` když je potřeba, a obdrží novou instanci pokaždé, když je vytvořena.</span><span class="sxs-lookup"><span data-stu-id="1675d-174">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="1675d-175">Objekty `HttpMessageHandler` ve fondu jsou však objekty, `HttpClient` které jsou znovu použity více instancí.</span><span class="sxs-lookup"><span data-stu-id="1675d-175">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="1675d-176">Použití tříd Zadaného klienta</span><span class="sxs-lookup"><span data-stu-id="1675d-176">Use your Typed Client classes</span></span>

<span data-ttu-id="1675d-177">Nakonec, jakmile budete mít zadané třídy implementovány `AddHttpClient()`a mít je registrovány a nakonfigurovány s , můžete je použít všude tam, kde můžete mít služby injekčně DI.</span><span class="sxs-lookup"><span data-stu-id="1675d-177">Finally, once you have your typed classes implemented and have them registered and configured with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="1675d-178">Například v kódu stránky Razor nebo řadiči webové aplikace MVC, jako v následujícím kódu z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="1675d-178">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="1675d-179">Až do tohoto okamžiku, zobrazený kód je pouze provádění pravidelných požadavků http, ale 'magie' přichází v následujících částech, kde pouhým přidáním zásad a delegování obslužné rutiny na registrované zadané klienty, všechny požadavky HTTP, které `HttpClient` mají být provedeny, se budou chovat s ohledem na odolné zásady, jako jsou opakované pokusy s exponenciálním vypnutím, jističi nebo jinými vlastními delegujícími obslužnými rutinami pro implementaci dalších funkcí zabezpečení, jako je použití auth tokenů nebo jakékoli jiné vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="1675d-179">Up to this point, the code shown is just performing regular Http requests, but the 'magic' comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1675d-180">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1675d-180">Additional resources</span></span>

- <span data-ttu-id="1675d-181">**Použití httpclientfactory v jádru rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="1675d-181">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="1675d-182">**Zdrojový kód HttpClientFactory `dotnet/extensions` v úložišti GitHub**</span><span class="sxs-lookup"><span data-stu-id="1675d-182">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="1675d-183">**Polly (knihovna odolnosti a zpracování přechodných chyb)**</span><span class="sxs-lookup"><span data-stu-id="1675d-183">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="1675d-184">**Použití IHttpClientFactory bez vkládání závislostí (problém GitHubu)**</span><span class="sxs-lookup"><span data-stu-id="1675d-184">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="1675d-185">[Předchozí](implement-resilient-entity-framework-core-sql-connections.md)
>[další](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="1675d-185">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
