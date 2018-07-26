---
title: Implementace vzoru Circuit Breaker
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace vzoru Circuit Breaker jako doplňkové systém k opakování Http
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: d5902c5a0744d74ae5086a4df3aee606b24b6030
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875164"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="94748-103">Implementace vzoru Circuit Breaker</span><span class="sxs-lookup"><span data-stu-id="94748-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="94748-104">Jak bylo uvedeno dříve, by měl zpracovává chyby, které může trvat různě dlouho obnovit, protože k tomu může dojít při pokusu o připojení ke vzdálené službě nebo prostředku.</span><span class="sxs-lookup"><span data-stu-id="94748-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as it might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="94748-105">Zpracování tohoto typu chyby může zlepšit stabilitu a odolnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="94748-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="94748-106">V distribuovaném prostředí můžou volání vzdálených prostředků a služeb můžete selhat z důvodu přechodných chyb, jako jsou pomalé síťové připojení a časové limity, nebo pokud prostředky se pomalé nebo jsou dočasně nedostupné.</span><span class="sxs-lookup"><span data-stu-id="94748-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="94748-107">Tyto chyby obvykle opraví po krátkou dobu samy a robustní Cloudová aplikace by měla být připravena je zvládnout pomocí strategie, jako je model"opakování".</span><span class="sxs-lookup"><span data-stu-id="94748-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span> 

<span data-ttu-id="94748-108">Však mohou také existovat situace, kdy jsou chyby způsobeny nepředvídatelnými událostmi, které může trvat déle, chcete-li vyřešit.</span><span class="sxs-lookup"><span data-stu-id="94748-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="94748-109">Tyto chyby můžou být různě od částečného výpadku připojení až po úplné selhání služby.</span><span class="sxs-lookup"><span data-stu-id="94748-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="94748-110">V těchto situacích může být bezúčelné pro aplikaci neustále opakovat operaci, která pravděpodobně nebude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="94748-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> 

<span data-ttu-id="94748-111">Místo toho aplikace by měly být kódovány potvrďte, že operace se nezdařila a odpovídajícím způsobem chybu zpracovat.</span><span class="sxs-lookup"><span data-stu-id="94748-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="94748-112">Použití opakování Http neuváženě může vést k vytváření cílem odepření služeb ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) útoku v rámci vlastního softwaru.</span><span class="sxs-lookup"><span data-stu-id="94748-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="94748-113">Mikroslužby selže nebo pomalu, více klientů může opakovaně opakování neúspěšných žádostí.</span><span class="sxs-lookup"><span data-stu-id="94748-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="94748-114">Který vytváří nebezpečné riziko exponenciálně prodlužuje provozu zaměřený na selhávající službu.</span><span class="sxs-lookup"><span data-stu-id="94748-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="94748-115">Proto je nutné nějaký druh defense barrier, aby opakované pokusy zastavit požadavky, když není za to pořád snažit.</span><span class="sxs-lookup"><span data-stu-id="94748-115">Therefore, you need some kind of defense barrier so the retries stop requests when it is not worth to keep trying.</span></span> <span data-ttu-id="94748-116">Této bariéry defense je přesně jističe.</span><span class="sxs-lookup"><span data-stu-id="94748-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="94748-117">Model jistič má jiný účel než "model opakování".</span><span class="sxs-lookup"><span data-stu-id="94748-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="94748-118">Model opakování"" umožňuje aplikaci opakovat operaci s předpokladem, že operace bude nakonec úspěšná.</span><span class="sxs-lookup"><span data-stu-id="94748-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="94748-119">Model jistič zabraňuje aplikaci provést operaci, která pravděpodobně selže.</span><span class="sxs-lookup"><span data-stu-id="94748-119">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="94748-120">Aplikace může tyto dva modely zkombinovat.</span><span class="sxs-lookup"><span data-stu-id="94748-120">An application can combine these two patterns.</span></span> <span data-ttu-id="94748-121">Ale logika opakovaných pokusů by měl být citlivé na jakoukoliv výjimku, vrácené jističem a by provádět opakované pokusy, pokud jistič signalizuje, že chyba není přechodná.</span><span class="sxs-lookup"><span data-stu-id="94748-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a><span data-ttu-id="94748-122">Implementace vzoru Circuit Breaker HttpClientFactory a Polly</span><span class="sxs-lookup"><span data-stu-id="94748-122">Implement Circuit Breaker pattern with HttpClientFactory and Polly</span></span>

<span data-ttu-id="94748-123">Při implementaci opakovaných pokusů, využívat osvědčené knihovny .NET, jako jsou knihovny Polly a jeho nativní integraci se sadou HttpClientFactory je doporučený postup pro jističe.</span><span class="sxs-lookup"><span data-stu-id="94748-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with HttpClientFactory.</span></span>

<span data-ttu-id="94748-124">Přidání zásady jistič do vaší HttpClientFactory odchozí kanál middlewaru je stejně jednoduché jako přidání přírůstkové jednoduchým kódu, které už jste při použití HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="94748-124">Adding a circuit breaker policy into your HttpClientFactory outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using HttpClientFactory.</span></span>

<span data-ttu-id="94748-125">Jenom přidávat tady na kód použitý pro opakování volání HTTP je kód, kde přidáte zásady jistič do seznamu zásad k použití, jak je znázorněno v následujícím kódu přírůstkové, součást ConfigureServices() metody.</span><span class="sxs-lookup"><span data-stu-id="94748-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to 5 minutes
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="94748-126">`AddPolicyHandler()`Metoda je co přidá do HttpClient objekty, kterou použijete zásady.</span><span class="sxs-lookup"><span data-stu-id="94748-126">The `AddPolicyHandler()`method is what adds policies to the HttpClient objects you will use.</span></span> <span data-ttu-id="94748-127">V takovém případě ji je přidání zásad Polly pro jističe.</span><span class="sxs-lookup"><span data-stu-id="94748-127">In this case, it is adding a Polly’s policy for a circuit breaker.</span></span>

<span data-ttu-id="94748-128">Pokud chcete mít modulárnější přístup, je definován jistič zásad v samostatné metodě s názvem GetCircuitBreakerPolicy() jako následující kód.</span><span class="sxs-lookup"><span data-stu-id="94748-128">In order to have a more modular approach, the Circuit Breaker Policy is defined in a separate method named GetCircuitBreakerPolicy(), as the following code.</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="94748-129">Ve výše uvedeném příkladu kódu jistič nakonfigurované tak, aby přeruší nebo otevře okruh, když byly pět výjimky při opakování požadavků Http.</span><span class="sxs-lookup"><span data-stu-id="94748-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five exceptions when retrying the Http requests.</span></span> <span data-ttu-id="94748-130">Potom 30 sekund bude trvání nebo přerušení.</span><span class="sxs-lookup"><span data-stu-id="94748-130">Then, 30 seconds will be the duration or the break.</span></span>

<span data-ttu-id="94748-131">Jističe by měla také sloužit k přesměrování požadavků na infrastrukturu pro použití náhradní lokality, pokud jste měli problémy v konkrétní prostředek, který je nasazený v jiném prostředí než klientská aplikace nebo služba, která provádí volání HTTP.</span><span class="sxs-lookup"><span data-stu-id="94748-131">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="94748-132">Tímto způsobem, pokud dojde k výpadku datového centra, který ovlivňuje pouze mikroslužby back-endu, ale ne klientských aplikací, klientské aplikace můžete přesměrovat náhradní služby.</span><span class="sxs-lookup"><span data-stu-id="94748-132">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="94748-133">Polly je plánování novou zásadu pro tento proces zautomatizovat [zásady převzetí služeb při selhání](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scénář.</span><span class="sxs-lookup"><span data-stu-id="94748-133">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span> 

<span data-ttu-id="94748-134">Všechny tyto funkce jsou určené pro případy, kde spravujete převzetí služeb při selhání z kódu .NET, na rozdíl od to spravuje automaticky za vás Azure, se místo průhlednosti.</span><span class="sxs-lookup"><span data-stu-id="94748-134">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span> 

<span data-ttu-id="94748-135">Z využití hlediska, když pomocí položky HttpClient není potřeba nic nového přidejte sem kód je stejný než při použití HttpClient s HttpClientFactory, jak je znázorněno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="94748-135">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using HttpClient with HttpClientFactory, as shown in previous sections.</span></span> 

## <a name="testing-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="94748-136">Testování opakování Http a jističe v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="94748-136">Testing Http retries and circuit breakers in eShopOnContainers</span></span>


<span data-ttu-id="94748-137">Pokaždé, když spustíte aplikaci eShopOnContainers řešení v hostitele Docker, je potřeba spustit několik kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="94748-137">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="94748-138">Některé z kontejnerů jsou pomalejší spuštění a inicializaci, jako je kontejner SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="94748-138">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="94748-139">To platí zejména při prvním nasazení aplikace aplikaci eShopOnContainers do Docker, protože se musí nastavit databázi a imagí.</span><span class="sxs-lookup"><span data-stu-id="94748-139">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="94748-140">Skutečnost, že některé kontejnery pomaleji, než ostatní může způsobit rest služby, které mají zpočátku vyvolávat výjimky HTTP, i když nastavíte závislosti mezi kontejnery na spuštění docker-compose úroveň, jak je popsáno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="94748-140">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="94748-141">Ty docker-compose závislosti mezi kontejnery jsou pouze na úrovni procesu.</span><span class="sxs-lookup"><span data-stu-id="94748-141">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="94748-142">Může spuštění kontejneru vstupní bod procesu, ale systém SQL Server pravděpodobně není připravena pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="94748-142">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="94748-143">Výsledkem může být kaskádové chyby a aplikaci můžete získat výjimku při pokusech o využívání této konkrétní kontejner.</span><span class="sxs-lookup"><span data-stu-id="94748-143">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span> 

<span data-ttu-id="94748-144">Můžete si také prohlédnout tohoto typu chyby při spuštění po nasazení aplikace do cloudu.</span><span class="sxs-lookup"><span data-stu-id="94748-144">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="94748-145">V takovém případě orchestrátorů může být přesunování kontejnerů z jednoho uzlu nebo virtuální počítač do jiného (který se spouštěním nových instancí) při vyrovnávání zatížení počet kontejnerů napříč uzly clusteru.</span><span class="sxs-lookup"><span data-stu-id="94748-145">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="94748-146">Způsob "aplikaci eShopOnContainers" řeší tyto problémy při spuštění všech kontejnerů pomocí modelu opakování jsme si uváděli dříve.</span><span class="sxs-lookup"><span data-stu-id="94748-146">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span> 

### <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="94748-147">Testování jističe v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="94748-147">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="94748-148">Existuje několik způsobů můžete přerušení/open okruh a testování s aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="94748-148">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="94748-149">Jednou z možností je na nižší povolený počet opakovaných pokusů pro 1 v zásadách jistič a znovu nasadit celé řešení do Docker.</span><span class="sxs-lookup"><span data-stu-id="94748-149">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="94748-150">Pomocí jednoho opakování je dobré pravděpodobné, že během nasazení se nezdaří požadavek HTTP, jistič se otevře a dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="94748-150">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="94748-151">Další možností je použití vlastního middlewaru, který je implementován v košíku mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="94748-151">Another option is to use custom middleware that is implemented in the Basket microservice.</span></span> <span data-ttu-id="94748-152">Pokud je povoleno tento middleware, zachytí všechny požadavky HTTP a vrátí stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="94748-152">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="94748-153">Můžete povolit middleware provedením požadavku GET selhání identifikátor URI, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="94748-153">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`

<span data-ttu-id="94748-154">Tento požadavek vrátí aktuální stav middlewaru.</span><span class="sxs-lookup"><span data-stu-id="94748-154">This request returns the current state of the middleware.</span></span> <span data-ttu-id="94748-155">Pokud je povolené middleware, požadavek vrátit stavový kód 500.</span><span class="sxs-lookup"><span data-stu-id="94748-155">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="94748-156">Pokud je zakázané middleware, nepřijde žádná odpověď.</span><span class="sxs-lookup"><span data-stu-id="94748-156">If the middleware is disabled, there is no response.</span></span> 

- `GET http://localhost:5103/failing?enable`

<span data-ttu-id="94748-157">Tento požadavek umožňuje middleware.</span><span class="sxs-lookup"><span data-stu-id="94748-157">This request enables the middleware.</span></span> 

- `GET http://localhost:5103/failing?disable`

<span data-ttu-id="94748-158">Tento požadavek zakáže middleware.</span><span class="sxs-lookup"><span data-stu-id="94748-158">This request disables the middleware.</span></span> 

<span data-ttu-id="94748-159">Pro instanci Jakmile je aplikace spuštěna, můžete povolit middleware tím, že žádost pomocí následující identifikátor URI v jakémkoli prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="94748-159">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="94748-160">Všimněte si, že pořadí mikroslužeb používá port 5103.</span><span class="sxs-lookup"><span data-stu-id="94748-160">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable` 

<span data-ttu-id="94748-161">Potom můžete zkontrolovat stav použitím tohoto identifikátoru URI http://localhost:5103/failing, jak ukazuje obrázek 10 až 4.</span><span class="sxs-lookup"><span data-stu-id="94748-161">You can then check the status using the URI http://localhost:5103/failing, as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="94748-162">**Obrázek 10-4**.</span><span class="sxs-lookup"><span data-stu-id="94748-162">**Figure 10-4**.</span></span> <span data-ttu-id="94748-163">Kontroluje se stav "Selhání" middleware ASP.NET – v takovém případě zakázané.</span><span class="sxs-lookup"><span data-stu-id="94748-163">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="94748-164">V tomto okamžiku nákupní košík mikroslužeb odpoví stavový kód 500 pokaždé, když voláte ho vyvolat.</span><span class="sxs-lookup"><span data-stu-id="94748-164">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="94748-165">Jakmile middleware běží, můžete zkusit provádění objednávky z webové aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="94748-165">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="94748-166">Protože požadavky nesplní, otevře se okruh.</span><span class="sxs-lookup"><span data-stu-id="94748-166">Because the requests fail, the circuit will open.</span></span> 

<span data-ttu-id="94748-167">V následujícím příkladu vidíte, že má webová aplikace MVC bloku catch bloku v logiku pro zadání objednávky.</span><span class="sxs-lookup"><span data-stu-id="94748-167">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="94748-168">Pokud kód zachytí výjimku open okruhu, ukazuje uživateli popisný zpráva s upozorněním čekání.</span><span class="sxs-lookup"><span data-stu-id="94748-168">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="94748-169">Toto je souhrn.</span><span class="sxs-lookup"><span data-stu-id="94748-169">Here’s a summary.</span></span> <span data-ttu-id="94748-170">Zásady opakování se pokusí několikrát, chcete-li požadavek HTTP a získá chyby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="94748-170">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="94748-171">Maximální číslo nastavené zásady jistič (v tomto případě 5) dosáhne počet opakovaných pokusů, vyvolá výjimku BrokenCircuitException aplikace.</span><span class="sxs-lookup"><span data-stu-id="94748-171">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="94748-172">Výsledkem je přátelskou zprávou, jak ukazuje obrázek 10 – 5.</span><span class="sxs-lookup"><span data-stu-id="94748-172">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="94748-173">**Obrázek 10 až 5**.</span><span class="sxs-lookup"><span data-stu-id="94748-173">**Figure 10-5**.</span></span> <span data-ttu-id="94748-174">Jistič vrátit chybu v uživatelském rozhraní</span><span class="sxs-lookup"><span data-stu-id="94748-174">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="94748-175">Můžete implementovat jiný logiku pro případ otevřít/přerušení okruh.</span><span class="sxs-lookup"><span data-stu-id="94748-175">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="94748-176">Nebo můžete zkusit požadavek HTTP na různé back-end mikroslužeb, pokud záložního datacentra nebo redundantní back endovému systému.</span><span class="sxs-lookup"><span data-stu-id="94748-176">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span> 

<span data-ttu-id="94748-177">A konečně Další možností pro `CircuitBreakerPolicy` je použití `Isolate` (což vynutí otevřít barvy a obsahuje otevřené okruhu) a `Reset` (který ukončí ho znovu).</span><span class="sxs-lookup"><span data-stu-id="94748-177">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="94748-178">Ty se používal k sestavení nástroj koncový bod HTTP, vyvolávající izolovat a obnovit přímo v této zásadě.</span><span class="sxs-lookup"><span data-stu-id="94748-178">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="94748-179">Takové koncový bod HTTP také lze použít řádně zabezpečená, v produkčním prostředí pro příjem dat systému, například když chcete upgradovat dočasně izolaci.</span><span class="sxs-lookup"><span data-stu-id="94748-179">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="94748-180">Nebo ji může dojít okruh ručně, aby se ochrana systému příjem dat, které předpokládáte, chcete-li být chybující.</span><span class="sxs-lookup"><span data-stu-id="94748-180">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>


## <a name="additional-resources"></a><span data-ttu-id="94748-181">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="94748-181">Additional resources</span></span>


-   <span data-ttu-id="94748-182">**Model jistič**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="94748-182">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="94748-183">[Předchozí](implement-http-call-retries-exponential-backoff-polly.md)
[další](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="94748-183">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
