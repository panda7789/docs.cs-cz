---
title: Deklarace proměnné objektu
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: d1964e3768124dde1deeabfada9006ff5a59def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351806"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="858f3-102">Deklarace proměnné objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="858f3-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="858f3-103">You use a normal declaration statement to declare an object variable.</span><span class="sxs-lookup"><span data-stu-id="858f3-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="858f3-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span><span class="sxs-lookup"><span data-stu-id="858f3-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="858f3-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="858f3-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="858f3-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span><span class="sxs-lookup"><span data-stu-id="858f3-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="858f3-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span><span class="sxs-lookup"><span data-stu-id="858f3-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="858f3-108">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="858f3-108">Declaration Syntax</span></span>  
 <span data-ttu-id="858f3-109">Use the following syntax to declare an object variable:</span><span class="sxs-lookup"><span data-stu-id="858f3-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="858f3-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span><span class="sxs-lookup"><span data-stu-id="858f3-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="858f3-111">The following example declarations are valid:</span><span class="sxs-lookup"><span data-stu-id="858f3-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="858f3-112">Late Binding and Early Binding</span><span class="sxs-lookup"><span data-stu-id="858f3-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="858f3-113">Sometimes the specific class is unknown until your code runs.</span><span class="sxs-lookup"><span data-stu-id="858f3-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="858f3-114">In this case, you must declare the object variable with the `Object` data type.</span><span class="sxs-lookup"><span data-stu-id="858f3-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="858f3-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span><span class="sxs-lookup"><span data-stu-id="858f3-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="858f3-116">This is called *late binding*.</span><span class="sxs-lookup"><span data-stu-id="858f3-116">This is called *late binding*.</span></span> <span data-ttu-id="858f3-117">Late binding requires additional execution time.</span><span class="sxs-lookup"><span data-stu-id="858f3-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="858f3-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span><span class="sxs-lookup"><span data-stu-id="858f3-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="858f3-119">This can cause run-time errors if your code attempts to access members of a different class.</span><span class="sxs-lookup"><span data-stu-id="858f3-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="858f3-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span><span class="sxs-lookup"><span data-stu-id="858f3-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="858f3-121">This is called *early binding*.</span><span class="sxs-lookup"><span data-stu-id="858f3-121">This is called *early binding*.</span></span> <span data-ttu-id="858f3-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span><span class="sxs-lookup"><span data-stu-id="858f3-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="858f3-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span><span class="sxs-lookup"><span data-stu-id="858f3-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="858f3-124">Advantages of Early Binding</span><span class="sxs-lookup"><span data-stu-id="858f3-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="858f3-125">Declaring an object variable as a specific class gives you several advantages:</span><span class="sxs-lookup"><span data-stu-id="858f3-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="858f3-126">Automatic type checking</span><span class="sxs-lookup"><span data-stu-id="858f3-126">Automatic type checking</span></span>  
  
- <span data-ttu-id="858f3-127">Guaranteed access to all members of the specific class</span><span class="sxs-lookup"><span data-stu-id="858f3-127">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="858f3-128">Microsoft IntelliSense support in the Code Editor</span><span class="sxs-lookup"><span data-stu-id="858f3-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="858f3-129">Improved readability of your code</span><span class="sxs-lookup"><span data-stu-id="858f3-129">Improved readability of your code</span></span>  
  
- <span data-ttu-id="858f3-130">Fewer errors in your code</span><span class="sxs-lookup"><span data-stu-id="858f3-130">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="858f3-131">Errors caught at compile time rather than run time</span><span class="sxs-lookup"><span data-stu-id="858f3-131">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="858f3-132">Faster code execution</span><span class="sxs-lookup"><span data-stu-id="858f3-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="858f3-133">Access to Object Variable Members</span><span class="sxs-lookup"><span data-stu-id="858f3-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="858f3-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span><span class="sxs-lookup"><span data-stu-id="858f3-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="858f3-135">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="858f3-135">The following example illustrates this.</span></span>  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 <span data-ttu-id="858f3-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span><span class="sxs-lookup"><span data-stu-id="858f3-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="858f3-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span><span class="sxs-lookup"><span data-stu-id="858f3-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="858f3-138">Flexibility of Object Variables</span><span class="sxs-lookup"><span data-stu-id="858f3-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="858f3-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span><span class="sxs-lookup"><span data-stu-id="858f3-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="858f3-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span><span class="sxs-lookup"><span data-stu-id="858f3-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="858f3-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span><span class="sxs-lookup"><span data-stu-id="858f3-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="858f3-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="858f3-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="858f3-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="858f3-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="858f3-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span><span class="sxs-lookup"><span data-stu-id="858f3-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="858f3-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="858f3-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="858f3-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span><span class="sxs-lookup"><span data-stu-id="858f3-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="858f3-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span><span class="sxs-lookup"><span data-stu-id="858f3-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="858f3-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span><span class="sxs-lookup"><span data-stu-id="858f3-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="858f3-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="858f3-149">See also</span></span>

- [<span data-ttu-id="858f3-150">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="858f3-150">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="858f3-151">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="858f3-151">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="858f3-152">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="858f3-152">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="858f3-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="858f3-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="858f3-154">Postupy: Přístup ke členům v objektu</span><span class="sxs-lookup"><span data-stu-id="858f3-154">How to: Access Members of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [<span data-ttu-id="858f3-155">Operátor New</span><span class="sxs-lookup"><span data-stu-id="858f3-155">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="858f3-156">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="858f3-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="858f3-157">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="858f3-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
