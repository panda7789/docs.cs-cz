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
ms.openlocfilehash: b80d6160876834b22e8d9d1eb7112b8b67c15fcc
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216463"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="b1f31-102">illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="b1f31-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="b1f31-103">Pokud volání metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> přímo nepředchází příkaz `try` obslužné rutiny výjimky, je aktivována aplikace `illegalPrepareConstrainedRegion` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="b1f31-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="b1f31-104">Toto omezení je na úrovni jazyka MSIL, takže je povoleno mít zdroj negenerující kód mezi voláním a `try`, jako jsou například komentáře.</span><span class="sxs-lookup"><span data-stu-id="b1f31-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b1f31-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="b1f31-105">Symptoms</span></span>  
 <span data-ttu-id="b1f31-106">Omezená oblast provádění (CER), která se nikdy nepovažuje za takovou, ale jako jednoduchý blok zpracování výjimek (`finally` nebo `catch`).</span><span class="sxs-lookup"><span data-stu-id="b1f31-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="b1f31-107">V důsledku toho se oblast nespustí v případě stavu mimo paměti nebo přerušení vlákna.</span><span class="sxs-lookup"><span data-stu-id="b1f31-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b1f31-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="b1f31-108">Cause</span></span>  
 <span data-ttu-id="b1f31-109">Vzor přípravy pro CER se nedodržuje správně.</span><span class="sxs-lookup"><span data-stu-id="b1f31-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="b1f31-110">Toto je chybná událost.</span><span class="sxs-lookup"><span data-stu-id="b1f31-110">This is an error event.</span></span> <span data-ttu-id="b1f31-111">Volání metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> používané k označení obslužných rutin výjimek v `catch`/`finally`/`fault`/`filter` bloky musí být použity těsně před příkazem `try`.</span><span class="sxs-lookup"><span data-stu-id="b1f31-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b1f31-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="b1f31-112">Resolution</span></span>  
 <span data-ttu-id="b1f31-113">Zajistěte, aby volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> následovalo těsně před příkazem `try`.</span><span class="sxs-lookup"><span data-stu-id="b1f31-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b1f31-114">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="b1f31-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="b1f31-115">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="b1f31-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b1f31-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="b1f31-116">Output</span></span>  
 <span data-ttu-id="b1f31-117">MDA zobrazuje název metody, která volá metodu <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, posun MSIL a zprávu indikující volání bezprostředně před začátkem bloku try.</span><span class="sxs-lookup"><span data-stu-id="b1f31-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b1f31-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b1f31-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="b1f31-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1f31-119">Example</span></span>  
 <span data-ttu-id="b1f31-120">Následující příklad kódu ukazuje vzor, který způsobuje, že je tento MDA aktivován.</span><span class="sxs-lookup"><span data-stu-id="b1f31-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1f31-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1f31-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="b1f31-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="b1f31-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b1f31-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="b1f31-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
