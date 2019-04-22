---
title: 'Postupy: Dotazu na znaky v řetězci (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 3f460f635c581eef5655c5707e3dd356e7986d74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819486"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="77c6d-102">Postupy: Dotazu na znaky v řetězci (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77c6d-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="77c6d-103">Vzhledem k tomu, <xref:System.String> třída implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, libovolný řetězec může být dotázán jako posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="77c6d-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="77c6d-104">Ale to není běžné použití odkazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="77c6d-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="77c6d-105">Pro komplexní porovnávání vzorů operace, použijte <xref:System.Text.RegularExpressions.Regex> třídy.</span><span class="sxs-lookup"><span data-stu-id="77c6d-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77c6d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="77c6d-106">Example</span></span>  
 <span data-ttu-id="77c6d-107">V následujícím příkladu se dotazuje řetězec a chce určit počet číslic, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="77c6d-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="77c6d-108">Všimněte si, že dotaz je "znovu" po provedení první.</span><span class="sxs-lookup"><span data-stu-id="77c6d-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="77c6d-109">To je možné, protože samotný dotaz nejsou uložené žádné skutečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="77c6d-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="77c6d-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="77c6d-110">Compiling the Code</span></span>  
 <span data-ttu-id="77c6d-111">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.</span><span class="sxs-lookup"><span data-stu-id="77c6d-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c6d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77c6d-112">See also</span></span>

- [<span data-ttu-id="77c6d-113">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77c6d-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="77c6d-114">Postupy: Kombinace dotazů LINQ s regulárními výrazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77c6d-114">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
