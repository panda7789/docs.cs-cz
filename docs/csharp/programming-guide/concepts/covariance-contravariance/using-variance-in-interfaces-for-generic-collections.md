---
title: "Použití odchylky v rozhraní pro obecné kolekce (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: be04b5c07eaf80058153a6e3866d405f48cea4e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="90b7d-102">Použití odchylky v rozhraní pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="90b7d-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="90b7d-103">Kovariantní rozhraní, které umožňuje její metody vrátit více odvozené typy než ty, zadaný v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90b7d-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="90b7d-104">Kontravariant rozhraní, které umožňuje její metody tak, aby přijímal parametry menší odvozené typy než platformám zadaným v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90b7d-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="90b7d-105">V rozhraní .NET Framework 4, stala kovariantní několik existujících rozhraní a kontravariant.</span><span class="sxs-lookup"><span data-stu-id="90b7d-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="90b7d-106">Mezi ně patří <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="90b7d-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="90b7d-107">Umožňuje znovu použít metody, které budou pracovat s obecné kolekce základních typů pro kolekce odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="90b7d-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="90b7d-108">Seznam variantních rozhraní v rozhraní .NET Framework, naleznete v části [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="90b7d-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="90b7d-109">Převádění obecné kolekce</span><span class="sxs-lookup"><span data-stu-id="90b7d-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="90b7d-110">Následující příklad ilustruje výhod kovariance podporu <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90b7d-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="90b7d-111">`PrintFullName` Metoda přijímá kolekce `IEnumerable<Person>` typ jako parametr.</span><span class="sxs-lookup"><span data-stu-id="90b7d-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="90b7d-112">Ale můžete použít pro kolekci `IEnumerable<Employee>` typu, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="90b7d-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,   
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="90b7d-113">Porovnání obecné kolekce</span><span class="sxs-lookup"><span data-stu-id="90b7d-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="90b7d-114">Následující příklad ilustruje výhod kontravariance podporu <xref:System.Collections.Generic.IComparer%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90b7d-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="90b7d-115">`PersonComparer` Třída implementuje `IComparer<Person>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90b7d-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="90b7d-116">Však můžete znovu použít tuto třídu k porovnání posloupnost objekty `Employee` typu, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="90b7d-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {              
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;              
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,   
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="90b7d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="90b7d-117">See Also</span></span>  
 [<span data-ttu-id="90b7d-118">Odchylky obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="90b7d-118">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
