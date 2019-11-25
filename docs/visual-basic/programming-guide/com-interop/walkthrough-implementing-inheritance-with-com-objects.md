---
title: 'Návod: Implementace dědičnosti s objekty modelu COM'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 209e1005b9f944bf4883e8406031fb17d4d60df1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347984"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="6035c-102">Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6035c-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>

<span data-ttu-id="6035c-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6035c-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="6035c-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span><span class="sxs-lookup"><span data-stu-id="6035c-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="6035c-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span><span class="sxs-lookup"><span data-stu-id="6035c-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>

<span data-ttu-id="6035c-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span><span class="sxs-lookup"><span data-stu-id="6035c-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="6035c-107">To build the COM object that is used in this walkthrough</span><span class="sxs-lookup"><span data-stu-id="6035c-107">To build the COM object that is used in this walkthrough</span></span>

1. <span data-ttu-id="6035c-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span><span class="sxs-lookup"><span data-stu-id="6035c-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="6035c-109">A project named `Project1` is created.</span><span class="sxs-lookup"><span data-stu-id="6035c-109">A project named `Project1` is created.</span></span> <span data-ttu-id="6035c-110">It has a class named `Class1`.</span><span class="sxs-lookup"><span data-stu-id="6035c-110">It has a class named `Class1`.</span></span>

2. <span data-ttu-id="6035c-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span><span class="sxs-lookup"><span data-stu-id="6035c-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="6035c-112">The **Project Properties** dialog box is displayed.</span><span class="sxs-lookup"><span data-stu-id="6035c-112">The **Project Properties** dialog box is displayed.</span></span>

3. <span data-ttu-id="6035c-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span><span class="sxs-lookup"><span data-stu-id="6035c-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>

4. <span data-ttu-id="6035c-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="6035c-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="6035c-115">The **Properties** window for the class is displayed.</span><span class="sxs-lookup"><span data-stu-id="6035c-115">The **Properties** window for the class is displayed.</span></span>

5. <span data-ttu-id="6035c-116">Change the `Name` property to `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="6035c-116">Change the `Name` property to `MathFunctions`.</span></span>

6. <span data-ttu-id="6035c-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span><span class="sxs-lookup"><span data-stu-id="6035c-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="6035c-118">The **Code Editor** is displayed.</span><span class="sxs-lookup"><span data-stu-id="6035c-118">The **Code Editor** is displayed.</span></span>

7. <span data-ttu-id="6035c-119">Add a local variable to hold the property value:</span><span class="sxs-lookup"><span data-stu-id="6035c-119">Add a local variable to hold the property value:</span></span>

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. <span data-ttu-id="6035c-120">Add Property `Let` and Property `Get` property procedures:</span><span class="sxs-lookup"><span data-stu-id="6035c-120">Add Property `Let` and Property `Get` property procedures:</span></span>

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. <span data-ttu-id="6035c-121">Add a function:</span><span class="sxs-lookup"><span data-stu-id="6035c-121">Add a function:</span></span>

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. <span data-ttu-id="6035c-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span><span class="sxs-lookup"><span data-stu-id="6035c-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6035c-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span><span class="sxs-lookup"><span data-stu-id="6035c-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="6035c-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="6035c-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>

## <a name="interop-assemblies"></a><span data-ttu-id="6035c-125">Interop Assemblies</span><span class="sxs-lookup"><span data-stu-id="6035c-125">Interop Assemblies</span></span>

<span data-ttu-id="6035c-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span><span class="sxs-lookup"><span data-stu-id="6035c-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="6035c-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span><span class="sxs-lookup"><span data-stu-id="6035c-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="6035c-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span><span class="sxs-lookup"><span data-stu-id="6035c-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="6035c-129">To use a COM object with Visual Basic 2005 and later versions</span><span class="sxs-lookup"><span data-stu-id="6035c-129">To use a COM object with Visual Basic 2005 and later versions</span></span>

1. <span data-ttu-id="6035c-130">Open a new Visual Basic Windows Application project.</span><span class="sxs-lookup"><span data-stu-id="6035c-130">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="6035c-131">On the **Project** menu, click **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="6035c-131">On the **Project** menu, click **Add Reference**.</span></span>

     <span data-ttu-id="6035c-132">The **Add Reference** dialog box is displayed.</span><span class="sxs-lookup"><span data-stu-id="6035c-132">The **Add Reference** dialog box is displayed.</span></span>

3. <span data-ttu-id="6035c-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span><span class="sxs-lookup"><span data-stu-id="6035c-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>

4. <span data-ttu-id="6035c-134">On the **Project** menu, click **Add New Item**.</span><span class="sxs-lookup"><span data-stu-id="6035c-134">On the **Project** menu, click **Add New Item**.</span></span>

     <span data-ttu-id="6035c-135">The **Add New Item** dialog box is displayed.</span><span class="sxs-lookup"><span data-stu-id="6035c-135">The **Add New Item** dialog box is displayed.</span></span>

5. <span data-ttu-id="6035c-136">In the **Templates** pane, click **Class**.</span><span class="sxs-lookup"><span data-stu-id="6035c-136">In the **Templates** pane, click **Class**.</span></span>

     <span data-ttu-id="6035c-137">The default file name, `Class1.vb`, appears in the **Name** field.</span><span class="sxs-lookup"><span data-stu-id="6035c-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="6035c-138">Change this field to MathClass.vb and click **Add**.</span><span class="sxs-lookup"><span data-stu-id="6035c-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="6035c-139">This creates a class named `MathClass`, and displays its code.</span><span class="sxs-lookup"><span data-stu-id="6035c-139">This creates a class named `MathClass`, and displays its code.</span></span>

6. <span data-ttu-id="6035c-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span><span class="sxs-lookup"><span data-stu-id="6035c-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. <span data-ttu-id="6035c-141">Overload the public method of the base class by adding the following code to `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="6035c-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. <span data-ttu-id="6035c-142">Extend the inherited class by adding the following code to `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="6035c-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

<span data-ttu-id="6035c-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span><span class="sxs-lookup"><span data-stu-id="6035c-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>

### <a name="to-test-the-inherited-class"></a><span data-ttu-id="6035c-144">To test the inherited class</span><span class="sxs-lookup"><span data-stu-id="6035c-144">To test the inherited class</span></span>

1. <span data-ttu-id="6035c-145">Add a button to your startup form, and then double-click it to view its code.</span><span class="sxs-lookup"><span data-stu-id="6035c-145">Add a button to your startup form, and then double-click it to view its code.</span></span>

2. <span data-ttu-id="6035c-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span><span class="sxs-lookup"><span data-stu-id="6035c-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. <span data-ttu-id="6035c-147">Run the project by pressing F5.</span><span class="sxs-lookup"><span data-stu-id="6035c-147">Run the project by pressing F5.</span></span>

<span data-ttu-id="6035c-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span><span class="sxs-lookup"><span data-stu-id="6035c-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="6035c-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="6035c-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="6035c-150">The third call calls the `SubtractNumbers` method, which extends the class.</span><span class="sxs-lookup"><span data-stu-id="6035c-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="6035c-151">The property in the base class is set, and the value is displayed.</span><span class="sxs-lookup"><span data-stu-id="6035c-151">The property in the base class is set, and the value is displayed.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6035c-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6035c-152">Next Steps</span></span>

<span data-ttu-id="6035c-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span><span class="sxs-lookup"><span data-stu-id="6035c-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="6035c-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6035c-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="6035c-155">The new function accepts 32-bit integers, and overloads the base class function.</span><span class="sxs-lookup"><span data-stu-id="6035c-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>

<span data-ttu-id="6035c-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span><span class="sxs-lookup"><span data-stu-id="6035c-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="6035c-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6035c-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>

<span data-ttu-id="6035c-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span><span class="sxs-lookup"><span data-stu-id="6035c-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="6035c-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span><span class="sxs-lookup"><span data-stu-id="6035c-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>

- <span data-ttu-id="6035c-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span><span class="sxs-lookup"><span data-stu-id="6035c-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>

- <span data-ttu-id="6035c-161">Properties that use `ByRef` parameters cannot be overridden.</span><span class="sxs-lookup"><span data-stu-id="6035c-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>

## <a name="see-also"></a><span data-ttu-id="6035c-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6035c-162">See also</span></span>

- [<span data-ttu-id="6035c-163">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6035c-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="6035c-164">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="6035c-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="6035c-165">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="6035c-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
