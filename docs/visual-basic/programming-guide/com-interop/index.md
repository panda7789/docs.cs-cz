---
title: Zprostředkovatel komunikace s objekty COM (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: b6da65a0c94875f73c8e1094448d76a72823404d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405947"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="c13ae-102">Zprostředkovatel komunikace s objekty COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c13ae-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="c13ae-103">Modelu COM (Component Object) umožňuje vystavit funkčnost pro jiné komponenty a k hostování aplikací.</span><span class="sxs-lookup"><span data-stu-id="c13ae-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="c13ae-104">Většina dnešních softwaru zahrnuje objekty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c13ae-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="c13ae-105">Přestože sestavení rozhraní .NET jsou nejlepší volbou pro nové aplikace, může čas od času musíte použít objekty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c13ae-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="c13ae-106">Tato část popisuje některé problémy spojené s vytváření a používání objektů COM pomocí jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c13ae-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c13ae-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c13ae-107">In This Section</span></span>  
 [<span data-ttu-id="c13ae-108">Představení zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="c13ae-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="c13ae-109">Poskytuje přehled o interoperabilita modelů COM.</span><span class="sxs-lookup"><span data-stu-id="c13ae-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="c13ae-110">Postupy: odkaz na objekty COM z jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c13ae-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="c13ae-111">Popisuje, jak přidat odkazy na objekty modelu COM, které mají knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="c13ae-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="c13ae-112">Postupy: Práce s ovládacími prvky ActiveX</span><span class="sxs-lookup"><span data-stu-id="c13ae-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="c13ae-113">Ukazuje, jak používat existující ovládací prvky ActiveX pro přidání funkcí do panelu nástrojů sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c13ae-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="c13ae-114">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="c13ae-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="c13ae-115">Vás provede procesem volání rozhraní API, které jsou součástí operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c13ae-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="c13ae-116">Postupy: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="c13ae-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="c13ae-117">Ukazuje, jak definovat a volat `MessageBox` funkce v User32.dll.</span><span class="sxs-lookup"><span data-stu-id="c13ae-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="c13ae-118">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="c13ae-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="c13ae-119">Ukazuje, jak volat funkci Windows, která má parametr typu bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="c13ae-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="c13ae-120">Návod: Vytváření objektů COM pomocí jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c13ae-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="c13ae-121">Vás provede procesem vytváření objektů modelu COM a nemusíte šablony třídy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c13ae-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="c13ae-122">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="c13ae-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="c13ae-123">Popisuje některé z problémů, se můžete setkat při použití modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c13ae-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="c13ae-124">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c13ae-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="c13ae-125">Poskytuje přehled o tom, jak používat objekty COM a rozhraní .NET Framework ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c13ae-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="c13ae-126">Návod: Implementace dědičnosti pomocí objektů COM</span><span class="sxs-lookup"><span data-stu-id="c13ae-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="c13ae-127">Popisuje použití existujících objektů modelu COM jako základ pro nové objekty.</span><span class="sxs-lookup"><span data-stu-id="c13ae-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c13ae-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c13ae-128">Related Sections</span></span>  
 [<span data-ttu-id="c13ae-129">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="c13ae-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="c13ae-130">Popisuje interoperability poskytované modulem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="c13ae-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="c13ae-131">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c13ae-131">Exposing COM Components to the .NET Framework</span></span>](https://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="c13ae-132">Popisuje postup volání typy modelu COM pomocí zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="c13ae-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="c13ae-133">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="c13ae-133">Exposing .NET Framework Components to COM</span></span>](https://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="c13ae-134">Popisuje Příprava a použití spravovaných typů z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c13ae-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="c13ae-135">Použití atributů spolupráce</span><span class="sxs-lookup"><span data-stu-id="c13ae-135">Applying Interop Attributes</span></span>](../../../framework/interop/applying-interop-attributes.md)  
 <span data-ttu-id="c13ae-136">Popisuje atributy, které můžete použít při práci s nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="c13ae-136">Covers attributes you can use when working with unmanaged code.</span></span>
