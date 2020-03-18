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
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="76e88-102">Jak dotaz ArrayList s LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="76e88-102">How to query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="76e88-103">Při použití LINQ dotaz <xref:System.Collections.IEnumerable> u neobecných kolekcí, jako je například <xref:System.Collections.ArrayList>, je nutné explicitně deklarovat typ proměnné rozsahu tak, aby odrážely konkrétní typ objektů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="76e88-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="76e88-104">Například pokud máte <xref:System.Collections.ArrayList> objekty, `Student` vaše [from klauzule](../../../language-reference/keywords/from-clause.md) by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="76e88-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="76e88-105">Zadáním typu proměnné rozsahu přetypujete každou <xref:System.Collections.ArrayList> položku `Student`v oblasti do .</span><span class="sxs-lookup"><span data-stu-id="76e88-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="76e88-106">Použití explicitně zadané proměnné rozsahu ve výrazu dotazu <xref:System.Linq.Enumerable.Cast%2A> je ekvivalentní volání metody.</span><span class="sxs-lookup"><span data-stu-id="76e88-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="76e88-107"><xref:System.Linq.Enumerable.Cast%2A>vyvolá výjimku, pokud zadaný přetypový blok nelze provést.</span><span class="sxs-lookup"><span data-stu-id="76e88-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="76e88-108"><xref:System.Linq.Enumerable.Cast%2A>a <xref:System.Linq.Enumerable.OfType%2A> jsou dvě standardní operátor dotazu metody, které pracují na neobecné <xref:System.Collections.IEnumerable> typy.</span><span class="sxs-lookup"><span data-stu-id="76e88-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="76e88-109">Další informace naleznete [v tématu Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="76e88-109">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76e88-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="76e88-110">Example</span></span>  
 <span data-ttu-id="76e88-111">Následující příklad ukazuje jednoduchý dotaz <xref:System.Collections.ArrayList>přes .</span><span class="sxs-lookup"><span data-stu-id="76e88-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="76e88-112">Všimněte si, že tento příklad používá <xref:System.Collections.ArrayList.Add%2A> inicializátory objektů při volání kódu metodu, ale to není požadavek.</span><span class="sxs-lookup"><span data-stu-id="76e88-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76e88-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="76e88-113">See also</span></span>

- [<span data-ttu-id="76e88-114">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="76e88-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
