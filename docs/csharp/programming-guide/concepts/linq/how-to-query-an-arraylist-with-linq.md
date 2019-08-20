---
title: 'Postupy: Dotazování objektu ArrayList pomocí LINQC#()'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: dca201a23b316cc16bc746ea920303814c8c7c87
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592931"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>Postupy: Dotazování objektu ArrayList pomocí LINQC#()
Při použití LINQ k dotazování na neobecné <xref:System.Collections.IEnumerable> kolekce <xref:System.Collections.ArrayList>, jako je například, je nutné explicitně deklarovat typ proměnné rozsahu, aby odrážel konkrétní typ objektů v kolekci. Například pokud máte <xref:System.Collections.ArrayList> `Student` objekt, vaše [klauzule FROM](../../../language-reference/keywords/from-clause.md) by měla vypadat takto:  
  
```  
var query = from Student s in arrList  
...  
```  
  
 Zadáním typu proměnné rozsahu budete přetypování do každé položky v poli <xref:System.Collections.ArrayList> `Student`do.  
  
 Použití explicitně typované proměnné rozsahu ve výrazu dotazu je ekvivalentní volání <xref:System.Linq.Enumerable.Cast%2A> metody. <xref:System.Linq.Enumerable.Cast%2A>vyvolá výjimku, pokud nelze provést zadané přetypování. <xref:System.Linq.Enumerable.Cast%2A>a <xref:System.Linq.Enumerable.OfType%2A> jsou dvě standardní metody operátoru dotazu, které pracují s neobecnými <xref:System.Collections.IEnumerable> typy. Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](./type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý dotaz nad <xref:System.Collections.ArrayList>. Všimněte si, že tento příklad používá Inicializátory objektů, když kód <xref:System.Collections.ArrayList.Add%2A> volá metodu, ale to není požadavek.  
  
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

- [LINQ to Objects (C#)](./linq-to-objects.md)
