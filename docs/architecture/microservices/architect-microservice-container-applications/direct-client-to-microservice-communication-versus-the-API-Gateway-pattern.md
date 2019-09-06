---
title: Vzor brány rozhraní API oproti přímé komunikaci mezi klientem a mikroslužbou
description: Seznamte se s rozdíly a využitím vzoru brány API a přímé komunikace mezi klientem a mikroslužbou.
ms.date: 01/07/2019
ms.openlocfilehash: c54287ea3e99ff7fe9faf02898b8c322b756e26f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "70296816"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>Vzor brány rozhraní API oproti přímé komunikaci mezi klientem a mikroslužbou

V architektuře mikroslužeb každá mikroslužba zveřejňuje sadu (typicky) jemně odstupňovaných koncových bodů. Tato skutečnost může mít dopad na komunikaci mezi klientem a mikroslužbou, jak je vysvětleno v této části.

## <a name="direct-client-to-microservice-communication"></a>Přímá komunikace mezi klientem a mikroslužbou

Možným přístupem je použití přímé architektury komunikace mezi klientem a mikroslužbou. V tomto přístupu může klientská aplikace dělat požadavky přímo na některé mikroslužby, jak je znázorněno na obrázku 4-12.

![Diagram znázorňující architekturu komunikace mezi klientem a mikroslužbou, kde každá aplikace komunikuje přímo s jednotlivými mikroslužbami.](./media/image12.png)

**Obrázek 4-12**. Použití přímé architektury komunikace mezi klientem a mikroslužbou

V tomto postupu má každá mikroslužba veřejný koncový bod, někdy s jiným portem TCP pro každou mikroslužbu. Příkladem adresy URL konkrétní služby může být následující adresa URL v Azure:

`http://eshoponcontainers.westus.cloudapp.azure.com:88/`

V produkčním prostředí založeném na clusteru by tato adresa URL byla namapována na nástroj pro vyrovnávání zatížení, který se používá v clusteru, který pak rozšíří požadavky napříč mikroslužbami. V produkčních prostředích můžete mít k dispozici řadič pro doručování aplikací (ADC), jako je například [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) mezi vašimi mikroslužbami a internetem. Funguje jako průhledná vrstva, která neprovádí vyrovnávání zatížení, ale zabezpečuje vaše služby tím, že nabízí ukončení protokolu SSL. Tím se zlepšuje zatížení hostitelů tím, že dojde k přesměrování ukončení protokolu SSL náročného na procesor a dalších funkcí směrování do Azure Application Gateway. Nástroj pro vyrovnávání zatížení a konektor ADC jsou v každém případě transparentní z pohledu logické architektury aplikace.

Pro malou aplikaci založenou na mikroslužbách by mohla být dostatečná pro komunikaci mezi klientem a mikroslužbou, zejména v případě, že klientská aplikace je webová aplikace, jako je aplikace ASP.NET MVC. Nicméně při vytváření rozsáhlých a složitých aplikací založených na mikroslužbách (například při manipulaci s desítkami typů mikroslužeb) a zejména v případě, že jsou klientské aplikace vzdálené mobilní aplikace nebo zabezpečené webové aplikace, které se blíží několika problémům.

Při vývoji velké aplikace založené na mikroslužbách Vezměte v úvahu následující otázky:

- *Jak můžou klientské aplikace minimalizovat počet požadavků na back-end a snížit komunikaci s konverzacemi s více mikroslužbami?*

Interakce s více mikroslužbami při vytváření jediné obrazovky uživatelského rozhraní zvyšuje počet přenosů po internetu. Tím se zvyšuje latence a složitost na straně uživatelského rozhraní. V ideálním případě by se odpovědi měly efektivně agregovat na straně serveru. Tím se snižuje latence, protože se souběžně vrací více dat a některé uživatelské rozhraní může zobrazit data hned po jejím dokončení.

- *Jak můžete zpracovávat problémy mezi průřezy, například autorizací, transformace dat a dynamické odesílání požadavků?*

Implementace zabezpečení a mezi průřezy, jako je zabezpečení a autorizace u každé mikroslužby, může vyžadovat významné úsilí při vývoji. Možným přístupem je mít tyto služby v rámci hostitele Docker nebo interního clusteru k omezení přímého přístupu k nim zvenčí a k implementaci těchto obav v centralizovaném umístění, jako je brána API.

- *Jak můžou klientské aplikace komunikovat se službami, které používají jiné protokoly než Internet?*

Protokoly používané na straně serveru (například AMQP nebo binární protokoly) nejsou většinou podporovány v klientských aplikacích. Proto musí být požadavky provedeny prostřednictvím protokolů jako HTTP/HTTPS a následně přeloženy do dalších protokolů. V této situaci vám může pomáhat *útok* prostředníkem.

- *Jak můžete vytvořit obrazec fasády, která je zvlášť vytvořená pro mobilní aplikace?*

Rozhraní API pro více mikroslužeb nemusí být navržené pro potřeby různých klientských aplikací. Třeba požadavky mobilní aplikace se mohou lišit od potřeb webové aplikace. U mobilních aplikací možná budete muset ještě více optimalizovat, aby bylo možné zajistit efektivnější odezvy dat. Můžete to udělat tak, že agregujete data z více mikroslužeb a vrátíte jednu sadu dat a někdy eliminují veškerá data v odpovědi, která mobilní aplikace nevyžaduje. Tato data samozřejmě můžete zkomprimovat. Pro tento scénář může být znovu vhodná fasáda nebo rozhraní API mezi mobilní aplikací a mikroslužbami.

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>Proč zvážit brány rozhraní API namísto přímé komunikace mezi klientem a mikroslužbou

V architektuře mikroslužeb klientské aplikace obvykle potřebují využívat funkce z více než jedné mikroslužby. Pokud je tato spotřeba prováděna přímo, klient potřebuje zpracovat více volání koncových bodů mikroslužeb. Co se stane, když se aplikace vyvíjí a zavádí se nové mikroslužby nebo se aktualizují stávající mikroslužby? Pokud má vaše aplikace velký počet mikroslužeb, což znamená, že mnoho koncových bodů z klientských aplikací může být Nightmare. Vzhledem k tomu, že klientská aplikace by byla propojená s těmito interními koncovými body, může být vývoj mikroslužeb v budoucnu ovlivněný vysokým dopadem na klientské aplikace.

Proto je pro aplikace založené na mikroslužbách velmi výhodné mít úroveň dereference (brána). Pokud nemáte brány rozhraní API, klientské aplikace musí posílat požadavky přímo na mikroslužby a, které vyvolává problémy, například následující problémy:

- **Spoj**: Bez vzoru brány API jsou klientské aplikace spojeny s interními mikroslužbami. Klientské aplikace potřebují informace o tom, jak se více oblastí aplikace rozloží v mikroslužbách. Při vývoji a refaktoringu vnitřních mikroslužeb tyto akce ovlivnily nechybnou údržbu, protože způsobují přerušující změny klientských aplikací kvůli přímému odkazu na interní mikroslužby z klientských aplikací. Klientské aplikace je třeba často aktualizovat, takže se řešení bude obtížnější vyvíjet.

- **Příliš mnoho zpátečních cest**: Jedna stránka nebo obrazovka v klientské aplikaci může vyžadovat několik volání na více služeb. To může vést k tomu, že mezi klientem a serverem dojde k většímu počtu síťových přenosů a přidáním významné latence. Agregace zpracovávaná na mezilehlé úrovni by mohla zlepšit výkon a uživatelské prostředí pro klientskou aplikaci.

- **Problémy se zabezpečením**: Bez brány musí být všechny mikroslužby vystavené externímu světu, takže je velikost prostoru pro útoky větší, než když skryjete interní mikroslužby, které nejsou přímo používané klientskými aplikacemi. Menší plocha pro útok je, tím bezpečnější může být aplikace.

- **Otázky pro průřez**: Každá veřejně publikovaná mikroslužba musí zvládnout obavy, jako je například autorizace, SSL atd. V mnoha situacích by tyto otázky mohly být zpracovány v rámci jedné úrovně, aby byly interní mikroslužby zjednodušeny.

## <a name="what-is-the-api-gateway-pattern"></a>Co je to vzor brány rozhraní API?

Při návrhu a vytváření rozsáhlých nebo složitých aplikací založených na mikroslužbách s více klientskými aplikacemi může být vhodné zvážit [bránu rozhraní API](https://microservices.io/patterns/apigateway.html). Toto je služba, která poskytuje jeden vstupní bod pro určité skupiny mikroslužeb. Je podobný [vzor průčelí](https://en.wikipedia.org/wiki/Facade_pattern) z objektově orientovaného návrhu, ale v tomto případě je součástí distribuovaného systému. Vzor brány rozhraní API se také někdy označuje jako "back-end pro front-end" ([BFF](https://samnewman.io/patterns/architectural/bff/)), protože ho sestavíte a myslíme na potřebách klientské aplikace.

Proto brána API se nachází mezi klientskými aplikacemi a mikroslužbami. Funguje jako reverzní proxy server, směrování požadavků od klientů na služby. Může také poskytovat další funkce pro různé průřezy, jako je ověřování, ukončení protokolu SSL a mezipaměť.

Obrázek 4-13 ukazuje, jak se dá vlastní brána API vejít do zjednodušené architektury založené na mikroslužbách jenom s několika mikroslužbami.

![Diagram znázorňující bránu rozhraní API implementovanou jako vlastní služba, aby se aplikace připojovaly k jednomu koncovému bodu, brána API, která je nakonfigurovaná tak, aby přenesla požadavky na jednotlivé mikroslužby.](./media/image13.png)

**Obrázek 4-13**. Použití brány API, která je implementovaná jako vlastní služba

V tomto příkladu by se brána API implementovala jako vlastní ASP.NET Core služba webhosta spuštěná jako kontejner.

Je důležité zdůraznit, že v tomto diagramu byste použili jednu vlastní službu API Gateway, která se týká více a různých klientských aplikací. Tato skutečnost může představovat důležité riziko, protože vaše služba API Gateway se bude zvětšovat a rozvíjet na základě mnoha různých požadavků z klientských aplikací. Nakonec bude bloated z důvodu těchto různých potřeb a efektivně může být poměrně podobný aplikaci monolitické nebo službě monolitické. To je důvod, proč je velmi vhodné rozdělit bránu API ve více službách nebo více menších bran rozhraní API, jeden pro každý klient aplikace typ formuláře-faktor.

Při implementaci vzoru brány rozhraní API musíte být opatrní. Obvykle není vhodné mít jedinou bránu rozhraní API, která agreguje všechny interní mikroslužby vaší aplikace. V takovém případě funguje jako agregátor monolitické nebo Orchestrator a je porušená autonomii mikroslužeb tím, že se připojí ke všem mikroslužbám.

Proto by se brány rozhraní API měly oddělit na základě hranic firmy a klientských aplikací a nemusí fungovat jako jeden agregátor pro všechny interní mikroslužby.

Při rozdělení vrstvy brány API na několik bran rozhraní API platí, že pokud má vaše aplikace více klientských aplikací, může být primárním objektem Pivot při identifikaci několika typů bran rozhraní API, takže můžete mít různou fasádu pro potřeby jednotlivých klientských aplikací. Tento případ je vzor nazvaný back-end pro front-end ([BFF](https://samnewman.io/patterns/architectural/bff/)), kde každá brána API může poskytovat jiné rozhraní API přizpůsobené pro každý typ klientské aplikace, případně i na základě faktoru formuláře klienta implementací konkrétního kódu adaptéru, který je pod voláními. několik interních mikroslužeb, jak je znázorněno na následujícím obrázku:

![Diagram znázorňující několik vlastních bran rozhraní API, kde jsou brány API oddělené od typu klienta; jeden pro mobilní klienty a jeden pro webové klienty. Tradiční webová aplikace se připojuje ke mikroslužbám MVC, která používá webovou bránu API.](./media/image13.1.png)

**Obrázek 4 – 13.1**. Používání několika vlastních bran API

Předchozí obrázek ukazuje zjednodušenou architekturu s několika jemně odstupňovanými branami API. V takovém případě jsou hranice identifikované pro jednotlivé brány rozhraní API založené čistě na vzoru back-end pro front-end ([BFF](https://samnewman.io/patterns/architectural/bff/)), a proto jsou založené jenom na rozhraní API potřebném pro každou klientskou aplikaci. Ale v větších aplikacích byste také měli dál pokračovat a vytvořit další brány API na základě hranic firmy jako druhého kontingenčního pivotu.

## <a name="main-features-in-the-api-gateway-pattern"></a>Hlavní funkce ve vzoru brány rozhraní API

Brána rozhraní API může nabízet víc funkcí. V závislosti na tom, jaký produkt může nabízet bohatší nebo jednodušší funkce, jsou ale nejdůležitější a základní funkce pro libovolnou bránu rozhraní API tyto vzory návrhu:

**Směrování reverzního proxy serveru nebo brány.** Rozhraní API Gateway nabízí reverzní proxy server pro přesměrování nebo směrování požadavků (směrování vrstvy 7, obvykle požadavky HTTP) do koncových bodů interních mikroslužeb. Brána poskytuje jeden koncový bod nebo adresu URL pro klientské aplikace a pak interně mapuje požadavky na skupinu interních mikroslužeb. Tato funkce směrování pomáhá oddělit klientské aplikace od mikroslužeb, ale je také poměrně výhodný, když modernizaci rozhraní API monolitické pomocí brány API v mezi rozhraními monolitické API a klientskými aplikacemi, a pak můžete přidat nová rozhraní API jako nové mikroslužby. Pořád se používá starší verze rozhraní monolitické API, dokud se v budoucnu nerozdělí na spoustu mikroslužeb. Z důvodu brány rozhraní API nebudou klientské aplikace všimnout, jestli se použitá rozhraní API implementují jako interní mikroslužby nebo rozhraní monolitické API a jsou důležitější, a to díky tomu, že se při vývoji a refaktorování rozhraní monolitické API na mikroslužby vyvíjejí pomocí směrování brány API. , klientské aplikace nebudou mít vliv na změny identifikátoru URI.

Další informace najdete v tématu [vzor směrování brány](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing).

**Agregace požadavků.** V rámci vzoru brány můžete agregovat více požadavků klientů (obvykle požadavků HTTP), které cílí na více interních mikroslužeb do jediné žádosti klienta. Tento model je vhodný hlavně v případě, že stránka klienta/obrazovka potřebuje informace z několika mikroslužeb. S tímto přístupem klientská aplikace pošle jednu žádost do brány rozhraní API, která odesílá několik požadavků do interních mikroslužeb a pak agreguje výsledky a pošle všechno zpátky do klientské aplikace. Hlavním přínosem a cílem tohoto vzoru návrhu je snížit upovídanost mezi klientskými aplikacemi a rozhraním back-end API, což je obzvláště důležité pro vzdálené aplikace z datového centra, ve kterém se mikroslužby nacházejí v provozu, jako jsou mobilní aplikace nebo požadavky, které pocházejí z aplikací SPA, které pocházet z JavaScriptu v klientských vzdálených prohlížečích. U běžných webových aplikací, které provádějí požadavky v prostředí serveru (jako je webová aplikace ASP.NET Core MVC), není tento model tak důležitý, protože latence je mnohem menší než u vzdálených klientských aplikací.

V závislosti na použitém produktu brány API může být tato agregace schopná provádět tuto agregaci. V mnoha případech je však pružnější vytvořit agregované mikroslužby v rámci oboru brány rozhraní API, takže definujete agregaci v kódu (tj. C# kód):

Další informace najdete v tématu [model agregace brány](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation).

**Problémy pro průřezy nebo snižování zátěže brány.** V závislosti na funkcích, které nabízí jednotlivé produkty brány rozhraní API, můžete přesměrovat funkce z jednotlivých mikroslužeb na bránu, což zjednodušuje implementaci každé mikroslužby sloučením různých oblastí průřezů do jedné úrovně. To je zvlášť užitečné pro specializované funkce, které je možné složitě použít v každé interní mikroslužbě, jako jsou například následující funkce:

- Ověřování a autorizace
- Integrace zjišťování služeb
- Ukládání odpovědí do mezipaměti
- Zásady opakování, přepínací modul okruhů a QoS
- Omezení rychlosti a omezení
- Vyrovnávání zatížení
- Protokolování, trasování, korelace
- Hlavičky, řetězce dotazů a transformace deklarací identity
- Seznam povolených IP adres

Další informace najdete v tématu [model snižování zátěže brány](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading).

## <a name="using-products-with-api-gateway-features"></a>Používání produktů s funkcemi API Gateway

V závislosti na každé implementaci může být k dispozici mnoho dalších častých otázek pro průřezy nabízených produkty API Gateway. Prozkoumáme toto:

- [API Management Azure](https://azure.microsoft.com/services/api-management/)
- [Ocelot](https://github.com/ThreeMammals/Ocelot)

### <a name="azure-api-management"></a>API Management Azure

[API Management Azure](https://azure.microsoft.com/services/api-management/) (jak je znázorněno na obrázku 4-14) nejenom řeší vaše požadavky na bránu API, ale poskytuje funkce, jako je shromažďování přehledů z vašich rozhraní API. Pokud používáte řešení API Management, brána rozhraní API je jenom součást v rámci celého řešení API Management.

![Azure API Management řeší jak vaše brána rozhraní API, tak i jejich požadavky na správu, jako je protokolování, zabezpečení, měření atd.](./media/api-gateway-azure-api-management.png)

**Obrázek 4-14**. Použití Azure API Management pro vaši bránu API

V takovém případě, když používáte produkt, jako je například Azure API Management, skutečnost, že máte jedinou bránu API, není tak riskantní, protože tyto druhy bran rozhraní API jsou "užší", což znamená, že neimplementujete vlastní C# kód, který by se mohl vyvíjet k komponenta monolitické 

Produkty brány rozhraní API obvykle fungují jako reverzní proxy server pro komunikaci příchozího přenosu dat, kde můžete také vyfiltrovat rozhraní API z interních mikroslužeb a použít autorizaci na publikovaná rozhraní API v této jedné vrstvě.

Přehledy dostupné z API Management systému vám pomůžou pochopit, jak se vaše rozhraní API používají a jak se provádějí. Díky tomu můžete zobrazit sestavy analýzy téměř v reálném čase a identifikovat trendy, které by mohly mít dopad na vaši firmu. Navíc můžete mít protokoly o aktivitě požadavků a odpovědí pro další online a offline analýzu.

Pomocí Azure API Management můžete zabezpečit vaše rozhraní API pomocí klíče, tokenu a filtrování IP adres. Tyto funkce umožňují vyhovět flexibilním a jemně odstupňovaným kvótám a omezením četnosti, měnit tvar a chování rozhraní API pomocí zásad a zlepšovat výkon pomocí ukládání odpovědí do mezipaměti.

V této příručce a v referenční aplikaci eShopOnContainers (Reference Sample Application) je architektura omezená na jednodušší a vlastní integrovanou architekturu, aby se daly soustředit na jednoduché kontejnery bez použití PaaSch produktů, jako je Azure API Management. Pro velké aplikace založené na mikroslužbách, které jsou nasazené v Microsoft Azure, doporučujeme, abyste Azure API Management vyhodnotili jako základ pro vaše brány rozhraní API v produkčním prostředí.

### <a name="ocelot"></a>Ocelot

[Ocelot](https://github.com/ThreeMammals/Ocelot) je zjednodušená brána API, která se doporučuje pro jednodušší přístupy. Ocelot je open source brána API založená na rozhraní .NET Core, která se skládá hlavně pro architekturu mikroslužeb, která vyžaduje sjednocení vstupních bodů do jejich systému. Je odlehčená, rychlá a škálovatelná a poskytuje směrování a ověřování mezi mnoha dalšími funkcemi.

Hlavním důvodem pro výběr Ocelot pro [referenční aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) je, že Ocelot je odlehčená brána rozhraní API .NET Core, kterou můžete nasadit do stejného prostředí nasazení aplikace, do kterého nasazujete mikroslužby/ kontejnery, jako je například hostitel Docker, Kubernetes atd. A vzhledem k tomu, že je založená na .NET Core, je to pro různé platformy, které vám umožní nasadit na Linux nebo Windows.

Předchozí diagramy, které zobrazují vlastní brány API spuštěné v kontejnerech, jsou přesně takové, jak můžete také spustit Ocelot v kontejneru a v aplikaci založené na mikroslužbách.

Kromě toho je na trhu mnoho dalších produktů, které nabízejí funkce bran rozhraní API, jako jsou Apigee, Hongkong, MuleSoft, WSO2 a další produkty, jako jsou linkery a Istio pro funkce herního adaptéru pro síť.

V dalších oddílech se po úvodní části architektury a vzorů vysvětlují, jak implementovat brány API pomocí [ocelot](https://github.com/ThreeMammals/Ocelot).

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Nevýhody vzoru brány rozhraní API

- Nejdůležitější nevýhodou je, že když implementujete bránu API, budete tuto vrstvu přidružit k vnitřním mikroslužbám. Propojení podobně může způsobit vážné problémy pro vaši aplikaci. Clemense obrovského, architekt ve Azure Service Bus týmu, odkazuje na toto potenciální potíže jako "nové ESB" v relaci "[zasílání zpráv a mikroslužeb](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" v tématu goto 2016.

- Použití brány rozhraní API mikroslužeb vytvoří další možný jediný bod selhání.

- Brána rozhraní API může způsobit zvýšení doby odezvy z důvodu dalšího síťového volání. Nicméně toto nadbytečné volání má méně dopad než klientské rozhraní, které je příliš nepřímým voláním vnitřních mikroslužeb.

- Pokud není horizontální horizontální navýšení kapacity, může se brána API stát kritickým bodem.

- Brána API vyžaduje další náklady na vývoj a budoucí údržbu, pokud obsahuje vlastní logiku a datovou agregaci. Vývojáři musí aktualizovat bránu rozhraní API, aby vystavily koncové body mikroslužeb. Změny v implementaci v interních mikroslužbách navíc můžou způsobit změny kódu na úrovni brány rozhraní API. Pokud se ale brána API jenom aplikuje na zabezpečení, protokolování a správu verzí (jako při použití Azure API Management), nemusí se tyto dodatečné náklady na vývoj vztahovat.

- Pokud je brána API vyvinutá jedním týmem, může dojít k nekritickému vývoji. To je další důvod, proč lepší přístup je mít několik jemně odstupňovaných bran rozhraní API, které reagují na různé požadavky klientů. Bránu rozhraní API můžete také interně rozdělit do několika oblastí nebo vrstev vlastněných různými týmy, které pracují na vnitřních mikroslužbách.

## <a name="additional-resources"></a>Další zdroje

- **Chris Richardson. Vzorku Brána API/back-end pro front-end** \
  <https://microservices.io/patterns/apigateway.html>

- **Vzor brány API** \
  <https://docs.microsoft.com/azure/architecture/microservices/gateway>

- **Model agregace a kompozice** \
  <https://microservices.io/patterns/data/api-composition.html>

- **API Management Azure** \
  <https://azure.microsoft.com/services/api-management/>

- **Udi Dahan. Složení orientované na služby** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

- **Clemense obrovské. Zasílání zpráv a mikroslužeb na adrese GOTO 2016 (video)**  \
  <https://www.youtube.com/watch?v=rXi5CLjIQ9k>

- **Brána API v kostce** (Řada kurzů ASP.net Core API Gateway) \
  <https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html>

>[!div class="step-by-step"]
>[Předchozí](identify-microservice-domain-model-boundaries.md)Další
>[](communication-in-microservice-architecture.md)
