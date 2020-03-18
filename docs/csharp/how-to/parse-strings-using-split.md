---
title: Jak analyzovat řetězce pomocí String.Split (C# Guide)
description: String.Split vrátí pole řetězců rozdělených ze sady oddělovačů. Je to snadný způsob, jak analyzovat struny.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973224"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="84677-104">Jak analyzovat řetězce pomocí String.Split (C# Guide)</span><span class="sxs-lookup"><span data-stu-id="84677-104">How to parse strings using String.Split (C# Guide)</span></span>

<span data-ttu-id="84677-105">Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> vytvoří pole podřetězců rozdělením vstupního řetězce na základě jednoho nebo více oddělovačů.</span><span class="sxs-lookup"><span data-stu-id="84677-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="84677-106">Často se jedná o nejjednodušší způsob, jak oddělit řetězec na hranice slov.</span><span class="sxs-lookup"><span data-stu-id="84677-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="84677-107">Používá se také k rozdělení řetězců na jiné konkrétní znaky nebo řetězce.</span><span class="sxs-lookup"><span data-stu-id="84677-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="84677-108">Následující kód rozdělí společnou frázi do pole řetězců pro každé slovo.</span><span class="sxs-lookup"><span data-stu-id="84677-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="84677-109">Každá instance znaku oddělovače vytvoří hodnotu ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="84677-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="84677-110">Po sobě jdoucí oddělovací znaky vytvářejí prázdný řetězec jako hodnotu ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="84677-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="84677-111">To můžete vidět v následujícím příkladu, který používá mezeru jako oddělovač:</span><span class="sxs-lookup"><span data-stu-id="84677-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="84677-112">Toto chování usnadňuje formáty, jako jsou soubory csv (comma separated) představující tabulková data.</span><span class="sxs-lookup"><span data-stu-id="84677-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="84677-113">Po sobě jdoucí čárky představují prázdný sloupec.</span><span class="sxs-lookup"><span data-stu-id="84677-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="84677-114">Můžete předat volitelný <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr vyloučit všechny prázdné řetězce ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="84677-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="84677-115">Pro složitější zpracování vrácené kolekce můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s výsledkovou sekvencí.</span><span class="sxs-lookup"><span data-stu-id="84677-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="84677-116"><xref:System.String.Split%2A?displayProperty=nameWithType>můžete použít více oddělovacích znaků.</span><span class="sxs-lookup"><span data-stu-id="84677-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="84677-117">Následující příklad používá mezery, čárky, tečky, dvojtečky a tabulátory, všechny <xref:System.String.Split%2A>předané v poli obsahujícím tyto oddělující znaky do .</span><span class="sxs-lookup"><span data-stu-id="84677-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="84677-118">Smyčka v dolní části kódu zobrazí každé slovo v vrácené pole.</span><span class="sxs-lookup"><span data-stu-id="84677-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="84677-119">Po sobě jdoucí instance libovolného oddělovače vytvoří prázdný řetězec ve výstupním poli:</span><span class="sxs-lookup"><span data-stu-id="84677-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="84677-120"><xref:System.String.Split%2A?displayProperty=nameWithType>může trvat pole řetězců (sekvence znaků, které fungují jako oddělovače pro analýzu cílového řetězce, namísto jednotlivých znaků).</span><span class="sxs-lookup"><span data-stu-id="84677-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="84677-121">Tyto ukázky můžete vyzkoušet tak, že se podíváte na kód v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="84677-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="84677-122">Nebo si můžete stáhnout ukázky [jako zip soubor](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="84677-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="84677-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="84677-123">See also</span></span>

- [<span data-ttu-id="84677-124">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84677-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="84677-125">Řetězce</span><span class="sxs-lookup"><span data-stu-id="84677-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="84677-126">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="84677-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
