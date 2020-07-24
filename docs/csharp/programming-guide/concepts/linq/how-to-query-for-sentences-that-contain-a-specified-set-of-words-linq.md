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
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="72c08-103">Dotazování na věty, které obsahují zadanou sadu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="72c08-103">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>
<span data-ttu-id="72c08-104">Tento příklad ukazuje, jak najít věty v textovém souboru, které obsahují shody pro každou zadanou sadu slov.</span><span class="sxs-lookup"><span data-stu-id="72c08-104">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="72c08-105">I když je pole hledaných výrazů pevně zakódované v tomto příkladu, mohlo by být také dynamicky vyplněno za běhu.</span><span class="sxs-lookup"><span data-stu-id="72c08-105">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="72c08-106">V tomto příkladu dotaz vrátí věty, které obsahují slova "historicky", "" data "a" integrovaná ".</span><span class="sxs-lookup"><span data-stu-id="72c08-106">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="72c08-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="72c08-107">Example</span></span>  
  
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
  
 <span data-ttu-id="72c08-108">Dotaz funguje tak, že nejprve rozdělí text na věty a pak rozdělíte věty na pole řetězců, které obsahují jednotlivá slova.</span><span class="sxs-lookup"><span data-stu-id="72c08-108">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="72c08-109">Pro každé z těchto polí <xref:System.Linq.Enumerable.Distinct%2A> Metoda odstraní všechna duplicitní slova a pak dotaz provede <xref:System.Linq.Enumerable.Intersect%2A> operaci na poli slov a v `wordsToMatch` poli.</span><span class="sxs-lookup"><span data-stu-id="72c08-109">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="72c08-110">Pokud je počet průniku stejný jako počet `wordsToMatch` polí, všechna slova byla nalezena v slovech a původní věta je vrácena.</span><span class="sxs-lookup"><span data-stu-id="72c08-110">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="72c08-111">V volání do <xref:System.String.Split%2A> jsou interpunkční znaménka použita jako oddělovače, aby je bylo možné odebrat z řetězce.</span><span class="sxs-lookup"><span data-stu-id="72c08-111">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="72c08-112">Pokud jste to nevytvořili, například byste mohli mít řetězec "historicky", který se neshoduje s "historicky" v poli `wordsToMatch` .</span><span class="sxs-lookup"><span data-stu-id="72c08-112">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="72c08-113">Je možné, že budete muset použít další oddělovače v závislosti na typech interpunkčních znamének, které se nachází ve zdrojovém textu.</span><span class="sxs-lookup"><span data-stu-id="72c08-113">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72c08-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="72c08-114">Compiling the Code</span></span>  
<span data-ttu-id="72c08-115">Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="72c08-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="72c08-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="72c08-116">See also</span></span>

- [<span data-ttu-id="72c08-117">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="72c08-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
