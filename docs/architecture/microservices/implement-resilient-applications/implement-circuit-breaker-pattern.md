---
title: Implementace vzoru pro přerušení okruhu
description: Naučte se implementovat vzor pro přerušení okruhu jako doplňkový systém pro opakované pokusy http.
ms.date: 10/16/2018
ms.openlocfilehash: f40a8eec50a4293e4dfb4df647ce3f69f6dc361b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296100"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="090c5-103">Implementace systému jističe</span><span class="sxs-lookup"><span data-stu-id="090c5-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="090c5-104">Jak bylo uvedeno dříve, měli byste zpracovat chyby, které mohou trvat proměnlivou dobu, kdy se může stát, když se pokusíte připojit ke vzdálené službě nebo prostředku.</span><span class="sxs-lookup"><span data-stu-id="090c5-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="090c5-105">Zpracování tohoto typu chyby může zlepšit stabilitu a odolnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="090c5-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="090c5-106">V distribuovaném prostředí můžou volání vzdálených prostředků a služeb selhat kvůli přechodným chybám, třeba k pomalým síťovým připojením a časovým limitům, nebo pokud prostředky nereagují pomalu nebo jsou dočasně nedostupné.</span><span class="sxs-lookup"><span data-stu-id="090c5-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="090c5-107">Tyto chyby se obvykle po krátké době opravují a robustní cloudová aplikace by se měla připravit na jejich zpracování pomocí strategie, jako je "vzor opakování".</span><span class="sxs-lookup"><span data-stu-id="090c5-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span> 

<span data-ttu-id="090c5-108">Mohou však nastat situace, kdy jsou chyby způsobeny neočekávanými událostmi, které mohou trvat mnohem déle.</span><span class="sxs-lookup"><span data-stu-id="090c5-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="090c5-109">Tyto chyby můžou být v rozsahu závažnosti od částečné ztráty připojení k úplnému selhání služby.</span><span class="sxs-lookup"><span data-stu-id="090c5-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="090c5-110">V těchto situacích může být bezúčelné, aby aplikace nepřetržitě opakovala operaci, která pravděpodobně nebude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="090c5-110">In these situations, it might be pointless for an application to continually retry an operation that's unlikely to succeed.</span></span> 

<span data-ttu-id="090c5-111">Místo toho by měla být aplikace kódována tak, aby přijímala, že operace se nezdařila, a odpovídajícím způsobem zpracovat selhání.</span><span class="sxs-lookup"><span data-stu-id="090c5-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="090c5-112">Použití carelessly pokusů http by mohlo vést k tomu, že by bylo možné vytvořit útok na útok[DOS (Denial](https://en.wikipedia.org/wiki/Denial-of-service_attack)of Service) ve vašem vlastním softwaru.</span><span class="sxs-lookup"><span data-stu-id="090c5-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="090c5-113">Když mikroslužba selhává nebo pracuje pomalu, může opakované pokusy o neúspěšných pokusech o více klientů.</span><span class="sxs-lookup"><span data-stu-id="090c5-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="090c5-114">Tím se vytvoří nebezpečné riziko exponenciálního zvyšování provozu zaměřeného na neúspěšné služby.</span><span class="sxs-lookup"><span data-stu-id="090c5-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="090c5-115">Proto budete potřebovat určitý druh bariéry proti obraně, aby se nadměrné požadavky zastavily, když nebudete muset dál zkoušet.</span><span class="sxs-lookup"><span data-stu-id="090c5-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it isn't worth to keep trying.</span></span> <span data-ttu-id="090c5-116">Tato bariéra obrany je přesně na konci okruhu.</span><span class="sxs-lookup"><span data-stu-id="090c5-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="090c5-117">Vzor přerušení okruhu má jiný účel než "vzor opakování".</span><span class="sxs-lookup"><span data-stu-id="090c5-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="090c5-118">"Vzor opakování" umožňuje aplikaci opakovat operaci s očekáváním, že operace bude nakonec úspěšná.</span><span class="sxs-lookup"><span data-stu-id="090c5-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="090c5-119">Vzor přerušení okruhu brání aplikaci v provedení operace, která pravděpodobně selže.</span><span class="sxs-lookup"><span data-stu-id="090c5-119">The Circuit Breaker pattern prevents an application from performing an operation that's likely to fail.</span></span> <span data-ttu-id="090c5-120">Aplikace může kombinovat tyto dva vzory.</span><span class="sxs-lookup"><span data-stu-id="090c5-120">An application can combine these two patterns.</span></span> <span data-ttu-id="090c5-121">Logika opakování by však měla být citlivá na jakoukoli výjimku vrácenou koncovým objektem okruhu a měla by porušovat opakované pokusy, pokud je indikátorem okruhu indikováno, že chyba není přechodná.</span><span class="sxs-lookup"><span data-stu-id="090c5-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a><span data-ttu-id="090c5-122">Implementace vzoru pro dělení na okruhy pomocí HttpClientFactory a Polly</span><span class="sxs-lookup"><span data-stu-id="090c5-122">Implement Circuit Breaker pattern with HttpClientFactory and Polly</span></span>

<span data-ttu-id="090c5-123">Stejně jako při implementaci opakování je doporučený postup pro přerušení okruhů, který využívá osvědčené knihovny .NET, jako je Polly a její nativní integraci s HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="090c5-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with HttpClientFactory.</span></span>

<span data-ttu-id="090c5-124">Přidání zásad pro doplňování okruhů do odchozího kanálu middlewaru HttpClientFactory je jednoduché, protože do toho, co už máte při použití HttpClientFactory, přidáte jenom jednu přírůstkovou část kódu.</span><span class="sxs-lookup"><span data-stu-id="090c5-124">Adding a circuit breaker policy into your HttpClientFactory outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using HttpClientFactory.</span></span>

<span data-ttu-id="090c5-125">Jediným přidaným kódem, který se používá pro opakované pokusy o volání HTTP, je kód, kde přidáte zásadu pro přerušení okruhů do seznamu zásad, které chcete použít, jak je znázorněno v následujícím přírůstkovém kódu, který je součástí metody ConfigureServices ().</span><span class="sxs-lookup"><span data-stu-id="090c5-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="090c5-126">Tato `AddPolicyHandler()` metoda přidává zásady `HttpClient` pro objekty, které budete používat.</span><span class="sxs-lookup"><span data-stu-id="090c5-126">The `AddPolicyHandler()` method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="090c5-127">V takovém případě přidá zásady Polly pro přepínací modul okruhů.</span><span class="sxs-lookup"><span data-stu-id="090c5-127">In this case, it's adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="090c5-128">Chcete-li mít více modulární přístup, je zásada pro přerušení okruhu definována v samostatné metodě s `GetCircuitBreakerPolicy()`názvem, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="090c5-128">To have a more modular approach, the Circuit Breaker Policy is defined in a separate method called `GetCircuitBreakerPolicy()`, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="090c5-129">Ve výše uvedeném příkladu kódu je zásada pro přerušení okruhu nakonfigurovaná tak, že se přeruší nebo otevře okruh v případě, že při opakování požadavků HTTP došlo k pěti po sobě jdoucími chybám.</span><span class="sxs-lookup"><span data-stu-id="090c5-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="090c5-130">Pokud k tomu dojde, okruh bude po dobu 30 sekund přerušen: v takovém případě budou volání okamžitě neúspěšná pomocí přepínacího modulu okruhů, nikoli ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="090c5-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="090c5-131">Zásady automaticky interpretují [relevantní výjimky a stavové kódy http](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) jako chyby.</span><span class="sxs-lookup"><span data-stu-id="090c5-131">The policy automatically interprets [relevant exceptions and HTTP status codes](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="090c5-132">K přesměrování požadavků na záložní infrastrukturu by se měly také použít vypínače okruhů, pokud máte problémy v konkrétním prostředku, který je nasazený v jiném prostředí než klientská aplikace nebo služba provádějící volání HTTP.</span><span class="sxs-lookup"><span data-stu-id="090c5-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that's deployed in a different environment than the client application or service that's performing the HTTP call.</span></span> <span data-ttu-id="090c5-133">Tímto způsobem dojde v případě výpadku v datovém centru, které ovlivňuje pouze vaše mikroslužby back-end, ale ne klientské aplikace, a klientské aplikace se mohou přesměrovat na záložní služby.</span><span class="sxs-lookup"><span data-stu-id="090c5-133">That way, if there's an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="090c5-134">Polly plánuje novou zásadu pro automatizaci tohoto scénáře [zásad převzetí služeb při selhání](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) .</span><span class="sxs-lookup"><span data-stu-id="090c5-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span> 

<span data-ttu-id="090c5-135">Všechny tyto funkce jsou pro případy, kdy spravujete převzetí služeb při selhání z kódu .NET, a to na rozdíl od toho, že je spravujete automaticky za vás Azure s transparentností polohy.</span><span class="sxs-lookup"><span data-stu-id="090c5-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span> 

<span data-ttu-id="090c5-136">Z bodu použití v zobrazení není nutné přidávat nic nového, protože kód je stejný, než když používáte HttpClient s HttpClientFactory, jak je znázorněno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="090c5-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using HttpClient with HttpClientFactory, as shown in previous sections.</span></span> 

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="090c5-137">Testování opakovaných pokusů http a přepínacích cyklů okruhů v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="090c5-137">Test Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="090c5-138">Kdykoli na hostiteli Docker spustíte řešení eShopOnContainers, musí být spuštěno více kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="090c5-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="090c5-139">U některých kontejnerů je pomalejší spuštění a inicializace, jako je SQL Server kontejner.</span><span class="sxs-lookup"><span data-stu-id="090c5-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="090c5-140">To platí hlavně při prvním nasazení aplikace eShopOnContainers do Docker, protože je potřeba nastavit Image a databázi.</span><span class="sxs-lookup"><span data-stu-id="090c5-140">This is especially true the first time you deploy the eShopOnContainers application into Docker because it needs to set up the images and the database.</span></span> <span data-ttu-id="090c5-141">Vzhledem k tomu, že některé kontejnery začínají pomalejší než jiné, může dojít k tomu, že zbytek služeb zpočátku vyvolá výjimky HTTP, a to i v případě, že nastavíte závislosti mezi kontejnery na úrovni Docker-skládání, jak je vysvětleno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="090c5-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="090c5-142">Tyto závislosti v Docker – skládání mezi kontejnery jsou pouze na úrovni procesu.</span><span class="sxs-lookup"><span data-stu-id="090c5-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="090c5-143">Můžete spustit proces vstupního bodu kontejneru, ale SQL Server nemusí být připravený na dotazy.</span><span class="sxs-lookup"><span data-stu-id="090c5-143">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="090c5-144">Výsledkem může být kaskáda chyb a aplikace může získat výjimku při pokusu o využití tohoto konkrétního kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090c5-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="090c5-145">Při nasazování aplikace do cloudu můžete také zobrazit tento typ chyby při spuštění.</span><span class="sxs-lookup"><span data-stu-id="090c5-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="090c5-146">V takovém případě mohou orchestrace přesunout kontejnery z jednoho uzlu nebo virtuálního počítače do jiného (to znamená spouštění nových instancí) při vyrovnávání počtu kontejnerů v uzlech clusteru.</span><span class="sxs-lookup"><span data-stu-id="090c5-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="090c5-147">Způsob, jakým "eShopOnContainers" řeší tyto problémy při spouštění všech kontejnerů, je pomocí vzoru opakování popsaného výše.</span><span class="sxs-lookup"><span data-stu-id="090c5-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span> 

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="090c5-148">Test přerušení okruhu v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="090c5-148">Test the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="090c5-149">Existuje několik způsobů, jak můžete okruh přerušit/otevřít a otestovat ho pomocí eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="090c5-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="090c5-150">Jednou z možností je snížit povolený počet opakovaných pokusů na 1 v zásadách pro dělení na okruhy a znovu nasadit celé řešení do Docker.</span><span class="sxs-lookup"><span data-stu-id="090c5-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="090c5-151">Při jednom opakovaném pokusu je pravděpodobné, že během nasazování selže požadavek HTTP, dojde k otevření přerušení okruhu a zobrazí se chyba.</span><span class="sxs-lookup"><span data-stu-id="090c5-151">With a single retry, there's a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="090c5-152">Další možností je použít vlastní middleware, který je implementován v mikroslužbě **koše** .</span><span class="sxs-lookup"><span data-stu-id="090c5-152">Another option is to use custom middleware that's implemented in the **Basket** microservice.</span></span> <span data-ttu-id="090c5-153">Pokud je tento middleware povolený, zachytává všechny požadavky HTTP a vrátí stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="090c5-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="090c5-154">Middleware můžete povolit tím, že vytvoříte požadavek GET na identifikátor URI, který se nezdaří, například následující:</span><span class="sxs-lookup"><span data-stu-id="090c5-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`\
  <span data-ttu-id="090c5-155">Tento požadavek vrátí aktuální stav middleware.</span><span class="sxs-lookup"><span data-stu-id="090c5-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="090c5-156">Pokud je povolen middleware, požadavek vrátí stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="090c5-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="090c5-157">Pokud je middleware zakázán, neexistuje žádná odpověď.</span><span class="sxs-lookup"><span data-stu-id="090c5-157">If the middleware is disabled, there's no response.</span></span>

- `GET http://localhost:5103/failing?enable`\
  <span data-ttu-id="090c5-158">Tento požadavek povoluje middleware.</span><span class="sxs-lookup"><span data-stu-id="090c5-158">This request enables the middleware.</span></span>

- `GET http://localhost:5103/failing?disable`\
  <span data-ttu-id="090c5-159">Tato žádost zakáže middleware.</span><span class="sxs-lookup"><span data-stu-id="090c5-159">This request disables the middleware.</span></span>

<span data-ttu-id="090c5-160">Například po spuštění aplikace můžete povolit middleware pomocí následujícího identifikátoru URI v jakémkoli prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="090c5-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="090c5-161">Všimněte si, že mikroslužba řazení používá port 5103.</span><span class="sxs-lookup"><span data-stu-id="090c5-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable` 

<span data-ttu-id="090c5-162">Pak můžete zjistit stav pomocí identifikátoru URI `http://localhost:5103/failing`, jak je znázorněno na obrázku 8-5.</span><span class="sxs-lookup"><span data-stu-id="090c5-162">You can then check the status using the URI `http://localhost:5103/failing`, as shown in Figure 8-5.</span></span>

![Zobrazení prohlížeče výsledku z kontroly stavu neúspěšné simulace middlewaru](./media/image4.png)

<span data-ttu-id="090c5-164">**Obrázek 8-5**.</span><span class="sxs-lookup"><span data-stu-id="090c5-164">**Figure 8-5**.</span></span> <span data-ttu-id="090c5-165">Kontroluje se stav neúspěšného middlewaru ASP.NET pro selhání – v tomto případě je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="090c5-165">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span>

<span data-ttu-id="090c5-166">V tomto okamžiku bude mikroslužba košíku reagovat se stavovým kódem 500, kdykoli volání vyvolá.</span><span class="sxs-lookup"><span data-stu-id="090c5-166">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="090c5-167">Jakmile middleware běží, můžete vyzkoušet vytvoření objednávky z webové aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="090c5-167">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="090c5-168">Vzhledem k tomu, že se požadavky selžou, okruh se otevře.</span><span class="sxs-lookup"><span data-stu-id="090c5-168">Because the requests fail, the circuit will open.</span></span> 

<span data-ttu-id="090c5-169">V následujícím příkladu vidíte, že webová aplikace MVC má v logice blok catch pro umístění objednávky.</span><span class="sxs-lookup"><span data-stu-id="090c5-169">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="090c5-170">Pokud kód zachytí výjimku otevřeného okruhu, zobrazí uživateli uživatelsky přívětivou zprávu s oznámením, že má počkat.</span><span class="sxs-lookup"><span data-stu-id="090c5-170">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="090c5-171">Tady je souhrn.</span><span class="sxs-lookup"><span data-stu-id="090c5-171">Here’s a summary.</span></span> <span data-ttu-id="090c5-172">Zásada opakování se několikrát pokusí vytvořit požadavek HTTP a získá chyby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="090c5-172">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="090c5-173">Pokud počet opakování dosáhne maximálního počtu nastaveného pro zásadu pro dělení na okruhy (v tomto případě 5), aplikace vyvolá výjimku BrokenCircuitException.</span><span class="sxs-lookup"><span data-stu-id="090c5-173">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="090c5-174">Výsledkem je Popisná zpráva, jak je znázorněno na obrázku 8-6.</span><span class="sxs-lookup"><span data-stu-id="090c5-174">The result is a friendly message, as shown in Figure 8-6.</span></span>

![Zobrazení prohlížeče webové aplikace MVC znázorňující zprávu "nefunkční služba košíku", která se aktivuje zásadami pro přerušení okruhů](./media/image5.png)

<span data-ttu-id="090c5-176">**Obrázek 8-6**.</span><span class="sxs-lookup"><span data-stu-id="090c5-176">**Figure 8-6**.</span></span> <span data-ttu-id="090c5-177">Přepínací modul okruhů vrátil chybu do uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="090c5-177">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="090c5-178">Můžete implementovat jinou logiku pro otevření nebo přerušení okruhu.</span><span class="sxs-lookup"><span data-stu-id="090c5-178">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="090c5-179">Nebo můžete vyzkoušet požadavek HTTP na jinou back-end mikroslužbu, pokud existuje záložní datové centrum nebo redundantní back-end systém.</span><span class="sxs-lookup"><span data-stu-id="090c5-179">Or you can try an HTTP request against a different back-end microservice if there's a fallback datacenter or redundant back-end system.</span></span> 

<span data-ttu-id="090c5-180">Nakonec další možnost pro `CircuitBreakerPolicy` je použít `Isolate` (které vynutí otevření a blokování otevřeného okruhu) a `Reset` (které se znovu zavřou).</span><span class="sxs-lookup"><span data-stu-id="090c5-180">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="090c5-181">Ty je možné použít k vytvoření koncového bodu HTTP nástroje, který vyvolá izolaci a resetování přímo na zásadě.</span><span class="sxs-lookup"><span data-stu-id="090c5-181">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="090c5-182">Takový koncový bod HTTP by se taky mohl použít, vhodně zabezpečený v produkčním prostředí pro dočasný izolaci systému pro příjem dat, třeba když ho chcete upgradovat.</span><span class="sxs-lookup"><span data-stu-id="090c5-182">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="090c5-183">Nebo může obcházet okruh ručně, aby se chránil systém pro příjem dat, u kterého se domníváte, že se jedná o poruchu.</span><span class="sxs-lookup"><span data-stu-id="090c5-183">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="090c5-184">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="090c5-184">Additional resources</span></span>

- <span data-ttu-id="090c5-185">**Vzorek pro přerušení okruhu**</span><span class="sxs-lookup"><span data-stu-id="090c5-185">**Circuit Breaker pattern**</span></span>\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
><span data-ttu-id="090c5-186">[Předchozí](implement-http-call-retries-exponential-backoff-polly.md)Další
>[](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="090c5-186">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
