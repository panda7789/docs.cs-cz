---
title: "virtualCERCall – pomocník spravovaného ladění (MDA)"
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
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3f0c06eef7524c18e252ade9122d8c9cb3c2f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="3f705-102">virtualCERCall – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="3f705-102">virtualCERCall MDA</span></span>
<span data-ttu-id="3f705-103">`virtualCERCall` Pomocník spravovaného ladění (MDA) je aktivován jako upozornění označující, že volání lokalitě v rámci graf volání (CER) oblasti omezeného provádění odkazuje na virtuální cíl, který je virtuální volání metody virtuální jiný koncový nebo volání pomocí rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f705-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="3f705-104">Modul CLR (CLR) nelze předvídání metodu cílové těchto volání z mezilehlých jazyk a metadata analýzy samostatně.</span><span class="sxs-lookup"><span data-stu-id="3f705-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="3f705-105">V důsledku toho stromu volání nelze připravit jako součást CER grafu a přerušení přístup z více vláken v tomto podstrom, nejde blokovat automaticky.</span><span class="sxs-lookup"><span data-stu-id="3f705-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="3f705-106">Tato MDA upozorňuje na případy, kdy je CER může být potřeba rozšířit pomocí explicitního volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metoda po další informace požadované pro výpočetní cíl volání se označuje za běhu.</span><span class="sxs-lookup"><span data-stu-id="3f705-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3f705-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="3f705-107">Symptoms</span></span>  
 <span data-ttu-id="3f705-108">Je odpojen CERs, které se nespustí, pokud byl přerušen vlákna nebo domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3f705-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3f705-109">příčina</span><span class="sxs-lookup"><span data-stu-id="3f705-109">Cause</span></span>  
 <span data-ttu-id="3f705-110">CER obsahuje volání virtuální metodu, která nelze připravit automaticky.</span><span class="sxs-lookup"><span data-stu-id="3f705-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3f705-111">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="3f705-111">Resolution</span></span>  
 <span data-ttu-id="3f705-112">Volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="3f705-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3f705-113">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="3f705-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="3f705-114">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="3f705-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3f705-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="3f705-115">Output</span></span>  
  
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
  
## <a name="configuration"></a><span data-ttu-id="3f705-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="3f705-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="3f705-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f705-117">Example</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="3f705-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f705-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="3f705-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="3f705-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="3f705-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="3f705-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
