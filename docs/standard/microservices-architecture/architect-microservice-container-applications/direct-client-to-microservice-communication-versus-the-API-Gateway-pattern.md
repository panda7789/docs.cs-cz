---
title: Vzor brány rozhraní API a přímá komunikace klienta mikroslužeb
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Vzor brány rozhraní API a přímá komunikace klienta mikroslužeb
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/07/2018
ms.openlocfilehash: f820b0ed866c539beda641164ef42631263490d3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739679"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Vzor brány rozhraní API a přímá komunikace klienta mikroslužeb

V architektuře mikroslužeb každá mikroslužba zveřejňuje sadu koncových bodů (obvykle) fine‑grained. Tato skutečnost může mít vliv client‑to‑microservice komunikaci, jak je popsáno v této části.

## <a name="direct-client-to-microservice-communication"></a>Přímá komunikace klienta mikroslužeb

Možných způsobů je použít architekturu přímá komunikace klienta mikroslužeb. V takovém případě klientskou aplikaci mohli požadavků přímo na některé z mikroslužeb, jak ukazuje obrázek 4-12.

![Diagram znázorňující architekturu přímá komunikace klienta mikroslužeb](./media/image12.png)

**Obrázek 4-12**. Použití architektury přímá komunikace klienta mikroslužeb

V takovém případě jednotlivých mikroslužeb má veřejný koncový bod, někdy s jiným portem TCP u jednotlivých mikroslužeb. Příkladem adresy URL pro konkrétní službu, může být následující adresy URL v Azure:

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

V produkčním prostředí založené na clusteru, která umožní mapování adresy URL pro vyrovnávání zatížení používá v clusteru, který pak distribuuje požadavky mezi mikroslužby. V produkčním prostředí můžete mít Application Delivery Controller (ADC) jako [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) mezi mikroslužby a Internetem. To slouží jako transparentní vrstvy, který nejen provede Vyrovnávání zatížení, ale chrání služby tím, že nabízí ukončení protokolu SSL. To zvyšuje zatížení hostitelů přesměrováním ukončení protokolu SSL náročnou na procesor a další směrování úkoly ke službě Azure Application Gateway. V každém případě jsou transparentní z hlediska of Architektura logické aplikační nástroje pro vyrovnávání zatížení a ADC.

Přímá komunikace klienta mikroslužeb architektury může být dostatečné pro malou aplikaci založených na mikroslužbách, zejména v případě, že je klientská aplikace na straně serveru webové aplikace, jako jsou aplikace ASP.NET MVC. Při sestavování velkých a složitých aplikací využívajících mikroslužby (například při zpracování desítek mikroslužeb typy) a zejména v případě klientských aplikací jsou vzdálené mobilní aplikace nebo webové aplikace SPA čelí tento přístup však několik problémů.

Při vývoji rozsáhlé aplikace založené na mikroslužbách, zvažte následující otázky:

- *Jak klientské aplikace minimalizovat počet požadavků na back-end a snížit košatá komunikace na více mikroslužby?*

Interakce s různými mikroslužbami k sestavení na jedné obrazovce uživatelského rozhraní se zvyšuje počet zpátečních cest přes Internet. Tím se zvyšuje latenci a složitostí na straně uživatelského rozhraní. V ideálním případě odpovědí efektivně agregace na straně serveru. Tím se snižuje latence, protože více kusů data vrátit paralelně a některé uživatelského rozhraní můžete zobrazit data, jakmile to bude připravené.

- *Jak můžete zpracovávat vyskytující aspekty, jako je například autorizace, transformace dat a odesílání dynamické požadavku?*

Implementace zabezpečení a převeďte společné aspekty, jako je zabezpečení a autorizace v každé mikroslužbě může vyžadovat významné vývoj úsilí. Možných způsobů je, aby tyto služby v rámci hostitele Docker nebo interní clusteru a omezit přímý přístup k nim z vnějšku těchto vyskytující aspekty implementace v centrálním umístění, jako jsou brány rozhraní API.

- *Jak může klientské aplikace komunikovat se službou, které používají protokoly sítě Internet vhodných?*

Klientské aplikace obvykle nepodporuje protokoly použité na straně serveru (jako je připojení přes AMQP nebo binární protokoly). Proto musí být žádostí provádí prostřednictvím protokolů, jako jsou HTTP/HTTPS a poté převedeny na jiné protokoly. A *man-in-the-middle* přístup může pomoct v této situaci.

- *Jak můžete tvarovat průčelí zejména vytvořené pro mobilní aplikace?*

Rozhraní API z několika mikroslužeb nemusí být dobře navržený pro potřeby různých klientských aplikací. Požadavky na mobilní aplikaci, může být jiný než potřebám webové aplikace. Pro mobilní aplikace může být nutné ještě více optimalizovat tak, aby data odpovědi může být efektivnější. Může to provedete tak, že agregace dat z několika mikroslužeb a vrací jednu sadu dat a někdy odstraněním všech dat v odpovědi, která není potřeba pro mobilní aplikace. A samozřejmě, může tato data komprimovat. Opět "fasády" nebo rozhraní API mezi mikroslužby a mobilní aplikace může být vhodné pro tento scénář.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Proč místo přímé komunikace klienta mikroslužeb zvažte brány rozhraní API

V architektuře mikroslužeb klientské aplikace obvykle potřebují využívat funkce z více než jeden mikroslužeb. Pokud se tento spotřeby provádí přímo, klient musí zpracovat více volání koncových bodů mikroslužeb. Co se stane, když se aplikace vyvíjí a vydávají nové mikroslužby nebo aktualizaci existující mikroslužeb? Pokud má vaše aplikace mnoha mikroslužeb, může být zpracování tolika koncových bodů z klientských aplikací připomínající. Vzhledem k tomu, že klientská aplikace by spjat s těchto vnitřních koncových bodů, vyvíjejí mikroslužby v budoucnu může způsobit vysoký dopad pro klientské aplikace.

Proto úrovní dereference (brány) nebo pokročilou úroveň může být velmi vhodné pro aplikace založené na mikroslužbách. Pokud nemáte brány rozhraní API, klientské aplikace musíte odeslat požadavků přímo na mikroslužby a, která vyvolává problémy, jako je například následující problémy:

- **Párování**: bez vzor brány rozhraní API, klientské aplikace jsou spojeny s interní mikroslužeb. Klientské aplikace potřebujete vědět, jak se více oblastí aplikace rozloží v mikroslužeb. Když se vyvíjejí a refaktoring interní mikroslužeb, tyto akce vliv údržby to je chybně protože mohou způsobit změny způsobující chyby do klientské aplikace z důvodu přímý odkaz na vnitřní mikroslužeb z klienta aplikace. Klientské aplikace potřeba aktualizovat často, což obtížnější vyvíjí řešení.

- **Moc velký počet zpátečních cest**: jednu stránku, obrazovky v klientské aplikaci může vyžadovat několik volání více služeb. Že výsledkem více síťových zaokrouhlit zkracuje dobu odezvy mezi klientem a serverem, přidání velkou latenci. Agregace v pokročilou úroveň zpracovává může zlepšit výkon a uživatelské prostředí pro klientské aplikace.

- **Problémy se zabezpečením**: bez brány, musí být vystavené všechny mikroslužby "externí World", aby útok větší než-li skrýt interní mikroslužby použité přímo pomocí klientských aplikací. Čím menší je útok, tím lépe zabezpečit vaše aplikace může být.

- **Převeďte společné aspekty**: každá mikroslužba veřejně publikovaného musí zpracovat aspekty jako je například autorizace, SSL atd. V mnoha situacích můžou tyto obavy zpracovat, v jedné vrstvě tak vnitřní mikroslužeb jsou zjednodušené.

## <a name="what-is-the-api-gateway-pattern"></a>Co je vzor brány rozhraní API?

Při navrhování a vytváření rozsáhlých nebo složitých aplikací využívajících mikroslužby s více klientských aplikací, může být dobrý nápad vzít v úvahu [Brána rozhraní API](https://microservices.io/patterns/apigateway.html). Jedná se o službu, která poskytuje jeden vstupní bod pro určité skupiny mikroslužeb. Se podobá [Facade vzor](https://en.wikipedia.org/wiki/Facade_pattern) z object‑oriented návrhu, ale v tomto případě to je součástí distribuovaného systému.
Vzor brány rozhraní API se také někdy označuje jako "back-endu pro front-endu" [(BFF)](https://samnewman.io/patterns/architectural/bff/) protože sestavení při přemýšlení o potřebách klientské aplikace.

Brána rozhraní API proto umístěná mezi klientské aplikace a mikroslužeb. Slouží jako reverzní proxy server, směrování požadavků od klientů ke službám. Může také nabízet další společné funkce, jako je například ověřování, ukončování protokolu SSL a mezipaměti.

Obrázek 4 – 13 ukazuje, jak je vlastní bránu rozhraní API můžete začlenit do zjednodušení architektury založené na mikroslužbách s několika mikroslužeb.

![Diagram znázorňující, že brány rozhraní API implementované jako vlastní službu](./media/image13.png)

**Obrázek 4 – 13**. Použití brány rozhraní API implementované jako vlastní službu

V tomto příkladu by se Brána rozhraní API implementované jako vlastní služby hostitele ASP.NET Core spuštěné jako kontejner.

Je důležité, abyste měli na očích, který v tomto diagramu, budete používat jeden vlastní bránu rozhraní API služby směřující více a různých klientských aplikací. Fakt může být důležité riziko, protože vaše Brána rozhraní API služeb se rozrůstá a vyvíjejí podle mnoha různých požadavků z klientských aplikací. Nakonec bude opakovaném kvůli tyto různé potřeby a efektivní může být poměrně podobný monolitické aplikace nebo monolitické služby. To je důvod, proč velmi dobře se doporučuje Brána rozhraní API ve více službách nebo několik menších brány rozhraní API, jeden pro každý typ uspořádání formuláře aplikace klienta, například rozdělit.

Musíte být opatrní při implementaci vzor brány rozhraní API. Obvykle není vhodné mít jediné brány rozhraní API agregaci všechny mikroslužby interní vaší aplikace. Pokud ano, funguje jako monolitický agregátoru nebo nástroje orchestrator a porušuje autonomie mikroslužeb pomocí párování všechny mikroslužby.

Proto brány rozhraní API by měly být oddělené na základě obchodní hranice a klientské aplikace a ne act jako jeden agregátor interní mikroslužeb.

Při rozdělování úroveň rozhraní API brány do více bran rozhraní API, pokud aplikace obsahuje víc klientských aplikací, které mohou být primární kontingenční tabulku při identifikaci více typů brány rozhraní API, takže můžete mít různé fasáda pro potřeby každou klientskou aplikaci. Tento případ je vzor s názvem "Back-endu pro front-endu" ([BFF](http://samnewman.io/patterns/architectural/bff/)) tam, kde každá brána rozhraní API můžete zadat jiné rozhraní API navržených pro jednotlivé typy aplikací klienta, případně i na základě provedení klientských implementací konkrétní adaptér kódu, které pod tím volá více interní mikroslužeb, jak je znázorněno na následujícím obrázku:

![Diagram znázorňující několik vlastních rozhraní API brány](./media/image13.1.png)

**Obrázek 4 – 13.1**. Použití více bran vlastní rozhraní API

Předchozí obrázek znázorňuje zjednodušenou architektury s využitím více podrobných brány rozhraní API. V tomto případě jsou hranice pro každou bránu rozhraní API založené výhradně na "Back-endu pro front-endu" ([BFF](http://samnewman.io/patterns/architectural/bff/)) vzor, proto založený na rozhraní API pro potřeby za klientské aplikace. Ale ve větších aplikací by měl také dále a vytvořit další brány rozhraní API založené na obchodní hranice jako druhý návrh kontingenční tabulku.

## <a name="main-features-in-the-api-gateway-pattern"></a>Hlavní funkce v vzor brány rozhraní API

Brány rozhraní API nabízí více funkcí. V závislosti na produktu mohou nabízet lepší nebo jednodušší funkce, ale nejdůležitější a základní funkce pro každou bránu, rozhraní API jsou následující vzory návrhu:

**Reverzní proxy server nebo směrování prostřednictvím brány**. Brána rozhraní API nabízí reverzní proxy k přesměrování nebo směrovat požadavky (směrování vrstvy 7, obvykle požadavků HTTP) ke koncovým bodům interní mikroslužeb. Brána poskytuje jeden koncový bod nebo URL klienta aplikace a interně mapuje požadavky na skupinu interní mikroslužeb. Tato funkce směrování pomáhá oddělit klientské aplikace z mikroslužeb, ale je také poměrně vhodné při modernizaci monolitické rozhraní API podle sedí mezi monolitické rozhraní API a klientské aplikace pak můžete bránu rozhraní API můžete přidat nové rozhraní API jako nové mikroslužby nadále pomocí starší verze rozhraní API monolitické, dokud se rozdělí na mnoha mikroslužeb v budoucnu. Z důvodu brány rozhraní API klientské aplikace nebude Všimněte si, že pokud rozhraní API používá jsou implementovány jako interní mikroslužby nebo monolitické rozhraní API a důležitější je, když vyvíjí a refaktoring monolitické rozhraní API do mikroslužeb, a díky směrování brány rozhraní API , klientské aplikace nebude mít vliv změny identifikátoru URI.

Další informace najdete v tématu [model směrování prostřednictvím brány](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Agregace požadavků**. Jako součást vzorku bránu můžete shromažďovat více požadavky klientů (obvykle požadavků HTTP) na jeden požadavek klienta cílení na více interní mikroslužeb. Tento model je zvlášť vhodné, pokud stránka/obrazovky klienta potřebuje informace z několika mikroslužeb. S tímto přístupem klientská aplikace odesílá jeden požadavek na bránu rozhraní API, která odešle několik interní mikroslužeb a pak agreguje výsledky a všechno, co odešle zpět do klientské aplikace. Hlavní výhodou a cílem tohoto vzoru návrhu je ke snížení nadměrné komunikace mezi back-end rozhraní API a klientské aplikace, který je obzvláště důležité pro vzdálené aplikace mimo datové centrum, kde mikroslužby za provozu, jako jsou mobilní aplikace nebo požadavky přicházející z aplikace SPA, který pocházejí z jazyka Javascript v prohlížečích klienta vzdálené. Tento model pro běžné webové aplikace provádění požadavků v serverovém prostředí (například webovou aplikaci ASP.NET Core MVC), není tak důležitý, protože latence je velmi mnohem menší, než klient služby Vzdálená aplikace.

V závislosti na bránu rozhraní API produktu, který používáte může být schopen provést tato agregace. V mnoha případech je ale flexibilnější vytváření mikroslužeb agregace v rozsahu bránu rozhraní API, takže definovat agregace v kódu (to znamená, že kód jazyka C#).

Další informace najdete v tématu [model agregace pomocí brány](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Převeďte společné aspekty nebo snižování zátěže pomocí brány**. V závislosti na funkcí, které nabízí jednotlivé produkty Brána rozhraní API může převzít funkci z jednotlivých mikroslužeb pro bránu, která zjednodušuje implementace jednotlivých mikroslužeb tím, že sloučení vyskytující aspekty do jedné vrstvy. To je zvlášť vhodné pro specializované funkce, které můžou být složité implementovat správně v každé vnitřní mikroslužeb, jako jsou následující funkce:

- Ověřování a autorizace
- Integrace služby zjišťování
- Ukládání odpovědí do mezipaměti
- Opakování zásady, jističe a QoS
- Omezení rychlosti a omezování
- Vyrovnávání zatížení
- Protokolování trasování, korelace
- Záhlaví, řetězce dotazu a transformace deklarací identity
- Přidávání na seznam povolených IP

Další informace najdete v tématu [brány snižování zátěže vzor](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Používání produktů s funkcí brány rozhraní API

Může existovat mnoho další vyskytující aspekty nabízených produktů brány rozhraní API v závislosti na každé provedení. Například [Azure API Management](https://azure.microsoft.com/services/api-management/) (jak je znázorněno v obrázek 4 – 14) nejen řeší potřeby Brána rozhraní API, ale poskytuje funkce, jako je shromažďování přehledů z rozhraní API. Pokud používáte vytváří řešení pro správu rozhraní API, brány rozhraní API je pouze v rámci této kompletnímu řešení správy rozhraní API.

![Diagram znázorňující Brána rozhraní API s architekturou Azure API management](./media/image14.png)

**Obrázek 4 – 14**. Pomocí Azure API Management pro vaši bránu rozhraní API

V takovém případě při použití produktů, jako je Azure API Management, skutečnost, že může mít jednu bránu rozhraní API není tak rizikové, protože tyto druhy brány rozhraní API se "tenčí", což znamená, že nemusíte implementovat vlastní kód jazyka C#, který by mohl vyvíjet monolitické komponenta.

Brána rozhraní API produktů obvykle fungují jako reverzní proxy server pro příchozí komunikaci, kde můžete taky filtrovat rozhraní API z interní mikroslužeb získat autorizace publikovaných rozhraní API na této úrovni jednoho.

Insights, která je dostupná z nápovědy API Management systému pomůžou pochopit, jak se používají vaše rozhraní API a jaký je výkon. Je to tak, že umožňuje zobrazit téměř v reálném čase analytické sestavy a identifikace trendů, které může mít vliv na vaši firmu. Navíc můžete mít protokolů o činnosti žádostí a odpovědí pro další online i offline analýzu.

S Azure API Management můžete zabezpečit vaše rozhraní API pomocí klíče, tokenu a filtrování protokolu IP. Tyto funkce umožňují vynucovat flexibilní a podrobné kvóty a omezení přenosové rychlosti, upravujte podobu a chování rozhraní API pomocí zásad a zlepšit výkon díky mezipaměti odpovědí.

V této příručce a odkaz na ukázkovou aplikaci (aplikaci eShopOnContainers) architektura je omezená na kontejnerizovaných architektura jednodušší a vlastních abychom se mohli zaměřit na prostý kontejnerů bez použití produktů PaaS, jako je Azure API Management. Ale pro velké aplikace založené na mikroslužbách, které jsou nasazené do Microsoft Azure, doporučujeme vyhodnotit Azure API Management jako základ pro vaše brány rozhraní API v produkčním prostředí.

**Ocelot.** Pro jednodušší přístupy lehké brány rozhraní API jako Ocelot se doporučuje. [Ocelot](https://github.com/ThreeMammals/Ocelot) je open source brány rozhraní API pomocí .NET Core zejména vytvořené pro architekturu mikroslužeb, potřebujete jednotné body vstupu v jejich systému. Je jednoduchý, rychlý, škálovatelný a poskytuje směrování a ověřování mezi mnoho dalších funkcí.

Hlavním důvodem, proč Ocelot použila [aplikaci eShopOnContainers odkazovat aplikace](https://github.com/dotnet-architecture/eShopOnContainers) totiž Ocelot je .NET Core zjednodušené rozhraní API brány, kterou můžete nasadit ve stejném prostředí nasazení aplikace, pokud nasazujete mikroslužby a kontejnery, například hostitele Docker, Kubernetes, Service Fabric, atd. A protože je založen na .NET Core, je multiplatformní můžete nasadit v systému Linux nebo Windows.

Předchozí diagramy zobrazující vlastní rozhraní API brány spouštěných v kontejnerech jsou přesně, jak můžete také spustit Ocelot v kontejneru a aplikací založených na mikroslužbách.

Kromě toho na trhu nabídky funkce brány rozhraní API, jako je například Apigee, Hongkongu, MuleSoft, WSO2, existuje mnoho dalších produktů a funkcí kontroleru příchozího přenosu dat sítě produkty, jako jsou Linkerd a Istio pro službu.

Po počáteční architektury a vysvětlení části vzorce, následující části popisují, jak implementovat brány rozhraní API s [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Nevýhody vzor brány rozhraní API

- Nejdůležitější nevýhodou je, že při implementaci bránu rozhraní API už párování tuto úroveň s využitím interní mikroslužeb. Párování tímto způsobem může způsobit obtížemi pro vaši aplikaci. Vaster Clemense Návrhář v týmu Azure Service Bus, odkazuje na tento potenciální problémy s dokončením jako "nové ESB" v "[zasílání zpráv a Mikroslužby](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" přednášky z konference GOTO 2016.

- Použití brány rozhraní API mikroslužeb vytvoří další možné jediný bod selhání.

- Brány rozhraní API můžete zavést prodloužení doby odezvy z důvodu další síťová volání. Toto dodatečné volání má však obvykle menší dopad, než klient rozhraní, která je příliš přetížení přímého volání vnitřní mikroslužeb.

- Pokud ne horizontálně navýší, brána rozhraní API se může stát kritickým bodem.

- Pokud obsahuje vlastní logiku a agregace dat vyžaduje náklady na další vývoj a údržbu na budoucí bránu rozhraní API. Vývojáři musí aktualizovat bránu rozhraní API, aby zpřístupňují koncové body jednotlivých mikroslužeb. Kromě toho provádění změn v interní mikroslužeb může způsobit změny kódu na úrovni rozhraní API brány. Ale pokud brána rozhraní API je pouze použití zabezpečení, protokolování a správa verzí (stejně jako při použití služby Azure API Management), nemusí platit náklady na tento další vývoj.

- Pokud brána rozhraní API je vyvinutý jeden tým, může být kritickým bodem vývoje. To je další důvod, proč lepším řešením je, aby několik pokutu grained brány rozhraní API, které reagují na požadavky jiného klienta. Brána rozhraní API byste mohli izolovat také interně do více oblastí nebo vrstvy, které jsou majetkem společnosti různé týmy pracující na interní mikroslužeb.

## <a name="additional-resources"></a>Další zdroje

- **Charles Richardson. Vzor: Brána rozhraní API / back-endu pro front-endu** [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

- **Vzor brány rozhraní API** [*https://docs.microsoft.com/azure/architecture/microservices/gateway*](https://docs.microsoft.com/azure/architecture/microservices/gateway)

- **Agregace a skládání modelu** [*http://microservices.io/patterns/data/api-composition.html*](http://microservices.io/patterns/data/api-composition.html)

- **Azure API Management** [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

- **Udi Dahan. Složení orientované na služby**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

- **Clemense Vasterse. Zasílání zpráv a Mikroslužby na GOTO 2016** (video)   [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)

>[!div class="step-by-step"]
[Předchozí](identify-microservice-domain-model-boundaries.md)
[další](communication-in-microservice-architecture.md)
