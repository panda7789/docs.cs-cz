---
title: fatalExecutionEngineError – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3fd58ae8f73fd932df641ea96a44ff618dd139e2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052810"
---
# <a name="fatalexecutionengineerror-mda"></a>fatalExecutionEngineError – pomocník spravovaného ladění (MDA)
Pokud byla zjištěna závažná chyba v modulu CLR (Common Language Runtime), je aktivována pomocník spravovanéholadění(MDA).`fatalExecutionEngineError` Proces se ukončí.  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané ukončení procesu. Jiné příznaky nelze určit, protože k selhání CLR může dojít z nejrůznějších důvodů.  
  
## <a name="cause"></a>příčina  
 Modul CLR byl závažně poškozen. To je nejčastěji způsobeno poškozením dat, což může být způsobeno několika problémy, jako jsou volání funkcí vyvolání poškozené platformy a předání neplatných dat modulu CLR.  
  
## <a name="resolution"></a>Řešení  
 Povolení dalších MDA může přispět k identifikaci problému. Následující MDA může být obzvláště užitečná při diagnostice tohoto problému:  
  
- [invalidOverlappedToPinvoke](invalidoverlappedtopinvoke-mda.md)  
  
- [overlappedFreeError](overlappedfreeerror-mda.md)  
  
- [pInvokeStackImbalance](pinvokestackimbalance-mda.md)  
  
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)  
  
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)  
  
- [callbackOnCollectedDelegate](callbackoncollecteddelegate-mda.md)  
  
- [reportAvOnComRelease](reportavoncomrelease-mda.md)  
  
- [invalidVariant](invalidvariant-mda.md)  
  
- [invalidIUnknown](invalidiunknown-mda.md)  
  
- [raceOnRCWCleanup](raceonrcwcleanup-mda.md)  
  
- [invalidFunctionPointerInDelegate](invalidfunctionpointerindelegate-mda.md)  
  
- [invalidGCHandleCookie](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na chování modulu runtime.  
  
## <a name="output"></a>Výstup  
 Adresa funkce CLR, která způsobila závažnou chybu, ID vlákna, ve kterém došlo k chybě, a kód chyby.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
