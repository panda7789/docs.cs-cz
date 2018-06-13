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
ms.openlocfilehash: 830a65a4490b1d084e3bb301e89293ccb9424b32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387000"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="d5c4b-102">pInvokeLog – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="d5c4b-102">pInvokeLog MDA</span></span>
<span data-ttu-id="d5c4b-103">`pInvokeLog` Pomocník spravovaného ladění (MDA) je aktivována pro každý jedinečný nespravovaného podpis použít během provádění.</span><span class="sxs-lookup"><span data-stu-id="d5c4b-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d5c4b-104">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="d5c4b-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="d5c4b-105">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d5c4b-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d5c4b-106">Výstup</span><span class="sxs-lookup"><span data-stu-id="d5c4b-106">Output</span></span>  
 <span data-ttu-id="d5c4b-107">Zprávu s upozorněním na platformu vyvolání podpis použít během provádění.</span><span class="sxs-lookup"><span data-stu-id="d5c4b-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d5c4b-108">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d5c4b-108">Configuration</span></span>  
 <span data-ttu-id="d5c4b-109">Každý shodu element filtry souborů DLL, na kterou platformu vyvolat volání jsou vytvářeny.</span><span class="sxs-lookup"><span data-stu-id="d5c4b-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5c4b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5c4b-110">See Also</span></span>  
 [<span data-ttu-id="d5c4b-111">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="d5c4b-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="d5c4b-112">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="d5c4b-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
