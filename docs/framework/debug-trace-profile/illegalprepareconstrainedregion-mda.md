---
title: "illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dad43859e6bec288b66c6c10256a6b2cbc1bbe0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="790c3-102">illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="790c3-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="790c3-103">`illegalPrepareConstrainedRegion` Pomocník spravovaného ladění (MDA) se aktivuje při <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> volání metody nepředchází okamžitě `try` prohlášení o obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="790c3-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="790c3-104">Toto omezení je na MSIL úroveň, tak, aby byl povolený mít jiný kód generování zdroj mezi volání a `try`, jako je například komentáře.</span><span class="sxs-lookup"><span data-stu-id="790c3-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="790c3-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="790c3-105">Symptoms</span></span>  
 <span data-ttu-id="790c3-106">Oblasti omezeného provádění (CER), která se nikdy považuje jako takový, ale jako jednoduchý výjimka zpracování blok (`finally` nebo `catch`).</span><span class="sxs-lookup"><span data-stu-id="790c3-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="790c3-107">V důsledku toho oblasti nespouští v události podmínku nedostatku paměti nebo přerušení přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="790c3-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="790c3-108">příčina</span><span class="sxs-lookup"><span data-stu-id="790c3-108">Cause</span></span>  
 <span data-ttu-id="790c3-109">Tento vzor přípravy CER nedodržíte správně.</span><span class="sxs-lookup"><span data-stu-id="790c3-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="790c3-110">Toto je událost chyby.</span><span class="sxs-lookup"><span data-stu-id="790c3-110">This is an error event.</span></span> <span data-ttu-id="790c3-111"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Volání metody, které používá se k označení obslužné rutiny výjimek jako představení CER v jejich `catch` / `finally` / `fault` / `filter` bloky se musí použít bezprostředně před `try` příkaz.</span><span class="sxs-lookup"><span data-stu-id="790c3-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="790c3-112">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="790c3-112">Resolution</span></span>  
 <span data-ttu-id="790c3-113">Ujistěte se, že volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> se stane bezprostředně před `try` příkaz.</span><span class="sxs-lookup"><span data-stu-id="790c3-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="790c3-114">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="790c3-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="790c3-115">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="790c3-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="790c3-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="790c3-116">Output</span></span>  
 <span data-ttu-id="790c3-117">MDA zobrazí název volání metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodu, posun MSIL a zprávu s upozorněním, volání nepředchází okamžitě začátku bloku try.</span><span class="sxs-lookup"><span data-stu-id="790c3-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="790c3-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="790c3-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="790c3-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="790c3-119">Example</span></span>  
 <span data-ttu-id="790c3-120">Následující příklad kódu ukazuje vzor, který způsobuje, že tento MDA chcete aktivovat.</span><span class="sxs-lookup"><span data-stu-id="790c3-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```  
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="790c3-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="790c3-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>  
 [<span data-ttu-id="790c3-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="790c3-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="790c3-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="790c3-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
