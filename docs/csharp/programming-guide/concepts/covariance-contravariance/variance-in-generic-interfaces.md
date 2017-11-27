---
title: "Odchylky obecných rozhraní (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc3fe009e89d5d8f6619b406c8c08f47620a881d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="0e67e-102">Odchylky obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="0e67e-102">Variance in Generic Interfaces (C#)</span></span>
<span data-ttu-id="0e67e-103">Rozhraní .NET framework 4 zavedly odchylku podporu pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e67e-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="0e67e-104">Podpora odchylku umožňuje implicitní převod tříd, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e67e-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="0e67e-105">Následující rozhraní jsou nyní variant:</span><span class="sxs-lookup"><span data-stu-id="0e67e-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="0e67e-106"><xref:System.Collections.Generic.IEnumerable%601>(T je kovariant)</span><span class="sxs-lookup"><span data-stu-id="0e67e-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="0e67e-107"><xref:System.Collections.Generic.IEnumerator%601>(T je kovariant)</span><span class="sxs-lookup"><span data-stu-id="0e67e-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="0e67e-108"><xref:System.Linq.IQueryable%601>(T je kovariant)</span><span class="sxs-lookup"><span data-stu-id="0e67e-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="0e67e-109"><xref:System.Linq.IGrouping%602>(`TKey` a `TElement` jsou kovariantní)</span><span class="sxs-lookup"><span data-stu-id="0e67e-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="0e67e-110"><xref:System.Collections.Generic.IComparer%601>(T je kontravariant)</span><span class="sxs-lookup"><span data-stu-id="0e67e-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="0e67e-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T je kontravariant)</span><span class="sxs-lookup"><span data-stu-id="0e67e-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="0e67e-112"><xref:System.IComparable%601>(T je kontravariant)</span><span class="sxs-lookup"><span data-stu-id="0e67e-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="0e67e-113">Kovariance umožňuje metodu tak, aby měl více odvozené návratový typ než definované parametr obecného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e67e-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="0e67e-114">Pro ilustraci funkci kovariance, zvažte tyto obecná rozhraní: `IEnumerable<Object>` a `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="0e67e-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="0e67e-115">`IEnumerable<String>` Rozhraní nedědí `IEnumerable<Object>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e67e-115">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="0e67e-116">Ale `String` typ dědit vlastnosti `Object` typ a v některých případech můžete chtít přiřazovat objekty z těchto rozhraní k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="0e67e-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="0e67e-117">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0e67e-117">This is shown in the following code example.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="0e67e-118">V dřívějších verzích rozhraní .NET Framework, tento kód způsobí chybu kompilace v jazyce C# s `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="0e67e-118">In earlier versions of the .NET Framework, this code causes a compilation error in C# with `Option Strict On`.</span></span> <span data-ttu-id="0e67e-119">Teď můžete použít, ale `strings` místo `objects`, jak ukazuje předchozí příklad, protože <xref:System.Collections.Generic.IEnumerable%601> rozhraní je kovariant.</span><span class="sxs-lookup"><span data-stu-id="0e67e-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="0e67e-120">Kontravariance umožňuje metodu tak, aby měl typy argumentů, které jsou odvozené menší než je určeno obecný parametr rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e67e-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="0e67e-121">Pro ilustraci kontravariance, předpokládá, že jste vytvořili `BaseComparer` třída k porovnání instance `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="0e67e-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="0e67e-122">`BaseComparer` Třída implementuje `IEqualityComparer<BaseClass>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e67e-122">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="0e67e-123">Protože <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní je nyní kontravariant, můžete použít `BaseComparer` k porovnání instance tříd, které dědí `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="0e67e-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="0e67e-124">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0e67e-124">This is shown in the following code example.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
class BaseClass { }  
class DerivedClass : BaseClass { }  
  
// Comparer class.  
class BaseComparer : IEqualityComparer<BaseClass>   
{  
    public int GetHashCode(BaseClass baseInstance)  
    {  
        return baseInstance.GetHashCode();  
    }  
    public bool Equals(BaseClass x, BaseClass y)  
    {  
        return x == y;  
    }  
}  
class Program  
{  
    static void Test()  
    {  
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();  
  
        // Implicit conversion of IEqualityComparer<BaseClass> to   
        // IEqualityComparer<DerivedClass>.  
        IEqualityComparer<DerivedClass> childComparer = baseComparer;  
    }  
}  
```  
  
 <span data-ttu-id="0e67e-125">Další příklady najdete v tématu [použití odchylky v rozhraní pro obecné kolekce (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="0e67e-125">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="0e67e-126">Odchylky obecných rozhraní je podporována pro odkazové typy pouze.</span><span class="sxs-lookup"><span data-stu-id="0e67e-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="0e67e-127">Typy hodnot nepodporují odchylky.</span><span class="sxs-lookup"><span data-stu-id="0e67e-127">Value types do not support variance.</span></span> <span data-ttu-id="0e67e-128">Například `IEnumerable<int>` nelze implicitně převést na `IEnumerable<object>`, protože celých čísel jsou reprezentované pomocí typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0e67e-128">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 <span data-ttu-id="0e67e-129">Je také důležité Pamatujte, že jsou stále invariantní třídy, které implementují rozhraní variant.</span><span class="sxs-lookup"><span data-stu-id="0e67e-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="0e67e-130">Například i když <xref:System.Collections.Generic.List%601> implementuje rozhraní kovariantní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List<Object>` k `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="0e67e-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="0e67e-131">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0e67e-131">This is illustrated in the following code example.</span></span>  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e67e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e67e-132">See Also</span></span>  
 [<span data-ttu-id="0e67e-133">Použití odchylky v rozhraní pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="0e67e-133">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [<span data-ttu-id="0e67e-134">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="0e67e-134">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [<span data-ttu-id="0e67e-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e67e-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
 [<span data-ttu-id="0e67e-136">Odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="0e67e-136">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
