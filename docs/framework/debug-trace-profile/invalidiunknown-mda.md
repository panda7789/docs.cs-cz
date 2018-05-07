---
title: invalidIUnknown – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db360a3b7c5f70596d5d5855b8e38dae5d484c42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown – pomocník spravovaného ladění (MDA)
`invalidIUnknown` Pomocník spravovaného ladění (MDA) se aktivuje, když neplatný `IUnknown` ukazatel je předán do spravovaného kódu z nativního kódu. `IUnknown` Nevrátí úspěch při dotázána ohledně `IUnknown` rozhraní.  
  
## <a name="symptoms"></a>Příznaky  
 Při zařazování ukazatele rozhraní COM při zařazování argument dojde k neočekávané chybě.  
  
## <a name="cause"></a>příčina  
 Nesprávné `QueryInterface` implementace na rozhraní COM předaný modulu CLR.  
  
## <a name="resolution"></a>Rozlišení  
 Opravte `QueryInterface` implementace.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Popis chyby.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
