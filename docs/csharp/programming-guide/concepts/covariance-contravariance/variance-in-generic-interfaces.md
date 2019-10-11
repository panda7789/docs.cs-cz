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
# <a name="variance-in-generic-interfaces-c"></a>Variance v obecných rozhraníchC#()

.NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní. Podpora variance umožňuje implicitní převod tříd, které implementují tato rozhraní. 

Počínaje .NET Framework 4 jsou následující rozhraní typu variant:

- <xref:System.Collections.Generic.IEnumerable%601> (T je kovariantní)

- <xref:System.Collections.Generic.IEnumerator%601> (T je kovariantní)

- <xref:System.Linq.IQueryable%601> (T je kovariantní)

- <xref:System.Linq.IGrouping%602> (`TKey` a `TElement` jsou kovariantní)

- <xref:System.Collections.Generic.IComparer%601> (T je kontravariantní)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T je kontravariantní)

- <xref:System.IComparable%601> (T je kontravariantní)

Počínaje .NET Framework 4,5 jsou následující rozhraní typu variant:

- <xref:System.Collections.Generic.IReadOnlyList%601> (T je kovariantní)

- <xref:System.Collections.Generic.IReadOnlyCollection%601> (T je kovariantní)

Kovariance povoluje, aby metoda měla více odvozený návratový typ, než je definováno parametrem obecného typu rozhraní. K ilustraci funkce kovariance zvažte Tato obecná rozhraní: `IEnumerable<Object>` a `IEnumerable<String>`. Rozhraní `IEnumerable<String>` nedědí rozhraní `IEnumerable<Object>`. Typ `String` však zdědí typ `Object` a v některých případech může být vhodné přiřadit objekty těchto rozhraní k sobě navzájem. Toto je znázorněno v následujícím příkladu kódu.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

V dřívějších verzích .NET Framework Tento kód způsobuje chybu kompilace v C# a, pokud je `Option Strict` zapnuta, v Visual Basic. Nyní ale můžete použít `strings` namísto `objects`, jak je znázorněno v předchozím příkladu, protože rozhraní <xref:System.Collections.Generic.IEnumerable%601> je kovariantní.

Kontravariance umožňuje, aby metoda měla typy argumentů, které jsou méně odvozené než zadané obecným parametrem rozhraní. Pro ilustraci aplikace kontravariance Předpokládejme, že jste vytvořili třídu `BaseComparer` pro porovnání instancí třídy `BaseClass`. Třída `BaseComparer` implementuje rozhraní `IEqualityComparer<BaseClass>`. Vzhledem k tomu, že rozhraní <xref:System.Collections.Generic.IEqualityComparer%601> je nyní kontravariantní, můžete použít `BaseComparer` k porovnání instancí tříd, které dědí třídu `BaseClass`. Toto je znázorněno v následujícím příkladu kódu.

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

Je také důležité pamatovat na to, že třídy, které implementují variantní rozhraní, jsou stále invariantní. Například i když <xref:System.Collections.Generic.List%601> implementuje kovariantní rozhraní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List<String>` na `List<Object>`. To je znázorněno v následujícím příkladu kódu.

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
