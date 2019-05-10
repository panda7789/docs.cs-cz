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
ms.openlocfilehash: b9a9061503ae4bf68903f35eb7624deed2f34c9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616602"
---
# <a name="clr-etw-keywords-and-levels"></a>Klíčová slova a úrovně ETW CLR
<a name="top"></a> Trasování událostí pro Windows (ETW) se dá filtrovat podle kategorie a úroveň. Událost [CLR ETW – klíčová slova](#keywords) možnost filtrovat události podle kategorie; se používají v kombinacích pro zprostředkovatele běhového prostředí a doběhu. [Událostí úrovně](#levels) jsou označeny příznaky.  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>CLR ETW – klíčová slova  
 Klíčová slova jsou příznaky, které mohou být kombinovány pro generování hodnot. V praxi šestnáctkové hodnoty klíčových slov použít místo názvů – klíčové slovo při volání nástroje příkazového řádku.  
  
 Klíčová slova jsou popsány v následujících tabulkách:  
  
- [Modul runtime CLR ETW – klíčová slova](#runtime)  
  
- [Doběhu klíčová slova CLR ETW](#rundown)  
  
- [Kombinace – klíčové slovo pro rozlišení symbolů pro zprostředkovatel běhového prostředí](#runtime_combo)  
  
- [Kombinace – klíčové slovo pro rozlišení symbolů pro zprostředkovatele doběhu](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>Modul Runtime CLR ETW – klíčová slova  
 V následující tabulce jsou uvedeny klíčová slova CLR ETW runtime, jejich hodnoty a jejich použití.  
  
|Název modulu runtime – klíčové slovo|Value|Účel|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Povoluje shromažďování [události kolekce paměti](../../../docs/framework/performance/garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Povoluje shromažďování [události zavaděče](../../../docs/framework/performance/loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Povoluje shromažďování [just-in-time (JIT) události](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Umožňuje shromažďování událostí pro nativní bitové kopie metody (metody zpracovány Native Image Generator Ngen.exe); použít s `StartEnumerationKeyword` a `EndEnumerationKeyword`. Toto klíčové slovo má vysoké režijní náklady. Generuje události pro každou metodu uvnitř všechny načtené moduly NGen. Pokaždé, když je to možné, namísto použití toto klíčové slovo, doporučujeme použít databáze programu (PDB) generovaných nástroje pro profilaci k načtení informací o metodách z modulů technologie NGen. Viz také `OverrideAndSuppressNGenEventsKeyword` dále v této tabulce.|  
|`StartEnumerationKeyword`|0x00000040|Umožňuje výčet všech metod v modulu runtime; použít ve spojení s `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Umožňuje výčet všech metod, které jsou zničeny v modulu runtime; použít ve spojení s `JITKeyword` a `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Povoluje shromažďování [události zabezpečení](../../../docs/framework/performance/security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Umožňuje kolekci prostředků, monitorování událostí na úrovni domény aplikace.|  
|`JITTracingKeyword`|0x00001000|Povoluje shromažďování [JIT – události trasování](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Povoluje shromažďování [události interoperability](../../../docs/framework/performance/interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Povoluje shromažďování [kolizní události](../../../docs/framework/performance/contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Povoluje shromažďování [události výjimky](../../../docs/framework/performance/exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Povoluje shromažďování [události fondu vláken](../../../docs/framework/performance/thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(K dispozici v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a novější.) Potlačí nároky na vysoce `NGenKeyword` – klíčové slovo a brání generování události pro metody, které jsou uvnitř modulů technologie NGen. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], nástroje pro profilaci používejte `OverrideAndSuppressNGenEventsKeyword` a `NGenKeyword` společně má potlačit generování událostí pro metody v modulech NGen. To umožňuje profilování nástroje můžete získat informace o metodách v modulech NGen efektivnější souborů PDB pro NGen. V rozhraní .NET Framework 4 a dřívějších verzích CLR nepodporuje vytváření souborů PDB pro NGen. V těchto starších verzí modulu CLR nerozpozná `OverrideAndSuppressNGenEventsKeyword` a zpracuje `NGenKeyword` generovat události pro metody v modulech NGen.|  
|`PerfTrackKeyWord`|0x2000000|Povoluje shromažďování `ModuleLoad` a `ModuleRange` události.|  
|`StackKeyword`|0x40000000|Povolí shromažďování CLR [události trasování zásobníku](../../../docs/framework/performance/stack-etw-event.md).|  
  
 [Zpět na začátek](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>Doběhu klíčová slova CLR ETW  
 V následující tabulce jsou uvedeny doběhu klíčová slova CLR ETW, jejich hodnoty a jejich použití.  
  
|Název doběhu – klíčové slovo|Value|Účel|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Umožňuje shromažďování událostí zavaděče při použití s `StartRundownKeyword` a `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Povolí shromažďování metoda `DCStart` a `DCEnd` události pro metody zkompilované JIT při použití s `StartRundownKeyword` a `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Povolí shromažďování metoda `DCStart` a `DCEnd` události pro metody nativních bitových kopií technologie NGen při použití s `StartRundownKeyword` a `EndRundownKeyword`. Toto klíčové slovo má vysoké režijní náklady. Generuje události pro každou metodu uvnitř všechny načtené moduly NGen. Pokaždé, když je to možné, namísto použití toto klíčové slovo, doporučujeme použít databáze programu (PDB) generovaných nástroje pro profilaci k načtení informací o metodách z modulů technologie NGen. Viz také `OverrideAndSuppressNGenEventsRundownKeyword` dále v této tabulce.|  
|`StartRundownKeyword`|0x00000040|Umožňuje výčet stavu systému během začátek doběhu.|  
|`EndRundownKeyword`|0x00000100|Umožňuje výčet stavu systému během konec doběhu.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Umožňuje shromažďování událostí pro sledování prostředků na <xref:System.AppDomain> úroveň při použití s `StartRundownKeyword` nebo `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|Povoluje shromažďování události fondu vláken.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(K dispozici v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a novější.) Potlačí nároky na vysoce `NGenRundownKeyword` – klíčové slovo a brání generování události pro metody, které jsou uvnitř modulů technologie NGen. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], nástroje pro profilaci používejte `OverrideAndSuppressNGenEventsRundownKeyword` a `NGenRundownKeyword` společně má potlačit generování událostí pro metody v modulech NGen. To umožňuje profilování nástroje můžete získat informace o metodách v modulech NGen efektivnější souborů PDB pro NGen. V rozhraní .NET Framework 4 a dřívějších verzích CLR nepodporuje vytváření souborů PDB pro NGen. V těchto starších verzí modulu CLR nerozpozná `OverrideAndSuppressNGenEventsRundownKeyword` a zpracuje `NGenRundownKeyword` generovat události pro metody v modulech NGen.|  
|`PerfTrackKeyWord`|0x2000000|Povoluje shromažďování `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart`, a `ModuleRangeDCEnd` události.|  
  
 [Zpět na začátek](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Kombinace – klíčové slovo pro rozlišení symbolů pro zprostředkovatel běhového prostředí  
  
|Klíčová slova a příznaky|Aplikační domény, sestavení, události načtení/uvolnění modulu|Metoda načtení/uvolnění události (s výjimkou dynamického události)|Dynamická metoda load/odstranění události|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Načtení a uvolnění události.|Žádné|Žádné|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` nepřidává NIC)|Žádné|Načíst události.|Načtení a uvolnění události.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Žádné|Načtení a uvolnění události.|Načtení a uvolnění události.|  
|`NGenKeyword`|Žádné|Žádné|Není k dispozici.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Žádné|Načíst události.|Není k dispozici.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Žádné|Uvolnění události.|Není k dispozici.|  
  
 [Zpět na začátek](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Kombinace – klíčové slovo pro rozlišení symbolů pro zprostředkovatele doběhu  
  
|Klíčová slova a příznaky|Aplikační domény, sestavení, události modulu DCStart/DCEnd|Metoda DCStart/DCEnd události (včetně dynamickou metodu události)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart` události.|Žádné|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd` události.|Žádné|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Žádné|`DCStart` události.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Žádné|`DCEnd` události.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Žádné|`DCStart` události.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Žádné|`DCEnd` události.|  
  
 [Zpět na začátek](#top)  
  
<a name="levels"></a>   
## <a name="etw-event-levels"></a>Úrovně událostí trasování událostí pro Windows  
 Události trasování událostí pro Windows je také možné filtrovat podle úrovně. Pokud úroveň je nastavená na 0x5, jsou vyvolány události všech úrovní, včetně 0x5 a pod (které jsou události, které patří do kategorií pomocí klíčových slov povolena). Pokud úroveň je nastavená na 0x2, jsou vyvolány pouze události, které patří do úrovně 0x2 a níže.  
  
 Úrovně mají následující význam:  
  
 0x5 - verbose  
  
 0x4 – informační  
  
 0x3 – upozornění  
  
 0x2 – chyba  
  
 0x1 – kritické  
  
 0x0 - LogAlways  
  
## <a name="see-also"></a>Viz také:

- [Poskytovatelé Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-providers.md)
- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
