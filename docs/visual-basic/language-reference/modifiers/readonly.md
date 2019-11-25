---
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 8c7e7e7c1571fd7c595ebfd54fb5767078ef41f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351283"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="540aa-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="540aa-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="540aa-103">Specifies that a variable or property can be read but not written.</span><span class="sxs-lookup"><span data-stu-id="540aa-103">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="540aa-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="540aa-104">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="540aa-105">Rules</span><span class="sxs-lookup"><span data-stu-id="540aa-105">Rules</span></span>

- <span data-ttu-id="540aa-106">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="540aa-106">**Declaration Context.**</span></span> <span data-ttu-id="540aa-107">You can use `ReadOnly` only at module level.</span><span class="sxs-lookup"><span data-stu-id="540aa-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="540aa-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span><span class="sxs-lookup"><span data-stu-id="540aa-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="540aa-109">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="540aa-109">**Combined Modifiers.**</span></span> <span data-ttu-id="540aa-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="540aa-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="540aa-111">**Assigning a Value.**</span><span class="sxs-lookup"><span data-stu-id="540aa-111">**Assigning a Value.**</span></span> <span data-ttu-id="540aa-112">Code consuming a `ReadOnly` property cannot set its value.</span><span class="sxs-lookup"><span data-stu-id="540aa-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="540aa-113">But code that has access to the underlying storage can assign or change the value at any time.</span><span class="sxs-lookup"><span data-stu-id="540aa-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="540aa-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span><span class="sxs-lookup"><span data-stu-id="540aa-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="540aa-115">When to Use a ReadOnly Variable</span><span class="sxs-lookup"><span data-stu-id="540aa-115">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="540aa-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span><span class="sxs-lookup"><span data-stu-id="540aa-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="540aa-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span><span class="sxs-lookup"><span data-stu-id="540aa-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="540aa-118">You might not even know the value at compile time.</span><span class="sxs-lookup"><span data-stu-id="540aa-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="540aa-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span><span class="sxs-lookup"><span data-stu-id="540aa-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="540aa-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="540aa-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="540aa-121">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="540aa-121">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="540aa-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span><span class="sxs-lookup"><span data-stu-id="540aa-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="540aa-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span><span class="sxs-lookup"><span data-stu-id="540aa-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="540aa-124">However, you can change the values of one or more of the array members.</span><span class="sxs-lookup"><span data-stu-id="540aa-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="540aa-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span><span class="sxs-lookup"><span data-stu-id="540aa-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="540aa-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span><span class="sxs-lookup"><span data-stu-id="540aa-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="540aa-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="540aa-127">Example</span></span>

<span data-ttu-id="540aa-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span><span class="sxs-lookup"><span data-stu-id="540aa-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="540aa-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span><span class="sxs-lookup"><span data-stu-id="540aa-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="540aa-130">However, the property is `Public`, and any code that can access the class can read the property.</span><span class="sxs-lookup"><span data-stu-id="540aa-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="540aa-131">The `ReadOnly` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="540aa-131">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="540aa-132">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="540aa-132">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="540aa-133">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="540aa-133">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="540aa-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="540aa-134">See also</span></span>

- [<span data-ttu-id="540aa-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="540aa-135">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="540aa-136">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="540aa-136">Keywords</span></span>](../keywords/index.md)
