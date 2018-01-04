---
title: "Implementace vzoru jistič"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace vzoru jistič"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d7db6899068f84f9165022cfbf17767a75e7db9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a>Implementace vzoru jistič

Jak jsme uvedli výše, by měla řídit chyb, které může trvat proměnné množství času dostat z, může dojít při pokusu o připojení k vzdálené služby nebo prostředku. Tento typ chyby zpracování může zvýšit stabilitu a odolnost aplikace.

V distribuovaném prostředí volání vzdálené prostředky a služby může selhat z důvodu přechodných chyb, jako je pomalé síťové připojení a vypršení časových limitů, nebo pokud jsou prostředky zpomalit nebo jsou dočasně nedostupné. Tyto chyby obvykle opravte po krátkou dobu sami a je třeba připravit robustní cloudových aplikací k jejich zpracování pomocí strategie jako vzor opakování.

Však může také nastat situace, kde jsou chyb z důvodu neočekávané události, které může trvat déle, chcete-li odstranit. Tyto chyby může být v rozsahu v závažnosti od částečné ztrátě připojení k úplnému selhání služby. V těchto situacích může být zbytečný pro aplikaci neustále opakujte operaci, která je pravděpodobně úspěšné. Místo toho by měly být napsané aplikace potvrďte, že operace se nezdařila a zpracování selhání odpovídajícím způsobem.

Vzor jistič má jiný účel než vzor opakování. Vzor opakování povolí aplikaci opakovat operace v očekávání, který nakonec operace proběhne úspěšně. Vzor jistič brání aplikaci v provádění operace, která je pravděpodobně selžou. Aplikace můžete kombinovat tyto dvě vzory pomocí vzoru opakování k vyvolání operace prostřednictvím jistič. Ale logika opakovaných pokusů by měla být citlivé na jakékoli výjimky vrácený vypínač a pokud vypínač signalizuje, že chybu není přechodný ho měli abandon počet pokusů o opakování.

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>Implementace vzoru jistič s Polly

Jako při implementaci opakování, umožní využít Principy knihovny .NET, jako je Polly je doporučený postup pro moduly okruh dělení.

Při implementaci HTTP opakování, používá aplikace eShopOnContainers Polly jistič zásad. Ve skutečnosti aplikace platí obě zásady pro třídu ResilientHttpClient nástroj. Vždy, když použijete objekt typu ResilientHttpClient požadavků HTTP (od eShopOnContainers), budou uplatňovat obě tyto zásady, ale můžete přidat další zásady, příliš.

Pouze přidání sem do kód použitý pro opakování volání HTTP je kód, kdy přidáte jistič zásad do seznamu zásad použití, jak je znázorněno na konci následující kód:

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

Kód přidá zásadu pro obálku protokolu HTTP. Aby zásad definuje jistič, které se otevře při kód zjistí zadaný počet po sobě jdoucích výjimek (výjimky v řádku), jako předán v parametru exceptionsAllowedBeforeBreaking (v tomto případě 5). Když okruh je otevřená, nefungují požadavků HTTP, ale je vyvolána výjimka.

Moduly dělení okruh by měla být používána pro přesměrování požadavků na infrastrukturu záložní, pokud může mít problémy v konkrétní prostředek, který je nasazen v jiném prostředí než klientská aplikace nebo služba, která provádí volání protokolu HTTP. Tímto způsobem, pokud dojde k výpadku v datovém centru, které ovlivňuje pouze vaše mikroslužeb back-end, ale ne klienta aplikace, můžete klientské aplikace přesměrovat do záložního služeb. Polly je plánování nové zásady k automatizaci to [zásad převzetí služeb při selhání](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scénář.

Samozřejmě všechny tyto funkce jsou pro případy, kdy spravujete převzetí služeb při selhání v rámci kód rozhraní .NET a nutnosti ho automaticky pro vás spravuje služba Azure, s průhlednost umístění.

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>Používání třídy nástroj ResilientHttpClient z eShopOnContainers

Můžete použít třídu nástroj ResilientHttpClient způsob použití třídy rozhraní .NET HttpClient podobným způsobem. V následujícím příkladu z webové aplikace MVC eShopOnContainers (OrderingService agenta třídu používá OrderController) je objekt ResilientHttpClient vložit prostřednictvím parametru httpClient konstruktoru. Objekt se pak používá k provedení požadavky HTTP.

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

Vždy, když \_apiClient člen objekt se používá, interně používá třídu obálky s Polly policiesؙ – zásady opakovaných pokusů, jistič zásady a jiné zásady, které můžete chtít použít z kolekce Polly zásady.

## <a name="testing-retries-in-eshoponcontainers"></a>Testování opakování v eShopOnContainers

Při každém spuštění eShopOnContainers řešení v nástroji Docker hostitele, musí se spustit několika kontejnerů. Některé z kontejnerů jsou pomalejší spuštění a inicializaci jako kontejneru systému SQL Server. To platí hlavně při prvním nasazení aplikace eShopOnContainers do Docker, protože je nutné nastavit bitové kopie a databáze. Skutečnost, že některé kontejnery něco pomalejší, než ostatní může způsobit zbytek služby původně vyvolat výjimky HTTP, i když nastavíte závislosti mezi kontejnery na spuštění docker compose úrovni, jak je popsáno v předchozí části. Ty docker tvoří závislosti mezi kontejnery jsou jenom na úrovni procesu. Kontejneru vstupní bod proces může být spuštěn, ale nemusí být připravené pro dotazy SQL Server. Výsledkem mohou být cascade chyb a aplikaci můžete získat výjimku při pokusu o využívání tohoto konkrétního kontejneru.

Můžete si také prohlédnout tohoto typu chyby na spuštění při nasazení aplikace v cloudu. V takovém případě orchestrators může být přesunutí kontejnery z jednoho uzlu nebo virtuální počítač na jiný (které spouští nové instance) při vyrovnávání počet kontejnerů mezi uzly clusteru.

Způsob eShopOnContainers řeší tento problém je pomocí opakování vzor, který jsme jsme si uváděli dříve. Je také proč, při spouštění řešení, mohou se zobrazovat protokolu trasování nebo upozornění takto:

> "**Opakujte 1 implementováno s RetryPolicy na Polly**, kvůli: System.Net.Http.HttpRequestException: při odesílání požadavku došlo k chybě. ---&gt;System.Net.Http.CurlException: Nelze se připojit k serveru\\n v System.Net.Http.CurlHandler.ThrowIfCURLEError (Chyba CURLcode)\\n v \[... \].

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>Testování vypínač v eShopOnContainers

Existuje několik způsobů, můžete otevřít okruhu a otestovat s eShopOnContainers.

Jednou z možností je na nižší povolený počet opakování 1 v zásadách jistič a znovu nasaďte celé řešení do Docker. Pomocí jednoho opakování je dobré pravděpodobné, že požadavek HTTP se nezdaří během nasazení, se otevře jistič a dojde k chybě.

Další možností je použít vlastní middleware, která je implementována v `Basket` mikroslužby. Pokud je povoleno tento middleware, zachytí všechny požadavky protokolu HTTP a vrátí stavový kód 500. Můžete povolit middleware tím, že požadavek GET na selhání identifikátor URI, třeba takto:

-   ZÍSKAT/selhání

Tento požadavek vrátí aktuální stav middleware. Pokud je povoleno middleware, žádost vrátí stavový kód 500. Pokud je zakázána middleware, nepřijde žádná odpověď.

-   ZÍSKAT/nedaří? povolit

Tento požadavek umožňuje middleware.

-   ZÍSKAT/nedaří? zakázat

Tento požadavek zakáže middleware.

Například když aplikace běží, můžete povolit middleware pomocí libovolného prohlížeče v následující identifikátor URI požadavku. Všimněte si, že řazení mikroslužbu používá port 5103.

http://localhost:5103 / nedaří? povolit

Potom můžete zkontrolovat stav pomocí identifikátoru URI [http://localhost:5103 / selhání](http://localhost:5103/failing), jak je znázorněno na obrázku 10-4.

![](./media/image4.png)

**Obrázek 10-4**. Kontroluje se stav "Selhání" middleware ASP.NET – v takovém případě zakázána. 

V tomto okamžiku odpoví mikroslužbu nákupního košíku se stavovým kódem 500 vždy, když zavoláte ji použít.

Jakmile middleware běží, můžete zkusit provedení pořadí z webové aplikace MVC. Protože žádosti se nezdařilo, otevře se okruh.

V následujícím příkladu vidíte, že má webová aplikace MVC catch blokovat v logiku pro umístění pořadí. Pokud kód zachytí výjimky otevřete okruh, ukazuje uživateli popisný zpráva s upozorněním čekání.

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

Zde je souhrn. Zásady opakování pokusí provést několikrát, chcete-li požadavek HTTP a získá chyby protokolu HTTP. Když počet pokusů dosáhne maximální číslo nastavené zásady jistič (v tomto případě 5), vyvolá aplikace BrokenCircuitException. Výsledkem je přátelskou zprávou, jak ukazuje obrázek 10-5.

![](./media/image5.png)

**Obrázek 10-5**. Jistič vrátila chybu do uživatelského rozhraní

Můžete implementovat jiný logiku pro při otevření okruh. Nebo můžete zkusit požadavek HTTP proti různých mikroslužbu back-end, pokud záložní datacenter nebo redundantní systému back-end.

Nakonec je další možností CircuitBreakerPolicy použití Isolate (která vynutí otevřete a obsahuje otevřete okruhu) a resetování (který zavře znovu). To může vytvořit nástroj pro koncový bod protokolu HTTP, která volá Isolate a resetování přímo na zásady. Takové koncový bod HTTP také může, vhodně zabezpečená, v produkčním prostředí dočasně oddělit podřízené systému, například když chcete upgradovat. Nebo ji může dojít okruhu ručně ochrana podřízené systému, které předpokládáte, chcete-li být chybující.

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>Přidávání zpoždění strategie do zásady opakovaných pokusů

Regulární zásady opakování může mít vliv na váš systém v případech vysoké souběžnosti a škálovatelnost a v části vysoké kolizí. K překonání vrcholů podobné opakování pocházejících z velkého počtu klientů v případě částečné výpadky, je dobré řešení přidat strategie kolísání do algoritmus nebo zásady opakování. Tím lze vylepšit celkový výkon systému začátku do konce přidáním náhodnost exponenciálního omezení rychlosti. To šíří se špičky případných problémech. Při použití Polly kód pro implementaci zpoždění může vypadat jako v následujícím příkladu:

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a>Další zdroje

-   **Opakujte vzor**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **Odolnost připojení** (Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Polly** (.NET odolnost a knihovna přechodná. selhání zpracování) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **Vzor jistič**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Marc Brooker. Zpoždění: Aby lépe s náhodnost** https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[Předchozí] (implement-http-call-retries-exponential-backoff-polly.md) [Další] (health.md monitorování aplikace)
