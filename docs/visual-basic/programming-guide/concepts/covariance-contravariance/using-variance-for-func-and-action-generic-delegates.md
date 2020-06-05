---
title: Použití odchylek pro obecné delegáty Func a Action
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: f824d2422d67f1395d21a0863ca8c95d9f108989
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375755"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="d5e03-102">Použití odchylky pro obecné delegáty Func a Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5e03-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>

<span data-ttu-id="d5e03-103">Tyto příklady ukazují, jak použít kovarianci a kontravariance v `Func` `Action` obecných delegátech a umožnit opakované použití metod a zajištění větší flexibility v kódu.</span><span class="sxs-lookup"><span data-stu-id="d5e03-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>

<span data-ttu-id="d5e03-104">Další informace o kovarianci a kontravariance naleznete v tématu [Variance v delegátech (Visual Basic)](variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d5e03-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="d5e03-105">Použití delegátů s parametry kovariantního typu</span><span class="sxs-lookup"><span data-stu-id="d5e03-105">Using Delegates with Covariant Type Parameters</span></span>

<span data-ttu-id="d5e03-106">Následující příklad znázorňuje výhody kovariance v obecných `Func` delegátech.</span><span class="sxs-lookup"><span data-stu-id="d5e03-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="d5e03-107">`FindByTitle`Metoda přebírá parametr `String` typu a vrací objekt `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="d5e03-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="d5e03-108">Tuto metodu však můžete přiřadit `Func(Of String, Person)` delegátovi, protože `Employee` dědí `Person` .</span><span class="sxs-lookup"><span data-stu-id="d5e03-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>

```vb
' Simple hierarchy of classes.
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class Finder
    Public Shared Function FindByTitle(
        ByVal title As String) As Employee
        ' This is a stub for a method that returns
        ' an employee that has the specified title.
        Return New Employee
    End Function

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim findEmployee As Func(Of String, Employee) =
            AddressOf FindByTitle

        ' The delegate expects a method to return Person,
        ' but you can assign it a method that returns Employee.
        Dim findPerson As Func(Of String, Person) =
            AddressOf FindByTitle

        ' You can also assign a delegate
        ' that returns a more derived type to a delegate
        ' that returns a less derived type.
        findPerson = findEmployee
    End Sub
End Class
```

## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="d5e03-109">Použití delegátů s kontravariantními parametry typu</span><span class="sxs-lookup"><span data-stu-id="d5e03-109">Using Delegates with Contravariant Type Parameters</span></span>

<span data-ttu-id="d5e03-110">Následující příklad znázorňuje výhody podpory aplikace kontravariance v obecných `Action` delegátech.</span><span class="sxs-lookup"><span data-stu-id="d5e03-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="d5e03-111">`AddToContacts`Metoda přebírá parametr `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="d5e03-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="d5e03-112">Tuto metodu však můžete přiřadit `Action(Of Employee)` delegátovi, protože `Employee` dědí `Person` .</span><span class="sxs-lookup"><span data-stu-id="d5e03-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>

```vb
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class AddressBook
    Shared Sub AddToContacts(ByVal person As Person)
        ' This method adds a Person object
        ' to a contact list.
    End Sub

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim addPersonToContacts As Action(Of Person) =
            AddressOf AddToContacts

        ' The Action delegate expects
        ' a method that has an Employee parameter,
        ' but you can assign it a method that has a Person parameter
        ' because Employee derives from Person.
        Dim addEmployeeToContacts As Action(Of Employee) =
            AddressOf AddToContacts

        ' You can also assign a delegate
        ' that accepts a less derived parameter
        ' to a delegate that accepts a more derived parameter.
        addEmployeeToContacts = addPersonToContacts
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="d5e03-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5e03-113">See also</span></span>

- [<span data-ttu-id="d5e03-114">Kovariance a kontravariance (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5e03-114">Covariance and Contravariance (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="d5e03-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="d5e03-115">Generics</span></span>](../../../../standard/generics/index.md)
