---
title: Implementace vzoru Circuit Breaker
description: Zjistěte, jak implementovat schéma jističe jako doplňkový systém opakování protokolu Http.
ms.date: 03/03/2020
ms.openlocfilehash: a79c6fcca1e29f3c30d697cb369060d59a72c121
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847242"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="8ae64-103">Implementace systému jističe</span><span class="sxs-lookup"><span data-stu-id="8ae64-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="8ae64-104">Jak již bylo uvedeno dříve, měli byste zpracovat chyby, které mohou trvat proměnné množství času zotavit se z, jak se může stát při pokusu o připojení ke vzdálené službě nebo prostředku.</span><span class="sxs-lookup"><span data-stu-id="8ae64-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="8ae64-105">Zpracování tohoto typu poruchy může zlepšit stabilitu a odolnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ae64-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="8ae64-106">V distribuovaném prostředí mohou volání vzdálených prostředků a služeb selhat z důvodu přechodných chyb, jako jsou pomalá síťová připojení a časové toky, nebo pokud prostředky reagují pomalu nebo jsou dočasně nedostupné.</span><span class="sxs-lookup"><span data-stu-id="8ae64-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="8ae64-107">Tyto chyby obvykle opravit sami po krátké době a robustní cloudová aplikace by měla být připravena k jejich zpracování pomocí strategie, jako je "Opakování vzor".</span><span class="sxs-lookup"><span data-stu-id="8ae64-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span>

<span data-ttu-id="8ae64-108">Mohou však také nastat situace, kdy jsou chyby způsobeny neočekávanými událostmi, které mohou trvat mnohem déle.</span><span class="sxs-lookup"><span data-stu-id="8ae64-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="8ae64-109">Tyto chyby můžou být různě závažné, od částečného výpadku připojení až po úplné selhání služby.</span><span class="sxs-lookup"><span data-stu-id="8ae64-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="8ae64-110">V těchto situacích může být zbytečné pro aplikaci neustále opakovat operaci, která je nepravděpodobné, že úspěšné.</span><span class="sxs-lookup"><span data-stu-id="8ae64-110">In these situations, it might be pointless for an application to continually retry an operation that's unlikely to succeed.</span></span>

<span data-ttu-id="8ae64-111">Místo toho by měla být aplikace kódována tak, aby akceptovala, že operace selhala, a odpovídajícím způsobem zpracovat selhání.</span><span class="sxs-lookup"><span data-stu-id="8ae64-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="8ae64-112">Použití http opakování nedbale může mít za následek vytvoření útoku odmítnutí služby[(DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)v rámci vlastního softwaru.</span><span class="sxs-lookup"><span data-stu-id="8ae64-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="8ae64-113">Jako mikroslužba selže nebo provádí pomalu, více klientů může opakovaně opakovat neúspěšné požadavky.</span><span class="sxs-lookup"><span data-stu-id="8ae64-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="8ae64-114">To vytváří nebezpečné riziko exponenciálně rostoucího provozu zaměřeného na selhávající službu.</span><span class="sxs-lookup"><span data-stu-id="8ae64-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="8ae64-115">Proto potřebujete nějakou obrannou bariéru, aby se nadměrné požadavky zastavily, když to nestojí za to, aby se snažil.</span><span class="sxs-lookup"><span data-stu-id="8ae64-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it isn't worth to keep trying.</span></span> <span data-ttu-id="8ae64-116">Ta obranná bariéra je přesně jistič.</span><span class="sxs-lookup"><span data-stu-id="8ae64-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="8ae64-117">Vzor jističe má jiný účel než "Opakovat vzor".</span><span class="sxs-lookup"><span data-stu-id="8ae64-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="8ae64-118">"Opakovat vzor" umožňuje aplikaci opakovat operaci v očekávání, že operace bude nakonec úspěšné.</span><span class="sxs-lookup"><span data-stu-id="8ae64-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="8ae64-119">Vzor jistič zabrání aplikaci provádět operace, která je pravděpodobně nezdaří.</span><span class="sxs-lookup"><span data-stu-id="8ae64-119">The Circuit Breaker pattern prevents an application from performing an operation that's likely to fail.</span></span> <span data-ttu-id="8ae64-120">Aplikace může kombinovat tyto dva vzory.</span><span class="sxs-lookup"><span data-stu-id="8ae64-120">An application can combine these two patterns.</span></span> <span data-ttu-id="8ae64-121">Logika opakování by však měla být citlivá na jakoukoli výjimku vrácenou jističem a měla by opustit pokusy o opakování, pokud jistič indikuje, že chyba není přechodná.</span><span class="sxs-lookup"><span data-stu-id="8ae64-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-ihttpclientfactory-and-polly"></a><span data-ttu-id="8ae64-122">Implementujte schéma `IHttpClientFactory` jističe s Polly a Polly</span><span class="sxs-lookup"><span data-stu-id="8ae64-122">Implement Circuit Breaker pattern with `IHttpClientFactory` and Polly</span></span>

<span data-ttu-id="8ae64-123">Stejně jako při implementaci opakování je doporučeným přístupem pro jističe využít osvědčené knihovny .NET, jako je Polly a jeho nativní integrace s `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="8ae64-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with `IHttpClientFactory`.</span></span>

<span data-ttu-id="8ae64-124">Přidání zásad jističe `IHttpClientFactory` do odchozího kanálu middlewaru je stejně jednoduché jako přidání jednoho `IHttpClientFactory`přírůstkového kódu k tomu, co již máte při použití .</span><span class="sxs-lookup"><span data-stu-id="8ae64-124">Adding a circuit breaker policy into your `IHttpClientFactory` outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using `IHttpClientFactory`.</span></span>

<span data-ttu-id="8ae64-125">Jediným doplňkem kódu použitého pro opakování volání HTTP je kód, ve kterém přidáte zásadu jističe do seznamu zásad, které chcete použít, jak je znázorněno v následujícím přírůstkovém kódu, který je součástí metody ConfigureServices().</span><span class="sxs-lookup"><span data-stu-id="8ae64-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="8ae64-126">Metoda `AddPolicyHandler()` je to, co `HttpClient` přidává zásady k objektům, které budete používat.</span><span class="sxs-lookup"><span data-stu-id="8ae64-126">The `AddPolicyHandler()` method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="8ae64-127">V tomto případě je to přidání Polly politiky pro jistič.</span><span class="sxs-lookup"><span data-stu-id="8ae64-127">In this case, it's adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="8ae64-128">Chcete-li mít více modulární přístup, jistič zásady `GetCircuitBreakerPolicy()`je definována v samostatné metodě s názvem , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8ae64-128">To have a more modular approach, the Circuit Breaker Policy is defined in a separate method called `GetCircuitBreakerPolicy()`, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="8ae64-129">V příkladu kódu výše je nakonfigurován ajistič zásady tak, aby se přeruší nebo otevře okruh, když došlo k pěti po sobě jdoucích chyb při opakování požadavků http.</span><span class="sxs-lookup"><span data-stu-id="8ae64-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="8ae64-130">Když se to stane, obvod se zlomí po dobu 30 sekund: v tomto období budou volání okamžitě neúspěšná jističem, spíše než skutečně umístěna.</span><span class="sxs-lookup"><span data-stu-id="8ae64-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="8ae64-131">Zásada automaticky interpretuje [příslušné výjimky a stavové kódy HTTP](/aspnet/core/fundamentals/http-requests#handle-transient-faults) jako chyby.</span><span class="sxs-lookup"><span data-stu-id="8ae64-131">The policy automatically interprets [relevant exceptions and HTTP status codes](/aspnet/core/fundamentals/http-requests#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="8ae64-132">Jističe by měly být také použity k přesměrování požadavků na záložní infrastrukturu, pokud jste měli problémy v určitém prostředku, který je nasazen v jiném prostředí než klientská aplikace nebo služba, která provádí volání HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ae64-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that's deployed in a different environment than the client application or service that's performing the HTTP call.</span></span> <span data-ttu-id="8ae64-133">Tímto způsobem pokud je výpadek v datovém centru, který má vliv pouze na vaše back-endové mikroslužby, ale ne klientské aplikace, klientské aplikace můžete přesměrovat na záložní služby.</span><span class="sxs-lookup"><span data-stu-id="8ae64-133">That way, if there's an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="8ae64-134">Polly plánuje novou zásadu pro automatizaci tohoto scénáře [zásad převzetí služeb při selhání.](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)</span><span class="sxs-lookup"><span data-stu-id="8ae64-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="8ae64-135">Všechny tyto funkce jsou pro případy, kdy spravujete převzetí služeb při selhání z v rámci kódu .NET, na rozdíl od toho, že ho spravujete automaticky azure, s transparentností umístění.</span><span class="sxs-lookup"><span data-stu-id="8ae64-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

<span data-ttu-id="8ae64-136">Z hlediska využití, při použití HttpClient, není třeba přidávat nic nového zde, protože `HttpClient` kód `IHttpClientFactory`je stejný jako při použití s , jak je znázorněno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="8ae64-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using `HttpClient` with `IHttpClientFactory`, as shown in previous sections.</span></span>

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="8ae64-137">Testování http opakování a jističů v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="8ae64-137">Test Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="8ae64-138">Při každém spuštění řešení eShopOnContainers v hostiteli Dockeru, je potřeba spustit více kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="8ae64-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="8ae64-139">Některé kontejnery jsou pomalejší spuštění a inicializovat, jako je kontejner serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8ae64-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="8ae64-140">To platí zejména při prvním nasazení aplikace eShopOnContainers do Dockeru, protože potřebuje nastavit bitové kopie a databázi.</span><span class="sxs-lookup"><span data-stu-id="8ae64-140">This is especially true the first time you deploy the eShopOnContainers application into Docker because it needs to set up the images and the database.</span></span> <span data-ttu-id="8ae64-141">Skutečnost, že některé kontejnery spustit pomaleji než ostatní může způsobit, že zbytek služeb zpočátku vyvolat výjimky HTTP, i v případě, že nastavíte závislosti mezi kontejnery na úrovni docker-compose, jak je vysvětleno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="8ae64-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="8ae64-142">Tyto docker-compose závislosti mezi kontejnery jsou pouze na úrovni procesu.</span><span class="sxs-lookup"><span data-stu-id="8ae64-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="8ae64-143">Proces vstupního bodu kontejneru může být spuštěn, ale SQL Server nemusí být připraven pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="8ae64-143">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="8ae64-144">Výsledkem může být kaskáda chyb a aplikace může získat výjimku při pokusu o využití tohoto konkrétního kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8ae64-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="8ae64-145">Tento typ chyby se může zobrazit také při spuštění při nasazování aplikace do cloudu.</span><span class="sxs-lookup"><span data-stu-id="8ae64-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="8ae64-146">V takovém případě může orchestrátory přesouvání kontejnerů z jednoho uzlu nebo virtuálního uživatele do jiného (to znamená spuštění nových instancí) při vyrovnávání počtu kontejnerů mezi uzly clusteru.</span><span class="sxs-lookup"><span data-stu-id="8ae64-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="8ae64-147">Způsob, jakým 'eShopOnContainers' řeší tyto problémy při spuštění všech kontejnerů je pomocí opakování vzor ilustrované dříve.</span><span class="sxs-lookup"><span data-stu-id="8ae64-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span>

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="8ae64-148">Otestujte jistič v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="8ae64-148">Test the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="8ae64-149">Existuje několik způsobů, jak můžete přerušit/ otevřít obvod a otestovat jej pomocí eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8ae64-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="8ae64-150">Jednou z možností je snížit povolený počet opakování na 1 v zásadě jističe a znovu nasadit celé řešení do Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8ae64-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="8ae64-151">Při jednom opakování je pravděpodobné, že požadavek HTTP se nezdaří během nasazení, jistič se otevře a zobrazí se chyba.</span><span class="sxs-lookup"><span data-stu-id="8ae64-151">With a single retry, there's a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="8ae64-152">Další možností je použití vlastního middlewaru, který je implementován v mikroslužbě **košíku.**</span><span class="sxs-lookup"><span data-stu-id="8ae64-152">Another option is to use custom middleware that's implemented in the **Basket** microservice.</span></span> <span data-ttu-id="8ae64-153">Pokud je tento middleware povolen, zachytí všechny požadavky HTTP a vrátí stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="8ae64-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="8ae64-154">Middleware můžete povolit tak, že požadavek GET na selhání URI, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="8ae64-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`\
  <span data-ttu-id="8ae64-155">Tento požadavek vrátí aktuální stav middleware.</span><span class="sxs-lookup"><span data-stu-id="8ae64-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="8ae64-156">Pokud je middleware povoleno, požadavek vrátí stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="8ae64-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="8ae64-157">Pokud je middleware zakázáno, neexistuje žádná odpověď.</span><span class="sxs-lookup"><span data-stu-id="8ae64-157">If the middleware is disabled, there's no response.</span></span>

- `GET http://localhost:5103/failing?enable`\
  <span data-ttu-id="8ae64-158">Tento požadavek umožňuje middleware.</span><span class="sxs-lookup"><span data-stu-id="8ae64-158">This request enables the middleware.</span></span>

- `GET http://localhost:5103/failing?disable`\
  <span data-ttu-id="8ae64-159">Tento požadavek zakáže middleware.</span><span class="sxs-lookup"><span data-stu-id="8ae64-159">This request disables the middleware.</span></span>

<span data-ttu-id="8ae64-160">Například, jakmile je aplikace spuštěna, můžete povolit middleware tím, že žádost pomocí následujícího URI v libovolném prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="8ae64-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="8ae64-161">Všimněte si, že objednávání mikroslužby používá port 5103.</span><span class="sxs-lookup"><span data-stu-id="8ae64-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable`

<span data-ttu-id="8ae64-162">Stav pak můžete zkontrolovat pomocí `http://localhost:5103/failing`identifikátoru URI , jak je znázorněno na obrázku 8-5.</span><span class="sxs-lookup"><span data-stu-id="8ae64-162">You can then check the status using the URI `http://localhost:5103/failing`, as shown in Figure 8-5.</span></span>

![Snímek obrazovky se zjišnou stavem neúspěšné simulace middlewaru.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

<span data-ttu-id="8ae64-164">**Obrázek 8-5**.</span><span class="sxs-lookup"><span data-stu-id="8ae64-164">**Figure 8-5**.</span></span> <span data-ttu-id="8ae64-165">Kontrola stavu "Selhání" ASP.NET middleware – V tomto případě zakázáno.</span><span class="sxs-lookup"><span data-stu-id="8ae64-165">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span>

<span data-ttu-id="8ae64-166">V tomto okamžiku mikroslužby košíku odpoví stavový kód 500 při každém volání vyvolat.</span><span class="sxs-lookup"><span data-stu-id="8ae64-166">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="8ae64-167">Jakmile je middleware spuštěn, můžete zkusit objednávku z webové aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="8ae64-167">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="8ae64-168">Protože požadavky se nezdaří, okruh se otevře.</span><span class="sxs-lookup"><span data-stu-id="8ae64-168">Because the requests fail, the circuit will open.</span></span>

<span data-ttu-id="8ae64-169">V následujícím příkladu uvidíte, že webová aplikace MVC má blok catch v logice pro zadání objednávky.</span><span class="sxs-lookup"><span data-stu-id="8ae64-169">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="8ae64-170">Pokud kód zachytí výjimku otevřeného okruhu, zobrazí uživateli popisnou zprávu s oznámením, aby počkali.</span><span class="sxs-lookup"><span data-stu-id="8ae64-170">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            var user = _appUserParser.Parse(HttpContext.User);
            //Http requests using the Typed Client (Service Agent)
            var vm = await _basketSvc.GetBasket(user);
            return View(vm);
        }
        catch (BrokenCircuitException)
        {
            // Catches error when Basket.api is in circuit-opened mode
            HandleBrokenCircuitException();
        }
        return View();
    }

    private void HandleBrokenCircuitException()
    {
        TempData["BasketInoperativeMsg"] = "Basket Service is inoperative, please try later on. (Business message due to Circuit-Breaker)";
    }
}
```

<span data-ttu-id="8ae64-171">Zde je shrnutí.</span><span class="sxs-lookup"><span data-stu-id="8ae64-171">Here’s a summary.</span></span> <span data-ttu-id="8ae64-172">Zásada opakování se několikrát pokusí vytvořit požadavek HTTP a získá chyby PROTOKOLU HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ae64-172">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="8ae64-173">Když počet opakování dosáhne maximální počet nastavený pro zásady jistič (v tomto případě 5), aplikace vyvolá BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="8ae64-173">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="8ae64-174">Výsledkem je přátelská zpráva, jak je znázorněno na obrázku 8-6.</span><span class="sxs-lookup"><span data-stu-id="8ae64-174">The result is a friendly message, as shown in Figure 8-6.</span></span>

![Snímek obrazovky s webovou aplikací MVC s nefunkční chybou služby košíku](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

<span data-ttu-id="8ae64-176">**Obrázek 8-6**.</span><span class="sxs-lookup"><span data-stu-id="8ae64-176">**Figure 8-6**.</span></span> <span data-ttu-id="8ae64-177">Jistič vracející chybu do ui</span><span class="sxs-lookup"><span data-stu-id="8ae64-177">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="8ae64-178">Můžete implementovat různé logiky pro otevření/přerušení obvodu.</span><span class="sxs-lookup"><span data-stu-id="8ae64-178">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="8ae64-179">Nebo můžete zkusit požadavek HTTP proti jiné back-end mikroslužby, pokud existuje záložní datové centrum nebo redundantní back-end systému.</span><span class="sxs-lookup"><span data-stu-id="8ae64-179">Or you can try an HTTP request against a different back-end microservice if there's a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="8ae64-180">A konečně, `CircuitBreakerPolicy` další možností `Isolate` pro použití (který nutí otevřít `Reset` a drží otevřít obvod) a (který jej zavře znovu).</span><span class="sxs-lookup"><span data-stu-id="8ae64-180">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="8ae64-181">Ty by mohly být použity k vytvoření koncového bodu http nástroje, který vyvolá Izolovat a Obnovit přímo na zásady.</span><span class="sxs-lookup"><span data-stu-id="8ae64-181">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="8ae64-182">Takový koncový bod HTTP by také mohl být použit, vhodně zabezpečený, v produkčním prostředí pro dočasně izolaci navazujícího systému, například když jej chcete upgradovat.</span><span class="sxs-lookup"><span data-stu-id="8ae64-182">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="8ae64-183">Nebo by to mohlo zakopnout oklikou ručně, aby byl chráněn navazující systém, o kterých máte podezření, že je vadný.</span><span class="sxs-lookup"><span data-stu-id="8ae64-183">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8ae64-184">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8ae64-184">Additional resources</span></span>

- <span data-ttu-id="8ae64-185">**Vzor jističe**</span><span class="sxs-lookup"><span data-stu-id="8ae64-185">**Circuit Breaker pattern**</span></span>\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
><span data-ttu-id="8ae64-186">[Předchozí](implement-http-call-retries-exponential-backoff-polly.md)
>[další](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="8ae64-186">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
