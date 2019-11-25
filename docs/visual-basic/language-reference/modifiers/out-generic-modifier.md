---
title: Out (generický modifikátor)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 0460015b44971fa638dba47183690ffcc89ca55f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351425"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="d9df6-102">Out (generický modifikátor) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9df6-102">Out (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="d9df6-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span><span class="sxs-lookup"><span data-stu-id="d9df6-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9df6-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9df6-104">Remarks</span></span>

<span data-ttu-id="d9df6-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span><span class="sxs-lookup"><span data-stu-id="d9df6-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="d9df6-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span><span class="sxs-lookup"><span data-stu-id="d9df6-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="d9df6-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9df6-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="d9df6-108">Rules</span><span class="sxs-lookup"><span data-stu-id="d9df6-108">Rules</span></span>

<span data-ttu-id="d9df6-109">You can use the `Out` keyword in generic interfaces and delegates.</span><span class="sxs-lookup"><span data-stu-id="d9df6-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="d9df6-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span><span class="sxs-lookup"><span data-stu-id="d9df6-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="d9df6-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span><span class="sxs-lookup"><span data-stu-id="d9df6-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d9df6-112">There is one exception to this rule.</span><span class="sxs-lookup"><span data-stu-id="d9df6-112">There is one exception to this rule.</span></span> <span data-ttu-id="d9df6-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span><span class="sxs-lookup"><span data-stu-id="d9df6-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="d9df6-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d9df6-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="d9df6-115">The type parameter is not used as a generic constraint for the interface methods.</span><span class="sxs-lookup"><span data-stu-id="d9df6-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>

<span data-ttu-id="d9df6-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span><span class="sxs-lookup"><span data-stu-id="d9df6-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

<span data-ttu-id="d9df6-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span><span class="sxs-lookup"><span data-stu-id="d9df6-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="d9df6-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span><span class="sxs-lookup"><span data-stu-id="d9df6-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="d9df6-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span><span class="sxs-lookup"><span data-stu-id="d9df6-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="d9df6-120">Behavior</span><span class="sxs-lookup"><span data-stu-id="d9df6-120">Behavior</span></span>

<span data-ttu-id="d9df6-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span><span class="sxs-lookup"><span data-stu-id="d9df6-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="d9df6-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span><span class="sxs-lookup"><span data-stu-id="d9df6-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="d9df6-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span><span class="sxs-lookup"><span data-stu-id="d9df6-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="d9df6-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9df6-124">Example</span></span>

<span data-ttu-id="d9df6-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span><span class="sxs-lookup"><span data-stu-id="d9df6-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="d9df6-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span><span class="sxs-lookup"><span data-stu-id="d9df6-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="d9df6-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9df6-127">Example</span></span>

<span data-ttu-id="d9df6-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span><span class="sxs-lookup"><span data-stu-id="d9df6-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="d9df6-129">It also shows how you can use implicit conversion for delegate types.</span><span class="sxs-lookup"><span data-stu-id="d9df6-129">It also shows how you can use implicit conversion for delegate types.</span></span>

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="d9df6-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9df6-130">See also</span></span>

- [<span data-ttu-id="d9df6-131">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9df6-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="d9df6-132">In</span><span class="sxs-lookup"><span data-stu-id="d9df6-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
