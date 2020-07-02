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
# <a name="pinvokelog-mda"></a><span data-ttu-id="e983e-103">pInvokeLog – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="e983e-103">pInvokeLog MDA</span></span>
<span data-ttu-id="e983e-104">`pInvokeLog`Pomocník spravovaného ladění (MDA) je aktivován pro každou jedinečnou signaturu vyvolání, která se používá při provádění.</span><span class="sxs-lookup"><span data-stu-id="e983e-104">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e983e-105">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="e983e-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="e983e-106">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="e983e-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e983e-107">Výstup</span><span class="sxs-lookup"><span data-stu-id="e983e-107">Output</span></span>  
 <span data-ttu-id="e983e-108">Zpráva oznamující, že signatura vyvolání platformy použitá při spuštění</span><span class="sxs-lookup"><span data-stu-id="e983e-108">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e983e-109">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e983e-109">Configuration</span></span>  
 <span data-ttu-id="e983e-110">Každý element Match filtruje soubory. dll, na které se volají volání volání platformy.</span><span class="sxs-lookup"><span data-stu-id="e983e-110">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e983e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e983e-111">See also</span></span>

- [<span data-ttu-id="e983e-112">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="e983e-112">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e983e-113">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="e983e-113">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
