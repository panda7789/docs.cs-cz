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
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a>Použití odchylky pro obecné delegáty Func a Action (Visual Basic)
Tyto příklady ukazují, jak použít kovarianci a kontravariance v `Func` obecných delegátech a `Action` umožnit opakované použití metod a zajištění větší flexibility v kódu.  
  
 Další informace o kovarianci a kontravariance naleznete v tématu [Variance v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Použití delegátů s parametry kovariantního typu  
 Následující příklad znázorňuje výhody kovariance v obecných `Func` delegátech. Metoda přebírá parametr `String` typu a `Employee` vrací objekt typu. `FindByTitle` Tuto metodu `Func(Of String, Person)` však můžete přiřadit delegátovi, protože `Employee` dědí `Person`.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Použití delegátů s kontravariantními parametry typu  
 Následující příklad znázorňuje výhody podpory aplikace kontravariance v obecných `Action` delegátech. Metoda přebírá parametr `Person`typu. `AddToContacts` Tuto metodu `Action(Of Employee)` však můžete přiřadit delegátovi, protože `Employee` dědí `Person`.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Kovariance a kontravariance (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Obecné typy](../../../../standard/generics/index.md)
