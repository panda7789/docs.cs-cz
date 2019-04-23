---
title: illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23a36d1709f03583ce39af0e7c80bb1ecd7cf809
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158974"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="162a6-102">illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="162a6-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="162a6-103">`illegalPrepareConstrainedRegion` Pomocníka spravovaného ladění (MDA) se aktivuje při <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> volání metody bezprostředně nepředchází `try` příkaz obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="162a6-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="162a6-104">Toto omezení je na jazyk MSIL úrovně, takže je přípustné, aby bez kódu generování zdroje mezi volání a `try`, například pro komentáře.</span><span class="sxs-lookup"><span data-stu-id="162a6-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="162a6-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="162a6-105">Symptoms</span></span>  
 <span data-ttu-id="162a6-106">Oblasti omezeného provádění (CER), který se nikdy zpracováván jako takové, ale jako jednoduchý výjimka bloku zpracování (`finally` nebo `catch`).</span><span class="sxs-lookup"><span data-stu-id="162a6-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="162a6-107">V důsledku toho oblast nejde spustit v případě podmínku paměti nebo přerušení vlákna.</span><span class="sxs-lookup"><span data-stu-id="162a6-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="162a6-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="162a6-108">Cause</span></span>  
 <span data-ttu-id="162a6-109">Vzor přípravy CER nedodrží správně.</span><span class="sxs-lookup"><span data-stu-id="162a6-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="162a6-110">Toto je událost chyby.</span><span class="sxs-lookup"><span data-stu-id="162a6-110">This is an error event.</span></span> <span data-ttu-id="162a6-111"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Volání metody používá k označení obslužné rutiny výjimek jako Představujeme CER v jejich `catch` / `finally` / `fault` / `filter` bloky musí být použita bezprostředně před `try` příkazu.</span><span class="sxs-lookup"><span data-stu-id="162a6-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="162a6-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="162a6-112">Resolution</span></span>  
 <span data-ttu-id="162a6-113">Ujistěte se, že volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> se stane, bezprostředně před `try` příkazu.</span><span class="sxs-lookup"><span data-stu-id="162a6-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="162a6-114">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="162a6-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="162a6-115">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="162a6-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="162a6-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="162a6-116">Output</span></span>  
 <span data-ttu-id="162a6-117">MDA zobrazí název metoda – volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodu, posun jazyk MSIL a zprávu s oznámením, volání okamžitě nepředchází začátek bloku try.</span><span class="sxs-lookup"><span data-stu-id="162a6-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="162a6-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="162a6-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="162a6-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="162a6-119">Example</span></span>  
 <span data-ttu-id="162a6-120">Následující příklad kódu ukazuje vzor, který způsobí, že toto MDA aktivaci.</span><span class="sxs-lookup"><span data-stu-id="162a6-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="162a6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="162a6-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="162a6-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="162a6-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="162a6-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="162a6-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
