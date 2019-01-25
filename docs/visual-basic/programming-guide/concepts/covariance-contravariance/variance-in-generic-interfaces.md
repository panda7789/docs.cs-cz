---
title: Odchylky obecných rozhraní (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: d39f1b125875f9a9f41ccb6b25a3a88fe577adba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618630"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="8bd7f-102">Odchylky obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="8bd7f-103">Rozhraní .NET framework 4 zavedena podpora odchylku pro existující několik obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="8bd7f-104">Podpora Variance umožňuje implicitní převod z třídy, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="8bd7f-105">Následující rozhraní jsou nyní variant:</span><span class="sxs-lookup"><span data-stu-id="8bd7f-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="8bd7f-106"><xref:System.Collections.Generic.IEnumerable%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="8bd7f-107"><xref:System.Collections.Generic.IEnumerator%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="8bd7f-108"><xref:System.Linq.IQueryable%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="8bd7f-109"><xref:System.Linq.IGrouping%602> (`TKey` a `TElement` jsou kovariantní.)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="8bd7f-110"><xref:System.Collections.Generic.IComparer%601> (T je kontravariantní.)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="8bd7f-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T je kontravariantní.)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="8bd7f-112"><xref:System.IComparable%601> (T je kontravariantní.)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="8bd7f-113">Kovariance povoluje metoda může mít více odvozený návratový typ, než je definován parametr obecného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="8bd7f-114">K ilustraci této funkce kovariance, vezměte v úvahu těmito obecnými rozhraními: `IEnumerable(Of Object)` a `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="8bd7f-115">`IEnumerable(Of String)` Rozhraní nedědí `IEnumerable(Of Object)` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="8bd7f-116">Ale `String` typ dědit `Object` typ a v některých případech můžete chtít přiřadit objekty z těchto rozhraní k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="8bd7f-117">To je ukázáno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-117">This is shown in the following code example.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="8bd7f-118">V dřívějších verzích rozhraní .NET Framework, tento kód způsobí chybu kompilace v jazyce Visual Basic s `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="8bd7f-119">Nyní můžete použít, ale `strings` místo `objects`, jak je znázorněno v předchozím příkladu, protože <xref:System.Collections.Generic.IEnumerable%601> rozhraní je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="8bd7f-120">Kontravariance umožní metoda může mít typy argumentů, které jsou méně odvozený než je určeno obecný parametr rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="8bd7f-121">Pro ilustraci kontravariance se předpokládá, že jste vytvořili `BaseComparer` třídy k porovnání instance `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="8bd7f-122">`BaseComparer` Implementuje třída `IEqualityComparer(Of BaseClass)` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="8bd7f-123">Protože <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní je kontravariantní, můžete použít `BaseComparer` k porovnání instance tříd, které dědí `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="8bd7f-124">To je ukázáno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="8bd7f-125">Další příklady najdete v tématu [použití odchylky v rozhraní pro obecné kolekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="8bd7f-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="8bd7f-126">Odchylky obecných rozhraní je podporována pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="8bd7f-127">Typy hodnot nepodporují variance.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-127">Value types do not support variance.</span></span> <span data-ttu-id="8bd7f-128">Například `IEnumerable(Of Integer)` nejde implicitně převést na `IEnumerable(Of Object)`, protože celá čísla jsou reprezentovány hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 <span data-ttu-id="8bd7f-129">Taky je dobré si uvědomit, že jsou stále invariantní třídy, které implementují rozhraní variant.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="8bd7f-130">Například i když <xref:System.Collections.Generic.List%601> implementuje rozhraní kovariantní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List(Of Object)` k `List(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="8bd7f-131">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8bd7f-131">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bd7f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bd7f-132">See also</span></span>
- [<span data-ttu-id="8bd7f-133">Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="8bd7f-134">Vytváření variantních obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [<span data-ttu-id="8bd7f-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bd7f-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="8bd7f-136">Odchylky v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd7f-136">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
