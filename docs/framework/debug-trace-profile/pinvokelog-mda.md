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
ms.openlocfilehash: 12d7f60bcaedc5a97a7718610f40188547f87050
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216115"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="6703b-102">pInvokeLog – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="6703b-102">pInvokeLog MDA</span></span>
<span data-ttu-id="6703b-103">Pro každou jedinečnou signaturu vyvolání, která se používá při provádění, se aktivuje Pomocník pro na`pInvokeLog` spravované ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="6703b-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6703b-104">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="6703b-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="6703b-105">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="6703b-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6703b-106">Výstup</span><span class="sxs-lookup"><span data-stu-id="6703b-106">Output</span></span>  
 <span data-ttu-id="6703b-107">Zpráva oznamující, že signatura vyvolání platformy použitá při spuštění</span><span class="sxs-lookup"><span data-stu-id="6703b-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6703b-108">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6703b-108">Configuration</span></span>  
 <span data-ttu-id="6703b-109">Každý element Match filtruje soubory. dll, na které se volají volání volání platformy.</span><span class="sxs-lookup"><span data-stu-id="6703b-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6703b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="6703b-110">See also</span></span>

- [<span data-ttu-id="6703b-111">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="6703b-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6703b-112">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="6703b-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
