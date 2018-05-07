---
title: gcUnmanagedToManaged – pomocník spravovaného ladění
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dfaa77adef7cdc21b1ad8abaca1439361a33d4b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged – pomocník spravovaného ladění
`gcUnmanagedToManaged` Pomocník spravovaného ladění (MDA) způsobí, že kolekce paměti vždy, když vlákno přechází z nespravovaného do spravovaného kódu.  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace běžící nespravované uživatelské komponenty pomocí COM a platforma vyvolání způsobuje narušení nedeterministická přístup v modulu CLR.  
  
## <a name="cause"></a>příčina  
 Pokud aplikace běží nespravované uživatelské komponenty, pak tyto součásti pravděpodobně došlo k poškození haldy uvolňování paměti. To způsobí, že porušení přístupu v modulu CLR při uvolňování paměti se pokusí vás grafu objektu.  
  
## <a name="resolution"></a>Rozlišení  
 Povolení tohoto pomocníka zkracuje dobu mezi při komponentu nespravované poškození haldy uvolňování paměti a když se stane narušení přístupu vynucením uvolňování před každý spravovaný přechod.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Vždy, když přechody přístup z více vláken z nespravovaného do spravovaného kódu způsobí, že uvolnění paměti.  
  
## <a name="output"></a>Výstup  
 Tato MDA neprodukuje žádný výstup.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
