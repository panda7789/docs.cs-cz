---
title: Použití odchylky v rozhraní pro obecné kolekce
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: 6ee133dfd61d7d7a88243ca592642ff21e0c2223
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349011"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a>Použití variance v rozhraních pro obecné kolekce (Visual Basic)

Kovariantní rozhraní umožňuje svým metodám vracet více odvozených typů než ty, které jsou zadány v rozhraní. Kontravariantní rozhraní umožňuje jeho metodám přijímat parametry méně odvozených typů než těch, které jsou zadány v rozhraní.

V .NET Framework 4 se několik stávajících rozhraní stala kovariantou a kontravariantní. Mezi ně patří <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601>. To umožňuje znovu použít metody, které pracují s obecnými kolekcemi základních typů pro kolekce odvozených typů.

Seznam rozhraní variant v .NET Framework naleznete v tématu [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).

## <a name="converting-generic-collections"></a>Převod obecných kolekcí

Následující příklad ukazuje výhody kovariance v rozhraní <xref:System.Collections.Generic.IEnumerable%601>. Metoda `PrintFullName` přijímá kolekci `IEnumerable(Of Person)` typu jako parametr. Můžete ji však znovu použít pro kolekci `IEnumerable(Of Person)`ho typu, protože `Employee` dědí `Person`.

```vb
' Simple hierarchy of classes.
Public Class Person
    Public Property FirstName As String
    Public Property LastName As String
End Class

Public Class Employee
    Inherits Person
End Class

' The method has a parameter of the IEnumerable(Of Person) type.
Public Sub PrintFullName(ByVal persons As IEnumerable(Of Person))
    For Each person As Person In persons
        Console.WriteLine(
            "Name: " & person.FirstName & " " & person.LastName)
    Next
End Sub

Sub Main()
    Dim employees As IEnumerable(Of Employee) = New List(Of Employee)

    ' You can pass IEnumerable(Of Employee),
    ' although the method expects IEnumerable(Of Person).

    PrintFullName(employees)

End Sub
```

## <a name="comparing-generic-collections"></a>Porovnání obecných kolekcí

Následující příklad znázorňuje výhody podpory aplikace kontravariance v rozhraní <xref:System.Collections.Generic.IComparer%601>. Třída `PersonComparer` implementuje rozhraní `IComparer(Of Person)`. Tuto třídu však můžete použít k porovnání sekvence objektů `Employee`ho typu, protože `Employee` dědí `Person`.

```vb
' Simple hierarchy of classes.
Public Class Person
    Public Property FirstName As String
    Public Property LastName As String
End Class

Public Class Employee
    Inherits Person
End Class
' The custom comparer for the Person type
' with standard implementations of Equals()
' and GetHashCode() methods.
Class PersonComparer
    Implements IEqualityComparer(Of Person)

    Public Function Equals1(
        ByVal x As Person,
        ByVal y As Person) As Boolean _
        Implements IEqualityComparer(Of Person).Equals

        If x Is y Then Return True
        If x Is Nothing OrElse y Is Nothing Then Return False
        Return (x.FirstName = y.FirstName) AndAlso
            (x.LastName = y.LastName)
    End Function
    Public Function GetHashCode1(
        ByVal person As Person) As Integer _
        Implements IEqualityComparer(Of Person).GetHashCode

        If person Is Nothing Then Return 0
        Dim hashFirstName =
            If(person.FirstName Is Nothing,
            0, person.FirstName.GetHashCode())
        Dim hashLastName = person.LastName.GetHashCode()
        Return hashFirstName Xor hashLastName
    End Function
End Class

Sub Main()
    Dim employees = New List(Of Employee) From {
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}
    }

    ' You can pass PersonComparer,
    ' which implements IEqualityComparer(Of Person),
    ' although the method expects IEqualityComparer(Of Employee)

    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())

    For Each employee In noduplicates
        Console.WriteLine(employee.FirstName & " " & employee.LastName)
    Next
End Sub
```

## <a name="see-also"></a>Viz také:

- [Variance v obecných rozhraních (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
