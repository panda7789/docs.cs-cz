---
title: Zásady architektury
description: Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | Zásady architektury
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: eb4af7e3472a39bc87f6fcc568b2519099bab279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589942"
---
# <a name="architectural-principles"></a>Zásady architektury

> "Pokud počítačů budovy programátory způsob napsali programy a první woodpecker, které byly dodány společně by destroy civilizace."  
> _\- Weinberg Lucie_

## <a name="summary"></a>Souhrn

Měli byste architektury a návrhu řešení softwaru s udržovatelnosti pamatovat. Principy uvedených v této části vám pomůže směrem k architektury rozhodnutí, která bude mít za následek čistá, údržby aplikace. Obecně platí tyto zásady pokyny k vytváření aplikací mimo diskrétní součásti, které nejsou pevně spojená do dalších částí vaší aplikace, ale spíš komunikují prostřednictvím explicitní rozhraní nebo systémem pro zasílání zpráv.

## <a name="common-design-principles"></a>Společné zásady návrhu

### <a name="separation-of-concerns"></a>Oddělené oblasti zájmu

Prvotní zásadou při vývoji je **oddělení obavy**. Této zásady vyhodnotí, že by měl být oddělený softwaru podle druhy práce, kterou provádí. Zvažte například aplikace, který obsahuje logiku pro identifikaci pozoruhodné položky k zobrazení pro uživatele a který zformátuje takové položky v konkrétní způsob, jak byla výraznější. Chování za výběr položky k formátování by měly být udržovány odděleně od chování zodpovědná za formátování položek, protože existují samostatné otázky, které se vztahují pouze shodou jednu na druhou.

Z pohledu architektury aplikace je možné logicky sestavit podle této zásady oddělením základní obchodní chování z infrastruktury a uživatelské rozhraní logiku. V ideálním případě obchodní pravidla a logiku musí nacházet v samostatné projektu, který by neměl závisí na jiné projekty v aplikaci. To pomáhá zajistit, že obchodní model je snadné testování a můžete rozvíjet bez se úzce párované nízké úrovně implementace na podrobnosti. Oddělené oblasti zájmu je je důležitým aspektem za použití vrstvy v architekturách aplikací.

### <a name="encapsulation"></a>Zapouzdření

Různé části aplikace, měli používat **zapouzdření** k izolovat z dalších částí aplikace. Součásti aplikace a vrstvy by mohli upravit interní implementace, aniž by vás jejich spolupracovníci tak dlouho, dokud nejsou externí kontrakty došlo k porušení. Správné použití operátoru zapouzdření pomůže dosáhnout volné párování a modularitu do návrhů aplikace, protože objekty a balíčky, lze nahradit alternativní implementace tak dlouho, dokud se udržuje stejné rozhraní.

Ve třídách se dosáhne zapouzdření omezení mimo přístup k vnitřní stav třídu. Pokud mimo objektu actor chce, aby se k manipulaci se stav objektu, se musí učinit přes dobře definované funkce (nebo metoda setter vlastnosti), místo přímý přístup k privátním stav objektu. Součásti aplikace a aplikace, sami, by měl vystavit dobře definované rozhraní pro jejich spolupracovníci k použití, namísto povolení jejich stavu přímo upravovat. Tím se uvolní interní návrhu aplikace tak, aby v průběhu času vyvíjejí bez obav, že to tak poruší spolupracovníci, tak dlouho, dokud se spravuje veřejné kontrakty.

### <a name="dependency-inversion"></a>Inverze závislostí

Směr závislosti v rámci aplikace musí být ve směru abstrakce, není podrobnosti implementace. Většina aplikací jsou určeny tak, aby kompilaci závislostí toků ve směru spuštění modulu runtime. To vytváří přímé závislost grafu. To znamená pokud modul A volání a funkce v modulu B, které volá funkci v modulu C, a potom v kompilaci čas A bude záležet na B, který bude záviset na C, jak ukazuje obrázek 4-1.

![](./media/image4-1.png)

**Obrázek 4-1.** Graf přímé závislostí.

Použití Princip inverzi závislostí umožňuje A volat metody abstrakci, který implementuje B, kterých by bylo možné pro A volání B za běhu, ale pro B závisí na rozhraní řízené A v době kompilace (tedy *převrácení* Typické kompilaci závislost). V době běhu toku spuštění programu zůstává beze změny, ale zavedení rozhraní znamená, že různé implementace tato rozhraní lze snadno připojit.

![](./media/image4-2.png)

**Obrázek 4-2.** Graf obráceným závislostí.

**Závislost inverzi** je klíčovou součástí vytváření volně spojené aplikace, protože závisí na a implementovat vyšší úrovni abstrakce, nikoli opačným způsobem je možné zapsat podrobnosti implementace. Výsledná aplikace jsou v důsledku možností intenzivního testování, modulární a udržovatelný. Praxe *vkládání závislostí* je možné díky podle zásady inverzi závislostí.

### <a name="explicit-dependencies"></a>Explicitní závislosti.

**Třídy a metody explicitně vyžadují všechny spolupráce objekty, které jsou nutné k fungování.** Třída konstruktory nabízejí možnost pro třídy k identifikaci akcí, které potřebují, aby byla v platném stavu a správně fungovat. Pokud definujete třídy, které můžete sestavený a názvem, ale které bude pouze fungovat správně, pokud jsou splněné určité globální nebo infrastruktury komponenty, jsou právě tyto třídy *nepoctivý* se svým klientům. Kontrakt konstruktor oznamuje, že klienta, která pouze potřebuje věcí zadaný (pravděpodobně nic, pokud třída právě používá výchozí konstruktor), ale pak za běhu, které se jím objekt skutečně vyžaduje něco jiného.

Pomocí následujících Princip explicitní závislosti, třídy a metody probíhá pravdivé s jejich klienty o požadované funkce. Díky tomu váš kód více samoobslužných dokumentace a kódování měnící přívětivější, protože uživatelé vrátí se do vztahu důvěryhodnosti, který také poskytují, co je potřeba ve formě metoda nebo konstruktor parametry, objekty, které pracují se budou chovat správně za běhu.

### <a name="single-responsibility"></a>Jeden odpovědnosti

Jeden odpovědnost princip platí pro objektově orientované návrhu, ale lze považovat také za architektury Princip podobná oddělené oblasti zájmu. Se stavy, že objekty by měl mít jenom jeden zodpovědnost a že by měly mít jenom jeden důvod, chcete-li změnit. Konkrétně pouze situace, ve kterém by se měl změnit objekt je, pokud způsobem, ve kterém se provádí jeho jeden odpovědnost musí aktualizovat. Podle této zásady umožňuje vytvořit více volně spojené a modulární systémy od různé druhy nové chování může být implementováno jako nové třídy, nikoli přidáním další zodpovědnost za existujících tříd. Přidání nové třídy je vždy bezpečnější než změna existujících tříd, protože žádný kód ještě závisí na nové třídy.

V aplikaci monolitický jsme můžete použít zásady jeden odpovědnosti na vysoké úrovni na vrstvy v aplikaci. Prezentace odpovědnost by měla zůstat v projektu uživatelského rozhraní, při přístupu k datům v rámci projektu infrastruktury by měly být udržovány zodpovědnost. V projektu základní aplikaci, kde lze snadno testovat a můžete rozvíjet nezávisle z jiných odpovědnosti by měly být udržovány obchodní logiku.

Při této zásady je použít Architektura aplikace a jsou přesměrováni na svůj logické koncový bod, získáte mikroslužeb. Daný mikroslužbu by měl mít jeden zodpovědnost. Pokud potřebujete rozšířit chování systému, je obvykle lepší to udělat tak, že přidáte další mikroslužeb, nikoli zodpovědnost za některého ze stávajících.

[Další informace o architektuře mikroslužeb](http://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Nemáte opakujte sami (SUCHÝCH)

Aplikace by měla Vyhněte se zadání chování související s konkrétní koncept na více místech, protože se jedná o zdroj časté chyb. V určitém okamžiku, bude vyžadovat změny v požadavcích změna toto chování a pravděpodobnost, že nejméně jedna instance chování nebude možné aktualizovat, bude mít za následek nekonzistentní chování systému.

Místo duplikování logiku, zapouzdření v programovací konstrukce. Vytvořit vytvořit jeden autority přes toto chování a další část aplikace, která vyžaduje tuto chování použijte novou konstrukce.

> [!NOTE]
> Vyhněte se vazby společně chování, které se pouze shodou opakují. Například právě, protože dva různé konstanty oba mají stejnou hodnotu, která neznamená, že byste měli mít jenom jeden konstantu, pokud koncepčně jste odkazující na různých věcí.

### <a name="persistence-ignorance"></a>Které trvalost

**Které trvalost** (PI) odkazuje na typy, které je potřeba nastavit jako trvalý, ale jejichž kód není ovlivněna volba technologie trvalost. Tyto typy v rozhraní .NET jsou někdy označovány jako prostý staré objekty CLR (POCOs), protože se nemusíte dědit z určité základní třídy nebo implementovat konkrétní rozhraní. Trvalost, které se hodí v situaci, protože umožňuje stejný model business zachovat v několika způsoby, nabízí větší flexibilita k aplikaci. Trvalost možnosti může změnit v čase od technologie jednu databázi na jiný, nebo může být potřeba kromě ať je aplikace spuštěna s další způsoby trvalost (například pomocí mezipaměť Redis nebo Azure DocumentDb kromě relační databáze).

Některé příklady porušení této zásady patří:

-   Vyžaduje základní třída

-   Implementace požadované rozhraní

-   Třídy zodpovědná za uložení sami (například vzoru aktivním záznamu)

-   Vyžaduje výchozí konstruktor

-   Vlastnosti, které vyžadují virtual – klíčové slovo

-   Povinné atributy specifické pro trvalost

Požadavek na třídy mají některé z výše uvedené funkce nebo chování přidá párování mezi typy, které mají být trvalý a volba technologie trvalost znesnadňuje přijmout nové strategií přístupu data v budoucnosti.

### <a name="bounded-contexts"></a>Ohraničené kontexty

**Vázaný kontexty** jsou centrální vzoru v Domain-Driven návrhu. Podle ji rozdělit na samostatné koncepční moduly poskytují způsob boji se složitosti pro velké aplikace nebo organizace. Každý koncepční modul pak představuje kontext, který je oddělená od jiných kontextech (proto ohraničenou) a můžete rozvíjet nezávisle. Každý ohraničené kontext by měla být v ideálním případě mohou zvolit vlastní názvy koncepty v něm a vlastní úložiště trvalosti by měl mít výhradní přístup.

Minimálně měli snažit jednotlivé webové aplikace se vlastní ohraničené kontextu, s vlastní úložiště trvalosti pro svůj obchodní model, místo sdílení databázi s jinými aplikacemi. Probíhá komunikace mezi ohraničené kontexty prostřednictvím programového rozhraní, a nikoli prostřednictvím sdílenou databázi, která umožňuje obchodní logiky a umístěte události provést v reakci na změny, které se uskuteční. Vázaný kontexty mapy úzce k mikroslužeb, které také jsou v ideálním případě implementované jako vlastní jednotlivých ohraničené kontexty.

> ### <a name="references--modern-web-applications"></a>Odkazy – moderních webových aplikací
> - **Oddělené oblasti zájmu**  
> <http://deviq.com/separation-of-concerns/>
> - **Zapouzdření** <http://deviq.com/encapsulation/>
> - **Princip inverzi závislostí**  
> <http://deviq.com/dependency-inversion-principle/>
> - **Princip explicitní závislosti.**  
> <http://deviq.com/explicit-dependencies-principle/>
> - **Nemáte opakujte sami**  
> <http://deviq.com/don-t-repeat-yourself/>
> - **Které trvalost**  
> <http://deviq.com/persistence-ignorance/>
> - **Ohraničené kontextu**  
> <https://martinfowler.com/bliki/BoundedContext.html>

> [!div class="step-by-step"]
[Předchozí] (choose-between-traditional-web-and-single-page-apps.md) [Další] (common-web-application-architectures.md)
