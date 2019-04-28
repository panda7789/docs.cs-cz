---
title: 'Postupy: Vytvoření dotazu na ArrayList pomocí LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 9276ebe02858d7a7e295430b0125c590b9c2f308
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702045"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>Postupy: Vytvoření dotazu na ArrayList pomocí LINQ (C#)
Při použití LINQ dotaz neobecnou <xref:System.Collections.IEnumerable> kolekcí, jako <xref:System.Collections.ArrayList>, musíte explicitně deklarovat typ proměnné rozsahu tak, aby odrážely konkrétní typ objektů v kolekci. Pokud máte například <xref:System.Collections.ArrayList> z `Student` objekty, vaše [klauzule from](../../../../csharp/language-reference/keywords/from-clause.md) by měl vypadat takto:  
  
```  
var query = from Student s in arrList  
...  
```  
  
 Zadáním typu proměnné rozsahu, jsou přetypování každou položku v <xref:System.Collections.ArrayList> k `Student`.  
  
 Použití explicitně rozsah proměnné ve výrazu dotazu je ekvivalentní volání <xref:System.Linq.Enumerable.Cast%2A> metody. <xref:System.Linq.Enumerable.Cast%2A> vyvolá výjimku, pokud zadané přetypování nelze provést. <xref:System.Linq.Enumerable.Cast%2A> a <xref:System.Linq.Enumerable.OfType%2A> jsou dvě metody standardního operátoru dotazu, které pracují s neobecnou <xref:System.Collections.IEnumerable> typy. Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý dotaz přes <xref:System.Collections.ArrayList>. Všimněte si, že tento příklad používá inicializátory objektů, když kód volá <xref:System.Collections.ArrayList.Add%2A> metody, ale to není povinné.  
  
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
  
## <a name="see-also"></a>Viz také:

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
