---
title: Object-oriented programming
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 3739919273f4cdd285d519c414c542f1a82a16d2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348160"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="68ebd-102">Object-oriented programming (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68ebd-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="68ebd-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span><span class="sxs-lookup"><span data-stu-id="68ebd-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="68ebd-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span><span class="sxs-lookup"><span data-stu-id="68ebd-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="68ebd-105">*Inheritance* describes the ability to create new classes based on an existing class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="68ebd-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span><span class="sxs-lookup"><span data-stu-id="68ebd-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="68ebd-107">This section describes the following concepts:</span><span class="sxs-lookup"><span data-stu-id="68ebd-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="68ebd-108">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="68ebd-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="68ebd-109">Class members</span><span class="sxs-lookup"><span data-stu-id="68ebd-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="68ebd-110">Properties and fields</span><span class="sxs-lookup"><span data-stu-id="68ebd-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="68ebd-111">Metody</span><span class="sxs-lookup"><span data-stu-id="68ebd-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="68ebd-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="68ebd-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="68ebd-113">Destruktory</span><span class="sxs-lookup"><span data-stu-id="68ebd-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="68ebd-114">Události</span><span class="sxs-lookup"><span data-stu-id="68ebd-114">Events</span></span>](#events)
    - [<span data-ttu-id="68ebd-115">Nested classes</span><span class="sxs-lookup"><span data-stu-id="68ebd-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="68ebd-116">Access modifiers and access levels</span><span class="sxs-lookup"><span data-stu-id="68ebd-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="68ebd-117">Instantiating classes</span><span class="sxs-lookup"><span data-stu-id="68ebd-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="68ebd-118">Shared classes and members</span><span class="sxs-lookup"><span data-stu-id="68ebd-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="68ebd-119">Anonymous types</span><span class="sxs-lookup"><span data-stu-id="68ebd-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="68ebd-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="68ebd-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="68ebd-121">Overriding members</span><span class="sxs-lookup"><span data-stu-id="68ebd-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="68ebd-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="68ebd-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="68ebd-123">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="68ebd-123">Generics</span></span>](#generics)
- [<span data-ttu-id="68ebd-124">Delegáty</span><span class="sxs-lookup"><span data-stu-id="68ebd-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="68ebd-125">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="68ebd-125">Classes and objects</span></span>

<span data-ttu-id="68ebd-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span><span class="sxs-lookup"><span data-stu-id="68ebd-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="68ebd-127">So, the act of creating an object is called *instantiation*.</span><span class="sxs-lookup"><span data-stu-id="68ebd-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="68ebd-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span><span class="sxs-lookup"><span data-stu-id="68ebd-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="68ebd-129">To define a class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="68ebd-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span><span class="sxs-lookup"><span data-stu-id="68ebd-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="68ebd-131">To define a structure:</span><span class="sxs-lookup"><span data-stu-id="68ebd-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="68ebd-132">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="68ebd-132">For more information, see:</span></span>

- [<span data-ttu-id="68ebd-133">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="68ebd-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="68ebd-134">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="68ebd-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="68ebd-135">Class members</span><span class="sxs-lookup"><span data-stu-id="68ebd-135">Class members</span></span>

<span data-ttu-id="68ebd-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span><span class="sxs-lookup"><span data-stu-id="68ebd-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="68ebd-137">Properties and fields</span><span class="sxs-lookup"><span data-stu-id="68ebd-137">Properties and fields</span></span>

<span data-ttu-id="68ebd-138">Fields and properties represent information that an object contains.</span><span class="sxs-lookup"><span data-stu-id="68ebd-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="68ebd-139">Fields are like variables because they can be read or set directly.</span><span class="sxs-lookup"><span data-stu-id="68ebd-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="68ebd-140">To define a field:</span><span class="sxs-lookup"><span data-stu-id="68ebd-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="68ebd-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span><span class="sxs-lookup"><span data-stu-id="68ebd-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="68ebd-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span><span class="sxs-lookup"><span data-stu-id="68ebd-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="68ebd-143">To define an auto-implemented property:</span><span class="sxs-lookup"><span data-stu-id="68ebd-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="68ebd-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span><span class="sxs-lookup"><span data-stu-id="68ebd-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

<span data-ttu-id="68ebd-145">Most properties have methods or procedures to both set and get the property value.</span><span class="sxs-lookup"><span data-stu-id="68ebd-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="68ebd-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span><span class="sxs-lookup"><span data-stu-id="68ebd-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="68ebd-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span><span class="sxs-lookup"><span data-stu-id="68ebd-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="68ebd-148">However, auto-implemented properties cannot be read-only or write-only.</span><span class="sxs-lookup"><span data-stu-id="68ebd-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="68ebd-149">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="68ebd-149">For more information, see:</span></span>

- [<span data-ttu-id="68ebd-150">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="68ebd-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="68ebd-151">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="68ebd-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="68ebd-152">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="68ebd-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="68ebd-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="68ebd-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="68ebd-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="68ebd-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="68ebd-155">Metody</span><span class="sxs-lookup"><span data-stu-id="68ebd-155">Methods</span></span>

 <span data-ttu-id="68ebd-156">A *method* is an action that an object can perform.</span><span class="sxs-lookup"><span data-stu-id="68ebd-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="68ebd-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span><span class="sxs-lookup"><span data-stu-id="68ebd-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="68ebd-158">To define a method of a class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="68ebd-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span><span class="sxs-lookup"><span data-stu-id="68ebd-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="68ebd-160">To overload a method:</span><span class="sxs-lookup"><span data-stu-id="68ebd-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="68ebd-161">In most cases you declare a method within a class definition.</span><span class="sxs-lookup"><span data-stu-id="68ebd-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="68ebd-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="68ebd-163">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="68ebd-163">For more information, see:</span></span>

- [<span data-ttu-id="68ebd-164">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="68ebd-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="68ebd-165">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="68ebd-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="68ebd-166">Overloads</span><span class="sxs-lookup"><span data-stu-id="68ebd-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="68ebd-167">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="68ebd-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="68ebd-168">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="68ebd-168">Constructors</span></span>

<span data-ttu-id="68ebd-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span><span class="sxs-lookup"><span data-stu-id="68ebd-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="68ebd-170">Constructors usually initialize the data members of the new object.</span><span class="sxs-lookup"><span data-stu-id="68ebd-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="68ebd-171">A constructor can run only once when a class is created.</span><span class="sxs-lookup"><span data-stu-id="68ebd-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="68ebd-172">Furthermore, the code in the constructor always runs before any other code in a class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="68ebd-173">However, you can create multiple constructor overloads in the same way as for any other method.</span><span class="sxs-lookup"><span data-stu-id="68ebd-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="68ebd-174">To define a constructor for a class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="68ebd-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="68ebd-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="68ebd-176">Destruktory</span><span class="sxs-lookup"><span data-stu-id="68ebd-176">Destructors</span></span>

<span data-ttu-id="68ebd-177">Destructors are used to destruct instances of classes.</span><span class="sxs-lookup"><span data-stu-id="68ebd-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="68ebd-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span><span class="sxs-lookup"><span data-stu-id="68ebd-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="68ebd-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span><span class="sxs-lookup"><span data-stu-id="68ebd-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="68ebd-180">There can be only one destructor for a class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="68ebd-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="68ebd-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="68ebd-182">Události</span><span class="sxs-lookup"><span data-stu-id="68ebd-182">Events</span></span>

<span data-ttu-id="68ebd-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span><span class="sxs-lookup"><span data-stu-id="68ebd-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="68ebd-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span><span class="sxs-lookup"><span data-stu-id="68ebd-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="68ebd-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="68ebd-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="68ebd-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="68ebd-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="68ebd-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="68ebd-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="68ebd-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span><span class="sxs-lookup"><span data-stu-id="68ebd-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="68ebd-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="68ebd-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="68ebd-190">Nested classes</span><span class="sxs-lookup"><span data-stu-id="68ebd-190">Nested classes</span></span>

<span data-ttu-id="68ebd-191">A class defined within another class is called *nested*.</span><span class="sxs-lookup"><span data-stu-id="68ebd-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="68ebd-192">By default, the nested class is private.</span><span class="sxs-lookup"><span data-stu-id="68ebd-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="68ebd-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="68ebd-194">Access modifiers and access levels</span><span class="sxs-lookup"><span data-stu-id="68ebd-194">Access modifiers and access levels</span></span>

<span data-ttu-id="68ebd-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span><span class="sxs-lookup"><span data-stu-id="68ebd-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="68ebd-196">The following access modifiers are available:</span><span class="sxs-lookup"><span data-stu-id="68ebd-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="68ebd-197">Visual Basic Modifier</span><span class="sxs-lookup"><span data-stu-id="68ebd-197">Visual Basic Modifier</span></span>|<span data-ttu-id="68ebd-198">Definice</span><span class="sxs-lookup"><span data-stu-id="68ebd-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="68ebd-199">Public</span><span class="sxs-lookup"><span data-stu-id="68ebd-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="68ebd-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span><span class="sxs-lookup"><span data-stu-id="68ebd-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="68ebd-201">Private</span><span class="sxs-lookup"><span data-stu-id="68ebd-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="68ebd-202">The type or member can only be accessed by code in the same class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="68ebd-203">Protected</span><span class="sxs-lookup"><span data-stu-id="68ebd-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="68ebd-204">The type or member can only be accessed by code in the same class or in a derived class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="68ebd-205">Friend</span><span class="sxs-lookup"><span data-stu-id="68ebd-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="68ebd-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span><span class="sxs-lookup"><span data-stu-id="68ebd-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="68ebd-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span><span class="sxs-lookup"><span data-stu-id="68ebd-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="68ebd-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="68ebd-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="68ebd-209">Instantiating classes</span><span class="sxs-lookup"><span data-stu-id="68ebd-209">Instantiating classes</span></span>

<span data-ttu-id="68ebd-210">To create an object, you need to instantiate a class, or create a class instance.</span><span class="sxs-lookup"><span data-stu-id="68ebd-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="68ebd-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span><span class="sxs-lookup"><span data-stu-id="68ebd-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="68ebd-212">To assign values to properties during the class instantiation process, use object initializers:</span><span class="sxs-lookup"><span data-stu-id="68ebd-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="68ebd-213">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="68ebd-213">For more information, see:</span></span>

- [<span data-ttu-id="68ebd-214">Operátor New</span><span class="sxs-lookup"><span data-stu-id="68ebd-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="68ebd-215">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="68ebd-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="68ebd-216">Shared classes and members</span><span class="sxs-lookup"><span data-stu-id="68ebd-216">Shared classes and members</span></span>

 <span data-ttu-id="68ebd-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="68ebd-218">To define a shared member:</span><span class="sxs-lookup"><span data-stu-id="68ebd-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="68ebd-219">To access the shared member, use the name of the class without creating an object of this class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="68ebd-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span><span class="sxs-lookup"><span data-stu-id="68ebd-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="68ebd-221">Shared members also cannot access non-shared properties, fields or methods</span><span class="sxs-lookup"><span data-stu-id="68ebd-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="68ebd-222">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="68ebd-222">For more information, see:</span></span>

- [<span data-ttu-id="68ebd-223">Shared</span><span class="sxs-lookup"><span data-stu-id="68ebd-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="68ebd-224">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="68ebd-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="68ebd-225">Anonymous types</span><span class="sxs-lookup"><span data-stu-id="68ebd-225">Anonymous types</span></span>

<span data-ttu-id="68ebd-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span><span class="sxs-lookup"><span data-stu-id="68ebd-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="68ebd-227">Instead, the compiler generates a class for you.</span><span class="sxs-lookup"><span data-stu-id="68ebd-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="68ebd-228">The class has no usable name and contains the properties you specify in declaring the object.</span><span class="sxs-lookup"><span data-stu-id="68ebd-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="68ebd-229">To create an instance of an anonymous type:</span><span class="sxs-lookup"><span data-stu-id="68ebd-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="68ebd-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="68ebd-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="68ebd-231">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="68ebd-231">Inheritance</span></span>

<span data-ttu-id="68ebd-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="68ebd-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span><span class="sxs-lookup"><span data-stu-id="68ebd-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="68ebd-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span><span class="sxs-lookup"><span data-stu-id="68ebd-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="68ebd-235">Visual Basic doesn't support multiple inheritance.</span><span class="sxs-lookup"><span data-stu-id="68ebd-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="68ebd-236">That is, you can specify only one base class for a derived class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="68ebd-237">To inherit from a base class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="68ebd-238">By default all classes can be inherited.</span><span class="sxs-lookup"><span data-stu-id="68ebd-238">By default all classes can be inherited.</span></span> <span data-ttu-id="68ebd-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span><span class="sxs-lookup"><span data-stu-id="68ebd-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="68ebd-240">To specify that a class cannot be used as a base class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="68ebd-241">To specify that a class can be used as a base class only and cannot be instantiated:</span><span class="sxs-lookup"><span data-stu-id="68ebd-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="68ebd-242">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="68ebd-242">For more information, see:</span></span>

- [<span data-ttu-id="68ebd-243">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="68ebd-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="68ebd-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="68ebd-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="68ebd-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="68ebd-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="68ebd-246">Overriding members</span><span class="sxs-lookup"><span data-stu-id="68ebd-246">Overriding members</span></span>

<span data-ttu-id="68ebd-247">By default, a derived class inherits all members from its base class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="68ebd-248">If you want to change the behavior of the inherited member, you need to override it.</span><span class="sxs-lookup"><span data-stu-id="68ebd-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="68ebd-249">That is, you can define a new implementation of the method, property or event in the derived class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="68ebd-250">The following modifiers are used to control how properties and methods are overridden:</span><span class="sxs-lookup"><span data-stu-id="68ebd-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="68ebd-251">Visual Basic Modifier</span><span class="sxs-lookup"><span data-stu-id="68ebd-251">Visual Basic Modifier</span></span>|<span data-ttu-id="68ebd-252">Definice</span><span class="sxs-lookup"><span data-stu-id="68ebd-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="68ebd-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="68ebd-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="68ebd-254">Allows a class member to be overridden in a derived class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="68ebd-255">Overrides</span><span class="sxs-lookup"><span data-stu-id="68ebd-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="68ebd-256">Overrides a virtual (overridable) member defined in the base class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="68ebd-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="68ebd-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="68ebd-258">Prevents a member from being overridden in an inheriting class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="68ebd-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="68ebd-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="68ebd-260">Requires that a class member to be overridden in the derived class.</span><span class="sxs-lookup"><span data-stu-id="68ebd-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="68ebd-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="68ebd-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="68ebd-262">Hides a member inherited from a base class</span><span class="sxs-lookup"><span data-stu-id="68ebd-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="68ebd-263">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="68ebd-263">Interfaces</span></span>

<span data-ttu-id="68ebd-264">Interfaces, like classes, define a set of properties, methods, and events.</span><span class="sxs-lookup"><span data-stu-id="68ebd-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="68ebd-265">But unlike classes, interfaces do not provide implementation.</span><span class="sxs-lookup"><span data-stu-id="68ebd-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="68ebd-266">They are implemented by classes, and defined as separate entities from classes.</span><span class="sxs-lookup"><span data-stu-id="68ebd-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="68ebd-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span><span class="sxs-lookup"><span data-stu-id="68ebd-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="68ebd-268">To define an interface:</span><span class="sxs-lookup"><span data-stu-id="68ebd-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="68ebd-269">To implement an interface in a class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="68ebd-270">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="68ebd-270">For more information, see:</span></span>

- [<span data-ttu-id="68ebd-271">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="68ebd-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="68ebd-272">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="68ebd-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="68ebd-273">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="68ebd-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="68ebd-274">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="68ebd-274">Generics</span></span>

<span data-ttu-id="68ebd-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span><span class="sxs-lookup"><span data-stu-id="68ebd-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="68ebd-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span><span class="sxs-lookup"><span data-stu-id="68ebd-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="68ebd-277">To define a generic class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="68ebd-278">To create an instance of a generic class:</span><span class="sxs-lookup"><span data-stu-id="68ebd-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="68ebd-279">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="68ebd-279">For more information, see:</span></span>

- [<span data-ttu-id="68ebd-280">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="68ebd-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="68ebd-281">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68ebd-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="68ebd-282">Delegáty</span><span class="sxs-lookup"><span data-stu-id="68ebd-282">Delegates</span></span>

 <span data-ttu-id="68ebd-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span><span class="sxs-lookup"><span data-stu-id="68ebd-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="68ebd-284">You can invoke (or call) the method through the delegate.</span><span class="sxs-lookup"><span data-stu-id="68ebd-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="68ebd-285">Delegáty se používají pro předávání metod jako argumentů jiným metodám.</span><span class="sxs-lookup"><span data-stu-id="68ebd-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="68ebd-286">Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="68ebd-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="68ebd-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="68ebd-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="68ebd-288">To create a delegate:</span><span class="sxs-lookup"><span data-stu-id="68ebd-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="68ebd-289">To create a reference to a method that matches the signature specified by the delegate:</span><span class="sxs-lookup"><span data-stu-id="68ebd-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

<span data-ttu-id="68ebd-290">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="68ebd-290">For more information, see:</span></span>

- [<span data-ttu-id="68ebd-291">Delegáty</span><span class="sxs-lookup"><span data-stu-id="68ebd-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="68ebd-292">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="68ebd-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="68ebd-293">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="68ebd-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="68ebd-294">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68ebd-294">See also</span></span>

- [<span data-ttu-id="68ebd-295">Visual Basic Programming Guide</span><span class="sxs-lookup"><span data-stu-id="68ebd-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
