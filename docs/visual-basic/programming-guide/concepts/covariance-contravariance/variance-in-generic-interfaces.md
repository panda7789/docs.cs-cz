---
title: "Odchylky obecných rozhraní (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d05ccdc97efd5dd193bbbe0d15dd227ec71910d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="6ac49-102">Odchylky obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ac49-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="6ac49-103">Rozhraní .NET framework 4 zavedly odchylku podporu pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ac49-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="6ac49-104">Podpora odchylku umožňuje implicitní převod tříd, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ac49-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="6ac49-105">Následující rozhraní jsou nyní variant:</span><span class="sxs-lookup"><span data-stu-id="6ac49-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="6ac49-106"><xref:System.Collections.Generic.IEnumerable%601>(T je kovariant)</span><span class="sxs-lookup"><span data-stu-id="6ac49-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="6ac49-107"><xref:System.Collections.Generic.IEnumerator%601>(T je kovariant)</span><span class="sxs-lookup"><span data-stu-id="6ac49-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="6ac49-108"><xref:System.Linq.IQueryable%601>(T je kovariant)</span><span class="sxs-lookup"><span data-stu-id="6ac49-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="6ac49-109"><xref:System.Linq.IGrouping%602>(`TKey` a `TElement` jsou kovariantní)</span><span class="sxs-lookup"><span data-stu-id="6ac49-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="6ac49-110"><xref:System.Collections.Generic.IComparer%601>(T je kontravariant)</span><span class="sxs-lookup"><span data-stu-id="6ac49-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="6ac49-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T je kontravariant)</span><span class="sxs-lookup"><span data-stu-id="6ac49-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="6ac49-112"><xref:System.IComparable%601>(T je kontravariant)</span><span class="sxs-lookup"><span data-stu-id="6ac49-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="6ac49-113">Kovariance umožňuje metodu tak, aby měl více odvozené návratový typ než definované parametr obecného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ac49-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="6ac49-114">Pro ilustraci funkci kovariance, zvažte tyto obecná rozhraní: `IEnumerable(Of Object)` a `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="6ac49-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="6ac49-115">`IEnumerable(Of String)` Rozhraní nedědí `IEnumerable(Of Object)` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ac49-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="6ac49-116">Ale `String` typ dědit vlastnosti `Object` typ a v některých případech můžete chtít přiřazovat objekty z těchto rozhraní k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="6ac49-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="6ac49-117">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="6ac49-117">This is shown in the following code example.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="6ac49-118">V dřívějších verzích rozhraní .NET Framework, tento kód způsobí chybu kompilace v jazyce Visual Basic s `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="6ac49-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="6ac49-119">Teď můžete použít, ale `strings` místo `objects`, jak ukazuje předchozí příklad, protože <xref:System.Collections.Generic.IEnumerable%601> rozhraní je kovariant.</span><span class="sxs-lookup"><span data-stu-id="6ac49-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="6ac49-120">Kontravariance umožňuje metodu tak, aby měl typy argumentů, které jsou odvozené menší než je určeno obecný parametr rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ac49-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="6ac49-121">Pro ilustraci kontravariance, předpokládá, že jste vytvořili `BaseComparer` třída k porovnání instance `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="6ac49-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="6ac49-122">`BaseComparer` Třída implementuje `IEqualityComparer(Of BaseClass)` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ac49-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="6ac49-123">Protože <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní je nyní kontravariant, můžete použít `BaseComparer` k porovnání instance tříd, které dědí `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="6ac49-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="6ac49-124">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="6ac49-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="6ac49-125">Další příklady najdete v tématu [použití odchylky v rozhraní pro obecné kolekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="6ac49-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="6ac49-126">Odchylky obecných rozhraní je podporována pro odkazové typy pouze.</span><span class="sxs-lookup"><span data-stu-id="6ac49-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="6ac49-127">Typy hodnot nepodporují odchylky.</span><span class="sxs-lookup"><span data-stu-id="6ac49-127">Value types do not support variance.</span></span> <span data-ttu-id="6ac49-128">Například `IEnumerable(Of Integer)` nelze implicitně převést na `IEnumerable(Of Object)`, protože celých čísel jsou reprezentované pomocí typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6ac49-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 <span data-ttu-id="6ac49-129">Je také důležité Pamatujte, že jsou stále invariantní třídy, které implementují rozhraní variant.</span><span class="sxs-lookup"><span data-stu-id="6ac49-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="6ac49-130">Například i když <xref:System.Collections.Generic.List%601> implementuje rozhraní kovariantní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List(Of Object)` k `List(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="6ac49-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="6ac49-131">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="6ac49-131">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ac49-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ac49-132">See Also</span></span>  
 [<span data-ttu-id="6ac49-133">Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ac49-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [<span data-ttu-id="6ac49-134">Vytváření variantních obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ac49-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [<span data-ttu-id="6ac49-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ac49-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
 [<span data-ttu-id="6ac49-136">Odchylky v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ac49-136">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
