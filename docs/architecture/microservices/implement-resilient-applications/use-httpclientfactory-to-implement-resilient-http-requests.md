---
title: Použití IHttpClientFactory k implementaci odolných požadavků HTTP
description: Naučte se používat IHttpClientFactory, k dispozici od .NET Core 2,1 pro vytváření `HttpClient` instancí, což usnadňuje jejich použití ve svých aplikacích.
ms.date: 08/31/2020
ms.openlocfilehash: 1df5432f215371b60722212cf706c28a4a5bb5f6
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271825"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="dd96c-103">Použití IHttpClientFactory k implementaci odolných požadavků HTTP</span><span class="sxs-lookup"><span data-stu-id="dd96c-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="dd96c-104"><xref:System.Net.Http.IHttpClientFactory> je kontraktem, který implementuje nástroj `DefaultHttpClientFactory` dogmatickým Factory, který je k dispozici od .NET Core 2,1 pro vytváření <xref:System.Net.Http.HttpClient> instancí, které se mají použít ve vašich aplikacích.</span><span class="sxs-lookup"><span data-stu-id="dd96c-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="dd96c-105">Problémy s původní třídou HttpClient dostupnou v .NET Core</span><span class="sxs-lookup"><span data-stu-id="dd96c-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="dd96c-106">Původní a dobře známou <xref:System.Net.Http.HttpClient> třídu lze snadno použít, ale v některých případech ji nepoužívá mnoho vývojářů.</span><span class="sxs-lookup"><span data-stu-id="dd96c-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="dd96c-107">I když tato třída implementuje `IDisposable` , deklaraci a vytvoření instance v rámci `using` příkazu není preferována, protože když dojde k `HttpClient` uvolnění objektu, základní soket není okamžitě uvolněn, což může vést k problému s _vyčerpáním soketu_ .</span><span class="sxs-lookup"><span data-stu-id="dd96c-107">Though this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="dd96c-108">Další informace o tomto problému najdete v blogovém příspěvku, [který používáte HttpClient, a který je destabilizující vašemu softwaru](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span><span class="sxs-lookup"><span data-stu-id="dd96c-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="dd96c-109">Proto `HttpClient` má být vytvořena instance jednou a znovu použita po celou dobu životnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="dd96c-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="dd96c-110">Vytvoření instance `HttpClient` třídy pro každý požadavek vyčerpá počet soketů, které jsou k dispozici v případě velkého zatížení.</span><span class="sxs-lookup"><span data-stu-id="dd96c-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="dd96c-111">K tomuto problému dojde v důsledku `SocketException` chyb.</span><span class="sxs-lookup"><span data-stu-id="dd96c-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="dd96c-112">Možné přístupy k vyřešení tohoto problému jsou založené na vytvoření `HttpClient` objektu jako singleton nebo static, jak je vysvětleno v tomto [článku o použití HttpClient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="dd96c-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="dd96c-113">Může to být dobré řešení pro krátkodobé konzolové aplikace nebo podobné, které běží několikrát denně.</span><span class="sxs-lookup"><span data-stu-id="dd96c-113">This can be a good solution for short-lived console apps or similar, that run a few times a day.</span></span>

<span data-ttu-id="dd96c-114">Dalším problémem, ve kterém se vývojáři spouštějí, je použití sdílené instance `HttpClient` v dlouhotrvajících procesech.</span><span class="sxs-lookup"><span data-stu-id="dd96c-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long-running processes.</span></span> <span data-ttu-id="dd96c-115">V situaci, kdy je instance HttpClient vytvořena jako typ singleton nebo statický objekt, se nedokáže zpracovat změny DNS, jak je popsáno v tomto [problému](https://github.com/dotnet/runtime/issues/18348) úložiště GitHub pro dotnet/modul runtime.</span><span class="sxs-lookup"><span data-stu-id="dd96c-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/runtime/issues/18348) of the dotnet/runtime GitHub repository.</span></span>

<span data-ttu-id="dd96c-116">Problém ale není v zásadě za se `HttpClient` , ale s [výchozím konstruktorem pro HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), protože vytvoří novou konkrétní instanci <xref:System.Net.Http.HttpMessageHandler> , která je v tom, který má *vyčerpání soketů* a DNS změny výše uvedené.</span><span class="sxs-lookup"><span data-stu-id="dd96c-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="dd96c-117">Rozhraní `HttpClient` .NET Core 2,1 představilo <xref:System.Net.Http.IHttpClientFactory> rozhraní, které se dá použít ke konfiguraci a vytváření `HttpClient` instancí v aplikaci prostřednictvím injektáže závislostí (di), aby vyřešilo výše uvedené problémy a aby bylo možné spravovat instance.</span><span class="sxs-lookup"><span data-stu-id="dd96c-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="dd96c-118">Poskytuje také rozšíření pro middleware založené na Polly, která umožňují využít výhod delegování obslužných rutin v HttpClient.</span><span class="sxs-lookup"><span data-stu-id="dd96c-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="dd96c-119">[Polly](http://www.thepollyproject.org/) je dočasná knihovna pro zpracování chyb, která vývojářům pomáhá zajistit odolnost proti svým aplikacím pomocí některých předdefinovaných zásad, které jsou bezpečné pro práci v Fluent a vlákně.</span><span class="sxs-lookup"><span data-stu-id="dd96c-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="dd96c-120">Výhody použití IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="dd96c-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="dd96c-121">Aktuální implementace <xref:System.Net.Http.IHttpClientFactory> , která také implementuje <xref:System.Net.Http.IHttpMessageHandlerFactory> , nabízí následující výhody:</span><span class="sxs-lookup"><span data-stu-id="dd96c-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="dd96c-122">Poskytuje centrální umístění pro pojmenovávání a konfiguraci logických `HttpClient` objektů.</span><span class="sxs-lookup"><span data-stu-id="dd96c-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="dd96c-123">Můžete například nakonfigurovat klienta (agenta služeb), který je předem nakonfigurovaný pro přístup k určité mikroslužbě.</span><span class="sxs-lookup"><span data-stu-id="dd96c-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="dd96c-124">Codify koncept odchozího middleware prostřednictvím delegování obslužných rutin v `HttpClient` a implementace middleware založeného na Polly, který využívá zásady Polly pro zajištění odolnosti.</span><span class="sxs-lookup"><span data-stu-id="dd96c-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="dd96c-125">`HttpClient` již má koncepci delegování obslužných rutin, které by mohly být propojeny pro odchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="dd96c-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="dd96c-126">Můžete zaregistrovat klienty HTTP do továrny a pomocí obslužné rutiny Polly použít zásady Polly pro opakování, CircuitBreakers a tak dále.</span><span class="sxs-lookup"><span data-stu-id="dd96c-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="dd96c-127">Spravujte dobu života, <xref:System.Net.Http.HttpMessageHandler> abyste se vyhnuli uvedeným problémům nebo problémům, ke kterým může dojít při správě `HttpClient` životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="dd96c-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="dd96c-128">`HttpClient`Instance vložené pomocí di mohou být odstraněny bezpečně, protože přidružený `HttpMessageHandler` je spravováno objektem pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="dd96c-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="dd96c-129">Vzhledem k tomu, že vložené `HttpClient` instance jsou *vymezené* z di perspektivy.</span><span class="sxs-lookup"><span data-stu-id="dd96c-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="dd96c-130">Implementace `IHttpClientFactory` ( `DefaultHttpClientFactory` ) je úzce svázána s implementací di v `Microsoft.Extensions.DependencyInjection` balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="dd96c-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="dd96c-131">Další informace o použití jiných kontejnerů DI najdete v této [diskuzi na GitHubu](https://github.com/dotnet/extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="dd96c-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="dd96c-132">Několik způsobů použití IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="dd96c-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="dd96c-133">V aplikaci můžete použít několik způsobů `IHttpClientFactory` :</span><span class="sxs-lookup"><span data-stu-id="dd96c-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="dd96c-134">Základní použití</span><span class="sxs-lookup"><span data-stu-id="dd96c-134">Basic usage</span></span>
- <span data-ttu-id="dd96c-135">Použití pojmenovaných klientů</span><span class="sxs-lookup"><span data-stu-id="dd96c-135">Use Named Clients</span></span>
- <span data-ttu-id="dd96c-136">Použití typových klientů</span><span class="sxs-lookup"><span data-stu-id="dd96c-136">Use Typed Clients</span></span>
- <span data-ttu-id="dd96c-137">Použít vygenerované klienty</span><span class="sxs-lookup"><span data-stu-id="dd96c-137">Use Generated Clients</span></span>

<span data-ttu-id="dd96c-138">Pro účely zkrácení vám tento návod ukáže, jak se používá `IHttpClientFactory` , aby bylo možné použít typové klienty (model agenta služby).</span><span class="sxs-lookup"><span data-stu-id="dd96c-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="dd96c-139">Všechny možnosti jsou však zdokumentovány a jsou aktuálně uvedeny v tomto [článku, který se týká `IHttpClientFactory` využití](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="dd96c-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="dd96c-140">Jak používat typové klienty s IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="dd96c-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="dd96c-141">Co je to "Typový klient"?</span><span class="sxs-lookup"><span data-stu-id="dd96c-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="dd96c-142">Je to jenom ta `HttpClient` , která je předem nakonfigurovaná pro konkrétní použití.</span><span class="sxs-lookup"><span data-stu-id="dd96c-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="dd96c-143">Tato konfigurace může zahrnovat konkrétní hodnoty, jako je základní server, hlavičky protokolu HTTP nebo časové limity.</span><span class="sxs-lookup"><span data-stu-id="dd96c-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="dd96c-144">Následující diagram znázorňuje, jak se používají typové klienty s `IHttpClientFactory` :</span><span class="sxs-lookup"><span data-stu-id="dd96c-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![Diagram znázorňující, jak se používají typové klienty s IHttpClientFactory](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="dd96c-146">**Obrázek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="dd96c-146">**Figure 8-4**.</span></span> <span data-ttu-id="dd96c-147">Použití `IHttpClientFactory` s typovými třídami klienta.</span><span class="sxs-lookup"><span data-stu-id="dd96c-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="dd96c-148">Na výše uvedeném obrázku, a `ClientService` (používá ho řadič nebo kód klienta), používá `HttpClient` vytvořenou registrovanou `IHttpClientFactory` .</span><span class="sxs-lookup"><span data-stu-id="dd96c-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="dd96c-149">Tento objekt pro vytváření přiřadí `HttpMessageHandler` z fondu do `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="dd96c-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="dd96c-150">`HttpClient`Lze nakonfigurovat zásady Polly při registraci `IHttpClientFactory` v kontejneru di s metodou rozšíření <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> .</span><span class="sxs-lookup"><span data-stu-id="dd96c-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>.</span></span>

<span data-ttu-id="dd96c-151">Pokud chcete nakonfigurovat výše uvedenou strukturu, přidejte ji <xref:System.Net.Http.IHttpClientFactory> do své aplikace tak, že nainstalujete `Microsoft.Extensions.Http` balíček NuGet, který obsahuje <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> metodu rozšíření pro <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="dd96c-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="dd96c-152">Tato metoda rozšíření registruje interní `DefaultHttpClientFactory` třídu, která se má použít jako typ singleton pro rozhraní `IHttpClientFactory` .</span><span class="sxs-lookup"><span data-stu-id="dd96c-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="dd96c-153">Definuje přechodnou konfiguraci pro <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> .</span><span class="sxs-lookup"><span data-stu-id="dd96c-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="dd96c-154">Tato obslužná rutina zprávy ( <xref:System.Net.Http.HttpMessageHandler> objekt), která je pořízena z fondu, je používána `HttpClient` vrácenou z továrny.</span><span class="sxs-lookup"><span data-stu-id="dd96c-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="dd96c-155">V dalším kódu vidíte, jak `AddHttpClient()` se dá použít k registraci typových klientů (agentů služeb), které je potřeba použít `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="dd96c-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="dd96c-156">Registrace služeb klienta, jak je znázorněno v předchozím kódu, vytvoří `DefaultClientFactory` `HttpClient` pro každou službu Standard.</span><span class="sxs-lookup"><span data-stu-id="dd96c-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="dd96c-157">Můžete také přidat konfiguraci specifickou pro instanci v registraci, například nakonfigurovat základní adresu a přidat některé zásady odolnosti, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="dd96c-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="dd96c-158">Podobně jako v tomto příkladu vidíte jednu z výše uvedených zásad v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="dd96c-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="dd96c-159">Další podrobnosti o používání Polly najdete v [dalším článku](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="dd96c-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="dd96c-160">HttpClient doby života</span><span class="sxs-lookup"><span data-stu-id="dd96c-160">HttpClient lifetimes</span></span>

<span data-ttu-id="dd96c-161">Pokaždé, když získáte `HttpClient` objekt z `IHttpClientFactory` , je vrácena nová instance.</span><span class="sxs-lookup"><span data-stu-id="dd96c-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="dd96c-162">Každá z nich ale `HttpClient` používá `HttpMessageHandler` fond a znovu `IHttpClientFactory` ho používá ke snížení spotřeby prostředků, pokud `HttpMessageHandler` Doba života ještě nevypršela.</span><span class="sxs-lookup"><span data-stu-id="dd96c-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="dd96c-163">Sdružování obslužných rutin je žádoucí, protože každá obslužná rutina obvykle spravuje vlastní podkladová připojení HTTP; vytváření dalších obslužných rutin, než je potřeba, může způsobit zpoždění připojení.</span><span class="sxs-lookup"><span data-stu-id="dd96c-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="dd96c-164">Některé obslužné rutiny také udržují připojení otevřené po neomezenou dobu, což může zabránit obslužné rutině v rekomunikaci se změnami DNS.</span><span class="sxs-lookup"><span data-stu-id="dd96c-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="dd96c-165">`HttpMessageHandler`Objekty ve fondu mají dobu života, která je doba, po kterou `HttpMessageHandler` lze instanci ve fondu znovu použít.</span><span class="sxs-lookup"><span data-stu-id="dd96c-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="dd96c-166">Výchozí hodnota je dvě minuty, ale je možné ji přepsat na typového klienta.</span><span class="sxs-lookup"><span data-stu-id="dd96c-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="dd96c-167">Chcete-li ho přepsat, zavolejte `SetHandlerLifetime()` na <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> to, které je vráceno při vytváření klienta, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="dd96c-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="dd96c-168">Každý typový klient může mít svou vlastní nakonfigurovanou hodnotu životnosti obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="dd96c-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="dd96c-169">Nastavte dobu života na `InfiniteTimeSpan` Zakázat vypršení platnosti obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="dd96c-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="dd96c-170">Implementujte typové klientské třídy, které používají vložené a nakonfigurované HttpClient</span><span class="sxs-lookup"><span data-stu-id="dd96c-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="dd96c-171">Jako předchozí krok musíte mít definované vaše typové klientské třídy, například třídy v ukázkovém kódu, jako je například "BasketService", "CatalogService", "OrderingService" atd. – typový klient je třída, která přijímá `HttpClient` objekt (vložený prostřednictvím jeho konstruktoru) a používá ho k volání některé vzdálené služby HTTP.</span><span class="sxs-lookup"><span data-stu-id="dd96c-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="dd96c-172">Příklad:</span><span class="sxs-lookup"><span data-stu-id="dd96c-172">For example:</span></span>

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

<span data-ttu-id="dd96c-173">Typový klient ( `CatalogService` v příkladu) je aktivován pomocí příkazu di (vkládání závislostí), což znamená, že může přijmout jakoukoli registrovanou službu ve svém konstruktoru, kromě `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="dd96c-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), that means it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="dd96c-174">Typový klient je efektivně přechodný objekt, což znamená, že se vytvoří nová instance pokaždé, když je potřeba jedna.</span><span class="sxs-lookup"><span data-stu-id="dd96c-174">A Typed Client is effectively a transient object, that means a new instance is created each time one is needed.</span></span> <span data-ttu-id="dd96c-175">`HttpClient`Při každém sestavení dostane novou instanci.</span><span class="sxs-lookup"><span data-stu-id="dd96c-175">It receives a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="dd96c-176">`HttpMessageHandler`Objekty ve fondu však jsou objekty, které jsou opakovaně používány více `HttpClient` instancemi.</span><span class="sxs-lookup"><span data-stu-id="dd96c-176">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="dd96c-177">Použití typových klientských tříd</span><span class="sxs-lookup"><span data-stu-id="dd96c-177">Use your Typed Client classes</span></span>

<span data-ttu-id="dd96c-178">Nakonec, jakmile máte implementované typové třídy, můžete je zaregistrovat a konfigurovat pomocí `AddHttpClient()` .</span><span class="sxs-lookup"><span data-stu-id="dd96c-178">Finally, once you have your typed classes implemented, you can have them registered and configured with `AddHttpClient()`.</span></span> <span data-ttu-id="dd96c-179">Pak je můžete použít všude, kde mají služby vložené do DI.</span><span class="sxs-lookup"><span data-stu-id="dd96c-179">After that you can use them wherever have services injected by DI.</span></span> <span data-ttu-id="dd96c-180">Například v kódu stránky Razor nebo kontroleru webové aplikace MVC, jako v následujícím kódu z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="dd96c-180">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="dd96c-181">Až do tohoto okamžiku byl výše uvedený fragment kódu zobrazen pouze jako příklad provádění běžných požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="dd96c-181">Up to this point, the above code snippet has only shown the example of performing regular HTTP requests.</span></span> <span data-ttu-id="dd96c-182">Ale "Magic" přichází v následujících částech, kde se zobrazuje, jak všechny požadavky HTTP vytvořené nástrojem `HttpClient` můžou mít odolné zásady, jako jsou opakování exponenciálního omezení rychlostiu, přepínacích bodů, funkce zabezpečení s použitím ověřovacích tokenů nebo dokonce jakékoli jiné vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="dd96c-182">But the 'magic' comes in the following sections where it shows how all the HTTP requests made by `HttpClient`, can have resilient policies such as retries with exponential backoff, circuit breakers, security features using auth tokens, or even any other custom feature.</span></span> <span data-ttu-id="dd96c-183">A všechny z nich je možné provést pouhým přidáním zásad a delegování obslužných rutin do registrovaných typových klientů.</span><span class="sxs-lookup"><span data-stu-id="dd96c-183">And all of these can be done just by adding policies and delegating handlers to your registered Typed Clients.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="dd96c-184">Další zdroje informací</span><span class="sxs-lookup"><span data-stu-id="dd96c-184">Additional resources</span></span>

- <span data-ttu-id="dd96c-185">**Používání HttpClientFactory v .NET Core**</span><span class="sxs-lookup"><span data-stu-id="dd96c-185">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="dd96c-186">**Zdrojový kód HttpClientFactory v `dotnet/extensions` úložišti GitHubu**</span><span class="sxs-lookup"><span data-stu-id="dd96c-186">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="dd96c-187">**Polly (odolnost proti chybám .NET a knihovna pro zpracování s přechodnými chybami)**</span><span class="sxs-lookup"><span data-stu-id="dd96c-187">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="dd96c-188">**Použití IHttpClientFactory bez injektáže závislosti (problém GitHubu)**</span><span class="sxs-lookup"><span data-stu-id="dd96c-188">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="dd96c-189">[Předchozí](implement-resilient-entity-framework-core-sql-connections.md) 
> [Další](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="dd96c-189">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
