---
title: pInvokeLog – pomocník spravovaného ladění (MDA)
description: Pochopení pomocníka spravovaného ladění pInvokeLog – (MDA), který se aktivuje pro každou jedinečnou identifikaci platformy, která se používá při provádění v rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: 05af4e17a91f7c0d8f3576a86d3d784ef6666aed
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803687"
---
# <a name="pinvokelog-mda"></a>pInvokeLog – pomocník spravovaného ladění (MDA)
`pInvokeLog`Pomocník spravovaného ladění (MDA) je aktivován pro každou jedinečnou signaturu vyvolání, která se používá při provádění.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující, že signatura vyvolání platformy použitá při spuštění  
  
## <a name="configuration"></a>Konfigurace  
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
