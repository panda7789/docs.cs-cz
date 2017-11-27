---
title: "Použití odchylek pro Func a akce obecní delegáti (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1b12a08579f70a07ebb90bfe723209b9f03460e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="d7716-102">Použití odchylek pro Func a akce obecní delegáti (C#)</span><span class="sxs-lookup"><span data-stu-id="d7716-102">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="d7716-103">Tyto příklady ukazují, jak používat kovariance a kontravariance v `Func` a `Action` obecní delegáti povolit opakované použití metod a poskytují větší flexibilitu v kódu.</span><span class="sxs-lookup"><span data-stu-id="d7716-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="d7716-104">Další informace o kovarianci a kontravarianci najdete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d7716-104">For more information about covariance and contravariance, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="d7716-105">Použití delegátů s kovariantní parametry typu</span><span class="sxs-lookup"><span data-stu-id="d7716-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="d7716-106">Následující příklad ilustruje výhody kovariance podpory v Obecné `Func` delegáti.</span><span class="sxs-lookup"><span data-stu-id="d7716-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="d7716-107">`FindByTitle` Metoda přebírá parametr `String` typ a vrátí objekt `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="d7716-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="d7716-108">Však můžete přiřadit tuto metodu za účelem `Func<String, Person>` delegáta, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="d7716-108">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="d7716-109">Použití delegátů pomocí parametrů typu kontravariant</span><span class="sxs-lookup"><span data-stu-id="d7716-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="d7716-110">Následující příklad ilustruje výhod podpory kontravariance v Obecné `Action` delegáti.</span><span class="sxs-lookup"><span data-stu-id="d7716-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="d7716-111">`AddToContacts` Metoda přebírá parametr `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="d7716-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="d7716-112">Však můžete přiřadit tuto metodu za účelem `Action<Employee>` delegáta, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="d7716-112">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7716-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7716-113">See Also</span></span>  
 [<span data-ttu-id="d7716-114">Kovariance a kontravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="d7716-114">Covariance and Contravariance (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="d7716-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="d7716-115">Generics</span></span>](~/docs/standard/generics/index.md)
