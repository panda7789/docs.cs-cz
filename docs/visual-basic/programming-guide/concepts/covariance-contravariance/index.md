---
title: Kovariance a kontravariance
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: a75970d98890cb1fb363d4672bd90d376bccf89c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352150"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="9673f-102">Covariance and Contravariance (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9673f-102">Covariance and Contravariance (Visual Basic)</span></span>

<span data-ttu-id="9673f-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span><span class="sxs-lookup"><span data-stu-id="9673f-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="9673f-104">Covariance preserves assignment compatibility and contravariance reverses it.</span><span class="sxs-lookup"><span data-stu-id="9673f-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>

<span data-ttu-id="9673f-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span><span class="sxs-lookup"><span data-stu-id="9673f-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>

```vb
' Assignment compatibility.
Dim str As String = "test"
' An object of a more derived type is assigned to an object of a less derived type.
Dim obj As Object = str

' Covariance.
Dim strings As IEnumerable(Of String) = New List(Of String)()
' An object that is instantiated with a more derived type argument
' is assigned to an object instantiated with a less derived type argument.
' Assignment compatibility is preserved.
Dim objects As IEnumerable(Of Object) = strings

' Contravariance.
' Assume that there is the following method in the class:
' Shared Sub SetObject(ByVal o As Object)
' End Sub
Dim actObject As Action(Of Object) = AddressOf SetObject

' An object that is instantiated with a less derived type argument
' is assigned to an object instantiated with a more derived type argument.
' Assignment compatibility is reversed.
Dim actString As Action(Of String) = actObject
```

<span data-ttu-id="9673f-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span><span class="sxs-lookup"><span data-stu-id="9673f-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="9673f-107">But this operation is not type safe, as shown in the following code example.</span><span class="sxs-lookup"><span data-stu-id="9673f-107">But this operation is not type safe, as shown in the following code example.</span></span>

```vb
Dim array() As Object = New String(10) {}
' The following statement produces a run-time exception.
' array(0) = 10
```

<span data-ttu-id="9673f-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span><span class="sxs-lookup"><span data-stu-id="9673f-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="9673f-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span><span class="sxs-lookup"><span data-stu-id="9673f-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="9673f-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9673f-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>

<span data-ttu-id="9673f-111">The following code example shows covariance and contravariance support for method groups.</span><span class="sxs-lookup"><span data-stu-id="9673f-111">The following code example shows covariance and contravariance support for method groups.</span></span>

```vb
Shared Function GetObject() As Object
    Return Nothing
End Function

Shared Sub SetObject(ByVal obj As Object)
End Sub

Shared Function GetString() As String
    Return ""
End Function

Shared Sub SetString(ByVal str As String)

End Sub

Shared Sub Test()
    ' Covariance. A delegate specifies a return type as object,
    ' but you can assign a method that returns a string.
    Dim del As Func(Of Object) = AddressOf GetString

    ' Contravariance. A delegate specifies a parameter type as string,
    ' but you can assign a method that takes an object.
    Dim del2 As Action(Of String) = AddressOf SetObject
End Sub
```

<span data-ttu-id="9673f-112">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span><span class="sxs-lookup"><span data-stu-id="9673f-112">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="9673f-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9673f-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>

<span data-ttu-id="9673f-114">The following code example shows implicit reference conversion for generic interfaces.</span><span class="sxs-lookup"><span data-stu-id="9673f-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="9673f-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span><span class="sxs-lookup"><span data-stu-id="9673f-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="9673f-116">Visual Basic enables you to create your own variant interfaces and delegates.</span><span class="sxs-lookup"><span data-stu-id="9673f-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="9673f-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9673f-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="9673f-118">Související témata</span><span class="sxs-lookup"><span data-stu-id="9673f-118">Related Topics</span></span>

|<span data-ttu-id="9673f-119">Název</span><span class="sxs-lookup"><span data-stu-id="9673f-119">Title</span></span>|<span data-ttu-id="9673f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="9673f-120">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="9673f-121">Variance in Generic Interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9673f-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="9673f-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9673f-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
|[<span data-ttu-id="9673f-123">Creating Variant Generic Interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9673f-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="9673f-124">Shows how to create custom variant interfaces.</span><span class="sxs-lookup"><span data-stu-id="9673f-124">Shows how to create custom variant interfaces.</span></span>|
|[<span data-ttu-id="9673f-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9673f-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="9673f-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span><span class="sxs-lookup"><span data-stu-id="9673f-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|
|[<span data-ttu-id="9673f-127">Variance in Delegates (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9673f-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="9673f-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9673f-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|
|[<span data-ttu-id="9673f-129">Using Variance in Delegates (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9673f-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="9673f-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span><span class="sxs-lookup"><span data-stu-id="9673f-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|
|[<span data-ttu-id="9673f-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9673f-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="9673f-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span><span class="sxs-lookup"><span data-stu-id="9673f-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
