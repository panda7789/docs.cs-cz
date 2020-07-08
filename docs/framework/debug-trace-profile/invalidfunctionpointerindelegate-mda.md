---
title: invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění invalidFunctionPointerInDelegate (MDA), který je vyvolán, pokud je předán neplatný ukazatel na funkci pro vytvoření delegáta.
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
ms.openlocfilehash: a17427d117c62ba782af3c9549c84623a3013b06
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051737"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)
`invalidFunctionPointerInDelegate`Pomocník spravovaného ladění (MDA) je aktivován, pokud je předán neplatný ukazatel na funkci, aby bylo možné vytvořit delegáta nad ukazatelem nativní funkce.  
  
## <a name="symptoms"></a>Příznaky  
 Při použití delegáta přes ukazatel na funkci došlo k narušení přístupu nebo neočekávanému poškození paměti.  
  
## <a name="cause"></a>Příčina  
 Byl zadán neplatný ukazatel na funkci.  
  
## <a name="resolution"></a>Řešení  
 Zadejte platný ukazatel na funkci.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Neplatný ukazatel na funkci.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
