---
title: Zásady architektury
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Architektonické principy
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: ffc890bf8cd6b07bd70d8fc7b2b8cfeaf474ae35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450268"
---
# <a name="architectural-principles"></a>Zásady architektury

> "Pokud stavitelé stavěli budovy tak, jak programátoři psali programy, pak první datel, který přišel, by zničil civilizaci."  
> _\-Gerald Weinberg_

Měli byste architekt a navrhnout softwarová řešení s ohledem na udržovatelnost. Zásady uvedené v této části vám mohou pomoci k architektonickým rozhodnutím, která budou mít za následek čisté a udržovatelné aplikace. Obecně platí, že tyto zásady vás povede k vytváření aplikací z diskrétních součástí, které nejsou pevně spojeny s jinými částmi aplikace, ale spíše komunikovat prostřednictvím explicitní rozhraní nebo systémy zasílání zpráv.

## <a name="common-design-principles"></a>Společné zásady návrhu

### <a name="separation-of-concerns"></a>Oddělení obav

Hlavní zásadou při vývoji je **oddělení obav**. Tento princip tvrdí, že software by měl být oddělen na základě druhů práce, kterou vykonává. Zvažte například aplikaci, která obsahuje logiku pro identifikaci pozoruhodných položek, které se mají uživateli zobrazit, a které tyto položky určitým způsobem formátují, aby byly výraznější. Chování odpovědné za výběr položek, které mají formátovat by měly být odděleny od chování odpovědné za formátování položek, protože se jedná o samostatné obavy, které jsou pouze shodou okolností souvisí s sebou.

Architektonicky aplikace mohou být logicky sestaveny tak, aby se řídily tímto principem oddělením základního obchodního chování od logiky infrastruktury a uživatelského rozhraní. V ideálním případě obchodní pravidla a logika by měla být umístěna v samostatném projektu, který by neměl záviset na jiných projektech v aplikaci. To pomáhá zajistit, že obchodní model je snadno testovat a může vyvíjet, aniž by byl pevně spojen s podrobnostmi implementace nižší úrovně. Oddělení obav je klíčovým aspektem použití vrstev v aplikačních architekturách.

### <a name="encapsulation"></a>Zapouzdření

Různé části aplikace by měly používat **zapouzdření** k jejich izolaci od jiných částí aplikace. Součásti aplikace a vrstvy by měly být schopny upravit jejich vnitřní implementaci bez porušení jejich spolupracovníky, pokud nejsou porušeny externí smlouvy. Správné použití zapouzdření pomáhá dosáhnout volné párování a modularity v návrzích aplikací, protože objekty a balíčky mohou být nahrazeny alternativními implementacemi, pokud je zachováno stejné rozhraní.

Ve třídách je zapouzdření dosaženo omezením vnějšího přístupu k vnitřnímu stavu třídy. Pokud vnější objekt actor chce manipulovat se stavem objektu, by měl tak učinit prostřednictvím dobře definované funkce (nebo setter vlastností), nikoli mít přímý přístup k soukromému stavu objektu. Podobně součásti aplikace a aplikace samy o sobě by měly vystavit dobře definované rozhraní pro jejich spolupracovníky k použití, spíše než povolit jejich stav upravit přímo. To uvolní vnitřní návrh aplikace, aby se vyvíjel v průběhu času bez obav, že tím dojde k přerušení spolupracovníků, pokud jsou zachovány veřejné zakázky.

### <a name="dependency-inversion"></a>Inverze závislostí

Směr závislosti v rámci aplikace by měl být ve směru abstrakce, nikoli podrobnosti implementace. Většina aplikací jsou zapsány tak, že závislost v době kompilace toky ve směru spuštění za běhu. To vytváří graf přímé závislosti. To znamená, že pokud modul A volá funkci v modulu B, který volá funkci v modulu C, pak v době kompilace A bude záviset na B, který bude záviset na C, jak je znázorněno na obrázku 4-1.

![Graf přímé závislosti](./media/image4-1.png)

**Obrázek 4-1.** Graf přímé závislosti.

Použití principu inverze závislosti umožňuje A volat metody na abstrakci, která implementuje B, což umožňuje A volání B za běhu, ale pro B závisí na rozhraní řízené a v době kompilace (tedy *invertování* typické kompilace závislost). V době běhu tok provádění programu zůstává beze změny, ale zavedení rozhraní znamená, že různé implementace těchto rozhraní lze snadno připojit.

![Invertovaný graf závislostí](./media/image4-2.png)

**Obrázek 4-2.** Invertovaný graf závislostí.

**Inverze závislostí** je klíčovou součástí vytváření volně vázaných aplikací, protože podrobnosti implementace mohou být zapsány tak, aby závisely na abstrakcích vyšší úrovně a implementovaly je, nikoli naopak. Výsledné aplikace jsou více testovatelné, modulární a udržovatelné jako výsledek. Praxe *vkládání závislostí* je možné pomocí následující princip inverze závislosti.

### <a name="explicit-dependencies"></a>Explicitní závislosti

**Metody a třídy by měly explicitně vyžadovat všechny kolaborující objekty, které potřebují ke správnému fungování.** Konstruktory tříd poskytují příležitost pro třídy k identifikaci věcí, které potřebují, aby byly v platném stavu a správně fungovaly. Pokud definujete třídy, které mohou být vytvořeny a volány, ale to bude fungovat správně pouze v případě, že jsou na místě určité globální součásti nebo součásti infrastruktury, tyto třídy jsou *nečestné* se svými klienty. Kontrakt konstruktoru říká klientovi, že potřebuje pouze zadané věci (možná nic, pokud třída používá pouze konstruktor bez parametrů), ale pak za běhu se ukáže, že objekt opravdu potřeboval něco jiného.

Dodržováním zásady explicitnízávislosti, vaše třídy a metody jsou upřímní se svými klienty o tom, co potřebují, aby fungovaly. Díky tomu je váš kód více self-dokumentování a kódování smlouvy více uživatelsky přívětivé, protože uživatelé přijdou k důvěře, že tak dlouho, dokud poskytují to, co je požadováno ve formě metody nebo konstruktoru parametry, objekty, které pracují s se bude chovat správně za běhu.

### <a name="single-responsibility"></a>Jednotná odpovědnost

Princip jediné odpovědnosti se vztahuje na objektově orientovaný design, ale lze jej také považovat za architektonický princip podobný oddělení zájmů. Uvádí, že objekty by měly mít pouze jednu odpovědnost a že by měly mít pouze jeden důvod ke změně. Konkrétně pouze situace, ve kterém by měl objekt změnit, je v případě, že musí být aktualizován způsob, jakým provádí svou jednu odpovědnost. Dodržování tohoto principu pomáhá vyrábět volněji spojené a modulární systémy, protože mnoho druhů nového chování může být implementováno jako nové třídy, spíše než přidáním další odpovědnosti do stávajících tříd. Přidání nových tříd je vždy bezpečnější než změna existujících tříd, protože žádný kód zatím závisí na nových třídách.

V monolitické aplikaci můžeme aplikovat princip jediné odpovědnosti na vysoké úrovni na vrstvy v aplikaci. Odpovědnost za prezentaci by měla zůstat v projektu uj. Obchodní logika by měla být zachována v základním projektu aplikace, kde ji lze snadno testovat a vyvíjet nezávisle na jiných odpovědnostech.

Když se tento princip použije na architekturu aplikace a přejde na jeho logický koncový bod, získáte mikroslužeb. Daná mikroslužba by měla mít jedinou odpovědnost. Pokud potřebujete rozšířit chování systému, je obvykle lepší to provést přidáním dalších mikroslužeb, spíše než přidáním odpovědnosti do existující.

[Další informace o architektuře mikroslužeb](https://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Neopakujte se (DRY)

Aplikace by se měla vyhnout určení chování související s konkrétní koncept na více místech, protože se jedná o častý zdroj chyb. V určitém okamžiku změna požadavků bude vyžadovat změnu tohoto chování a pravděpodobnost, že alespoň jedna instance chování se nezdaří být aktualizovánbude mít za následek nekonzistentní chování systému.

Spíše než duplikování logiky, zapouzdření v programovací konstrukce. Proveďte tuto konstrukci jediné oprávnění nad toto chování a mít jinou část aplikace, která vyžaduje toto chování použít nové konstrukce.

> [!NOTE]
> Vyhněte se vazby dohromady chování, které je jen shodou okolností opakující. Například jen proto, že dvě různé konstanty mají stejnou hodnotu, neznamená to, že byste měli mít pouze jednu konstantu, pokud koncepčně odkazují na různé věci.

### <a name="persistence-ignorance"></a>Vytrvalost nevědomost

**Neznalost přetrvávání** (PI) odkazuje na typy, které je třeba zachovat, ale jejichž kód není ovlivněn volbou technologie trvalosti. Tyto typy v rozhraní .NET jsou někdy označovány jako plain old CLR objects (POCO), protože není nutné dědit z určité základní třídy nebo implementovat určité rozhraní. Neznalost trvalosti je cenná, protože umožňuje zachovat stejný obchodní model několika způsoby a nabízí další flexibilitu aplikace. Možnosti trvalosti se mohou v průběhu času měnit, z jedné databázové technologie na jinou, nebo mohou být kromě toho, s čím aplikace byla spuštěna, vyžadovány další formy trvalosti (například použití mezipaměti Redis nebo Azure Cosmos DB kromě relační databáze).

Některé příklady porušení tohoto principu zahrnují:

- Povinná základní třída.

- Požadovaná implementace rozhraní.

- Třídy odpovědné za ukládání sebe (například vzor aktivního záznamu).

- Požadovaný konstruktor bez parametrů.

- Vlastnosti vyžadující virtuální klíčové slovo.

- Požadované atributy specifické pro trvalost.

Požadavek, aby třídy mají některé z výše uvedených funkcí nebo chování přidává spojení mezi typy, které mají být trvalé a výběr technologie trvalosti, takže je obtížnější přijmout nové strategie přístupu k datům v budoucnu.

### <a name="bounded-contexts"></a>Ohraničené kontexty

**Ohraničené kontexty** jsou centrální vzor v návrhu řízeném doménou. Poskytují způsob řešení složitosti ve velkých aplikacích nebo organizacích rozdělením do samostatných koncepčních modulů. Každý koncepční modul pak představuje kontext, který je oddělen od jiných kontextů (proto ohraničené) a může vyvíjet nezávisle. Každý ohraničený kontext by měl mít v ideálním případě možnost zvolit své vlastní názvy pro koncepty v něm a měl by mít výhradní přístup k vlastnímu úložišti trvalosti.

Minimálně jednotlivé webové aplikace by se měly snažit být jejich vlastní ohraničený kontext, s vlastním úložištěm trvalosti pro jejich obchodní model, spíše než sdílet databázi s jinými aplikacemi. Komunikace mezi ohraničené kontexty probíhá prostřednictvím programových rozhraní, nikoli prostřednictvím sdílené databáze, která umožňuje obchodní logiku a události probíhat v reakci na změny, ke kterým dochází. Ohraničené kontexty mapovat úzce mikroslužeb, které jsou také v ideálním případě implementovány jako jejich vlastní individuální ohraničené kontexty.

## <a name="additional-resources"></a>Další zdroje

- [Java Design Patterns: Principy](https://java-design-patterns.com/principles/)
- [Ohraničený kontext](https://martinfowler.com/bliki/BoundedContext.html)

>[!div class="step-by-step"]
>[Předchozí](choose-between-traditional-web-and-single-page-apps.md)
>[další](common-web-application-architectures.md)
