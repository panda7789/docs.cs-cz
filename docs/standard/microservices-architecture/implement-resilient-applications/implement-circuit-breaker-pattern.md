---
title: "Implementace vzoru jistič"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace vzoru jistič"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2a629e25a7565aaba156f68cf06d9a24b6c2b8b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="eb686-104">Implementace vzoru jistič</span><span class="sxs-lookup"><span data-stu-id="eb686-104">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="eb686-105">Jak jsme uvedli výše, by měla řídit chyb, které může trvat proměnné množství času dostat z, může dojít při pokusu o připojení k vzdálené služby nebo prostředku.</span><span class="sxs-lookup"><span data-stu-id="eb686-105">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="eb686-106">Tento typ chyby zpracování může zvýšit stabilitu a odolnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb686-106">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="eb686-107">V distribuovaném prostředí volání vzdálené prostředky a služby může selhat z důvodu přechodných chyb, jako je pomalé síťové připojení a vypršení časových limitů, nebo pokud jsou prostředky zpomalit nebo jsou dočasně nedostupné.</span><span class="sxs-lookup"><span data-stu-id="eb686-107">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="eb686-108">Tyto chyby obvykle opravte po krátkou dobu sami a je třeba připravit robustní cloudových aplikací k jejich zpracování pomocí strategie jako vzor opakování.</span><span class="sxs-lookup"><span data-stu-id="eb686-108">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="eb686-109">Však může také nastat situace, kde jsou chyb z důvodu neočekávané události, které může trvat déle, chcete-li odstranit.</span><span class="sxs-lookup"><span data-stu-id="eb686-109">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="eb686-110">Tyto chyby může být v rozsahu v závažnosti od částečné ztrátě připojení k úplnému selhání služby.</span><span class="sxs-lookup"><span data-stu-id="eb686-110">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="eb686-111">V těchto situacích může být zbytečný pro aplikaci neustále opakujte operaci, která je pravděpodobně úspěšné.</span><span class="sxs-lookup"><span data-stu-id="eb686-111">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="eb686-112">Místo toho by měly být napsané aplikace potvrďte, že operace se nezdařila a zpracování selhání odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="eb686-112">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="eb686-113">Vzor jistič má jiný účel než vzor opakování.</span><span class="sxs-lookup"><span data-stu-id="eb686-113">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="eb686-114">Vzor opakování povolí aplikaci opakovat operace v očekávání, který nakonec operace proběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="eb686-114">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="eb686-115">Vzor jistič brání aplikaci v provádění operace, která je pravděpodobně selžou.</span><span class="sxs-lookup"><span data-stu-id="eb686-115">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="eb686-116">Aplikace můžete kombinovat tyto dvě vzory pomocí vzoru opakování k vyvolání operace prostřednictvím jistič.</span><span class="sxs-lookup"><span data-stu-id="eb686-116">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="eb686-117">Ale logika opakovaných pokusů by měla být citlivé na jakékoli výjimky vrácený vypínač a pokud vypínač signalizuje, že chybu není přechodný ho měli abandon počet pokusů o opakování.</span><span class="sxs-lookup"><span data-stu-id="eb686-117">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="eb686-118">Implementace vzoru jistič s Polly</span><span class="sxs-lookup"><span data-stu-id="eb686-118">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="eb686-119">Jako při implementaci opakování, umožní využít Principy knihovny .NET, jako je Polly je doporučený postup pro moduly okruh dělení.</span><span class="sxs-lookup"><span data-stu-id="eb686-119">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="eb686-120">Při implementaci HTTP opakování, používá aplikace eShopOnContainers Polly jistič zásad.</span><span class="sxs-lookup"><span data-stu-id="eb686-120">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="eb686-121">Ve skutečnosti aplikace platí obě zásady pro třídu ResilientHttpClient nástroj.</span><span class="sxs-lookup"><span data-stu-id="eb686-121">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="eb686-122">Vždy, když použijete objekt typu ResilientHttpClient požadavků HTTP (od eShopOnContainers), budou uplatňovat obě tyto zásady, ale můžete přidat další zásady, příliš.</span><span class="sxs-lookup"><span data-stu-id="eb686-122">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="eb686-123">Pouze přidání sem do kód použitý pro opakování volání HTTP je kód, kdy přidáte jistič zásad do seznamu zásad použití, jak je znázorněno na konci následující kód:</span><span class="sxs-lookup"><span data-stu-id="eb686-123">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
            // number of retries
            6,
            // exponential backofff
            retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
            // on retry
            (exception, timeSpan, retryCount, context) =>
            {
                var msg = $"Retry {retryCount} implemented with Polly RetryPolicy " +
                    $"of {context.PolicyKey} " +
                    $"at {context.ExecutionKey}, " +
                    $"due to: {exception}.";
                _logger.LogWarning(msg);
                _logger.LogDebug(msg);
            }),
            Policy.Handle<HttpRequestException>()
                .CircuitBreakerAsync(
                    // number of exceptions before breaking circuit
                    5,
                    // time circuit opened before retry
                    TimeSpan.FromMinutes(1),
                    (exception, duration) =>
                    {
                        // on circuit opened
                        _logger.LogTrace("Circuit breaker opened");
                    },
                    () =>
                    {
                        // on circuit closed
                        _logger.LogTrace("Circuit breaker reset");
                    })
    };
}
```

<span data-ttu-id="eb686-124">Kód přidá zásadu pro obálku protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="eb686-124">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="eb686-125">Aby zásad definuje jistič, které se otevře při kód zjistí zadaný počet po sobě jdoucích výjimek (výjimky v řádku), jako předán v parametru exceptionsAllowedBeforeBreaking (v tomto případě 5).</span><span class="sxs-lookup"><span data-stu-id="eb686-125">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="eb686-126">Když okruh je otevřená, nefungují požadavků HTTP, ale je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="eb686-126">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="eb686-127">Moduly dělení okruh by měla být používána pro přesměrování požadavků na infrastrukturu záložní, pokud může mít problémy v konkrétní prostředek, který je nasazen v jiném prostředí než klientská aplikace nebo služba, která provádí volání protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="eb686-127">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="eb686-128">Tímto způsobem, pokud dojde k výpadku v datovém centru, které ovlivňuje pouze vaše mikroslužeb back-end, ale ne klienta aplikace, můžete klientské aplikace přesměrovat do záložního služeb.</span><span class="sxs-lookup"><span data-stu-id="eb686-128">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="eb686-129">Polly je plánování nové zásady k automatizaci to [zásad převzetí služeb při selhání](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scénář.</span><span class="sxs-lookup"><span data-stu-id="eb686-129">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="eb686-130">Samozřejmě všechny tyto funkce jsou pro případy, kdy spravujete převzetí služeb při selhání v rámci kód rozhraní .NET a nutnosti ho automaticky pro vás spravuje služba Azure, s průhlednost umístění.</span><span class="sxs-lookup"><span data-stu-id="eb686-130">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="eb686-131">Používání třídy nástroj ResilientHttpClient z eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="eb686-131">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="eb686-132">Můžete použít třídu nástroj ResilientHttpClient způsob použití třídy rozhraní .NET HttpClient podobným způsobem.</span><span class="sxs-lookup"><span data-stu-id="eb686-132">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="eb686-133">V následujícím příkladu z webové aplikace MVC eShopOnContainers (OrderingService agenta třídu používá OrderController) je objekt ResilientHttpClient vložit prostřednictvím parametru httpClient konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="eb686-133">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="eb686-134">Objekt se pak používá k provedení požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="eb686-134">Then the object is used to perform HTTP requests.</span></span>

```csharp
public class OrderingService : IOrderingService
{
    private IHttpClient _apiClient;
    private readonly string _remoteServiceBaseUrl;
    private readonly IOptionsSnapshot<AppSettings> _settings;
    private readonly IHttpContextAccessor _httpContextAccesor;

    public OrderingService(IOptionsSnapshot<AppSettings> settings,
        IHttpContextAccessor httpContextAccesor,
        IHttpClient httpClient)
    {
        _remoteServiceBaseUrl = $"{settings.Value.OrderingUrl}/api/v1/orders";
        _settings = settings;
        _httpContextAccesor = httpContextAccesor;
        _apiClient = httpClient;
    }

    async public Task<List<Order>> GetMyOrders(ApplicationUser user)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        var ordersUrl = _remoteServiceBaseUrl;
        var dataString = await _apiClient.GetStringAsync(ordersUrl);
        var response = JsonConvert.DeserializeObject<List<Order>>(dataString);
        return response;
    }

    // Other methods ...
    async public Task CreateOrder(Order order)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        _apiClient.Inst.DefaultRequestHeaders.Add("x-requestid",
            order.RequestId.ToString());
        var ordersUrl = $"{_remoteServiceBaseUrl}/new";
        order.CardTypeId = 1;
        order.CardExpirationApiFormat();
        SetFakeIdToProducts(order);
        var response = await _apiClient.PostAsync(ordersUrl, order);
        response.EnsureSuccessStatusCode();
    }
}
```

<span data-ttu-id="eb686-135">Vždy, když \_apiClient člen objekt se používá, interně používá třídu obálky s Polly policiesؙ – zásady opakovaných pokusů, jistič zásady a jiné zásady, které můžete chtít použít z kolekce Polly zásady.</span><span class="sxs-lookup"><span data-stu-id="eb686-135">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="eb686-136">Testování opakování v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="eb686-136">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="eb686-137">Při každém spuštění eShopOnContainers řešení v nástroji Docker hostitele, musí se spustit několika kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="eb686-137">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="eb686-138">Některé z kontejnerů jsou pomalejší spuštění a inicializaci jako kontejneru systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eb686-138">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="eb686-139">To platí hlavně při prvním nasazení aplikace eShopOnContainers do Docker, protože je nutné nastavit bitové kopie a databáze.</span><span class="sxs-lookup"><span data-stu-id="eb686-139">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="eb686-140">Skutečnost, že některé kontejnery něco pomalejší, než ostatní může způsobit zbytek služby původně vyvolat výjimky HTTP, i když nastavíte závislosti mezi kontejnery na spuštění docker compose úrovni, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="eb686-140">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="eb686-141">Ty docker tvoří závislosti mezi kontejnery jsou jenom na úrovni procesu.</span><span class="sxs-lookup"><span data-stu-id="eb686-141">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="eb686-142">Kontejneru vstupní bod proces může být spuštěn, ale nemusí být připravené pro dotazy SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eb686-142">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="eb686-143">Výsledkem mohou být cascade chyb a aplikaci můžete získat výjimku při pokusu o využívání tohoto konkrétního kontejneru.</span><span class="sxs-lookup"><span data-stu-id="eb686-143">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="eb686-144">Můžete si také prohlédnout tohoto typu chyby na spuštění při nasazení aplikace v cloudu.</span><span class="sxs-lookup"><span data-stu-id="eb686-144">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="eb686-145">V takovém případě orchestrators může být přesunutí kontejnery z jednoho uzlu nebo virtuální počítač na jiný (které spouští nové instance) při vyrovnávání počet kontejnerů mezi uzly clusteru.</span><span class="sxs-lookup"><span data-stu-id="eb686-145">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="eb686-146">Způsob eShopOnContainers řeší tento problém je pomocí opakování vzor, který jsme jsme si uváděli dříve.</span><span class="sxs-lookup"><span data-stu-id="eb686-146">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="eb686-147">Je také proč, při spouštění řešení, mohou se zobrazovat protokolu trasování nebo upozornění takto:</span><span class="sxs-lookup"><span data-stu-id="eb686-147">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="eb686-148">"**Opakujte 1 implementováno s RetryPolicy na Polly**, kvůli: System.Net.Http.HttpRequestException: při odesílání požadavku došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="eb686-148">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="eb686-149"> ---&gt;System.Net.Http.CurlException: Nelze se připojit k serveru\\n v System.Net.Http.CurlHandler.ThrowIfCURLEError (Chyba CURLcode)\\n v \[... \].</span><span class="sxs-lookup"><span data-stu-id="eb686-149"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="eb686-150">Testování vypínač v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="eb686-150">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="eb686-151">Existuje několik způsobů, můžete otevřít okruhu a otestovat s eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="eb686-151">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="eb686-152">Jednou z možností je na nižší povolený počet opakování 1 v zásadách jistič a znovu nasaďte celé řešení do Docker.</span><span class="sxs-lookup"><span data-stu-id="eb686-152">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="eb686-153">Pomocí jednoho opakování je dobré pravděpodobné, že požadavek HTTP se nezdaří během nasazení, se otevře jistič a dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="eb686-153">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="eb686-154">Další možností je použít vlastní middleware, která je implementována v řazení mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="eb686-154">Another option is to use custom middleware that is implemented in the ordering microservice.</span></span> <span data-ttu-id="eb686-155">Pokud je povoleno tento middleware, zachytí všechny požadavky protokolu HTTP a vrátí stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="eb686-155">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="eb686-156">Můžete povolit middleware tím, že požadavek GET na selhání identifikátor URI, třeba takto:</span><span class="sxs-lookup"><span data-stu-id="eb686-156">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="eb686-157">ZÍSKAT/selhání</span><span class="sxs-lookup"><span data-stu-id="eb686-157">GET /failing</span></span>

<span data-ttu-id="eb686-158">Tento požadavek vrátí aktuální stav middleware.</span><span class="sxs-lookup"><span data-stu-id="eb686-158">This request returns the current state of the middleware.</span></span> <span data-ttu-id="eb686-159">Pokud je povoleno middleware, žádost vrátí stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="eb686-159">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="eb686-160">Pokud je zakázána middleware, nepřijde žádná odpověď.</span><span class="sxs-lookup"><span data-stu-id="eb686-160">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="eb686-161">ZÍSKAT/nedaří? povolit</span><span class="sxs-lookup"><span data-stu-id="eb686-161">GET /failing?enable</span></span>

<span data-ttu-id="eb686-162">Tento požadavek umožňuje middleware.</span><span class="sxs-lookup"><span data-stu-id="eb686-162">This request enables the middleware.</span></span>

-   <span data-ttu-id="eb686-163">ZÍSKAT/nedaří? zakázat</span><span class="sxs-lookup"><span data-stu-id="eb686-163">GET /failing?disable</span></span>

<span data-ttu-id="eb686-164">Tento požadavek zakáže middleware.</span><span class="sxs-lookup"><span data-stu-id="eb686-164">This request disables the middleware.</span></span>

<span data-ttu-id="eb686-165">Například když aplikace běží, můžete povolit middleware pomocí libovolného prohlížeče v následující identifikátor URI požadavku.</span><span class="sxs-lookup"><span data-stu-id="eb686-165">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="eb686-166">Všimněte si, že řazení mikroslužbu používá port 5102.</span><span class="sxs-lookup"><span data-stu-id="eb686-166">Note that the ordering microservice uses port 5102.</span></span>

<span data-ttu-id="eb686-167">http://localhost:5102 / nedaří? povolit</span><span class="sxs-lookup"><span data-stu-id="eb686-167">http://localhost:5102/failing?enable</span></span>

<span data-ttu-id="eb686-168">Potom můžete zkontrolovat stav pomocí identifikátoru URI [http://localhost:5102 / selhání](http://localhost:5100/failing), jak je znázorněno na obrázku 10-4.</span><span class="sxs-lookup"><span data-stu-id="eb686-168">You can then check the status using the URI [http://localhost:5102/failing](http://localhost:5100/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="eb686-169">**Obrázek 10-4**.</span><span class="sxs-lookup"><span data-stu-id="eb686-169">**Figure 10-4**.</span></span> <span data-ttu-id="eb686-170">Simulace selhání s ASP.NET middlewaru</span><span class="sxs-lookup"><span data-stu-id="eb686-170">Simulating a failure with ASP.NET middleware</span></span>

<span data-ttu-id="eb686-171">V tomto okamžiku řazení odpoví mikroslužbu se stavovým kódem 500 vždy, když zavoláte ji použít.</span><span class="sxs-lookup"><span data-stu-id="eb686-171">At this point, the ordering microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="eb686-172">Jakmile middleware běží, můžete zkusit provedení pořadí z webové aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="eb686-172">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="eb686-173">Protože žádosti se nezdařilo, otevře se okruh.</span><span class="sxs-lookup"><span data-stu-id="eb686-173">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="eb686-174">V následujícím příkladu vidíte, že má webová aplikace MVC catch blokovat v logiku pro umístění pořadí.</span><span class="sxs-lookup"><span data-stu-id="eb686-174">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="eb686-175">Pokud kód zachytí výjimky otevřete okruh, ukazuje uživateli popisný zpráva s upozorněním čekání.</span><span class="sxs-lookup"><span data-stu-id="eb686-175">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
[HttpPost]
public async Task<IActionResult> Create(Order model, string action)
{
    try
    {
        if (ModelState.IsValid)
        {
            var user = _appUserParser.Parse(HttpContext.User);
            await _orderSvc.CreateOrder(model);
            //Redirect to historic list.
            return RedirectToAction("Index");
        }
    }
    catch(BrokenCircuitException ex)
    {
        ModelState.AddModelError("Error",
            "It was not possible to create a new order, please try later on");
    }
    return View(model);
}
```

<span data-ttu-id="eb686-176">Zde je souhrn.</span><span class="sxs-lookup"><span data-stu-id="eb686-176">Here’s a summary.</span></span> <span data-ttu-id="eb686-177">Zásady opakování pokusí provést několikrát, chcete-li požadavek HTTP a získá chyby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="eb686-177">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="eb686-178">Když počet pokusů dosáhne maximální číslo nastavené zásady jistič (v tomto případě 5), vyvolá aplikace BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="eb686-178">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="eb686-179">Výsledkem je přátelskou zprávou, jak ukazuje obrázek 10-5.</span><span class="sxs-lookup"><span data-stu-id="eb686-179">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="eb686-180">**Obrázek 10-5**.</span><span class="sxs-lookup"><span data-stu-id="eb686-180">**Figure 10-5**.</span></span> <span data-ttu-id="eb686-181">Jistič vrátila chybu do uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb686-181">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="eb686-182">Můžete implementovat jiný logiku pro při otevření okruh.</span><span class="sxs-lookup"><span data-stu-id="eb686-182">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="eb686-183">Nebo můžete zkusit požadavek HTTP proti různých mikroslužbu back-end, pokud záložní datacenter nebo redundantní systému back-end.</span><span class="sxs-lookup"><span data-stu-id="eb686-183">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="eb686-184">Nakonec je další možností CircuitBreakerPolicy použití Isolate (která vynutí otevřete a obsahuje otevřete okruhu) a resetování (který zavře znovu).</span><span class="sxs-lookup"><span data-stu-id="eb686-184">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="eb686-185">To může vytvořit nástroj pro koncový bod protokolu HTTP, která volá Isolate a resetování přímo na zásady.</span><span class="sxs-lookup"><span data-stu-id="eb686-185">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="eb686-186">Takové koncový bod HTTP také může, vhodně zabezpečená, v produkčním prostředí dočasně oddělit podřízené systému, například když chcete upgradovat.</span><span class="sxs-lookup"><span data-stu-id="eb686-186">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="eb686-187">Nebo ji může dojít okruhu ručně ochrana podřízené systému, které předpokládáte, chcete-li být chybující.</span><span class="sxs-lookup"><span data-stu-id="eb686-187">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="eb686-188">Přidávání zpoždění strategie do zásady opakovaných pokusů</span><span class="sxs-lookup"><span data-stu-id="eb686-188">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="eb686-189">Regulární zásady opakování může mít vliv na váš systém v případech vysoké souběžnosti a škálovatelnost a v části vysoké kolizí.</span><span class="sxs-lookup"><span data-stu-id="eb686-189">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="eb686-190">K překonání vrcholů podobné opakování pocházejících z velkého počtu klientů v případě částečné výpadky, je dobré řešení přidat strategie kolísání do algoritmus nebo zásady opakování.</span><span class="sxs-lookup"><span data-stu-id="eb686-190">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="eb686-191">Tím lze vylepšit celkový výkon systému začátku do konce přidáním náhodnost exponenciálního omezení rychlosti.</span><span class="sxs-lookup"><span data-stu-id="eb686-191">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="eb686-192">To šíří se špičky případných problémech.</span><span class="sxs-lookup"><span data-stu-id="eb686-192">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="eb686-193">Při použití Polly kód pro implementaci zpoždění může vypadat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="eb686-193">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="eb686-194">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="eb686-194">Additional resources</span></span>

-   <span data-ttu-id="eb686-195">**Opakujte vzor**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="eb686-195">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="eb686-196">**Odolnost připojení** (Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="eb686-196">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="eb686-197">**Polly** (.NET odolnost a knihovna přechodná. selhání zpracování) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="eb686-197">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="eb686-198">**Vzor jistič**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="eb686-198">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="eb686-199">**Marc Brooker. Zpoždění: Aby lépe s náhodnost** https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="eb686-199">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="eb686-200">[Předchozí] (implement-http-call-retries-exponential-backoff-polly.md) [Další] (health.md monitorování aplikace)</span><span class="sxs-lookup"><span data-stu-id="eb686-200">[Previous] (implement-http-call-retries-exponential-backoff-polly.md) [Next] (monitor-app-health.md)</span></span>
