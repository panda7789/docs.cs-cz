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
# <a name="pinvokelog-mda"></a><span data-ttu-id="b1aee-102">pInvokeLog – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="b1aee-102">pInvokeLog MDA</span></span>
<span data-ttu-id="b1aee-103">Pomocník `pInvokeLog` spravovaného ladění (MDA) je aktivován pro každou jedinečnou signaturu vyvolání, která se používá při provádění.</span><span class="sxs-lookup"><span data-stu-id="b1aee-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b1aee-104">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="b1aee-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="b1aee-105">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="b1aee-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b1aee-106">Výstup</span><span class="sxs-lookup"><span data-stu-id="b1aee-106">Output</span></span>  
 <span data-ttu-id="b1aee-107">Zpráva oznamující, že signatura vyvolání platformy použitá při spuštění</span><span class="sxs-lookup"><span data-stu-id="b1aee-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b1aee-108">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="b1aee-108">Configuration</span></span>  
 <span data-ttu-id="b1aee-109">Každý element Match filtruje soubory. dll, na které se volají volání volání platformy.</span><span class="sxs-lookup"><span data-stu-id="b1aee-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1aee-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1aee-110">See also</span></span>

- [<span data-ttu-id="b1aee-111">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="b1aee-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b1aee-112">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="b1aee-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
