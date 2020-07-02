---
title: overlappedFreeError – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění overlappedFreeError – (MDA) v rozhraní .NET, který se může aktivovat při narušení přístupu nebo poškození haldy uvolňování paměti.
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 9be33c59723ecb2743f2bc610d7fb69d24ff388c
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803909"
---
# <a name="overlappedfreeerror-mda"></a>overlappedFreeError – pomocník spravovaného ladění (MDA)
`overlappedFreeError`Pokud <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> je metoda volána před dokončením překryté operace, je aktivována funkce pomocník spravovaného ladění (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Narušení přístupu nebo poškození haldy uvolňování paměti.  
  
## <a name="cause"></a>Příčina  
 Překrytá struktura byla uvolněna před dokončením operace. Funkce, která používá překrytý ukazatel, může zapisovat do struktury později poté, co byla uvolněna. To může způsobit poškození haldy, protože teď jiný objekt může tuto oblast zabírat.  
  
 V případě, že se překrytá operace nezačala úspěšně, tato aplikace MDA nemusí představovat chybu.  
  
## <a name="resolution"></a>Řešení  
 Před voláním metody zajistěte, aby byla vstupně-výstupní operace s použitím překryté struktury dokončená <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> .  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Níže je ukázkový výstup pro tento MDA.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
