---
title: 'Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 46c9149a7cb1809bf94162649de0a35110bbc697
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294506"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="9581b-102">Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9581b-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="9581b-103">Následující příklad ukazuje způsob řazení řádků strukturovaných textu, jako je například textový soubor s oddělovači, podle libovolného pole v řádku.</span><span class="sxs-lookup"><span data-stu-id="9581b-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="9581b-104">Pole může být určen dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="9581b-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="9581b-105">Předpokládejme, že pole v scores.csv představují student získal identifikační číslo, za nímž následuje řadu čtyři skóre v testech.</span><span class="sxs-lookup"><span data-stu-id="9581b-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="9581b-106">Chcete-li vytvořit soubor, který obsahuje data</span><span class="sxs-lookup"><span data-stu-id="9581b-106">To create a file that contains data</span></span>  
  
1. <span data-ttu-id="9581b-107">Kopírování dat scores.csv z tématu [jak: Připojte se k obsahu z Nepodobných souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) a uloží ho do složky vašeho řešení.</span><span class="sxs-lookup"><span data-stu-id="9581b-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9581b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9581b-108">Example</span></span>  
  
```vb  
Class SortLines  
  
    Shared Sub Main()  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Change this to any value from 0 to 4  
        Dim sortField As Integer = 1  
  
        Console.WriteLine("Sorted highest to lowest by field " & sortField)  
  
        ' Demonstrates how to return query from a method.  
        ' The query is executed here.  
        For Each str As String In SortQuery(scores, sortField)  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Function SortQuery(  
        ByVal source As IEnumerable(Of String),   
        ByVal num As Integer) As IEnumerable(Of String)  
  
        Dim scoreQuery = From line In source   
                         Let fields = line.Split(New Char() {","})   
                         Order By fields(num) Descending   
                         Select line  
  
        Return scoreQuery  
    End Function  
End Class  
' Output:  
' Sorted highest to lowest by field 1  
' 116, 99, 86, 90, 94  
' 120, 99, 82, 81, 79  
' 111, 97, 92, 81, 60  
' 114, 97, 89, 85, 82  
' 121, 96, 85, 91, 60  
' 122, 94, 92, 91, 91  
' 117, 93, 92, 80, 87  
' 118, 92, 90, 83, 78  
' 113, 88, 94, 65, 91  
' 112, 75, 84, 91, 39  
' 119, 68, 79, 88, 92  
' 115, 35, 72, 91, 70  
```  
  
 <span data-ttu-id="9581b-109">Tento příklad také ukazuje, jak vrácení z funkce proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="9581b-109">This example also demonstrates how to return a query variable from a Function.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9581b-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9581b-110">Compiling the Code</span></span>  
 <span data-ttu-id="9581b-111">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="9581b-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9581b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9581b-112">See also</span></span>

- [<span data-ttu-id="9581b-113">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9581b-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
