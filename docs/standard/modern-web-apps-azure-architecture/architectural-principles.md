---
title: Zásady architektury
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Zásady architektury
author: ardalis
ms.author: wiwagn
ms.date: 02/16/2019
ms.openlocfilehash: 7d127476e37b9eefa9ddc13d26991145b6245b45
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442981"
---
# <a name="architectural-principles"></a>Zásady architektury

> "Pokud budov sestavili tvůrci programátoři způsob napsal programy a první woodpecker, který po něm přišel by zničit civilizace."  
> _\- Weinberg Lucie_

By měla navrhovat a navrhněte softwarová řešení s udržovatelnosti v úvahu. Zásady uvedené v této části vám pomůže směrem k rozhodnutí o architektuře, výsledkem bude čistý, údržby aplikace. Obecně tyto zásady se dozvíte, k vytváření aplikací ze samostatné součásti, které nejsou pevně ostatních částech aplikace, ale spíše komunikovat prostřednictvím explicitního rozhraní nebo systémů pro zasílání zpráv.

## <a name="common-design-principles"></a>Běžné zásady návrhu

### <a name="separation-of-concerns"></a>Oddělení oblastí zájmu

Je základní princip při vývoji **oddělení se týká**. Této zásady vyhodnotí, že by měla být oddělena software podle druhy práce, kterou provádí. Zvažte například aplikaci, která obsahuje logiku pro identifikaci zajímavosti položek se budou zobrazovat uživateli, a který zformátuje tyto položky tak, aby byly snadněji postřehnutelné určitým způsobem. Odpovědnost za výběr položek k formátování chování by měl být udržovány odděleně od chování za formátování položek, protože jde o samostatné otázky, které se vztahují pouze shodou mezi sebou.

Architektonicky aplikace se dají logicky vytvářet postupovat podle této zásady tak, že oddělíte core obchodní chování od logiky infrastruktury a uživatelské rozhraní. V ideálním případě obchodní pravidla a logiky by měl nacházet v samostatný projekt, který by neměl závisí na jiné projekty v aplikaci. To pomáhá zajistit, že je obchodní model usnadňuje testování a můžete rozvíjet bez jsou úzce spojeny s podrobnosti nízké úrovně implementace. Oddělení oblastí zájmu je důležitým aspektem za použití vrstev v aplikačních architektur.

### <a name="encapsulation"></a>Zapouzdření

Používejte různé části aplikace **zapouzdření** chcete izolovat je z jiných částí aplikace. Mezi součástmi aplikace a vrstvy by měl být moci upravit jejich vnitřní implementace bez porušení jejich spolupracovníky tak dlouho, dokud nejsou došlo k porušení smlouvy externí. Správné použití operátoru zapouzdření pomáhá dosahovat volné párování a modularitu při návrhy aplikací, protože objekty a balíčky je možné nahradit alternativní implementace tak dlouho, dokud se udržuje stejné rozhraní.

Ve třídách zapouzdření se dosahuje tím, že omezíte mimo přístup ke vnitřní stav třídy. Pokud prvek "actor" vnější chce, aby se k manipulaci s stavu objektu, je to měl dělat implementovaný prostřednictvím dobře definovaných – funkce (nebo vlastnost setter), namísto nutnosti přímý přístup k privátním stavu objektu. Mezi součástmi aplikace a samotnými aplikacemi, by měly vystavit dobře definovaných rozhraní pro své spolupracovníky k používání a nepovolí svůj stav na přímo upravovat. Tím se uvolní interní návrhu aplikace až po v průběhu času vyvíjejí bez obav, že to uděláte tak přeruší spolupracovníkům, tak dlouho, dokud se zachovají veřejné smluv.

### <a name="dependency-inversion"></a>Inverze závislostí

Směr závislosti v rámci aplikace musí být ve směru abstrakce, ne podrobnosti implementace. Většina aplikací jsou napsané tak, aby závislostí kompilace toky ve směru spuštění modulu runtime. Tímto se vytvoří graf závislosti s přímým přístupem. To znamená pokud modul A volá funkci v modulu B, které volá funkci v modulu jazyka C a pak podle času A kompilace závisí na B, který bude záviset na C, jak ukazuje obrázek 4-1.

![](./media/image4-1.png)

**Obrázek 4-1.** Graf závislosti s přímým přístupem.

Použití zásady čistého inverzi závislost umožňuje A volání metod na abstrakce, která implementuje B, aby bylo možné pro A volání B za běhu, ale pro B závisí na rozhraní řídí A v době kompilace (tedy *převrácení* Typické kompilace závislosti). V době běhu průběh provádění programu nezmění, ale po zavedení služby rozhraní znamená, že jedná o rozdílné implementace těchto rozhraní můžete snadno být zapojené do elektrické zásuvky.

![](./media/image4-2.png)

**Obrázek 4-2.** Graf závislosti obrácený.

**Závislost inverzi** je klíčovou součástí vytvoření volně spárované aplikace, protože podrobnosti implementace lze zapsat a závisí na implementaci vyšší úroveň abstrakce, spíše než naopak. Výsledná aplikace jsou v důsledku možností intenzivního testování, modulární a udržovatelný. Postup, kdy se *injektáž závislostí* je možné podle principu inverzi závislostí.

### <a name="explicit-dependencies"></a>Explicitní závislosti.

**Metody a třídy explicitně vyžadují žádné spolupracující objekty, které potřebují, aby bylo možné správně fungovat.** Konstruktor třídy poskytují příležitost pro třídy k identifikaci věci, které musí být v platném stavu a správně fungovat. Při definování třídy, která vytvořen a názvem, ale která bude pouze fungovat správně, pokud některé součásti globální nebo infrastruktury jsou na místě, se tyto třídy *nepoctivý* s klienty. Kontrakt konstruktor sděluje, že klienta, který potřebuje pouze věci zadané (pravděpodobně nic, pokud třída používá pouze výchozí konstruktor), ale pak za běhu, který ukazuje objekt opravdu potřebujete něco jiného.

Podle principu explicitní závislosti jsou ještě upřímná s klienty o to, co chtějí, aby bylo možné funkci třídy a metody. Díky tomu váš kód více samoobslužných dokumentace a smlouvy přívětivější, psaní kódu, protože uživatelé budou přicházet do vztahu důvěryhodnosti, který tak dlouho, dokud poskytují toho, co vyžaduje ve formě – metoda nebo parametry konstruktoru, objekty, které pracují se bude chovat. správně za běhu.

### <a name="single-responsibility"></a>Jednotnou zodpovědnost

Princip jednotnou zodpovědnost se vztahuje k objektově orientovaný návrh, ale můžete také považují za architektury Princip podobný oddělení oblastí zájmu. Uvádí, že objekty by měl mít pouze jednu zodpovědnost a že by měly mít pouze jeden důvod, proč změnit. Konkrétně pouze situace, ve kterém by měl změnit objekt je, pokud se musí aktualizovat způsob, ve které provádí její odpovědnosti jeden. Podle této zásady umožňuje vytvořit více volně spojené a modulární systémy, od mnoha různých nové chování je možné implementovat jako nové třídy, nikoli přidáním další odpovědnost na existující třídy. Přidání nové třídy je vždy bezpečnější než změna existujících tříd, protože žádný kód, ale závisí na nové třídy.

V monolitické aplikaci jsme do vrstvy v aplikaci použít principu jednotnou zodpovědnost na vysoké úrovni. Prezentace odpovědnost by měla zůstat v projektu uživatelského rozhraní, při přístupu k datům v rámci projektu aplikace infrastruktury by měly být neustále odpovědnost. Obchodní logika ukládat v základní projekt aplikace, ve kterém lze snadno testovat a můžete rozvíjet nezávisle z další úkoly.

Tato zásada je použita na architektuře aplikací a přesunete na jeho logický koncový bod, získáte mikroslužeb. Daný mikroslužba by měl mít jednotnou zodpovědnost. Pokud potřebujete rozšířit chování systému, je obvykle vhodnější to udělat tak, že přidáte další mikroslužeb, nikoli přidáním zodpovědností některý z existujících.

[Další informace o architektuře mikroslužeb](https://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Neopakovat sami (zkušební)

Aplikace se měli vyhnout určení chování je to časté příčiny chyby související s konkrétní pojem na více místech. V určitém okamžiku bude vyžadovat změny v požadavcích změna toto chování a pravděpodobnost, že nejméně jedna instance chování selže aktualizovat bude mít za následek nekonzistentní chování systému.

Namísto duplikování logiky zapouzdření v programovací konstrukce. Vytvořit sestavit jeden autority přes toto chování a mají jiné části aplikace, která potřebuje toto chování použít novou konstrukci.

> [!NOTE]
> Vyhněte se chování, které se shodou opakované vazby společně. Například pouze z důvodu dvě různé konstanty obě mají stejnou hodnotu, neznamená, že byste měli mít jenom jednu konstantu, koncepčně jste odkazující na různé věci.

### <a name="persistence-ignorance"></a>Trvalost neznalosti

**Trvalost neznalosti** (PÍ) odkazuje na typy, které je potřeba nastavit jako trvalý, ale jejíž kód není ovlivněn řadu technologií trvalosti. Tyto typy v rozhraní .NET jsou někdy označovány jako obyčejný starší objekty CLR (POCOs), protože není nutné dědí určité základní třídy nebo implementovat konkrétní rozhraní. Trvalost neznalosti je užitečné, protože umožňuje stejný model business natrvalo několika různými způsoby, nabízí větší flexibilitu pro aplikace. Možnosti trvalého může změnit v čase od technologie jednu databázi na jiný, nebo může být vyžadováno kromě cokoli, co je aplikace spuštěna s další formy trvalost (například použití mezipaměti redis cache nebo Azure DocumentDb kromě relační databáze).

Mezi příklady narušení této zásady patří:

- Vyžaduje základní třídy.

- Provádění požadované rozhraní.

- Třídy za samotné ukládání (například záznam Active vzor).

- Vyžaduje výchozí konstruktor.

- Vlastnosti vyžadující virtual – klíčové slovo.

- Vyžadované atributy specifické pro trvalost.

Požadavek třídy mají některé z výše uvedené funkce nebo chování přidá párování mezi typy natrvalo a volbu technologie trvalost znesnadňuje přijmout nové strategie přístup data v budoucnosti.

### <a name="bounded-contexts"></a>Ohraničené kontexty

**Ohraničených kontextech** jsou centrální model v Domain-Driven Design. Když ho rozdělíte do samostatných koncepční modulů poskytují způsob složitosti řešení pro velké aplikace nebo organizace. Každý koncepční modul představuje kontext, který je oddělená od ostatních kontextech (tedy ohraničeny) a můžete rozvíjet nezávisle na sobě. Jednotlivých ohraničených kontextech v ideálním případě měli zvolit vlastní názvy konceptů v rámci něj a má výhradní přístup k vlastním úložišti pro trvalé uložení.

Minimálně přiklonit jednotlivých webových aplikací na jejich vlastní ohraničený kontext s své vlastní úložiště trvalosti pro svůj obchodní model, nikoli databázi pro sdílení obsahu s jinými aplikacemi. Probíhá komunikace mezi ohraničené kontexty prostřednictvím programových rozhraní, a nikoli prostřednictvím sdílenou databázi, která umožňuje obchodní logiky a události se umístit v reakci na změny, které se provedou. Ohraničených kontextech mapy úzce do mikroslužeb, která také se v ideálním případě implementují jako vlastní jednotlivých ohraničené kontexty.

## <a name="additional-resources"></a>Další zdroje

* [Vzory návrhu JAVA: Zásady](https://java-design-patterns.com/principles/)
* [Ohraničený kontext](https://martinfowler.com/bliki/BoundedContext.html)

>[!div class="step-by-step"]
>[Předchozí](choose-between-traditional-web-and-single-page-apps.md)
>[další](common-web-application-architectures.md)
