---
title: illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění illegalPrepareConstrainedRegion, který je vyvolán, pokud volání PrepareConstrainedRegions není následováno příkazem try.
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: d6a0d1d95840ebd735806c5547730ae9e0b2aace
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051282"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="641d3-103">illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="641d3-103">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="641d3-104">`illegalPrepareConstrainedRegion`Pomocník spravovaného ladění (MDA) je aktivován, pokud <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> volání metody přímo nepředchází `try` příkaz obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="641d3-104">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="641d3-105">Toto omezení je na úrovni MSIL, takže je povoleno mít zdroj negenerující kód mezi voláním a `try` , jako jsou komentáře.</span><span class="sxs-lookup"><span data-stu-id="641d3-105">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="641d3-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="641d3-106">Symptoms</span></span>  
 <span data-ttu-id="641d3-107">Omezená oblast provádění (CER), která se nikdy nepovažuje za takovou, ale jako jednoduchý blok zpracování výjimek ( `finally` nebo `catch` ).</span><span class="sxs-lookup"><span data-stu-id="641d3-107">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="641d3-108">V důsledku toho se oblast nespustí v případě stavu mimo paměti nebo přerušení vlákna.</span><span class="sxs-lookup"><span data-stu-id="641d3-108">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="641d3-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="641d3-109">Cause</span></span>  
 <span data-ttu-id="641d3-110">Vzor přípravy pro CER se nedodržuje správně.</span><span class="sxs-lookup"><span data-stu-id="641d3-110">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="641d3-111">Toto je chybná událost.</span><span class="sxs-lookup"><span data-stu-id="641d3-111">This is an error event.</span></span> <span data-ttu-id="641d3-112"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>Volání metody použité k označení obslužných rutin výjimek, protože zavedete-li CER do jejich `catch` / `finally` / `fault` / `filter` bloků, je nutné použít těsně před `try` příkazem.</span><span class="sxs-lookup"><span data-stu-id="641d3-112">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="641d3-113">Řešení</span><span class="sxs-lookup"><span data-stu-id="641d3-113">Resolution</span></span>  
 <span data-ttu-id="641d3-114">Zajistěte, aby volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> následovalo těsně před `try` příkazem.</span><span class="sxs-lookup"><span data-stu-id="641d3-114">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="641d3-115">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="641d3-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="641d3-116">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="641d3-116">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="641d3-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="641d3-117">Output</span></span>  
 <span data-ttu-id="641d3-118">MDA zobrazuje název metody, která volá <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodu, posun MSIL a zprávu indikující volání bezprostředně před začátkem bloku try.</span><span class="sxs-lookup"><span data-stu-id="641d3-118">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="641d3-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="641d3-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="641d3-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="641d3-120">Example</span></span>  
 <span data-ttu-id="641d3-121">Následující příklad kódu ukazuje vzor, který způsobuje, že je tento MDA aktivován.</span><span class="sxs-lookup"><span data-stu-id="641d3-121">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="641d3-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="641d3-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="641d3-123">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="641d3-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="641d3-124">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="641d3-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
