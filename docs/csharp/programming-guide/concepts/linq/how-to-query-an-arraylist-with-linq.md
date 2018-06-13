---
title: 'Postupy: dotazu na ArrayList pomocí LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 8aaf90843fa85cf20a92a40644f085769404aa85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323232"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="e4cf7-102">Postupy: dotazu na ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="e4cf7-102">How to: Query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="e4cf7-103">Při použití LINQ k dotazu neobecnou <xref:System.Collections.IEnumerable> kolekcí, jako <xref:System.Collections.ArrayList>, je potřeba explicitně deklarovat druh proměnné rozsahu tak, aby odrážela konkrétní typy objektů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e4cf7-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="e4cf7-104">Pokud máte například <xref:System.Collections.ArrayList> z `Student` objekty, vaše [klauzule from](../../../../csharp/language-reference/keywords/from-clause.md) by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="e4cf7-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../../csharp/language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```  
var query = from Student s in arrList  
...  
```  
  
 <span data-ttu-id="e4cf7-105">Zadáním druh proměnné rozsahu jsou přetypování jednotlivé položky <xref:System.Collections.ArrayList> k `Student`.</span><span class="sxs-lookup"><span data-stu-id="e4cf7-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="e4cf7-106">Použití proměnné explicitně typové rozsah ve výrazu dotazu je ekvivalentní volání <xref:System.Linq.Enumerable.Cast%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e4cf7-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="e4cf7-107"><xref:System.Linq.Enumerable.Cast%2A> vyvolá výjimku, pokud zadané přetypování nelze provést.</span><span class="sxs-lookup"><span data-stu-id="e4cf7-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="e4cf7-108"><xref:System.Linq.Enumerable.Cast%2A> a <xref:System.Linq.Enumerable.OfType%2A> jsou tyto dvě metody standardní – operátor dotazu, které působí na neobecnou <xref:System.Collections.IEnumerable> typy.</span><span class="sxs-lookup"><span data-stu-id="e4cf7-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="e4cf7-109">Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e4cf7-109">For more information, see [Type Relationships in LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4cf7-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4cf7-110">Example</span></span>  
 <span data-ttu-id="e4cf7-111">Následující příklad ukazuje jednoduchý dotaz přes <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="e4cf7-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="e4cf7-112">Všimněte si, že tento příklad používá inicializátory objektů při volání kódu <xref:System.Collections.ArrayList.Add%2A> metoda, ale to není povinné.</span><span class="sxs-lookup"><span data-stu-id="e4cf7-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4cf7-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4cf7-113">See Also</span></span>  
 [<span data-ttu-id="e4cf7-114">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="e4cf7-114">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
