---
title: "nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b00d8396b07eb445414fb85cd830d595a513be0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="299e7-102">nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="299e7-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="299e7-103">`nonComVisibleBaseClass` Pomocník spravovaného ladění (MDA) se aktivuje při `QueryInterface` COM – viditelné spravované třídy, která je odvozena ze základní třídy, které nejsou viditelné modelu COM Přišla žádost kódem nativní nebo nespravované na obálka volatelná aplikacemi COM (doleva).</span><span class="sxs-lookup"><span data-stu-id="299e7-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="299e7-104">`QueryInterface` Volání způsobí, že MDA aktivovat pouze v případech, kdy volání požaduje třídy rozhraní nebo výchozí `IDispatch` COM-viditelných spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="299e7-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="299e7-105">MDA není aktivované, když `QueryInterface` je pro explicitní rozhraní, které má <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> použít atribut a je explicitně implementované COM – viditelné třídy.</span><span class="sxs-lookup"><span data-stu-id="299e7-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="299e7-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="299e7-106">Symptoms</span></span>  
 <span data-ttu-id="299e7-107">A `QueryInterface` volání z nativní kód, který se nedaří s hodnotou HRESULT COR_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="299e7-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="299e7-108">Hodnota HRESULT může být způsobeno runtime zakazuje `QueryInterface` volání, které by způsobily aktivace této (mda).</span><span class="sxs-lookup"><span data-stu-id="299e7-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="299e7-109">příčina</span><span class="sxs-lookup"><span data-stu-id="299e7-109">Cause</span></span>  
 <span data-ttu-id="299e7-110">Modul runtime nemůže povolit `QueryInterface` volání pro třídu rozhraní nebo výchozí `IDispatch` rozhraní COM – viditelné třídy, která je odvozena od třídy, která není viditelná COM z důvodu potenciální problémy se správou verzí.</span><span class="sxs-lookup"><span data-stu-id="299e7-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="299e7-111">Například pokud všechny veřejné členy byly přidány do základní třídu, která není viditelná COM, existující klientů modelu COM pomocí odvozená třída může potenciálně rozdělit protože by tím například změnit vtable odvozené třídy, která obsahuje členy základní třídy, změníte.</span><span class="sxs-lookup"><span data-stu-id="299e7-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="299e7-112">Explicitní rozhraní vystaven objektům modelu COM nemají tento problém, protože v tabulce vtable nezahrnují základní členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="299e7-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="299e7-113">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="299e7-113">Resolution</span></span>  
 <span data-ttu-id="299e7-114">Nevystavujte rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="299e7-114">Do not expose the class interface.</span></span> <span data-ttu-id="299e7-115">Definovat explicitní rozhraní a použít <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut ho.</span><span class="sxs-lookup"><span data-stu-id="299e7-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="299e7-116">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="299e7-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="299e7-117">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="299e7-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="299e7-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="299e7-118">Output</span></span>  
 <span data-ttu-id="299e7-119">Následující příklad zpráva pro je `QueryInterface` volání COM – viditelné třídy `Derived` , je odvozena od jiných COM – viditelné třídy `Base`.</span><span class="sxs-lookup"><span data-stu-id="299e7-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="299e7-120">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="299e7-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="299e7-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="299e7-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="299e7-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="299e7-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="299e7-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="299e7-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
