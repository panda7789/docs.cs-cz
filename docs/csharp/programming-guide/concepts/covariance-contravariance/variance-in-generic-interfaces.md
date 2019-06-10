---
title: Odchylky obecných rozhraní (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: a2d0bcc049d62978930b4e5cdef7920349e3b894
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66815958"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="cd6f4-102">Odchylky obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="cd6f4-103">Rozhraní .NET framework 4 zavedena podpora odchylku pro existující několik obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="cd6f4-104">Podpora Variance umožňuje implicitní převod z třídy, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> 

<span data-ttu-id="cd6f4-105">Rovnou začít tématem rozhraní .NET Framework 4, jsou následující rozhraní variant:</span><span class="sxs-lookup"><span data-stu-id="cd6f4-105">Staring with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="cd6f4-106"><xref:System.Collections.Generic.IEnumerable%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="cd6f4-107"><xref:System.Collections.Generic.IEnumerator%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="cd6f4-108"><xref:System.Linq.IQueryable%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="cd6f4-109"><xref:System.Linq.IGrouping%602> (`TKey` a `TElement` jsou kovariantní.)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="cd6f4-110"><xref:System.Collections.Generic.IComparer%601> (T je kontravariantní.)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="cd6f4-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T je kontravariantní.)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="cd6f4-112"><xref:System.IComparable%601> (T je kontravariantní.)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="cd6f4-113">Od verze rozhraní .NET Framework 4.5, jsou následující rozhraní variant:</span><span class="sxs-lookup"><span data-stu-id="cd6f4-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="cd6f4-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="cd6f4-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="cd6f4-116">Kovariance povoluje metoda může mít více odvozený návratový typ, než je definován parametr obecného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="cd6f4-117">K ilustraci této funkce kovariance, vezměte v úvahu těmito obecnými rozhraními: `IEnumerable<Object>` a `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="cd6f4-118">`IEnumerable<String>` Rozhraní nedědí `IEnumerable<Object>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="cd6f4-119">Ale `String` typ dědit `Object` typ a v některých případech můžete chtít přiřadit objekty z těchto rozhraní k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="cd6f4-120">To je ukázáno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="cd6f4-121">V dřívějších verzích rozhraní .NET Framework, tento kód způsobí chybu kompilace v C# a v případě `Option Strict` nachází v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="cd6f4-122">Nyní můžete použít, ale `strings` místo `objects`, jak je znázorněno v předchozím příkladu, protože <xref:System.Collections.Generic.IEnumerable%601> rozhraní je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="cd6f4-123">Kontravariance umožní metoda může mít typy argumentů, které jsou méně odvozený než je určeno obecný parametr rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="cd6f4-124">Pro ilustraci kontravariance se předpokládá, že jste vytvořili `BaseComparer` třídy k porovnání instance `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="cd6f4-125">`BaseComparer` Implementuje třída `IEqualityComparer<BaseClass>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="cd6f4-126">Protože <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní je kontravariantní, můžete použít `BaseComparer` k porovnání instance tříd, které dědí `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="cd6f4-127">To je ukázáno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-127">This is shown in the following code example.</span></span>

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

<span data-ttu-id="cd6f4-128">Další příklady najdete v tématu [použití odchylky v rozhraní pro obecné kolekce (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="cd6f4-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="cd6f4-129">Odchylky obecných rozhraní je podporována pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="cd6f4-130">Typy hodnot nepodporují variance.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-130">Value types do not support variance.</span></span> <span data-ttu-id="cd6f4-131">Například `IEnumerable<int>` nejde implicitně převést na `IEnumerable<object>`, protože celá čísla jsou reprezentovány hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="cd6f4-132">Taky je dobré si uvědomit, že jsou stále invariantní třídy, které implementují rozhraní variant.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="cd6f4-133">Například i když <xref:System.Collections.Generic.List%601> implementuje rozhraní kovariantní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List<Object>` k `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="cd6f4-134">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cd6f4-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="cd6f4-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd6f4-135">See also</span></span>

- [<span data-ttu-id="cd6f4-136">Použití odchylky v rozhraní pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="cd6f4-137">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-137">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [<span data-ttu-id="cd6f4-138">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd6f4-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="cd6f4-139">Odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="cd6f4-139">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
