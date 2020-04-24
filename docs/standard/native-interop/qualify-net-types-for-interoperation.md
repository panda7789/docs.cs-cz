---
title: Kvalifikace typů .NET pro mezichodové operace COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: f0b9bc03225ae3d2365a21fd3b78d09c08d4fc1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091582"
---
# <a name="qualifying-net-types-for-com-interoperation"></a><span data-ttu-id="6edc2-102">Kvalifikace typů .NET pro mezichodové operace COM</span><span class="sxs-lookup"><span data-stu-id="6edc2-102">Qualifying .NET Types for COM Interoperation</span></span>
<span data-ttu-id="6edc2-103">Pokud máte v úmyslu vystavovat typy v sestavení s aplikacemi modelu COM, zvažte požadavky zprostředkovatele komunikace s objekty COM v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="6edc2-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="6edc2-104">Spravované typy (třída, rozhraní, struktura a výčet) hladce integrují s typy modelu COM, když dodržujete následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="6edc2-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="6edc2-105">Třídy by měly implementovat rozhraní explicitně.</span><span class="sxs-lookup"><span data-stu-id="6edc2-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="6edc2-106">I když zprostředkovatel komunikace s objekty COM poskytuje mechanismus pro automatické generování rozhraní obsahujícího všechny členy třídy a členy své základní třídy, je mnohem lepší poskytnout explicitní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6edc2-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="6edc2-107">Automaticky generované rozhraní se nazývá rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="6edc2-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="6edc2-108">Pokyny naleznete v tématu [Představujeme rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="6edc2-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="6edc2-109">Můžete použít Visual Basic, C# a C++ pro začlenění definic rozhraní do kódu, místo abyste museli používat rozhraní IDL (Interface Definition Language) nebo jeho ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="6edc2-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="6edc2-110">Podrobnosti o syntaxi najdete v dokumentaci jazyka.</span><span class="sxs-lookup"><span data-stu-id="6edc2-110">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="6edc2-111">Spravované typy musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="6edc2-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="6edc2-112">Pouze veřejné typy v sestavení jsou registrovány a exportovány do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="6edc2-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="6edc2-113">V důsledku toho jsou pro model COM viditelné pouze veřejné typy.</span><span class="sxs-lookup"><span data-stu-id="6edc2-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="6edc2-114">Spravované typy zpřístupňují funkce jinému spravovanému kódu, který nemusí být vystavený modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6edc2-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="6edc2-115">Například parametrizované konstruktory, statické metody a konstantní pole nejsou vystaveny klientům modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6edc2-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="6edc2-116">V případě, že modul runtime zařazování dat do a z typu, mohou být data zkopírována nebo transformována.</span><span class="sxs-lookup"><span data-stu-id="6edc2-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="6edc2-117">Metody, vlastnosti, pole a události musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="6edc2-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="6edc2-118">Členové veřejných typů musí být také veřejné, pokud mají být viditelné modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6edc2-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="6edc2-119">Můžete omezit viditelnost sestavení, veřejného typu nebo veřejných členů veřejného typu použitím <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6edc2-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="6edc2-120">Ve výchozím nastavení jsou všechny veřejné typy a členy viditelné.</span><span class="sxs-lookup"><span data-stu-id="6edc2-120">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="6edc2-121">Typy musí mít veřejný konstruktor bez parametrů, který se má aktivovat z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6edc2-121">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="6edc2-122">Spravované, veřejné typy jsou viditelné v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6edc2-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="6edc2-123">Nicméně bez veřejného konstruktoru bez parametrů (konstruktor bez argumentů) nemohou klienti modelu COM vytvořit typ.</span><span class="sxs-lookup"><span data-stu-id="6edc2-123">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="6edc2-124">Klienti modelu COM mohou i nadále používat typ, pokud je aktivován jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="6edc2-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="6edc2-125">Typy nemohou být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="6edc2-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="6edc2-126">Klienti modelu COM ani klienti rozhraní .NET nemohou vytvářet abstraktní typy.</span><span class="sxs-lookup"><span data-stu-id="6edc2-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="6edc2-127">Při exportu do modelu COM je Hierarchie dědičnosti spravovaného typu sloučena.</span><span class="sxs-lookup"><span data-stu-id="6edc2-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="6edc2-128">Správa verzí se také liší mezi spravovanými a nespravovanými prostředími.</span><span class="sxs-lookup"><span data-stu-id="6edc2-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="6edc2-129">Typy vystavené objektu COM nemají stejné charakteristiky verze jako jiné spravované typy.</span><span class="sxs-lookup"><span data-stu-id="6edc2-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edc2-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="6edc2-130">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="6edc2-131">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="6edc2-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="6edc2-132">Představení rozhraní třídy</span><span class="sxs-lookup"><span data-stu-id="6edc2-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="6edc2-133">Použití atributů spolupráce</span><span class="sxs-lookup"><span data-stu-id="6edc2-133">Applying Interop Attributes</span></span>](../../../docs/standard/native-interop/apply-interop-attributes.md)
- [<span data-ttu-id="6edc2-134">Balení .NET Framework sestavení pro model COM</span><span class="sxs-lookup"><span data-stu-id="6edc2-134">Packaging a .NET Framework Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
