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
ms.openlocfilehash: f7e6334e20a6e0db1d52307a833de0ecd0d74cc4
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217474"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)
`gcManagedToUnmanaged` Pomocník pro spravované ladění (MDA) způsobí uvolnění paměti při každém přechodu vlákna ze spravovaného do nespravovaného kódu.  
  
## <a name="symptoms"></a>Příznaky  
 Nespravovaná uživatelská komponenta vyvolá narušení přístupu při pokusu o použití spravovaného objektu, který byl vystaven modelu COM. Zdá se, že objekt COM byl vydán. Porušení přístupu není deterministické.  
  
## <a name="cause"></a>Příčina  
 Pokud nespravovaná komponenta neodkazuje správně na počítání spravovaného objektu COM, pak modul runtime může shromáždit spravované objekty, které jsou vystaveny modelu COM v případě, že nespravované součásti stále drží odkaz na objekt. Běhové volání <xref:System.Runtime.InteropServices.Marshal.Release%2A> během uvolňování paměti, takže pokud uživatelská komponenta používá objekt ještě před uvolněním paměti, pak se ještě neshromáždí. Toto je zdroj nondeterminism.  
  
## <a name="resolution"></a>Řešení  
 Povolení tohoto pomocníka zkracuje dobu mezi tím, kdy je objekt způsobilý pro shromažďování a <xref:System.Runtime.InteropServices.Marshal.Release%2A> je volána, což pomáhá sledovat, která nespravované komponenty se nejprve pokusí o přístup k shromážděnému objektu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Způsobí uvolnění paměti při každém přechodu vlákna ze spravovaného do nespravovaného kódu.  
  
## <a name="output"></a>Výstup  
 Tento MDA nevytváří žádný výstup.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
