---
title: Jak dotaz na věty, které obsahují zadanou sadu slov (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: df279f57d9965d796397cbcf7a0f3ba05bf9e5c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168853"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="7ad14-102">Jak dotaz na věty, které obsahují zadanou sadu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad14-102">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>
<span data-ttu-id="7ad14-103">Tento příklad ukazuje, jak najít věty v textovém souboru, které obsahují shody pro každou zadanou sadu slov.</span><span class="sxs-lookup"><span data-stu-id="7ad14-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="7ad14-104">Přestože pole hledaných termínů je pevně zakódován v tomto příkladu, může být také naplněndynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="7ad14-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="7ad14-105">V tomto příkladu dotaz vrátí věty, které obsahují slova "Historicky", "data" a "integrované".</span><span class="sxs-lookup"><span data-stu-id="7ad14-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad14-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ad14-106">Example</span></span>  
  
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
  
 <span data-ttu-id="7ad14-107">Dotaz funguje tak, že nejprve rozdělí text na věty a potom rozdělí věty do pole řetězců, které drží každé slovo.</span><span class="sxs-lookup"><span data-stu-id="7ad14-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="7ad14-108">Pro každé z těchto <xref:System.Linq.Enumerable.Distinct%2A> polí metoda odebere všechna duplicitní slova <xref:System.Linq.Enumerable.Intersect%2A> a pak dotaz `wordsToMatch` provede operaci na pole slov a pole.</span><span class="sxs-lookup"><span data-stu-id="7ad14-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="7ad14-109">Pokud je počet průsečíku stejný jako `wordsToMatch` počet pole, všechna slova byla nalezena ve slovech a původní věta je vrácena.</span><span class="sxs-lookup"><span data-stu-id="7ad14-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="7ad14-110">Ve volání <xref:System.String.Split%2A>na , interpunkční znaménka se používají jako oddělovače k jejich odstranění z řetězce.</span><span class="sxs-lookup"><span data-stu-id="7ad14-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="7ad14-111">Pokud jste tak neučinili, například můžete mít řetězec "Historicky", který `wordsToMatch` by se neshoduje "Historicky" v poli.</span><span class="sxs-lookup"><span data-stu-id="7ad14-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="7ad14-112">V závislosti na typech interpunkce, které se nacházejí ve zdrojovém textu, bude pravděpodobně pravděpodobně třeba použít další oddělovače.</span><span class="sxs-lookup"><span data-stu-id="7ad14-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7ad14-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7ad14-113">Compiling the Code</span></span>  
<span data-ttu-id="7ad14-114">Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="7ad14-114">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ad14-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ad14-115">See also</span></span>

- [<span data-ttu-id="7ad14-116">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="7ad14-116">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
