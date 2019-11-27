---
title: 'Postupy: Vytvoření dotazu na ArrayList pomocí LINQ'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: 94a3c6d4c381f41f9ba87bf3af93261712ad1136
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347760"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="8b188-102">Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b188-102">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>

<span data-ttu-id="8b188-103">Při použití LINQ k dotazování na neobecné <xref:System.Collections.IEnumerable> kolekce, jako je například <xref:System.Collections.ArrayList>, je nutné explicitně deklarovat typ proměnné rozsahu, aby odrážel konkrétní typ objektů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="8b188-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="8b188-104">Například pokud máte <xref:System.Collections.ArrayList> objektů `Student`, [klauzule FROM](../../../../visual-basic/language-reference/queries/from-clause.md) by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="8b188-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) should look like this:</span></span>

```vb
Dim query = From student As Student In arrList
'...
```

<span data-ttu-id="8b188-105">Zadáním typu proměnné rozsahu přetypování každou položku v <xref:System.Collections.ArrayList> do `Student`.</span><span class="sxs-lookup"><span data-stu-id="8b188-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>

<span data-ttu-id="8b188-106">Použití explicitně typované proměnné rozsahu ve výrazu dotazu je ekvivalentní volání metody <xref:System.Linq.Enumerable.Cast%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b188-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="8b188-107"><xref:System.Linq.Enumerable.Cast%2A> vyvolá výjimku, pokud nelze provést zadané přetypování.</span><span class="sxs-lookup"><span data-stu-id="8b188-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="8b188-108"><xref:System.Linq.Enumerable.Cast%2A> a <xref:System.Linq.Enumerable.OfType%2A> jsou dvě standardní metody operátoru dotazu, které pracují s neobecnými typy <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="8b188-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="8b188-109">V Visual Basic musíte explicitně volat metodu <xref:System.Linq.Enumerable.Cast%2A> na zdroji dat, aby se zajistil konkrétní typ proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="8b188-109">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="8b188-110">Další informace najdete v tématu [vztahy typů v operacích dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8b188-110">For more information, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="8b188-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b188-111">Example</span></span>

<span data-ttu-id="8b188-112">Následující příklad ukazuje jednoduchý dotaz nad <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="8b188-112">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="8b188-113">Všimněte si, že tento příklad používá Inicializátory objektů, když kód volá metodu <xref:System.Collections.ArrayList.Add%2A>, ale to není požadavek.</span><span class="sxs-lookup"><span data-stu-id="8b188-113">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8b188-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b188-114">See also</span></span>

- [<span data-ttu-id="8b188-115">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b188-115">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
