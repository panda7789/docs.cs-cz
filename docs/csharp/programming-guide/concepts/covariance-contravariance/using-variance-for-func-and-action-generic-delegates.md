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
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="ac26c-102">Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)</span><span class="sxs-lookup"><span data-stu-id="ac26c-102">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="ac26c-103">Tyto příklady ukazují, jak používat kovariance a `Func` `Action` contravariance v a obecné delegáty povolit opakované použití metod a poskytují větší flexibilitu v kódu.</span><span class="sxs-lookup"><span data-stu-id="ac26c-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="ac26c-104">Další informace o kovariance a kontravariance naleznete [v tématu Odchylka v delegátech (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="ac26c-104">For more information about covariance and contravariance, see [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="ac26c-105">Použití delegátů s parametry kovariantního typu</span><span class="sxs-lookup"><span data-stu-id="ac26c-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="ac26c-106">Následující příklad ilustruje výhody podpory kovariance v `Func` obecných delegátech.</span><span class="sxs-lookup"><span data-stu-id="ac26c-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="ac26c-107">Metoda `FindByTitle` přebírá parametr `String` typu a vrátí objekt `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="ac26c-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="ac26c-108">Tuto metodu však můžete `Func<String, Person>` delegátovi přiřadit, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="ac26c-108">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="ac26c-109">Použití delegátů s parametry typu Contravariant</span><span class="sxs-lookup"><span data-stu-id="ac26c-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="ac26c-110">Následující příklad ilustruje výhody podpory contravariance v `Action` obecných delegátech.</span><span class="sxs-lookup"><span data-stu-id="ac26c-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="ac26c-111">Metoda `AddToContacts` přebírá parametr `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="ac26c-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="ac26c-112">Tuto metodu však můžete `Action<Employee>` delegátovi přiřadit, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="ac26c-112">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac26c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac26c-113">See also</span></span>

- [<span data-ttu-id="ac26c-114">Kovariance a kontravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="ac26c-114">Covariance and Contravariance (C#)</span></span>](./index.md)
- [<span data-ttu-id="ac26c-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="ac26c-115">Generics</span></span>](../../../../standard/generics/index.md)
