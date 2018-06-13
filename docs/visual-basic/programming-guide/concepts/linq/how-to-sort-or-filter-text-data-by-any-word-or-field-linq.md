---
title: 'Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 0e27a72fcb5789ac9a067091aeb150d33f646708
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641983"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="ef780-102">Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef780-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="ef780-103">Následující příklad ukazuje, jak k seřazení řádků strukturovaných text, například hodnot oddělených čárkami, podle libovolného pole v řádku.</span><span class="sxs-lookup"><span data-stu-id="ef780-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="ef780-104">Pole může zadat dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="ef780-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="ef780-105">Předpokládejme, že pole v scores.csv představují číslo ID Studentova, následované řadu čtyři výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="ef780-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="ef780-106">Chcete-li vytvořit soubor, který obsahuje data</span><span class="sxs-lookup"><span data-stu-id="ef780-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="ef780-107">Kopírování dat scores.csv z tématu [postupy: připojení k obsahu z odlišných typů souborů (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) a uložte ho do složky řešení.</span><span class="sxs-lookup"><span data-stu-id="ef780-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef780-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef780-108">Example</span></span>  
  
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
  
 <span data-ttu-id="ef780-109">Tento příklad také ukazuje, jak vrátit proměnné dotazu z funkce.</span><span class="sxs-lookup"><span data-stu-id="ef780-109">This example also demonstrates how to return a query variable from a Function.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef780-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ef780-110">Compiling the Code</span></span>  
 <span data-ttu-id="ef780-111">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="ef780-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef780-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef780-112">See Also</span></span>  
 [<span data-ttu-id="ef780-113">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef780-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
