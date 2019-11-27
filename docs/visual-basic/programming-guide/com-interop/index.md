---
title: Zprostředkovatel komunikace s objekty COM
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: dcfdb5f3661292dda2e084eca22afab9bbec15d3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348006"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="b3ab9-102">Zprostředkovatel komunikace s objekty COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3ab9-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="b3ab9-103">Component Object Model (COM) umožňuje objektu vystavit svou funkčnost jiným komponentám a hostovat aplikace.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="b3ab9-104">Většina dnešního softwaru zahrnuje objekty COM.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="b3ab9-105">I když jsou sestavení .NET nejlepší volbou pro nové aplikace, může být někdy nutné použít objekty COM.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="b3ab9-106">Tato část popisuje některé problémy spojené s vytvářením a používáním objektů COM pomocí Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3ab9-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b3ab9-107">In This Section</span></span>  
 [<span data-ttu-id="b3ab9-108">Představení zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="b3ab9-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="b3ab9-109">Poskytuje přehled interoperability modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="b3ab9-110">Postupy: odkazování objektů COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3ab9-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="b3ab9-111">Popisuje, jak přidat odkazy na objekty modelu COM, které mají knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="b3ab9-112">Postupy: Práce s ovládacími prvky ActiveX</span><span class="sxs-lookup"><span data-stu-id="b3ab9-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="b3ab9-113">Ukazuje, jak použít existující ovládací prvky ActiveX k přidání funkcí do sady nástrojů sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="b3ab9-114">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="b3ab9-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="b3ab9-115">Provede vás procesem volání rozhraní API, která jsou součástí operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="b3ab9-116">Postupy: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="b3ab9-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="b3ab9-117">Ukazuje, jak definovat a volat funkci `MessageBox` v souboru User32. dll.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="b3ab9-118">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="b3ab9-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="b3ab9-119">Ukazuje, jak zavolat funkci systému Windows, která má parametr typu bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="b3ab9-120">Návod: vytváření objektů COM pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3ab9-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="b3ab9-121">Provede kroky procesu vytváření objektů COM pomocí šablony třídy modelu COM a bez ní.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="b3ab9-122">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="b3ab9-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="b3ab9-123">Popisuje některé problémy, se kterými se můžete setkat při používání modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="b3ab9-124">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b3ab9-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="b3ab9-125">Poskytuje přehled o použití objektů COM a .NET Framework objektů ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="b3ab9-126">Návod: Implementace dědičnosti pomocí objektů COM</span><span class="sxs-lookup"><span data-stu-id="b3ab9-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="b3ab9-127">Popisuje použití existujících objektů COM jako základu pro nové objekty.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b3ab9-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b3ab9-128">Related Sections</span></span>  
 [<span data-ttu-id="b3ab9-129">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="b3ab9-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="b3ab9-130">Popisuje služby vzájemné funkční spolupráce poskytované modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b3ab9-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="b3ab9-131">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b3ab9-131">Exposing COM Components to the .NET Framework</span></span>](../../../framework/interop/exposing-com-components.md)  
 <span data-ttu-id="b3ab9-132">Popisuje proces volání typů COM pomocí zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="b3ab9-133">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="b3ab9-133">Exposing .NET Framework Components to COM</span></span>](../../../framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="b3ab9-134">Popisuje přípravu a použití spravovaných typů z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="b3ab9-135">Použití atributů spolupráce</span><span class="sxs-lookup"><span data-stu-id="b3ab9-135">Applying Interop Attributes</span></span>](../../../standard/native-interop/apply-interop-attributes.md)  
 <span data-ttu-id="b3ab9-136">Zahrnuje atributy, které lze použít při práci s nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="b3ab9-136">Covers attributes you can use when working with unmanaged code.</span></span>
