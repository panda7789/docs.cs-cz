---
title: Použití odchylky pro obecné delegáty Func a Action (C#)
description: Přečtěte si, jak pomocí kovariance a kontravariance v obecných delegátech Func a Action získat větší flexibilitu v kódu.
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: d7174b0f734d10ab69d0936cb5ca4aa2f4fafdf7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105705"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Použití odchylky pro obecné delegáty Func a Action (C#)
Tyto příklady ukazují, jak použít kovarianci a kontravariance v `Func` `Action` obecných delegátech a umožnit opakované použití metod a zajištění větší flexibility v kódu.  
  
 Další informace o kovarianci a kontravariance naleznete v tématu [Variance v delegátech (C#)](./variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Použití delegátů s parametry kovariantního typu  
 Následující příklad znázorňuje výhody kovariance v obecných `Func` delegátech. `FindByTitle`Metoda přebírá parametr `String` typu a vrací objekt `Employee` typu. Tuto metodu však můžete přiřadit `Func<String, Person>` delegátovi, protože `Employee` dědí `Person` .  
  
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
 Následující příklad znázorňuje výhody podpory aplikace kontravariance v obecných `Action` delegátech. `AddToContacts`Metoda přebírá parametr `Person` typu. Tuto metodu však můžete přiřadit `Action<Employee>` delegátovi, protože `Employee` dědí `Person` .  
  
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
