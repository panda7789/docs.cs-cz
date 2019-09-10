---
title: virtualCERCall – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3864ae416df0a2516a4dd9e6cf92669f66f27bb1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70853983"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="afb4f-102">virtualCERCall – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="afb4f-102">virtualCERCall MDA</span></span>
<span data-ttu-id="afb4f-103">Pomocník `virtualCERCall` spravovaného ladění (MDA) je aktivován jako upozornění označující, že web volání v rámci grafu volání oblasti s omezením (CER) odkazuje na virtuální cíl, tj. virtuální volání nekonečné virtuální metody nebo volání pomocí prostředí.</span><span class="sxs-lookup"><span data-stu-id="afb4f-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="afb4f-104">Modul CLR (Common Language Runtime) nemůže předpovědět cílovou metodu těchto volání ze samotného mezilehlého jazyka a analýzy metadat.</span><span class="sxs-lookup"><span data-stu-id="afb4f-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="afb4f-105">V důsledku toho nelze strom volání připravit jako součást grafu CER a přerušení vlákna v tomto podstromu nelze automaticky blokovat.</span><span class="sxs-lookup"><span data-stu-id="afb4f-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="afb4f-106">Tento MDA upozorňuje na případy, kdy může být potřeba rozšíření CER pomocí explicitního volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metody, jakmile jsou další informace vyžadované pro výpočet cíle volání známy v době běhu.</span><span class="sxs-lookup"><span data-stu-id="afb4f-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="afb4f-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="afb4f-107">Symptoms</span></span>  
 <span data-ttu-id="afb4f-108">CERs, které neběží, když je vlákno přerušeno nebo je doména aplikace uvolněna.</span><span class="sxs-lookup"><span data-stu-id="afb4f-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="afb4f-109">příčina</span><span class="sxs-lookup"><span data-stu-id="afb4f-109">Cause</span></span>  
 <span data-ttu-id="afb4f-110">CER obsahuje volání virtuální metody, která se nedá automaticky připravit.</span><span class="sxs-lookup"><span data-stu-id="afb4f-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="afb4f-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="afb4f-111">Resolution</span></span>  
 <span data-ttu-id="afb4f-112">Volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="afb4f-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="afb4f-113">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="afb4f-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="afb4f-114">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="afb4f-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="afb4f-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="afb4f-115">Output</span></span>  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="afb4f-116">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="afb4f-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="afb4f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="afb4f-117">Example</span></span>  
  
```csharp
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="afb4f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afb4f-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="afb4f-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="afb4f-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="afb4f-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="afb4f-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
