---
title: Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 17f55d594ad4364fd29c8f6e41bd6ad2445b0986
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169789"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)
Tyto příklady ukazují, jak používat kovariance a `Func` `Action` contravariance v a obecné delegáty povolit opakované použití metod a poskytují větší flexibilitu v kódu.  
  
 Další informace o kovariance a kontravariance naleznete [v tématu Odchylka v delegátech (C#)](./variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Použití delegátů s parametry kovariantního typu  
 Následující příklad ilustruje výhody podpory kovariance v `Func` obecných delegátech. Metoda `FindByTitle` přebírá parametr `String` typu a vrátí objekt `Employee` typu. Tuto metodu však můžete `Func<String, Person>` delegátovi přiřadit, protože `Employee` dědí `Person`.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Použití delegátů s parametry typu Contravariant  
 Následující příklad ilustruje výhody podpory contravariance v `Action` obecných delegátech. Metoda `AddToContacts` přebírá parametr `Person` typu. Tuto metodu však můžete `Action<Employee>` delegátovi přiřadit, protože `Employee` dědí `Person`.  
  
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
  
## <a name="see-also"></a>Viz také

- [Kovariance a kontravariance (C#)](./index.md)
- [Obecné typy](../../../../standard/generics/index.md)
