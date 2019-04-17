---
title: Obálka volatelná aplikacemi COM
ms.date: 10/23/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 942ba933126da291e072270318a5657953ddcdb8
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613249"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="a41c2-102">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="a41c2-102">COM Callable Wrapper</span></span>

<span data-ttu-id="a41c2-103">Jakmile klient modelu COM zavolá objekt rozhraní .NET, vytvoří modul CLR (Common Language Runtime) pro daný objekt spravovaný objekt a obálku volatelnou modelem COM (CCW).</span><span class="sxs-lookup"><span data-stu-id="a41c2-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="a41c2-104">Pokud nelze odkazovat na objekt rozhraní .NET přímo, budou klienti modelu COM pro spravovaný objekt používat objekt CCW jako proxy.</span><span class="sxs-lookup"><span data-stu-id="a41c2-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="a41c2-105">Modul runtime vytvoří pro spravovaný objekt přesně jeden objekt CCW, bez ohledu na počet klientů modelu COM, kteří vyžadují služby modelu.</span><span class="sxs-lookup"><span data-stu-id="a41c2-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="a41c2-106">Jak znázorňuje následující obrázek, může větší počet klientů modelu COM používat odkaz na objekt CCW, který zpřístupňuje rozhraní INew.</span><span class="sxs-lookup"><span data-stu-id="a41c2-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="a41c2-107">Na druhou stranu platí, že objekt CCW obsahuje jediný odkaz na spravovaný objekt, který implementuje rozhraní a u kterého je prováděno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a41c2-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="a41c2-108">Klienti modelu COM a rozhraní .NET mohou vytvářet požadavky na stejný spravovaný objekt současně.</span><span class="sxs-lookup"><span data-stu-id="a41c2-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![Více klientům modelu COM, která uchovává odkaz na objekt CCW, který zpřístupňuje INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="a41c2-110">Obálky volatelné modelem COM jsou pro ostatní třídy, které jsou spuštěny v rámci rozhraní .NET Framework, neviditelné.</span><span class="sxs-lookup"><span data-stu-id="a41c2-110">COM callable wrappers are invisible to other classes running within the .NET Framework.</span></span> <span data-ttu-id="a41c2-111">Jejich hlavním účelem je zařadit volání mezi spravovaný a nespravovaný kód. Nicméně objekty CCW provádějí také správu identity a doby života spravovaných objektů, které zabalují.</span><span class="sxs-lookup"><span data-stu-id="a41c2-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="a41c2-112">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="a41c2-112">Object Identity</span></span>

<span data-ttu-id="a41c2-113">Modul runtime přiděluje paměť objektu rozhraní .NET z množství uvolněné paměti, což modulu runtime umožňuje přesouvat objekt v paměti podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a41c2-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="a41c2-114">Naopak modul runtime přiděluje paměť pro objekt CCW z nenashromážděného množství, což klientům modelu COM umožňuje přímo odkazovat na obálku.</span><span class="sxs-lookup"><span data-stu-id="a41c2-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="a41c2-115">Doba života objektu</span><span class="sxs-lookup"><span data-stu-id="a41c2-115">Object Lifetime</span></span>

<span data-ttu-id="a41c2-116">Na rozdíl od objektu, který provádí zabalení klienta rozhraní .NET, je objekt CCW založen na tradičním způsobu počítání odkazů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="a41c2-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="a41c2-117">Pokud v případě objektů CCW dosáhne počet odkazů nuly, uvolní obálka svůj odkaz na spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="a41c2-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="a41c2-118">Spravovaný objekt, který již nemá žádné další odkazy, je shromážděn v rámci dalšího cyklu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a41c2-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="a41c2-119">Simulace rozhraní COM</span><span class="sxs-lookup"><span data-stu-id="a41c2-119">Simulating COM interfaces</span></span>

<span data-ttu-id="a41c2-120">Objekt CCW zpřístupňuje všechny veřejné, viditelný modulem COM rozhraní, datových typů a návratové hodnoty klientům modelu COM způsobem, který je konzistentní s modelu COM vynucení interakce založené na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="a41c2-121">Klient modelu COM volání metod pro objekt rozhraní .NET Framework je stejný jako volání metod na objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="a41c2-121">For a COM client, invoking methods on a .NET Framework object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="a41c2-122">Chcete-li vytvořit tento bezproblémový přístup, objekt CCW vyrábí tradiční rozhraní modelu COM, jako například **IUnknown** a **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="a41c2-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="a41c2-123">Jak ukazuje následující obrázek, objekt CCW udržuje jeden odkaz na objekt .NET, který ho zalamoval.</span><span class="sxs-lookup"><span data-stu-id="a41c2-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="a41c2-124">Klient COM a objektu rozhraní .NET komunikovat mezi sebou prostřednictvím proxy a zástupných procedur konstrukce CCW.</span><span class="sxs-lookup"><span data-stu-id="a41c2-124">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![Diagram znázorňující, jak objekt CCW vyrábí rozhraní modelu COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="a41c2-126">Kromě zpřístupnění rozhraní, která jsou explicitně implementováno třídou ve spravovaném prostředí, rozhraní .NET Framework poskytuje implementace rozhraní modelu COM, které jsou uvedeny v následující tabulce jménem objekt.</span><span class="sxs-lookup"><span data-stu-id="a41c2-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET Framework supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="a41c2-127">Třída rozhraní .NET výchozí chování můžete přepsat tím, že poskytuje vlastní implementaci těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="a41c2-128">Nicméně vždy modul runtime poskytuje implementaci pro **IUnknown** a **IDispatch** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="a41c2-129">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="a41c2-129">Interface</span></span>|<span data-ttu-id="a41c2-130">Popis</span><span class="sxs-lookup"><span data-stu-id="a41c2-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a41c2-131">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="a41c2-131">**IDispatch**</span></span>|<span data-ttu-id="a41c2-132">Poskytuje mechanismus pro pozdní vazbu na typ.</span><span class="sxs-lookup"><span data-stu-id="a41c2-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="a41c2-133">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="a41c2-133">**IErrorInfo**</span></span>|<span data-ttu-id="a41c2-134">Poskytuje textový popis chyby, její zdroj, soubor nápovědy, kontextové nápovědy a identifikátor GUID rozhraní definované chyba (vždy **GUID_NULL** pro třídy .NET).</span><span class="sxs-lookup"><span data-stu-id="a41c2-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="a41c2-135">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="a41c2-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="a41c2-136">Umožňuje získat přístup ke klientům modelu COM **ITypeInfo** rozhraní implementovány pomocí spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="a41c2-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span>|
|<span data-ttu-id="a41c2-137">**ISupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="a41c2-137">**ISupportErrorInfo**</span></span>|<span data-ttu-id="a41c2-138">Umožňuje určit, zda spravovaný objekt podporuje klient modelu COM **IErrorInfo** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-138">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="a41c2-139">Pokud ano, umožňuje klientům získat ukazatel objektu nejnovější výjimky.</span><span class="sxs-lookup"><span data-stu-id="a41c2-139">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="a41c2-140">Všechny spravované typy podporu **IErrorInfo** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-140">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="a41c2-141">**ITypeInfo**</span><span class="sxs-lookup"><span data-stu-id="a41c2-141">**ITypeInfo**</span></span>|<span data-ttu-id="a41c2-142">Poskytuje informace o typu pro třídu, která je stejná jako informace o typu, který je vytvořený pomocí Tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="a41c2-142">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="a41c2-143">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="a41c2-143">**IUnknown**</span></span>|<span data-ttu-id="a41c2-144">Poskytuje standardní implementace **IUnknown** rozhraní, se kterým klient modelu COM, spravuje životnost objekt CCW a obsahuje převod typu.</span><span class="sxs-lookup"><span data-stu-id="a41c2-144">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="a41c2-145">Spravované třídy můžete také zadat rozhraní modelu COM, které jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a41c2-145">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="a41c2-146">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="a41c2-146">Interface</span></span>|<span data-ttu-id="a41c2-147">Popis</span><span class="sxs-lookup"><span data-stu-id="a41c2-147">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a41c2-148">(\_*Classname*) rozhraní třídy</span><span class="sxs-lookup"><span data-stu-id="a41c2-148">The (\_*classname*) class interface</span></span>|<span data-ttu-id="a41c2-149">Rozhraní vystavena modulem runtime a nejsou explicitně definovány, která poskytuje veřejná rozhraní, metody, vlastnosti a pole, která dostanou na spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="a41c2-149">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="a41c2-150">**IConnectionPoint** a **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="a41c2-150">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="a41c2-151">Rozhraní pro objekty, které zdroj události na základě delegáta (rozhraní pro registraci odběratelů událostí).</span><span class="sxs-lookup"><span data-stu-id="a41c2-151">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="a41c2-152">**Rozhraní IDispatchEx**</span><span class="sxs-lookup"><span data-stu-id="a41c2-152">**IDispatchEx**</span></span>|<span data-ttu-id="a41c2-153">Zadaný modul runtime, pokud třída implementuje rozhraní **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="a41c2-153">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="a41c2-154">**Rozhraní IDispatchEx** rozhraní je rozšířením **IDispatch** rozhraní, na rozdíl od **IDispatch**, umožňuje výčtu, přidání, odstranění a malá a velká písmena volání členů.</span><span class="sxs-lookup"><span data-stu-id="a41c2-154">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="a41c2-155">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="a41c2-155">**IEnumVARIANT**</span></span>|<span data-ttu-id="a41c2-156">Rozhraní pro typ kolekce tříd, které vytvoří výčet objektů v kolekci, pokud třída implementuje **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="a41c2-156">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="a41c2-157">Představení rozhraní třídy</span><span class="sxs-lookup"><span data-stu-id="a41c2-157">Introducing the class interface</span></span>

<span data-ttu-id="a41c2-158">Rozhraní třídy, které nejsou výslovně definované ve spravovaném kódu, je rozhraní, který zpřístupňuje všechny veřejné metody, vlastnosti, pole a události, které se dostanou na objekt .NET.</span><span class="sxs-lookup"><span data-stu-id="a41c2-158">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="a41c2-159">Toto rozhraní může být duální nebo určené pouze pro rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-159">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="a41c2-160">Rozhraní třídy přijímá název třídy .NET, začínající podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="a41c2-160">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="a41c2-161">Například pro třídu savec, je třída rozhraní \_savec.</span><span class="sxs-lookup"><span data-stu-id="a41c2-161">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="a41c2-162">Odvozené třídy rozhraní třídy také zpřístupní všechny veřejné metody, vlastnosti a pole základní třídy.</span><span class="sxs-lookup"><span data-stu-id="a41c2-162">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="a41c2-163">Odvozená třída také poskytuje rozhraní třídy pro každou ze základních tříd.</span><span class="sxs-lookup"><span data-stu-id="a41c2-163">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="a41c2-164">Například pokud třída savec rozšiřuje třídu MammalSuperclass, které rozšiřuje System.Object, .NET zpřístupňuje objektů klienty modelu COM tři třídy rozhraní s názvem \_savec, \_MammalSuperclass, a \_objektu.</span><span class="sxs-lookup"><span data-stu-id="a41c2-164">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="a41c2-165">Představte si třeba následující třídy .NET:</span><span class="sxs-lookup"><span data-stu-id="a41c2-165">For example, consider the following .NET class:</span></span>

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
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

<span data-ttu-id="a41c2-166">Klient modelu COM může získání ukazatele na třídy rozhraní s názvem `_Mammal`, který je popsaný v knihovně typů, které [Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) Nástroj generuje.</span><span class="sxs-lookup"><span data-stu-id="a41c2-166">The COM client can obtain a pointer to a class interface named `_Mammal`, which is described in the type library that the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) tool generates.</span></span> <span data-ttu-id="a41c2-167">Pokud `Mammal` jedno nebo více rozhraní implementované třídy, rozhraní by se zobrazí pod coclass.</span><span class="sxs-lookup"><span data-stu-id="a41c2-167">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

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

<span data-ttu-id="a41c2-168">Generování třídy rozhraní je volitelné.</span><span class="sxs-lookup"><span data-stu-id="a41c2-168">Generating the class interface is optional.</span></span> <span data-ttu-id="a41c2-169">Ve výchozím nastavení spolupráci s COM generuje určené pouze pro rozhraní pro každou třídu, která exportujete do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a41c2-169">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="a41c2-170">Můžete zakázat nebo upravit automatické vytváření tohoto rozhraní použitím <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="a41c2-170">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="a41c2-171">Přestože rozhraní třídy můžete usnadnění vystavení spravované třídy modelu COM, jeho použití jsou omezené.</span><span class="sxs-lookup"><span data-stu-id="a41c2-171">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="a41c2-172">Pomocí třídy rozhraní, namísto explicitně definovat vlastní, může zkomplikovat budoucích verzí spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="a41c2-172">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="a41c2-173">Před použitím rozhraní si přečtěte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="a41c2-173">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="a41c2-174">Definujte explicitní rozhraní klientům modelu COM použít nikoli generování třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-174">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="a41c2-175">Protože komunikace s objekty COM automaticky vygeneruje třídy rozhraní, můžete změnit po verzi změny do vaší třídy rozložení třídy rozhraní vystavené modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a41c2-175">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="a41c2-176">Protože klienti modelu COM jsou obvykle připraven zpracovat změny v rozložení rozhraní, přerušit při změně rozložení třídy.</span><span class="sxs-lookup"><span data-stu-id="a41c2-176">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="a41c2-177">Toto pravidlo zvyšuje pojem, musí zůstat jakákoliv zveřejněné klientům modelu COM rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-177">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="a41c2-178">Aby se snížilo riziko rozbíjející klientům modelu COM opětovným uspořádáním neúmyslně rozložení rozhraní, izolují všechny změny do třídy z rozložení rozhraní explicitně definováním rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-178">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="a41c2-179">Použití **ClassInterfaceAttribute** musí vypnout automatické generování rozhraní, třídy a implementace explicitního rozhraní pro třídu, jak ukazuje následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="a41c2-179">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

<span data-ttu-id="a41c2-180">**ClassInterfaceType.None** hodnota zabraňuje rozhraní generovaných při exportu metadat třídy do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a41c2-180">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="a41c2-181">V předchozím příkladu, můžete přístup ke klientům modelu COM `LoanApp` pouze prostřednictvím třídy `IExplicit` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-181">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="a41c2-182">Vyhněte se ukládání do mezipaměti identifikátory odesílání (DISPID)</span><span class="sxs-lookup"><span data-stu-id="a41c2-182">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="a41c2-183">Pomocí rozhraní třídy je přijatelný varianta pro skriptované klientů, Microsoft Visual Basic 6.0 nebo jakéhokoli klienta s pozdní vazbou, která neukládá do mezipaměti dispID členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-183">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="a41c2-184">Hodnoty dispID určit členy rozhraní umožňující pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="a41c2-184">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="a41c2-185">Pro rozhraní třídy generování hodnoty dispID podle pozice člena v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-185">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="a41c2-186">Je-li změnit pořadí členů a exportovat třídy do knihovny typů, změní hodnoty dispID generované třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a41c2-186">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="a41c2-187">Chcete-li vyhnuli narušení funkčnosti klientů modelu COM s pozdní vazbou, při použití rozhraní třídy, použijte **ClassInterfaceAttribute** s **ClassInterfaceType.AutoDispatch** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a41c2-187">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="a41c2-188">Tato hodnota implementuje rozhraní určené pouze pro třídy, ale vynechá popis rozhraní z knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a41c2-188">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="a41c2-189">Bez případně popis rozhraní klienti nebudou moct mezipaměti hodnoty dispID v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a41c2-189">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="a41c2-190">I když se jedná o výchozí typ rozhraní pro rozhraní, můžete explicitně použít hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="a41c2-190">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

<span data-ttu-id="a41c2-191">Chcete-li získat identifikátor DispId člena rozhraní v době běhu, můžete volat klientům modelu COM **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="a41c2-191">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="a41c2-192">K vyvolání metody v rozhraní, předat jako argument pro DispId vrácená **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="a41c2-192">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="a41c2-193">Omezte použití možnosti duální rozhraní pro rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="a41c2-193">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="a41c2-194">Duální rozhraní povolit časná a pozdní vazby pro členy rozhraní modelu COM klienty.</span><span class="sxs-lookup"><span data-stu-id="a41c2-194">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="a41c2-195">V době návrhu a během testování může být užitečné nastavit na duální rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="a41c2-195">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="a41c2-196">Pro spravovanou třídu (a její základní třídy), která nebude nikdy změněn, tato možnost je také přijatelné.</span><span class="sxs-lookup"><span data-stu-id="a41c2-196">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="a41c2-197">Ve všech ostatních případech nenastavujte na duální rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="a41c2-197">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="a41c2-198">Automaticky generované duální rozhraní může být vhodné ve výjimečných případech; ale častěji vytvoří související verze složitost.</span><span class="sxs-lookup"><span data-stu-id="a41c2-198">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="a41c2-199">Například klienti modelu COM pomocí rozhraní třídy odvozené třídy může snadno překročit se změnami na základní třídu.</span><span class="sxs-lookup"><span data-stu-id="a41c2-199">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="a41c2-200">Při jiného výrobce poskytuje základní třídu, je rozložení rozhraní třídy mimo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a41c2-200">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="a41c2-201">Na rozdíl od rozhraní určené pouze pro odesílání, další duální rozhraní (**ClassInterfaceType.AutoDual**) obsahuje popis rozhraní třídy v exportované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a41c2-201">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="a41c2-202">Tento popis podporuje klienty s pozdní vazbou do mezipaměti hodnoty dispID v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a41c2-202">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="a41c2-203">Ujistěte se, že jsou všechna oznámení událostí modelu COM s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="a41c2-203">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="a41c2-204">Ve výchozím nastavení informace o typu modelu COM se vloží přímo do spravovaných sestavení, která eliminuje potřebu primárního sestavení interop (PIA).</span><span class="sxs-lookup"><span data-stu-id="a41c2-204">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="a41c2-205">Jeden z omezení vložené informace o typu je však, že volání časné vazby vtable nepodporuje doručování oznámení událostí modelu COM, ale podporuje pouze s pozdní vazbou `IDispatch::Invoke` volání.</span><span class="sxs-lookup"><span data-stu-id="a41c2-205">However, one of the limitations of embedded type information is that it does not supported delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="a41c2-206">Pokud vaše aplikace vyžaduje volání časné vazby na metody rozhraní události modelu COM, můžete nastavit **Embed Interop Types** v sadě Visual Studio k `true`, nebo obsahovat následující element v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="a41c2-206">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="a41c2-207">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a41c2-207">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="a41c2-208">COM – obálky</span><span class="sxs-lookup"><span data-stu-id="a41c2-208">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="a41c2-209">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="a41c2-209">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="a41c2-210">Kvalifikace typů .NET pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="a41c2-210">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)
- [<span data-ttu-id="a41c2-211">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="a41c2-211">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
