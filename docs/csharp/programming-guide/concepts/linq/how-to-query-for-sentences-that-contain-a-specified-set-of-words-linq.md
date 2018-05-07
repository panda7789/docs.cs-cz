---
title: 'Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: 736078ccf97ba3e61748932c3e48fb436b2c5564
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (C#)
Tento příklad ukazuje, jak najít věty do textového souboru, které obsahují odpovídá pro každou zadanou množinu slov. I když pole hledaných termínů je pevně zakódovaná v tomto příkladu, se může také naplnit dynamicky za běhu. V tomto příkladu dotaz vrátí věty obsahující slova "Upřednostňovala", "data" a "integrované".  
  
## <a name="example"></a>Příklad  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.   
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 Dotaz funguje tak, že nejprve rozdělení text do věty a pak do pole řetězců, které mají jednotlivých slov rozdělení věty. Pro každou z těchto polí <xref:System.Linq.Enumerable.Distinct%2A> metoda odebere všechna duplicitní slova, a potom se provede dotaz <xref:System.Linq.Enumerable.Intersect%2A> operace na pole aplikace word a `wordsToMatch` pole. Pokud počet průniku je stejný jako počet `wordsToMatch` pole, všechna slova nebyly nalezeny v slova a je vrácen původní větu.  
  
 Ve volání <xref:System.String.Split%2A>, interpunkčních znamének se používají jako oddělovače, aby bylo možné je odebrat z řetězce. Pokud není to uděláte, například můžete mít řetězec "Upřednostňovala", který by odpovídat "V minulosti" v `wordsToMatch` pole. Budete muset použít další oddělovačů, v závislosti na typech interpunkce v textu zdroj nalézt.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření projektu, jehož cílem rozhraní .NET Framework verze 3.5 nebo vyšší, s odkazem na System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také  
 [LINQ a řetězce (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
