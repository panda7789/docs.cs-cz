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
ms.openlocfilehash: 7bb4779e300df71a5d075a322bcac8398ce42f34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204273"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)
`gcManagedToUnmanaged` Pomocníka spravovaného ladění (MDA) způsobí, že uvolňování paměti pokaždé, když vlákno přejde ze spravovaného do nespravovaného kódu.  
  
## <a name="symptoms"></a>Příznaky  
 Jako součást nespravovaný uživatelský vyvolá narušení přístupu při pokusu o použití spravovaný objekt, který měl byly vystaveny objektům modelu COM. Zdá se, že objekt modelu COM byly vydány. Porušení přístupu je nedeterministická.  
  
## <a name="cause"></a>Příčina  
 Pokud nespravované součásti není správně spravovaný objekt modelu COM pro počítání odkazů, modul runtime může shromažďovat vystavit rozhraní COM při nespravované součásti dál obsahuje odkaz na objekt spravovaný objekt. Modul runtime zavolá <xref:System.Runtime.InteropServices.Marshal.Release%2A> během uvolnění paměti, takže pokud uživatel součást používá objekt, než dojde k uvolnění paměti, pak ji nebude ještě byly shromážděny. Toto je zdroj nondeterminism.  
  
## <a name="resolution"></a>Řešení  
 Povolení tohoto Pomocníka s nastavením zkracuje dobu mezi při objekt je vhodné pro kolekci a <xref:System.Runtime.InteropServices.Marshal.Release%2A> je volána, pomáhá sledovat, jaká součást nespravované se nejprve pokusí o přístup k shromážděné objekty.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Pokaždé, když vlákno přechody ze spravovaného do nespravovaného kódu způsobí, že uvolňování paměti.  
  
## <a name="output"></a>Výstup  
 Toto MDA negeneruje žádný výstup.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
- [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
