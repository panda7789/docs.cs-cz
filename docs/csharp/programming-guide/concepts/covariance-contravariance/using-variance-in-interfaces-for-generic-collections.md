---
title: Použití variance v rozhraních pro obecné kolekceC#()
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 53aaf49ee0802c0d207e0b0a29661cee7c628b4d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595217"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="416b3-102">Použití variance v rozhraních pro obecné kolekceC#()</span><span class="sxs-lookup"><span data-stu-id="416b3-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="416b3-103">Kovariantní rozhraní umožňuje svým metodám vracet více odvozených typů než ty, které jsou zadány v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="416b3-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="416b3-104">Kontravariantní rozhraní umožňuje jeho metodám přijímat parametry méně odvozených typů než těch, které jsou zadány v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="416b3-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="416b3-105">V .NET Framework 4 se několik stávajících rozhraní stala kovariantou a kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="416b3-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="416b3-106">Mezi ně <xref:System.Collections.Generic.IEnumerable%601> patří <xref:System.IComparable%601>a.</span><span class="sxs-lookup"><span data-stu-id="416b3-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="416b3-107">To umožňuje znovu použít metody, které pracují s obecnými kolekcemi základních typů pro kolekce odvozených typů.</span><span class="sxs-lookup"><span data-stu-id="416b3-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="416b3-108">Seznam rozhraní variant v .NET Framework naleznete v tématu [Variance in Generic InterfacesC#()](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="416b3-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="416b3-109">Převod obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="416b3-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="416b3-110">Následující příklad ukazuje výhody kovariance v <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="416b3-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="416b3-111">Metoda přijímá kolekci `IEnumerable<Person>` typu jako parametr. `PrintFullName`</span><span class="sxs-lookup"><span data-stu-id="416b3-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="416b3-112">Můžete ji však znovu použít pro kolekci `IEnumerable<Employee>` typu, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="416b3-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="416b3-113">Porovnání obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="416b3-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="416b3-114">Následující příklad znázorňuje výhody podpory aplikace kontravariance v <xref:System.Collections.Generic.IComparer%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="416b3-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="416b3-115">`PersonComparer` Třída`IComparer<Person>` implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="416b3-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="416b3-116">Tuto třídu však můžete použít k porovnání sekvence objektů `Employee` typu, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="416b3-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="416b3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="416b3-117">See also</span></span>

- [<span data-ttu-id="416b3-118">Variance v obecných rozhraníchC#()</span><span class="sxs-lookup"><span data-stu-id="416b3-118">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
