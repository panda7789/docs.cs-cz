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
ms.openlocfilehash: 4c16432df201d19b65c91206ec529d07605e979a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181792"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="822b5-102">nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="822b5-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="822b5-103">Spravovaný `nonComVisibleBaseClass` pomocník pro ladění (MDA) `QueryInterface` je aktivován, když je volání provedeno nativním nebo nespravovaným kódem na telefonním obalu COM (CCW) spravované třídy viditelné pro COM, která je odvozena ze základní třídy, která není viditelná pro COM.</span><span class="sxs-lookup"><span data-stu-id="822b5-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="822b5-104">Volání `QueryInterface` způsobí, že MDA aktivovat pouze v případech, `IDispatch` kdy volání požaduje rozhraní třídy nebo výchozí com viditelné spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="822b5-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="822b5-105">MDA není aktivován, `QueryInterface` pokud je pro explicitní <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> rozhraní, které má atribut použít a je explicitně implementována com viditelné třídy.</span><span class="sxs-lookup"><span data-stu-id="822b5-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="822b5-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="822b5-106">Symptoms</span></span>  
 <span data-ttu-id="822b5-107">Volání `QueryInterface` z nativního kódu, který selhává s COR_E_INVALIDOPERATION HRESULT.</span><span class="sxs-lookup"><span data-stu-id="822b5-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="822b5-108">HRESULT může být způsobeno za běhu nepovolování `QueryInterface` volání, které by způsobilo aktivaci tohoto MDA.</span><span class="sxs-lookup"><span data-stu-id="822b5-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="822b5-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="822b5-109">Cause</span></span>  
 <span data-ttu-id="822b5-110">Modul runtime `QueryInterface` nemůže povolit volání `IDispatch` pro rozhraní třídy nebo výchozí rozhraní třídy viditelné pro COM, která je odvozena z třídy, která není viditelná pro COM z důvodu potenciálních problémů se správu verzí.</span><span class="sxs-lookup"><span data-stu-id="822b5-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="822b5-111">Například pokud všechny veřejné členy byly přidány do základní třídy, která není viditelné COM, existující com klienti pomocí odvozené třídy by potenciálně přerušit, protože vtable odvozené třídy, která obsahuje členy základní třídy, by být změněny takové Změnit.</span><span class="sxs-lookup"><span data-stu-id="822b5-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="822b5-112">Explicitní rozhraní vystavená com nemají tento problém, protože nezahrnují základní členy rozhraní v vtable.</span><span class="sxs-lookup"><span data-stu-id="822b5-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="822b5-113">Řešení</span><span class="sxs-lookup"><span data-stu-id="822b5-113">Resolution</span></span>  
 <span data-ttu-id="822b5-114">Nezveřejňujte rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="822b5-114">Do not expose the class interface.</span></span> <span data-ttu-id="822b5-115">Definujte explicitní rozhraní <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> a aplikujte na něj atribut.</span><span class="sxs-lookup"><span data-stu-id="822b5-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="822b5-116">Vliv na běhový čas</span><span class="sxs-lookup"><span data-stu-id="822b5-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="822b5-117">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="822b5-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="822b5-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="822b5-118">Output</span></span>  
 <span data-ttu-id="822b5-119">Následuje ukázková zpráva pro `QueryInterface` volání třídy `Derived` viditelné pro COM, která je odvozena z třídy, `Base`která není viditelná jako COM .</span><span class="sxs-lookup"><span data-stu-id="822b5-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM
visible managed class 'Derived'. However since this class derives from
non COM visible class 'Base', the QueryInterface call will fail. This
is done to prevent the non COM visible base class from being
constrained by the COM versioning rules.
```  
  
## <a name="configuration"></a><span data-ttu-id="822b5-120">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="822b5-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="822b5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="822b5-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="822b5-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="822b5-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="822b5-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="822b5-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
