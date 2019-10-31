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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120722"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="29d66-102">Obálka volatelná aplikacemi COM</span><span class="sxs-lookup"><span data-stu-id="29d66-102">COM Callable Wrapper</span></span>

<span data-ttu-id="29d66-103">Jakmile klient modelu COM zavolá objekt rozhraní .NET, vytvoří modul CLR (Common Language Runtime) pro daný objekt spravovaný objekt a obálku volatelnou modelem COM (CCW).</span><span class="sxs-lookup"><span data-stu-id="29d66-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="29d66-104">Pokud nelze odkazovat na objekt rozhraní .NET přímo, budou klienti modelu COM pro spravovaný objekt používat objekt CCW jako proxy.</span><span class="sxs-lookup"><span data-stu-id="29d66-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="29d66-105">Modul runtime vytvoří pro spravovaný objekt přesně jeden objekt CCW, bez ohledu na počet klientů modelu COM, kteří vyžadují služby modelu.</span><span class="sxs-lookup"><span data-stu-id="29d66-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="29d66-106">Jak znázorňuje následující obrázek, může větší počet klientů modelu COM používat odkaz na objekt CCW, který zpřístupňuje rozhraní INew.</span><span class="sxs-lookup"><span data-stu-id="29d66-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="29d66-107">Na druhou stranu platí, že objekt CCW obsahuje jediný odkaz na spravovaný objekt, který implementuje rozhraní a u kterého je prováděno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="29d66-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="29d66-108">Klienti modelu COM a rozhraní .NET mohou vytvářet požadavky na stejný spravovaný objekt současně.</span><span class="sxs-lookup"><span data-stu-id="29d66-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![Několik klientů modelu COM drží odkaz na doleva, který zpřístupňuje INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="29d66-110">Obálky s příchodem modelu COM jsou neviditelné pro jiné třídy běžící v prostředí .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="29d66-110">COM callable wrappers are invisible to other classes running within the .NET runtime.</span></span> <span data-ttu-id="29d66-111">Jejich hlavním účelem je zařadit volání mezi spravovaný a nespravovaný kód. Nicméně objekty CCW provádějí také správu identity a doby života spravovaných objektů, které zabalují.</span><span class="sxs-lookup"><span data-stu-id="29d66-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="29d66-112">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="29d66-112">Object Identity</span></span>

<span data-ttu-id="29d66-113">Modul runtime přiděluje paměť objektu rozhraní .NET z množství uvolněné paměti, což modulu runtime umožňuje přesouvat objekt v paměti podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="29d66-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="29d66-114">Naopak modul runtime přiděluje paměť pro objekt CCW z nenashromážděného množství, což klientům modelu COM umožňuje přímo odkazovat na obálku.</span><span class="sxs-lookup"><span data-stu-id="29d66-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="29d66-115">Doba života objektu</span><span class="sxs-lookup"><span data-stu-id="29d66-115">Object Lifetime</span></span>

<span data-ttu-id="29d66-116">Na rozdíl od objektu, který provádí zabalení klienta rozhraní .NET, je objekt CCW založen na tradičním způsobu počítání odkazů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="29d66-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="29d66-117">Pokud v případě objektů CCW dosáhne počet odkazů nuly, uvolní obálka svůj odkaz na spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="29d66-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="29d66-118">Spravovaný objekt, který již nemá žádné další odkazy, je shromážděn v rámci dalšího cyklu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="29d66-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="29d66-119">Simulace rozhraní COM</span><span class="sxs-lookup"><span data-stu-id="29d66-119">Simulating COM interfaces</span></span>

<span data-ttu-id="29d66-120">DOLEVA zpřístupňuje všechna veřejná, rozhraní viditelná v modelu COM, datové typy a návratové hodnoty klientům modelu COM způsobem, který je konzistentní s vynucováním interakce založených na rozhraních modelu COM.</span><span class="sxs-lookup"><span data-stu-id="29d66-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="29d66-121">V případě klienta modelu COM je vyvolání metod objektu rozhraní .NET identické s voláním metod objektu COM.</span><span class="sxs-lookup"><span data-stu-id="29d66-121">For a COM client, invoking methods on a .NET object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="29d66-122">Pro vytvoření tohoto bezproblémového přístupu se v doleva vyrábí tradiční rozhraní COM, jako je **IUnknown** a **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="29d66-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="29d66-123">Jak ukazuje následující obrázek, doleva udržuje jediný odkaz na objekt .NET, který se zalomí.</span><span class="sxs-lookup"><span data-stu-id="29d66-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="29d66-124">Klient COM i objekt rozhraní .NET vzájemně komunikují prostřednictvím proxy serveru a vytváření zástupných procedur v rámci služby doleva.</span><span class="sxs-lookup"><span data-stu-id="29d66-124">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![Diagram znázorňující, jak doleva vyrábí rozhraní COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="29d66-126">Kromě vystavení rozhraní, která jsou explicitně implementována třídou ve spravovaném prostředí, modul runtime .NET poskytuje implementaci rozhraní COM uvedená v následující tabulce jménem objektu.</span><span class="sxs-lookup"><span data-stu-id="29d66-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET runtime supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="29d66-127">Třída .NET může přepsat výchozí chování tím, že poskytuje vlastní implementaci těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29d66-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="29d66-128">Modul runtime však vždy poskytuje implementaci rozhraní **IUnknown** a **IDispatch** .</span><span class="sxs-lookup"><span data-stu-id="29d66-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="29d66-129">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="29d66-129">Interface</span></span>|<span data-ttu-id="29d66-130">Popis</span><span class="sxs-lookup"><span data-stu-id="29d66-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="29d66-131">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="29d66-131">**IDispatch**</span></span>|<span data-ttu-id="29d66-132">Poskytuje mechanismus pro pozdní vazbu na typ.</span><span class="sxs-lookup"><span data-stu-id="29d66-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="29d66-133">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="29d66-133">**IErrorInfo**</span></span>|<span data-ttu-id="29d66-134">Poskytuje textový popis chyby, její zdroj, soubor s nápovědu, kontext nápovědu a identifikátor GUID rozhraní, které definuje chybu (vždy **GUID_NULL** pro třídy .NET).</span><span class="sxs-lookup"><span data-stu-id="29d66-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="29d66-135">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="29d66-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="29d66-136">Umožňuje klientům modelu COM získat přístup k rozhraní **volání ITypeInfo** implementovanému spravovanou třídou.</span><span class="sxs-lookup"><span data-stu-id="29d66-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span> <span data-ttu-id="29d66-137">Vrátí `COR_E_NOTSUPPORTED` pro .NET Core pro typy, které nejsou naimportované z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="29d66-137">Returns `COR_E_NOTSUPPORTED` on .NET Core for types not imported from COM.</span></span> |
|<span data-ttu-id="29d66-138">**ISupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="29d66-138">**ISupportErrorInfo**</span></span>|<span data-ttu-id="29d66-139">Umožňuje klientovi modelu COM určit, zda spravovaný objekt podporuje rozhraní **IErrorInfo** .</span><span class="sxs-lookup"><span data-stu-id="29d66-139">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="29d66-140">Pokud ano, umožňuje klientovi získat ukazatel na nejnovější objekt výjimky.</span><span class="sxs-lookup"><span data-stu-id="29d66-140">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="29d66-141">Všechny spravované typy podporují rozhraní **IErrorInfo** .</span><span class="sxs-lookup"><span data-stu-id="29d66-141">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="29d66-142">**Volání ITypeInfo** (pouze .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="29d66-142">**ITypeInfo** (.NET Framework Only)</span></span>|<span data-ttu-id="29d66-143">Poskytuje informace o typu pro třídu, která je přesně stejná jako informace o typu vytvořené nástrojem Tlbexp. exe.</span><span class="sxs-lookup"><span data-stu-id="29d66-143">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="29d66-144">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="29d66-144">**IUnknown**</span></span>|<span data-ttu-id="29d66-145">Poskytuje standardní implementaci rozhraní **IUnknown** , se kterým klient modelu COM spravuje dobu života doleva a poskytuje převod typu.</span><span class="sxs-lookup"><span data-stu-id="29d66-145">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="29d66-146">Spravovaná třída může také poskytovat rozhraní COM popsaná v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="29d66-146">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="29d66-147">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="29d66-147">Interface</span></span>|<span data-ttu-id="29d66-148">Popis</span><span class="sxs-lookup"><span data-stu-id="29d66-148">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="29d66-149">Rozhraní třídy (\_*ClassName*)</span><span class="sxs-lookup"><span data-stu-id="29d66-149">The (\_*classname*) class interface</span></span>|<span data-ttu-id="29d66-150">Rozhraní vystavené modulem runtime a není explicitně definováno, které zveřejňuje všechna veřejná rozhraní, metody, vlastnosti a pole, které jsou explicitně vystaveny na spravovaném objektu.</span><span class="sxs-lookup"><span data-stu-id="29d66-150">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="29d66-151">**IConnectionPoint** a **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="29d66-151">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="29d66-152">Rozhraní pro objekty, které jsou zdrojem událostí založených na delegátech (rozhraní pro registraci předplatitelů událostí).</span><span class="sxs-lookup"><span data-stu-id="29d66-152">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="29d66-153">**IDispatchEx –** (pouze .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="29d66-153">**IDispatchEx** (.NET Framework Only)</span></span>|<span data-ttu-id="29d66-154">Rozhraní dodávané modulem runtime, pokud třída implementuje **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="29d66-154">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="29d66-155">Rozhraní **IDispatchEx –** je rozšíření rozhraní **IDispatch** , které na rozdíl od rozhraní **IDispatch**povoluje vyčíslení, sčítání, odstraňování a rozlišování velkých a malých písmen členů.</span><span class="sxs-lookup"><span data-stu-id="29d66-155">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="29d66-156">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="29d66-156">**IEnumVARIANT**</span></span>|<span data-ttu-id="29d66-157">Rozhraní tříd typu kolekce, které vyčíslují objekty v kolekci, pokud třída implementuje rozhraní **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="29d66-157">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="29d66-158">Představení rozhraní třídy</span><span class="sxs-lookup"><span data-stu-id="29d66-158">Introducing the class interface</span></span>

<span data-ttu-id="29d66-159">Rozhraní třídy, které není explicitně definováno ve spravovaném kódu, je rozhraní, které zpřístupňuje všechny veřejné metody, vlastnosti, pole a události, které jsou explicitně vystaveny na objektu rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="29d66-159">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="29d66-160">Toto rozhraní může být rozhraní pouze pro duální nebo pouze pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="29d66-160">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="29d66-161">Rozhraní třídy přijímá název samotné třídy .NET, před kterým předchází podtržítko.</span><span class="sxs-lookup"><span data-stu-id="29d66-161">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="29d66-162">Například pro savce tříd je rozhraní třídy \_savců.</span><span class="sxs-lookup"><span data-stu-id="29d66-162">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="29d66-163">U odvozených tříd rozhraní třídy také zveřejňuje všechny veřejné metody, vlastnosti a pole základní třídy.</span><span class="sxs-lookup"><span data-stu-id="29d66-163">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="29d66-164">Odvozená třída také zpřístupňuje rozhraní třídy pro každou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="29d66-164">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="29d66-165">Například pokud třídy savců rozšiřuje třídu MammalSuperclass, která sám rozšiřuje System. Object, objekt .NET zpřístupňuje klientům modelu COM tři rozhraní třídy s názvem \_savci, \_MammalSuperclass a \_objekt.</span><span class="sxs-lookup"><span data-stu-id="29d66-165">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="29d66-166">Zvažte například následující třídu .NET:</span><span class="sxs-lookup"><span data-stu-id="29d66-166">For example, consider the following .NET class:</span></span>

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

<span data-ttu-id="29d66-167">Klient COM může získat ukazatel na rozhraní třídy s názvem `_Mammal`.</span><span class="sxs-lookup"><span data-stu-id="29d66-167">The COM client can obtain a pointer to a class interface named `_Mammal`.</span></span> <span data-ttu-id="29d66-168">V .NET Framework můžete použít nástroj [Exportér knihovny typů (Tlbexp. exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) k vygenerování knihovny typů obsahující `_Mammal` definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29d66-168">On .NET Framework, you can use the [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) tool to generate a type library containing the `_Mammal` interface definition.</span></span> <span data-ttu-id="29d66-169">Exportér knihovny typů není v rozhraní .NET Core podporován.</span><span class="sxs-lookup"><span data-stu-id="29d66-169">The Type Library Exporter is not supported on .NET Core.</span></span> <span data-ttu-id="29d66-170">Pokud `Mammal` třída implementovala jedno nebo více rozhraní, zobrazí se rozhraní v rámci třídy coclass.</span><span class="sxs-lookup"><span data-stu-id="29d66-170">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

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

<span data-ttu-id="29d66-171">Generování rozhraní třídy je volitelné.</span><span class="sxs-lookup"><span data-stu-id="29d66-171">Generating the class interface is optional.</span></span> <span data-ttu-id="29d66-172">Ve výchozím nastavení zprostředkovatel komunikace s objekty COM generuje pro každou třídu, kterou exportujete do knihovny typů, rozhraní pouze pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="29d66-172">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="29d66-173">Automatickému vytváření tohoto rozhraní můžete zabránit nebo upravit tak, že použijete <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> pro třídu.</span><span class="sxs-lookup"><span data-stu-id="29d66-173">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="29d66-174">I když rozhraní třídy může zjednodušit úlohu vystavení spravovaných tříd modelu COM, jejich použití je omezeno.</span><span class="sxs-lookup"><span data-stu-id="29d66-174">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="29d66-175">Použití rozhraní třídy namísto explicitního definování vlastního může zkomplikovat budoucí verze spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="29d66-175">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="29d66-176">Než použijete rozhraní třídy, přečtěte si následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="29d66-176">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="29d66-177">Definujte explicitní rozhraní pro klienty modelu COM, aby bylo možné použít místo generování rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="29d66-177">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="29d66-178">Vzhledem k tomu, že zprostředkovatel komunikace s objekty COM generuje rozhraní třídy automaticky, změny po změně verze vaší třídy mohou změnit rozložení rozhraní třídy vystavené modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="29d66-178">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="29d66-179">Vzhledem k tomu, že klienti modelu COM jsou obvykle nepřipraveni zpracovávat změny v rozložení rozhraní, jsou přerušeny při změně rozložení členů třídy.</span><span class="sxs-lookup"><span data-stu-id="29d66-179">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="29d66-180">Tento návod posiluje pojem, že rozhraní vystavená klientům modelu COM musejí zůstat nezměněná.</span><span class="sxs-lookup"><span data-stu-id="29d66-180">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="29d66-181">Chcete-li snížit riziko narušení klientů modelu COM neúmyslným přeřazením rozložení rozhraní, izolujte všechny změny třídy z rozložení rozhraní explicitním definováním rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29d66-181">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="29d66-182">Použijte **ClassInterfaceAttribute** k diskrokování automatické generace rozhraní třídy a implementaci explicitního rozhraní pro třídu, jak ukazuje následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="29d66-182">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

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

<span data-ttu-id="29d66-183">Hodnota **ClassInterfaceType. None** zabraňuje tomu, aby se rozhraní třídy vygenerovalo, když se metadata třídy exportují do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="29d66-183">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="29d66-184">V předchozím příkladu mají klienti modelu COM přístup k třídě `LoanApp` pouze prostřednictvím rozhraní `IExplicit`.</span><span class="sxs-lookup"><span data-stu-id="29d66-184">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="29d66-185">Vyhněte se neukládání do mezipaměti pro odesílání (identifikátory spId)</span><span class="sxs-lookup"><span data-stu-id="29d66-185">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="29d66-186">Použití rozhraní třídy je přijatelná možnost pro skripty spouštěné klienty, klienty Microsoft Visual Basic 6,0 nebo jakéhokoli klienta s pozdní vazbou, který neukládá do mezipaměti identifikátory spId členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29d66-186">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="29d66-187">Odidentifikátory DISPID identifikují členy rozhraní, aby umožnily pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="29d66-187">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="29d66-188">Pro rozhraní třídy je generování identifikátorů DISPID založeno na pozici člena v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29d66-188">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="29d66-189">Změníte-li pořadí člena a vyexportujete třídu do knihovny typů, změníte identifikátory spId vygenerované v rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="29d66-189">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="29d66-190">Aby nedocházelo k přerušení klientů modelu COM s pozdní vazbou při použití rozhraní třídy, použijte **ClassInterfaceAttribute** s hodnotou **ClassInterfaceType. Dispatch** .</span><span class="sxs-lookup"><span data-stu-id="29d66-190">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="29d66-191">Tato hodnota implementuje rozhraní třídy pouze pro odesílání, ale z knihovny typů je vynechán Popis rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29d66-191">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="29d66-192">Bez popisu rozhraní nemůžou klienti v době kompilace ukládat do mezipaměti identifikátory spId.</span><span class="sxs-lookup"><span data-stu-id="29d66-192">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="29d66-193">Přestože se jedná o výchozí typ rozhraní pro rozhraní třídy, můžete hodnotu atributu použít explicitně.</span><span class="sxs-lookup"><span data-stu-id="29d66-193">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

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

<span data-ttu-id="29d66-194">Chcete-li získat DispId člena rozhraní v době běhu, mohou klienti modelu COM volat metodu **IDispatch. GetIDsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="29d66-194">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="29d66-195">Chcete-li vyvolat metodu v rozhraní, předejte vrácenou hodnotu DispId jako argument do metody **IDispatch. Invoke**.</span><span class="sxs-lookup"><span data-stu-id="29d66-195">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="29d66-196">Omezte použití možnosti duálního rozhraní pro rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="29d66-196">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="29d66-197">Duální rozhraní umožňují předčasné a pozdní vazbu na členy rozhraní podle klientů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="29d66-197">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="29d66-198">V době návrhu a během testování může být užitečné nastavit rozhraní třídy na hodnotu duální.</span><span class="sxs-lookup"><span data-stu-id="29d66-198">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="29d66-199">Pro spravovanou třídu (a její základní třídy), která se nikdy neupraví, je tato možnost také přijatelná.</span><span class="sxs-lookup"><span data-stu-id="29d66-199">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="29d66-200">Ve všech ostatních případech Vyhněte nastavení rozhraní třídy na hodnotu duální.</span><span class="sxs-lookup"><span data-stu-id="29d66-200">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="29d66-201">Ve výjimečných případech může být vhodné automaticky vygenerované duální rozhraní. častěji ale vytváří složitost související s verzí.</span><span class="sxs-lookup"><span data-stu-id="29d66-201">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="29d66-202">Například klienti modelu COM používající rozhraní třídy odvozené třídy mohou snadno přerušit změny základní třídy.</span><span class="sxs-lookup"><span data-stu-id="29d66-202">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="29d66-203">Pokud třetí strana poskytne základní třídu, rozložení rozhraní třídy je mimo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="29d66-203">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="29d66-204">Na rozdíl od rozhraní pouze pro odesílání, duální rozhraní (**ClassInterfaceType. AutoDual**) poskytuje popis rozhraní třídy v exportované knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="29d66-204">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="29d66-205">Tento popis podporuje klienty s pozdní vazbou na ukládání identifikátorů spId do mezipaměti v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="29d66-205">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="29d66-206">Ujistěte se, že všechna oznámení o událostech COM jsou pozdní vazba.</span><span class="sxs-lookup"><span data-stu-id="29d66-206">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="29d66-207">Ve výchozím nastavení jsou informace o typu modelu COM vloženy přímo do spravovaných sestavení, což eliminuje nutnost primárních definičních sestavení (PIA).</span><span class="sxs-lookup"><span data-stu-id="29d66-207">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="29d66-208">Jedno z omezení vloženého typu informací však znamená, že nepodporuje doručování oznámení o událostech modelu COM pomocí volání vtable s časnou vazbou, ale podporuje pouze `IDispatch::Invoke` volání s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="29d66-208">However, one of the limitations of embedded type information is that it does not support delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="29d66-209">Pokud vaše aplikace vyžaduje volání s časnou vazbou na metody rozhraní COM, můžete nastavit vlastnost **Embed Interop Types** v sadě Visual Studio na `true`nebo zahrnout následující prvek do souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="29d66-209">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="29d66-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29d66-210">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="29d66-211">COM – obálky</span><span class="sxs-lookup"><span data-stu-id="29d66-211">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="29d66-212">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="29d66-212">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="29d66-213">Vystavení součástí .NET Core pro COM</span><span class="sxs-lookup"><span data-stu-id="29d66-213">Exposing .NET Core Components to COM</span></span>](../../core/native-interop/expose-components-to-com.md)
- [<span data-ttu-id="29d66-214">Kvalifikace typů .NET pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="29d66-214">Qualifying .NET Types for Interoperation</span></span>](qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="29d66-215">Obálka volatelná za běhu</span><span class="sxs-lookup"><span data-stu-id="29d66-215">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
