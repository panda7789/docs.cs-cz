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
ms.openlocfilehash: 35560b966d5fba60ac35b2eb1e559e196fc868f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754532"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown – pomocník spravovaného ladění (MDA)
`invalidIUnknown` Pomocníka spravovaného ladění (MDA) se aktivuje, když neplatný `IUnknown` předán ukazatel do spravovaného kódu z nativního kódu. `IUnknown` Nevrátí úspěch, když se dotázali `IUnknown` rozhraní.  
  
## <a name="symptoms"></a>Příznaky  
 Při zařazování při zařazování argument ukazatele rozhraní modelu COM, dojde k neočekávané chybě.  
  
## <a name="cause"></a>Příčina  
 Nesprávné `QueryInterface` implementace na rozhraní COM předán modulu CLR.  
  
## <a name="resolution"></a>Řešení  
 Opravte `QueryInterface` implementace.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
