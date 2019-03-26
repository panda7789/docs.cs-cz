---
title: Výzvy a řešení správy distribuovaných dat
description: Zjistěte, jaké jsou problémy a řešení správy distribuovaných dat ve světě mikroslužeb.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: f92410f2742ec1cbcb08d13614700eab348aa646
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463368"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Výzvy a řešení správy distribuovaných dat

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Výzvy \#1: Definování hranice jednotlivých mikroslužeb

Definování hranic mikroslužby je pravděpodobně první výzvy, které všem uživatelům, zaznamená. Každá mikroslužba musí být část vaší aplikace a každá mikroslužba by měla být autonomní s všechny výhody i výzvy, které se přenáší. Ale jak máte identifikovat tyto hranice?

Nejprve budete muset zaměřit na logické doménových modelů a související data aplikace. Pokuste se identifikovat oddělující ostrovy data a různých kontextech v rámci stejné aplikace. Každý kontext může mít různé obchodní jazyk (různé obchodní podmínky). Kontexty by měl definovány a spravovat nezávisle. Podmínky a entity, které se používají v těchto různých kontextech může zní podobně, ale může zjistit, že v konkrétním kontextu, obchodní konceptu s jedním používá pro jiný účel v jiném kontextu a dokonce může mít jiný název. Uživatel například může odkazovat jako uživatel v rámci identity nebo členství zákazníky v rámci CRM jako odběratel v pořadí kontextu a tak dále.

Způsob identifikace hranic mezi několika kontextech aplikaci s jinou doménu pro každý kontext je přesně, jak můžete identifikovat hranice pro každou obchodní mikroslužeb a související doménový model a data. Vždy snaží minimalizovat párování mezi těmito mikroslužeb. Tato příručka obsahuje další podrobnosti o tento návrh modelu identifikace a domény v části [identifikace hranic mezi modelem a doménou u jednotlivých mikroslužeb](identify-microservice-domain-model-boundaries.md) později.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Výzvy \#2: Jak vytvořit dotazy, které načítají data z několika mikroslužeb

Druhá výzva je implementace dotazů, které načítají data z několika mikroslužeb, při obcházení košatá komunikace na mikroslužby od aplikace vzdáleného klienta. Příkladem může být na jedné obrazovce z mobilní aplikace, které se musí zobrazovat informace o uživateli, který je vlastněn nákupní košík, katalogu a uživatele identit mikroslužeb. Dalším příkladem může být složité sestavy zahrnující mnoho tabulek v několika mikroslužeb. Má to pravé řešení závisí na složitosti dotazů. Ale v každém případě budete potřebovat způsob, jak souhrnné informace, pokud chcete zvýšit efektivitu v rámci komunikace vašeho systému. Nejoblíbenější řešení jsou uvedeny níže.

**Brána rozhraní API.** Doporučený postup pro jednoduchou datovou agregaci z několika mikroslužeb, která vlastníte různých databázích, je agregaci mikroslužeb označovány jako bránu rozhraní API. Musíte ale buďte opatrní při implementaci tohoto modelu, protože bod potlačení může být ve vašem systému a jeho porušovat zásady autonomie mikroslužeb. Ke zmírnění tuto možnost, můžete mít více bran rozhraní API pokutu grained každý jeden zaměření na svislé "řez" nebo obchodní oblast systému. Vzor brány rozhraní API je vysvětleno podrobněji [Brána rozhraní API části](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication) později.

**CQRS s tabulkami dotazování nebo čtení.** Druhým řešením pro agregaci dat z několika mikroslužeb je [modelu Materializovaného zobrazení](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). V takovém případě můžete vygenerovat, předem (předtím, než skutečný dotazy stát, Příprava Nenormalizovaná data), jen pro čtení tabulky s daty, který je vlastněn více mikroslužeb. Tabulka obsahuje formátu podle potřeb klientské aplikace.

Vezměte v úvahu něco jako na obrazovce pro mobilní aplikace. Pokud máte jednu databázi, může být společně načítal data pro tuto obrazovku pomocí dotazu SQL, která provádí komplexní spojením zahrnujícím více tabulek. Ale pokud máte více databází a každá databáze není ve vlastnictví různých mikroslužeb, nelze dotazovat tyto databáze a vytvořit připojení k SQL. Komplexní dotaz stává náročné. Vyřešíte požadavek použití přístupu CQRS – vytvořit tabulku Nenormalizovaná v jiné databázi, který se používá jenom pro dotazy. V tabulce můžete určený speciálně pro data, která budete potřebovat pro komplexní dotaz s relací 1: 1 mezi poli vyžadované vaší aplikace obrazovky a sloupce v tabulce dotazu. Současně může sloužit ke generování sestav.

Tento přístup nejen řeší původní problém (jak dotazu a spojení mezi mikroslužeb), ale také zlepšuje výkon výrazně ve srovnání s komplexní spojení, protože už máte data, která aplikace potřebuje v tabulce dotazu. Samozřejmě pomocí dotazů/čtení tabulek zodpovědnosti příkazů a dotazů oddělení (CQRS) znamená, že další vývojové práce a budete muset zapojte konečnou konzistenci. Nicméně požadavky na výkon a vysokou škálovatelnost v [spolupráci scénáře](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (nebo konkurenční scénáře, v závislosti na pohledu) jsou, kde byste měli použít modelu CQRS s více databází.

**"Studených dat" v centrální databáze.** Pro složitější sestavy a dotazy, které nemusí potřebovat data v reálném čase, běžným přístupem je exportovat vaší "horkými data" (transakční data z mikroslužeb) jako "studených"dat do velké databáze, které se používají pouze pro vytváření sestav. Může být centrální databázový systém na systém založený na velké objemy dat, jako jsou Hadoop, datového skladu, jako je na Azure SQL Data Warehouse, nebo dokonce izolované databáze SQL, který se používá jen pro sestavy (Pokud je velikost nesmí být problém).

Uvědomte si, že tento centralizované databázi se použije pouze pro dotazy a sestavy, které nepotřebují dat v reálném čase. Původní aktualizace a transakcí, jako zdroj pravdivých informací, musí být ve vašich datech mikroslužeb. Způsob, jakým by synchronizovat data by pomocí komunikace založená na událostech (popsané v další části) nebo pomocí jiných nástrojů infrastruktury import/export databáze. Pokud používáte komunikace založená na událostech, tento proces integrace by podobným způsobem, jak je popsáno výše u tabulek dotaz modelu CQRS se šířit data.

Ale pokud návrhu aplikace zahrnuje neustále agregování informací z několika mikroslužeb pro složité dotazy, může být příznakem chybný návrhu – mikroslužba by měla být izolaci jako z jiných mikroslužeb. (Nezahrnuje sestav a analýzu, která vždy používejte studeného data centrální databáze.) Často potíže pravděpodobně z důvodu sloučit mikroslužeb. Je potřeba vyrovnávat autonomie vývoj a nasazení jednotlivých mikroslužeb s silné závislosti, soudržnosti a agregace dat.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Výzvy \#3: Jak dosáhnout konzistence napříč různými mikroslužbami

Jak bylo uvedeno dříve, data vlastníkem jednotlivých mikroslužeb je privátní pro tento mikroslužeb a je přístupný pouze pomocí jeho mikroslužeb rozhraní API. Jak implementovat začátku do konce obchodních procesů při zachování konzistence napříč několika mikroslužeb je proto zobrazí výzvu.

Pokud chcete tento problém analyzovat, Podívejme se na příklad z [aplikaci eShopOnContainers odkazovat aplikace](https://aka.ms/eshoponcontainers). Mikroslužby katalogu uchovává informace o všech produktů, včetně cena produktu. Nákupní košík mikroslužeb spravuje o položky produktu, kteří uživatelé budou přidávat do své nákupní košíky, dočasná data, která zahrnuje cena položky v době, kdy byly přidány do košíku. Při aktualizaci ceny produktu v katalogu Tato cena by měl aktualizované taky v aktivní koše, které obsahují stejné produktu a systém by měl pravděpodobně upozornit uživatele, informacemi o tom, že cenou určité položky změnila jejich přidání do nákupního košíku.

Hypotetický monolitické verze této aplikace: Pokud cenových změn v tabulce produkty subsystému katalogu jednoduše použít transakci ACID aktualizovat aktuální ceny v tabulce Nákupní košík.

Však v aplikacích založených na mikroslužbách tabulek Product a nákupním košíku jsou vlastněny jejich odpovídajících mikroslužeb. Žádné mikroslužeb by měl obsahovat dříve vlastněn jinou mikroslužeb v jeho vlastní transakce, dokonce ani v přímých dotazů, tabulek a ukládání, jak ukazuje obrázek 4 – 9.

![Mikroslužby nemá přímý přístup k tabulce v jiném mikroslužeb, musí být konečné konzistence používá k synchronizaci dat.](./media/image9.png)

**Obrázek 4 – 9**. Mikroslužby nemá přímý přístup k tabulce v jiném mikroslužeb

Mikroslužeb katalogu by neměla aktualizovat tabulku nákupní košík přímo, protože tabulce Nákupní košík je vlastněná mikroslužeb nákupní košík. Mikroslužby katalogu provést malou úpravu mikroslužeb nákupní košík, měli by používat konečné konzistence pravděpodobně podle asynchronní komunikace, jako je například integrace událostí (zpráv a komunikaci na bázi události). Toto je způsob, jakým [aplikaci eShopOnContainers](https://aka.ms/eshoponcontainers) referenční aplikace provádí tento typ konzistence napříč mikroslužeb.

Jak je uvedeno ve [věty](https://en.wikipedia.org/wiki/CAP_theorem), je nutné zvolit mezi dostupností a odpovídající zásadám ACID silnou konzistenci. Většina scénářů založených na mikroslužbách poptávky, dostupnosti a vysokou škálovatelnost na rozdíl od silné konzistence. Důležité podnikové aplikace musí zůstat nahoru a běží a vývojáři můžete alternativně vyřešit silná konzistence pomocí techniky pro práci s slabá nebo konečné konzistence. Jedná se o postup provedenou většina architektur založených na mikroslužbách.

Kromě toho kyseliny – vizuální styl nebo dvoufázového potvrzení transakce, je právě proti principů mikroslužeb; Většina databází NoSQL (např. služby Azure Cosmos DB, MongoDB atd.) nepodporují dvoufázového potvrzení transakce, typické v situacích distribuovaných databází. Zachovat data konzistence napříč službami a databáze je však nezbytné. Tento problém souvisí na otázku, jak při určitých dat musí být redundantní šíří změny mezi různými mikroslužbami – například když potřebujete mít název nebo popis v katalogu mikroslužeb a košíku produktu mikroslužby.

Dobrým řešením tohoto problému je použít konečnou konzistenci mezi mikroslužbami kloubové prostřednictvím komunikace založená na událostech a systémem publikování a odběr. Tato témata jsou popsané v části [asynchronní komunikace založená na událostech](asynchronous-message-based-communication.md#asynchronous-event-driven-communication) dále v tomto průvodci.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Výzvy \#4: Postup návrhu komunikace mezi hranic mikroslužby

Komunikace v rámci mikroslužeb je hranice skutečnou výzvou. V tomto kontextu komunikace neodkazuje na co je protokol by měl používat (HTTP a REST, AMQP, zasílání zpráv a tak dále). Místo toho adresy byste měli použít styl komunikace a způsob propojených mikroslužby by se měly používat. V závislosti na úrovni párování když dojde k chybě, dopad tohoto selhání v systému bude výrazně lišit.

V distribuovaném systému jako aplikace založená na mikroslužbách, s tolika artefakty přesouvat a službami distribuované napříč mnoha servery nebo hostitele bude nakonec selže komponenty. Částečného selhání a ještě větší výpadků a se vyskytnou v případě, je potřeba navrhnout mikroslužby a komunikace mezi nimi zvážení běžné rizik u tohoto typu distribuovaného systému.

Oblíbené přístup je k implementaci mikroslužeb založených na protokolu HTTP REST, z důvodu jejich jednoduchost. Přístup založený na protokolu HTTP, je zcela přijatelné; Tady problém se týká jak je používáte. Pokud použijete jenom k interakci s klientskými aplikacemi nebo z brány rozhraní API mikroslužby požadavky a odpovědi HTTP, který je v pořádku. Pokud však vytvoříte dlouhé řetězce o synchronních voláních HTTP přes mikroslužeb, komunikaci přes jejich hranice, jako kdyby byly objekty monolitické aplikace mikroslužeb aplikace bude nakonec potížím.

Představte si například, že klientská aplikace provede volání rozhraní API HTTP jednotlivá mikroslužba jako jsou mikroslužby řazení. Pokud řazení mikroslužeb volá další cyklus mikroslužeb pomocí protokolu HTTP v rámci stejné žádostí a odpovědí, vytváříte řetěz volání HTTP. To může být zvukové přiměřené původně. Existují však důležité body ke zvážení při směrem dolů tuto cestu:

- Blokování a nízký výkon. Kvůli synchronní povaze HTTP nebude původní požadavek získat odpověď, dokud se nedokončí všechny vnitřní volání HTTP. Představte si, pokud počet těchto volání výrazně zvyšuje a ve stejnou dobu jeden zprostředkující HTTP volání pro mikroslužby je blokován. Výsledkem je, že je dopad na výkon a celkovou škálovatelnost exponenciálně ovlivní jako další zvýšení požadavků HTTP.

- Mikroslužby párování s protokolem HTTP. Mikroslužby firmy by neměl být vázány na jiné firmy mikroslužeb. V ideálním případě by neměla "ví" o existenci další mikroslužeb. Pokud vaše aplikace závisí na párování mikroslužeb jako v příkladu, bude autonomie jednotlivých mikroslužbách dosáhnout téměř nemožné.

- Selhání v jakékoli jednu mikroslužbu. Pokud jste implementovali řetěz mikroslužeb propojené volání HTTP, pokud některý z mikroslužeb selže (a nakonec se nezdaří) celý řetězec mikroslužeb se nezdaří. Chcete-li pokračovat v práci a také možné během částečné selhání by se měly navrhovat systému založených na mikroslužbách. I v případě, že budete implementovat logiku klienta, která používá opakování s exponenciální regresí nebo mechanismy jistič, další volání řetězy komplexní HTTP jsou, tím složitější je k implementaci strategie selhání založené na protokolu HTTP.

Ve skutečnosti pokud interní mikroslužby jsou komunikaci tak, že vytvoříte řetězy požadavků protokolu HTTP, jak je popsáno, může být uvedl, že máte u monolitické aplikace, ale jeden založené na protokolu HTTP mezi procesy místo uvnitř procesu komunikačních mechanizmů.

Pokud chcete vynutit autonomie mikroslužeb a mít lepší odolnost proti chybám, proto byste minimalizovat použití řetězy komunikace požadavku nebo odpovědi napříč mikroslužeb. Doporučujeme používat pouze asynchronní interakce pro komunikaci mezi virtuálními sítěmi mikroslužeb pomocí asynchronních zpráv a události – komunikace na základě nebo s použitím (asynchronního) dotazování HTTP bez ohledu na jejich původní požadavek protokolu HTTP / cyklus odpovědi.

Použití asynchronní komunikace je vysvětlen později v tomto průvodci v části Další podrobnosti o [integrace asynchronní mikroslužeb vynucuje pro mikroslužby autonomie](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy) a [asynchronní komunikace založená na zprávách](asynchronous-message-based-communication.md).

## <a name="additional-resources"></a>Další zdroje

- **Věty** \
  [https://en.wikipedia.org/wiki/CAP_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- **Konzistence typu případné** \
  [https://en.wikipedia.org/wiki/Eventual_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- **Úvod do konzistence dat** \
  [https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)](https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10))

- **Martina Fowlera. CQRS (Command and Query Responsibility Segregation)** \
  [https://martinfowler.com/bliki/CQRS.html](https://martinfowler.com/bliki/CQRS.html)

- **Materializované zobrazení** \
  [https://docs.microsoft.com/azure/architecture/patterns/materialized-view](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- **Charles řádek. Odpovídající zásadám ACID vs. ZÁKLADNÍ: PH Shifting zpracování transakcí databáze** \
  [https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/](https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/)

- **Kompenzační transakce** \
  [https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- **Udi Dahan. Služba orientovaný složení** \
  [http://udidahan.com/2014/07/30/service-oriented-composition-with-video/](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

>[!div class="step-by-step"]
>[Předchozí](logical-versus-physical-architecture.md)
>[další](identify-microservice-domain-model-boundaries.md)
