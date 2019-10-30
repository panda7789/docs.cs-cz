---
title: Implementace vzoru pro přerušení okruhu
description: Naučte se implementovat vzor pro přerušení okruhu jako doplňkový systém pro opakované pokusy http.
ms.date: 10/16/2018
ms.openlocfilehash: a1a24094ae98d8c767ccf692fe8ded6e28d47854
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094119"
---
# <a name="implement-the-circuit-breaker-pattern"></a>Implementace systému jističe

Jak bylo uvedeno dříve, měli byste zpracovat chyby, které mohou trvat proměnlivou dobu, kdy se může stát, když se pokusíte připojit ke vzdálené službě nebo prostředku. Zpracování tohoto typu chyby může zlepšit stabilitu a odolnost aplikace.

V distribuovaném prostředí můžou volání vzdálených prostředků a služeb selhat kvůli přechodným chybám, třeba k pomalým síťovým připojením a časovým limitům, nebo pokud prostředky nereagují pomalu nebo jsou dočasně nedostupné. Tyto chyby se obvykle po krátké době opravují a robustní cloudová aplikace by se měla připravit na jejich zpracování pomocí strategie, jako je "vzor opakování".

Mohou však nastat situace, kdy jsou chyby způsobeny neočekávanými událostmi, které mohou trvat mnohem déle. Tyto chyby můžou být v rozsahu závažnosti od částečné ztráty připojení k úplnému selhání služby. V těchto situacích může být bezúčelné, aby aplikace nepřetržitě opakovala operaci, která pravděpodobně nebude úspěšná.

Místo toho by měla být aplikace kódována tak, aby přijímala, že operace se nezdařila, a odpovídajícím způsobem zpracovat selhání.

Použití carelessly pokusů http by mohlo vést k tomu, že by bylo možné vytvořit útok na útok[DOS (Denial](https://en.wikipedia.org/wiki/Denial-of-service_attack)of Service) ve vašem vlastním softwaru. Když mikroslužba selhává nebo pracuje pomalu, může opakované pokusy o neúspěšných pokusech o více klientů. Tím se vytvoří nebezpečné riziko exponenciálního zvyšování provozu zaměřeného na neúspěšné služby.

Proto budete potřebovat určitý druh bariéry proti obraně, aby se nadměrné požadavky zastavily, když nebudete muset dál zkoušet. Tato bariéra obrany je přesně na konci okruhu.

Vzor přerušení okruhu má jiný účel než "vzor opakování". "Vzor opakování" umožňuje aplikaci opakovat operaci s očekáváním, že operace bude nakonec úspěšná. Vzor přerušení okruhu brání aplikaci v provedení operace, která pravděpodobně selže. Aplikace může kombinovat tyto dva vzory. Logika opakování by však měla být citlivá na jakoukoli výjimku vrácenou koncovým objektem okruhu a měla by porušovat opakované pokusy, pokud je indikátorem okruhu indikováno, že chyba není přechodná.

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a>Implementace vzoru pro dělení na okruhy pomocí HttpClientFactory a Polly

Stejně jako při implementaci opakování je doporučený postup pro přerušení okruhů, který využívá osvědčené knihovny .NET, jako je Polly a její nativní integraci s HttpClientFactory.

Přidání zásad pro doplňování okruhů do odchozího kanálu middlewaru HttpClientFactory je jednoduché, protože do toho, co už máte při použití HttpClientFactory, přidáte jenom jednu přírůstkovou část kódu.

Jediným přidaným kódem, který se používá pro opakované pokusy o volání HTTP, je kód, kde přidáte zásadu pro přerušení okruhů do seznamu zásad, které chcete použít, jak je znázorněno v následujícím přírůstkovém kódu, který je součástí metody ConfigureServices ().

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Metoda `AddPolicyHandler()` je to, co přidává zásady pro objekty `HttpClient`, které budete používat. V takovém případě přidá zásady Polly pro přepínací modul okruhů.

Chcete-li mít více modulární přístup, je zásada pro přerušení okruhu definována v samostatné metodě s názvem `GetCircuitBreakerPolicy()`, jak je znázorněno v následujícím kódu:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

Ve výše uvedeném příkladu kódu je zásada pro přerušení okruhu nakonfigurovaná tak, že se přeruší nebo otevře okruh v případě, že při opakování požadavků HTTP došlo k pěti po sobě jdoucími chybám. Pokud k tomu dojde, okruh bude po dobu 30 sekund přerušen: v takovém případě budou volání okamžitě neúspěšná pomocí přepínacího modulu okruhů, nikoli ve skutečnosti.  Zásady automaticky interpretují [relevantní výjimky a stavové kódy http](/aspnet/core/fundamentals/http-requests#handle-transient-faults) jako chyby.  

K přesměrování požadavků na záložní infrastrukturu by se měly také použít vypínače okruhů, pokud máte problémy v konkrétním prostředku, který je nasazený v jiném prostředí než klientská aplikace nebo služba provádějící volání HTTP. Tímto způsobem dojde v případě výpadku v datovém centru, které ovlivňuje pouze vaše mikroslužby back-end, ale ne klientské aplikace, a klientské aplikace se mohou přesměrovat na záložní služby. Polly plánuje novou zásadu pro automatizaci tohoto scénáře [zásad převzetí služeb při selhání](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) .

Všechny tyto funkce jsou pro případy, kdy spravujete převzetí služeb při selhání z kódu .NET, a to na rozdíl od toho, že je spravujete automaticky za vás Azure s transparentností polohy.

Z bodu použití v zobrazení není nutné přidávat nic nového, protože kód je stejný, než když používáte HttpClient s HttpClientFactory, jak je znázorněno v předchozích částech.

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Testování opakovaných pokusů http a přepínacích cyklů okruhů v eShopOnContainers

Kdykoli na hostiteli Docker spustíte řešení eShopOnContainers, musí být spuštěno více kontejnerů. U některých kontejnerů je pomalejší spuštění a inicializace, jako je SQL Server kontejner. To platí hlavně při prvním nasazení aplikace eShopOnContainers do Docker, protože je potřeba nastavit Image a databázi. Vzhledem k tomu, že některé kontejnery začínají pomalejší než jiné, může dojít k tomu, že zbytek služeb zpočátku vyvolá výjimky HTTP, a to i v případě, že nastavíte závislosti mezi kontejnery na úrovni Docker-skládání, jak je vysvětleno v předchozích částech. Tyto závislosti v Docker – skládání mezi kontejnery jsou pouze na úrovni procesu. Můžete spustit proces vstupního bodu kontejneru, ale SQL Server nemusí být připravený na dotazy. Výsledkem může být kaskáda chyb a aplikace může získat výjimku při pokusu o využití tohoto konkrétního kontejneru.

Při nasazování aplikace do cloudu můžete také zobrazit tento typ chyby při spuštění. V takovém případě mohou orchestrace přesunout kontejnery z jednoho uzlu nebo virtuálního počítače do jiného (to znamená spouštění nových instancí) při vyrovnávání počtu kontejnerů v uzlech clusteru.

Způsob, jakým "eShopOnContainers" řeší tyto problémy při spouštění všech kontejnerů, je pomocí vzoru opakování popsaného výše.

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>Test přerušení okruhu v eShopOnContainers

Existuje několik způsobů, jak můžete okruh přerušit/otevřít a otestovat ho pomocí eShopOnContainers.

Jednou z možností je snížit povolený počet opakovaných pokusů na 1 v zásadách pro dělení na okruhy a znovu nasadit celé řešení do Docker. Při jednom opakovaném pokusu je pravděpodobné, že během nasazování selže požadavek HTTP, dojde k otevření přerušení okruhu a zobrazí se chyba.

Další možností je použít vlastní middleware, který je implementován v mikroslužbě **koše** . Pokud je tento middleware povolený, zachytává všechny požadavky HTTP a vrátí stavový kód 500. Middleware můžete povolit tím, že vytvoříte požadavek GET na identifikátor URI, který se nezdaří, například následující:

- `GET http://localhost:5103/failing`\
  Tento požadavek vrátí aktuální stav middleware. Pokud je povolen middleware, požadavek vrátí stavový kód 500. Pokud je middleware zakázán, neexistuje žádná odpověď.

- `GET http://localhost:5103/failing?enable`\
  Tento požadavek povoluje middleware.

- `GET http://localhost:5103/failing?disable`\
  Tato žádost zakáže middleware.

Například po spuštění aplikace můžete povolit middleware pomocí následujícího identifikátoru URI v jakémkoli prohlížeči. Všimněte si, že mikroslužba řazení používá port 5103.

`http://localhost:5103/failing?enable`

Potom můžete stav ověřit pomocí `http://localhost:5103/failing`identifikátoru URI, jak je znázorněno na obrázku 8-5.

![Zobrazení prohlížeče výsledku z kontroly stavu neúspěšné simulace middlewaru](./media/image4.png)

**Obrázek 8-5**. Kontroluje se stav neúspěšného middlewaru ASP.NET pro selhání – v tomto případě je zakázaný.

V tomto okamžiku bude mikroslužba košíku reagovat se stavovým kódem 500, kdykoli volání vyvolá.

Jakmile middleware běží, můžete vyzkoušet vytvoření objednávky z webové aplikace MVC. Vzhledem k tomu, že se požadavky selžou, okruh se otevře.

V následujícím příkladu vidíte, že webová aplikace MVC má v logice blok catch pro umístění objednávky.  Pokud kód zachytí výjimku otevřeného okruhu, zobrazí uživateli uživatelsky přívětivou zprávu s oznámením, že má počkat.

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

Tady je souhrn. Zásada opakování se několikrát pokusí vytvořit požadavek HTTP a získá chyby protokolu HTTP. Pokud počet opakování dosáhne maximálního počtu nastaveného pro zásadu pro dělení na okruhy (v tomto případě 5), aplikace vyvolá výjimku BrokenCircuitException. Výsledkem je Popisná zpráva, jak je znázorněno na obrázku 8-6.

![Zobrazení prohlížeče webové aplikace MVC znázorňující zprávu "nefunkční služba košíku", která se aktivuje zásadami pro přerušení okruhů](./media/image5.png)

**Obrázek 8-6**. Přepínací modul okruhů vrátil chybu do uživatelského rozhraní.

Můžete implementovat jinou logiku pro otevření nebo přerušení okruhu. Nebo můžete vyzkoušet požadavek HTTP na jinou back-end mikroslužbu, pokud existuje záložní datové centrum nebo redundantní back-end systém.

Nakonec je další možností pro `CircuitBreakerPolicy` použít `Isolate` (které vynutí otevření a blokování otevřeného okruhu) a `Reset` (které se znovu zavřou). Ty je možné použít k vytvoření koncového bodu HTTP nástroje, který vyvolá izolaci a resetování přímo na zásadě.  Takový koncový bod HTTP by se taky mohl použít, vhodně zabezpečený v produkčním prostředí pro dočasný izolaci systému pro příjem dat, třeba když ho chcete upgradovat. Nebo může obcházet okruh ručně, aby se chránil systém pro příjem dat, u kterého se domníváte, že se jedná o poruchu.

## <a name="additional-resources"></a>Další zdroje

- \ **vzoru pro přerušení okruhu**
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Předchozí](implement-http-call-retries-exponential-backoff-polly.md)
>[Další](monitor-app-health.md)
