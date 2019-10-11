---
title: Variance v obecných rozhraníchC#()
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 71225814a11074f52e4937dec88ca5e27114d6c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179063"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="aa94a-102">Variance v obecných rozhraníchC#()</span><span class="sxs-lookup"><span data-stu-id="aa94a-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="aa94a-103">.NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa94a-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="aa94a-104">Podpora variance umožňuje implicitní převod tříd, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa94a-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> 

<span data-ttu-id="aa94a-105">Počínaje .NET Framework 4 jsou následující rozhraní typu variant:</span><span class="sxs-lookup"><span data-stu-id="aa94a-105">Starting with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="aa94a-106"><xref:System.Collections.Generic.IEnumerable%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="aa94a-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="aa94a-107"><xref:System.Collections.Generic.IEnumerator%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="aa94a-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="aa94a-108"><xref:System.Linq.IQueryable%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="aa94a-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="aa94a-109"><xref:System.Linq.IGrouping%602> (`TKey` a `TElement` jsou kovariantní)</span><span class="sxs-lookup"><span data-stu-id="aa94a-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="aa94a-110"><xref:System.Collections.Generic.IComparer%601> (T je kontravariantní)</span><span class="sxs-lookup"><span data-stu-id="aa94a-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="aa94a-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T je kontravariantní)</span><span class="sxs-lookup"><span data-stu-id="aa94a-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="aa94a-112"><xref:System.IComparable%601> (T je kontravariantní)</span><span class="sxs-lookup"><span data-stu-id="aa94a-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="aa94a-113">Počínaje .NET Framework 4,5 jsou následující rozhraní typu variant:</span><span class="sxs-lookup"><span data-stu-id="aa94a-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="aa94a-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="aa94a-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="aa94a-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="aa94a-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="aa94a-116">Kovariance povoluje, aby metoda měla více odvozený návratový typ, než je definováno parametrem obecného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa94a-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="aa94a-117">K ilustraci funkce kovariance zvažte Tato obecná rozhraní: `IEnumerable<Object>` a `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="aa94a-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="aa94a-118">Rozhraní `IEnumerable<String>` nedědí rozhraní `IEnumerable<Object>`.</span><span class="sxs-lookup"><span data-stu-id="aa94a-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="aa94a-119">Typ `String` však zdědí typ `Object` a v některých případech může být vhodné přiřadit objekty těchto rozhraní k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="aa94a-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="aa94a-120">Toto je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="aa94a-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="aa94a-121">V dřívějších verzích .NET Framework Tento kód způsobuje chybu kompilace v C# a, pokud je `Option Strict` zapnuta, v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="aa94a-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="aa94a-122">Nyní ale můžete použít `strings` namísto `objects`, jak je znázorněno v předchozím příkladu, protože rozhraní <xref:System.Collections.Generic.IEnumerable%601> je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="aa94a-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="aa94a-123">Kontravariance umožňuje, aby metoda měla typy argumentů, které jsou méně odvozené než zadané obecným parametrem rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa94a-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="aa94a-124">Pro ilustraci aplikace kontravariance Předpokládejme, že jste vytvořili třídu `BaseComparer` pro porovnání instancí třídy `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="aa94a-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="aa94a-125">Třída `BaseComparer` implementuje rozhraní `IEqualityComparer<BaseClass>`.</span><span class="sxs-lookup"><span data-stu-id="aa94a-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="aa94a-126">Vzhledem k tomu, že rozhraní <xref:System.Collections.Generic.IEqualityComparer%601> je nyní kontravariantní, můžete použít `BaseComparer` k porovnání instancí tříd, které dědí třídu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="aa94a-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="aa94a-127">Toto je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="aa94a-127">This is shown in the following code example.</span></span>

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

<span data-ttu-id="aa94a-128">Další příklady naleznete v tématu [použití variance v rozhraních pro obecné kolekceC#()](./using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="aa94a-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="aa94a-129">Variance v obecných rozhraních je podporován pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="aa94a-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="aa94a-130">Typy hodnot nepodporují odchylku.</span><span class="sxs-lookup"><span data-stu-id="aa94a-130">Value types do not support variance.</span></span> <span data-ttu-id="aa94a-131">Například `IEnumerable<int>` nelze implicitně převést na `IEnumerable<object>`, protože celá čísla jsou reprezentována typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="aa94a-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="aa94a-132">Je také důležité pamatovat na to, že třídy, které implementují variantní rozhraní, jsou stále invariantní.</span><span class="sxs-lookup"><span data-stu-id="aa94a-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="aa94a-133">Například i když <xref:System.Collections.Generic.List%601> implementuje kovariantní rozhraní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List<String>` na `List<Object>`.</span><span class="sxs-lookup"><span data-stu-id="aa94a-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="aa94a-134">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="aa94a-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="aa94a-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa94a-135">See also</span></span>

- [<span data-ttu-id="aa94a-136">Použití variance v rozhraních pro obecné kolekceC#()</span><span class="sxs-lookup"><span data-stu-id="aa94a-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="aa94a-137">Vytváření variantních obecných rozhraníC#()</span><span class="sxs-lookup"><span data-stu-id="aa94a-137">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="aa94a-138">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa94a-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="aa94a-139">Variance v delegátechC#()</span><span class="sxs-lookup"><span data-stu-id="aa94a-139">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
