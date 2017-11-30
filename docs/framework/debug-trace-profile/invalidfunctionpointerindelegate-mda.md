---
title: "invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e9fd1faacc7be5b95e2bab0d8fdbee105e35498
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="a063f-102">invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="a063f-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="a063f-103">`invalidFunctionPointerInDelegate` Pomocník spravovaného ladění (MDA) je aktivovat, pokud je předaná neplatný ukazatel funkce vytvořit delegáta přes nativní funkce ukazatel.</span><span class="sxs-lookup"><span data-stu-id="a063f-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a063f-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a063f-104">Symptoms</span></span>  
 <span data-ttu-id="a063f-105">Narušení přístupu nebo poškození neočekávané paměti při použití delegáta přes ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="a063f-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a063f-106">příčina</span><span class="sxs-lookup"><span data-stu-id="a063f-106">Cause</span></span>  
 <span data-ttu-id="a063f-107">Byl zadán neplatný ukazatel funkce.</span><span class="sxs-lookup"><span data-stu-id="a063f-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a063f-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="a063f-108">Resolution</span></span>  
 <span data-ttu-id="a063f-109">Zadejte platnou funkcí ukazatele</span><span class="sxs-lookup"><span data-stu-id="a063f-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a063f-110">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="a063f-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="a063f-111">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="a063f-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a063f-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="a063f-112">Output</span></span>  
 <span data-ttu-id="a063f-113">Ukazatel neplatná funkce.</span><span class="sxs-lookup"><span data-stu-id="a063f-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a063f-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a063f-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a063f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a063f-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="a063f-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a063f-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a063f-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="a063f-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
