---
title: Dotazování na věty, které obsahují zadanou sadu slov (LINQ) (C#)
description: Naučte se používat LINQ v jazyce C# k nalezení vět v textovém souboru, které obsahují shody pro každou sadu slov, která by mohla být naplněna za běhu.
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: c334c7948f19fb857709ff04a83e1dae56fc69da
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104520"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Dotazování na věty, které obsahují zadanou sadu slov (LINQ) (C#)
Tento příklad ukazuje, jak najít věty v textovém souboru, které obsahují shody pro každou zadanou sadu slov. I když je pole hledaných výrazů pevně zakódované v tomto příkladu, mohlo by být také dynamicky vyplněno za běhu. V tomto příkladu dotaz vrátí věty, které obsahují slova "historicky", "" data "a" integrovaná ".  
  
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
  
 Dotaz funguje tak, že nejprve rozdělí text na věty a pak rozdělíte věty na pole řetězců, které obsahují jednotlivá slova. Pro každé z těchto polí <xref:System.Linq.Enumerable.Distinct%2A> Metoda odstraní všechna duplicitní slova a pak dotaz provede <xref:System.Linq.Enumerable.Intersect%2A> operaci na poli slov a v `wordsToMatch` poli. Pokud je počet průniku stejný jako počet `wordsToMatch` polí, všechna slova byla nalezena v slovech a původní věta je vrácena.  
  
 V volání do <xref:System.String.Split%2A> jsou interpunkční znaménka použita jako oddělovače, aby je bylo možné odebrat z řetězce. Pokud jste to nevytvořili, například byste mohli mít řetězec "historicky", který se neshoduje s "historicky" v poli `wordsToMatch` . Je možné, že budete muset použít další oddělovače v závislosti na typech interpunkčních znamének, které se nachází ve zdrojovém textu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.

## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
