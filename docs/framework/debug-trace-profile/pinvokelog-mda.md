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
ms.openlocfilehash: a7fe0b33bbd77143da6d2f4a26b170e4d7afe1fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104465"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="c9dcd-102">pInvokeLog – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="c9dcd-102">pInvokeLog MDA</span></span>
<span data-ttu-id="c9dcd-103">`pInvokeLog` Pomocníka spravovaného ladění (MDA) se aktivuje pro každou jedinečnou platformu vyvolání podpis použít během provádění.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c9dcd-104">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="c9dcd-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="c9dcd-105">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c9dcd-106">Výstup</span><span class="sxs-lookup"><span data-stu-id="c9dcd-106">Output</span></span>  
 <span data-ttu-id="c9dcd-107">Zprávu s upozorněním na platformu vyvolání podpis použít během provádění.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c9dcd-108">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c9dcd-108">Configuration</span></span>  
 <span data-ttu-id="c9dcd-109">Každý filtry element shoda soubory .dll, na kterou platformu vyvolání volání jsou provedeny.</span><span class="sxs-lookup"><span data-stu-id="c9dcd-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9dcd-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9dcd-110">See also</span></span>

- [<span data-ttu-id="c9dcd-111">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c9dcd-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c9dcd-112">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="c9dcd-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
