---
title: 'Postupy: dotazu na znaky v řetězci (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 0953ff9152a4af1aa40379e15b2279d23ad0aac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642113"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="70f9c-102">Postupy: dotazu na znaky v řetězci (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70f9c-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="70f9c-103">Protože <xref:System.String> třída implementuje obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní, může být dotazován libovolný řetězec jako posloupnosti znaků.</span><span class="sxs-lookup"><span data-stu-id="70f9c-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="70f9c-104">Je to ale není běžně se používají LINQ.</span><span class="sxs-lookup"><span data-stu-id="70f9c-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="70f9c-105">Pro komplexní vzor odpovídající operace, použijte <xref:System.Text.RegularExpressions.Regex> třídy.</span><span class="sxs-lookup"><span data-stu-id="70f9c-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70f9c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="70f9c-106">Example</span></span>  
 <span data-ttu-id="70f9c-107">V následujícím příkladu se dotazuje řetězec můžete určit počet číslic, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="70f9c-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="70f9c-108">Všimněte si, že dotaz je "opakovaně" po provedení první.</span><span class="sxs-lookup"><span data-stu-id="70f9c-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="70f9c-109">To je možné, protože samotný dotaz neukládá skutečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="70f9c-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```vb  
Class QueryAString  
  
    Shared Sub Main()  
  
        ' A string is an IEnumerable data source.  
        Dim aString As String = "ABCDE99F-J74-12-89A"  
  
        ' Select only those characters that are numbers  
        Dim stringQuery = From ch In aString   
                          Where Char.IsDigit(ch)   
                          Select ch  
        ' Execute the query  
        For Each c As Char In stringQuery  
            Console.Write(c & " ")  
        Next  
  
        ' Call the Count method on the existing query.  
        Dim count As Integer = stringQuery.Count()  
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)  
  
        ' Select all characters before the first '-'  
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")  
  
        ' Execute the second query  
        For Each ch In stringQuery2  
            Console.Write(ch)  
        Next  
  
        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 9 9 7 4 1 2 8 9   
' Count = 8  
' ABCDE99F  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="70f9c-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="70f9c-110">Compiling the Code</span></span>  
 <span data-ttu-id="70f9c-111">Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="70f9c-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f9c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="70f9c-112">See Also</span></span>  
 [<span data-ttu-id="70f9c-113">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70f9c-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="70f9c-114">Postupy: kombinace dotazů LINQ s regulárními výrazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70f9c-114">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
