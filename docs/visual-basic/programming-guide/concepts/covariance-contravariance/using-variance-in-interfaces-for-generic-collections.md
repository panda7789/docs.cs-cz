---
title: Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: 7265fc208b7538a2ab63822afbe63b09b0f34135
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735406"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="bc538-102">Použití odchylky v rozhraní pro obecné kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc538-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>
<span data-ttu-id="bc538-103">Kovariantní rozhraní umožňuje její metody k vrácení více odvozené typy než procesory zadané v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc538-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="bc538-104">Rozhraní kontravariantní umožňuje její metody přijímají parametry méně odvozené typy než platformám zadaným v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc538-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="bc538-105">V rozhraní .NET Framework 4, stala několik existujících rozhraní kovariantního a kontravariantního.</span><span class="sxs-lookup"><span data-stu-id="bc538-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="bc538-106">Patří mezi ně <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="bc538-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="bc538-107">To umožňuje znovu použít metody, které pracují s obecné kolekce základních typů pro kolekce odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="bc538-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="bc538-108">Seznam variantních rozhraní v rozhraní .NET Framework najdete v tématu [odchylky obecných rozhraní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="bc538-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="bc538-109">Převádění obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="bc538-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="bc538-110">Následující příklad ukazuje výhody podpory Kovariance v <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc538-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="bc538-111">`PrintFullName` Metoda přijímá kolekce `IEnumerable(Of Person)` typ jako parametr.</span><span class="sxs-lookup"><span data-stu-id="bc538-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="bc538-112">Ale můžete použít pro kolekce `IEnumerable(Of Person)` typu, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="bc538-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="bc538-113">Porovnání obecné kolekce</span><span class="sxs-lookup"><span data-stu-id="bc538-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="bc538-114">Následující příklad ukazuje výhody podpory kontravariance v <xref:System.Collections.Generic.IComparer%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc538-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="bc538-115">`PersonComparer` Implementuje třída `IComparer(Of Person)` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc538-115">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="bc538-116">Ale můžete znovu použít tuto třídu pro porovnání sekvence objektů `Employee` typu, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="bc538-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc538-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc538-117">See also</span></span>
- [<span data-ttu-id="bc538-118">Odchylky obecných rozhraní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc538-118">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
