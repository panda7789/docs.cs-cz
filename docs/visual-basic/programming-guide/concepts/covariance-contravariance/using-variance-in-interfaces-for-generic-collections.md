---
title: Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: 860c41e73aa2d45ca1a9adcb3031834545e2fb37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642685"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a>Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)
Kovariantní rozhraní, které umožňuje její metody vrátit více odvozené typy než ty, zadaný v rozhraní. Kontravariant rozhraní, které umožňuje její metody tak, aby přijímal parametry menší odvozené typy než platformám zadaným v rozhraní.  
  
 V rozhraní .NET Framework 4, stala kovariantní několik existujících rozhraní a kontravariant. Mezi ně patří <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601>. Umožňuje znovu použít metody, které budou pracovat s obecné kolekce základních typů pro kolekce odvozené typy.  
  
 Seznam variantních rozhraní v rozhraní .NET Framework, naleznete v části [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Převádění obecné kolekce  
 Následující příklad ilustruje výhod kovariance podporu <xref:System.Collections.Generic.IEnumerable%601> rozhraní. `PrintFullName` Metoda přijímá kolekce `IEnumerable(Of Person)` typ jako parametr. Ale můžete použít pro kolekci `IEnumerable(Of Person)` typu, protože `Employee` dědí `Person`.  
  
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
 Následující příklad ilustruje výhod kontravariance podporu <xref:System.Collections.Generic.IComparer%601> rozhraní. `PersonComparer` Třída implementuje `IComparer(Of Person)` rozhraní. Však můžete znovu použít tuto třídu k porovnání posloupnost objekty `Employee` typu, protože `Employee` dědí `Person`.  
  
```vb  
' Simple hierarhcy of classes.  
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
  
## <a name="see-also"></a>Viz také  
 [Odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
