---
title: 'Postupy: Přístup ke členům v objektu'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: d44b538e8413eb1412e937375e9bca77600a29b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348671"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="825c3-102">Postupy: Přístup ke členům v objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="825c3-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="825c3-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span><span class="sxs-lookup"><span data-stu-id="825c3-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="825c3-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span><span class="sxs-lookup"><span data-stu-id="825c3-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="825c3-105">Accessing Members</span><span class="sxs-lookup"><span data-stu-id="825c3-105">Accessing Members</span></span>

<span data-ttu-id="825c3-106">You access an object's members through the variable that refers to it.</span><span class="sxs-lookup"><span data-stu-id="825c3-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="825c3-107">To access members of an object</span><span class="sxs-lookup"><span data-stu-id="825c3-107">To access members of an object</span></span>

- <span data-ttu-id="825c3-108">Use the member-access operator (`.`) between the object variable name and the member name.</span><span class="sxs-lookup"><span data-stu-id="825c3-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="825c3-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span><span class="sxs-lookup"><span data-stu-id="825c3-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="825c3-110">Accessing Members of an Object of Known Type</span><span class="sxs-lookup"><span data-stu-id="825c3-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="825c3-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span><span class="sxs-lookup"><span data-stu-id="825c3-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="825c3-112">To access members of an object for which you know the type at compile time</span><span class="sxs-lookup"><span data-stu-id="825c3-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="825c3-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span><span class="sxs-lookup"><span data-stu-id="825c3-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="825c3-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="825c3-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="825c3-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="825c3-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="825c3-116">Use the member-access operator (`.`) between the object variable name and the member name.</span><span class="sxs-lookup"><span data-stu-id="825c3-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="825c3-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span><span class="sxs-lookup"><span data-stu-id="825c3-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="825c3-118">Accessing Members of an Object of Unknown Type</span><span class="sxs-lookup"><span data-stu-id="825c3-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="825c3-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span><span class="sxs-lookup"><span data-stu-id="825c3-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="825c3-120">To access members of an object for which you do not know the type at compile time</span><span class="sxs-lookup"><span data-stu-id="825c3-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="825c3-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="825c3-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="825c3-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="825c3-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="825c3-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span><span class="sxs-lookup"><span data-stu-id="825c3-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="825c3-124">Use the member-access operator (`.`) between the object variable name and the member name.</span><span class="sxs-lookup"><span data-stu-id="825c3-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="825c3-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="825c3-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="825c3-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span><span class="sxs-lookup"><span data-stu-id="825c3-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="825c3-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span><span class="sxs-lookup"><span data-stu-id="825c3-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="825c3-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="825c3-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="825c3-129">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="825c3-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="825c3-130">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="825c3-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="825c3-131">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="825c3-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="825c3-132">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="825c3-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
