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
ms.openlocfilehash: cbb33d2cddab22ad2072354ba543d2cd6a60a668
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218274"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)
`invalidFunctionPointerInDelegate` Pomocníka spravovaného ladění (MDA) je aktivován, když je neplatný ukazatel na funkci předaný k vytvoření delegáta přes ukazatel na funkci nativní.  
  
## <a name="symptoms"></a>Příznaky  
 Narušení přístupu nebo neočekávaným paměťovým poškození při používání delegáta přes ukazatel na funkci.  
  
## <a name="cause"></a>Příčina  
 Byl zadán neplatný ukazatel na funkci.  
  
## <a name="resolution"></a>Řešení  
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
