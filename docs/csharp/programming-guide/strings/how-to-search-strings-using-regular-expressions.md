---
title: "Postupy: Vyhledávání řetězců pomocí regulárních výrazů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c851c57b44f1343816b905db002e530121fb6c0a
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a><span data-ttu-id="2453e-102">Postupy: Vyhledávání řetězců pomocí regulárních výrazů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2453e-102">How to: Search Strings Using Regular Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="2453e-103"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Třídu lze použít k vyhledání řetězců.</span><span class="sxs-lookup"><span data-stu-id="2453e-103">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="2453e-104">Tato hledání mohou být v rozsahu v složitosti od velmi jednoduché provedení úplné použití regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="2453e-104">These searches can range in complexity from very simple to making full use of regular expressions.</span></span> <span data-ttu-id="2453e-105">Následují dva příklady vyhledávání pomocí řetězce <xref:System.Text.RegularExpressions.Regex> třídy.</span><span class="sxs-lookup"><span data-stu-id="2453e-105">The following are two examples of string searching by using the <xref:System.Text.RegularExpressions.Regex> class.</span></span> <span data-ttu-id="2453e-106">Další informace najdete v tématu [regulární výrazy rozhraní .NET Framework](https://msdn.microsoft.com/library/hs600312).</span><span class="sxs-lookup"><span data-stu-id="2453e-106">For more information, see [.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2453e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2453e-107">Example</span></span>  
 <span data-ttu-id="2453e-108">Následující kód je konzolovou aplikaci, která provede jednoduché hledání bez rozlišování velikosti písmen řetězců v matici.</span><span class="sxs-lookup"><span data-stu-id="2453e-108">The following code is a console application that performs a simple case-insensitive search of the strings in an array.</span></span> <span data-ttu-id="2453e-109">Statickou metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> provede vyhledávání zadaný hledaný řetězec a řetězec, který obsahuje vzor hledání.</span><span class="sxs-lookup"><span data-stu-id="2453e-109">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search given the string to search and a string that contains the search pattern.</span></span> <span data-ttu-id="2453e-110">V takovém případě třetí argument slouží k označení, že by měl být ignoruje velikost písmen.</span><span class="sxs-lookup"><span data-stu-id="2453e-110">In this case, a third argument is used to indicate that case should be ignored.</span></span> <span data-ttu-id="2453e-111">Další informace naleznete v tématu <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2453e-111">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="2453e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2453e-112">Example</span></span>  
 <span data-ttu-id="2453e-113">Následující kód je konzolovou aplikaci, která používá regulární výrazy k ověření formát každý řetězce v matici.</span><span class="sxs-lookup"><span data-stu-id="2453e-113">The following code is a console application that uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="2453e-114">Ověření vyžaduje, aby každý řetězec mít formu telefonní číslo, ve kterém jsou tři skupiny číslic odděleny pomlčkami, první dvě skupiny obsahují tři znaky a třetí skupina obsahuje čtyři číslice.</span><span class="sxs-lookup"><span data-stu-id="2453e-114">The validation requires that each string take the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="2453e-115">To se provádí pomocí regulárního výrazu `^\\d{3}-\\d{3}-\\d{4}$`.</span><span class="sxs-lookup"><span data-stu-id="2453e-115">This is done by using the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="2453e-116">Další informace najdete v tématu [jazyk regulárních výrazů – Stručná referenční příručka](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span><span class="sxs-lookup"><span data-stu-id="2453e-116">For more information, see [Regular Expression Language - Quick Reference](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span></span>  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2453e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2453e-117">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [<span data-ttu-id="2453e-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2453e-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2453e-119">Řetězce</span><span class="sxs-lookup"><span data-stu-id="2453e-119">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="2453e-120">Regulární výrazy rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="2453e-120">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)  
 [<span data-ttu-id="2453e-121">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="2453e-121">Regular Expression Language - Quick Reference</span></span>](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
