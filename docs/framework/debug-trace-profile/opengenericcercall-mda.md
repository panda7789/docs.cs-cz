---
title: "openGenericCERCall – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 766f36ae49d19a11f299fe95f272cc8e72093331
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="4e3e6-102">openGenericCERCall – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="4e3e6-102">openGenericCERCall MDA</span></span>
<span data-ttu-id="4e3e6-103">`openGenericCERCall` Upozornit, že graf omezeného provádění oblast (CER) s proměnné obecného typu v kořenové metoda je zpracovávaný v JIT – kompilace nebo nativních bitových kopií časem vygenerování a alespoň jeden z obecná se aktivuje Pomocník spravovaného ladění Typ proměnné je odkaz na typ objektu.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4e3e6-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="4e3e6-104">Symptoms</span></span>  
 <span data-ttu-id="4e3e6-105">CER kód není spuštěn, když byl přerušen vlákna nebo když je odpojen domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4e3e6-106">příčina</span><span class="sxs-lookup"><span data-stu-id="4e3e6-106">Cause</span></span>  
 <span data-ttu-id="4e3e6-107">Během JIT – kompilace vytvoření instance obsahující odkaz na typ objektu, který je pouze zástupce, protože výsledná kód jsou sdílena a každý typ proměnné objektových referencí mohou být jakéhokoli typu odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="4e3e6-108">To může zabránit přípravy některé prostředky běhu předem.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>  
  
 <span data-ttu-id="4e3e6-109">Metody s proměnné obecného typu můžete konkrétně líné přidělení prostředků na pozadí.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="4e3e6-110">Tyto jsou označovány jako položky obecné slovníku.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="4e3e6-111">Například pro příkaz `List<T> list = new List<T>();` kde `T` je proměnná obecného typu modulu runtime musí vyhledat a případně vytvořit přesný instance za běhu, například `List<Object>, List<String>`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`,and so forth.</span></span> <span data-ttu-id="4e3e6-112">To může selhat z různých důvodů mimo kontrolu vývojáře, například spuštění nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>  
  
 <span data-ttu-id="4e3e6-113">Tato MDA by měl být aktivován pouze během JIT – kompilace, ne při přesné vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>  
  
 <span data-ttu-id="4e3e6-114">Po aktivaci tato MDA pravděpodobně příznaky jsou, že CERs nejsou funkční pro chybný konkretizací.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="4e3e6-115">Modul runtime nebyla ve skutečnosti se pokusil implementovat CER okolností, které způsobily MDA chcete aktivovat.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="4e3e6-116">Takže pokud vývojář používá sdílené vytváření instancí z CER, pak JIT – kompilace chyby, Obecné zadejte chyby při načítání nebo zrušení vláken v rámci oblasti určený CER nejsou zachycena.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4e3e6-117">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="4e3e6-117">Resolution</span></span>  
 <span data-ttu-id="4e3e6-118">Nepoužívejte proměnné obecného typu, které jsou typu odkaz objektu pro metody, které mohou obsahovat CER.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4e3e6-119">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="4e3e6-119">Effect on the Runtime</span></span>  
 <span data-ttu-id="4e3e6-120">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-120">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4e3e6-121">Výstup</span><span class="sxs-lookup"><span data-stu-id="4e3e6-121">Output</span></span>  
 <span data-ttu-id="4e3e6-122">Zde je ukázkový výstup z této (mda).</span><span class="sxs-lookup"><span data-stu-id="4e3e6-122">The following is a sample of output from this MDA.</span></span>  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a><span data-ttu-id="4e3e6-123">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="4e3e6-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="4e3e6-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e3e6-124">Example</span></span>  
 <span data-ttu-id="4e3e6-125">CER kód není spuštěn.</span><span class="sxs-lookup"><span data-stu-id="4e3e6-125">The CER code is not executed.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e3e6-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e3e6-126">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [<span data-ttu-id="4e3e6-127">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="4e3e6-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
