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
ms.openlocfilehash: e2c8712837dab17f70be32617711c1bad9349508
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086075"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="e788d-102">virtualCERCall – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="e788d-102">virtualCERCall MDA</span></span>
<span data-ttu-id="e788d-103">`virtualCERCall` Pomocníka spravovaného ladění (MDA) je aktivován jako upozornění, že lokalita volání v grafu volání (CER) oblasti omezeného provádění odkazuje na virtuální cíl, tedy virtuální volání nefinální virtuální metody nebo volání pomocí rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e788d-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="e788d-104">Modul CLR (CLR) nelze předvídat cílové metody těchto volání z intermediate language a metadata analýzy samostatně.</span><span class="sxs-lookup"><span data-stu-id="e788d-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="e788d-105">V důsledku toho jako součást CER grafu nelze připravit stromu volání a přerušení vlákna v tomto podstromu, nejde blokovat automaticky.</span><span class="sxs-lookup"><span data-stu-id="e788d-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="e788d-106">Toto MDA upozorňuje na případy, kdy může být nutné rozšířit pomocí explicitního volání CER <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metoda po další informace potřebné k volání cílové výpočetní prostředí je znám v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e788d-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e788d-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="e788d-107">Symptoms</span></span>  
 <span data-ttu-id="e788d-108">CERs, která nepoužívají při přerušeno vlákno nebo doménu aplikace je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="e788d-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e788d-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="e788d-109">Cause</span></span>  
 <span data-ttu-id="e788d-110">CER obsahuje volání virtuální metody, která nelze připravit automaticky.</span><span class="sxs-lookup"><span data-stu-id="e788d-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e788d-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="e788d-111">Resolution</span></span>  
 <span data-ttu-id="e788d-112">Volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="e788d-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e788d-113">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="e788d-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="e788d-114">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="e788d-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e788d-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="e788d-115">Output</span></span>  
  
```  
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="e788d-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e788d-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="e788d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e788d-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e788d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e788d-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e788d-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="e788d-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e788d-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="e788d-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
