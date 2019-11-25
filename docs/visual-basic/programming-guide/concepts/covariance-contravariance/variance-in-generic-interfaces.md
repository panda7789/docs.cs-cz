---
title: Odchylky obecných rozhraní
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 1f6913b322e2d3d9ec2234e556e63d67324277e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348980"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="23395-102">Variance in Generic Interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23395-102">Variance in Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="23395-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span><span class="sxs-lookup"><span data-stu-id="23395-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="23395-104">Variance support enables implicit conversion of classes that implement these interfaces.</span><span class="sxs-lookup"><span data-stu-id="23395-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="23395-105">The following interfaces are now variant:</span><span class="sxs-lookup"><span data-stu-id="23395-105">The following interfaces are now variant:</span></span>

- <span data-ttu-id="23395-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span><span class="sxs-lookup"><span data-stu-id="23395-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="23395-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span><span class="sxs-lookup"><span data-stu-id="23395-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="23395-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span><span class="sxs-lookup"><span data-stu-id="23395-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="23395-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span><span class="sxs-lookup"><span data-stu-id="23395-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="23395-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span><span class="sxs-lookup"><span data-stu-id="23395-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="23395-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span><span class="sxs-lookup"><span data-stu-id="23395-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="23395-112"><xref:System.IComparable%601> (T is contravariant)</span><span class="sxs-lookup"><span data-stu-id="23395-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="23395-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span><span class="sxs-lookup"><span data-stu-id="23395-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="23395-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="23395-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="23395-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span><span class="sxs-lookup"><span data-stu-id="23395-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="23395-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span><span class="sxs-lookup"><span data-stu-id="23395-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="23395-117">This is shown in the following code example.</span><span class="sxs-lookup"><span data-stu-id="23395-117">This is shown in the following code example.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="23395-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="23395-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="23395-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span><span class="sxs-lookup"><span data-stu-id="23395-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="23395-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span><span class="sxs-lookup"><span data-stu-id="23395-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="23395-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span><span class="sxs-lookup"><span data-stu-id="23395-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="23395-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span><span class="sxs-lookup"><span data-stu-id="23395-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="23395-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span><span class="sxs-lookup"><span data-stu-id="23395-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="23395-124">This is shown in the following code example.</span><span class="sxs-lookup"><span data-stu-id="23395-124">This is shown in the following code example.</span></span>

```vb
' Simple hierarchy of classes.
Class BaseClass
End Class

Class DerivedClass
    Inherits BaseClass
End Class

' Comparer class.
Class BaseComparer
    Implements IEqualityComparer(Of BaseClass)

    Public Function Equals1(ByVal x As BaseClass,
                            ByVal y As BaseClass) As Boolean _
                            Implements IEqualityComparer(Of BaseClass).Equals
        Return (x.Equals(y))
    End Function

    Public Function GetHashCode1(ByVal obj As BaseClass) As Integer _
        Implements IEqualityComparer(Of BaseClass).GetHashCode
        Return obj.GetHashCode
    End Function
End Class
Sub Test()
    Dim baseComparer As IEqualityComparer(Of BaseClass) = New BaseComparer
    ' Implicit conversion of IEqualityComparer(Of BaseClass) to
    ' IEqualityComparer(Of DerivedClass).
    Dim childComparer As IEqualityComparer(Of DerivedClass) = baseComparer
End Sub
```

<span data-ttu-id="23395-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="23395-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="23395-126">Variance in generic interfaces is supported for reference types only.</span><span class="sxs-lookup"><span data-stu-id="23395-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="23395-127">Value types do not support variance.</span><span class="sxs-lookup"><span data-stu-id="23395-127">Value types do not support variance.</span></span> <span data-ttu-id="23395-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span><span class="sxs-lookup"><span data-stu-id="23395-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

<span data-ttu-id="23395-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span><span class="sxs-lookup"><span data-stu-id="23395-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="23395-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="23395-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="23395-131">This is illustrated in the following code example.</span><span class="sxs-lookup"><span data-stu-id="23395-131">This is illustrated in the following code example.</span></span>

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a><span data-ttu-id="23395-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23395-132">See also</span></span>

- [<span data-ttu-id="23395-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23395-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="23395-134">Creating Variant Generic Interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23395-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [<span data-ttu-id="23395-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="23395-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="23395-136">Variance in Delegates (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23395-136">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
