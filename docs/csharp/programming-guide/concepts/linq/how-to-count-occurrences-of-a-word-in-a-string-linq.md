---
title: Jak spočítat výskyty slova v řetězci (LINQ) (C#)
description: Tento příklad používá dotaz LINQ v jazyce C# k výpočtu výskytů zadaného slova v řetězci. Používá metodu Split k vytvoření pole slov.
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: 1621e776510e366aa779f1d45468be34b3dec373
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103364"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a><span data-ttu-id="a5c57-104">Jak spočítat výskyty slova v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a5c57-104">How to count occurrences of a word in a string (LINQ) (C#)</span></span>
<span data-ttu-id="a5c57-105">Tento příklad ukazuje, jak pomocí dotazu LINQ spočítat výskyty zadaného slova v řetězci.</span><span class="sxs-lookup"><span data-stu-id="a5c57-105">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="a5c57-106">Všimněte si, že k provedení tohoto počtu je nejprve <xref:System.String.Split%2A> volána metoda pro vytvoření pole slov.</span><span class="sxs-lookup"><span data-stu-id="a5c57-106">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="a5c57-107">K metodě se účtují náklady na výkon <xref:System.String.Split%2A> .</span><span class="sxs-lookup"><span data-stu-id="a5c57-107">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="a5c57-108">Pokud má jediná operace v řetězci spočítat slova, měli byste zvážit <xref:System.Text.RegularExpressions.Regex.Matches%2A> <xref:System.String.IndexOf%2A> místo toho použití metod nebo.</span><span class="sxs-lookup"><span data-stu-id="a5c57-108">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="a5c57-109">Pokud ale výkon není kritickým problémem nebo jste už tuto větu rozdělili, abyste mohli provádět další typy dotazů, je vhodné použít LINQ k počítání slov nebo frází.</span><span class="sxs-lookup"><span data-stu-id="a5c57-109">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5c57-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5c57-110">Example</span></span>  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET Framework APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a5c57-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a5c57-111">Compiling the Code</span></span>  
 <span data-ttu-id="a5c57-112">Vytvořte projekt konzolové aplikace v jazyce C# se `using` direktivami pro obory názvů System. Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="a5c57-112">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c57-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5c57-113">See also</span></span>

- [<span data-ttu-id="a5c57-114">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="a5c57-114">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
