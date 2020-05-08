---
title: Zásady architektury
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Principy architektury
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: e291888bee25a9c87259560ca4b12635ee73c3c7
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975404"
---
# <a name="architectural-principles"></a>Zásady architektury

> "Pokud si tvůrci vytvořili budovy způsob, jakým programátoři zapsali programy, pak první Woodpecker, která byla vytvořena společně, by Civilization zničit."  
> _\-Gerald Weinberg_

Měli byste vytvářet architekta a navrhovat softwarová řešení s ohledem na udržovatelnost. Zásady uvedené v této části vám pomohou při rozhodování o architektuře, které budou mít za následek čisté a udržovatelnější aplikace. Obecně platí, že tyto zásady vám pomohou sestavovat aplikace z diskrétních komponent, které nejsou pevně spojené s ostatními částmi aplikace, ale budou komunikovat přes explicitní rozhraní nebo systémy zasílání zpráv.

## <a name="common-design-principles"></a>Obecné principy návrhu

### <a name="separation-of-concerns"></a>Oddělení obav

Princip identifikátoru GUID při vývoji je **oddělením otázek**. Tento princip vyhodnotí, že software by měl být oddělený podle druhu práce, kterou provádí. Představte si například aplikaci, která obsahuje logiku pro identifikaci zajímavostich položek, které se mají zobrazit uživateli, a které formátuje tyto položky určitým způsobem, aby je bylo možné posuzovat. Chování zodpovědné za výběr položek, které se mají formátovat, by mělo být oddělené od chování zodpovědného za formátování položek, protože se jedná o samostatné otázky, které se týkají pouze koincidentů, které se na sebe vztahují.

Aplikace může být logicky sestavena tak, aby se pomocí tohoto principu oddělující základní obchodní chování od infrastruktury a logiky uživatelského rozhraní. V ideálním případě by se obchodní pravidla a logika měla nacházet v samostatném projektu, který by neměl záviset na jiných projektech v aplikaci. Díky tomu je možné zajistit, aby byl obchodní model snadno testován a mohl se vyvíjet bez úzce se spojit s podrobnostmi o implementaci nízké úrovně. Oddělení obav je klíčové hledisko za použití vrstev v architekturách aplikací.

### <a name="encapsulation"></a>Zapouzdření

Různé části aplikace by měly používat **zapouzdření** k izolaci z jiných částí aplikace. Komponenty a vrstvy aplikace by měly být schopné upravit svou interní implementaci bez nutnosti přerušit své spolupracovníky, pokud nedošlo k porušení vnějších smluv. Správné použití zapouzdření pomáhá dosáhnout volného propojení a modularity v návrzích aplikací, protože objekty a balíčky lze nahradit alternativními implementacemi, pokud je stejné rozhraní zachováno.

Ve třídách je zapouzdření dosaženo omezením přístupu mimo přístup k vnitřnímu stavu třídy. Pokud externí objekt actor chce manipulovat se stavem objektu, měl by tak učinit prostřednictvím dobře definované funkce (nebo metody setter) místo přímého přístupu k privátnímu stavu objektu. Stejně tak by komponenty aplikace a aplikace samy měly vystavovat dobře definovaná rozhraní pro své spolupracovníky, aby je bylo možné použít, místo aby bylo možné jejich stav upravovat přímo. Tím se uvolní interní návrh aplikace v průběhu času, aniž by to mělo starosti s tím, že spolupracuje spolupracovníci, pokud se zachovají veřejné smlouvy.

### <a name="dependency-inversion"></a>Inverze závislosti

Směr závislosti v rámci aplikace by měl být ve směru abstrakce, nikoli v podrobnostech implementace. Většina aplikací je zapsána tak, aby toky závislostí při kompilaci byly ve směru provádění za běhu. Tím se vytvoří graf přímého závislosti. To znamená, že pokud modul A zavolá funkci v modulu B, která volá funkci v modulu C, pak v době kompilace bude záviset na B, která bude záviset na C, jak je znázorněno na obrázku 4-1.

![Graf přímého závislosti](./media/image4-1.png)

**Obrázek 4-1.** Graf přímého závislosti

Použití principu pro inverze závislostí umožňuje volat metody na abstrakci, kterou B implementuje, aby bylo možné volat B za běhu, ale v případě B na rozhraní, které je řízeno v době kompilace (tedy *Invertuje* typickou závislost v době kompilace). V době běhu zůstává tok spuštění programu nezměněný, ale zavedení rozhraní znamená, že je možné snadno zapojit různé implementace těchto rozhraní.

![Graf obrácené závislosti](./media/image4-2.png)

**Obrázek 4-2.** Graf nevrácené závislosti

**Inverze závislosti** je klíčovou součástí vytváření volně vázaných aplikací, protože podrobnosti implementace mohou být zapsány do záviset na a implementovat abstrakce na vyšší úrovni, nikoli jiným způsobem. Výsledné aplikace jsou ve výsledku testovatelné, modulární a udržovatelnější. Postup *Injektáže závislosti* je možný pomocí principu inverze závislosti.

### <a name="explicit-dependencies"></a>Explicitní závislosti

**Metody a třídy by měly explicitně vyžadovat všechny objekty spolupráce, které potřebují, aby fungovaly správně.** Konstruktory třídy poskytují příležitost pro třídy k identifikaci potřebných věcí, aby byly v platném stavu a fungovaly správně. Pokud definujete třídy, které mohou být vytvořeny a volány, ale budou správně fungovat pouze v případě, že jsou vytvořeny určité globální nebo infrastrukturní komponenty, tyto třídy jsou pro *klienty bez problémů* . Kontrakt konstruktoru oznamuje klientovi, že potřebuje jenom zadané věci (možná nic, když třída používá jenom parametr bez parametrů), ale pak za běhu vypíná objekt, který skutečně potřebuje něco jiného.

Pomocí principu explicitních závislostí jsou vaše třídy a metody od klientů od jejich klientů bezvýznamné, aby fungovaly. Díky tomu je váš kód podrobněji uživatelsky přívětivý a vaše smlouvy s kódováním jsou uživatelsky přívětivé, protože uživatelé budou mít důvěru, že pokud poskytnou, co je potřeba ve formě parametrů metod nebo konstruktorů, objekty, se kterými se pracuje, se budou chovat správně za běhu.

### <a name="single-responsibility"></a>Jediná odpovědnost

Princip jedné zodpovědnosti se vztahuje na objektově orientovaný návrh, ale je možné ho také považovat za Princip architektury, který se podobá oddělení obav. Uvádí, že by měly mít objekty jenom jednu zodpovědnost a že by měly mít jenom jeden důvod, aby se změnila. Konkrétně jediná situace, kdy se má objekt změnit, je třeba aktualizovat způsob, jakým má být proveden jeho jedna zodpovědnost. V rámci tohoto principu je usnadněno vytvoření více volně propojených a modulárních systémů, protože mnoho druhů nového chování může být implementováno jako nové třídy, nikoli přidáním další zodpovědnosti existující třídy. Přidávání nových tříd je vždy bezpečnější než změna stávajících tříd, protože žádný kód ještě nezávisí na nových třídách.

V aplikaci monolitické můžeme uplatnit zásadu jedné zodpovědnosti na vysokou úroveň na vrstvy v aplikaci. Odpovědnost za prezentaci by měla zůstat v projektu uživatelského rozhraní, zatímco odpovědnost za přístup k datům by měla být zachována v rámci projektu infrastruktury. Obchodní logika by měla být zachována v projektu základního aplikace, kde ji lze snadno otestovat a lze ji vyvíjet nezávisle na jiných odpovědnostech.

Pokud se tento princip aplikuje na architekturu aplikace a převezme se ke svému logickému koncovému bodu, získáte mikroslužby. Daná mikroslužba by měla mít jednu zodpovědnost. Pokud potřebujete rozšířit chování systému, je obvykle lepší to udělat přidáním dalších mikroslužeb, nikoli přidáním zodpovědnosti do existující.

[Další informace o architektuře mikroslužeb](https://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Neopakuje se sami (SUCHá)

Aplikace by se neměla zacházet s určením chování týkajícího se konkrétního konceptu na více místech, protože se jedná o často se zdrojem chyb. V určitém okamžiku bude změna požadavků vyžadovat změnu tohoto chování. Je možné, že se nejméně jedna instance chování nebude aktualizovat a bude to mít za následek nekonzistentní chování systému.

Místo duplikace logiky je zapouzdřovat v programovacím konstruktoru. Tuto konstrukci udělejte od tohoto chování jediným orgánem a všechny ostatní části aplikace, které vyžadují toto chování, používají novou konstrukci.

> [!NOTE]
> Vyhněte se vazbě chování, které se provádí pouze při incidentech. Například vzhledem k tomu, že dvě různé konstanty mají stejnou hodnotu, to neznamená, že byste měli mít pouze jednu konstantu, pokud koncepčně odkazuje na různé věci.

### <a name="persistence-ignorance"></a>Ignorování trvalosti

**Ignorování trvalosti** (pi) odkazuje na typy, které je nutné zachovat, ale jejichž kód není ovlivněn volbou technologie trvalosti. Tyto typy v rozhraní .NET jsou někdy označovány jako prosté staré objekty CLR (POCOs), protože nejsou nutné dědit z konkrétní základní třídy nebo implementovat konkrétní rozhraní. Ignorování trvalosti je užitečné, protože umožňuje, aby byl stejný obchodní model trvalý více způsoby, a nabízí tak aplikaci větší flexibilitu. Volby trvalosti se můžou v průběhu času měnit, od jedné databázové technologie až po jinou, ale kromě toho, že je aplikace spuštěná (například pomocí Redis Cache nebo Azure Cosmos DB kromě relační databáze), se může vyžadovat i další forma trvalosti.

Mezi příklady porušení tohoto principu patří:

- Požadovaná základní třída.

- Požadovaná implementace rozhraní.

- Třídy zodpovědné za uložení samotných (například modelu aktivního záznamu).

- Požadovaný konstruktor bez parametrů.

- Vlastnosti vyžadující klíčové slovo Virtual

- Požadované atributy trvalého uložení.

Požadavek, aby třídy měly některé z výše uvedených funkcí nebo chování, přidává propojení mezi typy, které se mají zachovat, a volba technologie trvalosti, díky čemuž je obtížnější v budoucnu přijmout nové strategie přístupu k datům.

### <a name="bounded-contexts"></a>Ohraničené kontexty

**Ohraničené** kontexty jsou centrálním vzorem v návrhu založeném na doméně. Poskytují způsob, jak vypořádat složitost ve velkých aplikacích nebo organizacích tím, že je rozbalíte do samostatných koncepčních modulů. Každý koncepční modul pak představuje kontext, který je oddělený od jiných kontextů (proto, vázaný) a může se vyvíjet nezávisle. Každý ohraničený kontext by měl být v ideálním případě bezplatný pro výběr jeho vlastních názvů a měl by mít výhradní přístup k vlastnímu úložišti trvalosti.

Minimálně jednotlivé webové aplikace by měly být zaměřené na vlastní ohraničený kontext s vlastním úložištěm trvalého využití pro svůj obchodní model místo sdílení databáze s jinými aplikacemi. Komunikace mezi ohraničenými kontexty probíhá prostřednictvím programových rozhraní, nikoli přes sdílenou databázi, která umožňuje, aby obchodní logika a události byly provedeny v reakci na změny, které probíhají. Ohraničené kontexty jsou úzce namapovány na mikroslužby, které jsou také ideálním způsobem implementovány jako vlastní jednotlivé ohraničené kontexty.

## <a name="additional-resources"></a>Další zdroje

- [Vzory návrhu JAVA: principy](https://java-design-patterns.com/principles/)
- [Ohraničený kontext](https://martinfowler.com/bliki/BoundedContext.html)

>[!div class="step-by-step"]
>[Předchozí](choose-between-traditional-web-and-single-page-apps.md)
>[Další](common-web-application-architectures.md)
