---
title: Kvalifikace typů .NET pro spolupráci
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cad67f52a4ca977606d7b5a307868ff129570e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097974"
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="02f98-102">Kvalifikace typů .NET pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="02f98-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="02f98-103">Pokud chcete vystavit typy v sestavení aplikace modelu COM, zvažte požadavky na spolupráci s COM v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="02f98-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="02f98-104">Spravované typy (třída, rozhraní, struktury a výčet) bez problémů integrovat typy modelu COM při dodržovat následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="02f98-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
-   <span data-ttu-id="02f98-105">Třídy musí implementovat rozhraní explicitně.</span><span class="sxs-lookup"><span data-stu-id="02f98-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="02f98-106">Ačkoli komunikace s objekty COM poskytuje mechanismus pro automatické generování rozhraní obsahující všechny členy třídy a členy své základní třídy, je mnohem lepší poskytnout explicitní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="02f98-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="02f98-107">Automaticky generovaného rozhraní je volat rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="02f98-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="02f98-108">Pokyny najdete v části [představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="02f98-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="02f98-109">Můžete použít v jazyce Visual Basic C#a C++ až po začlenění definice rozhraní ve vašem kódu, místo nutnosti použít rozhraní Definition Language (IDL) nebo jeho ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="02f98-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="02f98-110">Podrobnosti o syntaxi naleznete v dokumentaci jazyka.</span><span class="sxs-lookup"><span data-stu-id="02f98-110">For syntax details, see your language documentation.</span></span>  
  
-   <span data-ttu-id="02f98-111">Spravované typy musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="02f98-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="02f98-112">Pouze veřejné typy v sestavení jsou registrovány a exportovat do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="02f98-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="02f98-113">V důsledku toho pouze veřejné typy jsou viditelné v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="02f98-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="02f98-114">Spravované typy zveřejňují funkce pro další spravovaný kód, který nemusí být vystaveny objektům modelu COM.</span><span class="sxs-lookup"><span data-stu-id="02f98-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="02f98-115">Například konstruktor s parametry, statické metody a konstantní pole nejsou zveřejněné klientům modelu COM.</span><span class="sxs-lookup"><span data-stu-id="02f98-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="02f98-116">Dále jak modul runtime zařazuje dat do a z typu, data může kopírovat nebo transformovat.</span><span class="sxs-lookup"><span data-stu-id="02f98-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
-   <span data-ttu-id="02f98-117">Metody, vlastnosti, pole a události musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="02f98-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="02f98-118">Členové veřejné typy musí být také veřejné, pokud mají být viditelné modelu COM.</span><span class="sxs-lookup"><span data-stu-id="02f98-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="02f98-119">Můžete omezit, zda se sestavení, veřejný typ nebo veřejné členy typu public použitím <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="02f98-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="02f98-120">Ve výchozím nastavení jsou viditelné všechny veřejné typy a členy.</span><span class="sxs-lookup"><span data-stu-id="02f98-120">By default, all public types and members are visible.</span></span>  
  
-   <span data-ttu-id="02f98-121">Typy musí mít veřejný výchozí konstruktor, chcete-li aktivovat z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="02f98-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="02f98-122">Spravovaná, veřejné typy jsou viditelné v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="02f98-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="02f98-123">Ale bez veřejného výchozího konstruktoru (konstruktor bez argumentů), nelze vytvořit klientům modelu COM typu.</span><span class="sxs-lookup"><span data-stu-id="02f98-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="02f98-124">Klientům modelu COM můžete stále použít typ, pokud je aktivovaná jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="02f98-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
-   <span data-ttu-id="02f98-125">Typy nemohou být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="02f98-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="02f98-126">Klienti modelu COM ani klientů .NET můžete vytvořit abstraktní typy.</span><span class="sxs-lookup"><span data-stu-id="02f98-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="02f98-127">Při exportu do modelu COM, hierarchie dědičnosti spravovaného typu se sloučí.</span><span class="sxs-lookup"><span data-stu-id="02f98-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="02f98-128">Správa verzí se také liší mezi spravovanými a nespravovanými prostředí.</span><span class="sxs-lookup"><span data-stu-id="02f98-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="02f98-129">Typy vystavit rozhraní COM nemají stejné vlastnosti jako jiné spravované typy správy verzí.</span><span class="sxs-lookup"><span data-stu-id="02f98-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f98-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02f98-130">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="02f98-131">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="02f98-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="02f98-132">Představení rozhraní třídy</span><span class="sxs-lookup"><span data-stu-id="02f98-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="02f98-133">Použití atributů spolupráce</span><span class="sxs-lookup"><span data-stu-id="02f98-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)
- [<span data-ttu-id="02f98-134">Zabalení sestavení pro model COM</span><span class="sxs-lookup"><span data-stu-id="02f98-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
