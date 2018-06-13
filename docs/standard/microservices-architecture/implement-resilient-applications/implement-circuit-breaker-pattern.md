---
title: Implementace vzoru jistič
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace vzoru jistič
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.openlocfilehash: dea94d8eda3341cca5e3aaf6b3c8369c27381135
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578011"
---
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="0c20a-103">Implementace vzoru jistič</span><span class="sxs-lookup"><span data-stu-id="0c20a-103">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="0c20a-104">Jak jsme uvedli výše, by měla řídit chyb, které může trvat proměnné množství času dostat z, může dojít při pokusu o připojení k vzdálené služby nebo prostředku.</span><span class="sxs-lookup"><span data-stu-id="0c20a-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="0c20a-105">Tento typ chyby zpracování může zvýšit stabilitu a odolnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="0c20a-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="0c20a-106">V distribuovaném prostředí volání vzdálené prostředky a služby může selhat z důvodu přechodných chyb, jako je pomalé síťové připojení a vypršení časových limitů, nebo pokud jsou prostředky zpomalit nebo jsou dočasně nedostupné.</span><span class="sxs-lookup"><span data-stu-id="0c20a-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="0c20a-107">Tyto chyby obvykle opravte po krátkou dobu sami a je třeba připravit robustní cloudových aplikací k jejich zpracování pomocí strategie jako vzor opakování.</span><span class="sxs-lookup"><span data-stu-id="0c20a-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="0c20a-108">Však může také nastat situace, kde jsou chyb z důvodu neočekávané události, které může trvat déle, chcete-li odstranit.</span><span class="sxs-lookup"><span data-stu-id="0c20a-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="0c20a-109">Tyto chyby může být v rozsahu v závažnosti od částečné ztrátě připojení k úplnému selhání služby.</span><span class="sxs-lookup"><span data-stu-id="0c20a-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="0c20a-110">V těchto situacích může být zbytečný pro aplikaci neustále opakujte operaci, která je pravděpodobně úspěšné.</span><span class="sxs-lookup"><span data-stu-id="0c20a-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="0c20a-111">Místo toho by měly být napsané aplikace potvrďte, že operace se nezdařila a zpracování selhání odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="0c20a-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="0c20a-112">Vzor jistič má jiný účel než vzor opakování.</span><span class="sxs-lookup"><span data-stu-id="0c20a-112">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="0c20a-113">Vzor opakování povolí aplikaci opakovat operace v očekávání, který nakonec operace proběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="0c20a-113">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="0c20a-114">Vzor jistič brání aplikaci v provádění operace, která je pravděpodobně selžou.</span><span class="sxs-lookup"><span data-stu-id="0c20a-114">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="0c20a-115">Aplikace můžete kombinovat tyto dvě vzory pomocí vzoru opakování k vyvolání operace prostřednictvím jistič.</span><span class="sxs-lookup"><span data-stu-id="0c20a-115">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="0c20a-116">Ale logika opakovaných pokusů by měla být citlivé na jakékoli výjimky vrácený vypínač a pokud vypínač signalizuje, že chybu není přechodný ho měli abandon počet pokusů o opakování.</span><span class="sxs-lookup"><span data-stu-id="0c20a-116">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="0c20a-117">Implementace vzoru jistič s Polly</span><span class="sxs-lookup"><span data-stu-id="0c20a-117">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="0c20a-118">Jako při implementaci opakování, umožní využít Principy knihovny .NET, jako je Polly je doporučený postup pro moduly okruh dělení.</span><span class="sxs-lookup"><span data-stu-id="0c20a-118">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="0c20a-119">Při implementaci HTTP opakování, používá aplikace eShopOnContainers Polly jistič zásad.</span><span class="sxs-lookup"><span data-stu-id="0c20a-119">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="0c20a-120">Ve skutečnosti aplikace platí obě zásady pro třídu ResilientHttpClient nástroj.</span><span class="sxs-lookup"><span data-stu-id="0c20a-120">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="0c20a-121">Vždy, když použijete objekt typu ResilientHttpClient požadavků HTTP (od eShopOnContainers), budou uplatňovat obě tyto zásady, ale můžete přidat další zásady, příliš.</span><span class="sxs-lookup"><span data-stu-id="0c20a-121">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="0c20a-122">Pouze přidání sem do kód použitý pro opakování volání HTTP je kód, kdy přidáte jistič zásad do seznamu zásad použití, jak je znázorněno na konci následující kód:</span><span class="sxs-lookup"><span data-stu-id="0c20a-122">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

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

<span data-ttu-id="0c20a-123">Kód přidá zásadu pro obálku protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0c20a-123">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="0c20a-124">Aby zásad definuje jistič, které se otevře při kód zjistí zadaný počet po sobě jdoucích výjimek (výjimky v řádku), jako předán v parametru exceptionsAllowedBeforeBreaking (v tomto případě 5).</span><span class="sxs-lookup"><span data-stu-id="0c20a-124">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="0c20a-125">Když okruh je otevřená, nefungují požadavků HTTP, ale je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0c20a-125">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="0c20a-126">Moduly dělení okruh by měla být používána pro přesměrování požadavků na infrastrukturu záložní, pokud může mít problémy v konkrétní prostředek, který je nasazen v jiném prostředí než klientská aplikace nebo služba, která provádí volání protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0c20a-126">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="0c20a-127">Tímto způsobem, pokud dojde k výpadku v datovém centru, které ovlivňuje pouze vaše mikroslužeb back-end, ale ne klienta aplikace, můžete klientské aplikace přesměrovat do záložního služeb.</span><span class="sxs-lookup"><span data-stu-id="0c20a-127">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="0c20a-128">Polly je plánování nové zásady k automatizaci to [zásad převzetí služeb při selhání](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scénář.</span><span class="sxs-lookup"><span data-stu-id="0c20a-128">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="0c20a-129">Samozřejmě všechny tyto funkce jsou pro případy, kdy spravujete převzetí služeb při selhání v rámci kód rozhraní .NET a nutnosti ho automaticky pro vás spravuje služba Azure, s průhlednost umístění.</span><span class="sxs-lookup"><span data-stu-id="0c20a-129">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="0c20a-130">Používání třídy nástroj ResilientHttpClient z eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="0c20a-130">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="0c20a-131">Můžete použít třídu nástroj ResilientHttpClient způsob použití třídy rozhraní .NET HttpClient podobným způsobem.</span><span class="sxs-lookup"><span data-stu-id="0c20a-131">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="0c20a-132">V následujícím příkladu z webové aplikace MVC eShopOnContainers (OrderingService agenta třídu používá OrderController) je objekt ResilientHttpClient vložit prostřednictvím parametru httpClient konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0c20a-132">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="0c20a-133">Objekt se pak používá k provedení požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="0c20a-133">Then the object is used to perform HTTP requests.</span></span>

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

<span data-ttu-id="0c20a-134">Vždy, když \_apiClient člen objekt se používá, interně používá třídu obálky s Polly policiesؙ – zásady opakovaných pokusů, jistič zásady a jiné zásady, které můžete chtít použít z kolekce Polly zásady.</span><span class="sxs-lookup"><span data-stu-id="0c20a-134">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="0c20a-135">Testování opakování v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="0c20a-135">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="0c20a-136">Při každém spuštění eShopOnContainers řešení v nástroji Docker hostitele, musí se spustit několika kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="0c20a-136">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="0c20a-137">Některé z kontejnerů jsou pomalejší spuštění a inicializaci jako kontejneru systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c20a-137">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="0c20a-138">To platí hlavně při prvním nasazení aplikace eShopOnContainers do Docker, protože je nutné nastavit bitové kopie a databáze.</span><span class="sxs-lookup"><span data-stu-id="0c20a-138">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="0c20a-139">Skutečnost, že některé kontejnery něco pomalejší, než ostatní může způsobit zbytek služby původně vyvolat výjimky HTTP, i když nastavíte závislosti mezi kontejnery na spuštění docker compose úrovni, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="0c20a-139">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="0c20a-140">Ty docker tvoří závislosti mezi kontejnery jsou jenom na úrovni procesu.</span><span class="sxs-lookup"><span data-stu-id="0c20a-140">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="0c20a-141">Kontejneru vstupní bod proces může být spuštěn, ale nemusí být připravené pro dotazy SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c20a-141">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="0c20a-142">Výsledkem mohou být cascade chyb a aplikaci můžete získat výjimku při pokusu o využívání tohoto konkrétního kontejneru.</span><span class="sxs-lookup"><span data-stu-id="0c20a-142">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="0c20a-143">Můžete si také prohlédnout tohoto typu chyby na spuštění při nasazení aplikace v cloudu.</span><span class="sxs-lookup"><span data-stu-id="0c20a-143">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="0c20a-144">V takovém případě orchestrators může být přesunutí kontejnery z jednoho uzlu nebo virtuální počítač na jiný (které spouští nové instance) při vyrovnávání počet kontejnerů mezi uzly clusteru.</span><span class="sxs-lookup"><span data-stu-id="0c20a-144">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="0c20a-145">Způsob eShopOnContainers řeší tento problém je pomocí opakování vzor, který jsme jsme si uváděli dříve.</span><span class="sxs-lookup"><span data-stu-id="0c20a-145">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="0c20a-146">Je také proč, při spouštění řešení, mohou se zobrazovat protokolu trasování nebo upozornění takto:</span><span class="sxs-lookup"><span data-stu-id="0c20a-146">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="0c20a-147">"**Opakujte 1 implementováno s RetryPolicy na Polly**, kvůli: System.Net.Http.HttpRequestException: při odesílání požadavku došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="0c20a-147">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="0c20a-148"> ---&gt; System.Net.Http.CurlException: Nelze se připojit k serveru\\n v System.Net.Http.CurlHandler.ThrowIfCURLEError (Chyba CURLcode)\\n v \[... \].</span><span class="sxs-lookup"><span data-stu-id="0c20a-148"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="0c20a-149">Testování vypínač v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="0c20a-149">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="0c20a-150">Existuje několik způsobů, můžete otevřít okruhu a otestovat s eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0c20a-150">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="0c20a-151">Jednou z možností je na nižší povolený počet opakování 1 v zásadách jistič a znovu nasaďte celé řešení do Docker.</span><span class="sxs-lookup"><span data-stu-id="0c20a-151">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="0c20a-152">Pomocí jednoho opakování je dobré pravděpodobné, že požadavek HTTP se nezdaří během nasazení, se otevře jistič a dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="0c20a-152">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="0c20a-153">Další možností je použít vlastní middleware, která je implementována v `Basket` mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="0c20a-153">Another option is to use custom middleware that is implemented in the `Basket` microservice.</span></span> <span data-ttu-id="0c20a-154">Pokud je povoleno tento middleware, zachytí všechny požadavky protokolu HTTP a vrátí stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="0c20a-154">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="0c20a-155">Můžete povolit middleware tím, že požadavek GET na selhání identifikátor URI, třeba takto:</span><span class="sxs-lookup"><span data-stu-id="0c20a-155">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="0c20a-156">ZÍSKAT/selhání</span><span class="sxs-lookup"><span data-stu-id="0c20a-156">GET /failing</span></span>

<span data-ttu-id="0c20a-157">Tento požadavek vrátí aktuální stav middleware.</span><span class="sxs-lookup"><span data-stu-id="0c20a-157">This request returns the current state of the middleware.</span></span> <span data-ttu-id="0c20a-158">Pokud je povoleno middleware, žádost vrátí stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="0c20a-158">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="0c20a-159">Pokud je zakázána middleware, nepřijde žádná odpověď.</span><span class="sxs-lookup"><span data-stu-id="0c20a-159">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="0c20a-160">ZÍSKAT/nedaří? povolit</span><span class="sxs-lookup"><span data-stu-id="0c20a-160">GET /failing?enable</span></span>

<span data-ttu-id="0c20a-161">Tento požadavek umožňuje middleware.</span><span class="sxs-lookup"><span data-stu-id="0c20a-161">This request enables the middleware.</span></span>

-   <span data-ttu-id="0c20a-162">ZÍSKAT/nedaří? zakázat</span><span class="sxs-lookup"><span data-stu-id="0c20a-162">GET /failing?disable</span></span>

<span data-ttu-id="0c20a-163">Tento požadavek zakáže middleware.</span><span class="sxs-lookup"><span data-stu-id="0c20a-163">This request disables the middleware.</span></span>

<span data-ttu-id="0c20a-164">Například když aplikace běží, můžete povolit middleware pomocí libovolného prohlížeče v následující identifikátor URI požadavku.</span><span class="sxs-lookup"><span data-stu-id="0c20a-164">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="0c20a-165">Všimněte si, že řazení mikroslužbu používá port 5103.</span><span class="sxs-lookup"><span data-stu-id="0c20a-165">Note that the ordering microservice uses port 5103.</span></span>

http://localhost:5103/failing?enable

<span data-ttu-id="0c20a-166">Potom můžete zkontrolovat stav pomocí identifikátoru URI [ http://localhost:5103/failing ](http://localhost:5103/failing), jak je znázorněno na obrázku 10-4.</span><span class="sxs-lookup"><span data-stu-id="0c20a-166">You can then check the status using the URI [http://localhost:5103/failing](http://localhost:5103/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="0c20a-167">**Obrázek 10-4**.</span><span class="sxs-lookup"><span data-stu-id="0c20a-167">**Figure 10-4**.</span></span> <span data-ttu-id="0c20a-168">Kontroluje se stav "Selhání" middleware ASP.NET – v takovém případě zakázána.</span><span class="sxs-lookup"><span data-stu-id="0c20a-168">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="0c20a-169">V tomto okamžiku odpoví mikroslužbu nákupního košíku se stavovým kódem 500 vždy, když zavoláte ji použít.</span><span class="sxs-lookup"><span data-stu-id="0c20a-169">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="0c20a-170">Jakmile middleware běží, můžete zkusit provedení pořadí z webové aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="0c20a-170">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="0c20a-171">Protože žádosti se nezdařilo, otevře se okruh.</span><span class="sxs-lookup"><span data-stu-id="0c20a-171">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="0c20a-172">V následujícím příkladu vidíte, že má webová aplikace MVC catch blokovat v logiku pro umístění pořadí.</span><span class="sxs-lookup"><span data-stu-id="0c20a-172">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="0c20a-173">Pokud kód zachytí výjimky otevřete okruh, ukazuje uživateli popisný zpráva s upozorněním čekání.</span><span class="sxs-lookup"><span data-stu-id="0c20a-173">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            //… Other code
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

<span data-ttu-id="0c20a-174">Zde je souhrn.</span><span class="sxs-lookup"><span data-stu-id="0c20a-174">Here’s a summary.</span></span> <span data-ttu-id="0c20a-175">Zásady opakování pokusí provést několikrát, chcete-li požadavek HTTP a získá chyby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0c20a-175">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="0c20a-176">Když počet pokusů dosáhne maximální číslo nastavené zásady jistič (v tomto případě 5), vyvolá aplikace BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="0c20a-176">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="0c20a-177">Výsledkem je přátelskou zprávou, jak ukazuje obrázek 10-5.</span><span class="sxs-lookup"><span data-stu-id="0c20a-177">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="0c20a-178">**Obrázek 10-5**.</span><span class="sxs-lookup"><span data-stu-id="0c20a-178">**Figure 10-5**.</span></span> <span data-ttu-id="0c20a-179">Jistič vrátila chybu do uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c20a-179">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="0c20a-180">Můžete implementovat jiný logiku pro při otevření okruh.</span><span class="sxs-lookup"><span data-stu-id="0c20a-180">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="0c20a-181">Nebo můžete zkusit požadavek HTTP proti různých mikroslužbu back-end, pokud záložní datacenter nebo redundantní systému back-end.</span><span class="sxs-lookup"><span data-stu-id="0c20a-181">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="0c20a-182">Nakonec je další možností CircuitBreakerPolicy použití Isolate (která vynutí otevřete a obsahuje otevřete okruhu) a resetování (který zavře znovu).</span><span class="sxs-lookup"><span data-stu-id="0c20a-182">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="0c20a-183">To může vytvořit nástroj pro koncový bod protokolu HTTP, která volá Isolate a resetování přímo na zásady.</span><span class="sxs-lookup"><span data-stu-id="0c20a-183">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="0c20a-184">Takové koncový bod HTTP také může, vhodně zabezpečená, v produkčním prostředí dočasně oddělit podřízené systému, například když chcete upgradovat.</span><span class="sxs-lookup"><span data-stu-id="0c20a-184">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="0c20a-185">Nebo ji může dojít okruhu ručně ochrana podřízené systému, které předpokládáte, chcete-li být chybující.</span><span class="sxs-lookup"><span data-stu-id="0c20a-185">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="0c20a-186">Přidávání zpoždění strategie do zásady opakovaných pokusů</span><span class="sxs-lookup"><span data-stu-id="0c20a-186">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="0c20a-187">Regulární zásady opakování může mít vliv na váš systém v případech vysoké souběžnosti a škálovatelnost a v části vysoké kolizí.</span><span class="sxs-lookup"><span data-stu-id="0c20a-187">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="0c20a-188">K překonání vrcholů podobné opakování pocházejících z velkého počtu klientů v případě částečné výpadky, je dobré řešení přidat strategie kolísání do algoritmus nebo zásady opakování.</span><span class="sxs-lookup"><span data-stu-id="0c20a-188">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="0c20a-189">Tím lze vylepšit celkový výkon systému začátku do konce přidáním náhodnost exponenciálního omezení rychlosti.</span><span class="sxs-lookup"><span data-stu-id="0c20a-189">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="0c20a-190">To šíří se špičky případných problémech.</span><span class="sxs-lookup"><span data-stu-id="0c20a-190">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="0c20a-191">Při použití Polly kód pro implementaci zpoždění může vypadat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0c20a-191">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="0c20a-192">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0c20a-192">Additional resources</span></span>

-   <span data-ttu-id="0c20a-193">**Opakujte vzor**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="0c20a-193">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="0c20a-194">**Odolnost připojení** (Entity Framework jader) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="0c20a-194">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="0c20a-195">**Polly** (.NET odolnost a přechodná. selhání zpracování knihovny) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="0c20a-195">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="0c20a-196">**Vzor jistič**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="0c20a-196">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="0c20a-197">**Marc Brooker. Zpoždění: Aby lépe s náhodnost** https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="0c20a-197">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0c20a-198">[Předchozí] (implement-http-call-retries-exponential-backoff-polly.md) [Další] (health.md monitorování aplikace)</span><span class="sxs-lookup"><span data-stu-id="0c20a-198">[Previous] (implement-http-call-retries-exponential-backoff-polly.md) [Next] (monitor-app-health.md)</span></span>
