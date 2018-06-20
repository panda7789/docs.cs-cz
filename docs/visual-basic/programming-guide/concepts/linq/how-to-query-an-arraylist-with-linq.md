---
title: 'Postupy: dotazu na ArrayList pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: 24865842d073dbd4cbb60fe4a228520e98010f4d
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207242"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="c1307-102">Postupy: dotazu na ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1307-102">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>
<span data-ttu-id="c1307-103">Při použití LINQ k dotazu neobecnou <xref:System.Collections.IEnumerable> kolekcí, jako <xref:System.Collections.ArrayList>, je potřeba explicitně deklarovat druh proměnné rozsahu tak, aby odrážela konkrétní typy objektů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="c1307-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="c1307-104">Pokud máte například <xref:System.Collections.ArrayList> z `Student` objekty, vaše [klauzule From](../../../../visual-basic/language-reference/queries/from-clause.md) by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="c1307-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) should look like this:</span></span>  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 <span data-ttu-id="c1307-105">Zadáním druh proměnné rozsahu jsou přetypování jednotlivé položky <xref:System.Collections.ArrayList> k `Student`.</span><span class="sxs-lookup"><span data-stu-id="c1307-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="c1307-106">Použití proměnné explicitně typové rozsah ve výrazu dotazu je ekvivalentní volání <xref:System.Linq.Enumerable.Cast%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c1307-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="c1307-107"><xref:System.Linq.Enumerable.Cast%2A> vyvolá výjimku, pokud zadané přetypování nelze provést.</span><span class="sxs-lookup"><span data-stu-id="c1307-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="c1307-108"><xref:System.Linq.Enumerable.Cast%2A> a <xref:System.Linq.Enumerable.OfType%2A> jsou tyto dvě metody standardní – operátor dotazu, které působí na neobecnou <xref:System.Collections.IEnumerable> typy.</span><span class="sxs-lookup"><span data-stu-id="c1307-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="c1307-109">V jazyce Visual Basic, musíte explicitně zavolat <xref:System.Linq.Enumerable.Cast%2A> metoda ve zdroji dat, aby typ proměnné určitého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="c1307-109">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="c1307-110">Další informace najdete v tématu [vztahy typů v operacích dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c1307-110">For more information, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1307-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1307-111">Example</span></span>  
 <span data-ttu-id="c1307-112">Následující příklad ukazuje jednoduchý dotaz přes <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="c1307-112">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="c1307-113">Všimněte si, že tento příklad používá inicializátory objektů při volání kódu <xref:System.Collections.ArrayList.Add%2A> metoda, ale to není povinné.</span><span class="sxs-lookup"><span data-stu-id="c1307-113">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```vb  
Imports System.Collections  
Imports System.Linq  
  
Module Module1  
  
    Public Class Student  
        Public Property FirstName As String  
        Public Property LastName As String  
        Public Property Scores As Integer()  
    End Class  
  
    Sub Main()  
  
        Dim student1 As New Student With {.FirstName = "Svetlana",   
                                     .LastName = "Omelchenko",   
                                     .Scores = New Integer() {98, 92, 81, 60}}  
        Dim student2 As New Student With {.FirstName = "Claire",   
                                    .LastName = "O'Donnell",   
                                    .Scores = New Integer() {75, 84, 91, 39}}  
        Dim student3 As New Student With {.FirstName = "Cesar",   
                                    .LastName = "Garcia",   
                                    .Scores = New Integer() {97, 89, 85, 82}}  
        Dim student4 As New Student With {.FirstName = "Sven",   
                                    .LastName = "Mortensen",   
                                    .Scores = New Integer() {88, 94, 65, 91}}  
  
        Dim arrList As New ArrayList()  
        arrList.Add(student1)  
        arrList.Add(student2)  
        arrList.Add(student3)  
        arrList.Add(student4)  
  
        ' Use an explicit type for non-generic collections  
        Dim query = From student As Student In arrList   
                    Where student.Scores(0) > 95   
                    Select student  
  
        For Each student As Student In query  
            Console.WriteLine(student.LastName & ": " & student.Scores(0))  
        Next  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Module  
' Output:  
'   Omelchenko: 98  
'   Garcia: 97  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1307-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1307-114">See Also</span></span>  
 [<span data-ttu-id="c1307-115">LINQ na objekty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1307-115">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
