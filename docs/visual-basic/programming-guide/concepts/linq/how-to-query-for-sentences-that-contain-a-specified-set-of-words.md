---
title: "Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 523b1e681c97e14f1d0e49b82a426b0e0e54fa1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)
Tento příklad ukazuje, jak najít věty do textového souboru, které obsahují odpovídá pro každou zadanou množinu slov. I když pole hledaných termínů je pevně zakódovaná v tomto příkladu, se může také naplnit dynamicky za běhu. V tomto příkladu dotaz vrátí věty obsahující slova "Upřednostňovala", "data" a "integrované".  
  
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
  
 Dotaz funguje tak, že nejprve rozdělení text do věty a pak do pole řetězců, které mají jednotlivých slov rozdělení věty. Pro každou z těchto polí <xref:System.Linq.Enumerable.Distinct%2A> metoda odebere všechna duplicitní slova, a potom se provede dotaz <xref:System.Linq.Enumerable.Intersect%2A> operace na pole aplikace word a `wordsToMatch` pole. Pokud počet průniku je stejný jako počet `wordsToMatch` pole, všechna slova nebyly nalezeny v slova a je vrácen původní větu.  
  
 Ve volání <xref:System.String.Split%2A>, interpunkčních znamének se používají jako oddělovače, aby bylo možné je odebrat z řetězce. Pokud není to uděláte, například můžete mít řetězec "Upřednostňovala", který by odpovídat "V minulosti" v `wordsToMatch` pole. Budete muset použít další oddělovačů, v závislosti na typech interpunkce v textu zdroj nalézt.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na System.Core.dll a `Imports` příkaz pro obor názvů System.Linq.  
  
## <a name="see-also"></a>Viz také  
 [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
