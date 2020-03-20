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
ms.openlocfilehash: a2112baed863b1035cbee4e956c1b6e271ff6e3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181712"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="09036-102">virtualCERCall – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="09036-102">virtualCERCall MDA</span></span>
<span data-ttu-id="09036-103">Spravovaný `virtualCERCall` ladicí asistent (MDA) je aktivován jako upozornění označující, že lokalita volání v rámci grafu volání v rámci grafu volání omezené ho spuštění (CER) odkazuje na virtuální cíl, to znamená virtuální volání nefinal virtual metody nebo volání pomocí rozhraní.</span><span class="sxs-lookup"><span data-stu-id="09036-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="09036-104">Modul CLR (COMMON Language runtime) nemůže předpovědět cílovou metodu těchto volání z mezilehlého jazyka a analýzy metadat samostatně.</span><span class="sxs-lookup"><span data-stu-id="09036-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="09036-105">V důsledku toho nelze připravit strom volání jako součást grafu CER a přerušení podprocesu v tomto podstromu nelze automaticky blokovat.</span><span class="sxs-lookup"><span data-stu-id="09036-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="09036-106">Tento MDA varuje před případy, kdy cer může být <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> nutné rozšířit pomocí explicitní volání metody, jakmile další informace potřebné k výpočtu cíle volání je známa v době běhu.</span><span class="sxs-lookup"><span data-stu-id="09036-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="09036-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="09036-107">Symptoms</span></span>  
 <span data-ttu-id="09036-108">CER, které nejsou spuštěny při přerušení podprocesu nebo je uvolněna doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="09036-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="09036-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="09036-109">Cause</span></span>  
 <span data-ttu-id="09036-110">Cer obsahuje volání virtuální metody, která nemůže být připravena automaticky.</span><span class="sxs-lookup"><span data-stu-id="09036-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="09036-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="09036-111">Resolution</span></span>  
 <span data-ttu-id="09036-112">Volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="09036-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="09036-113">Vliv na běhový čas</span><span class="sxs-lookup"><span data-stu-id="09036-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="09036-114">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="09036-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="09036-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="09036-115">Output</span></span>  
  
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
  
## <a name="configuration"></a><span data-ttu-id="09036-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="09036-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="09036-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="09036-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09036-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="09036-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="09036-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="09036-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="09036-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="09036-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
