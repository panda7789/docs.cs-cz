---
title: Odchylka v obecných rozhraních (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 2020ea54734724de775192a1a438413a73003d17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169659"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="8e85b-102">Odchylka v obecných rozhraních (C#)</span><span class="sxs-lookup"><span data-stu-id="8e85b-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="8e85b-103">Rozhraní .NET Framework 4 zavedlo podporu rozptylu pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e85b-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="8e85b-104">Podpora odchylky umožňuje implicitní převod tříd, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e85b-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span>

<span data-ttu-id="8e85b-105">Počínaje rozhraním .NET Framework 4 jsou varianta následující rozhraní:</span><span class="sxs-lookup"><span data-stu-id="8e85b-105">Starting with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="8e85b-106"><xref:System.Collections.Generic.IEnumerable%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="8e85b-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="8e85b-107"><xref:System.Collections.Generic.IEnumerator%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="8e85b-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="8e85b-108"><xref:System.Linq.IQueryable%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="8e85b-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="8e85b-109"><xref:System.Linq.IGrouping%602>(`TKey` `TElement` a jsou kovariantní)</span><span class="sxs-lookup"><span data-stu-id="8e85b-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="8e85b-110"><xref:System.Collections.Generic.IComparer%601>(T je kontravarianta)</span><span class="sxs-lookup"><span data-stu-id="8e85b-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="8e85b-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T je kontravarianta)</span><span class="sxs-lookup"><span data-stu-id="8e85b-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="8e85b-112"><xref:System.IComparable%601>(T je kontravarianta)</span><span class="sxs-lookup"><span data-stu-id="8e85b-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="8e85b-113">Počínaje rozhraním .NET Framework 4.5 jsou varianta následující rozhraní:</span><span class="sxs-lookup"><span data-stu-id="8e85b-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="8e85b-114"><xref:System.Collections.Generic.IReadOnlyList%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="8e85b-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="8e85b-115"><xref:System.Collections.Generic.IReadOnlyCollection%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="8e85b-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="8e85b-116">Kovariance umožňuje metodu mít více odvozené návratový typ, než je definován parametrem obecného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e85b-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="8e85b-117">Chcete-li ilustrovat funkci kovariance, `IEnumerable<Object>` zvažte tato obecná rozhraní: a `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="8e85b-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="8e85b-118">Rozhraní `IEnumerable<String>` nedědí `IEnumerable<Object>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e85b-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="8e85b-119">`String` Typ však dědí `Object` typ a v některých případech můžete chtít přiřadit objekty těchto rozhraní k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="8e85b-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="8e85b-120">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8e85b-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="8e85b-121">V dřívějších verzích rozhraní .NET Framework způsobí tento kód chybu `Option Strict` kompilace v jazyce C# a pokud je zapnuto, v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8e85b-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="8e85b-122">Ale teď můžete `strings` použít `objects`místo , jak je znázorněno v předchozím příkladu, <xref:System.Collections.Generic.IEnumerable%601> protože rozhraní je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="8e85b-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="8e85b-123">Contravariance umožňuje metodu mít typy argumentů, které jsou méně odvozené než zadané obecným parametrem rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e85b-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="8e85b-124">Pro ilustraci protitřídy předpokládejme, že jste vytvořili třídu `BaseComparer` pro porovnání instancí `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="8e85b-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="8e85b-125">Třída `BaseComparer` implementuje rozhraní `IEqualityComparer<BaseClass>`.</span><span class="sxs-lookup"><span data-stu-id="8e85b-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="8e85b-126">Vzhledem <xref:System.Collections.Generic.IEqualityComparer%601> k tomu, že rozhraní `BaseComparer` je nyní contravariant, `BaseClass` můžete použít k porovnání instancí tříd, které dědí třídy.</span><span class="sxs-lookup"><span data-stu-id="8e85b-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="8e85b-127">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8e85b-127">This is shown in the following code example.</span></span>

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

<span data-ttu-id="8e85b-128">Další příklady naleznete [v tématu Použití odchylky v rozhraní pro obecné kolekce (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="8e85b-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="8e85b-129">Odchylka v obecných rozhraních je podporována pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="8e85b-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="8e85b-130">Typy hodnot nepodporují odchylky.</span><span class="sxs-lookup"><span data-stu-id="8e85b-130">Value types do not support variance.</span></span> <span data-ttu-id="8e85b-131">Nelze například `IEnumerable<int>` implicitně převést `IEnumerable<object>`na aplikaci , protože celá čísla jsou reprezentována typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8e85b-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="8e85b-132">Je také důležité si uvědomit, že třídy, které implementují variantní rozhraní jsou stále invariantní.</span><span class="sxs-lookup"><span data-stu-id="8e85b-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="8e85b-133">Například i <xref:System.Collections.Generic.List%601> když implementuje <xref:System.Collections.Generic.IEnumerable%601>kovariantní rozhraní `List<String>` `List<Object>`, nelze implicitně převést na .</span><span class="sxs-lookup"><span data-stu-id="8e85b-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="8e85b-134">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8e85b-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="8e85b-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e85b-135">See also</span></span>

- [<span data-ttu-id="8e85b-136">Použití odchylky v rozhraních pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="8e85b-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="8e85b-137">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="8e85b-137">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="8e85b-138">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e85b-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="8e85b-139">Odchylka v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="8e85b-139">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
