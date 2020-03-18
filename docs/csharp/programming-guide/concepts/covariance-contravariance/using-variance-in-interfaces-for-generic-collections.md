---
title: Použití odchylky v rozhraních pro obecné kolekce (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: b891ccde93e18baf5d5e814911666e9c6268e009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169737"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="96f6b-102">Použití odchylky v rozhraních pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="96f6b-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="96f6b-103">Kovariantní rozhraní umožňuje jeho metody vrátit více odvozených typů, než jsou uvedeny v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96f6b-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="96f6b-104">Rozhraní contravariant umožňuje jeho metody přijímat parametry méně odvozené typy, než jsou uvedeny v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96f6b-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="96f6b-105">V rozhraní .NET Framework 4 se několik existujících rozhraní stalo kovariantním i kontravariantními.</span><span class="sxs-lookup"><span data-stu-id="96f6b-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="96f6b-106">Patří <xref:System.Collections.Generic.IEnumerable%601> mezi <xref:System.IComparable%601>ně a .</span><span class="sxs-lookup"><span data-stu-id="96f6b-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="96f6b-107">To umožňuje znovu použít metody, které pracují s obecnými kolekcemi základních typů pro kolekce odvozených typů.</span><span class="sxs-lookup"><span data-stu-id="96f6b-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="96f6b-108">Seznam variantních rozhraní v rozhraní .NET Framework naleznete v tématu [Odchylka v obecných rozhraních (C#).](./variance-in-generic-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="96f6b-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="96f6b-109">Převod obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="96f6b-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="96f6b-110">Následující příklad ilustruje výhody podpory kovariance <xref:System.Collections.Generic.IEnumerable%601> v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96f6b-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="96f6b-111">Metoda `PrintFullName` přijímá kolekci `IEnumerable<Person>` typu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="96f6b-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="96f6b-112">Můžete jej však znovu použít pro `IEnumerable<Employee>` kolekci typu, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="96f6b-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="96f6b-113">Porovnání obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="96f6b-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="96f6b-114">Následující příklad ilustruje výhody podpory contravariance <xref:System.Collections.Generic.IComparer%601> v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96f6b-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="96f6b-115">Třída `PersonComparer` implementuje rozhraní `IComparer<Person>`.</span><span class="sxs-lookup"><span data-stu-id="96f6b-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="96f6b-116">Tuto třídu však můžete znovu použít k `Employee` porovnání `Employee` posloupnosti objektů typu, protože dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="96f6b-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96f6b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="96f6b-117">See also</span></span>

- [<span data-ttu-id="96f6b-118">Odchylka v obecných rozhraních (C#)</span><span class="sxs-lookup"><span data-stu-id="96f6b-118">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
