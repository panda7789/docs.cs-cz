---
title: "Použití odchylek pro Func a akce obecní delegáti (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b8f9b2ebf758bc0d67b2b623038a4beeb7149261
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="1c2cb-102">Použití odchylek pro Func a akce obecní delegáti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c2cb-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="1c2cb-103">Tyto příklady ukazují, jak používat kovariance a kontravariance v `Func` a `Action` obecní delegáti povolit opakované použití metod a poskytují větší flexibilitu v kódu.</span><span class="sxs-lookup"><span data-stu-id="1c2cb-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="1c2cb-104">Další informace o kovarianci a kontravarianci najdete v tématu [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1c2cb-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="1c2cb-105">Použití delegátů s kovariantní parametry typu</span><span class="sxs-lookup"><span data-stu-id="1c2cb-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="1c2cb-106">Následující příklad ilustruje výhody kovariance podpory v Obecné `Func` delegáti.</span><span class="sxs-lookup"><span data-stu-id="1c2cb-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="1c2cb-107">`FindByTitle` Metoda přebírá parametr `String` typ a vrátí objekt `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="1c2cb-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="1c2cb-108">Však můžete přiřadit tuto metodu za účelem `Func(Of String, Person)` delegáta, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="1c2cb-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="1c2cb-109">Použití delegátů pomocí parametrů typu kontravariant</span><span class="sxs-lookup"><span data-stu-id="1c2cb-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="1c2cb-110">Následující příklad ilustruje výhod podpory kontravariance v Obecné `Action` delegáti.</span><span class="sxs-lookup"><span data-stu-id="1c2cb-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="1c2cb-111">`AddToContacts` Metoda přebírá parametr `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="1c2cb-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="1c2cb-112">Však můžete přiřadit tuto metodu za účelem `Action(Of Employee)` delegáta, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="1c2cb-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c2cb-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c2cb-113">See Also</span></span>  
 [<span data-ttu-id="1c2cb-114">Kovariance a kontravariance (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c2cb-114">Covariance and Contravariance (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="1c2cb-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1c2cb-115">Generics</span></span>](~/docs/standard/generics/index.md)
