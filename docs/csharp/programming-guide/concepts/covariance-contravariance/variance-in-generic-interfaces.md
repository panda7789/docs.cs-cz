---
title: Variance v obecných rozhraníchC#()
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 12a8b58983256be0ca2b56ea6ed09e724e0814c8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595159"
---
# <a name="variance-in-generic-interfaces-c"></a>Variance v obecných rozhraníchC#()

.NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní. Podpora variance umožňuje implicitní převod tříd, které implementují tato rozhraní. 

Hvězdičky s .NET Framework 4 jsou následující rozhraní variant:

- <xref:System.Collections.Generic.IEnumerable%601>(T je kovariantní)

- <xref:System.Collections.Generic.IEnumerator%601>(T je kovariantní)

- <xref:System.Linq.IQueryable%601>(T je kovariantní)

- <xref:System.Linq.IGrouping%602>(`TKey` a`TElement` jsou kovariantní)

- <xref:System.Collections.Generic.IComparer%601>(T je kontravariantní)

- <xref:System.Collections.Generic.IEqualityComparer%601>(T je kontravariantní)

- <xref:System.IComparable%601>(T je kontravariantní)

Počínaje .NET Framework 4,5 jsou následující rozhraní typu variant:

- <xref:System.Collections.Generic.IReadOnlyList%601>(T je kovariantní)

- <xref:System.Collections.Generic.IReadOnlyCollection%601>(T je kovariantní)

Kovariance povoluje, aby metoda měla více odvozený návratový typ, než je definováno parametrem obecného typu rozhraní. Pro ilustraci funkce kovariance zvažte Tato obecná rozhraní: `IEnumerable<Object>` a. `IEnumerable<String>` `IEnumerable<String>` Rozhraní nedědí rozhraní. `IEnumerable<Object>` `String` Typ však`Object` dědí typ a v některých případech může být vhodné přiřadit objekty těchto rozhraní k sobě navzájem. Toto je znázorněno v následujícím příkladu kódu.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

V dřívějších verzích .NET Framework Tento kód způsobuje chybu kompilace v C# a, pokud `Option Strict` je v, v Visual Basic. Teď ale můžete použít `strings` místo z `objects`, jak je znázorněno v <xref:System.Collections.Generic.IEnumerable%601> předchozím příkladu, protože rozhraní je kovariantní.

Kontravariance umožňuje, aby metoda měla typy argumentů, které jsou méně odvozené než zadané obecným parametrem rozhraní. Pro ilustraci aplikace kontravariance Předpokládejme, že jste vytvořili `BaseComparer` třídu pro porovnání instancí `BaseClass` třídy. `BaseComparer` Třída`IEqualityComparer<BaseClass>` implementuje rozhraní. Vzhledem k tomu, že `BaseComparer` `BaseClass` rozhraníjenyníkontravariantní,lzepoužítkporovnáníinstancítříd,<xref:System.Collections.Generic.IEqualityComparer%601> které dědí třídu. Toto je znázorněno v následujícím příkladu kódu.

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

Další příklady naleznete v tématu [použití variance v rozhraních pro obecné kolekceC#()](./using-variance-in-interfaces-for-generic-collections.md).

Variance v obecných rozhraních je podporován pouze pro typy odkazů. Typy hodnot nepodporují odchylku. Například `IEnumerable<int>` nelze implicitně převést na `IEnumerable<object>`, protože celá čísla jsou reprezentována typem hodnoty.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Je také důležité pamatovat na to, že třídy, které implementují variantní rozhraní, jsou stále invariantní. Například i když <xref:System.Collections.Generic.List%601> implementuje kovariantní rozhraní <xref:System.Collections.Generic.IEnumerable%601>, nemůžete implicitně převést `List<String>` na `List<Object>`. To je znázorněno v následujícím příkladu kódu.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Viz také:

- [Použití variance v rozhraních pro obecné kolekceC#()](./using-variance-in-interfaces-for-generic-collections.md)
- [Vytváření variantních obecných rozhraníC#()](./creating-variant-generic-interfaces.md)
- [Obecná rozhraní](../../../../standard/generics/interfaces.md)
- [Variance v delegátechC#()](./variance-in-delegates.md)
