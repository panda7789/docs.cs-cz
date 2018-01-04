---
title: "invalidIUnknown – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff88f8bc544c95a4fe5149cd517d9157d5ac23c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
