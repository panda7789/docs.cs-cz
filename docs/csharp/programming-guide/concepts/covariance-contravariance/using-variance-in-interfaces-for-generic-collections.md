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
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Použití odchylky v rozhraních pro obecné kolekce (C#)
Kovariantní rozhraní umožňuje jeho metody vrátit více odvozených typů, než jsou uvedeny v rozhraní. Rozhraní contravariant umožňuje jeho metody přijímat parametry méně odvozené typy, než jsou uvedeny v rozhraní.  
  
 V rozhraní .NET Framework 4 se několik existujících rozhraní stalo kovariantním i kontravariantními. Patří <xref:System.Collections.Generic.IEnumerable%601> mezi <xref:System.IComparable%601>ně a . To umožňuje znovu použít metody, které pracují s obecnými kolekcemi základních typů pro kolekce odvozených typů.  
  
 Seznam variantních rozhraní v rozhraní .NET Framework naleznete v tématu [Odchylka v obecných rozhraních (C#).](./variance-in-generic-interfaces.md)  
  
## <a name="converting-generic-collections"></a>Převod obecných kolekcí  
 Následující příklad ilustruje výhody podpory kovariance <xref:System.Collections.Generic.IEnumerable%601> v rozhraní. Metoda `PrintFullName` přijímá kolekci `IEnumerable<Person>` typu jako parametr. Můžete jej však znovu použít pro `IEnumerable<Employee>` kolekci typu, protože `Employee` dědí `Person`.  
  
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
  
## <a name="comparing-generic-collections"></a>Porovnání obecných kolekcí  
 Následující příklad ilustruje výhody podpory contravariance <xref:System.Collections.Generic.IComparer%601> v rozhraní. Třída `PersonComparer` implementuje rozhraní `IComparer<Person>`. Tuto třídu však můžete znovu použít k `Employee` porovnání `Employee` posloupnosti objektů typu, protože dědí `Person`.  
  
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
  
## <a name="see-also"></a>Viz také

- [Odchylka v obecných rozhraních (C#)](./variance-in-generic-interfaces.md)
