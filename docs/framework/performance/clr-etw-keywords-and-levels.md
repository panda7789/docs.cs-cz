---
title: Klíčová slova a úrovně ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dce8c58f94c66bcf2336d3708ebc64699148d556
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046709"
---
# <a name="clr-etw-keywords-and-levels"></a>Klíčová slova a úrovně ETW CLR
<a name="top"></a>Události trasování událostí pro Windows (ETW) je možné filtrovat podle kategorie a úrovně. [Klíčová slova ETW modulu CLR](#keywords) události umožňují filtrovat události podle kategorie. používají se v kombinaci pro modul runtime a poskytovatele doběhu. [Úrovně událostí](#levels) jsou identifikovány pomocí příznaků.  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>CLR ETW – klíčová slova  
 Klíčová slova jsou příznaky, které mohou být kombinovány, aby generovaly hodnoty. V praxi použijete při volání nástrojů příkazového řádku šestnáctkové hodnoty klíčových slov namísto názvů klíčových slov.  
  
 Klíčová slova jsou popsána v následujících tabulkách:  
  
- [Běhová klíčová slova modulu CLR ETW](#runtime)  
  
- [Doběhu klíčová slova technologie CLR ETW](#rundown)  
  
- [Kombinace klíčových slov pro rozlišení symbolů pro poskytovatele modulu runtime](#runtime_combo)  
  
- [Kombinace klíčových slov pro rozlišení symbolů pro poskytovatele doběhu](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>Běhová klíčová slova modulu CLR ETW  
 V následující tabulce jsou uvedena klíčová slova modulu CLR ETW runtime, jejich hodnoty a jejich použití pro.  
  
|Název klíčového slova za běhu|Value|Účel|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Povolí shromažďování [událostí uvolňování paměti](garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Povolí shromažďování [událostí zavaděče](loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Povoluje kolekci [událostí JIT (just-in-time)](jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Povoluje shromažďování událostí pro metody nativních imagí (metody zpracované generátorem nativních imagí, Ngen. exe); používá se `StartEnumerationKeyword` s `EndEnumerationKeyword`a. Toto klíčové slovo má vysokou režii. Generuje události pro každou metodu uvnitř každého načteného modulu NGen. Pokud je to možné, místo použití tohoto klíčového slova doporučujeme použít databáze programu (soubory PDB) vygenerované nástroji pro profilaci, abyste načetli informace o metodách z modulů NGen. Viz také `OverrideAndSuppressNGenEventsKeyword` dále v této tabulce.|  
|`StartEnumerationKeyword`|0x00000040|Povoluje výčet všech metod v modulu runtime; používá se ve spojení `NGenKeyword`s.|  
|`EndEnumerationKeyword`|0x00000080|Povoluje výčet všech metod, které byly zničeny v modulu runtime; používá se ve spojení `JITKeyword` s `NGenKeyword`a.|  
|`SecurityKeyword`|0x00000400|Povolí shromažďování [událostí zabezpečení](security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Povolí shromažďování událostí monitorování prostředků na úrovni domény aplikace.|  
|`JITTracingKeyword`|0x00001000|Povolí shromažďování [událostí trasování JIT](jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Povolí shromažďování [událostí spolupráce](interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Povolí shromažďování [událostí sporů](contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Povolí shromažďování [událostí výjimek](exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Povolí shromažďování [událostí fondu vláken](thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(K dispozici v .NET Framework 4,5 a novějším.) Potlačí klíčové slovo vysoké režie `NGenKeyword` a zabrání generování událostí pro metody, které jsou uvnitř modulů Ngen. Počínaje .NET Framework 4,5 by nástroje pro profilaci měly používat `OverrideAndSuppressNGenEventsKeyword` a `NGenKeyword` společně potlačit generování událostí pro metody v modulech Ngen. To umožňuje, aby nástroj profilace používal efektivnější soubory PDB NGen k získání informací o metodách v modulech NGen. Modul CLR v .NET Framework 4 a dřívějších verzích nepodporuje vytváření soubory PDB NGen. V těchto starších verzích modul CLR nebude rozpoznávat `OverrideAndSuppressNGenEventsKeyword` a bude zpracovávat `NGenKeyword` události pro metody v modulech Ngen.|  
|`PerfTrackKeyWord`|0x2000000|Povolí shromažďování `ModuleLoad` událostí a `ModuleRange` .|  
|`StackKeyword`|0x40000000|Povolí shromažďování [událostí trasování zásobníku](stack-etw-event.md)CLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>Doběhu klíčová slova technologie CLR ETW  
 V následující tabulce jsou uvedena klíčová slova modulu CLR ETW doběhu, jejich hodnoty a jejich použití pro.  
  
|Název klíčového slova doběhu|Value|Účel|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Povoluje shromažďování událostí zavaděče při použití s `StartRundownKeyword` a. `EndRundownKeyword`|  
|`JitRundownKeyword`|0x00000010|Povoluje shromažďování `DCStart` metod a `DCEnd` událostí pro metody kompilované JIT při použití s `StartRundownKeyword` a `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Povoluje shromažďování `DCStart` metod a `DCEnd` událostí pro metody nativní bitové kopie Ngen při použití s `StartRundownKeyword` a `EndRundownKeyword`. Toto klíčové slovo má vysokou režii. Generuje události pro každou metodu uvnitř každého načteného modulu NGen. Pokud je to možné, místo použití tohoto klíčového slova doporučujeme použít databáze programu (soubory PDB) vygenerované nástroji pro profilaci, abyste načetli informace o metodách z modulů NGen. Viz také `OverrideAndSuppressNGenEventsRundownKeyword` dále v této tabulce.|  
|`StartRundownKeyword`|0x00000040|Umožňuje vyčíslení stavu systému během spouštěcí doběhu.|  
|`EndRundownKeyword`|0x00000100|Povolí výčet stavu systému během koncového doběhu.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Povolí shromažďování událostí pro monitorování prostředků na <xref:System.AppDomain> úrovni při použití s `StartRundownKeyword` nebo `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|Povolí shromažďování událostí fondu vláken.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(K dispozici v .NET Framework 4,5 a novějším.) Potlačí klíčové slovo vysoké režie `NGenRundownKeyword` a zabrání generování událostí pro metody, které jsou uvnitř modulů Ngen. Počínaje .NET Framework 4,5 by nástroje pro profilaci měly používat `OverrideAndSuppressNGenEventsRundownKeyword` a `NGenRundownKeyword` společně potlačit generování událostí pro metody v modulech Ngen. To umožňuje, aby nástroj profilace používal efektivnější soubory PDB NGen k získání informací o metodách v modulech NGen. Modul CLR v .NET Framework 4 a dřívějších verzích nepodporuje vytváření soubory PDB NGen. V těchto starších verzích modul CLR nebude rozpoznávat `OverrideAndSuppressNGenEventsRundownKeyword` a bude zpracovávat `NGenRundownKeyword` události pro metody v modulech Ngen.|  
|`PerfTrackKeyWord`|0x2000000|Povolí shromažďování `ModuleDCStart`událostí, `ModuleDCEnd`, `ModuleRangeDCStart`a. `ModuleRangeDCEnd`|  
  
 [Zpět na začátek](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Kombinace klíčových slov pro rozlišení symbolů pro poskytovatele modulu runtime  
  
|Klíčová slova a příznaky|Události aplikační domény, sestavení, načtení a uvolnění modulu|Události načítání a uvolňování metod (s výjimkou dynamických událostí)|Události načtení a zničení dynamické metody|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Načítání a uvolňování událostí.|Žádné|Žádné|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` nepřidává cokoli)|Žádné|Načtěte události.|Načítání a uvolňování událostí.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Žádné|Načítání a uvolňování událostí.|Načítání a uvolňování událostí.|  
|`NGenKeyword`|Žádné|Žádné|Není k dispozici.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Žádné|Načtěte události.|Není k dispozici.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Žádné|Uvolněte události.|Není k dispozici.|  
  
 [Zpět na začátek](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Kombinace klíčových slov pro rozlišení symbolů pro poskytovatele doběhu  
  
|Klíčová slova a příznaky|Aplikační doména, sestavení, modul DCStart/DCEnd události|Události DCStart/DCEnd metody (včetně událostí dynamické metody)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart`událost.|Žádné|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd`událost.|Žádné|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Žádné|`DCStart`událost.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Žádné|`DCEnd`událost.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Žádné|`DCStart`událost.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Žádné|`DCEnd`událost.|  
  
 [Zpět na začátek](#top)  
  
<a name="levels"></a>   
## <a name="etw-event-levels"></a>Úrovně událostí ETW  
 Události ETW je také možné filtrovat podle úrovně. Pokud je úroveň nastavena na 0x5, jsou vyvolány události všech úrovní, včetně 0x5 a níže (což jsou události, které patří do kategorií povolených pomocí klíčových slov). Pokud je úroveň nastavena na 0x2, jsou vyvolány pouze události, které patří do úrovně 0x2 a níže.  
  
 Úrovně mají následující význam:  
  
 0x5 – verbose  
  
 0x4 – informativní  
  
 0x3 – upozornění  
  
 0x2 – chyba  
  
 0x1 – kritické  
  
 0x0 – LogAlways  
  
## <a name="see-also"></a>Viz také:

- [Poskytovatelé Trasování událostí pro Windows v CLR](clr-etw-providers.md)
- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](etw-events-in-the-common-language-runtime.md)
