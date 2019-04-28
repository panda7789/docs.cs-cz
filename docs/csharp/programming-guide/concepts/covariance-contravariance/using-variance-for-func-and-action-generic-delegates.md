---
title: Použití odchylek pro delegáty Func a Action obecný (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: f517eea07588bb01ef903c8311126eab872bd735
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668546"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="b1596-102">Použití odchylek pro delegáty Func a Action obecný (C#)</span><span class="sxs-lookup"><span data-stu-id="b1596-102">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="b1596-103">Tyto příklady ukazují, jak používat kovariance a kontravariance v `Func` a `Action` obecné delegáty umožňují opakované použití metod a poskytují větší flexibilitu v kódu.</span><span class="sxs-lookup"><span data-stu-id="b1596-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="b1596-104">Další informace o kovarianci a kontravarianci naleznete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b1596-104">For more information about covariance and contravariance, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="b1596-105">Použití delegátů parametry kovariantního typu</span><span class="sxs-lookup"><span data-stu-id="b1596-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="b1596-106">Následující příklad ukazuje výhody podpory Kovariance v Obecné `Func` delegátů.</span><span class="sxs-lookup"><span data-stu-id="b1596-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="b1596-107">`FindByTitle` Metoda přijímá parametr `String` typ a vrátí objekt `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="b1596-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="b1596-108">Však můžete přiřadit tuto metodu za účelem `Func<String, Person>` delegáta, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="b1596-108">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="b1596-109">Použití delegátů s parametry kontravariantního typu</span><span class="sxs-lookup"><span data-stu-id="b1596-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="b1596-110">Následující příklad ukazuje výhody podpory kontravariance v Obecné `Action` delegátů.</span><span class="sxs-lookup"><span data-stu-id="b1596-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="b1596-111">`AddToContacts` Metoda přijímá parametr `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="b1596-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="b1596-112">Však můžete přiřadit tuto metodu za účelem `Action<Employee>` delegáta, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="b1596-112">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1596-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1596-113">See also</span></span>

- [<span data-ttu-id="b1596-114">Kovariance a kontravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="b1596-114">Covariance and Contravariance (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="b1596-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="b1596-115">Generics</span></span>](~/docs/standard/generics/index.md)
