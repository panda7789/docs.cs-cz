---
title: nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 707dad3c5286fc9c8d5aa3735418607fb0a769a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392174"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="c2c83-102">nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="c2c83-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="c2c83-103">`nonComVisibleBaseClass` Pomocník spravovaného ladění (MDA) se aktivuje při `QueryInterface` COM – viditelné spravované třídy, která je odvozena ze základní třídy, které nejsou viditelné modelu COM Přišla žádost kódem nativní nebo nespravované na obálka volatelná aplikacemi COM (doleva).</span><span class="sxs-lookup"><span data-stu-id="c2c83-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="c2c83-104">`QueryInterface` Volání způsobí, že MDA aktivovat pouze v případech, kdy volání požaduje třídy rozhraní nebo výchozí `IDispatch` COM-viditelných spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="c2c83-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="c2c83-105">MDA není aktivované, když `QueryInterface` je pro explicitní rozhraní, které má <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> použít atribut a je explicitně implementované COM – viditelné třídy.</span><span class="sxs-lookup"><span data-stu-id="c2c83-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c2c83-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="c2c83-106">Symptoms</span></span>  
 <span data-ttu-id="c2c83-107">A `QueryInterface` volání z nativní kód, který se nedaří s hodnotou HRESULT COR_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="c2c83-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="c2c83-108">Hodnota HRESULT může být způsobeno runtime zakazuje `QueryInterface` volání, které by způsobily aktivace této (mda).</span><span class="sxs-lookup"><span data-stu-id="c2c83-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c2c83-109">příčina</span><span class="sxs-lookup"><span data-stu-id="c2c83-109">Cause</span></span>  
 <span data-ttu-id="c2c83-110">Modul runtime nemůže povolit `QueryInterface` volání pro třídu rozhraní nebo výchozí `IDispatch` rozhraní COM – viditelné třídy, která je odvozena od třídy, která není viditelná COM z důvodu potenciální problémy se správou verzí.</span><span class="sxs-lookup"><span data-stu-id="c2c83-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="c2c83-111">Například pokud všechny veřejné členy byly přidány do základní třídu, která není viditelná COM, existující klientů modelu COM pomocí odvozená třída může potenciálně rozdělit protože by tím například změnit vtable odvozené třídy, která obsahuje členy základní třídy, změníte.</span><span class="sxs-lookup"><span data-stu-id="c2c83-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="c2c83-112">Explicitní rozhraní vystaven objektům modelu COM nemají tento problém, protože v tabulce vtable nezahrnují základní členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c2c83-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c2c83-113">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="c2c83-113">Resolution</span></span>  
 <span data-ttu-id="c2c83-114">Nevystavujte rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="c2c83-114">Do not expose the class interface.</span></span> <span data-ttu-id="c2c83-115">Definovat explicitní rozhraní a použít <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut ho.</span><span class="sxs-lookup"><span data-stu-id="c2c83-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c2c83-116">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="c2c83-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="c2c83-117">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c2c83-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c2c83-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="c2c83-118">Output</span></span>  
 <span data-ttu-id="c2c83-119">Následující příklad zpráva pro je `QueryInterface` volání COM – viditelné třídy `Derived` , je odvozena od jiných COM – viditelné třídy `Base`.</span><span class="sxs-lookup"><span data-stu-id="c2c83-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="c2c83-120">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c2c83-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2c83-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2c83-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="c2c83-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c2c83-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="c2c83-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="c2c83-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
