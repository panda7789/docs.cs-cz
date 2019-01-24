---
title: Použití odchylek pro delegáty Func a Action obecný (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: f517eea07588bb01ef903c8311126eab872bd735
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540595"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Použití odchylek pro delegáty Func a Action obecný (C#)
Tyto příklady ukazují, jak používat kovariance a kontravariance v `Func` a `Action` obecné delegáty umožňují opakované použití metod a poskytují větší flexibilitu v kódu.  
  
 Další informace o kovarianci a kontravarianci naleznete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Použití delegátů parametry kovariantního typu  
 Následující příklad ukazuje výhody podpory Kovariance v Obecné `Func` delegátů. `FindByTitle` Metoda přijímá parametr `String` typ a vrátí objekt `Employee` typu. Však můžete přiřadit tuto metodu za účelem `Func<String, Person>` delegáta, protože `Employee` dědí `Person`.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Použití delegátů s parametry kontravariantního typu  
 Následující příklad ukazuje výhody podpory kontravariance v Obecné `Action` delegátů. `AddToContacts` Metoda přijímá parametr `Person` typu. Však můžete přiřadit tuto metodu za účelem `Action<Employee>` delegáta, protože `Employee` dědí `Person`.  
  
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

- [Kovariance a kontravariance (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Obecné typy](~/docs/standard/generics/index.md)
