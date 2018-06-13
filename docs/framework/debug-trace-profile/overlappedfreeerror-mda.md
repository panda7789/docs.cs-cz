---
title: overlappedFreeError – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 301d36820ed5ae1d6ba1cfd2961221095b02bea6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386402"
---
# <a name="overlappedfreeerror-mda"></a>overlappedFreeError – pomocník spravovaného ladění (MDA)
`overlappedFreeError` Pomocník spravovaného ladění (MDA) se aktivuje při <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> metoda je volána před překryté operace byla dokončena.  
  
## <a name="symptoms"></a>Příznaky  
 Narušení přístupu nebo poškození haldy uvolňování paměti.  
  
## <a name="cause"></a>příčina  
 Překryté struktury bylo uvolněno před operace byla dokončena. Funkce, která používá překrytý ukazatel může zapisovat do struktury později, po bylo uvolněno. Vzhledem k tomu, že jiný objekt může nyní zabírají této oblasti, které můžou způsobit poškození haldy.  
  
 Tato MDA nemusí představovat chybu, pokud překryté operaci nebyl úspěšně spuštěn.  
  
## <a name="resolution"></a>Rozlišení  
 Ujistěte se, že vstupně-výstupní operace použitím překryté struktury skončí před voláním <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> metoda.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Zde je ukázkový výstup pro tento (mda).  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
