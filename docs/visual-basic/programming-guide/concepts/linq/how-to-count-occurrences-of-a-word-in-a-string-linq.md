---
title: 'Postupy: počítání výskytů slova v řetězci (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: 3a2ae52a3380e4a0d8df4adb580e84362e3f13f3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524163"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="4bf57-102">Postupy: počítání výskytů slova v řetězci (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bf57-102">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="4bf57-103">Tento příklad ukazuje, jak pomocí dotazu LINQ spočítat výskyty zadaného slova v řetězci.</span><span class="sxs-lookup"><span data-stu-id="4bf57-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="4bf57-104">Všimněte si, že k provedení tohoto počtu je nejprve volána metoda <xref:System.String.Split%2A> pro vytvoření pole slov.</span><span class="sxs-lookup"><span data-stu-id="4bf57-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="4bf57-105">Do metody <xref:System.String.Split%2A> se účtují náklady na výkon.</span><span class="sxs-lookup"><span data-stu-id="4bf57-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="4bf57-106">Pokud je jedinou operací na řetězci spočítat slova, měli byste zvážit použití metod <xref:System.Text.RegularExpressions.Regex.Matches%2A> nebo <xref:System.String.IndexOf%2A>.</span><span class="sxs-lookup"><span data-stu-id="4bf57-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="4bf57-107">Pokud ale výkon není kritickým problémem nebo jste už tuto větu rozdělili, abyste mohli provádět další typy dotazů, je vhodné použít LINQ k počítání slov nebo frází.</span><span class="sxs-lookup"><span data-stu-id="4bf57-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>

## <a name="example"></a><span data-ttu-id="4bf57-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bf57-108">Example</span></span>

```vb
Class CountWords

    Shared Sub Main()

        Dim text As String = "Historically, the world of data and the world of objects" &
                  " have not been well integrated. Programmers work in C# or Visual Basic" &
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &
                  " them. Data types often require translation between the two worlds; there are" &
                  " different standard functions. Because the object world has no notion of query, a" &
                  " query can only be represented as a string without compile-time type checking or" &
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &
                  " objects in memory is often tedious and error-prone."

        Dim searchTerm As String = "data"

        ' Convert the string into an array of words.
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},
                                                 StringSplitOptions.RemoveEmptyEntries)

        ' Create and execute the query. It executes immediately
        ' because a singleton value is produced.
        ' Use ToLower to match "data" and "Data"
        Dim matchQuery = From word In dataSource
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()
                      Select word

        ' Count the matches.
        Dim count As Integer = matchQuery.Count()
        Console.WriteLine(count & " occurrence(s) of the search term """ &
                          searchTerm & """ were found.")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 3 occurrence(s) of the search term "data" were found.
```

## <a name="compiling-the-code"></a><span data-ttu-id="4bf57-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4bf57-109">Compiling the Code</span></span>

<span data-ttu-id="4bf57-110">Vytvořte projekt konzolové aplikace VB.NET s příkazem `Imports` pro obor názvů System. Linq.</span><span class="sxs-lookup"><span data-stu-id="4bf57-110">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bf57-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bf57-111">See also</span></span>

- [<span data-ttu-id="4bf57-112">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bf57-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
