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
ms.openlocfilehash: a26863f2a1880cffba5eb3ea51573f45323be72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700855"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="5a11a-102">nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="5a11a-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="5a11a-103">`nonComVisibleBaseClass` Pomocníka spravovaného ladění (MDA) se aktivuje při `QueryInterface` je provedeno volání pomocí nativní nebo nespravovaného kódu na obálka volatelná aplikacemi COM (CCW) COM – viditelné spravované třídy, která je odvozena ze základní třídy, které nejsou viditelné modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5a11a-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="5a11a-104">`QueryInterface` Volání způsobí, že MDA aktivovat pouze v případech, kde požadavky na třídy rozhraní nebo výchozí volání `IDispatch` COM-viditelných spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="5a11a-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="5a11a-105">MDA není aktivuje se, když `QueryInterface` je pro explicitní rozhraní, který má <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> použít atribut a je explicitně implementované COM – viditelné třídy.</span><span class="sxs-lookup"><span data-stu-id="5a11a-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5a11a-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="5a11a-106">Symptoms</span></span>  
 <span data-ttu-id="5a11a-107">A `QueryInterface` volání z nativního kódu, který je neúspěšné s chybou HRESULT COR_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="5a11a-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="5a11a-108">Hodnota HRESULT mohou být způsobeny runtime zákaz `QueryInterface` volání, které by mohly způsobit aktivace toto MDA.</span><span class="sxs-lookup"><span data-stu-id="5a11a-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5a11a-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="5a11a-109">Cause</span></span>  
 <span data-ttu-id="5a11a-110">Modul runtime nemůže povolit `QueryInterface` volání pro rozhraní třídy nebo výchozí `IDispatch` rozhraní COM – viditelné třídy, která je odvozena z třídy, který není viditelný modulem COM z důvodu potenciální problémy se správou verzí.</span><span class="sxs-lookup"><span data-stu-id="5a11a-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="5a11a-111">Například, pokud žádné veřejné členy byly přidány na základní třídu, která není viditelný modulem COM, existující klienti modelu COM pomocí odvozené třídy může potenciálně narušit vzhledem k tomu tabulku vtable, který obsahuje členy základní třídy odvozené třídy by změněny, Změňte.</span><span class="sxs-lookup"><span data-stu-id="5a11a-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="5a11a-112">Explicitní rozhraní vystavit rozhraní COM nemají tento problém, protože v tabulce vtable neobsahují základních členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5a11a-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5a11a-113">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="5a11a-113">Resolution</span></span>  
 <span data-ttu-id="5a11a-114">Nezveřejňujte třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5a11a-114">Do not expose the class interface.</span></span> <span data-ttu-id="5a11a-115">Definujte explicitní rozhraní a použít <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut k němu.</span><span class="sxs-lookup"><span data-stu-id="5a11a-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5a11a-116">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="5a11a-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="5a11a-117">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="5a11a-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5a11a-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="5a11a-118">Output</span></span>  
 <span data-ttu-id="5a11a-119">Tady je ukázková zpráva pro `QueryInterface` volání COM – viditelné třídy `Derived` , která je odvozena z třídy není viditelný pro COM `Base`.</span><span class="sxs-lookup"><span data-stu-id="5a11a-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="5a11a-120">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5a11a-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a11a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a11a-121">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5a11a-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="5a11a-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5a11a-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="5a11a-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
