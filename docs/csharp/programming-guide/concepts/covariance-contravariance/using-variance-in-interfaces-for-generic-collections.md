---
title: Použití variance v rozhraních pro obecné kolekce (C#)
description: Naučte se používat kovariantní a kontravariantní rozhraní pro obecné kolekce. Podívejte se na příklady převodu a porovnání obecných kolekcí.
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: c2ce849e32520cb91422ff36173e418a010476bd
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105672"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="31027-104">Použití variance v rozhraních pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="31027-104">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="31027-105">Kovariantní rozhraní umožňuje svým metodám vracet více odvozených typů než ty, které jsou zadány v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="31027-105">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="31027-106">Kontravariantní rozhraní umožňuje jeho metodám přijímat parametry méně odvozených typů než těch, které jsou zadány v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="31027-106">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="31027-107">V .NET Framework 4 se několik stávajících rozhraní stala kovariantou a kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="31027-107">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="31027-108">Mezi ně patří <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> .</span><span class="sxs-lookup"><span data-stu-id="31027-108">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="31027-109">To umožňuje znovu použít metody, které pracují s obecnými kolekcemi základních typů pro kolekce odvozených typů.</span><span class="sxs-lookup"><span data-stu-id="31027-109">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="31027-110">Seznam rozhraní variant v rozhraní .NET najdete v tématu [Variance v obecných rozhraních (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="31027-110">For a list of variant interfaces in .NET, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="31027-111">Převod obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="31027-111">Converting Generic Collections</span></span>  
 <span data-ttu-id="31027-112">Následující příklad ukazuje výhody kovariance v <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="31027-112">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="31027-113">`PrintFullName`Metoda přijímá kolekci `IEnumerable<Person>` typu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="31027-113">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="31027-114">Můžete ji však znovu použít pro kolekci `IEnumerable<Employee>` typu, protože `Employee` dědí `Person` .</span><span class="sxs-lookup"><span data-stu-id="31027-114">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="31027-115">Porovnání obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="31027-115">Comparing Generic Collections</span></span>  
 <span data-ttu-id="31027-116">Následující příklad znázorňuje výhody podpory aplikace kontravariance v <xref:System.Collections.Generic.IComparer%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="31027-116">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="31027-117">Třída `PersonComparer` implementuje rozhraní `IComparer<Person>`.</span><span class="sxs-lookup"><span data-stu-id="31027-117">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="31027-118">Tuto třídu však můžete použít k porovnání sekvence objektů `Employee` typu, protože `Employee` dědí `Person` .</span><span class="sxs-lookup"><span data-stu-id="31027-118">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31027-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="31027-119">See also</span></span>

- [<span data-ttu-id="31027-120">Variance v obecných rozhraních (C#)</span><span class="sxs-lookup"><span data-stu-id="31027-120">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
