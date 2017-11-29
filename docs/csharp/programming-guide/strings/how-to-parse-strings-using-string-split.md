---
title: "Postupy: Analýza řetězců využívajících String.Split (programování průvodce v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b97d1d89a4c74a4c759d1ed41a0bc2476b3b07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a><span data-ttu-id="a6fa8-102">Postupy: Analýza řetězců využívajících String.Split (programování průvodce v C#)</span><span class="sxs-lookup"><span data-stu-id="a6fa8-102">How to: Parse Strings Using String.Split (C# Programming Guide)</span></span>
<span data-ttu-id="a6fa8-103">Následující příklad kódu ukazuje, jak může být řetězec analyzovat pomocí <xref:System.String.Split%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="a6fa8-103">The following code example demonstrates how a string can be parsed using the <xref:System.String.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a6fa8-104">Jako vstup <xref:System.String.Split%2A> přijímá pole znaků, které označují, které znaky oddělení zajímavé řetězců dílčí řetězce cíl.</span><span class="sxs-lookup"><span data-stu-id="a6fa8-104">As input, <xref:System.String.Split%2A> takes an array of characters that indicate which characters separate interesting sub strings of the target string.</span></span>  <span data-ttu-id="a6fa8-105">Funkce vrátí hodnotu pole řetězců sub.</span><span class="sxs-lookup"><span data-stu-id="a6fa8-105">The function returns an array of the sub strings.</span></span>  
  
 <span data-ttu-id="a6fa8-106">Tento příklad používá mezery, čárky, tečky, dvojtečky a karty, všechny předané pole obsahující tyto oddělení znaků, který má <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6fa8-106">This example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="a6fa8-107">Jednotlivých slov ve větě cílový řetězec zobrazí samostatně z výsledné pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="a6fa8-107">Each word in the target string's sentence displays separately from the resulting array of strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6fa8-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6fa8-108">Example</span></span>  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="a6fa8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6fa8-109">Example</span></span>  
 <span data-ttu-id="a6fa8-110">Ve výchozím nastavení vrátí String.Split prázdné řetězce, pokud dva znaky dělicí zobrazí souvisle v cílový řetězec.</span><span class="sxs-lookup"><span data-stu-id="a6fa8-110">By default, String.Split returns empty strings when two separating characters appear contiguously in the target string.</span></span>  <span data-ttu-id="a6fa8-111">Můžete předat volitelný parametr StringSplitOptions.RemoveEmptyEntries vyloučit všechny prázdné řetězce ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="a6fa8-111">You can pass an optional StringSplitOptions.RemoveEmptyEntries parameter to exclude any empty strings in the output.</span></span>  
  
 <span data-ttu-id="a6fa8-112">String.Split může trvat pole řetězců (sekvence znaků, které se chovají jako oddělovače pro potřeby analýzy cíl řetězce, místo jedné znaků).</span><span class="sxs-lookup"><span data-stu-id="a6fa8-112">String.Split can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
```csharp  
class TestStringSplit  
{  
    static void Main()  
    {  
        string[] separatingChars = { "<<", "..." };  
  
        string text = "one<<two......three<four";  
        System.Console.WriteLine("Original text: '{0}'", text);  
  
        string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries );  
        System.Console.WriteLine("{0} substrings in text:", words.Length);  
  
        foreach (string s in words)  
        {  
            System.Console.WriteLine(s);  
        }  
  
        // Keep the console window open in debug mode.  
        System.Console.WriteLine("Press any key to exit.");  
        System.Console.ReadKey();  
    }  
}  
/* Output:  
    Original text: 'one<<two......three<four'  
    3 words in text:  
    one  
    two  
    three<four  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6fa8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6fa8-113">See Also</span></span>  
 [<span data-ttu-id="a6fa8-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a6fa8-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a6fa8-115">Řetězce</span><span class="sxs-lookup"><span data-stu-id="a6fa8-115">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="a6fa8-116">Regulární výrazy rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="a6fa8-116">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)
