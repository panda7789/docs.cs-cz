---
title: Objekty a třídy
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: d45aca8b137f56cf058b63b9286504259c0005eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346702"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="efa5c-102">Objects and classes in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efa5c-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="efa5c-103">An *object* is a combination of code and data that can be treated as a unit.</span><span class="sxs-lookup"><span data-stu-id="efa5c-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="efa5c-104">An object can be a piece of an application, like a control or a form.</span><span class="sxs-lookup"><span data-stu-id="efa5c-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="efa5c-105">An entire application can also be an object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-105">An entire application can also be an object.</span></span>

<span data-ttu-id="efa5c-106">When you create an application in Visual Basic, you constantly work with objects.</span><span class="sxs-lookup"><span data-stu-id="efa5c-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="efa5c-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span><span class="sxs-lookup"><span data-stu-id="efa5c-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="efa5c-108">You can also use objects from other applications within your Visual Basic application.</span><span class="sxs-lookup"><span data-stu-id="efa5c-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="efa5c-109">You can even create your own objects and define additional properties and methods for them.</span><span class="sxs-lookup"><span data-stu-id="efa5c-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="efa5c-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span><span class="sxs-lookup"><span data-stu-id="efa5c-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="efa5c-111">This topic discusses objects in detail.</span><span class="sxs-lookup"><span data-stu-id="efa5c-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="efa5c-112">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="efa5c-112">Objects and classes</span></span>

<span data-ttu-id="efa5c-113">Each object in Visual Basic is defined by a *class*.</span><span class="sxs-lookup"><span data-stu-id="efa5c-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="efa5c-114">A class describes the variables, properties, procedures, and events of an object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="efa5c-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="efa5c-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span><span class="sxs-lookup"><span data-stu-id="efa5c-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="efa5c-117">The cookie cutter is the class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-117">The cookie cutter is the class.</span></span> <span data-ttu-id="efa5c-118">It defines the characteristics of each cookie, for example size and shape.</span><span class="sxs-lookup"><span data-stu-id="efa5c-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="efa5c-119">The class is used to create objects.</span><span class="sxs-lookup"><span data-stu-id="efa5c-119">The class is used to create objects.</span></span> <span data-ttu-id="efa5c-120">The objects are the cookies.</span><span class="sxs-lookup"><span data-stu-id="efa5c-120">The objects are the cookies.</span></span>

<span data-ttu-id="efa5c-121">You must create an object before you can access its members.</span><span class="sxs-lookup"><span data-stu-id="efa5c-121">You must create an object before you can access its members.</span></span>

### <a name="to-create-an-object-from-a-class"></a><span data-ttu-id="efa5c-122">To create an object from a class</span><span class="sxs-lookup"><span data-stu-id="efa5c-122">To create an object from a class</span></span>

1. <span data-ttu-id="efa5c-123">Determine from which class you want to create an object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-123">Determine from which class you want to create an object.</span></span>

2. <span data-ttu-id="efa5c-124">Write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span><span class="sxs-lookup"><span data-stu-id="efa5c-124">Write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="efa5c-125">The variable should be of the type of the desired class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-125">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As customer
   ```

3. <span data-ttu-id="efa5c-126">Add the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-126">Add the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New customer
   ```

4. <span data-ttu-id="efa5c-127">You can now access the members of the class through the object variable.</span><span class="sxs-lookup"><span data-stu-id="efa5c-127">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="efa5c-128">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span><span class="sxs-lookup"><span data-stu-id="efa5c-128">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="efa5c-129">This is called *early binding*.</span><span class="sxs-lookup"><span data-stu-id="efa5c-129">This is called *early binding*.</span></span> <span data-ttu-id="efa5c-130">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="efa5c-130">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="efa5c-131">However, late binding can make performance slower and limit access to the run-time object's members.</span><span class="sxs-lookup"><span data-stu-id="efa5c-131">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="efa5c-132">For more information, see [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="efa5c-132">For more information, see [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="efa5c-133">Multiple instances</span><span class="sxs-lookup"><span data-stu-id="efa5c-133">Multiple instances</span></span>

<span data-ttu-id="efa5c-134">Objects newly created from a class are often identical to each other.</span><span class="sxs-lookup"><span data-stu-id="efa5c-134">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="efa5c-135">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span><span class="sxs-lookup"><span data-stu-id="efa5c-135">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="efa5c-136">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-136">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="efa5c-137">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-137">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="efa5c-138">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span><span class="sxs-lookup"><span data-stu-id="efa5c-138">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="efa5c-139">Object members</span><span class="sxs-lookup"><span data-stu-id="efa5c-139">Object members</span></span>

<span data-ttu-id="efa5c-140">An object is an element of an application, representing an *instance* of a class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-140">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="efa5c-141">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span><span class="sxs-lookup"><span data-stu-id="efa5c-141">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="efa5c-142">Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="efa5c-142">Member Access</span></span>

<span data-ttu-id="efa5c-143">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span><span class="sxs-lookup"><span data-stu-id="efa5c-143">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="efa5c-144">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-144">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="efa5c-145">IntelliSense listing of members</span><span class="sxs-lookup"><span data-stu-id="efa5c-145">IntelliSense listing of members</span></span>

<span data-ttu-id="efa5c-146">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span><span class="sxs-lookup"><span data-stu-id="efa5c-146">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="efa5c-147">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span><span class="sxs-lookup"><span data-stu-id="efa5c-147">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="efa5c-148">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span><span class="sxs-lookup"><span data-stu-id="efa5c-148">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="efa5c-149">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="efa5c-149">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="efa5c-150">Fields and properties</span><span class="sxs-lookup"><span data-stu-id="efa5c-150">Fields and properties</span></span>

<span data-ttu-id="efa5c-151">*Fields* and *properties* represent information stored in an object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-151">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="efa5c-152">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span><span class="sxs-lookup"><span data-stu-id="efa5c-152">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="efa5c-153">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-153">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="efa5c-154">Note that a field is also called a *member variable*.</span><span class="sxs-lookup"><span data-stu-id="efa5c-154">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="efa5c-155">Use property procedures when:</span><span class="sxs-lookup"><span data-stu-id="efa5c-155">Use property procedures when:</span></span>

- <span data-ttu-id="efa5c-156">You need to control when and how a value is set or retrieved.</span><span class="sxs-lookup"><span data-stu-id="efa5c-156">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="efa5c-157">The property has a well-defined set of values that need to be validated.</span><span class="sxs-lookup"><span data-stu-id="efa5c-157">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="efa5c-158">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span><span class="sxs-lookup"><span data-stu-id="efa5c-158">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="efa5c-159">Setting the property causes changes to other internal variables or to the values of other properties.</span><span class="sxs-lookup"><span data-stu-id="efa5c-159">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="efa5c-160">A set of steps must be performed before the property can be set or retrieved.</span><span class="sxs-lookup"><span data-stu-id="efa5c-160">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="efa5c-161">Use fields when:</span><span class="sxs-lookup"><span data-stu-id="efa5c-161">Use fields when:</span></span>

- <span data-ttu-id="efa5c-162">The value is of a self-validating type.</span><span class="sxs-lookup"><span data-stu-id="efa5c-162">The value is of a self-validating type.</span></span> <span data-ttu-id="efa5c-163">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span><span class="sxs-lookup"><span data-stu-id="efa5c-163">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="efa5c-164">Any value in the range supported by the data type is valid.</span><span class="sxs-lookup"><span data-stu-id="efa5c-164">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="efa5c-165">This is true of many properties of type `Single` or `Double`.</span><span class="sxs-lookup"><span data-stu-id="efa5c-165">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="efa5c-166">The property is a `String` data type, and there is no constraint on the size or value of the string.</span><span class="sxs-lookup"><span data-stu-id="efa5c-166">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="efa5c-167">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="efa5c-167">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

### <a name="methods"></a><span data-ttu-id="efa5c-168">Metody</span><span class="sxs-lookup"><span data-stu-id="efa5c-168">Methods</span></span>

<span data-ttu-id="efa5c-169">A *method* is an action that an object can perform.</span><span class="sxs-lookup"><span data-stu-id="efa5c-169">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="efa5c-170">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span><span class="sxs-lookup"><span data-stu-id="efa5c-170">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="efa5c-171">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-171">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="efa5c-172">Note that a method is simply a *procedure* that is exposed by an object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-172">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="efa5c-173">For more information, see [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="efa5c-173">For more information, see [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="efa5c-174">Události</span><span class="sxs-lookup"><span data-stu-id="efa5c-174">Events</span></span>

<span data-ttu-id="efa5c-175">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span><span class="sxs-lookup"><span data-stu-id="efa5c-175">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="efa5c-176">Events can occur as a result of a user action or program code, or they can be caused by the system.</span><span class="sxs-lookup"><span data-stu-id="efa5c-176">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="efa5c-177">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span><span class="sxs-lookup"><span data-stu-id="efa5c-177">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="efa5c-178">You can also develop your own custom events to be raised by your objects and handled by other objects.</span><span class="sxs-lookup"><span data-stu-id="efa5c-178">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="efa5c-179">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="efa5c-179">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="efa5c-180">Instance members and shared members</span><span class="sxs-lookup"><span data-stu-id="efa5c-180">Instance members and shared members</span></span>

<span data-ttu-id="efa5c-181">When you create an object from a class, the result is an instance of that class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-181">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="efa5c-182">Members that are not declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span><span class="sxs-lookup"><span data-stu-id="efa5c-182">Members that are not declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="efa5c-183">An instance member in one instance is independent of the same member in another instance of the same class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-183">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="efa5c-184">An instance member variable, for example, can have different values in different instances.</span><span class="sxs-lookup"><span data-stu-id="efa5c-184">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="efa5c-185">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span><span class="sxs-lookup"><span data-stu-id="efa5c-185">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="efa5c-186">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span><span class="sxs-lookup"><span data-stu-id="efa5c-186">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="efa5c-187">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-187">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-nonshared-members"></a><span data-ttu-id="efa5c-188">Accessing nonshared members</span><span class="sxs-lookup"><span data-stu-id="efa5c-188">Accessing nonshared members</span></span>

##### <a name="to-access-a-nonshared-member-of-an-object"></a><span data-ttu-id="efa5c-189">To access a nonshared member of an object</span><span class="sxs-lookup"><span data-stu-id="efa5c-189">To access a nonshared member of an object</span></span>

1. <span data-ttu-id="efa5c-190">Make sure the object has been created from its class and assigned to an object variable.</span><span class="sxs-lookup"><span data-stu-id="efa5c-190">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="efa5c-191">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span><span class="sxs-lookup"><span data-stu-id="efa5c-191">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="efa5c-192">Accessing shared members</span><span class="sxs-lookup"><span data-stu-id="efa5c-192">Accessing shared members</span></span>

##### <a name="to-access-a-shared-member-of-an-object"></a><span data-ttu-id="efa5c-193">To access a shared member of an object</span><span class="sxs-lookup"><span data-stu-id="efa5c-193">To access a shared member of an object</span></span>

- <span data-ttu-id="efa5c-194">Follow the class name with the *member-access operator* (`.`) and then the member name.</span><span class="sxs-lookup"><span data-stu-id="efa5c-194">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="efa5c-195">You should always access a `Shared` member of the object directly through the class name.</span><span class="sxs-lookup"><span data-stu-id="efa5c-195">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="efa5c-196">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span><span class="sxs-lookup"><span data-stu-id="efa5c-196">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="efa5c-197">Differences between classes and modules</span><span class="sxs-lookup"><span data-stu-id="efa5c-197">Differences between classes and modules</span></span>

<span data-ttu-id="efa5c-198">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span><span class="sxs-lookup"><span data-stu-id="efa5c-198">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="efa5c-199">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span><span class="sxs-lookup"><span data-stu-id="efa5c-199">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="efa5c-200">In contrast, object data exists separately for each instantiated object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-200">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="efa5c-201">Another difference is that unlike standard modules, classes can implement interfaces.</span><span class="sxs-lookup"><span data-stu-id="efa5c-201">Another difference is that unlike standard modules, classes can implement interfaces.</span></span>

> [!NOTE]
> <span data-ttu-id="efa5c-202">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-202">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="efa5c-203">The member is accessed directly by using the class name, the same way module members are accessed.</span><span class="sxs-lookup"><span data-stu-id="efa5c-203">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="efa5c-204">Classes and modules also use different scopes for their members.</span><span class="sxs-lookup"><span data-stu-id="efa5c-204">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="efa5c-205">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-205">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="efa5c-206">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span><span class="sxs-lookup"><span data-stu-id="efa5c-206">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="efa5c-207">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span><span class="sxs-lookup"><span data-stu-id="efa5c-207">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="efa5c-208">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span><span class="sxs-lookup"><span data-stu-id="efa5c-208">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="efa5c-209">Reusing classes and objects</span><span class="sxs-lookup"><span data-stu-id="efa5c-209">Reusing classes and objects</span></span>

<span data-ttu-id="efa5c-210">Objects let you declare variables and procedures once and then reuse them whenever needed.</span><span class="sxs-lookup"><span data-stu-id="efa5c-210">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="efa5c-211">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span><span class="sxs-lookup"><span data-stu-id="efa5c-211">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="efa5c-212">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span><span class="sxs-lookup"><span data-stu-id="efa5c-212">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="efa5c-213">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span><span class="sxs-lookup"><span data-stu-id="efa5c-213">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="efa5c-214">The .NET Framework provides many examples of components that are available for use.</span><span class="sxs-lookup"><span data-stu-id="efa5c-214">The .NET Framework provides many examples of components that are available for use.</span></span> <span data-ttu-id="efa5c-215">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="efa5c-215">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="efa5c-216"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span><span class="sxs-lookup"><span data-stu-id="efa5c-216"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

<span data-ttu-id="efa5c-217">In the preceding example, the first [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span><span class="sxs-lookup"><span data-stu-id="efa5c-217">In the preceding example, the first [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="efa5c-218">Relationships among objects</span><span class="sxs-lookup"><span data-stu-id="efa5c-218">Relationships among objects</span></span>

<span data-ttu-id="efa5c-219">Objects can be related to each other in several ways.</span><span class="sxs-lookup"><span data-stu-id="efa5c-219">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="efa5c-220">The principal kinds of relationship are *hierarchical* and *containment*.</span><span class="sxs-lookup"><span data-stu-id="efa5c-220">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="efa5c-221">Hierarchical relationship</span><span class="sxs-lookup"><span data-stu-id="efa5c-221">Hierarchical relationship</span></span>

<span data-ttu-id="efa5c-222">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span><span class="sxs-lookup"><span data-stu-id="efa5c-222">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="efa5c-223">Class hierarchies are useful when describing items that are a subtype of a more general class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-223">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="efa5c-224">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span><span class="sxs-lookup"><span data-stu-id="efa5c-224">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a><span data-ttu-id="efa5c-225">To define a class is derived from an already existing class</span><span class="sxs-lookup"><span data-stu-id="efa5c-225">To define a class is derived from an already existing class</span></span>

1. <span data-ttu-id="efa5c-226">Use a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span><span class="sxs-lookup"><span data-stu-id="efa5c-226">Use a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class reversibleButton
   ```

   <span data-ttu-id="efa5c-227">Be sure an `End Class` statement follows the last line of code in your class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-227">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="efa5c-228">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span><span class="sxs-lookup"><span data-stu-id="efa5c-228">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="efa5c-229">Follow the `Class` statement immediately with an [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="efa5c-229">Follow the `Class` statement immediately with an [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="efa5c-230">Specify the class from which your new class derives.</span><span class="sxs-lookup"><span data-stu-id="efa5c-230">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="efa5c-231">Your new class inherits all the members defined by the base class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-231">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="efa5c-232">Add the code for the additional members your derived class exposes.</span><span class="sxs-lookup"><span data-stu-id="efa5c-232">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="efa5c-233">For example, you might add a `reverseColors` method, and your derived class might look as follows:</span><span class="sxs-lookup"><span data-stu-id="efa5c-233">For example, you might add a `reverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="efa5c-234">If you create an object from the `reversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `reverseColors` method and any other new members you define on `reversibleButton`.</span><span class="sxs-lookup"><span data-stu-id="efa5c-234">If you create an object from the `reversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `reverseColors` method and any other new members you define on `reversibleButton`.</span></span>

<span data-ttu-id="efa5c-235">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span><span class="sxs-lookup"><span data-stu-id="efa5c-235">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="efa5c-236">For more information, see [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="efa5c-236">For more information, see [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

### <a name="compiling-the-code"></a><span data-ttu-id="efa5c-237">Compiling the code</span><span class="sxs-lookup"><span data-stu-id="efa5c-237">Compiling the code</span></span>

<span data-ttu-id="efa5c-238">Be sure the compiler can access the class from which you intend to derive your new class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-238">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="efa5c-239">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="efa5c-239">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="efa5c-240">If the class is in a different project, you might need to add a reference to that project.</span><span class="sxs-lookup"><span data-stu-id="efa5c-240">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="efa5c-241">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="efa5c-241">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="efa5c-242">Containment relationship</span><span class="sxs-lookup"><span data-stu-id="efa5c-242">Containment relationship</span></span>

<span data-ttu-id="efa5c-243">Another way that objects can be related is a *containment relationship*.</span><span class="sxs-lookup"><span data-stu-id="efa5c-243">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="efa5c-244">Container objects logically encapsulate other objects.</span><span class="sxs-lookup"><span data-stu-id="efa5c-244">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="efa5c-245">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span><span class="sxs-lookup"><span data-stu-id="efa5c-245">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="efa5c-246">Note that the container object does not physically contain any other object.</span><span class="sxs-lookup"><span data-stu-id="efa5c-246">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="efa5c-247">Kolekce</span><span class="sxs-lookup"><span data-stu-id="efa5c-247">Collections</span></span>

<span data-ttu-id="efa5c-248">One particular type of object containment is represented by *collections*.</span><span class="sxs-lookup"><span data-stu-id="efa5c-248">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="efa5c-249">Collections are groups of similar objects that can be enumerated.</span><span class="sxs-lookup"><span data-stu-id="efa5c-249">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="efa5c-250">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span><span class="sxs-lookup"><span data-stu-id="efa5c-250">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="efa5c-251">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span><span class="sxs-lookup"><span data-stu-id="efa5c-251">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="efa5c-252">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span><span class="sxs-lookup"><span data-stu-id="efa5c-252">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="efa5c-253">Because of their ease of use, collections are often used to store forms and controls.</span><span class="sxs-lookup"><span data-stu-id="efa5c-253">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="efa5c-254">Související témata</span><span class="sxs-lookup"><span data-stu-id="efa5c-254">Related topics</span></span>

<span data-ttu-id="efa5c-255">[Walkthrough: Defining Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="efa5c-255">[Walkthrough: Defining Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="efa5c-256">Provides a step-by-step description of how to create a class.</span><span class="sxs-lookup"><span data-stu-id="efa5c-256">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="efa5c-257">[Overloaded Properties and Methods](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="efa5c-257">[Overloaded Properties and Methods](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="efa5c-258">Vlastnosti a metody přetečení</span><span class="sxs-lookup"><span data-stu-id="efa5c-258">Overloaded Properties and Methods</span></span>

<span data-ttu-id="efa5c-259">[Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="efa5c-259">[Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span></span>\
<span data-ttu-id="efa5c-260">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span><span class="sxs-lookup"><span data-stu-id="efa5c-260">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="efa5c-261">[Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="efa5c-261">[Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="efa5c-262">Discusses creating and disposing of class instances.</span><span class="sxs-lookup"><span data-stu-id="efa5c-262">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="efa5c-263">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="efa5c-263">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span></span>\
<span data-ttu-id="efa5c-264">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span><span class="sxs-lookup"><span data-stu-id="efa5c-264">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="efa5c-265">[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="efa5c-265">[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="efa5c-266">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span><span class="sxs-lookup"><span data-stu-id="efa5c-266">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="efa5c-267">[How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="efa5c-267">[How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="efa5c-268">Explains how to infer property names and types in anonymous type declarations.</span><span class="sxs-lookup"><span data-stu-id="efa5c-268">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="efa5c-269">Provides examples of successful and unsuccessful inference.</span><span class="sxs-lookup"><span data-stu-id="efa5c-269">Provides examples of successful and unsuccessful inference.</span></span>
