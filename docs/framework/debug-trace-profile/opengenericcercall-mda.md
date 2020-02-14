---
title: openGenericCERCall – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
ms.openlocfilehash: de1735103314dfedbabe27623f579ce2c1e728af
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217266"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="8305f-102">openGenericCERCall – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="8305f-102">openGenericCERCall MDA</span></span>

<span data-ttu-id="8305f-103">Je aktivován Pomocník pro vy`openGenericCERCall` spravované ladění, který upozorňuje na to, že graf s omezeným výkonem (CER) s proměnnými obecného typu v kořenové metodě se zpracovává při kompilaci JIT nebo při generování nativní bitové kopie a aspoň jedna z obecných typů proměnných je typ odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="8305f-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>

## <a name="symptoms"></a><span data-ttu-id="8305f-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="8305f-104">Symptoms</span></span>

<span data-ttu-id="8305f-105">Kód CER se nespustí, pokud je vlákno přerušeno nebo pokud je doména aplikace uvolněna.</span><span class="sxs-lookup"><span data-stu-id="8305f-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>

## <a name="cause"></a><span data-ttu-id="8305f-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="8305f-106">Cause</span></span>

<span data-ttu-id="8305f-107">V době kompilace JIT je vytváření instancí obsahující typ odkazu na objekt pouze zástupce, protože výsledný kód je sdílen a každá proměnná typu odkazu na objekt může být libovolný typ odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="8305f-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="8305f-108">To může předem zabránit přípravě některých prostředků za běhu.</span><span class="sxs-lookup"><span data-stu-id="8305f-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>

<span data-ttu-id="8305f-109">Konkrétně metody s proměnnými obecného typu mohou laxně vytvářená přidělit prostředky na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8305f-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="8305f-110">Ty jsou označovány jako položky obecného slovníku.</span><span class="sxs-lookup"><span data-stu-id="8305f-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="8305f-111">Například pro příkaz `List<T> list = new List<T>();`, kde `T` je proměnná obecného typu, musí modul runtime vyhledat a případně vytvořit přesnou instanci v době běhu, například `List<Object>, List<String>`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="8305f-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`, and so forth.</span></span> <span data-ttu-id="8305f-112">To může selhat z nejrůznějších důvodů mimo řízení vývojáře, jako je například nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="8305f-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>

<span data-ttu-id="8305f-113">Tato položka MDA by měla být aktivována pouze v době kompilace JIT, nikoli v případě přesného vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="8305f-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>

<span data-ttu-id="8305f-114">Když je tento MDA aktivovaný, je pravděpodobným symptomem, že CERs nejsou funkční pro špatné vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="8305f-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="8305f-115">Ve skutečnosti se modul runtime nepokusil implementovat CER za okolností, které způsobily aktivaci modulu MDA.</span><span class="sxs-lookup"><span data-stu-id="8305f-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="8305f-116">Takže pokud vývojář používá sdílené vytváření instancí CER, chyby kompilace JIT, chyby načítání obecných typů nebo přerušení vlákna v rámci oblasti zamýšleného CER se nezachycují.</span><span class="sxs-lookup"><span data-stu-id="8305f-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>

## <a name="resolution"></a><span data-ttu-id="8305f-117">Řešení</span><span class="sxs-lookup"><span data-stu-id="8305f-117">Resolution</span></span>

<span data-ttu-id="8305f-118">Nepoužívejte proměnné obecného typu, které jsou typu odkazu na objekt pro metody, které mohou obsahovat CER.</span><span class="sxs-lookup"><span data-stu-id="8305f-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="8305f-119">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="8305f-119">Effect on the Runtime</span></span>

<span data-ttu-id="8305f-120">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="8305f-120">This MDA has no effect on the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="8305f-121">Výstup</span><span class="sxs-lookup"><span data-stu-id="8305f-121">Output</span></span>

<span data-ttu-id="8305f-122">Následuje ukázka výstupu z tohoto MDA:</span><span class="sxs-lookup"><span data-stu-id="8305f-122">The following is a sample of output from this MDA:</span></span>
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution. 
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a><span data-ttu-id="8305f-123">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8305f-123">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a><span data-ttu-id="8305f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="8305f-124">Example</span></span>

<span data-ttu-id="8305f-125">Kód CER není proveden.</span><span class="sxs-lookup"><span data-stu-id="8305f-125">The CER code is not executed.</span></span>

```csharp
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

## <a name="see-also"></a><span data-ttu-id="8305f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="8305f-126">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="8305f-127">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="8305f-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
