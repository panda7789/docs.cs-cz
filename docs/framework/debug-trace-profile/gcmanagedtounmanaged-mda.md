---
title: gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9be8165af499729c7b3a95c480cb64d0200e23fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)
`gcManagedToUnmanaged` Pomocník spravovaného ladění (MDA) způsobí, že kolekce paměti vždy, když vlákno přejde ze spravovaného na nespravovaný kód.  
  
## <a name="symptoms"></a>Příznaky  
 Při pokusu o použití spravovaný objekt, který byl vystaven COM., vyvolá komponentu nespravované uživatele porušení přístupu Zdá se, že objekt COM byly vydány. Narušení přístupu není deterministický.  
  
## <a name="cause"></a>příčina  
 Pokud komponentu nespravované není správně spravovaného objektu COM při počítání referencí, může shromažďovat modulu runtime spravovaného objektu vystaven objektům modelu COM, když komponentu nespravované dál obsahuje odkaz na objekt. Volání modulu runtime <xref:System.Runtime.InteropServices.Marshal.Release%2A> během kolekce, takže pokud komponentu uživatel používá objekt předtím, než dojde k uvolnění paměti, pak jej nebude ještě byly shromážděny. Toto je zdroj nondeterminism.  
  
## <a name="resolution"></a>Rozlišení  
 Povolení tohoto pomocníka zkracuje čas mezi když je objekt v vhodné pro kolekce a <xref:System.Runtime.InteropServices.Marshal.Release%2A> je volána, pomáhá sledovat, která nespravované komponenta nejprve pokusí o přístup k objektu shromažďovat.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Vždy, když přechodů přístup z více vláken ze spravovaného na nespravovaný kód způsobí, že uvolnění paměti.  
  
## <a name="output"></a>Výstup  
 Tato MDA neprodukuje žádný výstup.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
