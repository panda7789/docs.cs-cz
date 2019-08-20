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
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Použití variance v rozhraních pro obecné kolekceC#()
Kovariantní rozhraní umožňuje svým metodám vracet více odvozených typů než ty, které jsou zadány v rozhraní. Kontravariantní rozhraní umožňuje jeho metodám přijímat parametry méně odvozených typů než těch, které jsou zadány v rozhraní.  
  
 V .NET Framework 4 se několik stávajících rozhraní stala kovariantou a kontravariantní. Mezi ně <xref:System.Collections.Generic.IEnumerable%601> patří <xref:System.IComparable%601>a. To umožňuje znovu použít metody, které pracují s obecnými kolekcemi základních typů pro kolekce odvozených typů.  
  
 Seznam rozhraní variant v .NET Framework naleznete v tématu [Variance in Generic InterfacesC#()](./variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Převod obecných kolekcí  
 Následující příklad ukazuje výhody kovariance v <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Metoda přijímá kolekci `IEnumerable<Person>` typu jako parametr. `PrintFullName` Můžete ji však znovu použít pro kolekci `IEnumerable<Employee>` typu, protože `Employee` dědí `Person`.  
  
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
 Následující příklad znázorňuje výhody podpory aplikace kontravariance v <xref:System.Collections.Generic.IComparer%601> rozhraní. `PersonComparer` Třída`IComparer<Person>` implementuje rozhraní. Tuto třídu však můžete použít k porovnání sekvence objektů `Employee` typu, protože `Employee` dědí `Person`.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Variance v obecných rozhraníchC#()](./variance-in-generic-interfaces.md)
