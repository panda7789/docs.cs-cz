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
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="f72b1-102">Použití odchylky pro obecné delegáty Func a ActionC#()</span><span class="sxs-lookup"><span data-stu-id="f72b1-102">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="f72b1-103">Tyto příklady ukazují, jak použít kovarianci a kontravariance v `Func` obecných delegátech a `Action` umožnit opakované použití metod a zajištění větší flexibility v kódu.</span><span class="sxs-lookup"><span data-stu-id="f72b1-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="f72b1-104">Další informace o kovarianci a kontravariance naleznete v tématu [Variance in DelegatesC#()](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f72b1-104">For more information about covariance and contravariance, see [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="f72b1-105">Použití delegátů s parametry kovariantního typu</span><span class="sxs-lookup"><span data-stu-id="f72b1-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="f72b1-106">Následující příklad znázorňuje výhody kovariance v obecných `Func` delegátech.</span><span class="sxs-lookup"><span data-stu-id="f72b1-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="f72b1-107">Metoda přebírá parametr `String` typu a `Employee` vrací objekt typu. `FindByTitle`</span><span class="sxs-lookup"><span data-stu-id="f72b1-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="f72b1-108">Tuto metodu `Func<String, Person>` však můžete přiřadit delegátovi, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="f72b1-108">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="f72b1-109">Použití delegátů s kontravariantními parametry typu</span><span class="sxs-lookup"><span data-stu-id="f72b1-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="f72b1-110">Následující příklad znázorňuje výhody podpory aplikace kontravariance v obecných `Action` delegátech.</span><span class="sxs-lookup"><span data-stu-id="f72b1-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="f72b1-111">Metoda přebírá parametr `Person`typu. `AddToContacts`</span><span class="sxs-lookup"><span data-stu-id="f72b1-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="f72b1-112">Tuto metodu `Action<Employee>` však můžete přiřadit delegátovi, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="f72b1-112">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f72b1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f72b1-113">See also</span></span>

- [<span data-ttu-id="f72b1-114">Kovariance a kontravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="f72b1-114">Covariance and Contravariance (C#)</span></span>](./index.md)
- [<span data-ttu-id="f72b1-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="f72b1-115">Generics</span></span>](~/docs/standard/generics/index.md)
