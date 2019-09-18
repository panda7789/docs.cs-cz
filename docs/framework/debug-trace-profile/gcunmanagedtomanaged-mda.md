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
ms.openlocfilehash: 1679f87276262a08f5717ea81d263f4600542971
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052765"
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged – pomocník spravovaného ladění
Pomocník `gcUnmanagedToManaged` spravovaného ladění (MDA) způsobuje uvolnění paměti při každém přechodu vlákna z nespravovaného do spravovaného kódu.  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace, která spouští nespravované uživatelské komponenty pomocí modelu COM a vyvolání platformy, způsobuje nedeterministické porušení přístupu v modulu CLR.  
  
## <a name="cause"></a>příčina  
 Pokud aplikace spouští nespravované uživatelské komponenty, mohou tyto součásti poškodit haldu uvolňování paměti. Tím dojde k porušení přístupu v modulu CLR, když se systém uvolňování paměti pokusí projít graf objektu.  
  
## <a name="resolution"></a>Řešení  
 Povolení tohoto pomocníka zkracuje dobu mezi tím, kdy nespravovaná komponenta poškozuje uvolňování paměti, a když dojde k narušení přístupu vynuceným uvolňováním paměti před každým spravovaným přechodem.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Způsobí uvolnění paměti při každém přechodu vlákna z nespravovaného do spravovaného kódu.  
  
## <a name="output"></a>Výstup  
 Tento MDA nevytváří žádný výstup.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
