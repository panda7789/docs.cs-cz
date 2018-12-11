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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2cb99a1bda8223ddece4b4aff4a87d95357d90e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153693"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="f17ba-102">openGenericCERCall – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="f17ba-102">openGenericCERCall MDA</span></span>
<span data-ttu-id="f17ba-103">`openGenericCERCall` Upozornit, oblast (CER) graf omezeného provádění s proměnnými obecného typu v metodě kořenové je zpracovávána v kompilaci JIT nebo nativní bitové kopie generování a alespoň jeden z obecného se aktivuje pomocníka spravovaného ladění Typ proměnné je odkaz na typ objektu.</span><span class="sxs-lookup"><span data-stu-id="f17ba-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f17ba-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="f17ba-104">Symptoms</span></span>  
 <span data-ttu-id="f17ba-105">CER kód nejde spustit, když je přerušeno vlákno nebo když je doména aplikace uvolněna.</span><span class="sxs-lookup"><span data-stu-id="f17ba-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f17ba-106">příčina</span><span class="sxs-lookup"><span data-stu-id="f17ba-106">Cause</span></span>  
 <span data-ttu-id="f17ba-107">V době kompilace JIT je instance obsahující odkaz na typ objektu, který pouze zástupce, protože výsledný kód je sdílet, a každý typ proměnné odkazu na objekt může být libovolný typ objektu odkaz.</span><span class="sxs-lookup"><span data-stu-id="f17ba-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="f17ba-108">To může zabránit přípravy několik zdrojů informací za běhu, předem.</span><span class="sxs-lookup"><span data-stu-id="f17ba-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>  
  
 <span data-ttu-id="f17ba-109">Zejména metody s proměnnými obecného typu laxně přidělení prostředků na pozadí.</span><span class="sxs-lookup"><span data-stu-id="f17ba-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="f17ba-110">Tyto jsou označovány jako položky generický slovník.</span><span class="sxs-lookup"><span data-stu-id="f17ba-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="f17ba-111">Například pro příkaz `List<T> list = new List<T>();` kde `T` je obecný typem proměnné modul runtime musí vyhledat a případně také mohli vytvářet přesné vytváření instancí v době běhu, třeba `List<Object>, List<String>`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f17ba-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`,and so forth.</span></span> <span data-ttu-id="f17ba-112">To může selhat z různých důvodů mimo kontrolu vývojáře, jako je například spuštění nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="f17ba-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>  
  
 <span data-ttu-id="f17ba-113">Toto MDA by měl být aktivována pouze v době kompilace JIT, ne po přesné vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="f17ba-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>  
  
 <span data-ttu-id="f17ba-114">Když je toto MDA aktivováno, pravděpodobně příznaky jsou, že CERs nejsou funkční pro chybný instancí.</span><span class="sxs-lookup"><span data-stu-id="f17ba-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="f17ba-115">Ve skutečnosti modul runtime nezačaly k implementaci CER za okolností, které způsobily MDA aktivaci.</span><span class="sxs-lookup"><span data-stu-id="f17ba-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="f17ba-116">Pokud vývojář používá sdílené instance CER, pak chyby kompilace JIT, obecných typů zadejte chyby při načítání nebo zrušení vláken v oblasti určené CER proto nejsou zachyceny.</span><span class="sxs-lookup"><span data-stu-id="f17ba-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f17ba-117">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="f17ba-117">Resolution</span></span>  
 <span data-ttu-id="f17ba-118">Nepoužívejte proměnné obecného typu, které jsou objekt odkazového typu pro metody, které mohou obsahovat CER.</span><span class="sxs-lookup"><span data-stu-id="f17ba-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f17ba-119">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="f17ba-119">Effect on the Runtime</span></span>  
 <span data-ttu-id="f17ba-120">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="f17ba-120">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f17ba-121">Výstup</span><span class="sxs-lookup"><span data-stu-id="f17ba-121">Output</span></span>  
 <span data-ttu-id="f17ba-122">Následuje ukázkový výstup z tohoto MDA.</span><span class="sxs-lookup"><span data-stu-id="f17ba-122">The following is a sample of output from this MDA.</span></span>  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a><span data-ttu-id="f17ba-123">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f17ba-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f17ba-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="f17ba-124">Example</span></span>  
 <span data-ttu-id="f17ba-125">Kód CER není spuštěn.</span><span class="sxs-lookup"><span data-stu-id="f17ba-125">The CER code is not executed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f17ba-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f17ba-126">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [<span data-ttu-id="f17ba-127">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f17ba-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
