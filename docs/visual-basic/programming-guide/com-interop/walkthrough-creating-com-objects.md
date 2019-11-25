---
title: 'Walkthrough: Creating COM Objects'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 5d00aff07358a0c40159fde9c12c70e0842d848b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338621"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="c3f3c-102">Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3f3c-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="c3f3c-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="c3f3c-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="c3f3c-105">This enables you to provide new components for earlier application suites that require COM components.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="c3f3c-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="c3f3c-107">The easiest way to expose COM objects is by using the COM class template.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="c3f3c-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3f3c-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="c3f3c-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="c3f3c-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="c3f3c-111">To create a COM object by using the COM class template</span><span class="sxs-lookup"><span data-stu-id="c3f3c-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="c3f3c-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="c3f3c-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="c3f3c-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="c3f3c-115">The new project is displayed.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="c3f3c-116">Select **Add New Item** from the **Project** menu.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="c3f3c-117">The **Add New Item** dialog box is displayed.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="c3f3c-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="c3f3c-119">Visual Basic adds a new class and configures the new project for COM interop.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="c3f3c-120">Add code such as properties, methods, and events to the COM class.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="c3f3c-121">Select **Build ClassLibrary1** from the **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="c3f3c-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="c3f3c-123">Creating COM Objects without the COM Class Template</span><span class="sxs-lookup"><span data-stu-id="c3f3c-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="c3f3c-124">You can also create a COM class manually instead of using the COM class template.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="c3f3c-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="c3f3c-126">To set up your project to generate a COM object</span><span class="sxs-lookup"><span data-stu-id="c3f3c-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="c3f3c-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="c3f3c-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="c3f3c-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="c3f3c-130">The new project is displayed.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="c3f3c-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="c3f3c-132">The **Project Designer** is displayed.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="c3f3c-133">Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="c3f3c-134">Select the **Register for COM Interop** check box.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="c3f3c-135">To set up the code in your class to create a COM object</span><span class="sxs-lookup"><span data-stu-id="c3f3c-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="c3f3c-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="c3f3c-137">Rename the class to `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="c3f3c-138">Add the following constants to `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="c3f3c-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="c3f3c-140">On the **Tools** menu, click **Create Guid**.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="c3f3c-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="c3f3c-142">Click **Exit**.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="c3f3c-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="c3f3c-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="c3f3c-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="c3f3c-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="c3f3c-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span><span class="sxs-lookup"><span data-stu-id="c3f3c-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="c3f3c-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="c3f3c-149">Add a parameterless constructor to the class:</span><span class="sxs-lookup"><span data-stu-id="c3f3c-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="c3f3c-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="c3f3c-151">Select **Build Solution** from the **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="c3f3c-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c3f3c-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="c3f3c-154">Attempts to add references to such COM objects will raise an error.</span><span class="sxs-lookup"><span data-stu-id="c3f3c-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="c3f3c-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="c3f3c-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f3c-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3f3c-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="c3f3c-157">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="c3f3c-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="c3f3c-158">Návod: Implementace dědičnosti pomocí objektů COM</span><span class="sxs-lookup"><span data-stu-id="c3f3c-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="c3f3c-159">Direktiva #Region</span><span class="sxs-lookup"><span data-stu-id="c3f3c-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="c3f3c-160">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c3f3c-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="c3f3c-161">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="c3f3c-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
