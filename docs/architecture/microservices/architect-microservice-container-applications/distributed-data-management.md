---
title: Výzvy a řešení správy distribuovaných dat
description: Zjistěte, jaké jsou výzvy a řešení pro správu distribuovaných dat ve světě mikroslužeb.
ms.date: 09/20/2018
ms.openlocfilehash: c30de24591d5a73fd34087f34a69e9c7ed54cd35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834448"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Výzvy a řešení správy distribuovaných dat

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Výzva \#1: Jak definovat hranice každé mikroslužby

Definování hranice mikroslužeb je pravděpodobně první výzvou, se kterou se setká kdokoli. Každá mikroslužba musí být součástí vaší aplikace a každá mikroslužba by měla být autonomní se všemi výhodami a výzvami, které zprostředkovává. Ale jak ty hranice identifikujete?

Nejprve se musíte zaměřit na modely logické domény aplikace a související data. Pokuste se identifikovat oddělené ostrovy dat a různé kontexty v rámci stejné aplikace. Každý kontext může mít jiný obchodní jazyk (jiné obchodní podmínky). Kontexty by měly být definovány a spravovány nezávisle. Termíny a entity, které se používají v těchto různých kontextech může znít podobně, ale můžete zjistit, že v určitém kontextu obchodní koncept s jedním se používá pro jiný účel v jiném kontextu a může dokonce mít jiný název. Například uživatel může být odkazován jako uživatel v kontextu identity nebo členství, jako zákazník v kontextu CRM, jako kupující v kontextu objednávky a tak dále.

Způsob, jakým identifikujete hranice mezi více kontexty aplikace s jinou doménou pro každý kontext, je přesně způsob, jak můžete identifikovat hranice pro každou obchodní mikroslužbu a její související model domény a data. Vždy se pokusíte minimalizovat propojení mezi těmito mikroslužeb. Tato příručka jde do více podrobností o této identifikace a návrh modelu domény v části [Identifikace hranice modelu domény pro každou mikroslužbu](identify-microservice-domain-model-boundaries.md) později.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Výzva \#2: Jak vytvořit dotazy, které načítají data z několika mikroslužeb

Druhou výzvou je, jak implementovat dotazy, které načítají data z několika mikroslužeb, a zároveň se vyhnout upovídaný komunikaci s mikroslužeb ze vzdálených klientských aplikací. Příkladem může být jedna obrazovka z mobilní aplikace, která potřebuje zobrazit informace o uživateli, který je vlastněn košíku, katalogu a mikroslužeb identity uživatele. Dalším příkladem by komplexní sestavy zahrnující mnoho tabulek umístěných ve více mikroslužeb. Správné řešení závisí na složitosti dotazů. Ale v každém případě budete potřebovat způsob, jak agregovat informace, pokud chcete zlepšit efektivitu komunikace vašeho systému. Nejoblíbenější řešení jsou následující.

**Brána rozhraní API.** Pro jednoduché agregace dat z více mikroslužeb, které vlastní různé databáze, doporučený přístup je agregace mikroslužby označovány jako brána rozhraní API. Však musíte být opatrní při implementaci tohoto vzoru, protože může být bod sytič v systému a může porušovat princip autonomie mikroslužeb. Chcete-li tuto možnost zmírnit, můžete mít více fined-zrnitý brány rozhraní API každý z nich se zaměřením na vertikální "řez" nebo obchodní oblasti systému. Vzor brány rozhraní API je vysvětleno podrobněji v [části Brána rozhraní API](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication) později.

**CQRS s tabulkami dotazů a čtení.** Dalším řešením pro agregaci dat z více mikroslužeb je [vzor materializovaného zobrazení](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). V tomto přístupu vygenerujete předem (připravit nenormalizovaná data před skutečné dotazy dojít), tabulka jen pro čtení s daty, která je vlastněna více mikroslužeb. Tabulka má formát vhodný pro potřeby klientské aplikace.

Zvažte něco jako obrazovku pro mobilní aplikaci. Pokud máte jednu databázi, můžete shromáždit data pro tuto obrazovku pomocí dotazu SQL, který provádí komplexní spojení zahrnující více tabulek. Však pokud máte více databází a každá databáze je vlastněna jinou mikroslužbu, nelze dotaz ovat tyto databáze a vytvořit spojení SQL. Složitý dotaz se stává výzvou. Požadavek můžete řešit pomocí přístupu CQRS – vytvoříte nenormalizovanou tabulku v jiné databázi, která se používá pouze pro dotazy. Tabulka může být navržena speciálně pro data, která potřebujete pro složitý dotaz, s relace 1:1 mezi poli potřebnými na obrazovce aplikace a sloupci v tabulce dotazů. Mohlo by to také sloužit pro účely podávání zpráv.

Tento přístup nejen řeší původní problém (jak dotazovat a připojit se napříč mikroslužbami), ale také výrazně zvyšuje výkon ve srovnání se složitým spojením, protože již máte data, která aplikace potřebuje v tabulce dotazů. Samozřejmě pomocí příkazu a dotazu odpovědnost oddělení (CQRS) s dotazem nebo čtení tabulek znamená další vývojové práce a budete muset přijmout případné konzistence. Nicméně požadavky na výkon a vysokou škálovatelnost ve [scénářích spolupráce](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (nebo konkurenční scénáře, v závislosti na úhlu pohledu) jsou, kde byste měli použít CQRS s více databází.

**"Studená data" v centrálních databázích.** Pro složité sestavy a dotazy, které nemusí vyžadovat data v reálném čase, běžným přístupem je exportovat "horká data" (transakční data z mikroslužeb) jako "studená data" do rozsáhlých databází, které se používají pouze pro vytváření sestav. Tento centrální databázový systém může být systém založený na velkých datech, jako hadoop, datový sklad, jako je ten založený na Azure SQL Data Warehouse, nebo dokonce jedna databáze SQL, která se používá pouze pro sestavy (pokud velikost nebude problém).

Mějte na paměti, že tato centralizovaná databáze by se používala pouze pro dotazy a sestavy, které nepotřebují data v reálném čase. Původní aktualizace a transakce, jako zdroj pravdy, musí být v datech mikroslužeb. Způsob, jakým byste synchronizovali data, by byl buď pomocí komunikace řízené událostmi (zahrnuty v následujících částech), nebo pomocí jiných nástrojů pro import a export databázové infrastruktury. Pokud používáte komunikaci řízenou událostmi, bude tento proces integrace podobný způsobu šíření dat, jak je popsáno dříve pro tabulky dotazů CQRS.

Pokud však návrh aplikace zahrnuje neustále agregovat informace z více mikroslužeb pro složité dotazy, může být příznakem chybný návrh - mikroslužba by měla být co nejvíce izolována od jiných mikroslužeb. (To vylučuje sestavy/analýzy, které by měly vždy používat centrální databáze za studena dat.) S tento problém často může být důvod emitovat mikroslužeb. Je třeba vyvážit autonomii evoluce a nasazení každé mikroslužby se silnými závislostmi, soudržností a agregací dat.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Výzva \#3: Jak dosáhnout konzistence mezi více mikroslužeb

Jak již bylo uvedeno dříve, data vlastněná každou mikroslužbu je privátní pro tuto mikroslužbu a lze přistupovat pouze pomocí jeho rozhraní API mikroslužeb. Proto představuje výzvu, jak implementovat obchodní procesy od konce do konce při zachování konzistence mezi více mikroslužeb.

Chcete-li analyzovat tento problém, podívejme se na příklad z [referenční aplikace eShopOnContainers](https://aka.ms/eshoponcontainers). Mikroslužba katalogu udržuje informace o všech produktech, včetně ceny produktu. Mikroslužba Košík spravuje časová data o položkách produktu, které uživatelé přidávají do svých nákupních košíků, což zahrnuje cenu položek v době, kdy byly přidány do košíku. Pokud je cena produktu aktualizována v katalogu, měla by být tato cena aktualizována také v aktivních koších, které mají stejný produkt, plus systém by měl pravděpodobně varovat uživatele, že se cena určité položky změnila od doby, kdy ji přidali do košíku.

V hypotetické monolitické verzi této aplikace, když se změní cena v tabulce produktů, podsystém katalogu může jednoduše použít transakci ACID k aktualizaci aktuální ceny v tabulce košíku.

V aplikaci založené na mikroslužbách jsou však tabulky Product a Basket vlastněny příslušnými mikroslužbami. Žádná mikroslužba by nikdy neměla zahrnovat tabulky nebo úložiště vlastněné jinou mikroslužbou ve vlastních transakcích, ani v přímých dotazech, jak je znázorněno na obrázku 4-9.

![Diagram znázorňující, že data databáze mikroslužeb nelze sdílet.](./media/distributed-data-management/indepentent-microservice-databases.png)

**Obrázek 4-9**. Mikroslužba nemá přímý přístup ke tabulce v jiné mikroslužbě

Mikroslužba katalogu by neměla aktualizovat tabulku košíku přímo, protože tabulka košíku je vlastněna mikroslužbou košíku. Chcete-li provést aktualizaci mikroslužby košíku, mikroslužba katalogu by měla používat konečnou konzistenci pravděpodobně založenou na asynchronní komunikaci, jako jsou události integrace (komunikace založená na zprávě a událostech). To je, jak [eShopOnContainers](https://aka.ms/eshoponcontainers) referenční aplikace provádí tento typ konzistence mezi mikroslužeb.

Jak je uvedeno v [teoréme SZP](https://en.wikipedia.org/wiki/CAP_theorem), musíte si vybrat mezi dostupností a konzistencí silnou acid. Většina scénářů založených na mikroslužbách vyžaduje dostupnost a vysokou škálovatelnost oproti silné konzistenci. Důležité aplikace musí zůstat v provozu a vývojáři mohou obejít silnou konzistenci pomocí technik pro práci se slabou nebo konečnou konzistencí. Toto je přístup, který používá většina architektur založených na mikroslužbách.

Transakce ve stylu ACID nebo dvoufázové potvrzení navíc nejsou pouze v rozporu se zásadami mikroslužeb; většina databází NoSQL (jako je Azure Cosmos DB, MongoDB atd.) nepodporuje transakce dvoufázového potvrzení, typické ve scénářích distribuovaných databází. Je však nezbytné zachovat konzistenci dat mezi službami a databázemi. Tato výzva souvisí také s otázkou, jak šířit změny mezi více mikroslužeb, když některá data musí být redundantní – například když potřebujete mít název nebo popis produktu v mikroslužbě katalogu a košíku mikroservis.

Dobrým řešením tohoto problému je použít případnou konzistenci mezi mikroslužbami formulované prostřednictvím komunikace řízené událostmi a systémem publikování a odběru. Tato témata jsou popsána v části [Asynchronní komunikace řízená událostmi](asynchronous-message-based-communication.md#asynchronous-event-driven-communication) dále v této příručce.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Výzva \#4: Jak navrhnout komunikaci přes hranice mikroslužeb

Komunikace přes hranice mikroslužeb je skutečnou výzvou. V tomto kontextu komunikace neodkazuje na jaký protokol byste měli použít (HTTP a REST, AMQP, zasílání zpráv a tak dále). Místo toho řeší, jaký styl komunikace byste měli použít a zejména jak by měly být vaše mikroslužby spojeny. V závislosti na úrovni párování, když dojde k poruše, dopad této poruchy na váš systém se bude výrazně lišit.

V distribuovaném systému, jako je aplikace založená na mikroslužbách, s tolika artefakty pohybujícími se a s distribuovanými službami na mnoha serverech nebo hostitelích, komponenty nakonec selžou. Částečné selhání a ještě větší výpadky dojde, takže je třeba navrhnout mikroslužeb a komunikace mezi nimi s ohledem na běžná rizika v tomto typu distribuovaného systému.

Populární přístup je implementovat mikroslužeb založené http (REST) z důvodu jejich jednoduchosti. Přístup založený na protokolu HTTP je naprosto přijatelný; problém zde souvisí s tím, jak jej používáte. Pokud používáte požadavky HTTP a odpovědi pouze pro interakci s mikroslužeb z klientských aplikací nebo z brány rozhraní API, to je v pořádku. Ale pokud vytvoříte dlouhé řetězce synchronní volání HTTP přes mikroslužeb, komunikaci přes jejich hranice, jako kdyby mikroslužeb byly objekty v monolitické aplikace, aplikace nakonec narazí na problémy.

Představte si například, že vaše klientská aplikace provede volání rozhraní HTTP API pro jednotlivé mikroslužby, jako je řazení mikroslužeb. Pokud řazení mikroslužeb zase volá další mikroslužby pomocí protokolu HTTP v rámci stejného cyklu požadavku a odpovědi, vytváříte řetězec volání HTTP. Zpočátku by to mohlo znít rozumně. Existují však důležité body, které je třeba vzít v úvahu při cestě touto cestou:

- Blokování a nízký výkon. Vzhledem k synchronní povaze protokolu HTTP původní požadavek nezíská odpověď, dokud nebudou dokončena všechna interní volání HTTP. Představte si, pokud počet těchto volání výrazně zvyšuje a současně jeden z přechodných volání HTTP mikroslužby je blokován. Výsledkem je, že výkon je ovlivněna a celková škálovatelnost bude exponenciálně ovlivněna jako další požadavky HTTP zvýšit.

- Propojení mikroslužeb s HTTP. Obchodní mikroslužby by neměly být spojeny s jinými obchodními mikroslužbami. V ideálním případě by neměli "vědět" o existenci jiných mikroslužeb. Pokud vaše aplikace závisí na propojení mikroslužeb jako v příkladu, dosažení autonomie na mikroslužbu bude téměř nemožné.

- Selhání v jedné mikroslužbě. Pokud jste implementovali řetězec mikroslužeb propojených voláním HTTP, když dojde k selhání některé mikroslužeb (a nakonec se nezdaří), celý řetězec mikroslužeb se nezdaří. Systém založený na mikroslužbách by měl být navržen tak, aby i nadále fungovat stejně dobře, jak je to možné během částečné selhání. I v případě, že implementovat logiku klienta, který používá opakování s exponenciální backoff nebo jistič mechanismy, složitější řetězce volání HTTP jsou, složitější je implementovat strategii selhání na základě protokolu HTTP.

Ve skutečnosti pokud vaše interní mikroslužby komunikují vytvořením řetězců požadavků HTTP, jak je popsáno, může být argumentováno, že máte monolitickou aplikaci, ale založenou na protokolu HTTP mezi procesy namísto mechanismů komunikace v rámci procesu.

Proto za účelem vynucení autonomie mikroslužeb a mají lepší odolnost proti chybám, měli byste minimalizovat použití řetězců komunikace požadavku a odpovědi napříč mikroslužeb. Doporučujeme používat pouze asynchronní interakci pro komunikaci mezi mikroslužbami, a to buď pomocí asynchronní komunikace založené na událostech, nebo pomocí (asynchronního) dotazování HTTP nezávisle na původním cyklu požadavku a odpovědi HTTP.

Použití asynchronní komunikace je vysvětleno další podrobnosti dále v této příručce v [oddílech Asynchronní integrace mikroslužeb vynucuje autonomii mikroslužeb](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy) a [asynchronní komunikaci založenou na zprávě](asynchronous-message-based-communication.md).

## <a name="additional-resources"></a>Další zdroje

- **SZP** \
  <https://en.wikipedia.org/wiki/CAP_theorem>

- **Konečná konzistence** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Základní nátěr konzistence dat** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Martin Fowler. CQRS (oddělení odpovědnosti příkazu a dotazu)** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Zhmotněný pohled** \
  <https://docs.microsoft.com/azure/architecture/patterns/materialized-view>

- **Charles Erow. ACID vs. BASE: Přesouvání pH zpracování databázových transakcí** \
  <https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/>

- **Kompenzační transakce** \
  <https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction>

- **Udi Dahan. Služba orientovaná kompozice** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

>[!div class="step-by-step"]
>[Předchozí](logical-versus-physical-architecture.md)
>[další](identify-microservice-domain-model-boundaries.md)
