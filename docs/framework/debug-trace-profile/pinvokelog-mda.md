---
title: pInvokeLog – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0883849eee12922601e50c2337bb0048d77cab68
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052379"
---
# <a name="pinvokelog-mda"></a>pInvokeLog – pomocník spravovaného ladění (MDA)
Pomocník `pInvokeLog` spravovaného ladění (MDA) je aktivován pro každou jedinečnou signaturu vyvolání, která se používá při provádění.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že signatura vyvolání platformy použitá při spuštění  
  
## <a name="configuration"></a>Konfiguraci  
 Každý element Match filtruje soubory. dll, na které se volají volání volání platformy.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Používání nespravovaných funkcí DLL](../interop/consuming-unmanaged-dll-functions.md)
