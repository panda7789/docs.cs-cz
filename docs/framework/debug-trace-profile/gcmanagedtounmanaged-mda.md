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
ms.openlocfilehash: afc0fd47e51723a7b3ba1b07dffc49260f88917d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052775"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)
Pomocník `gcManagedToUnmanaged` spravovaného ladění (MDA) způsobuje uvolnění paměti při každém přechodu vlákna ze spravovaného do nespravovaného kódu.  
  
## <a name="symptoms"></a>Příznaky  
 Nespravovaná uživatelská komponenta vyvolá narušení přístupu při pokusu o použití spravovaného objektu, který byl vystaven modelu COM. Zdá se, že objekt COM byl vydán. Porušení přístupu není deterministické.  
  
## <a name="cause"></a>příčina  
 Pokud nespravovaná komponenta neodkazuje správně na počítání spravovaného objektu COM, pak modul runtime může shromáždit spravované objekty, které jsou vystaveny modelu COM v případě, že nespravované součásti stále drží odkaz na objekt. Běhové volání <xref:System.Runtime.InteropServices.Marshal.Release%2A> během uvolňování paměti, takže pokud uživatelská komponenta používá objekt před uvolněním paměti, pak se ještě neshromáždí. Toto je zdroj nondeterminism.  
  
## <a name="resolution"></a>Řešení  
 Povolení tohoto pomocníka zkracuje dobu mezi tím, kdy je objekt způsobilý pro shromažďování <xref:System.Runtime.InteropServices.Marshal.Release%2A> a je volán, což pomáhá sledovat, která nespravované komponenty se nejprve pokusí o přístup k shromážděnému objektu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Způsobí uvolnění paměti při každém přechodu vlákna ze spravovaného do nespravovaného kódu.  
  
## <a name="output"></a>Výstup  
 Tento MDA nevytváří žádný výstup.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
