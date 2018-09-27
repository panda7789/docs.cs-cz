---
title: Odchylky obecných rozhraní (C#)
ms.date: 07/20/2015
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 11d0c8665412bb513cb68d58203a454b7c97e052
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399778"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="1f639-102">Odchylky obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="1f639-102">Variance in Generic Interfaces (C#)</span></span>
<span data-ttu-id="1f639-103">Rozhraní .NET framework 4 zavedena podpora odchylku pro existující několik obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f639-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="1f639-104">Podpora Variance umožňuje implicitní převod z třídy, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f639-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="1f639-105">Následující rozhraní jsou nyní variant:</span><span class="sxs-lookup"><span data-stu-id="1f639-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="1f639-106"><xref:System.Collections.Generic.IEnumerable%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="1f639-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="1f639-107"><xref:System.Collections.Generic.IEnumerator%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="1f639-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="1f639-108"><xref:System.Linq.IQueryable%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="1f639-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="1f639-109"><xref:System.Linq.IGrouping%602> (`TKey` a `TElement` jsou kovariantní.)</span><span class="sxs-lookup"><span data-stu-id="1f639-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="1f639-110"><xref:System.Collections.Generic.IComparer%601> (T je kontravariantní.)</span><span class="sxs-lookup"><span data-stu-id="1f639-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="1f639-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T je kontravariantní.)</span><span class="sxs-lookup"><span data-stu-id="1f639-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="1f639-112"><xref:System.IComparable%601> (T je kontravariantní.)</span><span class="sxs-lookup"><span data-stu-id="1f639-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="1f639-113">Kovariance povoluje metoda může mít více odvozený návratový typ, než je definován parametr obecného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f639-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="1f639-114">K ilustraci této funkce kovariance, vezměte v úvahu těmito obecnými rozhraními: `IEnumerable<Object>` a `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="1f639-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="1f639-115">`IEnumerable<String>` Rozhraní nedědí `IEnumerable<Object>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f639-115">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="1f639-116">Ale `String` typ dědit `Object` typ a v některých případech můžete chtít přiřadit objekty z těchto rozhraní k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="1f639-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="1f639-117">To je ukázáno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="1f639-117">This is shown in the following code example.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="1f639-118">V dřívějších verzích rozhraní .NET Framework, tento kód způsobí chybu kompilace v jazyce C# s `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="1f639-118">In earlier versions of the .NET Framework, this code causes a compilation error in C# with `Option Strict On`.</span></span> <span data-ttu-id="1f639-119">Nyní můžete použít, ale `strings` místo `objects`, jak je znázorněno v předchozím příkladu, protože <xref:System.Collections.Generic.IEnumerable%601> rozhraní je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="1f639-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="1f639-120">Kontravariance umožní metoda může mít typy argumentů, které jsou méně odvozený než je určeno obecný parametr rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f639-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="1f639-121">Pro ilustraci kontravariance se předpokládá, že jste vytvořili `BaseComparer` třídy k porovnání instance `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="1f639-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="1f639-122">`BaseComparer` Implementuje třída `IEqualityComparer<BaseClass>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f639-122">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="1f639-123">Protože <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní je kontravariantní, můžete použít `BaseComparer` k porovnání instance tříd, které dědí `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="1f639-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="1f639-124">To je ukázáno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="1f639-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="1f639-125">Další příklady najdete v tématu [použití odchylky v rozhraní pro obecné kolekce (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="1f639-125">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="1f639-126">Odchylky obecných rozhraní je podporována pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="1f639-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="1f639-127">Typy hodnot nepodporují variance.</span><span class="sxs-lookup"><span data-stu-id="1f639-127">Value types do not support variance.</span></span> <span data-ttu-id="1f639-128">Například `IEnumerable<int>` nejde implicitně převést na `IEnumerable<object>`, protože celá čísla jsou reprezentovány hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="1f639-128">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 <span data-ttu-id="1f639-129">Taky je dobré si uvědomit, že jsou stále invariantní třídy, které implementují rozhraní variant.</span><span class="sxs-lookup"><span data-stu-id="1f639-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="1f639-130">Například i když <xref:System.Collections.Generic.List%601> implementuje rozhraní kovariantní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List<Object>` k `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="1f639-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="1f639-131">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="1f639-131">This is illustrated in the following code example.</span></span>  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f639-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f639-132">See Also</span></span>

- [<span data-ttu-id="1f639-133">Použití odchylky v rozhraní pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="1f639-133">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
- [<span data-ttu-id="1f639-134">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="1f639-134">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
- [<span data-ttu-id="1f639-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f639-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
- [<span data-ttu-id="1f639-136">Odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="1f639-136">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
