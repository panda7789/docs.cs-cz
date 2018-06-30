---
title: Brána rozhraní API vzor versus přímou komunikaci klienta mikroslužbu
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Brána rozhraní API vzor versus přímou komunikaci klienta mikroslužbu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/07/2018
ms.openlocfilehash: 83ec054239814ba20ebeec1f3d50b9f7e6dcdd87
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106275"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Brána rozhraní API vzor versus přímou komunikaci klienta mikroslužbu

V architektuře mikroslužeb každý mikroslužbu zpřístupňuje řadu (obvykle) fine‑grained koncové body. Tato skutečnost může mít vliv client‑to‑microservice komunikaci, jak je popsáno v této části.

## <a name="direct-client-to-microservice-communication"></a>Přímé komunikaci klienta mikroslužbu

Možných přístupů je používat architekturu přímou komunikaci klienta mikroslužby. V tomto přístupu klientskou aplikaci můžete provést požadavky přímo některé mikroslužeb, jak ukazuje obrázek 4 – 12.

![Diagram zobrazující přímou komunikaci klienta mikroslužbu architektura](./media/image12.png)

**Obrázek 4 – 12**. Pomocí architektury přímou komunikaci klienta mikroslužbu

V tomto přístupu. Každý mikroslužbu má veřejný koncový bod, někdy s jiný port TCP pro každou mikroslužby. Příklad adresy URL pro konkrétní službu, může být následující adresu URL v Azure:

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

V produkčním prostředí založené na clusteru, která umožní mapování adresy URL pro vyrovnávání zatížení použít v clusteru, který naopak rozděluje požadavky na mikroslužeb. V produkčním prostředí, můžete mít aplikaci doručení řadiče (ADC) jako [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) mezi vaší mikroslužeb a Internetem. To funguje jako transparentní vrstvy, která pouze provede Vyrovnávání zatížení, ale zabezpečuje vašim službám prostřednictvím nabídky ukončení protokolu SSL. To zvyšuje zatížení hostitele, protože snižování zátěže ukončení protokolu SSL náročná na prostředky procesoru a další směrování dávky do služby Azure Application Gateway. Nástroj pro vyrovnávání zatížení a ADC jsou v každém případě transparentní z hlediska of Architektura logické aplikace.

Architektura přímou komunikaci klienta mikroslužbu může být vhodné dostatečně pro malá na základě mikroslužbu aplikace, zejména pokud je aplikace klienta webové serverové aplikace jako aplikace rozhraní ASP.NET MVC. Při vytváření velké a komplexní na základě mikroslužbu aplikací (například při zpracování desítek mikroslužbu typy) a zejména v případě, že jsou klientské aplikace vzdálené mobilní aplikace nebo SPA webových aplikací, ale tento přístup otočená několik problémů.

Při vývoji rozsáhlé aplikace založené na mikroslužeb, zvažte následující otázky:

- *Jak aplikace klienta minimalizovat počet žádostí pro back-end a snížit chatty komunikaci s více mikroslužeb?*

Interakci s více mikroslužeb k vytvoření jedné obrazovce uživatelského rozhraní zvyšuje počet zpátečních cest přes Internet. Tím se zvyšuje latenci a složitost na straně uživatelského rozhraní. Odpovědi v ideálním případě by měl být efektivně agregován, na straně serveru. To snižuje latence, protože data na více místech vraťte paralelně a některé uživatelského rozhraní můžete zobrazit data, jakmile je připraven.

- *Jak může zpracovat mezi vyjímání otázky, jako je například autorizace, transformace dat a dynamické žádost o odeslání?*

Implementace zabezpečení a aspekty mezi vyjímání jako zabezpečení a autorizace na každý mikroslužbu může vyžadovat významné vývoj úsilí. Možných přístupů je mít těchto služeb v rámci hostitelů Docker nebo interní clusteru, které nemají přímý přístup k nim z vnějšku a implementovat tyto otázky mezi vyjímání v centrálním umístění, jako je brána rozhraní API.

- *Jak může klientské aplikace komunikovat s služby, které používají protokoly Internetu popisný?*

Protokoly používá na straně serveru (například AMQP nebo binární protokoly) nepodporuje obvykle klientské aplikace. Proto musí být požadavky provést prostřednictvím protokolů jako protokolu HTTP nebo HTTPS a převedeny na ostatní protokoly později. A *man-in-the-middle* postup může pomoci v této situaci.

- *Jak budete utvářejí průčelí za zejména provedené pro mobilní aplikace?*

Rozhraní API více mikroslužeb nemusí dobře navrženy pro potřeby různých klientských aplikací. Například potřebám mobilní aplikace může být jiná než potřebám webové aplikace. Pro mobilní aplikace možná budete muset i další optimalizace tak, aby data odpovědí může být efektivnější. Můžete to třeba udělat tak, že agregaci dat z více mikroslužeb a vrací jednu sadu dat a někdy odstranění všech dat v odpovědi, která není potřeba mobilní aplikace. A samozřejmě může komprimovat data. Znovu průčelí za nebo API mezi mobilní aplikaci a mikroslužeb může být vhodné pro tento scénář.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Proč místo přímé komunikaci klienta mikroslužby zvažte brány rozhraní API

V architektuře mikroslužeb klientské aplikace obvykle nutné využívat funkce z více než jeden mikroslužby. V případě, že využití provádí přímo, klient musí pro zpracování více volání do koncových bodů mikroslužby. Co se stane při zpracovaní aplikace a byly zavedeny nové mikroslužeb nebo aktualizaci existujícího mikroslužeb? Pokud aplikace obsahuje mnoho mikroslužeb, může být zpracování tolika koncových bodů z klientských aplikací při důvodů. Vzhledem k tomu, že klientská aplikace by se lze připojit do těchto interní koncových bodů, mikroslužeb vyvíjející se v budoucnu může způsobit vysoký dopad pro klientské aplikace.

Proto pokročilou úroveň nebo vrstvě dereference (brány) může být velmi vhodné pro aplikace založené na mikroslužby. Pokud nemáte brány rozhraní API, klientské aplikace musí odesílat požadavky přímo mikroslužeb a který vyvolá problémy, jako je například následující problémy:

- **Vazební**: bez vzoru Brána rozhraní API jsou pro interní mikroslužeb doplněná klientské aplikace. Musíte vědět, jak se více oblastí aplikace rozloží v mikroslužeb klientské aplikace. Když vyvíjejí a refaktoring interní mikroslužeb, vliv na tyto akce údržby velmi chybně protože způsobí nejnovější změny do klientské aplikace z důvodu přímý odkaz na interní mikroslužeb z klienta aplikace. Klientské aplikace je nutné aktualizovat často, což těžší vyvíjí řešení.

- **Moc velký počet zpátečních cest**: jednu stránku nebo obrazovku v aplikaci klienta může vyžadovat několik volání na více služeb. Aby výsledek v síti více zaokrouhlí odezvy mezi klientem a serverem, přidání významné latence. Agregace, které jsou zpracovány v pokročilou úroveň může zvýšit výkon a uživatelské prostředí pro klientské aplikace.

- **Problémy se zabezpečením**: bez bránu, musí být všechny mikroslužeb zpřístupněny "externí světa", provedení prostor pro útoky na větší než skryjete interní mikroslužeb používá není přímo klientských aplikací. Tím menší je prostor pro útoky, tím víc zabezpečit vaše aplikace může být.

- **Mezi vyjímání obavy**: každý veřejně publikovaných mikroslužbu musí zpracovávat obavy jako je například autorizace, SSL, atd. V mnoha situacích může tyto otázky zpracovávat, v jedné vrstvě, jsou zjednodušené interní mikroslužeb.

## <a name="what-is-the-api-gateway-pattern"></a>Co je vzor Brána rozhraní API?

Při návrhu a vytvářet velká nebo složitá na základě mikroslužbu aplikace s více klientských aplikací, může být dobrým přístupem vzít v úvahu [Brána rozhraní API](https://microservices.io/patterns/apigateway.html). Toto je služba, která poskytuje jeden vstupní bod pro určité skupiny mikroslužeb. Je podobná [Facade vzor](https://en.wikipedia.org/wiki/Facade_pattern) z object‑oriented návrhu, ale v takovém případě ji je součástí distribuovaného systému.
Vzor Brána rozhraní API se také někdy označuje jako "back-end pro front-endové" [(BFF)](https://samnewman.io/patterns/architectural/bff/) vzhledem k tomu, že vytvoříte při přemýšlení o potřebám klientské aplikace.

Brána rozhraní API je proto umístěna mezi klientské aplikace a mikroslužeb. Slouží jako reverzní proxy server, směrování požadavky od klientů ke službám. Také můžete získat další vyjímání mezi funkce, například ověřování, ukončení protokolu SSL a mezipaměti.

Obrázek 4 – 13 ukazuje, jak můžete začlenit vlastní Brána rozhraní API do zjednodušené architektura založená na mikroslužbu s několika mikroslužeb.

![Diagram znázorňující, že bránu rozhraní API implementovaný jako vlastní služby](./media/image13.png)

**Obrázek 4 – 13**. Pomocí služby API Gateway implementovaný jako vlastní služby

V tomto příkladu by být bránou rozhraní API implementovaný jako vlastní ASP.NET Core tomuto webovému hostiteli služby spuštěné jako kontejner.

Je důležité, abyste měli na očích, v tomto diagramu, budete používat jeden vlastní Brána rozhraní API služby čelí více a jiné klientské aplikace. Aby fakt může být důležité riziko, protože brána rozhraní API služby bude rostoucí a vyvíjející se na základě mnoho různých požadavků z klientské aplikace. Nakonec se z důvodu těchto různé potřeby bude opakovaném a efektivně může být poměrně podobná monolitický aplikace nebo monolitický služby. To je proto velmi mnohem se doporučuje Brána rozhraní API v několika služeb nebo více menší API bran, jeden pro každý typ faktor formuláře aplikace klienta, například rozdělení.

Budete muset buďte opatrní při implementaci vzoru Brána rozhraní API. Obvykle je vhodné jedinou Brána rozhraní API agregování všechny interní mikroslužeb vaší aplikace. Pokud ano, funguje jako monolitický agregátoru nebo orchestrator a spojovacích všechny mikroslužeb porušuje mikroslužbu nezávislé.

Proto brány rozhraní API by měl být oddělené na základě obchodní hranice a klientské aplikace a není act jako jeden agregátor pro všechny interní mikroslužeb.

Při rozdělování vrstvě Brána rozhraní API do více bran rozhraní API, pokud vaše aplikace obsahuje více klientských aplikací, které se dají na primární pivot při identifikaci více typů brány rozhraní API, tak, aby může mít různé průčelí za pro potřeby každou klientskou aplikaci. Tento případ je vzor s názvem "Back-end pro Frontend" ([BFF](http://samnewman.io/patterns/architectural/bff/)) tam, kde každý Brána rozhraní API můžete zadat různé API přizpůsobit pro každý typ klienta aplikace, které by mohly mít i na základě faktor formuláře klienta implementací konkrétní adaptér kód který dole volá více interní mikroslužeb, jak je znázorněno na následujícím obrázku:

![Diagram zobrazující více bran vlastní rozhraní API](./media/image13.1.png)

**Obrázek 4-13.1**. Použití více bran vlastní rozhraní API

Předchozí obrázek ukazuje zjednodušení architektury s více bran podrobných rozhraní API. V takovém případě jsou hranice identifikovat pro každý Brána rozhraní API založené výhradně na "back-end pro Frontend" ([BFF](http://samnewman.io/patterns/architectural/bff/)) vzor, proto na základě jenom na rozhraní API potřebné pro klientské aplikace. Ale v větší aplikace by měl taky přejít na další a vytvořit další rozhraní API brány založené na hranicích obchodní jako druhý pivot návrhu.

## <a name="main-features-in-the-api-gateway-pattern"></a>Hlavní funkce ve vzoru Brána rozhraní API

Bránu rozhraní API nabízí více funkcí. V závislosti na produktu může nabízet bohatší nebo jednodušší funkce, ale většina důležité a základní funkce pro všechny brány rozhraní API jsou tyto vzory návrhu:

**Reverse server proxy nebo brány směrování**. Brána rozhraní API nabízí reverzní proxy server pro přesměrování nebo směrování požadavků (vrstvy 7 směrování, obvykle požadavky Http) ke koncovým bodům interní mikroslužeb. Brána poskytuje jeden koncový bod nebo adresa URL pro klienta, aplikací a interně mapuje požadavky na skupinu interní mikroslužeb. Tato funkce směrování vám pomůže oddělit klientských aplikací z mikroslužeb je však také poměrně vhodné při modernizing monolitický rozhraní API pomocí uložený bránou rozhraní API mezi monolitický rozhraní API a klientské aplikace, pak je můžete přidat nové rozhraní API jako nový mikroslužeb nadále pomocí starší verze rozhraní API monolitický, dokud ho je rozdělená do mnoha mikroslužeb v budoucnu. Z důvodu bránou rozhraní API klienta aplikace nebude Všimněte si, pokud rozhraní API používá jsou implementované jako interní mikroslužeb nebo monolitický rozhraní API a je důležité, když vyvíjejí a refaktoring monolitický rozhraní API do mikroslužeb, díky bránou rozhraní API směrování , nebude mít vliv klientských aplikací s všechny změny identifikátoru URI.

Další informace najdete v tématu [brány směrování vzor](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Požadavky agregace**. Jako součást vzoru brány můžete agregovat více žádostí klienta (obvykle požadavků Http) cílení na více interní mikroslužeb do požadavek jednoho klienta. Tento vzor je zvlášť vhodné, pokud na stránce nebo obrazovky klienta potřebuje informace z několika mikroslužeb. Klientská aplikace s tímto přístupem odešle jednu žádost bránou rozhraní API, která odešle zprávu několik požadavků na interní mikroslužeb a agreguje výsledky a odešle všechno zpět do klientské aplikace. Hlavní výhody a cílem tohoto vzoru návrhu je ke snížení chattiness mezi klientské aplikace a rozhraní API, back-end, který je obzvláště důležité pro vzdálené aplikace mimo datového centra, kde mikroslužeb live, jako je mobilní aplikace nebo požadavky přicházející z SPA aplikací, pocházet z jazyka Javascript v prohlížečích vzdáleného klienta. Pro provedení žádosti v prostředí serveru (jako jsou webové aplikace ASP.NET MVC základní) regulární webové aplikace není tento vzor tak důležité, protože latence je velmi mnohem menší než pro aplikace vzdáleného klienta.

V závislosti na produkt Brána rozhraní API, který používáte může být schopni provést tato agregace. V mnoha případech je však flexibilnější vytvoření agregace mikroslužeb v oboru bránou rozhraní API, můžete definovat agregace v kódu (to znamená, kód C#).

Další informace najdete v tématu [brány agregace vzor](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Mezi vyjímání obavy nebo snižování zátěže brány**. V závislosti na funkce, které nabízí každý produkt Brána rozhraní API může převzít funkci z jednotlivých mikroslužeb k bráně, kterou zjednodušuje provádění jednotlivých mikroslužbu tím, že konsolidují mezi vyjímání obavy do jedné vrstvy. To je zvlášť vhodné pro speciální funkce, které může být složité implementace správně v každé interní mikroslužbu, jako jsou následující funkce:

- Ověřování a autorizace
- Integrace služby zjišťování
- Ukládání odpovědí do mezipaměti
- Opakujte zásady, jistič a technologie QoS
- Omezení rychlosti a omezování
- Vyrovnávání zatížení
- Protokolování, trasování, korelace
- Záhlaví, řetězce dotazu a transformaci deklarací identity
- Vytvoření seznamu povolených IP

Další informace najdete v tématu [brány snižování zátěže vzor](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Produkty pomocí funkce Brána rozhraní API

Může být mnoho další otázky mezi vyjímání nabízené produkty brány rozhraní API v závislosti na každou implementaci. Například [Azure API Management](https://azure.microsoft.com/services/api-management/) (jak je znázorněno v obrázek 4-14) nejen řeší potřeb Brána rozhraní API, ale poskytuje funkce, jako je shromažďování přehledy z vašich rozhraní API. Pokud používáte do řešení pro správu rozhraní API, bránu rozhraní API je pouze součástí v rámci tohoto řešení pro správu úplné rozhraní API.

![Diagram zobrazující Brána rozhraní API s architekturou Azure API management](./media/image14.png)

**Obrázek 4-14**. Pro bránu rozhraní API pomocí Azure API Management

V takovém případě při používání produktu, jako je Azure API Management, fakt, že můžete mít jeden Brána rozhraní API není tak rizikové, protože tyto druhy brány rozhraní API jsou "užší", což znamená, že nebudete implementovat vlastní C# kód, který by mohl vyvíjet monolitický komponenta.

Brána rozhraní API produkty obvykle fungují jako reverzní proxy server pro příchozí komunikaci, kde je můžete také filtrovat rozhraní API z interní mikroslužeb plus autorizace provádí publikovaných rozhraní API v této jedné úrovni.

Pomocí API Management systému nápovědy k dispozici statistiky získat představu o tom, jak jsou používány vaše rozhraní API a jak jsou provádění. Je to tak, že umožňují zobrazit téměř sestavy analýzy v reálném čase a identifikaci trendů, které může mít vliv na vaši firmu. Plus může mít protokoly o žádosti a odpovědi aktivity pro další analýzu online a offline.

S Azure API Management můžete zabezpečit vaše rozhraní API pomocí klíče, token a filtrování protokolu IP. Tyto funkce umožňují vynutit flexibilní a podrobných kvóty a omezení přenosové rychlosti, upravit tvar a chování vaše rozhraní API pomocí zásad a zlepšují výkon při ukládání odpovědí do mezipaměti.

V této příručce a referenční dokumentace ukázkovou aplikaci (eShopOnContainers) architektura je omezený na jednodušší a vlastní kontejnerizované architektura s cílem zaměřit na prostý kontejnery bez použití PaaS produkty, jako je Azure API Management. Ale pro velké aplikace na základě mikroslužbu, které jsou nasazeny do Microsoft Azure, doporučujeme, abyste vyhodnotit Azure API Management jako základ pro vaše rozhraní API brány v produkčním prostředí.

**Ocelot.** Pro jednodušší přístupy lehké Brána rozhraní API jako Ocelot se doporučuje. [Ocelot](https://github.com/ThreeMammals/Ocelot) otevřeným zdrojem brána založená na .NET Core API zejména přišla pro architekturu mikroslužeb, vyžadující jednotná body vstupu v jejich systému. Je jednoduché, rychlá a škálovatelná a poskytuje směrování a ověřování mezi řadu dalších funkcí.

Hlavním důvodem, proč se v použil Ocelot [eShopOnContainers odkazovat aplikace](https://github.com/dotnet-architecture/eShopOnContainers) totiž Ocelot je .NET Core jednoduché rozhraní API bránu, kterou můžete nasadit do stejné prostředí nasazení aplikace, které nasazujete mikroslužeb/kontejnerů, jako je například hostitelů Docker, Kubernetes, Service Fabric, atd. A vzhledem k tomu, že je založena na .NET Core, je díky tomu můžete nasadit na systému Linux nebo Windows napříč platformami.

Předchozích diagramech zobrazuje vlastní rozhraní API Gateway spuštěná v kontejnerech přesněji jsou, jak můžete také spustit Ocelot v kontejneru a aplikace založené na mikroslužby.

Kromě toho existuje mnoho dalších produktů na trhu nabídky brány rozhraní API funkce, jako je Apigee, Kong, MuleSoft, WSO2, a další produkty jako Linkerd a Istio služby OK sítě příchozího řadiče funkce.

Po počáteční architektura a vzory vysvětlení části Další části popisují, jak implementovat rozhraní API brány s [Ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Nevýhody vzoru Brána rozhraní API

- Nejdůležitější nevýhodou je, že při implementaci bránu rozhraní API se spojovacím této vrstvě s interní mikroslužeb. Párování jako to může způsobit vážné problémy pro aplikaci. Vaster od Clemense architekti na tým Azure Service Bus, odkazuje na tato potenciální potíže jako "nové ESB" v "[zasílání zpráv a Mikroslužeb](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" relace v GOTO 2016.

- Brána rozhraní API mikroslužeb pomocí vytvoří další možné jediný bod selhání.

- Bránu rozhraní API můžete zavést prodloužení doby odezvy z důvodu další síťové volání. Toto volání navíc má však obvykle menší dopad, než by byl klient rozhraní, která je příliš chatty přímo volání interní mikroslužeb.

- Pokud není škálovat na více systémů správně, bránou rozhraní API se může stát úzkým místem.

- Bránu rozhraní API vyžaduje další vývoj náklady a budoucí údržby, pokud obsahuje vlastní logiky a agregace dat. Vývojáři musí aktualizovat bránou rozhraní API tak, aby získal každý mikroslužbu koncové body. Implementace změny v interní mikroslužeb kromě toho může způsobit změny kódu na úrovni Brána rozhraní API. Ale pokud brána rozhraní API právě aplikuje zabezpečení, protokolování a správa verzí (stejně jako při použití Azure API Management), nemusí tato náklady na vývoj pro další použití.

- Pokud brána rozhraní API je vyvinuté jeden tým, může být úzkým místem vývoj. To je další důvod, proč je vhodnější je několik pokutu podrobných API brány, které reagují na požadavky jiného klienta. Brána rozhraní API může také oddělit interně do několika oblastem nebo vrstvy, které jsou vlastněny různé týmy pracující na interní mikroslužeb.

## <a name="additional-resources"></a>Další zdroje

- **Charlese Ryšánková. Vzor: Brána rozhraní API / back-end pro front-endu** [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

- **Brána rozhraní API vzor** [*https://docs.microsoft.com/azure/architecture/microservices/gateway*](https://docs.microsoft.com/azure/architecture/microservices/gateway)

- **Agregace a složení vzor** [*http://microservices.io/patterns/data/api-composition.html*](http://microservices.io/patterns/data/api-composition.html)

- **Azure API Management** [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

- **Udi Dahan. Složení orientované na služby**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

- **Od Clemense Vasters. Zasílání zpráv a Mikroslužeb v GOTO 2016** (video)   [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)

>[!div class="step-by-step"]
[Předchozí](identify-microservice-domain-model-boundaries.md)
[další](communication-in-microservice-architecture.md)
