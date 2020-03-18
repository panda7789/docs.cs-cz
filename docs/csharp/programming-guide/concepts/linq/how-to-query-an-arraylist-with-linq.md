---
title: Jak dotaz ArrayList s LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: fa185ba3793b628b0d65e1f513a70ec68f6f2425
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168931"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>Jak dotaz ArrayList s LINQ (C#)
Při použití LINQ dotaz <xref:System.Collections.IEnumerable> u neobecných kolekcí, jako je například <xref:System.Collections.ArrayList>, je nutné explicitně deklarovat typ proměnné rozsahu tak, aby odrážely konkrétní typ objektů v kolekci. Například pokud máte <xref:System.Collections.ArrayList> objekty, `Student` vaše [from klauzule](../../../language-reference/keywords/from-clause.md) by měla vypadat takto:  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 Zadáním typu proměnné rozsahu přetypujete každou <xref:System.Collections.ArrayList> položku `Student`v oblasti do .  
  
 Použití explicitně zadané proměnné rozsahu ve výrazu dotazu <xref:System.Linq.Enumerable.Cast%2A> je ekvivalentní volání metody. <xref:System.Linq.Enumerable.Cast%2A>vyvolá výjimku, pokud zadaný přetypový blok nelze provést. <xref:System.Linq.Enumerable.Cast%2A>a <xref:System.Linq.Enumerable.OfType%2A> jsou dvě standardní operátor dotazu metody, které pracují na neobecné <xref:System.Collections.IEnumerable> typy. Další informace naleznete [v tématu Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý dotaz <xref:System.Collections.ArrayList>přes . Všimněte si, že tento příklad používá <xref:System.Collections.ArrayList.Add%2A> inicializátory objektů při volání kódu metodu, ale to není požadavek.  
  
```csharp  
using System;  
using System.Collections;  
using System.Linq;  
  
namespace NonGenericLINQ  
{  
    public class Student  
    {  
        public string FirstName { get; set; }  
        public string LastName { get; set; }  
        public int[] Scores { get; set; }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ArrayList arrList = new ArrayList();  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Svetlana", LastName = "Omelchenko", Scores = new int[] { 98, 92, 81, 60 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Claire", LastName = "O’Donnell", Scores = new int[] { 75, 84, 91, 39 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Sven", LastName = "Mortensen", Scores = new int[] { 88, 94, 65, 91 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Cesar", LastName = "Garcia", Scores = new int[] { 97, 89, 85, 82 }  
                    });  
  
            var query = from Student student in arrList  
                        where student.Scores[0] > 95  
                        select student;  
  
            foreach (Student s in query)  
                Console.WriteLine(s.LastName + ": " + s.Scores[0]);  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
}  
/* Output:
    Omelchenko: 98  
    Garcia: 97  
*/  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ na objekty (C#)](./linq-to-objects.md)
