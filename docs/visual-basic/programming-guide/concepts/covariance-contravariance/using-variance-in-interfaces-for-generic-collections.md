---
title: Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: 3c7cde2baf6d8b163c6765b87d6bebef803eb6ee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356699"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a>Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)

Kovariantní rozhraní umožňuje její metody k vrácení více odvozené typy než procesory zadané v rozhraní. Rozhraní kontravariantní umožňuje její metody přijímají parametry méně odvozené typy než platformám zadaným v rozhraní.

V rozhraní .NET Framework 4, stala několik existujících rozhraní kovariantního a kontravariantního. Patří mezi ně <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601>. To umožňuje znovu použít metody, které pracují s obecné kolekce základních typů pro kolekce odvozené typy.

Seznam variantních rozhraní v rozhraní .NET Framework najdete v tématu [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).

## <a name="converting-generic-collections"></a>Převádění obecných kolekcí

Následující příklad ukazuje výhody podpory Kovariance v <xref:System.Collections.Generic.IEnumerable%601> rozhraní. `PrintFullName` Metoda přijímá kolekce `IEnumerable(Of Person)` typ jako parametr. Ale můžete použít pro kolekce `IEnumerable(Of Person)` typu, protože `Employee` dědí `Person`.

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

## <a name="comparing-generic-collections"></a>Porovnání obecné kolekce

Následující příklad ukazuje výhody podpory kontravariance v <xref:System.Collections.Generic.IComparer%601> rozhraní. `PersonComparer` Implementuje třída `IComparer(Of Person)` rozhraní. Ale můžete znovu použít tuto třídu pro porovnání sekvence objektů `Employee` typu, protože `Employee` dědí `Person`.

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

- [Odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
