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
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052674"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="6a01e-102">illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="6a01e-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="6a01e-103">Pomocník `illegalPrepareConstrainedRegion` spravovaného ladění (MDA) je aktivován, <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> Pokud volání metody přímo nepředchází `try` příkaz obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="6a01e-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="6a01e-104">Toto omezení je na úrovni MSIL, takže je povoleno mít zdroj negenerující kód mezi voláním a `try`, jako jsou komentáře.</span><span class="sxs-lookup"><span data-stu-id="6a01e-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6a01e-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="6a01e-105">Symptoms</span></span>  
 <span data-ttu-id="6a01e-106">Omezená oblast provádění (CER), která se nikdy nepovažuje za takovou, ale jako jednoduchý blok zpracování výjimek (`finally` nebo `catch`).</span><span class="sxs-lookup"><span data-stu-id="6a01e-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="6a01e-107">V důsledku toho se oblast nespustí v případě stavu mimo paměti nebo přerušení vlákna.</span><span class="sxs-lookup"><span data-stu-id="6a01e-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6a01e-108">příčina</span><span class="sxs-lookup"><span data-stu-id="6a01e-108">Cause</span></span>  
 <span data-ttu-id="6a01e-109">Vzor přípravy pro CER se nedodržuje správně.</span><span class="sxs-lookup"><span data-stu-id="6a01e-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="6a01e-110">Toto je chybná událost.</span><span class="sxs-lookup"><span data-stu-id="6a01e-110">This is an error event.</span></span> <span data-ttu-id="6a01e-111">/ / `catch` `fault` Volánímetodypoužité`filter` k označení obslužných rutin výjimek, `finally` protože/ zavedete-li CER do bloků, je nutné použít bezprostředně před <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> `try` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6a01e-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6a01e-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="6a01e-112">Resolution</span></span>  
 <span data-ttu-id="6a01e-113">Zajistěte, aby <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> volání následovalo těsně `try` před příkazem.</span><span class="sxs-lookup"><span data-stu-id="6a01e-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6a01e-114">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="6a01e-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="6a01e-115">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="6a01e-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6a01e-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="6a01e-116">Output</span></span>  
 <span data-ttu-id="6a01e-117">MDA zobrazuje název metody, která volá <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodu, posun MSIL a zprávu indikující volání bezprostředně před začátkem bloku try.</span><span class="sxs-lookup"><span data-stu-id="6a01e-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6a01e-118">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="6a01e-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="6a01e-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a01e-119">Example</span></span>  
 <span data-ttu-id="6a01e-120">Následující příklad kódu ukazuje vzor, který způsobuje, že je tento MDA aktivován.</span><span class="sxs-lookup"><span data-stu-id="6a01e-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a01e-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a01e-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="6a01e-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="6a01e-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6a01e-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="6a01e-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
