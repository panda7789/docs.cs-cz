---
title: 'Postupy: Dotazování objektu ArrayList pomocí LINQC#()'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 51c42296b8acb6be1c9c4505f9af3d6fbaf248ce
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253442"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="7cc8a-102">Postupy: Dotazování objektu ArrayList pomocí LINQC#()</span><span class="sxs-lookup"><span data-stu-id="7cc8a-102">How to: Query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="7cc8a-103">Při použití LINQ k dotazování na neobecné <xref:System.Collections.IEnumerable> kolekce <xref:System.Collections.ArrayList>, jako je například, je nutné explicitně deklarovat typ proměnné rozsahu, aby odrážel konkrétní typ objektů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7cc8a-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="7cc8a-104">Například pokud máte <xref:System.Collections.ArrayList> `Student` objekt, vaše [klauzule FROM](../../../language-reference/keywords/from-clause.md) by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7cc8a-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp  
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="7cc8a-105">Zadáním typu proměnné rozsahu budete přetypování do každé položky v poli <xref:System.Collections.ArrayList> `Student`do.</span><span class="sxs-lookup"><span data-stu-id="7cc8a-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="7cc8a-106">Použití explicitně typované proměnné rozsahu ve výrazu dotazu je ekvivalentní volání <xref:System.Linq.Enumerable.Cast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7cc8a-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="7cc8a-107"><xref:System.Linq.Enumerable.Cast%2A>vyvolá výjimku, pokud nelze provést zadané přetypování.</span><span class="sxs-lookup"><span data-stu-id="7cc8a-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="7cc8a-108"><xref:System.Linq.Enumerable.Cast%2A>a <xref:System.Linq.Enumerable.OfType%2A> jsou dvě standardní metody operátoru dotazu, které pracují s neobecnými <xref:System.Collections.IEnumerable> typy.</span><span class="sxs-lookup"><span data-stu-id="7cc8a-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="7cc8a-109">Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](./type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7cc8a-109">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cc8a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="7cc8a-110">Example</span></span>  
 <span data-ttu-id="7cc8a-111">Následující příklad ukazuje jednoduchý dotaz nad <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="7cc8a-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="7cc8a-112">Všimněte si, že tento příklad používá Inicializátory objektů, když kód <xref:System.Collections.ArrayList.Add%2A> volá metodu, ale to není požadavek.</span><span class="sxs-lookup"><span data-stu-id="7cc8a-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7cc8a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cc8a-113">See also</span></span>

- [<span data-ttu-id="7cc8a-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="7cc8a-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
