---
title: Klíčová slova a úrovně ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
ms.openlocfilehash: 2106ed0d85cd116be4d7c46396ad6e1597c4341d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400062"
---
# <a name="clr-etw-keywords-and-levels"></a>Klíčová slova a úrovně ETW CLR
Trasování událostí pro události systému Windows (ETW) lze filtrovat podle kategorie a úrovně. Klíčová [slova CLR ETW](#clr-etw-keywords) události umožňují filtrování událostí podle kategorie; používají se v kombinacích pro zprostředkovatele runtime a rundown. [Úrovně událostí](#etw-event-levels) jsou označeny příznaky.  
  
## <a name="clr-etw-keywords"></a>Klíčová slova CLR ETW  
 Klíčová slova jsou příznaky, které lze kombinovat pro generování hodnot. V praxi použijete šestnáctkové hodnoty klíčových slov namísto názvů klíčových slov při volání nástrojů příkazového řádku.  
  
 Klíčová slova jsou popsána v následujících tabulkách:  
  
- [Klíčová slova clr ETW runtime](#runtime)  
  
- [Clr ETW zchátřit klíčová slova](#rundown)  
  
- [Kombinace klíčových slov pro rozlišení symbolů pro zprostředkovatele runtime](#runtime_combo)  
  
- [Kombinace klíčových slov pro rozlišení symbolů pro zprostředkovatele rundown](#rundown_combo)  
  
<a name="runtime"></a>
### <a name="clr-etw-runtime-keywords"></a>Klíčová slova clr ETW Runtime  
 V následující tabulce jsou uvedena klíčová slova clr ETW runtime, jejich hodnoty a pro co se používají.  
  
|Název klíčového slova Runtime|Hodnota|Účel|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Umožňuje shromažďování [událostí uvolňování paměti](garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Umožňuje shromažďování [událostí zavaděče](loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Umožňuje shromažďování [událostí za čase (JIT).](jit-tracing-etw-events.md)|  
|`NGenKeyword`|0x00000020|Umožňuje shromažďování událostí pro metody nativního obrazu (metody zpracované generátorem nativního obrazu Ngen.exe); s `StartEnumerationKeyword` a `EndEnumerationKeyword`. Toto klíčové slovo má vysokou režii. Generuje události pro každou metodu uvnitř každého načteného modulu NGen. Kdykoli je to možné, namísto použití tohoto klíčového slova, doporučujeme použít programové databáze (PDBs) generované profilovací nástroje k načtení informací o metodách z modulů NGen. Viz `OverrideAndSuppressNGenEventsKeyword` také dále v této tabulce.|  
|`StartEnumerationKeyword`|0x00000040|Umožňuje výčet všech metod v běhu; ve spojení `NGenKeyword`s .|  
|`EndEnumerationKeyword`|0x00000080|Umožňuje výčet všech metod zničených v běhu; ve spojení `JITKeyword` s `NGenKeyword`písmenem a) a.|  
|`SecurityKeyword`|0x00000400|Umožňuje shromažďování [událostí zabezpečení](security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Umožňuje shromažďování událostí monitorování prostředků na úrovni domény aplikace.|  
|`JITTracingKeyword`|0x000010000|Umožňuje shromažďování [událostí trasování JIT](jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Umožňuje shromažďování [událostí interop](interop-etw-events.md).|  
|`ContentionKeyword`|0x000040000|Umožňuje shromažďování [konfliktních událostí](contention-etw-events.md).|  
|`ExceptionKeyword`|0x000080000 000000000000000000000|Povolí shromažďování [událostí výjimek](exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x000100000|Umožňuje kolekci [událostí fondu vláken](thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x000400000|(K dispozici v rozhraní .NET Framework 4.5 a novější.) Potlačí klíčové slovo `NGenKeyword` s vysokou režií a zabrání generování událostí pro metody, které jsou uvnitř modulů NGen. Počínaje rozhraním .NET Framework 4.5 by `OverrideAndSuppressNGenEventsKeyword` `NGenKeyword` měly nástroje profilování používat a společně potlačit generování událostí pro metody v modulech NGen. To umožňuje profilování nástroj používat efektivnější NGen PDB získat informace o metodách v modulech NGen. CLR v rozhraní .NET Framework 4 a starší verze nepodporuje vytváření NGen PDBs. V těchto dřívějších verzích CLR `OverrideAndSuppressNGenEventsKeyword` nerozpozná `NGenKeyword` a zpracuje ke generování událostí pro metody v modulech NGen.|  
|`PerfTrackKeyWord`|0x2000000|Umožňuje shromažďování událostí `ModuleLoad` `ModuleRange` a.|  
|`StackKeyword`|0x40000000|Umožňuje shromažďování událostí [trasování zásobníku](stack-etw-event.md)CLR .|  
  
<a name="rundown"></a>
### <a name="clr-etw-rundown-keywords"></a>Clr ETW Rundown Klíčová slova  
 V následující tabulce jsou uvedena klíčová slova clr ETW rundown, jejich hodnoty a k čemu se používají.  
  
|Název klíčového slova Rundown|Hodnota|Účel|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Umožňuje shromažďování událostí zavaděče `StartRundownKeyword` `EndRundownKeyword`při použití s a .|  
|`JitRundownKeyword`|0x00000010|Umožňuje shromažďování metod `DCStart` `DCEnd` a událostí pro metody kompilované `StartRundownKeyword` `EndRundownKeyword`JIT při použití s a .|  
|`NGenRundownKeyword`|0x00000020|Umožňuje kolekci `DCStart` metod `DCEnd` a událostí pro metody nativního obrazu NGen při použití s `StartRundownKeyword` a `EndRundownKeyword`. Toto klíčové slovo má vysokou režii. Generuje události pro každou metodu uvnitř každého načteného modulu NGen. Kdykoli je to možné, namísto použití tohoto klíčového slova, doporučujeme použít programové databáze (PDBs) generované profilovací nástroje k načtení informací o metodách z modulů NGen. Viz `OverrideAndSuppressNGenEventsRundownKeyword` také dále v této tabulce.|  
|`StartRundownKeyword`|0x00000040|Umožňuje výčet stavu systému během spuštění rundown.|  
|`EndRundownKeyword`|0x00000100|Umožňuje výčet stavu systému během ukončení rundown.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Umožňuje shromažďování událostí pro monitorování <xref:System.AppDomain> prostředků na `StartRundownKeyword` úrovni `EndRundownKeyword`při použití s nebo .|  
|`ThreadingKeyword`|0x000100000|Umožňuje kolekci událostí fondu vláken.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x000400000|(K dispozici v rozhraní .NET Framework 4.5 a novější.) Potlačí klíčové slovo `NGenRundownKeyword` s vysokou režií a zabrání generování událostí pro metody, které jsou uvnitř modulů NGen. Počínaje rozhraním .NET Framework 4.5 by `OverrideAndSuppressNGenEventsRundownKeyword` `NGenRundownKeyword` měly nástroje profilování používat a společně potlačit generování událostí pro metody v modulech NGen. To umožňuje profilování nástroj používat efektivnější NGen PDB získat informace o metodách v modulech NGen. CLR v rozhraní .NET Framework 4 a starší verze nepodporuje vytváření NGen PDBs. V těchto dřívějších verzích CLR `OverrideAndSuppressNGenEventsRundownKeyword` nerozpozná `NGenRundownKeyword` a zpracuje ke generování událostí pro metody v modulech NGen.|  
|`PerfTrackKeyWord`|0x2000000|Umožňuje kolekci `ModuleDCStart`, `ModuleDCEnd` `ModuleRangeDCStart`, `ModuleRangeDCEnd` a události.|
  
<a name="runtime_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Kombinace klíčových slov pro rozlišení symbolů pro zprostředkovatele runtime  
  
|Klíčová slova a příznaky|Domény aplikace, sestavení, události načtení/uvolnění modulu|Události načtení a uvolnění metody (kromě dynamických událostí)|Události zatížení/zničení dynamické metody|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Načíst a uvolnit události.|Žádné.|Žádné.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` nepřidává nic)|Žádné.|Načíst události.|Načíst a uvolnit události.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Žádné.|Načíst a uvolnit události.|Načíst a uvolnit události.|  
|`NGenKeyword`|Žádné.|Žádné.|Neužívá se.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Žádné.|Načíst události.|Neužívá se.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Žádné.|Uvolnit události.|Neužívá se.|  
  
<a name="rundown_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Kombinace klíčových slov pro rozlišení symbolů pro zprostředkovatele rundown  
  
|Klíčová slova a příznaky|Aplikační doména, sestavení, události modulu DCStart/DCEnd|Metoda UDÁLOSTI DCStart/DCEnd (včetně událostí dynamické metody)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart`Události.|Žádné.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd`Události.|Žádné.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Žádné.|`DCStart`Události.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Žádné.|`DCEnd`Události.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Žádné.|`DCStart`Události.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Žádné.|`DCEnd`Události.|  

## <a name="etw-event-levels"></a>Úrovně událostí ETW  
 ETW události lze také filtrovat podle úrovně. Pokud je úroveň nastavena na 0x5, jsou vyvolány události všech úrovní, včetně 0x5 a nižší (které jsou události, které patří do kategorií povolených pomocí klíčových slov). Pokud je nastavena úroveň 0x2, jsou vyvolány pouze události, které patří do úrovně 0x2 a nižší.  
  
 Úrovně mají následující významy:  
  
 0x5 - Podrobné  
  
 0x4 - Informační  
  
 0x3 - Upozornění  
  
 0x2 - Chyba  
  
 0x1 - Kritické  
  
 0x0 - LogAlways  
  
## <a name="see-also"></a>Viz také

- [Poskytovatelé CLR ETW](clr-etw-providers.md)
- [Události ETW CLR](clr-etw-events.md)
- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](etw-events-in-the-common-language-runtime.md)
