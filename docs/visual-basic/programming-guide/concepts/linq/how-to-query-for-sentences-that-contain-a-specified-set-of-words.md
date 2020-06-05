---
title: 'Postupy: Vytvoření dotazu na věty obsahující zadanou množinu slov (LINQ)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: ce88bf001346f90eb9b08ca1ff14afc7dcb04fa0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397957"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a><span data-ttu-id="33545-102">Postupy: vytvoření dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33545-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="33545-103">Tento příklad ukazuje, jak najít věty v textovém souboru, které obsahují shody pro každou zadanou sadu slov.</span><span class="sxs-lookup"><span data-stu-id="33545-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="33545-104">I když je pole hledaných výrazů pevně zakódované v tomto příkladu, mohlo by být také dynamicky vyplněno za běhu.</span><span class="sxs-lookup"><span data-stu-id="33545-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="33545-105">V tomto příkladu dotaz vrátí věty, které obsahují slova "historicky", "" data "a" integrovaná ".</span><span class="sxs-lookup"><span data-stu-id="33545-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>

## <a name="example"></a><span data-ttu-id="33545-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="33545-106">Example</span></span>

```vb
Class FindSentences

    Shared Sub Main()
        Dim text As String = "Historically, the world of data and the world of objects " &
        "have not been well integrated. Programmers work in C# or Visual Basic " &
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &
        "are tables, columns, rows, nodes, and separate languages for dealing with " &
        "them. Data types often require translation between the two worlds; there are " &
        "different standard functions. Because the object world has no notion of query, a " &
        "query can only be represented as a string without compile-time type checking or " &
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &
        "objects in memory is often tedious and error-prone."

        ' Split the text block into an array of sentences.
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})

        ' Define the search terms. This list could also be dynamically populated at runtime
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}

        ' Find sentences that contain all the terms in the wordsToMatch array
        ' Note that the number of terms to match is not specified at compile time
        Dim sentenceQuery = From sentence In sentences
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},
                                                   StringSplitOptions.RemoveEmptyEntries)
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()
                            Select sentence

        ' Execute the query
        For Each str As String In sentenceQuery
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Class
' Output:
' Historically, the world of data and the world of objects have not been well integrated
```

<span data-ttu-id="33545-107">Dotaz funguje tak, že nejprve rozdělí text na věty a pak rozdělíte věty na pole řetězců, které obsahují jednotlivá slova.</span><span class="sxs-lookup"><span data-stu-id="33545-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="33545-108">Pro každé z těchto polí <xref:System.Linq.Enumerable.Distinct%2A> Metoda odstraní všechna duplicitní slova a pak dotaz provede <xref:System.Linq.Enumerable.Intersect%2A> operaci na poli slov a v `wordsToMatch` poli.</span><span class="sxs-lookup"><span data-stu-id="33545-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="33545-109">Pokud je počet průniku stejný jako počet `wordsToMatch` polí, všechna slova byla nalezena v slovech a původní věta je vrácena.</span><span class="sxs-lookup"><span data-stu-id="33545-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>

<span data-ttu-id="33545-110">V volání do <xref:System.String.Split%2A> jsou interpunkční znaménka použita jako oddělovače, aby je bylo možné odebrat z řetězce.</span><span class="sxs-lookup"><span data-stu-id="33545-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="33545-111">Pokud jste to nevytvořili, například byste mohli mít řetězec "historicky", který se neshoduje s "historicky" v poli `wordsToMatch` .</span><span class="sxs-lookup"><span data-stu-id="33545-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="33545-112">Je možné, že budete muset použít další oddělovače v závislosti na typech interpunkčních znamének, které se nachází ve zdrojovém textu.</span><span class="sxs-lookup"><span data-stu-id="33545-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="33545-113">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="33545-113">Compile the code</span></span>

<span data-ttu-id="33545-114">Vytvořte projekt konzolové aplikace Visual Basic s `Imports` příkazem pro obor názvů System. Linq.</span><span class="sxs-lookup"><span data-stu-id="33545-114">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="33545-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="33545-115">See also</span></span>

- [<span data-ttu-id="33545-116">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33545-116">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
