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
ms.openlocfilehash: 66f662114868832f909d734a482e1dc9aefb841a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754476"
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged – pomocník spravovaného ladění
`gcUnmanagedToManaged` Pomocníka spravovaného ladění (MDA) způsobí, že uvolňování paměti pokaždé, když vlákno přejde z nespravovaného do spravovaného kódu.  
  
## <a name="symptoms"></a>Příznaky  
 Vyvolat pomocí modelu COM a platformy spuštěné nespravovaný uživatelský komponenty aplikace způsobuje narušení přístupu nedeterministická v CLR.  
  
## <a name="cause"></a>Příčina  
 Pokud aplikace běží nespravované součásti, pak tyto součásti pravděpodobně došlo k poškození haldy uvolňování. To způsobí, že porušení přístupu v CLR systému uvolňování paměti se pokusí vás grafu objektů.  
  
## <a name="resolution"></a>Řešení  
 Povolení tohoto Pomocníka s nastavením zkracuje dobu mezi při nespravované součásti poškození haldy uvolňování a po porušení přístupu se stane, můžete vynutit uvolnění paměti dojde k před každý spravovaný přechod.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Pokaždé, když přechody vláken z nespravovaného do spravovaného kódu způsobí, že uvolňování paměti.  
  
## <a name="output"></a>Výstup  
 Toto MDA negeneruje žádný výstup.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
