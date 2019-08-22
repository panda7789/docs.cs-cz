---
title: Použití odchylky pro obecné delegáty Func a Action (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: ce560f6246469620032ececa4afeeffe69baf407
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664364"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="7b4aa-102">Použití odchylky pro obecné delegáty Func a Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b4aa-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="7b4aa-103">Tyto příklady ukazují, jak použít kovarianci a kontravariance v `Func` obecných delegátech a `Action` umožnit opakované použití metod a zajištění větší flexibility v kódu.</span><span class="sxs-lookup"><span data-stu-id="7b4aa-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="7b4aa-104">Další informace o kovarianci a kontravariance naleznete v tématu [Variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="7b4aa-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="7b4aa-105">Použití delegátů s parametry kovariantního typu</span><span class="sxs-lookup"><span data-stu-id="7b4aa-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="7b4aa-106">Následující příklad znázorňuje výhody kovariance v obecných `Func` delegátech.</span><span class="sxs-lookup"><span data-stu-id="7b4aa-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="7b4aa-107">Metoda přebírá parametr `String` typu a `Employee` vrací objekt typu. `FindByTitle`</span><span class="sxs-lookup"><span data-stu-id="7b4aa-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="7b4aa-108">Tuto metodu `Func(Of String, Person)` však můžete přiřadit delegátovi, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="7b4aa-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="7b4aa-109">Použití delegátů s kontravariantními parametry typu</span><span class="sxs-lookup"><span data-stu-id="7b4aa-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="7b4aa-110">Následující příklad znázorňuje výhody podpory aplikace kontravariance v obecných `Action` delegátech.</span><span class="sxs-lookup"><span data-stu-id="7b4aa-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="7b4aa-111">Metoda přebírá parametr `Person`typu. `AddToContacts`</span><span class="sxs-lookup"><span data-stu-id="7b4aa-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="7b4aa-112">Tuto metodu `Action(Of Employee)` však můžete přiřadit delegátovi, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="7b4aa-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7b4aa-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b4aa-113">See also</span></span>

- [<span data-ttu-id="7b4aa-114">Kovariance a kontravariance (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b4aa-114">Covariance and Contravariance (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="7b4aa-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="7b4aa-115">Generics</span></span>](../../../../standard/generics/index.md)
