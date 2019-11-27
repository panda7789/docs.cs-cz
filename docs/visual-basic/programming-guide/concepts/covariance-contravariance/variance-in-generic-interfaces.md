---
title: Odchylky obecných rozhraní
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 1f6913b322e2d3d9ec2234e556e63d67324277e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348980"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a>Variance v obecných rozhraních (Visual Basic)

.NET Framework 4 představili podporu variance pro několik existujících obecných rozhraní. Podpora variance umožňuje implicitní převod tříd, které implementují tato rozhraní. Nyní jsou k disvariantě následující rozhraní:

- <xref:System.Collections.Generic.IEnumerable%601> (T je kovariantní)

- <xref:System.Collections.Generic.IEnumerator%601> (T je kovariantní)

- <xref:System.Linq.IQueryable%601> (T je kovariantní)

- <xref:System.Linq.IGrouping%602> (`TKey` a `TElement` jsou kovariantní)

- <xref:System.Collections.Generic.IComparer%601> (T je kontravariantní)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T je kontravariantní)

- <xref:System.IComparable%601> (T je kontravariantní)

Kovariance povoluje, aby metoda měla více odvozený návratový typ, než je definováno parametrem obecného typu rozhraní. Pro ilustraci funkce kovariance zvažte Tato obecná rozhraní: `IEnumerable(Of Object)` a `IEnumerable(Of String)`. Rozhraní `IEnumerable(Of String)` nedědí rozhraní `IEnumerable(Of Object)`. Typ `String` však dědí typ `Object` a v některých případech může být vhodné přiřadit objekty těchto rozhraní k sobě navzájem. Toto je znázorněno v následujícím příkladu kódu.

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

V dřívějších verzích .NET Framework Tento kód způsobuje chybu kompilace v Visual Basic s `Option Strict On`. Teď ale můžete místo `objects`použít `strings`, jak je znázorněno v předchozím příkladu, protože rozhraní <xref:System.Collections.Generic.IEnumerable%601> je kovariantní.

Kontravariance umožňuje, aby metoda měla typy argumentů, které jsou méně odvozené než zadané obecným parametrem rozhraní. Pro ilustraci aplikace kontravariance Předpokládejme, že jste vytvořili třídu `BaseComparer` pro porovnání instancí `BaseClass` třídy. Třída `BaseComparer` implementuje rozhraní `IEqualityComparer(Of BaseClass)`. Vzhledem k tomu, že rozhraní <xref:System.Collections.Generic.IEqualityComparer%601> je nyní kontravariantní, lze pomocí `BaseComparer` porovnat instance tříd, které dědí třídu `BaseClass`. Toto je znázorněno v následujícím příkladu kódu.

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

Další příklady naleznete v tématu [použití variance v rozhraních pro obecné kolekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).

Variance v obecných rozhraních je podporován pouze pro typy odkazů. Typy hodnot nepodporují odchylku. Například `IEnumerable(Of Integer)` nelze implicitně převést na `IEnumerable(Of Object)`, protože celá čísla jsou reprezentována typem hodnoty.

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

Je také důležité pamatovat na to, že třídy, které implementují variantní rozhraní, jsou stále invariantní. Například i když <xref:System.Collections.Generic.List%601> implementuje kovariantní rozhraní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List(Of Object)` na `List(Of String)`. To je znázorněno v následujícím příkladu kódu.

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a>Viz také:

- [Použití variance v rozhraních pro obecné kolekce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [Vytváření variantních obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [Obecná rozhraní](../../../../standard/generics/interfaces.md)
- [Variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
