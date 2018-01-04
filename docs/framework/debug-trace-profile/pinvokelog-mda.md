---
title: "pInvokeLog – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 343ec424105d1c775592aba316b50da4010f7c8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="0b81e-102">pInvokeLog – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="0b81e-102">pInvokeLog MDA</span></span>
<span data-ttu-id="0b81e-103">`pInvokeLog` Pomocník spravovaného ladění (MDA) je aktivována pro každý jedinečný nespravovaného podpis použít během provádění.</span><span class="sxs-lookup"><span data-stu-id="0b81e-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0b81e-104">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="0b81e-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="0b81e-105">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0b81e-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0b81e-106">Výstup</span><span class="sxs-lookup"><span data-stu-id="0b81e-106">Output</span></span>  
 <span data-ttu-id="0b81e-107">Zprávu s upozorněním na platformu vyvolání podpis použít během provádění.</span><span class="sxs-lookup"><span data-stu-id="0b81e-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0b81e-108">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0b81e-108">Configuration</span></span>  
 <span data-ttu-id="0b81e-109">Každý shodu element filtry souborů DLL, na kterou platformu vyvolat volání jsou vytvářeny.</span><span class="sxs-lookup"><span data-stu-id="0b81e-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0b81e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b81e-110">See Also</span></span>  
 [<span data-ttu-id="0b81e-111">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="0b81e-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="0b81e-112">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="0b81e-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
