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
ms.openlocfilehash: 6f2f4055a95dbcea8d7872b5c5fa3ccede8c2c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400377"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="c43e8-102">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="c43e8-102">COM Callable Wrapper</span></span>

<span data-ttu-id="c43e8-103">Jakmile klient modelu COM zavolá objekt rozhraní .NET, vytvoří modul CLR (Common Language Runtime) pro daný objekt spravovaný objekt a obálku volatelnou modelem COM (CCW).</span><span class="sxs-lookup"><span data-stu-id="c43e8-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="c43e8-104">Pokud nelze odkazovat na objekt rozhraní .NET přímo, budou klienti modelu COM pro spravovaný objekt používat objekt CCW jako proxy.</span><span class="sxs-lookup"><span data-stu-id="c43e8-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="c43e8-105">Modul runtime vytvoří pro spravovaný objekt přesně jeden objekt CCW, bez ohledu na počet klientů modelu COM, kteří vyžadují služby modelu.</span><span class="sxs-lookup"><span data-stu-id="c43e8-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="c43e8-106">Jak znázorňuje následující obrázek, může větší počet klientů modelu COM používat odkaz na objekt CCW, který zpřístupňuje rozhraní INew.</span><span class="sxs-lookup"><span data-stu-id="c43e8-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="c43e8-107">Na druhou stranu platí, že objekt CCW obsahuje jediný odkaz na spravovaný objekt, který implementuje rozhraní a u kterého je prováděno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c43e8-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="c43e8-108">Klienti modelu COM a rozhraní .NET mohou vytvářet požadavky na stejný spravovaný objekt současně.</span><span class="sxs-lookup"><span data-stu-id="c43e8-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![Více klientů COM, kteří drží odkaz na CCW, který zveřejňuje INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="c43e8-110">Com volatelné obálky jsou neviditelné pro ostatní třídy spuštěné v rámci běhu .NET.</span><span class="sxs-lookup"><span data-stu-id="c43e8-110">COM callable wrappers are invisible to other classes running within the .NET runtime.</span></span> <span data-ttu-id="c43e8-111">Jejich hlavním účelem je zařadit volání mezi spravovaný a nespravovaný kód. Nicméně objekty CCW provádějí také správu identity a doby života spravovaných objektů, které zabalují.</span><span class="sxs-lookup"><span data-stu-id="c43e8-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="c43e8-112">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="c43e8-112">Object Identity</span></span>

<span data-ttu-id="c43e8-113">Modul runtime přiděluje paměť objektu rozhraní .NET z množství uvolněné paměti, což modulu runtime umožňuje přesouvat objekt v paměti podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c43e8-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="c43e8-114">Naopak modul runtime přiděluje paměť pro objekt CCW z nenashromážděného množství, což klientům modelu COM umožňuje přímo odkazovat na obálku.</span><span class="sxs-lookup"><span data-stu-id="c43e8-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="c43e8-115">Doba života objektu</span><span class="sxs-lookup"><span data-stu-id="c43e8-115">Object Lifetime</span></span>

<span data-ttu-id="c43e8-116">Na rozdíl od objektu, který provádí zabalení klienta rozhraní .NET, je objekt CCW založen na tradičním způsobu počítání odkazů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c43e8-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="c43e8-117">Pokud v případě objektů CCW dosáhne počet odkazů nuly, uvolní obálka svůj odkaz na spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="c43e8-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="c43e8-118">Spravovaný objekt, který již nemá žádné další odkazy, je shromážděn v rámci dalšího cyklu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c43e8-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="c43e8-119">Simulace rozhraní COM</span><span class="sxs-lookup"><span data-stu-id="c43e8-119">Simulating COM interfaces</span></span>

<span data-ttu-id="c43e8-120">CCW zveřejňuje všechna veřejná rozhraní, rozhraní, datové typy a vrácené hodnoty klientům COM způsobem, který je v souladu s vynucením interakce založené na rozhraní com.</span><span class="sxs-lookup"><span data-stu-id="c43e8-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="c43e8-121">Pro klienta COM je vyvolání metod na objektu .NET shodné s metodami vyvolání objektu COM.</span><span class="sxs-lookup"><span data-stu-id="c43e8-121">For a COM client, invoking methods on a .NET object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="c43e8-122">Chcete-li vytvořit tento bezproblémový přístup, CCW vyrábí tradiční com rozhraní, jako je **například IUnknown** a **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="c43e8-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="c43e8-123">Jak ukazuje následující obrázek, CCW udržuje jeden odkaz na objekt .NET, který obtéká.</span><span class="sxs-lookup"><span data-stu-id="c43e8-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="c43e8-124">Klient COM i objekt .NET vzájemně spolupracují prostřednictvím proxy serveru a ověřování stavu dat konstrukce CCW.</span><span class="sxs-lookup"><span data-stu-id="c43e8-124">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![Diagram, který ukazuje, jak CCW vyrábí rozhraní COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="c43e8-126">Kromě vystavení rozhraní, které jsou explicitně implementovány třídou ve spravovaném prostředí, modul runtime .NET dodává implementace rozhraní COM uvedených v následující tabulce jménem objektu.</span><span class="sxs-lookup"><span data-stu-id="c43e8-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET runtime supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="c43e8-127">Třída .NET může přepsat výchozí chování poskytnutím vlastní implementace těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c43e8-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="c43e8-128">Modul runtime však vždy poskytuje implementaci pro rozhraní **IUnknown** a **IDispatch.**</span><span class="sxs-lookup"><span data-stu-id="c43e8-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="c43e8-129">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="c43e8-129">Interface</span></span>|<span data-ttu-id="c43e8-130">Popis</span><span class="sxs-lookup"><span data-stu-id="c43e8-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c43e8-131">**Idispatch**</span><span class="sxs-lookup"><span data-stu-id="c43e8-131">**IDispatch**</span></span>|<span data-ttu-id="c43e8-132">Poskytuje mechanismus pro pozdní vazbu na typ.</span><span class="sxs-lookup"><span data-stu-id="c43e8-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="c43e8-133">**Ierrorinfo**</span><span class="sxs-lookup"><span data-stu-id="c43e8-133">**IErrorInfo**</span></span>|<span data-ttu-id="c43e8-134">Poskytuje textový popis chyby, její zdroj, soubor nápovědy, kontext nápovědy a identifikátor GUID rozhraní, které chybu definovalo (vždy **GUID_NULL** pro třídy .NET).</span><span class="sxs-lookup"><span data-stu-id="c43e8-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="c43e8-135">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="c43e8-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="c43e8-136">Umožňuje klientům COM získat přístup k rozhraní **ITypeInfo** implementovanému spravovanou třídou.</span><span class="sxs-lookup"><span data-stu-id="c43e8-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span> <span data-ttu-id="c43e8-137">Vrátí `COR_E_NOTSUPPORTED` na .NET Core pro typy, které nejsou importovány z com.</span><span class="sxs-lookup"><span data-stu-id="c43e8-137">Returns `COR_E_NOTSUPPORTED` on .NET Core for types not imported from COM.</span></span> |
|<span data-ttu-id="c43e8-138">**ISupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="c43e8-138">**ISupportErrorInfo**</span></span>|<span data-ttu-id="c43e8-139">Umožňuje klientovi COM určit, zda spravovaný objekt podporuje rozhraní **IErrorInfo.**</span><span class="sxs-lookup"><span data-stu-id="c43e8-139">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="c43e8-140">Pokud ano, umožňuje klientovi získat ukazatel na nejnovější objekt výjimky.</span><span class="sxs-lookup"><span data-stu-id="c43e8-140">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="c43e8-141">Všechny spravované typy podporují rozhraní **IErrorInfo.**</span><span class="sxs-lookup"><span data-stu-id="c43e8-141">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="c43e8-142">**ITypeInfo** (pouze rozhraní .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="c43e8-142">**ITypeInfo** (.NET Framework Only)</span></span>|<span data-ttu-id="c43e8-143">Poskytuje informace o typu pro třídu, která je přesně stejná jako informace o typu vytvořené tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="c43e8-143">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="c43e8-144">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="c43e8-144">**IUnknown**</span></span>|<span data-ttu-id="c43e8-145">Poskytuje standardní implementaci rozhraní **IUnknown,** se kterým klient COM spravuje životnost CCW a poskytuje typ nátlaku.</span><span class="sxs-lookup"><span data-stu-id="c43e8-145">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="c43e8-146">Spravovaná třída může také poskytnout rozhraní COM popsaná v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c43e8-146">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="c43e8-147">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="c43e8-147">Interface</span></span>|<span data-ttu-id="c43e8-148">Popis</span><span class="sxs-lookup"><span data-stu-id="c43e8-148">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c43e8-149">Rozhraní\_*třídy*( název třídy)</span><span class="sxs-lookup"><span data-stu-id="c43e8-149">The (\_*classname*) class interface</span></span>|<span data-ttu-id="c43e8-150">Rozhraní vystavené modulu runtime a není explicitně definováno, které zveřejňuje všechna veřejná rozhraní, metody, vlastnosti a pole, které jsou explicitně vystaveny spravovanému objektu.</span><span class="sxs-lookup"><span data-stu-id="c43e8-150">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="c43e8-151">**IConnectionPoint** a **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="c43e8-151">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="c43e8-152">Rozhraní pro objekty, které zdroj delegáta založené události (rozhraní pro registraci předplatitelů událostí).</span><span class="sxs-lookup"><span data-stu-id="c43e8-152">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="c43e8-153">**IDispatchEx** (pouze rozhraní .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="c43e8-153">**IDispatchEx** (.NET Framework Only)</span></span>|<span data-ttu-id="c43e8-154">Rozhraní dodané modulu runtime, pokud třída implementuje **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="c43e8-154">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="c43e8-155">Rozhraní **IDispatchEx** je rozšíření rozhraní **IDispatch,** které na rozdíl od **IDispatch**umožňuje výčet, sčítání, mazání a malá a velká písmena volání členů.</span><span class="sxs-lookup"><span data-stu-id="c43e8-155">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="c43e8-156">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="c43e8-156">**IEnumVARIANT**</span></span>|<span data-ttu-id="c43e8-157">Rozhraní pro třídy typu kolekce, které vyjmenovává objekty v kolekci, pokud třída implementuje **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="c43e8-157">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="c43e8-158">Představujeme rozhraní třídy</span><span class="sxs-lookup"><span data-stu-id="c43e8-158">Introducing the class interface</span></span>

<span data-ttu-id="c43e8-159">Rozhraní třídy, které není explicitně definováno ve spravovaném kódu, je rozhraní, které zveřejňuje všechny veřejné metody, vlastnosti, pole a události, které jsou explicitně vystaveny na objektu .NET.</span><span class="sxs-lookup"><span data-stu-id="c43e8-159">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="c43e8-160">Toto rozhraní může být duální nebo pouze pro odeslání rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c43e8-160">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="c43e8-161">Rozhraní třídy obdrží název samotné třídy .NET, před nímž je podtržítko.</span><span class="sxs-lookup"><span data-stu-id="c43e8-161">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="c43e8-162">Například pro třídu Mammal je \_rozhraní třídy Mammal.</span><span class="sxs-lookup"><span data-stu-id="c43e8-162">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="c43e8-163">Pro odvozené třídy rozhraní třídy také zveřejňuje všechny veřejné metody, vlastnosti a pole základní třídy.</span><span class="sxs-lookup"><span data-stu-id="c43e8-163">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="c43e8-164">Odvozené třídy také zpřístupňuje rozhraní třídy pro každou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="c43e8-164">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="c43e8-165">Například pokud třída Mammal rozšiřuje třídu MammalSuperclass, která sama rozšiřuje System.Object, objekt .NET \_zpřístupňuje klientům COM tři rozhraní třídy s názvem Mammal, \_MammalSuperclass a \_Object.</span><span class="sxs-lookup"><span data-stu-id="c43e8-165">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="c43e8-166">Zvažte například následující třídu .NET:</span><span class="sxs-lookup"><span data-stu-id="c43e8-166">For example, consider the following .NET class:</span></span>

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

<span data-ttu-id="c43e8-167">Klient COM může získat ukazatel na `_Mammal`rozhraní třídy s názvem .</span><span class="sxs-lookup"><span data-stu-id="c43e8-167">The COM client can obtain a pointer to a class interface named `_Mammal`.</span></span> <span data-ttu-id="c43e8-168">V rozhraní .NET Framework můžete použít nástroj [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) ke generování knihovny typů obsahující definici `_Mammal` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c43e8-168">On .NET Framework, you can use the [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) tool to generate a type library containing the `_Mammal` interface definition.</span></span> <span data-ttu-id="c43e8-169">Exportér knihovny typů není u jádra .NET podporován.</span><span class="sxs-lookup"><span data-stu-id="c43e8-169">The Type Library Exporter is not supported on .NET Core.</span></span> <span data-ttu-id="c43e8-170">Pokud `Mammal` třída implementována jedno nebo více rozhraní, rozhraní se zobrazí pod coclass.</span><span class="sxs-lookup"><span data-stu-id="c43e8-170">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

```console
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

<span data-ttu-id="c43e8-171">Generování rozhraní třídy je volitelné.</span><span class="sxs-lookup"><span data-stu-id="c43e8-171">Generating the class interface is optional.</span></span> <span data-ttu-id="c43e8-172">Ve výchozím nastavení interop com generuje rozhraní pouze pro odeslání pro každou třídu, kterou exportujete do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="c43e8-172">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="c43e8-173">Automatické vytváření tohoto rozhraní můžete zabránit nebo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> upravit použitím této třídy.</span><span class="sxs-lookup"><span data-stu-id="c43e8-173">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="c43e8-174">Přestože rozhraní třídy může usnadnit úlohu vystavení spravovaných tříd com, jeho použití jsou omezené.</span><span class="sxs-lookup"><span data-stu-id="c43e8-174">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="c43e8-175">Pomocí rozhraní třídy, namísto explicitně definování vlastní, může zkomplikovat budoucí správu verzí spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="c43e8-175">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="c43e8-176">Před použitím rozhraní třídy si přečtěte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="c43e8-176">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="c43e8-177">Definujte explicitní rozhraní pro klienty COM, které chcete použít, místo generování rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="c43e8-177">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="c43e8-178">Vzhledem k tomu, že interop com generuje rozhraní třídy automaticky, změny po verzi vaší třídy můžete změnit rozložení rozhraní třídy vystavené modulu runtime společného jazyka.</span><span class="sxs-lookup"><span data-stu-id="c43e8-178">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="c43e8-179">Vzhledem k tomu, že klienti COM jsou obvykle nepřipraveni na zpracování změn v rozložení rozhraní, přeruší se, pokud změníte rozložení členů třídy.</span><span class="sxs-lookup"><span data-stu-id="c43e8-179">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="c43e8-180">Tento pokyn posiluje představu, že rozhraní vystavená klientům COM musí zůstat neměnná.</span><span class="sxs-lookup"><span data-stu-id="c43e8-180">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="c43e8-181">Chcete-li snížit riziko přerušení klientů COM neúmyslně změnit pořadí rozložení rozhraní, izolovat všechny změny třídy z rozložení rozhraní explicitně definování rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c43e8-181">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="c43e8-182">Pomocí **classInterfaceAttribute** odpojit automatické generování rozhraní třídy a implementovat explicitní rozhraní pro třídu, jak ukazuje následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="c43e8-182">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

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

<span data-ttu-id="c43e8-183">Hodnota **ClassInterfaceType.None** zabraňuje generování rozhraní třídy při exportu metadat třídy do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="c43e8-183">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="c43e8-184">V předchozím příkladu mohou klienti `LoanApp` COM přistupovat `IExplicit` ke třídě pouze prostřednictvím rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c43e8-184">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="c43e8-185">Vyhněte se ukládání identifikátorů odeslání do mezipaměti (DispIds)</span><span class="sxs-lookup"><span data-stu-id="c43e8-185">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="c43e8-186">Použití rozhraní třídy je přijatelnou možností pro skriptované klienty, klienty jazyka Microsoft Visual Basic 6.0 nebo všechny klienty s pozdní vazbou, který neukládá do mezipaměti dispIds členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c43e8-186">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="c43e8-187">DispIds identifikovat členy rozhraní povolit pozdní vazby.</span><span class="sxs-lookup"><span data-stu-id="c43e8-187">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="c43e8-188">Pro rozhraní třídy generování DispIds je založena na pozici člena v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c43e8-188">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="c43e8-189">Pokud změníte pořadí člena a exportujete třídu do knihovny typů, změníte dispIds generované v rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="c43e8-189">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="c43e8-190">Chcete-li se vyhnout porušení pozdní vázané klienty COM při použití rozhraní třídy, použijte **ClassInterfaceAttribute** s **classInterfaceType.AutoDispatch** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c43e8-190">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="c43e8-191">Tato hodnota implementuje rozhraní třídy pouze pro odeslání, ale vynese popis rozhraní z knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="c43e8-191">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="c43e8-192">Bez popisu rozhraní klienti nejsou schopni do mezipaměti DispIds v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c43e8-192">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="c43e8-193">Přestože se jedná o výchozí typ rozhraní pro rozhraní třídy, můžete explicitně použít hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="c43e8-193">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

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

<span data-ttu-id="c43e8-194">Chcete-li získat DispId člena rozhraní za běhu, mohou klienti COM volat **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="c43e8-194">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="c43e8-195">Chcete-li vyvolat metodu v rozhraní, předejte vrácený DispId jako argument **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="c43e8-195">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="c43e8-196">Omezte pomocí možnosti duálního rozhraní pro rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="c43e8-196">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="c43e8-197">Duální rozhraní umožňují včasné a pozdní vazby na členy rozhraní klienty COM.</span><span class="sxs-lookup"><span data-stu-id="c43e8-197">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="c43e8-198">V době návrhu a během testování může být užitečné nastavit rozhraní třídy na duální.</span><span class="sxs-lookup"><span data-stu-id="c43e8-198">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="c43e8-199">Pro spravovanou třídu (a její základní třídy), která se nikdy nezmění, je tato možnost také přijatelná.</span><span class="sxs-lookup"><span data-stu-id="c43e8-199">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="c43e8-200">Ve všech ostatních případech se vyhněte nastavení rozhraní třídy na duální.</span><span class="sxs-lookup"><span data-stu-id="c43e8-200">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="c43e8-201">Automaticky generované duální rozhraní může být vhodné ve výjimečných případech; však častěji vytváří složitost související s verzí.</span><span class="sxs-lookup"><span data-stu-id="c43e8-201">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="c43e8-202">Například klienti COM pomocí rozhraní třídy odvozené třídy můžete snadno přerušit se změnami základní třídy.</span><span class="sxs-lookup"><span data-stu-id="c43e8-202">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="c43e8-203">Pokud třetí strana poskytuje základní třídu, rozložení rozhraní třídy je mimo vaši kontrolu.</span><span class="sxs-lookup"><span data-stu-id="c43e8-203">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="c43e8-204">Dále, na rozdíl od rozhraní pouze pro odeslání, duální rozhraní **(ClassInterfaceType.AutoDual**) poskytuje popis rozhraní třídy v knihovně exportovaných typů.</span><span class="sxs-lookup"><span data-stu-id="c43e8-204">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="c43e8-205">Takový popis povzbuzuje klienty s pozdní vazbou do mezipaměti DispIds v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c43e8-205">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="c43e8-206">Ujistěte se, že všechna oznámení událostí COM jsou pozdní vazba.</span><span class="sxs-lookup"><span data-stu-id="c43e8-206">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="c43e8-207">Ve výchozím nastavení jsou informace o typu COM vloženy přímo do spravovaných sestavení, což eliminuje potřebu primárních meziop sestavení (PIA).</span><span class="sxs-lookup"><span data-stu-id="c43e8-207">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="c43e8-208">Jedním z omezení informací o vloženém typu je však, že nepodporuje doručování oznámení událostí COM pomocí volání `IDispatch::Invoke` vtable s časnou vazbou, ale podporuje pouze volání s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="c43e8-208">However, one of the limitations of embedded type information is that it does not support delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="c43e8-209">Pokud vaše aplikace vyžaduje volání včasného vázaného na metody rozhraní událostí COM, můžete `true`nastavit vlastnost **Embed Interop Types** v sadě Visual Studio nebo zahrnout do souboru projektu následující prvek:</span><span class="sxs-lookup"><span data-stu-id="c43e8-209">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="c43e8-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="c43e8-210">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="c43e8-211">Obálky COM</span><span class="sxs-lookup"><span data-stu-id="c43e8-211">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="c43e8-212">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="c43e8-212">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="c43e8-213">Vystavení komponent .NET Core pro COM</span><span class="sxs-lookup"><span data-stu-id="c43e8-213">Exposing .NET Core Components to COM</span></span>](../../core/native-interop/expose-components-to-com.md)
- [<span data-ttu-id="c43e8-214">Kvalifikace typů .NET pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="c43e8-214">Qualifying .NET Types for Interoperation</span></span>](qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="c43e8-215">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="c43e8-215">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
