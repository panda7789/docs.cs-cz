---
title: Implementace vzoru Circuit Breaker
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace vzoru Circuit Breaker jako doplňkové systém k opakování Http
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 8cd3564e5240ec5a8783edb336957549be27ea6a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193234"
---
# <a name="implement-the-circuit-breaker-pattern"></a>Implementace vzoru Circuit Breaker

Jak je uvedeno výše, by měl zpracovává chyby, které může trvat různě dlouho obnovit, protože může dojít při pokusu o připojení ke vzdálené službě nebo prostředku. Zpracování tohoto typu chyby může zlepšit stabilitu a odolnost aplikace.

V distribuovaném prostředí můžou volání vzdálených prostředků a služeb může selhat z důvodu přechodných chyb, jako jsou pomalé síťové připojení a časové limity, nebo pokud prostředky neodpovídá pomalu nebo jsou dočasně nedostupné. Tyto chyby obvykle opraví po krátkou dobu samy a robustní Cloudová aplikace by měla být připravena je zvládnout pomocí strategie, jako je model"opakování". 

Však mohou také existovat situace, kdy jsou chyby způsobeny nepředvídatelnými událostmi, které může trvat déle, chcete-li vyřešit. Tyto chyby můžou být různě od částečného výpadku připojení až po úplné selhání služby. V těchto situacích může být bezúčelné pro aplikaci neustále opakovat operaci, která pravděpodobně nebude úspěšná. 

Místo toho aplikace by měly být kódovány potvrďte, že operace se nezdařila a odpovídajícím způsobem chybu zpracovat.

Použití opakování Http neuváženě může vést k vytváření cílem odepření služeb ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) útoku v rámci vlastního softwaru. Mikroslužby selže nebo pomalu, více klientů může opakovaně opakování neúspěšných žádostí. Který vytváří nebezpečné riziko exponenciálně prodlužuje provozu zaměřený na selhávající službu.

Proto je nutné nějaký druh defense bariéry, tak, aby nadměrné požadavky zastavit, když není vhodné při zachování. Této bariéry defense je přesně jističe.

Model jistič má jiný účel než "model opakování". Model opakování"" umožňuje aplikaci opakovat operaci s předpokladem, že operace bude nakonec úspěšná. Model jistič zabraňuje aplikaci provést operaci, která pravděpodobně selže. Aplikace může tyto dva modely zkombinovat. Ale logika opakovaných pokusů by měl být citlivé na jakoukoliv výjimku, vrácené jističem a by provádět opakované pokusy, pokud jistič signalizuje, že chyba není přechodná.

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a>Implementace vzoru Circuit Breaker HttpClientFactory a Polly

Při implementaci opakovaných pokusů, využívat osvědčené knihovny .NET, jako jsou knihovny Polly a jeho nativní integraci se sadou HttpClientFactory je doporučený postup pro jističe.

Přidání zásady jistič do vaší HttpClientFactory odchozí kanál middlewaru je stejně jednoduché jako přidání přírůstkové jednoduchým kódu, které už jste při použití HttpClientFactory.

Jenom přidávat tady na kód použitý pro opakování volání HTTP je kód, kde přidáte zásady jistič do seznamu zásad k použití, jak je znázorněno v následujícím kódu přírůstkové, součást ConfigureServices() metody.

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to 5 minutes
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

`AddPolicyHandler()`Metoda je co přidá do HttpClient objekty, kterou použijete zásady. V takovém případě se přidává Polly zásadu jističe.

Pokud chcete mít modulárnější přístup, je definován jistič zásad v samostatné metodě s názvem GetCircuitBreakerPolicy() jako následující kód.

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

Ve výše uvedeném příkladu kódu jistič nakonfigurované tak, aby přeruší nebo otevře okruh, když byly pět po sobě jdoucích chyb při opakování požadavků Http. Pokud k tomu dojde, je okruh přeruší po dobu 30 sekund: v daném období volání bude možné provést okamžitě jističem-spíše než skutečně umístit.  Zásady automaticky interpretuje [relevantní výjimky a stavové kódy HTTP](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) jako chyby.  

Jističe by měla také sloužit k přesměrování požadavků na infrastrukturu pro použití náhradní lokality, pokud jste měli problémy v konkrétní prostředek, který je nasazený v jiném prostředí než klientská aplikace nebo služba, která provádí volání HTTP. Tímto způsobem, pokud dojde k výpadku datového centra, který ovlivňuje pouze mikroslužby back-endu, ale ne klientských aplikací, klientské aplikace můžete přesměrovat náhradní služby. Polly je plánování novou zásadu pro tento proces zautomatizovat [zásady převzetí služeb při selhání](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scénář. 

Všechny tyto funkce jsou určené pro případy, kde spravujete převzetí služeb při selhání z kódu .NET, na rozdíl od to spravuje automaticky za vás Azure, se místo průhlednosti. 

Z využití hlediska, když pomocí položky HttpClient není potřeba nic nového přidejte sem kód je stejný než při použití HttpClient s HttpClientFactory, jak je znázorněno v předchozích částech. 

## <a name="testing-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Testování opakování Http a jističe v aplikaci eShopOnContainers

Pokaždé, když spustíte aplikaci eShopOnContainers řešení v hostitele Docker, je potřeba spustit několik kontejnerů. Některé z kontejnerů jsou pomalejší spuštění a inicializaci, jako je kontejner SQL serveru. To platí zejména při prvním nasazení aplikace aplikaci eShopOnContainers do Docker, protože se musí nastavit databázi a imagí. Skutečnost, že některé kontejnery pomaleji, než ostatní může způsobit rest služby, které mají zpočátku vyvolávat výjimky HTTP, i když nastavíte závislosti mezi kontejnery na spuštění docker-compose úroveň, jak je popsáno v předchozích částech. Ty docker-compose závislosti mezi kontejnery jsou pouze na úrovni procesu. Může spuštění kontejneru vstupní bod procesu, ale systém SQL Server pravděpodobně není připravena pro dotazy. Výsledkem může být kaskádové chyby a aplikaci můžete získat výjimku při pokusech o využívání této konkrétní kontejner. 

Můžete si také prohlédnout tohoto typu chyby při spuštění po nasazení aplikace do cloudu. V takovém případě orchestrátorů může být přesunování kontejnerů z jednoho uzlu nebo virtuální počítač do jiného (který se spouštěním nových instancí) při vyrovnávání zatížení počet kontejnerů napříč uzly clusteru.

Způsob "aplikaci eShopOnContainers" řeší tyto problémy při spuštění všech kontejnerů pomocí modelu opakování jsme si uváděli dříve. 

### <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>Testování jističe v aplikaci eShopOnContainers

Existuje několik způsobů můžete přerušení/open okruh a testování s aplikaci eShopOnContainers.

Jednou z možností je na nižší povolený počet opakovaných pokusů pro 1 v zásadách jistič a znovu nasadit celé řešení do Docker. Pomocí jednoho opakování je dobré pravděpodobné, že během nasazení se nezdaří požadavek HTTP, jistič se otevře a dojde k chybě.

Další možností je použití vlastního middlewaru, který je implementován v košíku mikroslužeb. Pokud je povoleno tento middleware, zachytí všechny požadavky HTTP a vrátí stavový kód 500. Můžete povolit middleware provedením požadavku GET selhání identifikátor URI, jako je následující:

- `GET http://localhost:5103/failing`

Tento požadavek vrátí aktuální stav middlewaru. Pokud je povolené middleware, požadavek vrátit stavový kód 500. Pokud je zakázané middleware, nepřijde žádná odpověď. 

- `GET http://localhost:5103/failing?enable`

Tento požadavek umožňuje middleware. 

- `GET http://localhost:5103/failing?disable`

Tento požadavek zakáže middleware. 

Pro instanci Jakmile je aplikace spuštěna, můžete povolit middleware tím, že žádost pomocí následující identifikátor URI v jakémkoli prohlížeči. Všimněte si, že pořadí mikroslužeb používá port 5103.

`http://localhost:5103/failing?enable` 

Potom můžete zkontrolovat stav použitím tohoto identifikátoru URI http://localhost:5103/failing, jak ukazuje obrázek 10 až 4.

![](./media/image4.png)

**Obrázek 10-4**. Kontroluje se stav "Selhání" middleware ASP.NET – v takovém případě zakázané. 

V tomto okamžiku nákupní košík mikroslužeb odpoví stavový kód 500 pokaždé, když voláte ho vyvolat.

Jakmile middleware běží, můžete zkusit provádění objednávky z webové aplikace MVC. Protože požadavky nesplní, otevře se okruh. 

V následujícím příkladu vidíte, že má webová aplikace MVC bloku catch bloku v logiku pro zadání objednávky.  Pokud kód zachytí výjimku open okruhu, ukazuje uživateli popisný zpráva s upozorněním čekání.

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

Toto je souhrn. Zásady opakování se pokusí několikrát, chcete-li požadavek HTTP a získá chyby protokolu HTTP. Maximální číslo nastavené zásady jistič (v tomto případě 5) dosáhne počet opakovaných pokusů, vyvolá výjimku BrokenCircuitException aplikace. Výsledkem je přátelskou zprávou, jak ukazuje obrázek 10 – 5.

![](./media/image5.png)

**Obrázek 10 až 5**. Jistič vrátit chybu v uživatelském rozhraní

Můžete implementovat jiný logiku pro případ otevřít/přerušení okruh. Nebo můžete zkusit požadavek HTTP na různé back-end mikroslužeb, pokud záložního datacentra nebo redundantní back endovému systému. 

A konečně Další možností pro `CircuitBreakerPolicy` je použití `Isolate` (což vynutí otevřít barvy a obsahuje otevřené okruhu) a `Reset` (který ukončí ho znovu). Ty se používal k sestavení nástroj koncový bod HTTP, vyvolávající izolovat a obnovit přímo v této zásadě.  Takové koncový bod HTTP také lze použít řádně zabezpečená, v produkčním prostředí pro příjem dat systému, například když chcete upgradovat dočasně izolaci. Nebo ji může dojít okruh ručně, aby se ochrana systému příjem dat, které předpokládáte, chcete-li být chybující.


## <a name="additional-resources"></a>Další zdroje


-   **Model jistič**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)


>[!div class="step-by-step"]
[Předchozí](implement-http-call-retries-exponential-backoff-polly.md)
[další](monitor-app-health.md)
