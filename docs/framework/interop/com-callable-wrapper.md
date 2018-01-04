---
title: "Obálka volatelná aplikacemi COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8c39d3c84fe24f86692c289860f22381a3cf5a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="731aa-102">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="731aa-102">COM Callable Wrapper</span></span>
<span data-ttu-id="731aa-103">Jakmile klient modelu COM zavolá objekt rozhraní .NET, vytvoří modul CLR (Common Language Runtime) pro daný objekt spravovaný objekt a obálku volatelnou modelem COM (CCW).</span><span class="sxs-lookup"><span data-stu-id="731aa-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="731aa-104">Pokud nelze odkazovat na objekt rozhraní .NET přímo, budou klienti modelu COM pro spravovaný objekt používat objekt CCW jako proxy.</span><span class="sxs-lookup"><span data-stu-id="731aa-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>  
  
 <span data-ttu-id="731aa-105">Modul runtime vytvoří pro spravovaný objekt přesně jeden objekt CCW, bez ohledu na počet klientů modelu COM, kteří vyžadují služby modelu.</span><span class="sxs-lookup"><span data-stu-id="731aa-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="731aa-106">Jak znázorňuje následující obrázek, může větší počet klientů modelu COM používat odkaz na objekt CCW, který zpřístupňuje rozhraní INew.</span><span class="sxs-lookup"><span data-stu-id="731aa-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="731aa-107">Na druhou stranu platí, že objekt CCW obsahuje jediný odkaz na spravovaný objekt, který implementuje rozhraní a u kterého je prováděno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="731aa-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="731aa-108">Klienti modelu COM a rozhraní .NET mohou vytvářet požadavky na stejný spravovaný objekt současně.</span><span class="sxs-lookup"><span data-stu-id="731aa-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>  
  
 <span data-ttu-id="731aa-109">![Obálka volatelná aplikacemi COM](../../../docs/framework/interop/media/ccw.gif "doleva")</span><span class="sxs-lookup"><span data-stu-id="731aa-109">![COM callable wrapper](../../../docs/framework/interop/media/ccw.gif "ccw")</span></span>  
<span data-ttu-id="731aa-110">Přístup k objektům rozhraní .NET prostřednictvím obálky volatelné modelem COM</span><span class="sxs-lookup"><span data-stu-id="731aa-110">Accessing .NET objects through COM callable wrapper</span></span>  
  
 <span data-ttu-id="731aa-111">Obálky volatelné modelem COM jsou pro ostatní třídy, které jsou spuštěny v rámci rozhraní .NET Framework, neviditelné.</span><span class="sxs-lookup"><span data-stu-id="731aa-111">COM callable wrappers are invisible to other classes running within the .NET Framework.</span></span> <span data-ttu-id="731aa-112">Jejich hlavním účelem je zařadit volání mezi spravovaný a nespravovaný kód. Nicméně objekty CCW provádějí také správu identity a doby života spravovaných objektů, které zabalují.</span><span class="sxs-lookup"><span data-stu-id="731aa-112">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>  
  
## <a name="object-identity"></a><span data-ttu-id="731aa-113">Identity – objekt</span><span class="sxs-lookup"><span data-stu-id="731aa-113">Object Identity</span></span>  
 <span data-ttu-id="731aa-114">Modul runtime přiděluje paměť objektu rozhraní .NET z množství uvolněné paměti, což modulu runtime umožňuje přesouvat objekt v paměti podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="731aa-114">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="731aa-115">Naopak modul runtime přiděluje paměť pro objekt CCW z nenashromážděného množství, což klientům modelu COM umožňuje přímo odkazovat na obálku.</span><span class="sxs-lookup"><span data-stu-id="731aa-115">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>  
  
## <a name="object-lifetime"></a><span data-ttu-id="731aa-116">Doba života objektu</span><span class="sxs-lookup"><span data-stu-id="731aa-116">Object Lifetime</span></span>  
 <span data-ttu-id="731aa-117">Na rozdíl od objektu, který provádí zabalení klienta rozhraní .NET, je objekt CCW založen na tradičním způsobu počítání odkazů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="731aa-117">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="731aa-118">Pokud v případě objektů CCW dosáhne počet odkazů nuly, uvolní obálka svůj odkaz na spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="731aa-118">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="731aa-119">Spravovaný objekt, který již nemá žádné další odkazy, je shromážděn v rámci dalšího cyklu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="731aa-119">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>  
  
## <a name="simulating-com-interfaces"></a><span data-ttu-id="731aa-120">Simulaci COM – rozhraní</span><span class="sxs-lookup"><span data-stu-id="731aa-120">Simulating COM interfaces</span></span>  
 <span data-ttu-id="731aa-121">[Obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md) (doleva) zpřístupní všechny veřejné, rozhraní COM – viditelné, datové typy a návratové hodnoty klientům COM způsobem, který je v souladu s COM na vynucení založené na rozhraní interakce.</span><span class="sxs-lookup"><span data-stu-id="731aa-121">The [COM callable wrapper](../../../docs/framework/interop/com-callable-wrapper.md) (CCW) exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="731aa-122">Pro klienta COM volání metod v rozhraní .NET Framework objektu je stejný jako k vyvolání metody u objektu COM.</span><span class="sxs-lookup"><span data-stu-id="731aa-122">For a COM client, invoking methods on a .NET Framework object is identical to invoking methods on a COM object.</span></span>  
  
 <span data-ttu-id="731aa-123">Pokud chcete vytvořit tento bezproblémový přístup, doleva vyrábí tradiční rozhraní modelu COM, například **IUnknown** a **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="731aa-123">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="731aa-124">Jak ukazuje následující obrázek, doleva udržuje jeden odkaz na objekt .NET, který se zabalí.</span><span class="sxs-lookup"><span data-stu-id="731aa-124">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="731aa-125">Klient COM i rozhraní .NET objekt vzájemně spolupracovat prostřednictvím proxy serveru a se zakázaným inzerováním konstrukce CCW.</span><span class="sxs-lookup"><span data-stu-id="731aa-125">Both the COM client and .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>  
  
 <span data-ttu-id="731aa-126">![COM – rozhraní](../../../docs/framework/interop/media/ccwwithinterfaces.gif "ccwwithinterfaces")</span><span class="sxs-lookup"><span data-stu-id="731aa-126">![COM interfaces](../../../docs/framework/interop/media/ccwwithinterfaces.gif "ccwwithinterfaces")</span></span>  
<span data-ttu-id="731aa-127">Rozhraní COM a obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="731aa-127">Com interfaces and the COM callable wrapper</span></span>  
  
 <span data-ttu-id="731aa-128">Kromě vystavení rozhraní, které jsou explicitně implementované třídou ve spravovaném prostředí, rozhraní .NET Framework poskytuje implementace rozhraní modelu COM, které jsou uvedené v následující tabulce jménem objekt.</span><span class="sxs-lookup"><span data-stu-id="731aa-128">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET Framework supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="731aa-129">Třída rozhraní .NET můžete přepsat výchozí chování tím, že poskytuje vlastní implementaci těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-129">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="731aa-130">Ale modulu runtime vždy poskytuje implementaci pro **IUnknown** a **IDispatch** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-130">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>  
  
|<span data-ttu-id="731aa-131">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="731aa-131">Interface</span></span>|<span data-ttu-id="731aa-132">Popis</span><span class="sxs-lookup"><span data-stu-id="731aa-132">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="731aa-133">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="731aa-133">**Idispatch**</span></span>|<span data-ttu-id="731aa-134">Poskytuje mechanismus pro pozdní vazbu na typ.</span><span class="sxs-lookup"><span data-stu-id="731aa-134">Provides a mechanism for late binding to type.</span></span>|  
|<span data-ttu-id="731aa-135">**IerrorInfo**</span><span class="sxs-lookup"><span data-stu-id="731aa-135">**IerrorInfo**</span></span>|<span data-ttu-id="731aa-136">Obsahuje textový popis chyby, její zdroj, soubor nápovědy, kontextové nápovědy a identifikátor GUID rozhraní definované chyba (vždy **GUID_NULL** pro rozhraní .NET třídy).</span><span class="sxs-lookup"><span data-stu-id="731aa-136">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|  
|<span data-ttu-id="731aa-137">**IprovideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="731aa-137">**IprovideClassInfo**</span></span>|<span data-ttu-id="731aa-138">Umožňuje klientům získat přístup k modelu COM **ITypeInfo** rozhraní implementované spravovanou třídou.</span><span class="sxs-lookup"><span data-stu-id="731aa-138">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span>|  
|<span data-ttu-id="731aa-139">**IsupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="731aa-139">**IsupportErrorInfo**</span></span>|<span data-ttu-id="731aa-140">Umožňuje klientovi COM, abyste zjistili, jestli podporuje spravovaného objektu **IErrorInfo** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-140">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="731aa-141">Pokud ano, umožňuje klientům získat ukazatele na nejnovější objekt výjimky.</span><span class="sxs-lookup"><span data-stu-id="731aa-141">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="731aa-142">Všechny typy podpora spravovaného **IErrorInfo** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-142">All managed types support the **IErrorInfo** interface.</span></span>|  
|<span data-ttu-id="731aa-143">**ItypeInfo**</span><span class="sxs-lookup"><span data-stu-id="731aa-143">**ItypeInfo**</span></span>|<span data-ttu-id="731aa-144">Poskytuje informace o typu pro třídu, která je stejná jako informace o typu vytvářených Tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="731aa-144">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|  
|<span data-ttu-id="731aa-145">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="731aa-145">**Iunknown**</span></span>|<span data-ttu-id="731aa-146">Poskytuje standardní implementace **IUnknown** rozhraní, se kterým klient COM spravuje životnost doleva a poskytuje převod typu.</span><span class="sxs-lookup"><span data-stu-id="731aa-146">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|  
  
 <span data-ttu-id="731aa-147">Spravované třídy můžete zadat taky rozhraní modelu COM, které jsou popsané v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="731aa-147">A managed class can also provide the COM interfaces described in the following table.</span></span>  
  
|<span data-ttu-id="731aa-148">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="731aa-148">Interface</span></span>|<span data-ttu-id="731aa-149">Popis</span><span class="sxs-lookup"><span data-stu-id="731aa-149">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="731aa-150">(_*Classname*) rozhraní – třída</span><span class="sxs-lookup"><span data-stu-id="731aa-150">The (_*classname*) class interface</span></span>|<span data-ttu-id="731aa-151">Rozhraní, vystavené modulu runtime a nejsou explicitně definovány, který zpřístupní všechny veřejné rozhraní, metody, vlastnosti a pole, která jsou explicitně zveřejněné na spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="731aa-151">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|  
|<span data-ttu-id="731aa-152">**IConnectionPoint –** a **IconnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="731aa-152">**IConnectionPoint** and **IconnectionPointContainer**</span></span>|<span data-ttu-id="731aa-153">Rozhraní pro objekty, které zdroje události na základě delegáta (rozhraní pro registraci události odběratele).</span><span class="sxs-lookup"><span data-stu-id="731aa-153">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|  
|<span data-ttu-id="731aa-154">**IdispatchEx**</span><span class="sxs-lookup"><span data-stu-id="731aa-154">**IdispatchEx**</span></span>|<span data-ttu-id="731aa-155">Zadaný modulem runtime, pokud třída implementuje rozhraní **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="731aa-155">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="731aa-156">**IDispatchEx** rozhraní je rozšířením **IDispatch** rozhraní, na rozdíl od **IDispatch**, umožňuje výčtu, přidání, odstranění a to malá a velká písmena volání metody členů.</span><span class="sxs-lookup"><span data-stu-id="731aa-156">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|  
|<span data-ttu-id="731aa-157">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="731aa-157">**IEnumVARIANT**</span></span>|<span data-ttu-id="731aa-158">Rozhraní pro typ kolekce tříd, které vytvoří výčet objektů v kolekci, pokud třída implementuje **rozhraní IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="731aa-158">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|  
  
## <a name="introducing-the-class-interface"></a><span data-ttu-id="731aa-159">Představení rozhraní – třída</span><span class="sxs-lookup"><span data-stu-id="731aa-159">Introducing the class interface</span></span>  
 <span data-ttu-id="731aa-160">Třída rozhraní, které nejsou výslovně definované ve spravovaném kódu, je rozhraní, které vystavuje všechny veřejné metody, vlastnosti, pole a události, které jsou explicitně zveřejněné na objekt .NET.</span><span class="sxs-lookup"><span data-stu-id="731aa-160">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="731aa-161">Toto rozhraní může být dva nebo pouze pro odeslání rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-161">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="731aa-162">Třída rozhraní obdrží název třídy rozhraní .NET, samostatně, podtržítko před sebou.</span><span class="sxs-lookup"><span data-stu-id="731aa-162">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="731aa-163">Třída rozhraní je pro třídu savec _Mammal.</span><span class="sxs-lookup"><span data-stu-id="731aa-163">For example, for class Mammal, the class interface is _Mammal.</span></span>  
  
 <span data-ttu-id="731aa-164">Odvozené třídy rozhraní třída taky zpřístupňuje všechny veřejné metody, vlastnosti a pole základní třídy.</span><span class="sxs-lookup"><span data-stu-id="731aa-164">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="731aa-165">Odvozené třídy taky zpřístupňuje rozhraní třídy pro každou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="731aa-165">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="731aa-166">Například pokud třída savec rozšiřuje třídu MammalSuperclass, které rozšiřuje System.Object, vystavuje rozhraní modelu COM klienti tři třídy s názvem _Mammal, _MammalSuperclass a _Object objekt .NET.</span><span class="sxs-lookup"><span data-stu-id="731aa-166">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named _Mammal, _MammalSuperclass, and _Object.</span></span>  
  
 <span data-ttu-id="731aa-167">Zvažte například následující třídy rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="731aa-167">For example, consider the following .NET class:</span></span>  
  
```vb  
' Applies the ClassInterfaceAttribute to set the interface to dual.  
<ClassInterface(ClassInterfaceType.AutoDual)> _  
' Implicitly extends System.Object.  
Public Class Mammal  
    Sub Eat()  
    Sub Breathe()  
    Sub Sleep()  
End Class  
```  
  
```csharp  
// Applies the ClassInterfaceAttribute to set the interface to dual.  
[ClassInterface(ClassInterfaceType.AutoDual)]  
// Implicitly extends System.Object.  
public class Mammal  
{  
    void  Eat();  
    void  Breathe():  
    void  Sleep();  
}  
```  
  
 <span data-ttu-id="731aa-168">Klient COM můžete získat ukazatele na třídu rozhraní s názvem `_Mammal`, který je popsaný v knihovně typu, [Exportér knihovny typů (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) nástroj, který generuje.</span><span class="sxs-lookup"><span data-stu-id="731aa-168">The COM client can obtain a pointer to a class interface named `_Mammal`, which is described in the type library that the [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) tool generates.</span></span> <span data-ttu-id="731aa-169">Pokud `Mammal` třída implementovat jednu nebo více rozhraní, rozhraní se zobrazí v části coclass.</span><span class="sxs-lookup"><span data-stu-id="731aa-169">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>  
  
```  
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]  
interface _Mammal : IDispatch  
{  
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*  
        pRetVal);  
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]  
        VARIANT_BOOL* pRetVal);  
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);  
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);  
    [id(0x6002000d)] HRESULT Eat();  
    [id(0x6002000e)] HRESULT Breathe();  
    [id(0x6002000f)] HRESULT Sleep();  
}  
[uuid(…)]  
coclass Mammal   
{  
    [default] interface _Mammal;  
}  
```  
  
 <span data-ttu-id="731aa-170">Generování rozhraní třída je volitelný.</span><span class="sxs-lookup"><span data-stu-id="731aa-170">Generating the class interface is optional.</span></span> <span data-ttu-id="731aa-171">Ve výchozím nastavení generuje zprostředkovatel komunikace s objekty COM rozhraní, které je určené pouze pro jednotlivé třídy, které můžete exportovat do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="731aa-171">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="731aa-172">Můžete zakázat nebo upravit automatické vytvoření tohoto rozhraní s použitím <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> na třídu.</span><span class="sxs-lookup"><span data-stu-id="731aa-172">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="731aa-173">I když je třída rozhraní můžete zjednodušují vystavení spravované třídy do modelu COM, jeho použití jsou omezené.</span><span class="sxs-lookup"><span data-stu-id="731aa-173">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="731aa-174">Pomocí třídy rozhraní, namísto výslovně definování vlastní, může zkomplikovat budoucí verze vaší spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="731aa-174">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="731aa-175">Před použitím rozhraní třída přečtěte si následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="731aa-175">Please read the following guidelines before using the class interface.</span></span>  
  
### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="731aa-176">Zadejte explicitní rozhraní COM klientům použít nikoli generování rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="731aa-176">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>  
 <span data-ttu-id="731aa-177">Vzhledem k tomu, že zprostředkovatel komunikace s objekty COM automaticky vygeneruje třídu rozhraní, můžete změny po verze vaší třídy změnit rozložení rozhraní třída vystavené modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="731aa-177">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="731aa-178">Vzhledem k tomu, že jsou klienti COM obvykle neupravený zpracovat změny v rozložení rozhraní, přerušení při změně rozložení člena třídy.</span><span class="sxs-lookup"><span data-stu-id="731aa-178">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>  
  
 <span data-ttu-id="731aa-179">Toto platí posiluje zápisu, rozhraní, které jsou vystavené klientům COM musí zůstat neměnný.</span><span class="sxs-lookup"><span data-stu-id="731aa-179">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="731aa-180">Aby se snížilo riziko nejnovější klientů modelu COM pomocí nechtěně Změna rozložení rozhraní, izolovat všechny změny do třídy z rozhraní rozložení explicitně definováním rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-180">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>  
  
 <span data-ttu-id="731aa-181">Použití **ClassInterfaceAttribute** musí vypnout automatické generování třídy rozhraní a implementace explicitního rozhraní pro třídu, jak ukazuje následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="731aa-181">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>  
  
```vb  
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp  
    Implements IExplicit  
    Sub M() Implements IExplicit.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.None)]  
public class LoanApp : IExplicit {  
    void M();  
}  
```  
  
 <span data-ttu-id="731aa-182">**ClassInterfaceType.None** hodnota zabraňuje rozhraní třída generován při metadata tříd se exportují do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="731aa-182">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="731aa-183">V předchozím příkladu, mohou mít přístup klienti COM `LoanApp` pouze prostřednictvím třídy `IExplicit` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-183">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>  
  
### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="731aa-184">Vyhněte se ukládání do mezipaměti identifikátorů odesílání (hodnoty DISPID).</span><span class="sxs-lookup"><span data-stu-id="731aa-184">Avoid caching dispatch identifiers (DispIds).</span></span>  
 <span data-ttu-id="731aa-185">Pomocí třídy rozhraní je přijatelné možnost pro skriptované klientů, Microsoft Visual Basic 6.0 nebo libovolného klienta pozdní vazbou, který neukládá do mezipaměti hodnoty dispID rozhraní členů.</span><span class="sxs-lookup"><span data-stu-id="731aa-185">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="731aa-186">Hodnoty dispID identifikovat členové rozhraní povolit pozdní vazba.</span><span class="sxs-lookup"><span data-stu-id="731aa-186">DispIds identify interface members to enable late binding.</span></span>  
  
 <span data-ttu-id="731aa-187">Pro rozhraní třídy generování hodnoty dispID vychází z pozice člena v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-187">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="731aa-188">Je-li změnit pořadí člena a exportovat třídu do knihovny typů, změní se hodnoty dispID generované třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-188">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>  
  
 <span data-ttu-id="731aa-189">Pokud chcete vyhnout pozastavení klienti COM pozdní vazbou při pomocí třídy rozhraní, použít **ClassInterfaceAttribute** s **ClassInterfaceType.AutoDispatch** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="731aa-189">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="731aa-190">Tato hodnota implementuje rozhraní, které je určené pouze pro třídy, ale vynechá popis rozhraní z knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="731aa-190">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="731aa-191">Bez popisu rozhraní se klienti nemohou doba kompilace hodnoty dispID v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="731aa-191">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="731aa-192">Přestože je toto výchozí typ rozhraní pro třídu rozhraní, můžete použít hodnotu atributu explicitně.</span><span class="sxs-lookup"><span data-stu-id="731aa-192">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>  
  
```vb  
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp  
    Implements IAnother  
    Sub M() Implements IAnother.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.AutoDispatch]  
public class LoanApp : IAnother {  
    void M();  
}  
```  
  
 <span data-ttu-id="731aa-193">Chcete-li získat DispId člena rozhraní za běhu, klienti COM zavolat **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="731aa-193">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="731aa-194">Pro vyvolání metody na rozhraní, předat jako argument pro vrácené DispId **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="731aa-194">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>  
  
### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="731aa-195">Omezte pomocí možnosti duální rozhraní pro třídu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="731aa-195">Restrict using the dual interface option for the class interface.</span></span>  
 <span data-ttu-id="731aa-196">Duální rozhraní povolit časná a pozdní vazbu na členy rozhraní COM klienty.</span><span class="sxs-lookup"><span data-stu-id="731aa-196">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="731aa-197">V době návrhu a během testování může být užitečné nastavit rozhraní třídy na dva.</span><span class="sxs-lookup"><span data-stu-id="731aa-197">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="731aa-198">Pro spravované třídy (a její základní třídy), nikdy nebudou změněna, tato možnost je také přijatelné.</span><span class="sxs-lookup"><span data-stu-id="731aa-198">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="731aa-199">Ve všech ostatních případech Vyhněte se nastavení rozhraní třída Dual.</span><span class="sxs-lookup"><span data-stu-id="731aa-199">In all other cases, avoid setting the class interface to dual.</span></span>  
  
 <span data-ttu-id="731aa-200">Duální rozhraní automaticky generované může být vhodné ve výjimečných případech; ale častěji vytvoří verze související složitost.</span><span class="sxs-lookup"><span data-stu-id="731aa-200">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="731aa-201">Například klientů modelu COM pomocí rozhraní třídy odvozené třídy můžete snadno rozdělit změn v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="731aa-201">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="731aa-202">Když třetích stran poskytuje základní třídu, rozložení rozhraní třída je mimo vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="731aa-202">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="731aa-203">Na rozdíl od určené pouze pro rozhraní, další dva rozhraní (**ClassInterface.AutoDual**) obsahuje popis rozhraní – třída v knihovně exportovaný typu.</span><span class="sxs-lookup"><span data-stu-id="731aa-203">Further, unlike a dispatch-only interface, a dual interface (**ClassInterface.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="731aa-204">Tento popis doporučuje pozdní vazbou klientům mezipaměti hodnoty dispID za běhu.</span><span class="sxs-lookup"><span data-stu-id="731aa-204">Such a description encourages late-bound clients to cache DispIds at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="731aa-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="731aa-205">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [<span data-ttu-id="731aa-206">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="731aa-206">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)  
 [<span data-ttu-id="731aa-207">COM – obálky</span><span class="sxs-lookup"><span data-stu-id="731aa-207">COM Wrappers</span></span>](../../../docs/framework/interop/com-wrappers.md)  
 [<span data-ttu-id="731aa-208">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="731aa-208">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="731aa-209">Simulace COM – rozhraní</span><span class="sxs-lookup"><span data-stu-id="731aa-209">Simulating COM Interfaces</span></span>](http://msdn.microsoft.com/en-us/ad2ab959-e2be-411b-aaff-275c3fba606c)  
 [<span data-ttu-id="731aa-210">Kvalifikace typů .NET pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="731aa-210">Qualifying .NET Types for Interoperation</span></span>](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [<span data-ttu-id="731aa-211">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="731aa-211">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)
