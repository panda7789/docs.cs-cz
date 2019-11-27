---
title: 'Postupy: Vytvoření dotazu na věty obsahující zadanou množinu slov (LINQ)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: 4a068f4f5500da5fd26e3dea753ec9591b6c7f5f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347679"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>Postupy: vytvoření dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)

Tento příklad ukazuje, jak najít věty v textovém souboru, které obsahují shody pro každou zadanou sadu slov. I když je pole hledaných výrazů pevně zakódované v tomto příkladu, mohlo by být také dynamicky vyplněno za běhu. V tomto příkladu dotaz vrátí věty, které obsahují slova "historicky", "" data "a" integrovaná ".

## <a name="example"></a>Příklad

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

Dotaz funguje tak, že nejprve rozdělí text na věty a pak rozdělíte věty na pole řetězců, které obsahují jednotlivá slova. Pro každé z těchto polí <xref:System.Linq.Enumerable.Distinct%2A> metoda odstraní všechna duplicitní slova a pak dotaz provede operaci <xref:System.Linq.Enumerable.Intersect%2A> v poli Wordu a v poli `wordsToMatch`. Pokud je počet průniku stejný jako počet `wordsToMatch`ho pole, všechna slova byla nalezena v slovech a původní věta je vrácena.

V volání <xref:System.String.Split%2A>se interpunkční znaménka používají jako oddělovače, aby je bylo možné odebrat z řetězce. Pokud jste to nevytvořili, například byste mohli mít řetězec "historicky", který se neshoduje s "historicky" v poli `wordsToMatch`. Je možné, že budete muset použít další oddělovače v závislosti na typech interpunkčních znamének, které se nachází ve zdrojovém textu.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Vytvořte projekt konzolové aplikace VB.NET s příkazem `Imports` pro obor názvů System. Linq.

## <a name="see-also"></a>Viz také:

- [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
