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
# <a name="variance-in-generic-interfaces-c"></a>Odchylka v obecných rozhraních (C#)

Rozhraní .NET Framework 4 zavedlo podporu rozptylu pro několik existujících obecných rozhraní. Podpora odchylky umožňuje implicitní převod tříd, které implementují tato rozhraní.

Počínaje rozhraním .NET Framework 4 jsou varianta následující rozhraní:

- <xref:System.Collections.Generic.IEnumerable%601>(T je kovariantní)

- <xref:System.Collections.Generic.IEnumerator%601>(T je kovariantní)

- <xref:System.Linq.IQueryable%601>(T je kovariantní)

- <xref:System.Linq.IGrouping%602>(`TKey` `TElement` a jsou kovariantní)

- <xref:System.Collections.Generic.IComparer%601>(T je kontravarianta)

- <xref:System.Collections.Generic.IEqualityComparer%601>(T je kontravarianta)

- <xref:System.IComparable%601>(T je kontravarianta)

Počínaje rozhraním .NET Framework 4.5 jsou varianta následující rozhraní:

- <xref:System.Collections.Generic.IReadOnlyList%601>(T je kovariantní)

- <xref:System.Collections.Generic.IReadOnlyCollection%601>(T je kovariantní)

Kovariance umožňuje metodu mít více odvozené návratový typ, než je definován parametrem obecného typu rozhraní. Chcete-li ilustrovat funkci kovariance, `IEnumerable<Object>` zvažte tato obecná rozhraní: a `IEnumerable<String>`. Rozhraní `IEnumerable<String>` nedědí `IEnumerable<Object>` rozhraní. `String` Typ však dědí `Object` typ a v některých případech můžete chtít přiřadit objekty těchto rozhraní k sobě navzájem. To je znázorněno v následujícím příkladu kódu.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

V dřívějších verzích rozhraní .NET Framework způsobí tento kód chybu `Option Strict` kompilace v jazyce C# a pokud je zapnuto, v jazyce Visual Basic. Ale teď můžete `strings` použít `objects`místo , jak je znázorněno v předchozím příkladu, <xref:System.Collections.Generic.IEnumerable%601> protože rozhraní je kovariantní.

Contravariance umožňuje metodu mít typy argumentů, které jsou méně odvozené než zadané obecným parametrem rozhraní. Pro ilustraci protitřídy předpokládejme, že jste vytvořili třídu `BaseComparer` pro porovnání instancí `BaseClass` třídy. Třída `BaseComparer` implementuje rozhraní `IEqualityComparer<BaseClass>`. Vzhledem <xref:System.Collections.Generic.IEqualityComparer%601> k tomu, že rozhraní `BaseComparer` je nyní contravariant, `BaseClass` můžete použít k porovnání instancí tříd, které dědí třídy. To je znázorněno v následujícím příkladu kódu.

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

Další příklady naleznete [v tématu Použití odchylky v rozhraní pro obecné kolekce (C#)](./using-variance-in-interfaces-for-generic-collections.md).

Odchylka v obecných rozhraních je podporována pouze pro typy odkazů. Typy hodnot nepodporují odchylky. Nelze například `IEnumerable<int>` implicitně převést `IEnumerable<object>`na aplikaci , protože celá čísla jsou reprezentována typem hodnoty.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Je také důležité si uvědomit, že třídy, které implementují variantní rozhraní jsou stále invariantní. Například i <xref:System.Collections.Generic.List%601> když implementuje <xref:System.Collections.Generic.IEnumerable%601>kovariantní rozhraní `List<String>` `List<Object>`, nelze implicitně převést na . To je znázorněno v následujícím příkladu kódu.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Viz také

- [Použití odchylky v rozhraních pro obecné kolekce (C#)](./using-variance-in-interfaces-for-generic-collections.md)
- [Vytváření variantních obecných rozhraní (C#)](./creating-variant-generic-interfaces.md)
- [Obecná rozhraní](../../../../standard/generics/interfaces.md)
- [Odchylka v delegátech (C#)](./variance-in-delegates.md)
