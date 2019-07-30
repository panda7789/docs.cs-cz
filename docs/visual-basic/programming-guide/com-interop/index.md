---
title: Zprostředkovatel komunikace s objekty COM (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: 1bcfba25c86c46f986c061241a5d09f9aaa6d248
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627080"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="292ef-102">Zprostředkovatel komunikace s objekty COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="292ef-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="292ef-103">Component Object Model (COM) umožňuje objektu vystavit svou funkčnost jiným komponentám a hostovat aplikace.</span><span class="sxs-lookup"><span data-stu-id="292ef-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="292ef-104">Většina dnešního softwaru zahrnuje objekty COM.</span><span class="sxs-lookup"><span data-stu-id="292ef-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="292ef-105">I když jsou sestavení .NET nejlepší volbou pro nové aplikace, může být někdy nutné použít objekty COM.</span><span class="sxs-lookup"><span data-stu-id="292ef-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="292ef-106">Tato část popisuje některé problémy spojené s vytvářením a používáním objektů COM pomocí Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="292ef-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="292ef-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="292ef-107">In This Section</span></span>  
 [<span data-ttu-id="292ef-108">Představení zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="292ef-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="292ef-109">Poskytuje přehled interoperability modelu COM.</span><span class="sxs-lookup"><span data-stu-id="292ef-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="292ef-110">Postupy: Odkazování na objekty modelu COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="292ef-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="292ef-111">Popisuje, jak přidat odkazy na objekty modelu COM, které mají knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="292ef-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="292ef-112">Postupy: Práce s ovládacími prvky ActiveX</span><span class="sxs-lookup"><span data-stu-id="292ef-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="292ef-113">Ukazuje, jak použít existující ovládací prvky ActiveX k přidání funkcí do sady nástrojů sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="292ef-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="292ef-114">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="292ef-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="292ef-115">Provede vás procesem volání rozhraní API, která jsou součástí operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="292ef-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="292ef-116">Postupy: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="292ef-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="292ef-117">Ukazuje, jak definovat a zavolat `MessageBox` funkci v knihovně user32. dll.</span><span class="sxs-lookup"><span data-stu-id="292ef-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="292ef-118">Postupy: Volání funkce Windows, která přebírá typy bez znaménka</span><span class="sxs-lookup"><span data-stu-id="292ef-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="292ef-119">Ukazuje, jak zavolat funkci systému Windows, která má parametr typu bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="292ef-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="292ef-120">Návod: Vytváření objektů COM pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="292ef-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="292ef-121">Provede kroky procesu vytváření objektů COM pomocí šablony třídy modelu COM a bez ní.</span><span class="sxs-lookup"><span data-stu-id="292ef-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="292ef-122">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="292ef-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="292ef-123">Popisuje některé problémy, se kterými se můžete setkat při používání modelu COM.</span><span class="sxs-lookup"><span data-stu-id="292ef-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="292ef-124">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="292ef-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="292ef-125">Poskytuje přehled o použití objektů COM a .NET Framework objektů ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="292ef-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="292ef-126">Návod: Implementace dědičnosti pomocí objektů COM</span><span class="sxs-lookup"><span data-stu-id="292ef-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="292ef-127">Popisuje použití existujících objektů COM jako základu pro nové objekty.</span><span class="sxs-lookup"><span data-stu-id="292ef-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="292ef-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="292ef-128">Related Sections</span></span>  
 [<span data-ttu-id="292ef-129">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="292ef-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="292ef-130">Popisuje služby vzájemné funkční spolupráce poskytované modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="292ef-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="292ef-131">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="292ef-131">Exposing COM Components to the .NET Framework</span></span>](../../../framework/interop/exposing-com-components.md)  
 <span data-ttu-id="292ef-132">Popisuje proces volání typů COM pomocí zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="292ef-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="292ef-133">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="292ef-133">Exposing .NET Framework Components to COM</span></span>](../../../framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="292ef-134">Popisuje přípravu a použití spravovaných typů z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="292ef-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="292ef-135">Použití atributů spolupráce</span><span class="sxs-lookup"><span data-stu-id="292ef-135">Applying Interop Attributes</span></span>](../../../standard/native-interop/apply-interop-attributes.md)  
 <span data-ttu-id="292ef-136">Zahrnuje atributy, které lze použít při práci s nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="292ef-136">Covers attributes you can use when working with unmanaged code.</span></span>
