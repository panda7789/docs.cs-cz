---
title: 'Postupy: počítání výskytů slova v řetězci (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: 48eda99970744a659a803f52bb3a3c499390f5c8
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44352960"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a><span data-ttu-id="9c541-102">Postupy: počítání výskytů slova v řetězci (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9c541-102">How to: Count Occurrences of a Word in a String (LINQ) (C#)</span></span>
<span data-ttu-id="9c541-103">Tento příklad ukazuje, jak můžete počítat výskyty zadaného slova v řetězci dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c541-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="9c541-104">Všimněte si, že počet, nejprve provést <xref:System.String.Split%2A> metoda je volána k vytvoření pole slov.</span><span class="sxs-lookup"><span data-stu-id="9c541-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="9c541-105">Je snížení výkonu <xref:System.String.Split%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9c541-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="9c541-106">Pokud je počet slov pouze operace s řetězci, měli byste zvážit použití <xref:System.Text.RegularExpressions.Regex.Matches%2A> nebo <xref:System.String.IndexOf%2A> metody místo.</span><span class="sxs-lookup"><span data-stu-id="9c541-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="9c541-107">Ale pokud výkon není kritický problém nebo jste už rozdělili věty nad ním provádět jiné typy dotazů, pak je vhodné zprostředkovatel LINQ slouží pro počet slov nebo frází také.</span><span class="sxs-lookup"><span data-stu-id="9c541-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c541-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c541-108">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9c541-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9c541-109">Compiling the Code</span></span>  
 <span data-ttu-id="9c541-110">Vytvořit projekt, který cílí na rozhraní .NET Framework verze 3.5 nebo vyšší s odkazem na knihovnu System.Core.dll a `using` direktivy pro obory názvů System.Linq a System.IO.</span><span class="sxs-lookup"><span data-stu-id="9c541-110">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c541-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c541-111">See Also</span></span>

- [<span data-ttu-id="9c541-112">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="9c541-112">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
