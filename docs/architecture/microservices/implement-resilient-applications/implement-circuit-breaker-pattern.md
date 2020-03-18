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
# <a name="implement-the-circuit-breaker-pattern"></a>Implementace systému jističe

Jak již bylo uvedeno dříve, měli byste zpracovat chyby, které mohou trvat proměnné množství času zotavit se z, jak se může stát při pokusu o připojení ke vzdálené službě nebo prostředku. Zpracování tohoto typu poruchy může zlepšit stabilitu a odolnost aplikace.

V distribuovaném prostředí mohou volání vzdálených prostředků a služeb selhat z důvodu přechodných chyb, jako jsou pomalá síťová připojení a časové toky, nebo pokud prostředky reagují pomalu nebo jsou dočasně nedostupné. Tyto chyby obvykle opravit sami po krátké době a robustní cloudová aplikace by měla být připravena k jejich zpracování pomocí strategie, jako je "Opakování vzor".

Mohou však také nastat situace, kdy jsou chyby způsobeny neočekávanými událostmi, které mohou trvat mnohem déle. Tyto chyby můžou být různě závažné, od částečného výpadku připojení až po úplné selhání služby. V těchto situacích může být zbytečné pro aplikaci neustále opakovat operaci, která je nepravděpodobné, že úspěšné.

Místo toho by měla být aplikace kódována tak, aby akceptovala, že operace selhala, a odpovídajícím způsobem zpracovat selhání.

Použití http opakování nedbale může mít za následek vytvoření útoku odmítnutí služby[(DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack)v rámci vlastního softwaru. Jako mikroslužba selže nebo provádí pomalu, více klientů může opakovaně opakovat neúspěšné požadavky. To vytváří nebezpečné riziko exponenciálně rostoucího provozu zaměřeného na selhávající službu.

Proto potřebujete nějakou obrannou bariéru, aby se nadměrné požadavky zastavily, když to nestojí za to, aby se snažil. Ta obranná bariéra je přesně jistič.

Vzor jističe má jiný účel než "Opakovat vzor". "Opakovat vzor" umožňuje aplikaci opakovat operaci v očekávání, že operace bude nakonec úspěšné. Vzor jistič zabrání aplikaci provádět operace, která je pravděpodobně nezdaří. Aplikace může kombinovat tyto dva vzory. Logika opakování by však měla být citlivá na jakoukoli výjimku vrácenou jističem a měla by opustit pokusy o opakování, pokud jistič indikuje, že chyba není přechodná.

## <a name="implement-circuit-breaker-pattern-with-ihttpclientfactory-and-polly"></a>Implementujte schéma `IHttpClientFactory` jističe s Polly a Polly

Stejně jako při implementaci opakování je doporučeným přístupem pro jističe využít osvědčené knihovny .NET, jako je Polly a jeho nativní integrace s `IHttpClientFactory`.

Přidání zásad jističe `IHttpClientFactory` do odchozího kanálu middlewaru je stejně jednoduché jako přidání jednoho `IHttpClientFactory`přírůstkového kódu k tomu, co již máte při použití .

Jediným doplňkem kódu použitého pro opakování volání HTTP je kód, ve kterém přidáte zásadu jističe do seznamu zásad, které chcete použít, jak je znázorněno v následujícím přírůstkovém kódu, který je součástí metody ConfigureServices().

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Metoda `AddPolicyHandler()` je to, co `HttpClient` přidává zásady k objektům, které budete používat. V tomto případě je to přidání Polly politiky pro jistič.

Chcete-li mít více modulární přístup, jistič zásady `GetCircuitBreakerPolicy()`je definována v samostatné metodě s názvem , jak je znázorněno v následujícím kódu:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

V příkladu kódu výše je nakonfigurován ajistič zásady tak, aby se přeruší nebo otevře okruh, když došlo k pěti po sobě jdoucích chyb při opakování požadavků http. Když se to stane, obvod se zlomí po dobu 30 sekund: v tomto období budou volání okamžitě neúspěšná jističem, spíše než skutečně umístěna.  Zásada automaticky interpretuje [příslušné výjimky a stavové kódy HTTP](/aspnet/core/fundamentals/http-requests#handle-transient-faults) jako chyby.  

Jističe by měly být také použity k přesměrování požadavků na záložní infrastrukturu, pokud jste měli problémy v určitém prostředku, který je nasazen v jiném prostředí než klientská aplikace nebo služba, která provádí volání HTTP. Tímto způsobem pokud je výpadek v datovém centru, který má vliv pouze na vaše back-endové mikroslužby, ale ne klientské aplikace, klientské aplikace můžete přesměrovat na záložní služby. Polly plánuje novou zásadu pro automatizaci tohoto scénáře [zásad převzetí služeb při selhání.](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)

Všechny tyto funkce jsou pro případy, kdy spravujete převzetí služeb při selhání z v rámci kódu .NET, na rozdíl od toho, že ho spravujete automaticky azure, s transparentností umístění.

Z hlediska využití, při použití HttpClient, není třeba přidávat nic nového zde, protože `HttpClient` kód `IHttpClientFactory`je stejný jako při použití s , jak je znázorněno v předchozích částech.

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Testování http opakování a jističů v eShopOnContainers

Při každém spuštění řešení eShopOnContainers v hostiteli Dockeru, je potřeba spustit více kontejnerů. Některé kontejnery jsou pomalejší spuštění a inicializovat, jako je kontejner serveru SQL Server. To platí zejména při prvním nasazení aplikace eShopOnContainers do Dockeru, protože potřebuje nastavit bitové kopie a databázi. Skutečnost, že některé kontejnery spustit pomaleji než ostatní může způsobit, že zbytek služeb zpočátku vyvolat výjimky HTTP, i v případě, že nastavíte závislosti mezi kontejnery na úrovni docker-compose, jak je vysvětleno v předchozích částech. Tyto docker-compose závislosti mezi kontejnery jsou pouze na úrovni procesu. Proces vstupního bodu kontejneru může být spuštěn, ale SQL Server nemusí být připraven pro dotazy. Výsledkem může být kaskáda chyb a aplikace může získat výjimku při pokusu o využití tohoto konkrétního kontejneru.

Tento typ chyby se může zobrazit také při spuštění při nasazování aplikace do cloudu. V takovém případě může orchestrátory přesouvání kontejnerů z jednoho uzlu nebo virtuálního uživatele do jiného (to znamená spuštění nových instancí) při vyrovnávání počtu kontejnerů mezi uzly clusteru.

Způsob, jakým 'eShopOnContainers' řeší tyto problémy při spuštění všech kontejnerů je pomocí opakování vzor ilustrované dříve.

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>Otestujte jistič v eShopOnContainers

Existuje několik způsobů, jak můžete přerušit/ otevřít obvod a otestovat jej pomocí eShopOnContainers.

Jednou z možností je snížit povolený počet opakování na 1 v zásadě jističe a znovu nasadit celé řešení do Dockeru. Při jednom opakování je pravděpodobné, že požadavek HTTP se nezdaří během nasazení, jistič se otevře a zobrazí se chyba.

Další možností je použití vlastního middlewaru, který je implementován v mikroslužbě **košíku.** Pokud je tento middleware povolen, zachytí všechny požadavky HTTP a vrátí stavový kód 500. Middleware můžete povolit tak, že požadavek GET na selhání URI, jako je následující:

- `GET http://localhost:5103/failing`\
  Tento požadavek vrátí aktuální stav middleware. Pokud je middleware povoleno, požadavek vrátí stavový kód 500. Pokud je middleware zakázáno, neexistuje žádná odpověď.

- `GET http://localhost:5103/failing?enable`\
  Tento požadavek umožňuje middleware.

- `GET http://localhost:5103/failing?disable`\
  Tento požadavek zakáže middleware.

Například, jakmile je aplikace spuštěna, můžete povolit middleware tím, že žádost pomocí následujícího URI v libovolném prohlížeči. Všimněte si, že objednávání mikroslužby používá port 5103.

`http://localhost:5103/failing?enable`

Stav pak můžete zkontrolovat pomocí `http://localhost:5103/failing`identifikátoru URI , jak je znázorněno na obrázku 8-5.

![Snímek obrazovky se zjišnou stavem neúspěšné simulace middlewaru.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

**Obrázek 8-5**. Kontrola stavu "Selhání" ASP.NET middleware – V tomto případě zakázáno.

V tomto okamžiku mikroslužby košíku odpoví stavový kód 500 při každém volání vyvolat.

Jakmile je middleware spuštěn, můžete zkusit objednávku z webové aplikace MVC. Protože požadavky se nezdaří, okruh se otevře.

V následujícím příkladu uvidíte, že webová aplikace MVC má blok catch v logice pro zadání objednávky.  Pokud kód zachytí výjimku otevřeného okruhu, zobrazí uživateli popisnou zprávu s oznámením, aby počkali.

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

Zde je shrnutí. Zásada opakování se několikrát pokusí vytvořit požadavek HTTP a získá chyby PROTOKOLU HTTP. Když počet opakování dosáhne maximální počet nastavený pro zásady jistič (v tomto případě 5), aplikace vyvolá BrokenCircuitException. Výsledkem je přátelská zpráva, jak je znázorněno na obrázku 8-6.

![Snímek obrazovky s webovou aplikací MVC s nefunkční chybou služby košíku](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

**Obrázek 8-6**. Jistič vracející chybu do ui

Můžete implementovat různé logiky pro otevření/přerušení obvodu. Nebo můžete zkusit požadavek HTTP proti jiné back-end mikroslužby, pokud existuje záložní datové centrum nebo redundantní back-end systému.

A konečně, `CircuitBreakerPolicy` další možností `Isolate` pro použití (který nutí otevřít `Reset` a drží otevřít obvod) a (který jej zavře znovu). Ty by mohly být použity k vytvoření koncového bodu http nástroje, který vyvolá Izolovat a Obnovit přímo na zásady.  Takový koncový bod HTTP by také mohl být použit, vhodně zabezpečený, v produkčním prostředí pro dočasně izolaci navazujícího systému, například když jej chcete upgradovat. Nebo by to mohlo zakopnout oklikou ručně, aby byl chráněn navazující systém, o kterých máte podezření, že je vadný.

## <a name="additional-resources"></a>Další zdroje

- **Vzor jističe**\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Předchozí](implement-http-call-retries-exponential-backoff-polly.md)
>[další](monitor-app-health.md)
