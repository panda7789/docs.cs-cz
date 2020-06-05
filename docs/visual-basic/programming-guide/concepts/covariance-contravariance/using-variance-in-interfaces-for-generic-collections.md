---
title: Použití odchylky v rozhraní pro obecné kolekce
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: b762ce42215f9b24371313446637e95962677bfb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375638"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="aa093-102">Použití variance v rozhraních pro obecné kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa093-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>

<span data-ttu-id="aa093-103">Kovariantní rozhraní umožňuje svým metodám vracet více odvozených typů než ty, které jsou zadány v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa093-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="aa093-104">Kontravariantní rozhraní umožňuje jeho metodám přijímat parametry méně odvozených typů než těch, které jsou zadány v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa093-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>

<span data-ttu-id="aa093-105">V .NET Framework 4 se několik stávajících rozhraní stala kovariantou a kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="aa093-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="aa093-106">Mezi ně patří <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> .</span><span class="sxs-lookup"><span data-stu-id="aa093-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="aa093-107">To umožňuje znovu použít metody, které pracují s obecnými kolekcemi základních typů pro kolekce odvozených typů.</span><span class="sxs-lookup"><span data-stu-id="aa093-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>

<span data-ttu-id="aa093-108">Seznam rozhraní variant v .NET Framework naleznete v tématu [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="aa093-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md).</span></span>

## <a name="converting-generic-collections"></a><span data-ttu-id="aa093-109">Převod obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="aa093-109">Converting Generic Collections</span></span>

<span data-ttu-id="aa093-110">Následující příklad ukazuje výhody kovariance v <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa093-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="aa093-111">`PrintFullName`Metoda přijímá kolekci `IEnumerable(Of Person)` typu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="aa093-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="aa093-112">Můžete ji však znovu použít pro kolekci `IEnumerable(Of Person)` typu, protože `Employee` dědí `Person` .</span><span class="sxs-lookup"><span data-stu-id="aa093-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>

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

## <a name="comparing-generic-collections"></a><span data-ttu-id="aa093-113">Porovnání obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="aa093-113">Comparing Generic Collections</span></span>

<span data-ttu-id="aa093-114">Následující příklad znázorňuje výhody podpory aplikace kontravariance v <xref:System.Collections.Generic.IComparer%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa093-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="aa093-115">Třída `PersonComparer` implementuje rozhraní `IComparer(Of Person)`.</span><span class="sxs-lookup"><span data-stu-id="aa093-115">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="aa093-116">Tuto třídu však můžete použít k porovnání sekvence objektů `Employee` typu, protože `Employee` dědí `Person` .</span><span class="sxs-lookup"><span data-stu-id="aa093-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aa093-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa093-117">See also</span></span>

- [<span data-ttu-id="aa093-118">Variance v obecných rozhraních (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa093-118">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)
