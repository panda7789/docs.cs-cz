---
title: Variance v obecných rozhraních (C#)
description: Zobrazit informace o podpoře odchylek pro Obecná rozhraní, včetně aktualizovaných informací pro existující rozhraní v .NET Framework 4 a 4,5.
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 91218742c01eeb6e65ea26d9dc41ed7c98827377
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105627"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="454f4-103">Variance v obecných rozhraních (C#)</span><span class="sxs-lookup"><span data-stu-id="454f4-103">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="454f4-104">.NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="454f4-104">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="454f4-105">Podpora variance umožňuje implicitní převod tříd, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="454f4-105">Variance support enables implicit conversion of classes that implement these interfaces.</span></span>

<span data-ttu-id="454f4-106">Počínaje .NET Framework 4 jsou následující rozhraní typu variant:</span><span class="sxs-lookup"><span data-stu-id="454f4-106">Starting with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="454f4-107"><xref:System.Collections.Generic.IEnumerable%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="454f4-107"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="454f4-108"><xref:System.Collections.Generic.IEnumerator%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="454f4-108"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="454f4-109"><xref:System.Linq.IQueryable%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="454f4-109"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="454f4-110"><xref:System.Linq.IGrouping%602>( `TKey` a `TElement` jsou kovariantní)</span><span class="sxs-lookup"><span data-stu-id="454f4-110"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="454f4-111"><xref:System.Collections.Generic.IComparer%601>(T je kontravariantní)</span><span class="sxs-lookup"><span data-stu-id="454f4-111"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="454f4-112"><xref:System.Collections.Generic.IEqualityComparer%601>(T je kontravariantní)</span><span class="sxs-lookup"><span data-stu-id="454f4-112"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="454f4-113"><xref:System.IComparable%601>(T je kontravariantní)</span><span class="sxs-lookup"><span data-stu-id="454f4-113"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="454f4-114">Počínaje .NET Framework 4,5 jsou následující rozhraní typu variant:</span><span class="sxs-lookup"><span data-stu-id="454f4-114">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="454f4-115"><xref:System.Collections.Generic.IReadOnlyList%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="454f4-115"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="454f4-116"><xref:System.Collections.Generic.IReadOnlyCollection%601>(T je kovariantní)</span><span class="sxs-lookup"><span data-stu-id="454f4-116"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="454f4-117">Kovariance povoluje, aby metoda měla více odvozený návratový typ, než je definováno parametrem obecného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="454f4-117">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="454f4-118">Pro ilustraci funkce kovariance zvažte Tato obecná rozhraní: `IEnumerable<Object>` a `IEnumerable<String>` .</span><span class="sxs-lookup"><span data-stu-id="454f4-118">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="454f4-119">`IEnumerable<String>`Rozhraní nedědí `IEnumerable<Object>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="454f4-119">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="454f4-120">`String`Typ však dědí `Object` typ a v některých případech může být vhodné přiřadit objekty těchto rozhraní k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="454f4-120">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="454f4-121">Toto je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="454f4-121">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="454f4-122">V dřívějších verzích .NET Framework Tento kód způsobí chybu kompilace v jazyce C# a v případě, že `Option Strict` je zapnutý, v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="454f4-122">In earlier versions of .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="454f4-123">Teď ale můžete použít `strings` místo z `objects` , jak je znázorněno v předchozím příkladu, protože <xref:System.Collections.Generic.IEnumerable%601> rozhraní je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="454f4-123">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="454f4-124">Kontravariance umožňuje, aby metoda měla typy argumentů, které jsou méně odvozené než zadané obecným parametrem rozhraní.</span><span class="sxs-lookup"><span data-stu-id="454f4-124">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="454f4-125">Pro ilustraci aplikace kontravariance Předpokládejme, že jste vytvořili `BaseComparer` třídu pro porovnání instancí `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="454f4-125">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="454f4-126">Třída `BaseComparer` implementuje rozhraní `IEqualityComparer<BaseClass>`.</span><span class="sxs-lookup"><span data-stu-id="454f4-126">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="454f4-127">Vzhledem k tomu <xref:System.Collections.Generic.IEqualityComparer%601> , že rozhraní je nyní kontravariantní, lze použít `BaseComparer` k porovnání instancí tříd, které dědí `BaseClass` třídu.</span><span class="sxs-lookup"><span data-stu-id="454f4-127">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="454f4-128">Toto je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="454f4-128">This is shown in the following code example.</span></span>

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

<span data-ttu-id="454f4-129">Další příklady naleznete v tématu [použití variance v rozhraní pro obecné kolekce (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="454f4-129">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="454f4-130">Variance v obecných rozhraních je podporován pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="454f4-130">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="454f4-131">Typy hodnot nepodporují odchylku.</span><span class="sxs-lookup"><span data-stu-id="454f4-131">Value types do not support variance.</span></span> <span data-ttu-id="454f4-132">Například `IEnumerable<int>` nelze implicitně převést na `IEnumerable<object>` , protože celá čísla jsou reprezentována typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="454f4-132">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="454f4-133">Je také důležité pamatovat na to, že třídy, které implementují variantní rozhraní, jsou stále invariantní.</span><span class="sxs-lookup"><span data-stu-id="454f4-133">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="454f4-134">Například i když <xref:System.Collections.Generic.List%601> implementuje kovariantní rozhraní <xref:System.Collections.Generic.IEnumerable%601> , nemůžete implicitně převést `List<String>` na `List<Object>` .</span><span class="sxs-lookup"><span data-stu-id="454f4-134">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="454f4-135">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="454f4-135">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="454f4-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="454f4-136">See also</span></span>

- [<span data-ttu-id="454f4-137">Použití variance v rozhraních pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="454f4-137">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="454f4-138">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="454f4-138">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="454f4-139">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="454f4-139">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="454f4-140">Variance v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="454f4-140">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
