---
title: Použití odchylky v rozhraní pro obecné kolekce (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 66a1eac33d5f715f52bd83c43bac4452df41aabd
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46526429"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="725fa-102">Použití odchylky v rozhraní pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="725fa-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="725fa-103">Kovariantní rozhraní umožňuje její metody k vrácení více odvozené typy než procesory zadané v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="725fa-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="725fa-104">Rozhraní kontravariantní umožňuje její metody přijímají parametry méně odvozené typy než platformám zadaným v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="725fa-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="725fa-105">V rozhraní .NET Framework 4, stala několik existujících rozhraní kovariantního a kontravariantního.</span><span class="sxs-lookup"><span data-stu-id="725fa-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="725fa-106">Patří mezi ně <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="725fa-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="725fa-107">To umožňuje znovu použít metody, které pracují s obecné kolekce základních typů pro kolekce odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="725fa-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="725fa-108">Seznam variantních rozhraní v rozhraní .NET Framework najdete v tématu [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="725fa-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="725fa-109">Převádění obecných kolekcí</span><span class="sxs-lookup"><span data-stu-id="725fa-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="725fa-110">Následující příklad ukazuje výhody podpory Kovariance v <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="725fa-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="725fa-111">`PrintFullName` Metoda přijímá kolekce `IEnumerable<Person>` typ jako parametr.</span><span class="sxs-lookup"><span data-stu-id="725fa-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="725fa-112">Ale můžete použít pro kolekce `IEnumerable<Employee>` typu, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="725fa-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="725fa-113">Porovnání obecné kolekce</span><span class="sxs-lookup"><span data-stu-id="725fa-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="725fa-114">Následující příklad ukazuje výhody podpory kontravariance v <xref:System.Collections.Generic.IComparer%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="725fa-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="725fa-115">`PersonComparer` Implementuje třída `IComparer<Person>` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="725fa-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="725fa-116">Ale můžete znovu použít tuto třídu pro porovnání sekvence objektů `Employee` typu, protože `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="725fa-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="725fa-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="725fa-117">See Also</span></span>

- [<span data-ttu-id="725fa-118">Odchylky obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="725fa-118">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
