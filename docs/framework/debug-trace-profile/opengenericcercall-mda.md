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
ms.openlocfilehash: 7492a4c0547680a6ace85a5f7c98567770f5575a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181778"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="379be-102">openGenericCERCall – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="379be-102">openGenericCERCall MDA</span></span>

<span data-ttu-id="379be-103">Spravovaný `openGenericCERCall` ladicí asistent je aktivován, aby varoval, že graf oblasti omezeného spuštění (CER) s obecnými proměnnými typu v kořenové metodě je zpracováván v době kompilace JIT nebo nativnígenerace bitové kopie a alespoň jedna z proměnných obecného typu je typ odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="379be-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>

## <a name="symptoms"></a><span data-ttu-id="379be-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="379be-104">Symptoms</span></span>

<span data-ttu-id="379be-105">Kód CER se nespustí, pokud je vlákno přerušeno nebo když je uvolněna doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="379be-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>

## <a name="cause"></a><span data-ttu-id="379be-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="379be-106">Cause</span></span>

<span data-ttu-id="379be-107">V době kompilace JIT je instance obsahující typ odkazu na objekt pouze reprezentativní, protože výsledný kód je sdílen a každá z proměnných typu odkazu na objekt může být libovolný typ odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="379be-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="379be-108">To může zabránit přípravě některých prostředků run-time předem.</span><span class="sxs-lookup"><span data-stu-id="379be-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>

<span data-ttu-id="379be-109">Zejména metody s proměnnými typu obecného typu mohou líně přidělit prostředky na pozadí.</span><span class="sxs-lookup"><span data-stu-id="379be-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="379be-110">Tyto položky jsou označovány jako položky obecného slovníku.</span><span class="sxs-lookup"><span data-stu-id="379be-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="379be-111">Například pro `List<T> list = new List<T>();` příkaz, `T` kde je obecná proměnná typu, musí runtime vyhledat a případně vytvořit `List<Object>, List<String>`přesnou inkaso za běhu, například , a tak dále.</span><span class="sxs-lookup"><span data-stu-id="379be-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`, and so forth.</span></span> <span data-ttu-id="379be-112">To může selhat z různých důvodů mimo kontrolu vývojáře, jako je například nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="379be-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>

<span data-ttu-id="379be-113">Tento MDA by měl být aktivován pouze v době kompilace JIT, nikoli v případě, že existuje přesná instance.</span><span class="sxs-lookup"><span data-stu-id="379be-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>

<span data-ttu-id="379be-114">Když je aktivován tento MDA, pravděpodobné příznaky jsou, že CER nejsou funkční pro špatné konkresace.</span><span class="sxs-lookup"><span data-stu-id="379be-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="379be-115">Ve skutečnosti se runtime nepokusil implementovat CER za okolností, které způsobily aktivaci MDA.</span><span class="sxs-lookup"><span data-stu-id="379be-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="379be-116">Takže pokud vývojář používá sdílenou instanci CER, pak jit kompilace chyby, obecné typy typu načítání chyby nebo podproces přeruší v rámci oblasti zamýšlené CER nejsou zachyceny.</span><span class="sxs-lookup"><span data-stu-id="379be-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>

## <a name="resolution"></a><span data-ttu-id="379be-117">Řešení</span><span class="sxs-lookup"><span data-stu-id="379be-117">Resolution</span></span>

<span data-ttu-id="379be-118">Nepoužívejte obecné proměnné typu, které jsou typu odkazu na objekt pro metody, které mohou obsahovat CER.</span><span class="sxs-lookup"><span data-stu-id="379be-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="379be-119">Vliv na běhový čas</span><span class="sxs-lookup"><span data-stu-id="379be-119">Effect on the Runtime</span></span>

<span data-ttu-id="379be-120">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="379be-120">This MDA has no effect on the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="379be-121">Výstup</span><span class="sxs-lookup"><span data-stu-id="379be-121">Output</span></span>

<span data-ttu-id="379be-122">Následuje ukázka výstupu z tohoto MDA:</span><span class="sxs-lookup"><span data-stu-id="379be-122">The following is a sample of output from this MDA:</span></span>
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution.
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a><span data-ttu-id="379be-123">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="379be-123">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a><span data-ttu-id="379be-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="379be-124">Example</span></span>

<span data-ttu-id="379be-125">Kód CER není spuštěn.</span><span class="sxs-lookup"><span data-stu-id="379be-125">The CER code is not executed.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="379be-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="379be-126">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="379be-127">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="379be-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
