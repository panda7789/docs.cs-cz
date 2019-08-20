---
title: Použití odchylky pro obecné delegáty Func a ActionC#()
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 2e2c5c80c54ff6788653f63a5bda85598e73824c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595236"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Použití odchylky pro obecné delegáty Func a ActionC#()
Tyto příklady ukazují, jak použít kovarianci a kontravariance v `Func` obecných delegátech a `Action` umožnit opakované použití metod a zajištění větší flexibility v kódu.  
  
 Další informace o kovarianci a kontravariance naleznete v tématu [Variance in DelegatesC#()](./variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Použití delegátů s parametry kovariantního typu  
 Následující příklad znázorňuje výhody kovariance v obecných `Func` delegátech. Metoda přebírá parametr `String` typu a `Employee` vrací objekt typu. `FindByTitle` Tuto metodu `Func<String, Person>` však můžete přiřadit delegátovi, protože `Employee` dědí `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static Employee FindByTitle(String title)  
    {  
        // This is a stub for a method that returns  
        // an employee that has the specified title.  
        return new Employee();  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Func<String, Employee> findEmployee = FindByTitle;  
  
        // The delegate expects a method to return Person,  
        // but you can assign it a method that returns Employee.  
        Func<String, Person> findPerson = FindByTitle;  
  
        // You can also assign a delegate   
        // that returns a more derived type   
        // to a delegate that returns a less derived type.  
        findPerson = findEmployee;  
  
    }  
}  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Použití delegátů s kontravariantními parametry typu  
 Následující příklad znázorňuje výhody podpory aplikace kontravariance v obecných `Action` delegátech. Metoda přebírá parametr `Person`typu. `AddToContacts` Tuto metodu `Action<Employee>` však můžete přiřadit delegátovi, protože `Employee` dědí `Person`.  
  
```csharp  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static void AddToContacts(Person person)  
    {  
        // This method adds a Person object  
        // to a contact list.  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Action<Person> addPersonToContacts = AddToContacts;  
  
        // The Action delegate expects   
        // a method that has an Employee parameter,  
        // but you can assign it a method that has a Person parameter  
        // because Employee derives from Person.  
        Action<Employee> addEmployeeToContacts = AddToContacts;  
  
        // You can also assign a delegate   
        // that accepts a less derived parameter to a delegate   
        // that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts;  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Kovariance a kontravariance (C#)](./index.md)
- [Obecné typy](~/docs/standard/generics/index.md)
