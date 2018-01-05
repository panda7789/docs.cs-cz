---
title: "Klíčová slova a úrovně ETW CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72775d4cb478b6d9c9d2e65119c63f8a34ae47d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clr-etw-keywords-and-levels"></a>Klíčová slova a úrovně ETW CLR
<a name="top"></a>Trasování událostí pro Windows (ETW) události lze filtrovat podle kategorie a úroveň. Událost [CLR ETW – klíčová slova](#keywords) povolit filtrování událostí podle kategorie; se používají v kombinacích runtime a rundown zprostředkovatele. [Úrovně událostí](#levels) jsou identifikovány příznaky.  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>CLR ETW – klíčová slova  
 Klíčová slova jsou příznaky, které mohou být kombinovány ke generování hodnot. V praxi použijte při volání nástroje příkazového řádku hexadecimální hodnoty klíčových slov namísto názvů – klíčové slovo.  
  
 Klíčová slova jsou popsány v následujících tabulkách:  
  
-   [CLR ETW – klíčová slova modulu runtime](#runtime)  
  
-   [CLR ETW – sekvence daneho klíčová slova](#rundown)  
  
-   [Kombinace – klíčové slovo pro překlad symbol pro zprostředkovatele modulu runtime](#runtime_combo)  
  
-   [Kombinace – klíčové slovo pro překlad symbol pro sekvence daneho zprostředkovatele](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>CLR ETW – klíčová slova modulu Runtime  
 Následující tabulka uvádí runtime CLR ETW – klíčová slova, jejich hodnot a jejich použití.  
  
|Název modulu runtime – klíčové slovo|Hodnota|Účel|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Povoluje shromažďování [události uvolňování paměti](../../../docs/framework/performance/garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Povoluje shromažďování [události zavaděče](../../../docs/framework/performance/loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Povoluje shromažďování [události v běhu (JIT)](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Povoluje shromažďování událostí pro metody nativních bitových kopií (metody zpracovávaných generátor, Ngen.exe); použít s `StartEnumerationKeyword` a `EndEnumerationKeyword`. This – klíčové slovo má vysoké režijní náklady. Vygeneruje pro každou metodu uvnitř každých načíst modul NGen události. Kdykoli je to možné, nepoužívejte toto klíčové slovo, doporučujeme načíst informace o metodách z modulů NGen pomocí generované nástroje pro profilaci databáze programu (PDB). Viz také `OverrideAndSuppressNGenEventsKeyword` dál v této tabulce.|  
|`StartEnumerationKeyword`|0x00000040|Umožňuje výčet všech metod v modulu runtime; používá ve spojení s `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Umožňuje výčet všech metod zničen v modulu runtime; používá ve spojení s `JITKeyword` a `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Povoluje shromažďování [události zabezpečení](../../../docs/framework/performance/security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Umožňuje kolekci prostředků sledování událostí na úrovni domény aplikace.|  
|`JITTracingKeyword`|0x00001000|Povoluje shromažďování [JIT – události trasování](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Povoluje shromažďování [události interoperability](../../../docs/framework/performance/interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Povoluje shromažďování [kolizní události](../../../docs/framework/performance/contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Povoluje shromažďování [událostí výjimky](../../../docs/framework/performance/exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Povoluje shromažďování [události fondu vláken](../../../docs/framework/performance/thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(K dispozici v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a novější.) Potlačí nároky na vysokou `NGenKeyword` – klíčové slovo a brání generování událostí pro metody, které jsou uvnitř NGen moduly. Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], nástroje pro profilaci by měl používat `OverrideAndSuppressNGenEventsKeyword` a `NGenKeyword` společně má potlačit generování událostí pro metody v modulech NGen. To umožňuje efektivnější PDB NGen slouží k získání informací o metodách v modulech NGen profilování nástroje. Modul CLR v rozhraní .NET Framework 4 a dřívějších verzích nepodporuje vytvoření NGen soubory PDB. V těchto starších verzí nebudou rozpoznat modulu CLR `OverrideAndSuppressNGenEventsKeyword` a zpracuje `NGenKeyword` generovat události pro metody v modulech NGen.|  
|`PerfTrackKeyWord`|0x2000000|Povoluje shromažďování `ModuleLoad` a `ModuleRange` události.|  
|`StackKeyword`|0x40000000|Povoluje shromažďování CLR [události trasování zásobníku](../../../docs/framework/performance/stack-etw-event.md).|  
  
 [Zpět na začátek](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>CLR ETW – sekvence daneho klíčová slova  
 Následující tabulka uvádí CLR ETW sekvence daneho klíčová slova, jejich hodnot a jejich použití.  
  
|Název sekvence daneho – klíčové slovo|Hodnota|Účel|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Povoluje shromažďování události zavaděče při použití s `StartRundownKeyword` a `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Povoluje shromažďování metoda `DCStart` a `DCEnd` události pro metody kompilována při použití s `StartRundownKeyword` a `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Povoluje shromažďování metoda `DCStart` a `DCEnd` události pro NGen nativních bitových kopií metody při použití s `StartRundownKeyword` a `EndRundownKeyword`. This – klíčové slovo má vysoké režijní náklady. Vygeneruje pro každou metodu uvnitř každých načíst modul NGen události. Kdykoli je to možné, nepoužívejte toto klíčové slovo, doporučujeme načíst informace o metodách z modulů NGen pomocí generované nástroje pro profilaci databáze programu (PDB). Viz také `OverrideAndSuppressNGenEventsRundownKeyword` dál v této tabulce.|  
|`StartRundownKeyword`|0x00000040|Umožňuje výčet stavu systému při spuštění rundown.|  
|`EndRundownKeyword`|0x00000100|Umožňuje výčet stavu systému během rundown end.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Povoluje shromažďování událostí pro sledování prostředků v <xref:System.AppDomain> úrovně při použití s `StartRundownKeyword` nebo `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|Povoluje shromažďování události fondu vláken.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(K dispozici v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a novější.) Potlačí nároky na vysokou `NGenRundownKeyword` – klíčové slovo a brání generování událostí pro metody, které jsou uvnitř NGen moduly. Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], nástroje pro profilaci by měl používat `OverrideAndSuppressNGenEventsRundownKeyword` a `NGenRundownKeyword` společně má potlačit generování událostí pro metody v modulech NGen. To umožňuje efektivnější PDB NGen slouží k získání informací o metodách v modulech NGen profilování nástroje. Modul CLR v rozhraní .NET Framework 4 a dřívějších verzích nepodporuje vytvoření NGen soubory PDB. V těchto starších verzí nebudou rozpoznat modulu CLR `OverrideAndSuppressNGenEventsRundownKeyword` a zpracuje `NGenRundownKeyword` generovat události pro metody v modulech NGen.|  
|`PerfTrackKeyWord`|0x2000000|Povoluje shromažďování `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart`, a `ModuleRangeDCEnd` události.|  
  
 [Zpět na začátek](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Kombinace – klíčové slovo pro překlad Symbol pro zprostředkovatele modulu Runtime  
  
|Klíčová slova a značky|Aplikační domény, sestavení, zatížení a vyřadit události modulu|Zavést a vyřadit události metod (s výjimkou dynamické události)|Události zatížení/odstranění dynamických metod|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Zavedení a uvolnění události.|Žádné|Žádné|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` nepřidává NIC)|Žádné|Načíst události.|Zavedení a uvolnění události.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Žádné|Zavedení a uvolnění události.|Zavedení a uvolnění události.|  
|`NGenKeyword`|Žádné|Žádné|Nelze použít.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Žádné|Načíst události.|Nelze použít.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Žádné|Uvolnění události.|Nelze použít.|  
  
 [Zpět na začátek](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Kombinace – klíčové slovo pro překlad Symbol pro sekvence daneho zprostředkovatele  
  
|Klíčová slova a značky|Aplikační domény, sestavení, DCStart/DCEnd události modulu|Metoda DCStart/DCEnd události (včetně dynamických metoda události)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart`události.|Žádné|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd`události.|Žádné|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Žádné|`DCStart`události.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Žádné|`DCEnd`události.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Žádné|`DCStart`události.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Žádné|`DCEnd`události.|  
  
 [Zpět na začátek](#top)  
  
<a name="levels"></a>   
## <a name="etw-event-levels"></a>Události ETW – úrovně  
 Události trasování událostí je také možné filtrovat podle úrovně. Pokud úroveň je nastavená na hodnotu 0x5, jsou vyvolány události všech úrovních, včetně 0x5 a pod (které jsou události, které patří do kategorií, které zajišťuje klíčová slova). Pokud úroveň je nastavená na 0x2, jenom události, které patří do úrovně 0x2 a níže jsou vyvolány.  
  
 Úrovní záznamu do mají následující významy:  
  
 0x5 - verbose  
  
 0x4 - informační  
  
 0x3 – upozornění  
  
 0x2 – chyba  
  
 0x1 – kritická  
  
 0x0 - LogAlways  
  
## <a name="see-also"></a>Viz také  
 [Poskytovatelé Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-providers.md)  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)  
 [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
