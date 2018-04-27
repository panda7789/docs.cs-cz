---
title: Problémy a řešení pro správu distribuovaných dat
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Problémy a řešení pro správu distribuovaných dat
keywords: Docker, Mikroslužeb, ASP.NET, kontejneru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a26f4243acee52e493a10f13ff18899823fd03ba
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Problémy a řešení pro správu distribuovaných dat

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Výzvy \#1: definování hranice každý mikroslužbu

Definování hranice mikroslužbu je pravděpodobně v prvním kroku, které každý, kdo zaznamená. Každý mikroslužbu musí být část vaší aplikace a každý mikroslužbu musí být autonomního všechny výhody a problémy, které se přenese tak. Ale jak můžete určit tyto hranice?

Nejdřív je potřeba zaměřit se na logické domény modely aplikace a související data. Musí se pokusí identifikovat odpojeného ostrovy dat a různých kontextů stejné aplikace. Každý kontext může mít jiné organizační jazyk (různých obchodních podmínky). Kontexty by měl být definovaný a spravovat nezávisle. Podmínky a entit používaných v těchto různých kontextech zvukových podobné může, ale může zjistit, že v určitém kontextu, obchodní koncept s jedním používá pro jiný účel v jiném kontextu a může mít i jiný název. Uživatel například může označuje jako uživatel v rámci identity nebo členství jako zákazníka v kontextu CRM, jako kupujících v kontextu řazení a tak dále.

Způsob, jak identifikovat hranice mezi více kontexty aplikaci s jinou doménu pro každý kontext je přesně identifikaci hranice pro každou obchodní mikroslužbu a jeho souvisejících modelu domény a data. Vždy pokusí minimalizovat párování mezi těmito mikroslužeb. Tato příručka obsahuje větší podrobnosti o tomto návrhu modelu identifikace a domény v části [identifikace modelu domény hranice pro každou mikroslužbu](#identifying-domain-model-boundaries-for-each-microservice) později.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Výzvy \#2: vytvoření dotazů, které načtení dat z několika mikroslužeb

Druhá výzva je postup implementovat dotazy, které načtení dat z několika mikroslužeb, aniž by chatty komunikace na mikroslužeb od aplikace vzdáleného klienta. Příkladem může být jeden obrazovky z mobilní aplikace, která potřebuje zobrazit informace o uživateli, který je vlastněn košík, katalogu a mikroslužeb identity uživatele. Dalším příkladem může být složité sestavy zahrnující mnoho tabulek, které jsou umístěné v několika mikroslužeb. Správné řešení závisí na složitosti dotazy. Ale v žádném případě musíte způsob, jak agregační informace, pokud chcete zlepšit efektivitu při komunikaci vašeho systému. Nejčastěji používané řešení jsou následující.

**Brána rozhraní API**. Za účelem agregace jednoduché data z více mikroslužeb, který vlastní různých databází doporučuje se agregaci mikroslužbu označuje jako bránu rozhraní API. Ale musíte pečlivě o implementaci tohoto vzoru, protože v systému může být bod potlačení a ho můžete porušují Princip mikroslužbu nezávislé. Pro zmírnění této možnosti, můžete mít více bran pokutu podrobných rozhraní API každý jeden zaměřené na svislé "řez" nebo obchodní oblast systému. Vzor Brána rozhraní API je vysvětlené podrobněji v příslušné části na pomocí později bránu rozhraní API.

**CQRS s tabulkami dotazu nebo čtení**. Jiné řešení pro agregaci dat z více mikroslužeb je [Materializována zobrazení vzor](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). V tomto přístupu můžete vygenerovat, předem (připravit nenormalizované data, před dojít skutečné dotazy), jen pro čtení tabulku s daty, který je vlastněn více mikroslužeb. Tabulka má formát vhodné potřebám klientské aplikace.

Zvažte něco podobného jako na obrazovce pro mobilní aplikace. Pokud máte jednu databázi, může být společně vyžádá data pro tuto obrazovku pomocí dotaz SQL, který provádí komplexní spojení zahrnující více tabulek. Ale pokud máte více databází a jiné mikroslužbu vlastní každou databázi, nelze dotaz tyto databáze a vytvořit připojení k SQL. Komplexní dotazu se změní na výzvu. Můžete vyřešit požadavek CQRS přístup – vytvořit nenormalizované tabulku v jiné databázi, která se používá pouze pro dotazy. V tabulce můžete určený speciálně pro data, která je nutné pro komplexní dotaz s relací mezi poli potřebují obrazovky vaší aplikace a sloupců v tabulce dotazu. Také může fungovat pro účely vytváření sestav.

Tento přístup nejen řeší původní problém (jak dotaz a spojení mezi mikroslužeb); také zlepšuje výkon výrazně ve srovnání s komplexní spojení, vzhledem k tomu, že již máte data, která aplikace je v tabulce dotazu. Samozřejmě příkazů a dotazů odpovědnost oddělení (CQRS) pomocí dotazu nebo čtení tabulky znamená další vývojové práci a budete muset použít konzistence typu případné. Nicméně požadavky na výkon a škálovatelnost vysoké v [spolupráce scénáře](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (nebo konkurenční scénářů, v závislosti na hlediska) je, kde byste měli použít CQRS s více databází.

**"Pomaleji přístupná data" centrální databáze**. Pro komplexní sestavy a dotazy, které nemusejí být nutné dat v reálném čase je běžný postup exportovat vaší "horkého data" (transakční data z mikroslužeb) jako "pomaleji přístupná data" do velké databáze, které se používají pouze pro vytváření sestav. Tento systém centrální databáze může být systém na základě velkých objemů dat, jako jsou Hadoop, datového skladu jako jeden založené na Azure SQL Data Warehouse nebo i jedné databáze SQL (Pokud je velikost nebude problém) používá pouze pro sestavy.

Uvědomte si, že tato centralizované databáze budou použita pouze pro dotazy a sestavy, které není nutné data v reálném čase. Původní aktualizace a transakce, jako zdroj pravdivosti, musí být ve vašich datech mikroslužeb. Způsob, jakým byste synchronizaci dat bude pomocí komunikace založeného na událostech (popsané v následujících částech) nebo pomocí jiných nástrojů databáze infrastruktury importu a exportu. Pokud použijete komunikaci založeného na událostech, by tento proces integrace podobným způsobem, jak je popsáno výše pro CQRS dotazu na tabulky se rozšíří data.

Ale pokud váš návrh aplikace zahrnuje neustále agregující informace z více mikroslužeb pro složité dotazy, může být příznakem chybný návrhu – mikroslužbu by měl být jako izolované nejblíže z jiných mikroslužeb. (Nezahrnuje to sestavy nebo analýz, které se vždycky měli použít centrální databáze studený data.) Často má tento problém může být důvod sloučit mikroslužeb. Musíte vyvážit samostatnost vývoj a nasazení každé mikroslužbu s silné závislosti, soudržnost a agregace dat.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Výzvy \#3: jak k zajištění konzistence mezi více mikroslužeb

Jak jsme uvedli dříve, data vlastníkem jednotlivých mikroslužbu soukromý této mikroslužbu a může otevřít pouze pomocí jeho mikroslužbu rozhraní API. Zobrazí výzvu je proto, jak implementovat začátku do konce obchodních procesů při zachování konzistence napříč více mikroslužeb.

K analýze tento problém, podíváme se na příklad z [eShopOnContainers odkazovat aplikace](http://aka.ms/eshoponcontainers). Mikroslužbu katalogu uchovává informace o všech produktů, včetně jejich uložených úroveň. Mikroslužbu řazení spravuje objednávky a musí ověřit, že nové pořadí nepřekročí stock produktu katalog k dispozici. (Nebo scénář mohou zahrnovat logiky, která zpracovává produkty doobjednáno.) V hypotetický monolitický verze této aplikace řazení subsystému jednoduše použít transakci ACID kontrolovat dostupného, vytvořit pořadí v tabulce objednávky, a aktualizovat dostupné stock v tabulce produkty.

Ale v mikroslužeb – na základě aplikací, pořadí a produktu tabulky jsou vlastněny jejich odpovídajících mikroslužeb. Žádné mikroslužbu někdy obsahovat databází, které vlastní jiný mikroslužbu ve vlastní transakce nebo dotazy, jak ukazuje obrázek 4 – 9.

![](./media/image9.PNG)

**Obrázek 4 – 9**. Mikroslužbu nemají přímý přístup do tabulky v jiné mikroslužbu

Mikroslužbu řazení nesmí přímo, aktualizovat tabulky produktů, protože vlastníkem tabulky produktů je mikroslužbu katalogu. Chcete-li provést aktualizaci katalogu mikroslužbu, měli mikroslužbu řazení pouze někdy použít asynchronní komunikaci například integrace událostí (zpráv a komunikaci na bázi události). Jedná se jak [eShopOnContainers](http://aka.ms/eshoponcontainers) aplikace referenční provede tento typ aktualizace.

Podle [věta CAP](https://en.wikipedia.org/wiki/CAP_theorem), budete muset zvolit dostupnosti a ACID silnou konzistenci. Většina scénářů mikroslužbu na základě poptávky dostupnost a škálovatelnost vysoké a silnou konzistenci. Kritické aplikace musí zůstat nahoru a spuštěná a vývojářům můžete obejít silnou konzistenci pomocí techniky pro práci s slabá nebo případné konzistence. Jedná se o postup provedenou většina architektury na základě mikroslužby.

Kromě toho kyseliny stylu nebo dvojfázového zápisu transakce nejsou právě proti mikroslužeb zásad; Většina databáze NoSQL (např. Azure Cosmos DB, MongoDB atd.) nepodporují dvojfázového zápisu transakce. Udržování dat konzistence napříč služby a databáze je však nezbytné. Tento problém souvisí otázku o tom, jak rozšířit změny napříč více mikroslužeb, když některá data, je potřeba redundantní – například když potřebujete mít název nebo popis v katalogu mikroslužbu a košíku produktu mikroslužby.

Dobrým řešením tohoto problému je použití konzistence typu případné mezi mikroslužeb kloubové prostřednictvím událostmi řízené komunikace a systémem publikování a odběru. Tato témata jsou popsané v části [asynchronní komunikaci událostmi řízené](#async_event_driven_communication) dál v této příručce.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Výzvy \#4: navrhování komunikaci napříč hranicemi mikroslužbu

Komunikace v rámci mikroslužbu hranice je skutečné výzvu. V tomto kontextu komunikace neodkazuje na co protokolu můžete využít (HTTP a REST, AMQP, zasílání zpráv a tak dále). Místo toho řeší, jaké komunikace styl, měli byste použít, a jak párované vaší mikroslužeb by se měly používat. V závislosti na úrovni párování když dojde k selhání, dopad tohoto selhání v systému se bude lišit výrazně.

V distribuované systému jako aplikace na základě mikroslužeb, s tolika artefakty pohyb a distribuované služby napříč mnoha servery nebo hostitele selžou nakonec součásti. Částečné selhání a i větší výpadky vzhledem k tomu, takže je třeba navrhnout vaše mikroslužeb a komunikace mezi nimi zohledněním rizika běžné u tohoto typu distribuovaného systému.

Oblíbené přístupem je implementace protokolu HTTP (REST) – na základě mikroslužeb z důvodu jejich jednoduchost. Přístup založený na protokolu HTTP je zcela přijatelné; Zde problém se týká jeho použití. Pokud použijete jenom k interakci s vaší mikroslužeb z klientské aplikace nebo z rozhraní API brány požadavky a odpovědi HTTP, který je v pořádku. Ale pokud vytvoříte dlouho řetězy synchronní volání protokolu HTTP mezi mikroslužeb, komunikaci přes jejich hranice, jako kdyby mikroslužeb objekty monolitický aplikace, spustí se vaše aplikace nakonec k potížím.

Představte si například, že klientské aplikace provede volání rozhraní API HTTP jednotlivých mikroslužbu jako mikroslužbu řazení. Pokud mikroslužbu řazení volá další cyklus mikroslužeb pomocí protokolu HTTP v rámci stejné požadavků a odpovědí, vytváříte řetěz volání protokolu HTTP. Ho může zvukových přiměřené původně. Existují však body důležité zvážit při směrem dolů tuto cestu:

-   Blokování a nízkou výkon. Z důvodu synchronní povaha HTTP nebude původní žádost získat odpověď až do dokončení všech interní volání protokolu HTTP. Představte si, pokud počet těchto volání výrazně zvyšuje a ve stejnou dobu, kdy jeden zprostředkující HTTP volá, aby se mikroslužbu je blokovaná. Výsledkem je, že ovlivněn výkon a celkovou škálovatelnost exponenciálnímu ovlivní jako další zvýšení požadavky HTTP.

-   Párování mikroslužeb s protokolem HTTP. Obchodní mikroslužeb by neměl kombinaci s mikroslužeb jiné firmy. V ideálním případě by neměl "znají" o existenci jiných mikroslužeb. Pokud vaše aplikace využívá spojovacích mikroslužeb jako v příkladu, bude téměř znemožněno dosažení nezávislé na mikroslužby.

-   Došlo k selhání všech jeden mikroslužby. Pokud jste implementovali řetěz mikroslužeb propojeny prostřednictvím volání protokolu HTTP, některé mikroslužeb nezdaří (a nakonec se nezdaří) celý řetězec mikroslužeb se nezdaří. Chcete-li pokračovat v práci a také možné při částečné selhání by se měly navrhovat systému mikroslužby. I v případě, že budete implementovat logiku klienta, která používá opakování exponenciálního omezení rychlosti nebo jistič mechanismy, další volání řetězy komplexní HTTP jsou, tím složitější je ho implementovat strategie selhání založené na protokolu HTTP.

Ve skutečnosti Pokud vaše interní mikroslužeb komunikují vytvořením řetězy požadavků HTTP, jak je popsáno, může být uvedl, že je k dispozici monolitický aplikace, ale jeden založené na protokolu HTTP mezi procesy místo intraprocess komunikační mechanizmy.

Proto aby bylo možné vynutit mikroslužbu nezávislé a mají lepší odolnost proti chybám, měli byste minimalizovat použití řetězy požadavků a odpovědí komunikace mezi mikroslužeb. Doporučujeme používat pouze asynchronní interakce pro komunikaci mezi mikroslužbu, buď pomocí asynchronní zpráva - a na základě událostí komunikace, nebo pomocí protokolu HTTP dotazování nezávisle na původní cyklus požadavků a odpovědí HTTP.

Další podrobnosti o později v tomto průvodci v částech je popsané použití asynchronní komunikaci [asynchronní mikroslužbu integrace vynucuje nezávislé na mikroslužbu](#asynchronous-microservice-integration-enforce-microservices-autonomy) a [asynchronního komunikace na základě zpráv](#asynchronous-message-based-communication).

## <a name="additional-resources"></a>Další zdroje

-   **Zakončení věta**
    [*https://en.wikipedia.org/wiki/CAP\_věta*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **Konzistence typu případné**
    [*https://en.wikipedia.org/wiki/Eventual\_konzistence*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Úvod do konzistence dat**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Martin Fowler. CQRS (příkaz a dotaz odpovědnost oddělení)**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Vyhodnocená zobrazení**
    [*https://docs.microsoft.com/azure/architecture/patterns/materialized-view*](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

-   **Charlese řádek. ACID vs. Základní: Parametr Shifting zpracování transakcí databáze**
    [*http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/*](http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/)

-   **Kompenzace transakce**
    [*https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction*](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

-   **Udi Dahan. Služba zaměřené na konkrétní složení**
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)


>[!div class="step-by-step"]
[Předchozí] (logical-versus-physical-architecture.md) [Další] (identify-microservice-domain-model-boundaries.md)
