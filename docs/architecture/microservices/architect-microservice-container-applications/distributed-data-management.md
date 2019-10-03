---
title: Výzvy a řešení pro správu distribuovaných dat
description: Seznamte se s výzvami a řešeními pro správu distribuovaných dat v celém světě mikroslužeb.
ms.date: 09/20/2018
ms.openlocfilehash: c30de24591d5a73fd34087f34a69e9c7ed54cd35
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834448"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Výzvy a řešení pro správu distribuovaných dat

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Challenge \#1: jak definovat hranice každé mikroslužby

Definování hranice mikroslužeb je pravděpodobně první výzvou, kterou každý uživatel najde. Každá mikroslužba musí být součástí vaší aplikace a každá mikroslužba by měla být autonomní se všemi výhodami a výzvami, které přináší. Ale jak identifikujete tyto hranice?

Nejprve se musíte zaměřit na logické doménové modely aplikace a související data. Zkuste identifikovat oddělené ostrovy dat a různé kontexty v rámci stejné aplikace. Každý kontext může mít jiný obchodní jazyk (různé obchodní výrazy). Kontexty by se měly definovat a spravovat nezávisle. Pojmy a entity, které jsou používány v těchto různých kontextech, mohou být podobné podobným způsobem, ale je možné, že v určitém kontextu bude obchodní koncept s jedním účelem použit pro jiný účel v jiném kontextu a může mít i jiný název. Například uživatel může být uveden jako uživatel v kontextu identity nebo členství, jako zákazník v kontextu CRM, jako kupující v kontextu řazení a tak dále.

Způsob identifikace hranic mezi více kontexty aplikace s různou doménou pro každý kontext je přesně takový, jak můžete identifikovat hranice pro jednotlivé obchodní mikroslužby a související doménové modely a data. Při pokusu o odpojení mezi těmito mikroslužbami se vždycky pokusíte minimalizovat. V této příručce se dozvíte víc podrobností o této identifikaci a návrhu doménového modelu v oddílu, kde se později [identifikují hranice doménového modelu pro jednotlivé mikroslužby](identify-microservice-domain-model-boundaries.md) .

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Výzva \#2: jak vytvářet dotazy, které načítají data z několika mikroslužeb

Druhá výzva je způsob implementace dotazů, které načítají data z několika mikroslužeb, a současně neumožňuje komunikaci s konverzacemi s těmito mikroslužbami ze vzdálených klientských aplikací. Příkladem může být jedna obrazovka z mobilní aplikace, která potřebuje zobrazit informace o uživateli, které vlastní košík, katalog a identitu uživatelů. Dalším příkladem může být složitá sestava zahrnující mnoho tabulek umístěných v několika mikroslužbách. Správné řešení závisí na složitosti dotazů. Ale v každém případě budete potřebovat způsob, jak agregovat informace, pokud chcete zvýšit efektivitu komunikace systému. Nejoblíbenější řešení jsou následující.

**Brána API.** Pro jednoduchou agregaci dat z více mikroslužeb, které vlastní různé databáze, je doporučený přístup agregační mikroslužba označovaná jako brána rozhraní API. Je však nutné, abyste měli pozor na implementaci tohoto modelu, protože to může být sytič v systému a může porušovat princip autonomie mikroslužeb. Chcete-li zmírnit tuto možnost, můžete mít několik jemných bran rozhraní API, které se zaměřují na vertikální "řez" nebo obchodní oblast systému. Vzor brány rozhraní API je podrobněji vysvětlen v [části brána rozhraní API](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication) později.

**CQRS pomocí dotazů nebo čtení tabulek.** Dalším řešením pro agregaci dat z více mikroslužeb je [model materializované zobrazení](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). V tomto postupu vygenerujete předem (připravuje Denormalizovaná data před samotnými dotazy) a tabulku jen pro čtení s daty, která vlastní více mikroslužeb. Tabulka má formát, který je vhodný pro potřeby klientských aplikací.

Zvažte něco podobného jako na obrazovce mobilní aplikace. Pokud máte izolovanou databázi, můžete data pro tuto obrazovku vyžádat pomocí dotazu SQL, který provádí komplexní spojení zahrnující více tabulek. Pokud máte ale více databází a každá databáze vlastní jinou mikroslužbu, nemůžete tyto databáze zadat dotazem a vytvořit připojení SQL. Váš složitý dotaz se stává výzvou. Požadavek můžete vyřešit pomocí přístupu k CQRS – vytvoříte denormalizovanou tabulku v jiné databázi, která se používá jenom pro dotazy. Tabulka může být navržena speciálně pro data, která potřebujete pro složitý dotaz, s relací 1:1 mezi poli, které vyžaduje obrazovka vaší aplikace, a sloupci v tabulce dotazů. Může také sloužit pro účely vytváření sestav.

Tento přístup nejenom vyřeší původní problém (dotazování a spojování napříč mikroslužbami), ale také výrazně zvyšuje výkon ve srovnání se složitým spojením, protože už máte data, která aplikace potřebuje v tabulce dotazů. Samozřejmě použití CQRS (Command and Query Responsibility Segregation) (CQRS) s tabulkami dotaz/čtení znamená další vývojovou práci a vy budete muset zapracovat s konečnou konzistencí. Nicméně požadavky na výkon a vysokou škálovatelnost ve [scénářích spolupráce](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (nebo v případě konkurenčních scénářů v závislosti na bodu zobrazení) byste měli použít pro CQRS s více databázemi.

**"Studená data" v centrálních databázích.** U složitých sestav a dotazů, které nemusí vyžadovat data v reálném čase, se jedná o společný přístup k vyexportování "aktivních dat" (transakčních dat z mikroslužeb) jako "studená data" do rozsáhlých databází, které se používají jenom pro vytváření sestav. Tento centrální databázový systém může být systémem využívajícím velké objemy dat, jako je Hadoop, datový sklad, který je založený na Azure SQL Data Warehouse, nebo dokonce jenom jedna databáze SQL, která se používá jenom pro sestavy (Pokud se nejedná o problém s velikostí).

Mějte na paměti, že tato Centralizovaná databáze by se používala jenom pro dotazy a sestavy, které nepotřebují data v reálném čase. Původní aktualizace a transakce jako zdroj pravdy musí být ve vašich datech mikroslužeb. Způsob synchronizace dat by byl buď pomocí komunikace založené na událostech (popsaná v následujících částech), nebo pomocí dalších nástrojů pro import/export infrastruktury databáze. Pokud používáte komunikaci založenou na událostech, proces integrace by byl podobný způsobu, jakým šíříte data, jak je popsáno výše pro tabulky dotazů CQRS.

Pokud ale návrh vaší aplikace zahrnuje nepřetržitou agregaci informací z různých mikroslužeb pro složité dotazy, může to být příznakem špatného návrhu – mikroslužba by měla být izolovaná, jak je to možné, od ostatních mikroslužeb. (To nezahrnuje sestavy/analýzy, které vždy používají centrální databáze studených dat.) Příčinou tohoto problému často může být důvod, jak mikroslužby sloučit. Musíte vyvážit autonomii vývoje a nasazení každé mikroslužby se silnými závislostmi, soudržnosti a agregací dat.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Výzva \#3: jak dosáhnout konzistence napříč několika mikroslužbami

Jak bylo uvedeno dříve, data vlastněná jednotlivými mikroslužba jsou pro tuto mikroslužbu soukromá a dají se k ní dostat jenom pomocí jejího rozhraní API mikroslužeb. Proto se zobrazí výzva k implementaci koncových obchodních procesů a zachování konzistence napříč několika mikroslužbami.

Abychom mohli tento problém analyzovat, Podívejme se na příklad z [Referenční aplikace eShopOnContainers](https://aka.ms/eshoponcontainers). Mikroslužba katalogu uchovává informace o všech produktech, včetně ceny produktu. Mikroslužba košíku spravuje dočasná data o položkách produktu, které uživatelé přidávají do svých nákupních košíků, včetně ceny položek v době, kdy byly přidány do košíku. V případě aktualizace ceny produktu v katalogu by měla být tato cena aktualizována také v aktivních košíkech, které obsahují stejný produkt, a systém by měl pravděpodobně upozornit uživatele, že se změnila cena konkrétní položky od jejich přidání k košíku.

V hypotetické verzi monolitické této aplikace při změně ceny v tabulce Products by subsystém katalogu mohl jednoduše použít transakci kyseliny k aktualizaci aktuální ceny v tabulce koše.

V aplikacích založených na mikroslužbách ale tabulky produktů a koše jsou vlastněné příslušnými mikroslužbami. Žádná mikroslužba by nikdy neměla zahrnovat tabulky/úložiště vlastněné jinou mikroslužbou ve svých vlastních transakcích, a ne ani v přímých dotazech, jak je znázorněno na obrázku 4-9.

![Diagram znázorňující, že data databáze mikroslužeb nejde sdílet.](./media/distributed-data-management/indepentent-microservice-databases.png)

**Obrázek 4-9**. Mikroslužba nemůže získat přímý přístup k tabulce v jiné mikroslužbě.

Mikroslužba katalogu by neměla aktualizovat tabulku koše přímo, protože tabulka koše je vlastněna mikroslužbou košíku. Pro zajištění aktualizace mikroslužby koše by služba Cloud Service měla použít konečnou konzistenci, která je pravděpodobně založená na asynchronní komunikaci, jako jsou například integrační události (zpráva a komunikace na základě událostí). To je způsob, jakým referenční aplikace [eShopOnContainers](https://aka.ms/eshoponcontainers) tento typ konzistence provádí napříč mikroslužbami.

Jak je uvedeno v [věta Cap](https://en.wikipedia.org/wiki/CAP_theorem), musíte zvolit mezi vysokou konzistencí dostupnosti a kyselinou. Většina scénářů založených na mikroslužbách vyžaduje dostupnost a vysokou škálovatelnost na rozdíl od silné konzistence. Klíčové aplikace musí zůstat v provozu a vývojáři mohou obejít silnou konzistenci pomocí technik pro práci se slabou nebo konečnou konzistencí. Toto je přístup, který zabere Většina architektur založených na mikroslužbách.

Kromě toho se ve stylu KYSELosti nebo dvoufázové transakce potvrzení nemění jenom na princip mikroslužeb. Většina databází NoSQL (například Azure Cosmos DB, MongoDB atd.) nepodporuje dvoufázové transakce potvrzení, typické ve scénářích distribuovaných databází. Zachování konzistence dat napříč službami a databázemi je ale nezbytné. Tato výzva se také týká otázky, jak rozšířit změny napříč více mikroslužbami, pokud je potřeba, aby určitá data byla redundantní, například když potřebujete mít název nebo popis produktu v katalogu mikroslužeb a v koši. mikroslužeb.

Dobrým řešením tohoto problému je použití konečné konzistence mezi mikroslužbami propojenými prostřednictvím komunikace řízené událostmi a systémem pro publikování a odběr. Tato témata jsou popsaná v části [asynchronní komunikace řízená událostmi](asynchronous-message-based-communication.md#asynchronous-event-driven-communication) dále v této příručce.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Výzva @no__t – 04: jak navrhovat komunikaci napříč hranicemi mikroslužeb

Komunikace mezi hranicemi mikroslužeb je skutečnou výzvou. V tomto kontextu komunikace neodkazuje na protokol, který byste měli použít (HTTP, REST, AMQP, zasílání zpráv a tak dále). Místo toho řeší, který styl komunikace byste měli použít, a zejména to, jak by měly být vaše mikroslužby. V závislosti na úrovni spojení, kdy dojde k chybě, se dopad této chyby na váš systém výrazně liší.

V distribuovaném systému jako aplikace založené na mikroslužbách, a díky tomu mnoho artefaktů, které se pohybují kolem a s distribuovanými službami na mnoha serverech nebo hostitelích, budou součásti nakonec neúspěšné. Dojde k částečnému selhání a dokonce i většímu výpadku, takže je potřeba navrhnout mikroslužby a komunikaci napříč nimi, aby se v tomto typu distribuovaného systému stala běžnými riziky.

Oblíbeným přístupem je implementace mikroslužeb založených na protokolu HTTP (REST) z důvodu jejich jednoduchosti. Přístup založený na protokolu HTTP je dokonale přijatelný; Tento problém se týká toho, jak ho používáte. Pokud používáte požadavky a odpovědi HTTP pouze k interakci s mikroslužbami z klientských aplikací nebo z bran rozhraní API, je to přesně. Pokud ale vytvoříte dlouhé řetězce synchronních volání HTTP napříč mikroslužbami, komunikujete přes jejich hranice, jako kdyby mikroslužby byly objekty v aplikaci monolitické, a nakonec dojde k potížím s aplikací.

Představte si například, že vaše klientská aplikace provede volání HTTP API na jednotlivé mikroslužby, jako je objednávání mikroslužeb. Pokud mikroslužba řazení zase volá další mikroslužby pomocí protokolu HTTP v rámci stejného cyklu žádosti a odpověď, vytváříte řetěz volání HTTP. Zpočátku to může být na dobrém měřeno. Existují však důležité body, které je potřeba vzít v úvahu při přechodu k této cestě:

- Blokování a nízký výkon. V důsledku synchronní povahy HTTP neobdrží původní požadavek odpověď, dokud nejsou dokončená všechna interní volání HTTP. Představte si, jestli se počet těchto volání významně zvyšuje a zároveň je blokované jedno ze zprostředkujících volání HTTP do mikroslužeb. Výsledkem je, že výkon bude ovlivněn a celková škálovatelnost bude exponenciálně ovlivněna při zvýšení počtu dalších požadavků HTTP.

- Napojuje mikroslužby pomocí protokolu HTTP. Obchodní mikroslužby by se neměly spojit s jinými mikroslužbami v podniku. V ideálním případě by neměl "znát" existenci ostatních mikroslužeb. Pokud vaše aplikace spoléhá na přihlašování mikroslužeb, jako v příkladu, bude téměř nemožné dosáhnout autonomie na mikroslužby.

- Selhání v žádné jedné mikroslužbě. Pokud jste implementovali řetěz mikroslužeb propojených voláními HTTP, když kterákoli z mikroslužeb selže (a nakonec dojde k selhání), celý řetěz mikroslužeb se nezdaří. Systém založený na mikroslužbách by měl být navržený tak, aby během částečných selhání pokračoval i v práci. I když implementujete klientskou logiku, která používá opakování pomocí exponenciálních mechanismů omezení rychlosti nebo přestávek okruhů, složitější řetězce volání HTTP jsou složitější, takže je implementace strategie selhání založená na protokolu HTTP.

Ve skutečnosti platí, že pokud vaše interní mikroslužby komunikují vytvořením řetězů požadavků HTTP, jak je popsáno, může být namítáno, že máte aplikaci monolitické, ale jednu na základě HTTP mezi procesy namísto mechanismů komunikace uvnitř procesu.

Aby bylo možné vyhovět autonomii mikroslužeb a mít lepší odolnost, měli byste minimalizovat použití řetězů komunikace mezi žádostmi a odpověďmi napříč mikroslužbami. Doporučuje se použít jenom asynchronní interakci pro komunikaci mezi mikroslužbami, a to buď pomocí asynchronní komunikace založené na zprávách a událostech, nebo pomocí (asynchronního) dotazování HTTP nezávisle na původní žádosti HTTP/ cyklus odezvy.

Použití asynchronní komunikace je vysvětleno dalšími podrobnostmi dále v této příručce v části [asynchronní integrace mikroslužeb vynutila samostatnou](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy) komunikaci mikroslužeb a [asynchronní komunikaci na základě zpráv](asynchronous-message-based-communication.md).

## <a name="additional-resources"></a>Další zdroje informací:

- **Cap věta** \
  <https://en.wikipedia.org/wiki/CAP_theorem>

- Konečná **konzistence**@no__t – 1
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Úvod do konzistence dat** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Martin Fowlera. CQRS (CQRS (Command and Query Responsibility Segregation))**  \
  <https://martinfowler.com/bliki/CQRS.html>

- **Materializované zobrazení** \
  <https://docs.microsoft.com/azure/architecture/patterns/materialized-view>

- **Charles řádek Kyselina vs. BASE: posunování pH zpracování transakcí databáze** \
  <https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/>

- **Kompenzační transakce** \
  <https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction>

- **UDI Dahan. Složení orientované na služby** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

>[!div class="step-by-step"]
>[Předchozí](logical-versus-physical-architecture.md)@no__t – 1 –[Další](identify-microservice-domain-model-boundaries.md)
