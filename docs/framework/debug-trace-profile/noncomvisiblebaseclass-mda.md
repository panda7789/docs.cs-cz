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
ms.openlocfilehash: e4340dd75e24ddeb01428159d5532b86e76fd8b4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052441"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="7b590-102">nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="7b590-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="7b590-103">Pomocník spravovaného ladění (MDA) je aktivován `QueryInterface` při volání z nativního nebo nespravovaného kódu na obálku s podporou modelu COM, která je odvozena ze základní třídy, která není viditelná v modelu COM. `nonComVisibleBaseClass`</span><span class="sxs-lookup"><span data-stu-id="7b590-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="7b590-104">Volání způsobí, že se třída MDA aktivuje pouze v případech, kdy volání vyžaduje rozhraní třídy `IDispatch` nebo výchozí spravovanou třídu viditelnou z modelu COM. `QueryInterface`</span><span class="sxs-lookup"><span data-stu-id="7b590-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="7b590-105">MDA se neaktivuje, pokud `QueryInterface` je pro explicitní rozhraní, které <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> má atribut použit a je explicitně implementováno třídou, která je viditelná v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7b590-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7b590-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="7b590-106">Symptoms</span></span>  
 <span data-ttu-id="7b590-107">Bylo `QueryInterface` provedeno volání z nativního kódu, které se nedaří s COR_E_INVALIDOPERATION HRESULT.</span><span class="sxs-lookup"><span data-stu-id="7b590-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="7b590-108">Hodnota HRESULT může být způsobena nepovolenými `QueryInterface` voláními modulu runtime, která by způsobila aktivaci této aplikace MDA.</span><span class="sxs-lookup"><span data-stu-id="7b590-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7b590-109">příčina</span><span class="sxs-lookup"><span data-stu-id="7b590-109">Cause</span></span>  
 <span data-ttu-id="7b590-110">Modul runtime nemůže umožňovat `QueryInterface` volání rozhraní třídy nebo výchozího `IDispatch` rozhraní třídy viditelné v modelu COM, která je odvozena od třídy, která není viditelná jako model COM, z důvodu potenciálních problémů se správou verzí.</span><span class="sxs-lookup"><span data-stu-id="7b590-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="7b590-111">Například pokud byly některé veřejné členy přidány do základní třídy, která není viditelná v modelu COM, existující klienti modelu COM používající odvozenou třídu mohou potenciálně poškodit, protože tabulka odvozené třídy, která obsahuje členy základní třídy, by mohla být změněna tímto mění.</span><span class="sxs-lookup"><span data-stu-id="7b590-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="7b590-112">Explicitní rozhraní vystavená modelu COM nemají tento problém, protože neobsahují základní členy rozhraní v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="7b590-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7b590-113">Řešení</span><span class="sxs-lookup"><span data-stu-id="7b590-113">Resolution</span></span>  
 <span data-ttu-id="7b590-114">Nezveřejňujte rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="7b590-114">Do not expose the class interface.</span></span> <span data-ttu-id="7b590-115">Definujte explicitní rozhraní a použijte <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> k němu atribut.</span><span class="sxs-lookup"><span data-stu-id="7b590-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7b590-116">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="7b590-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="7b590-117">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="7b590-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7b590-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="7b590-118">Output</span></span>  
 <span data-ttu-id="7b590-119">Následuje příklad zprávy pro `QueryInterface` volání ve třídě `Derived` viditelné pomocí modelu COM, která je odvozena od třídy `Base`, která není viditelná z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7b590-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="7b590-120">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="7b590-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b590-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b590-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7b590-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7b590-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7b590-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="7b590-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
