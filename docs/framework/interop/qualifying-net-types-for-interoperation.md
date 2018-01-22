---
title: "Kvalifikace typů .NET pro spolupráci"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a05330a6834b4775e62b7b55aee03526b2a9bbda
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="f4874-102">Kvalifikace typů .NET pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="f4874-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="f4874-103">Pokud máte v úmyslu vystavit typy v sestavení aplikace modelu COM, zvažte požadavky na zprostředkovatel komunikace s objekty COM v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="f4874-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="f4874-104">Spravované typy (třída, rozhraní, struktura a výčet) se hladce integrují s typy modelu COM, když budete dodržovat následující pokyny:</span><span class="sxs-lookup"><span data-stu-id="f4874-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
-   <span data-ttu-id="f4874-105">Třídy musí implementovat rozhraní explicitně.</span><span class="sxs-lookup"><span data-stu-id="f4874-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="f4874-106">I když se zprostředkovatel komunikace s objekty COM poskytuje mechanismus pro automatické generování rozhraní obsahující všechny členy třídy a členy základní třídy, je mnohem lepší zajistit explicitní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f4874-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="f4874-107">Automaticky generovaného rozhraní nazývá rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="f4874-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="f4874-108">Pokyny najdete v části [představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="f4874-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="f4874-109">Visual Basic, C# a C++ slouží k začlenit definice rozhraní v kódu, místo nutnosti použít definice jazyka IDL (Interface) nebo jeho ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="f4874-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="f4874-110">Syntaxe podrobnosti najdete v dokumentaci jazyk.</span><span class="sxs-lookup"><span data-stu-id="f4874-110">For syntax details, see your language documentation.</span></span>  
  
-   <span data-ttu-id="f4874-111">Spravované typy musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="f4874-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="f4874-112">Pouze veřejné typy v sestavení jsou zaregistrované a exportují do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="f4874-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="f4874-113">V důsledku toho jsou pouze veřejné typy viditelné modelu COM.</span><span class="sxs-lookup"><span data-stu-id="f4874-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="f4874-114">Spravované typy zveřejněte funkce do jiných spravovaného kódu, která nemusí být vystavena modelu COM.</span><span class="sxs-lookup"><span data-stu-id="f4874-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="f4874-115">Parametrizované konstruktory, statické metody a konstantní pole nejsou pro instanci zveřejněné klientům COM.</span><span class="sxs-lookup"><span data-stu-id="f4874-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="f4874-116">Navíc jako modul runtime zařazuje dat a deaktivovat typu, data mohou kopírovat nebo transformovat.</span><span class="sxs-lookup"><span data-stu-id="f4874-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
-   <span data-ttu-id="f4874-117">Metody, vlastnosti, pole a události musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="f4874-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="f4874-118">Členové veřejné typy musí být také veřejné, pokud mají být viditelné modelu COM.</span><span class="sxs-lookup"><span data-stu-id="f4874-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="f4874-119">Můžete omezit viditelnost sestavení, typu veřejný nebo veřejné členy veřejného typu použitím <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f4874-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="f4874-120">Ve výchozím nastavení jsou zobrazené všechny veřejné typy a členy.</span><span class="sxs-lookup"><span data-stu-id="f4874-120">By default, all public types and members are visible.</span></span>  
  
-   <span data-ttu-id="f4874-121">Typy musí mít veřejný výchozí konstruktor chcete aktivovat. z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="f4874-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="f4874-122">Spravované, veřejné typy jsou viditelné pro COM.</span><span class="sxs-lookup"><span data-stu-id="f4874-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="f4874-123">Bez výchozí veřejný konstruktor (konstruktor bez argumentů), ale klienti COM nelze vytvořit typ.</span><span class="sxs-lookup"><span data-stu-id="f4874-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="f4874-124">Klienti COM můžete dál používat typ, pokud je aktivovaná jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="f4874-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
-   <span data-ttu-id="f4874-125">Typy nemohou být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="f4874-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="f4874-126">Klienti COM ani klientů .NET můžete vytvořit abstraktní typy.</span><span class="sxs-lookup"><span data-stu-id="f4874-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="f4874-127">Při exportu do modelu COM, se sloučí hierarchie dědičnosti spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="f4874-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="f4874-128">Správa verzí se také liší mezi spravovanými a nespravovanými prostředí.</span><span class="sxs-lookup"><span data-stu-id="f4874-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="f4874-129">Typy vystaven objektům modelu COM nemají stejné vlastnosti Správa verzí jako jiné spravované typy.</span><span class="sxs-lookup"><span data-stu-id="f4874-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4874-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4874-130">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>  
 [<span data-ttu-id="f4874-131">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="f4874-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="f4874-132">Představení rozhraní – třída</span><span class="sxs-lookup"><span data-stu-id="f4874-132">Introducing the Class Interface</span></span>](http://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [<span data-ttu-id="f4874-133">Použití atributů spolupráce</span><span class="sxs-lookup"><span data-stu-id="f4874-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)  
 [<span data-ttu-id="f4874-134">Zabalení sestavení pro model COM</span><span class="sxs-lookup"><span data-stu-id="f4874-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
