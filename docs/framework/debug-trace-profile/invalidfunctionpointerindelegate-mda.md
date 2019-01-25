---
title: invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff026ddd9f9dc7c1556c55b285958dad7139e8eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699308"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)
`invalidFunctionPointerInDelegate` Pomocníka spravovaného ladění (MDA) je aktivován, když je neplatný ukazatel na funkci předaný k vytvoření delegáta přes ukazatel na funkci nativní.  
  
## <a name="symptoms"></a>Příznaky  
 Narušení přístupu nebo neočekávaným paměťovým poškození při používání delegáta přes ukazatel na funkci.  
  
## <a name="cause"></a>Příčina  
 Byl zadán neplatný ukazatel na funkci.  
  
## <a name="resolution"></a>Rozlišení  
 Zadejte platný ukazatel  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Ukazatel funkce je neplatný.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
