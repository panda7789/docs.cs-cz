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
ms.openlocfilehash: fe1d783017369a78074e5abf278ac2facf6ee32b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734062"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="19bdb-102">pInvokeLog – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="19bdb-102">pInvokeLog MDA</span></span>
<span data-ttu-id="19bdb-103">`pInvokeLog` Pomocníka spravovaného ladění (MDA) se aktivuje pro každou jedinečnou platformu vyvolání podpis použít během provádění.</span><span class="sxs-lookup"><span data-stu-id="19bdb-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="19bdb-104">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="19bdb-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="19bdb-105">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="19bdb-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="19bdb-106">Výstup</span><span class="sxs-lookup"><span data-stu-id="19bdb-106">Output</span></span>  
 <span data-ttu-id="19bdb-107">Zprávu s upozorněním na platformu vyvolání podpis použít během provádění.</span><span class="sxs-lookup"><span data-stu-id="19bdb-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="19bdb-108">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="19bdb-108">Configuration</span></span>  
 <span data-ttu-id="19bdb-109">Každý filtry element shoda soubory .dll, na kterou platformu vyvolání volání jsou provedeny.</span><span class="sxs-lookup"><span data-stu-id="19bdb-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19bdb-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19bdb-110">See also</span></span>
- [<span data-ttu-id="19bdb-111">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="19bdb-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="19bdb-112">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="19bdb-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
