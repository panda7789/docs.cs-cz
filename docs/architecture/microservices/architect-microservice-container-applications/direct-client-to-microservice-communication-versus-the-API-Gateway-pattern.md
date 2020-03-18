---
title: Vzor brány rozhraní API versus přímá komunikace mezi klientem a mikroslužbou
description: Pochopit rozdíly a použití vzoru brány rozhraní API a přímé komunikace klienta mikroslužeb.
ms.date: 01/07/2019
ms.openlocfilehash: 47e9a383c1fcb6c9fec38cb376b60a4ab839077d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401723"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Vzor brány rozhraní API versus přímá komunikace mezi klientem a mikroslužbou

V architektuře mikroslužeb každá mikroslužba zveřejňuje sadu (obvykle) jemně odstupňované koncové body. Tato skutečnost může mít vliv na komunikaci mezi klientem a mikroslužbou, jak je vysvětleno v této části.

## <a name="direct-client-to-microservice-communication"></a>Přímá komunikace mezi klientem a mikroslužbami

Možný přístup je použití architektury přímé komunikace mezi klientem a mikroslužbami. V tomto přístupu klientská aplikace můžete provádět požadavky přímo na některé mikroslužeb, jak je znázorněno na obrázku 4-12.

![Diagram znázorňující architekturu komunikace mezi klientem a mikroslužbami.](./media/direct-client-to-microservice-communication.png)

**Obrázek 4-12**. Použití architektury přímé komunikace mezi klientem a mikroslužbami

V tomto přístupu má každá mikroslužba veřejný koncový bod, někdy s jiným portem TCP pro každou mikroslužbu. Příkladem adresy URL pro konkrétní službu může být následující adresa URL v Azure:

`http://eshoponcontainers.westus.cloudapp.azure.com:88/`

V produkčním prostředí založeném na clusteru by tato adresa URL mapovala na nástroje pro vyrovnávání zatížení používaný v clusteru, který zase distribuuje požadavky mezi mikroslužeb. V produkčním prostředí můžete mít řadič pro doručování aplikací (ADC), jako je [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) mezi mikroslužbami a Internetem. To funguje jako transparentní vrstva, která nejen provádí vyrovnávání zatížení, ale zabezpečuje vaše služby tím, že nabízí ukončení SSL. To zlepšuje zatížení vašich hostitelů tím, že přečítáte ukončení SSL náročné na procesor a další povinnosti směrování do brány aplikace Azure. V každém případě je z hlediska architektury logické aplikace transparentní správce zatížení a ADC.

Architektura přímé komunikace mezi klientem a mikroslužbami může být dost dobrá pro malou aplikaci založenou na mikroslužbách, zejména pokud je klientská aplikace webovou aplikací na straně serveru, jako je ASP.NET aplikace MVC. Však při vytváření velkých a složitých aplikací založených na mikroslužbách (například při zpracování desítky typů mikroslužeb), a zejména v případě, že klientské aplikace jsou vzdálené mobilní aplikace nebo SPA webové aplikace, tento přístup čelí několik problémů.

Při vývoji velké aplikace založené na mikroslužbách zvažte následující otázky:

- *Jak mohou klientské aplikace minimalizovat počet požadavků na back-end a snížit upovídanou komunikaci s více mikroslužbami?*

Interakce s více mikroslužeb k vytvoření jedné obrazovky ui zvyšuje počet zpátečních cest přes Internet. To zvyšuje latenci a složitost na straně ui. V ideálním případě by odpovědi měly být efektivně agregovány na straně serveru. To snižuje latenci, protože více kusů dat vrátit paralelně a některé uI můžete zobrazit data, jakmile je připraven.

- *Jak můžete zpracovat průřezové problémy, jako je autorizace, transformace dat a dynamické odesílání požadavků?*

Implementace zabezpečení a průřezové obavy, jako je zabezpečení a autorizace na každé mikroslužby může vyžadovat značné úsilí vývoje. Možným přístupem je mít tyto služby v rámci hostitele Dockeru nebo interní cluster omezit přímý přístup k nim zvenčí a implementovat tyto průřezové obavy v centralizovaném místě, jako je brána rozhraní API.

- *Jak mohou klientské aplikace komunikovat se službami, které používají protokoly, které nejsou vhodné pro internet?*

Protokoly používané na straně serveru (například AMQP nebo binární protokoly) obvykle nejsou v klientských aplikacích podporovány. Proto požadavky musí být provedeny prostřednictvím protokolů, jako je HTTP/HTTPS a překládat do jiných protokolů později. *Man-in-the-middle* přístup může pomoci v této situaci.

- *Jak můžete utvářet fasádu speciálně vyrobenou pro mobilní aplikace?*

Rozhraní API více mikroslužeb nemusí být dobře navrženy pro potřeby různých klientských aplikací. Například potřeby mobilní aplikace se mohou lišit od potřeb webové aplikace. Pro mobilní aplikace může být nutné optimalizovat ještě dále, aby odpovědi na data mohly být efektivnější. Můžete to provést agregací dat z více mikroslužeb a vrácením jedné sady dat a někdy odstraněním všech dat v odpovědi, která mobilní aplikace nepotřebuje. A samozřejmě, můžete komprimovat tato data. Opět platí, že fasáda nebo rozhraní API mezi mobilní aplikace a mikroslužeb může být vhodné pro tento scénář.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Proč zvážit brány rozhraní API namísto přímé komunikace mezi klientem a mikroslužbami

V architektuře mikroslužeb klientské aplikace obvykle potřebují využívat funkce z více než jedné mikroslužby. Pokud se tato spotřeba provádí přímo, klient potřebuje zpracovat více volání koncových bodů mikroslužeb. Co se stane, když se aplikace vyvíjí a jsou zavedeny nové mikroslužby nebo jsou aktualizovány stávající mikroslužby? Pokud vaše aplikace má mnoho mikroslužeb, zpracování tolik koncových bodů z klientských aplikací může být noční můra. Vzhledem k tomu, že klientská aplikace by být spojeny s těmito interníkoncové body, vyvíjející se mikroslužeb v budoucnu může způsobit velký dopad na klientské aplikace.

Proto s mezilehlou úroveň nebo úroveň dereference (Gateway) může být velmi vhodné pro aplikace založené na mikroslužbách. Pokud nemáte brány rozhraní API, klientské aplikace musí odesílat požadavky přímo mikroslužbám a to vyvolává problémy, jako jsou následující problémy:

- **Párování**: Bez vzoru brány rozhraní API jsou klientské aplikace spojeny s interními mikroslužbami. Klientské aplikace potřebují vědět, jak se v mikroslužbách rozloží více oblastí aplikace. Při vývoji a refaktoring interní mikroslužeb, tyto akce dopad údržby docela špatně, protože způsobují narušující změny klientských aplikací z důvodu přímý odkaz na interní mikroslužeb z klientských aplikací. Klientské aplikace je třeba často aktualizovat, což ztěžuje vývoj řešení.

- **Příliš mnoho zpátečních cest**: Jedna stránka nebo obrazovka v klientské aplikaci může vyžadovat několik volání více služeb. To může mít za následek více síťových zpátečních cest mezi klientem a serverem, přidání významné latence. Agregace zpracovat v mezilehlé úrovni může zlepšit výkon a uživatelské prostředí pro klientskou aplikaci.

- **Problémy se zabezpečením**: Bez brány všechny mikroslužby musí být vystaveny "externí svět", takže prostor pro útok větší, než pokud skrýt interní mikroslužeb, které nejsou přímo používány klientské aplikace. Čím menší je povrch útoku, tím bezpečnější může být vaše aplikace.

- **Průřezové obavy**: Každá veřejně publikovaná mikroslužba musí řešit obavy, jako je autorizace, SSL atd. V mnoha situacích tyto obavy by mohly být zpracovány v jedné vrstvě, takže vnitřní mikroslužby jsou zjednodušeny.

## <a name="what-is-the-api-gateway-pattern"></a>Co je vzor brány rozhraní API?

Při navrhování a vytváření velkých nebo složitých aplikací založených na mikroslužbách s více klientskými aplikacemi může být dobrým přístupem, který je třeba zvážit, [brána rozhraní API](https://microservices.io/patterns/apigateway.html). Toto je služba, která poskytuje jeden vstupní bod pro určité skupiny mikroslužeb. Je to podobné [vzoru Fasáda](https://en.wikipedia.org/wiki/Facade_pattern) z objektově orientovaného designu, ale v tomto případě je součástí distribuovaného systému. Vzor brány rozhraní API je také někdy známý jako "back-end pro frontend" ([BFF](https://samnewman.io/patterns/architectural/bff/)), protože jej vytvoříte při přemýšlení o potřebách klientské aplikace.

Proto brána rozhraní API je mezi klientské aplikace a mikroslužeb. Funguje jako reverzní proxy server, směrování požadavků od klientů ke službám. Může také poskytovat další průřezové funkce, jako je ověřování, ukončení Protokolu SSL a mezipaměti.

Obrázek 4-13 ukazuje, jak se vlastní brána rozhraní API vejde do zjednodušené architektury založené na mikroslužbách s několika mikroslužbami.

![Diagram znázorňující bránu rozhraní API implementovanou jako vlastní službu.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/custom-service-api-gateway.png)

**Obrázek 4-13**. Použití brány rozhraní API implementované jako vlastní služby

Aplikace se připojují k jedinému koncovému bodu, bráně rozhraní API, která je nakonfigurovaná tak, aby přesměrovala požadavky na jednotlivé mikroslužby. V tomto příkladu brána rozhraní API by být implementována jako vlastní ASP.NET služby Core WebHost běží jako kontejner.

Je důležité zdůraznit, že v tomto diagramu byste používali jednu vlastní službu brány rozhraní API, která čelí více a různým klientským aplikacím. Tato skutečnost může být důležitým rizikem, protože vaše služba brány rozhraní API bude růst a vyvíjet se na základě mnoha různých požadavků z klientských aplikací. Nakonec, to bude nafouklý, protože tyto různé potřeby a efektivně by to mohlo být docela podobné monolitické aplikace nebo monolitické služby. That's why it's very much recommended to split the API Gateway in multiple services or multiple smaller API Gateways, one per client app form-factor type, for instance.

Při implementaci vzoru brány rozhraní API musíte být opatrní. Obvykle není vhodné mít jednu bránu rozhraní API agregovat všechny interní mikroslužeb vaší aplikace. Pokud ano, funguje jako monolitický agregátor nebo orchestrator a porušuje autonomii mikroslužeb propojením všech mikroslužeb.

Brány rozhraní API by proto měly být odděleny na základě obchodních hranic a klientských aplikací a neměly by fungovat jako jeden agregátor pro všechny interní mikroslužby.

Při rozdělení úrovně brány rozhraní API do více bran rozhraní API, pokud vaše aplikace má více klientských aplikací, které může být primární pivot při identifikaci více typů brány rozhraní API, takže můžete mít jinou fasádu pro potřeby každé klientské aplikace. Tento případ je vzor s názvem "Backend pro front-end" ([BFF),](https://samnewman.io/patterns/architectural/bff/)kde každá brána rozhraní API může poskytnout jiné rozhraní API přizpůsobené pro každý typ klientské aplikace, případně i na základě faktoru tvaru klienta implementací konkrétního kódu adaptéru, který pod voláním více interních mikroslužeb, jak je znázorněno na následujícím obrázku:

![Diagram znázorňující více vlastních bran rozhraní API.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/multiple-custom-api-gateways.png)

**Obrázek 4-13.1**. Použití více vlastních bran rozhraní API

Obrázek 4-13.1 znázorňuje brány rozhraní API, které jsou odděleny podle typu klienta; jeden pro mobilní klienty a jeden pro webové klienty. Tradiční webová aplikace se připojuje k mikroslužbě MVC, která používá webovou bránu rozhraní API. Příklad znázorňuje zjednodušenou architekturu s více jemně odstupňovanými bránami rozhraní API. V tomto případě jsou hranice identifikované pro každou bránu rozhraní API založeny čistě na vzoru "Backend for Frontend" ([BFF),](https://samnewman.io/patterns/architectural/bff/)tedy pouze na základě rozhraní API potřebného pro klientskou aplikaci. Ale ve větších aplikacích byste měli také jít dál a vytvořit další brány rozhraní API založené na obchodních hranicích jako druhý pivot návrhu.

## <a name="main-features-in-the-api-gateway-pattern"></a>Hlavní funkce ve vzoru brány rozhraní API

Brána rozhraní API může nabízet více funkcí. V závislosti na produktu může nabízet bohatší nebo jednodušší funkce, ale nejdůležitější a základní funkce pro všechny brány rozhraní API jsou následující návrhové vzory:

**Reverzní směrování proxy nebo brány.** Brána rozhraní API nabízí reverzní proxy pro přesměrování nebo směrování požadavků (směrování vrstvy 7, obvykle požadavky HTTP) do koncových bodů interních mikroslužeb. Brána poskytuje jeden koncový bod nebo adresu URL pro klientské aplikace a pak interně mapuje požadavky na skupinu interních mikroslužeb. Tato funkce směrování pomáhá oddělit klientské aplikace od mikroslužeb, ale je také velmi pohodlné při modernizaci monolitického rozhraní API tím, že sedí bránu rozhraní API mezi monolitické rozhraní API a klientské aplikace, pak můžete přidat nová rozhraní API jako nové mikroslužby při stále používáte starší monolitické rozhraní API, dokud se v budoucnu nerozdělí na mnoho mikroslužeb. Z důvodu brány rozhraní API si klientské aplikace nevšimnou, pokud jsou používaná rozhraní API implementována jako interní mikroslužby nebo monolitické rozhraní API a co je důležitější, při vývoji a refaktorování monolitického rozhraní API do mikroslužeb, a to díky směrování brány rozhraní API , klientské aplikace nebudou ovlivněny žádnou změnou identifikátoru URI.

Další informace naleznete v tématu [Gateway routing pattern](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Požadavky agregace.** Jako součást vzoru brány můžete agregovat více požadavků klientů (obvykle http požadavky) cílení více interních mikroslužeb do jednoho požadavku klienta. Tento vzor je zvláště vhodné, když stránka klienta nebo obrazovka potřebuje informace z několika mikroslužeb. S tímto přístupem klientská aplikace odešle jeden požadavek do brány rozhraní API, která odešle několik požadavků na interní mikroslužeb a pak agreguje výsledky a odešle vše zpět do klientské aplikace. Hlavní výhodou a cílem tohoto návrhového vzoru je snížit chattiness mezi klientskými aplikacemi a rozhraním API back-endu, což je obzvláště důležité pro vzdálené aplikace mimo datové centrum, kde žijí mikroslužby, jako jsou mobilní aplikace nebo požadavky pocházející z aplikací SPA, které pocházejí z Javascriptu v klientských vzdálených prohlížečích. Pro běžné webové aplikace, které provádějí požadavky v prostředí serveru (například ASP.NET webové aplikace Core MVC), není tento vzor tak důležitý, protože latence je mnohem menší než u vzdálených klientských aplikací.

V závislosti na produktu brány rozhraní API, který používáte, může být schopen provést tuto agregaci. V mnoha případech je však flexibilnější vytvořit mikroslužby agregace v rámci oboru brány rozhraní API, takže definujete agregaci v kódu (to znamená kód C#):

Další informace naleznete [v tématu Gateway agregace vzor](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Průřezové obavy nebo vyložení brány.** V závislosti na funkcích nabízených jednotlivými produkty brány rozhraní API můžete převést funkce z jednotlivých mikroslužeb do brány, což zjednodušuje implementaci každé mikroslužby konsolidací průřezových problémů do jedné vrstvy. To je zvláště vhodné pro specializované funkce, které mohou být složité správně implementovat v každé interní mikroslužby, jako jsou následující funkce:

- Ověřování a autorizace
- Integrace zjišťování služeb
- Ukládání odpovědí do mezipaměti
- Zásady opakování, jistič a technologie QoS
- Omezení rychlosti a omezení
- Vyrovnávání zatížení
- Protokolování, trasování, korelace
- Záhlaví, řetězce dotazů a transformace deklarací identity
- Seznam povolených adres IP

Další informace naleznete v [tématu Gateway offloading pattern](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Používání produktů s funkcemi brány rozhraní API

V závislosti na každé implementaci může existovat mnoho dalších průřezových problémů nabízených produkty brány rozhraní API. Prozkoumáme zde:

- [Azure API Management](https://azure.microsoft.com/services/api-management/)
- [Ocelot](https://github.com/ThreeMammals/Ocelot)

### <a name="azure-api-management"></a>Azure API Management

[Azure API Management](https://azure.microsoft.com/services/api-management/) (jak je znázorněno na obrázku 4-14) nejen řeší vaše potřeby brány rozhraní API, ale poskytuje funkce, jako je shromažďování přehledů z vašich rozhraní API. Pokud používáte řešení pro správu rozhraní API, brána rozhraní API je jenom součást v rámci tohoto úplného řešení pro správu rozhraní API.

![Diagram znázorňující, jak používat Azure API Management jako bránu rozhraní API.](./media/direct-client-to-microservice-communication-versus-the-API-Gateway-pattern/api-gateway-azure-api-management.png)

**Obrázek 4-14**. Použití Azure API Management pro bránu rozhraní API

Azure API Management řeší vaše brány rozhraní API a potřeby správy, jako je protokolování, zabezpečení, měření atd. V tomto případě při použití produktu, jako je Správa rozhraní API Azure, skutečnost, že můžete mít jednu bránu rozhraní API není tak riskantní, protože tyto druhy brány rozhraní API jsou "tenčí", což znamená, že neimplementujete vlastní kód Jazyka C#, který by se mohl vyvíjet směrem k monolitické součásti.

Produkty brány rozhraní API obvykle fungují jako reverzní proxy pro příchozí komunikaci, kde můžete také filtrovat rozhraní API z interních mikroslužeb a použít autorizaci na publikovaná rozhraní API v této jedné vrstvě.

Přehledy dostupné ze systému správy rozhraní API vám pomohou pochopit, jak se vaše rozhraní API používají a jak si vedou. Dělají to tím, že vám umožní zobrazit přehledy analýz v reálném čase a identifikovat trendy, které by mohly mít vliv na vaši firmu. Navíc můžete mít protokoly o činnosti požadavků a odpovědí pro další online a offline analýzu.

Pomocí Azure API Management můžete zabezpečit rozhraní API pomocí klíče, tokenu a filtrování IP adres. Tyto funkce umožňují vynutit flexibilní a jemně odstupňované kvóty a omezení rychlosti, upravit tvar a chování vašich api pomocí zásad a zlepšit výkon pomocí ukládání odpovědí do mezipaměti.

V této příručce a referenční ukázkové aplikace (eShopOnContainers) je architektura omezena na jednodušší a na zakázku vyrobenou kontejnerizovanou architekturu, aby se zaměřila na prosté kontejnery bez použití produktů PaaS, jako je Správa rozhraní API Azure. Ale pro velké aplikace založené na mikroslužbách, které se nasazují do Microsoft Azure, doporučujeme vyhodnotit Azure API Management jako základ pro vaše brány rozhraní API v produkčním prostředí.

### <a name="ocelot"></a>Ocelot

[Ocelot](https://github.com/ThreeMammals/Ocelot) je lehká brána rozhraní API, doporučená pro jednodušší přístupy. Ocelot je brána ROZHRANÍ API založená na open source jádru, která je speciálně vyrobena pro architekturu mikroslužeb, která potřebuje jednotné vstupní body do svého systému. Je lehký, rychlý, škálovatelný a poskytuje směrování a ověřování mezi mnoha dalšími funkcemi.

Hlavním důvodem pro výběr Ocelot u [referenční aplikace eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) je, že Ocelot je .NET Core lightweight API Gateway, kterou můžete nasadit do stejného prostředí nasazení aplikace, kde nasazujete mikroslužby/kontejnery, jako je například Hostitel Dockeru, Kubernetes atd. A protože je založen na .NET Core, je to cross-platformní umožňuje nasazení na Linuxu nebo Windows.

Předchozí diagramy znázorňující vlastní brány rozhraní API spuštěné v kontejnerech jsou přesně tak, jak můžete také spustit Ocelot v kontejneru a aplikaci založené na mikroslužbách.

Kromě toho existuje mnoho dalších produktů na trhu, které nabízejí funkce brány rozhraní API, jako je Apigee, Kong, MuleSoft, WSO2 a další produkty, jako je Linkerd a Istio pro funkce řadiče sítě služeb.

Po počáteční architektury a vzory vysvětlení části, další části vysvětlují, jak implementovat brány rozhraní API s [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Nevýhody vzoru brány rozhraní API

- Nejdůležitější nevýhodou je, že při implementaci brány rozhraní API, jste připojení této vrstvy s interní mikroslužeb. Párování, jako je tento, může způsobit vážné potíže pro vaši aplikaci. Clemens Vaster, architekt v týmu Azure Service Bus, odkazuje na tento potenciální problém jako "nový ESB" v relaci "[Zasílání zpráv a mikroslužeb](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" na GOTO 2016.

- Pomocí brány rozhraní API mikroslužeb vytvoří další možný jediný bod selhání.

- Brána rozhraní API může zavést delší dobu odezvy z důvodu dalšího volání sítě. Toto volání navíc však má obvykle menší dopad než s rozhraní klienta, který je příliš upovídaný přímo volání interní mikroslužeb.

- Pokud není správně škálovat, brána rozhraní API se může stát kritickým bodem.

- Brána rozhraní API vyžaduje další náklady na vývoj a budoucí údržbu, pokud zahrnuje vlastní logiku a agregaci dat. Vývojáři musí aktualizovat bránu rozhraní API, aby bylo možné vystavit koncové body jednotlivých mikroslužeb. Kromě toho změny implementace v interní mikroslužeb může způsobit změny kódu na úrovni brány rozhraní API. Pokud však brána rozhraní API používá pouze zabezpečení, protokolování a správu verzí (jako při použití služby Azure API Management), nemusí se tyto dodatečné náklady na vývoj použít.

- Pokud brána rozhraní API je vyvinuta jedním týmem, může existovat kritické místo vývoje. To je další důvod, proč je lepším přístupem mít několik chybně odstupňovaných bran rozhraní API, které reagují na různé potřeby klientů. Můžete také oddělit bránu rozhraní API interně do více oblastí nebo vrstev, které jsou vlastněny různými týmy pracujícími na interních mikroslužeb.

## <a name="additional-resources"></a>Další zdroje

- **Chrise Richardsona. Vzor: Brána rozhraní API / back-end pro front-end** \
  <https://microservices.io/patterns/apigateway.html>

- **Vzor brány rozhraní API** \
  <https://docs.microsoft.com/azure/architecture/microservices/gateway>

- **Vzor agregace a složení** \
  <https://microservices.io/patterns/data/api-composition.html>

- **Správa rozhraní AZURE API** \
  <https://azure.microsoft.com/services/api-management/>

- **Udi Dahan. Služba orientovaná kompozice** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

- **Clemens Vasters. Zasílání zpráv a mikroslužby na GOTO 2016 (video)** \
  <https://www.youtube.com/watch?v=rXi5CLjIQ9k>

- **Brána rozhraní API v kostce** (ASP.net základní řady výukových programů brány rozhraní API) \
  <https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html>

>[!div class="step-by-step"]
>[Předchozí](identify-microservice-domain-model-boundaries.md)
>[další](communication-in-microservice-architecture.md)
