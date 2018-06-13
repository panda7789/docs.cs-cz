---
title: 'Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: 77ff74788adddcd28e23028b034cd682f2d94233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641234"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a><span data-ttu-id="2fd91-102">Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fd91-102">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="2fd91-103">Tento příklad ukazuje, jak používat k porovnání dvou seznamů řetězců a výstupní tyto řádky, které jsou v names1.txt, ale není v names2.txt LINQ.</span><span class="sxs-lookup"><span data-stu-id="2fd91-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="2fd91-104">K vytvoření datových souborů</span><span class="sxs-lookup"><span data-stu-id="2fd91-104">To create the data files</span></span>  
  
1.  <span data-ttu-id="2fd91-105">Zkopírování names1.txt a names2.txt do složky řešení, jak je znázorněno v [postupy: kombinace a porovnávání řetězec kolekcí (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="2fd91-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fd91-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fd91-106">Example</span></span>  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 <span data-ttu-id="2fd91-107">Některé typy dotaz operací v jazyce Visual Basic, jako například <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, a <xref:System.Linq.Enumerable.Concat%2A>, lze vyjádřit pouze v na základě metod syntaxi.</span><span class="sxs-lookup"><span data-stu-id="2fd91-107">Some types of query operations in Visual Basic, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2fd91-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2fd91-108">Compiling the Code</span></span>  
 <span data-ttu-id="2fd91-109">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="2fd91-109">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd91-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fd91-110">See Also</span></span>  
 [<span data-ttu-id="2fd91-111">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fd91-111">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
