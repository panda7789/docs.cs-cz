---
title: invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff026ddd9f9dc7c1556c55b285958dad7139e8eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699308"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="e9de2-102">invalidFunctionPointerInDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="e9de2-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="e9de2-103">`invalidFunctionPointerInDelegate` Pomocníka spravovaného ladění (MDA) je aktivován, když je neplatný ukazatel na funkci předaný k vytvoření delegáta přes ukazatel na funkci nativní.</span><span class="sxs-lookup"><span data-stu-id="e9de2-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e9de2-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="e9de2-104">Symptoms</span></span>  
 <span data-ttu-id="e9de2-105">Narušení přístupu nebo neočekávaným paměťovým poškození při používání delegáta přes ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="e9de2-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e9de2-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="e9de2-106">Cause</span></span>  
 <span data-ttu-id="e9de2-107">Byl zadán neplatný ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="e9de2-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e9de2-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="e9de2-108">Resolution</span></span>  
 <span data-ttu-id="e9de2-109">Zadejte platný ukazatel</span><span class="sxs-lookup"><span data-stu-id="e9de2-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e9de2-110">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="e9de2-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="e9de2-111">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="e9de2-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e9de2-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="e9de2-112">Output</span></span>  
 <span data-ttu-id="e9de2-113">Ukazatel funkce je neplatný.</span><span class="sxs-lookup"><span data-stu-id="e9de2-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e9de2-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e9de2-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9de2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9de2-115">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e9de2-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="e9de2-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e9de2-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="e9de2-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
