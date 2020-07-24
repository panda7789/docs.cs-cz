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
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Použití variance v rozhraních pro obecné kolekce (C#)
Kovariantní rozhraní umožňuje svým metodám vracet více odvozených typů než ty, které jsou zadány v rozhraní. Kontravariantní rozhraní umožňuje jeho metodám přijímat parametry méně odvozených typů než těch, které jsou zadány v rozhraní.  
  
 V .NET Framework 4 se několik stávajících rozhraní stala kovariantou a kontravariantní. Mezi ně patří <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> . To umožňuje znovu použít metody, které pracují s obecnými kolekcemi základních typů pro kolekce odvozených typů.  
  
 Seznam rozhraní variant v rozhraní .NET najdete v tématu [Variance v obecných rozhraních (C#)](./variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Převod obecných kolekcí  
 Následující příklad ukazuje výhody kovariance v <xref:System.Collections.Generic.IEnumerable%601> rozhraní. `PrintFullName`Metoda přijímá kolekci `IEnumerable<Person>` typu jako parametr. Můžete ji však znovu použít pro kolekci `IEnumerable<Employee>` typu, protože `Employee` dědí `Person` .  
  
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
 Následující příklad znázorňuje výhody podpory aplikace kontravariance v <xref:System.Collections.Generic.IComparer%601> rozhraní. Třída `PersonComparer` implementuje rozhraní `IComparer<Person>`. Tuto třídu však můžete použít k porovnání sekvence objektů `Employee` typu, protože `Employee` dědí `Person` .  
  
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

- [Variance v obecných rozhraních (C#)](./variance-in-generic-interfaces.md)
