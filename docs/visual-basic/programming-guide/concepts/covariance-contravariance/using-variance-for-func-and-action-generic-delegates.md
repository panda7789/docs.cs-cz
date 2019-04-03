---
title: Použití odchylek pro delegáty Func a Action obecný (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: f2f45a9b6536859499f882b4cd585595176208f2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814291"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a>Použití odchylek pro delegáty Func a Action obecný (Visual Basic)
Tyto příklady ukazují, jak používat kovariance a kontravariance v `Func` a `Action` obecné delegáty umožňují opakované použití metod a poskytují větší flexibilitu v kódu.  
  
 Další informace o kovarianci a kontravarianci naleznete v tématu [odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Použití delegátů parametry kovariantního typu  
 Následující příklad ukazuje výhody podpory Kovariance v Obecné `Func` delegátů. `FindByTitle` Metoda přijímá parametr `String` typ a vrátí objekt `Employee` typu. Však můžete přiřadit tuto metodu za účelem `Func(Of String, Person)` delegáta, protože `Employee` dědí `Person`.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Použití delegátů s parametry kontravariantního typu  
 Následující příklad ukazuje výhody podpory kontravariance v Obecné `Action` delegátů. `AddToContacts` Metoda přijímá parametr `Person` typu. Však můžete přiřadit tuto metodu za účelem `Action(Of Employee)` delegáta, protože `Employee` dědí `Person`.  
  
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
- [Obecné typy](~/docs/standard/generics/index.md)
