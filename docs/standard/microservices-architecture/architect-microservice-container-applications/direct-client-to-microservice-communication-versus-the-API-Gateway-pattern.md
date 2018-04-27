---
title: Přímé komunikaci klienta mikroslužbu versus vzoru Brána rozhraní API
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Přímé komunikaci klienta mikroslužbu versus vzoru Brána rozhraní API
keywords: Docker Mikroslužeb, ASP.NET, kontejner, brána rozhraní API
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fa3f4bb97cf942ee7698b1efa1dcd09b3f2ca571
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="direct-client-to-microservice-communication-versus-the-api-gateway-pattern"></a>Přímé komunikaci klienta mikroslužbu versus vzoru Brána rozhraní API

V architektuře mikroslužeb každý mikroslužbu zpřístupňuje řadu (obvykle) fine‑grained koncové body. Tato skutečnost může mít vliv client‑to‑microservice komunikaci, jak je popsáno v této části.

## <a name="direct-client-to-microservice-communication"></a>Přímé komunikaci klienta mikroslužbu

Možných přístupů je používat architekturu přímou komunikaci klienta mikroslužby. V tomto přístupu klientskou aplikaci můžete provést požadavky přímo některé mikroslužeb, jak ukazuje obrázek 4 – 12.

![](./media/image12.png)

**Obrázek 4 – 12**. Pomocí architektury přímou komunikaci klienta mikroslužbu

V tomto přístupu. Každý mikroslužbu má veřejný koncový bod, někdy s jiný port TCP pro každou mikroslužby. Příklad adresy URL pro konkrétní službu, může být následující adresu URL v Azure:

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

V produkčním prostředí založené na clusteru, která umožní mapování adresy URL pro vyrovnávání zatížení použít v clusteru, který naopak rozděluje požadavky na mikroslužeb. V produkčním prostředí, můžete mít aplikaci doručení řadiče (ADC) jako [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) mezi vaší mikroslužeb a Internetem. To funguje jako transparentní vrstvy, která pouze provede Vyrovnávání zatížení, ale zabezpečuje vašim službám prostřednictvím nabídky ukončení protokolu SSL. To zvyšuje zatížení hostitele, protože snižování zátěže ukončení protokolu SSL náročná na prostředky procesoru a další směrování dávky do služby Azure Application Gateway. Nástroj pro vyrovnávání zatížení a ADC jsou v každém případě transparentní z hlediska of Architektura logické aplikace.

Architektura přímou komunikaci klienta mikroslužbu může být vhodné dostatečně pro malá na základě mikroslužbu aplikace, zejména pokud je aplikace klienta webové serverové aplikace jako aplikace rozhraní ASP.NET MVC. Při vytváření velké a komplexní na základě mikroslužbu aplikací (například při zpracování desítek mikroslužbu typy) a zejména v případě, že jsou klientské aplikace vzdálené mobilní aplikace nebo SPA webových aplikací, ale tento přístup otočená několik problémů.

Při vývoji rozsáhlé aplikace založené na mikroslužeb, zvažte následující otázky:

-   *Jak aplikace klienta minimalizovat počet žádostí pro back-end a snížit chatty komunikaci s více mikroslužeb?*

Interakci s více mikroslužeb k vytvoření jedné obrazovce uživatelského rozhraní zvyšuje počet zbytečné komunikace přes Internet. Tím se zvyšuje latenci a složitost na straně uživatelského rozhraní. V ideálním případě odpovědí by měl být efektivně agregován v na straně serveru – tím se snižuje latence, protože data na více místech vraťte paralelně a některé uživatelského rozhraní můžete zobrazit data, jakmile je připraven.

-   *Jak může zpracovat mezi vyjímání otázky, jako je například autorizace, transformace dat a dynamické žádost o odeslání?*

Implementace zabezpečení a aspekty mezi vyjímání jako zabezpečení a autorizace na každý mikroslužbu může vyžadovat významné vývoj úsilí. Možných přístupů je mít těchto služeb v rámci hostitelů Docker nebo interní clusteru, aby bylo možné omezit přímý přístup k nim z vnějšku a implementovat tyto otázky mezi vyjímání v centrálním umístění, jako je brána rozhraní API.

-   *Jak může klientské aplikace komunikovat s služby, které používají protokoly Internetu popisný?*

Protokoly používá na straně serveru (například AMQP nebo binární protokoly) nepodporuje obvykle klientské aplikace. Proto musí být požadavky provést prostřednictvím protokolů jako protokolu HTTP nebo HTTPS a převedeny na ostatní protokoly později. A *man-in-the-middle* postup může pomoci v této situaci.

-   *Jak budete utvářejí průčelí za zejména provedené pro mobilní aplikace?*

Rozhraní API více mikroslužeb nemusí dobře navrženy pro potřeby různých klientských aplikací. Například potřebám mobilní aplikace může být jiná než potřebám webové aplikace. Pro mobilní aplikace možná budete muset i další optimalizace tak, aby data odpovědí může být efektivnější. Můžete to třeba udělat tak, že agregaci dat z více mikroslužeb a vrací jednu sadu dat a někdy odstranění všech dat v odpovědi, která není potřeba mobilní aplikace. A samozřejmě může komprimovat data. Znovu průčelí za nebo API mezi mobilní aplikaci a mikroslužeb může být vhodné pro tento scénář.

## <a name="using-an-api-gateway"></a>Pomocí služby Gateway rozhraní API

Při návrhu a vytvářet velká nebo složitá na základě mikroslužbu aplikace s více klientských aplikací, může být dobrým přístupem vzít v úvahu [Brána rozhraní API](https://microservices.io/patterns/apigateway.html). Toto je služba, která poskytuje jeden vstupní bod pro určité skupiny mikroslužeb. Je podobná [Facade vzor](https://en.wikipedia.org/wiki/Facade_pattern) z object‑oriented návrhu, ale v takovém případě je součástí distribuovaného systému. Vzor Brána rozhraní API se také někdy označuje jako "back-end pro front-endové" [(BFF)](https://samnewman.io/patterns/architectural/bff/) vzhledem k tomu, že vytvoříte při přemýšlení o potřebám klientské aplikace.

Obrázek 4 – 13 ukazuje, jak můžete začlenit vlastní Brána rozhraní API do architektury založené na mikroslužby.
Je důležité, abyste měli na očích, v tomto diagramu, budete používat jeden vlastní Brána rozhraní API služby čelí více a jiné klientské aplikace. Aby fakt může být důležité riziko, protože brána rozhraní API služby bude rostoucí a vyvíjející se na základě mnoho různých požadavků z klientské aplikace. Nakonec se z důvodu těchto různé potřeby bude opakovaném a efektivně může být poměrně podobná monolitický aplikace nebo monolitický služby. To je proto velmi výrazně se doporučuje rozdělení bránou rozhraní API v několika služeb nebo více menší API bran, jeden pro každý typ faktor formuláře pro instanci.

![](./media/image13.png)

**Obrázek 4 – 13**. Pomocí služby API Gateway implementovaný jako vlastní webového rozhraní API služby

V tomto příkladu by být bránou rozhraní API implementovaný jako vlastní webového rozhraní API služby spuštěné jako kontejner.

Jak je uvedeno, měli byste implementovat několik rozhraní API brány tak, aby může mít různé průčelí za pro potřeby každou klientskou aplikaci. Každý Brána rozhraní API můžete zadat jinou API přizpůsobené pro každou klientskou aplikaci, případně i na základě faktor formuláře klienta implementací konkrétní adaptér kód, který dole volá více interní mikroslužeb.

Vzhledem k tomu, že vlastní Brána rozhraní API je obvykle data agregátoru, musíte pečlivě s ním. Obvykle je vhodné jedinou Brána rozhraní API agregování všechny interní mikroslužeb vaší aplikace. Pokud ano, funguje jako monolitický agregátoru nebo orchestrator a spojovacích všechny mikroslužeb porušuje mikroslužbu nezávislé. Proto brány rozhraní API by měl být oddělené na základě obchodní hranice a není act jako agregátoru pro celou aplikaci.

Někdy granulární Brána rozhraní API můžete také být mikroslužbu sama o sobě a i domény nebo název firmy a související data. S bránou rozhraní API hranice závisí na podnik nebo doméně vám pomůže získat lepší návrhu.

Členitost ve vrstvě Brána rozhraní API může být užitečné zejména pro pokročilejší kompozitních aplikací uživatelského rozhraní založené na mikroslužeb, protože koncept podrobných Brána rozhraní API je podobná služby složení uživatelského rozhraní. To později probereme [vytváření složených uživatelského rozhraní založené na mikroslužeb](#creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices).

Proto pro mnoho aplikací, střední a velké velikosti, pomocí uživatelské rozhraní API brány je obvykle dobrou přístup, ale ne jako jeden monolitický agregátoru nebo jedinečný centrální vlastní Brána rozhraní API.

Další možností je použít produkt jako [Azure API Management](https://azure.microsoft.com/services/api-management/) jak ukazuje obrázek 4-14. Tento přístup pouze řeší potřeb Brána rozhraní API, ale poskytuje funkce, jako je shromažďování přehledy z vašich rozhraní API. Pokud používáte do řešení pro správu rozhraní API, bránu rozhraní API je pouze součástí v rámci tohoto řešení pro správu úplné rozhraní API.

![](./media/image14.png)

**Obrázek 4-14**. Pro bránu rozhraní API pomocí Azure API Management

V takovém případě při používání produktu, jako je Azure API Management, fakt, že můžete mít jeden Brána rozhraní API není tak rizikové, protože tyto druhy brány rozhraní API jsou "užší", což znamená, že nebudete implementovat vlastní C# kód, který by mohl vyvíjet monolitický komponenta. 

Tento typ produktu pracuje jako reverzní proxy server pro příchozí komunikaci, kde je můžete také filtrovat rozhraní API z interní mikroslužeb plus autorizace provádí publikovaných rozhraní API v této jedné úrovni.

Pomocí API Management systému nápovědy k dispozici statistiky získat představu o tom, jak jsou používány vaše rozhraní API a jak jsou provádění. Je to tak, že umožňují zobrazit téměř sestavy analýzy v reálném čase a identifikaci trendů, které může mít vliv na vaši firmu. Plus může mít protokoly o žádosti a odpovědi aktivity pro další analýzu online a offline.

S Azure API Management můžete zabezpečit vaše rozhraní API pomocí klíče, token a filtrování protokolu IP. Tyto funkce umožňují vynutit flexibilní a podrobných kvóty a omezení přenosové rychlosti, upravit tvar a chování vaše rozhraní API pomocí zásad a zlepšují výkon při ukládání odpovědí do mezipaměti.

V této příručce a referenční dokumentace ukázkovou aplikaci (eShopOnContainers) jsme jsou omezení architekturu pro jednodušší a vlastní kontejnerizované architektura s cílem zaměřit na prostý kontejnery bez použití PaaS produkty, jako je Azure API Management. Ale pro velké aplikace na základě mikroslužbu, které jsou nasazeny do Microsoft Azure, doporučujeme, abyste ke kontrole a přijmout službu Azure API Management jako základ pro vaše rozhraní API brány.

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Nevýhody vzoru Brána rozhraní API

-   Nejdůležitější nevýhodou je, že při implementaci bránu rozhraní API jsou spojovacích této vrstvě s interní mikroslužeb. Párování jako to může způsobit vážné problémy pro aplikaci. Vaster od Clemense architekti na tým Azure Service Bus, odkazuje na tato potenciální potíže jako "nové ESB" v svůj "[zasílání zpráv a Mikroslužeb](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" relace v GOTO 2016.

-   Brána rozhraní API mikroslužeb pomocí vytvoří další možné jediný bod selhání.

-   Bránu rozhraní API můžete zavést prodloužení doby odezvy z důvodu další síťové volání. Toto volání navíc má však obvykle menší dopad, než by byl klient rozhraní, která je příliš chatty přímo volání interní mikroslužeb.

-   Pokud není škálovat na více systémů správně, bránou rozhraní API se může stát úzkým místem.

-   Bránu rozhraní API vyžaduje další vývoj náklady a budoucí údržby, pokud obsahuje vlastní logiky a agregace dat. Vývojáři musí aktualizovat bránou rozhraní API tak, aby získal každý mikroslužbu koncové body. Implementace změny v interní mikroslužeb kromě toho může způsobit změny kódu na úrovni Brána rozhraní API. Ale pokud brána rozhraní API právě aplikuje zabezpečení, protokolování a správa verzí (stejně jako při použití Azure API Management), nemusí tato náklady na vývoj pro další použití.

-   Pokud brána rozhraní API je vyvinuté jeden tým, může být úzkým místem vývoj. To je další důvod, proč je vhodnější je několik pokutu podrobných API brány, které reagují na požadavky jiného klienta. Brána rozhraní API může také oddělit interně do několika oblastem nebo vrstvy, které jsou vlastněny různé týmy pracující na interní mikroslužeb.

## <a name="additional-resources"></a>Další zdroje

-   **Charlese Ryšánková. Vzor: Brána rozhraní API / back-end pro front-endu**
    [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

-   **Azure API Management**
    [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

-   **Udi Dahan. Služba zaměřené na konkrétní složení**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

-   **Od Clemense Vasters. Zasílání zpráv a Mikroslužeb v GOTO 2016** (video) [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)


>[!div class="step-by-step"]
[Předchozí] (identify-microservice-domain-model-boundaries.md) [Další] (communication-in-microservice-architecture.md)
