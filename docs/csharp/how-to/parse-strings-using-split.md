---
title: Jak analyzovat řetězce pomocí String. Split (C# vodítko)
description: String. Split vrátí pole řetězců rozdělené ze sady oddělovačů. Je to snadný způsob, jak analyzovat řetězce.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973224"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="0c9fa-104">Jak analyzovat řetězce pomocí String. Split (C# vodítko)</span><span class="sxs-lookup"><span data-stu-id="0c9fa-104">How to parse strings using String.Split (C# Guide)</span></span>

<span data-ttu-id="0c9fa-105">Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> vytvoří pole podřetězců rozdělením vstupního řetězce na základě jednoho nebo více oddělovačů.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="0c9fa-106">Je často nejjednodušší způsob, jak oddělit řetězec na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="0c9fa-107">Používá se také k rozdělení řetězců na jiné konkrétní znaky nebo řetězce.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="0c9fa-108">Následující kód rozdělí společnou frázi na pole řetězců pro každé slovo.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="0c9fa-109">Každá instance znaku oddělovače vytvoří hodnotu ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="0c9fa-110">Po sobě jdoucí oddělovací znaky vytvoří prázdný řetězec jako hodnotu ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="0c9fa-111">Můžete to vidět v následujícím příkladu, který jako oddělovač používá místo:</span><span class="sxs-lookup"><span data-stu-id="0c9fa-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="0c9fa-112">Toto chování usnadňuje formátování, jako jsou soubory s hodnotami oddělenými čárkou (CSV), které představují tabulková data.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="0c9fa-113">Po sobě jdoucí čárky představuje prázdný sloupec.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="0c9fa-114">Můžete předat volitelný <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr pro vyloučení prázdných řetězců ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="0c9fa-115">Pro složitější zpracování vrácené kolekce můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s pořadím výsledků.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="0c9fa-116"><xref:System.String.Split%2A?displayProperty=nameWithType> může použít více znaků oddělovače.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="0c9fa-117">Následující příklad používá mezery, čárky, tečky, dvojtečky a tabulátory, všechny předané v poli, které obsahuje tyto dělicí znaky, k <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="0c9fa-118">Smyčka v dolní části kódu zobrazí všechna slova ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="0c9fa-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="0c9fa-119">Po sobě jdoucí instance libovolného oddělovače vyprodukuje prázdný řetězec v výstupním poli:</span><span class="sxs-lookup"><span data-stu-id="0c9fa-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="0c9fa-120"><xref:System.String.Split%2A?displayProperty=nameWithType> může převzít pole řetězců (sekvence znaků, které fungují jako oddělovače pro analýzu cílového řetězce místo jednotlivých znaků).</span><span class="sxs-lookup"><span data-stu-id="0c9fa-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="0c9fa-121">Tyto ukázky můžete vyzkoušet na základě kódu v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="0c9fa-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="0c9fa-122">Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="0c9fa-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c9fa-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c9fa-123">See also</span></span>

- [<span data-ttu-id="0c9fa-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0c9fa-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="0c9fa-125">Řetězce</span><span class="sxs-lookup"><span data-stu-id="0c9fa-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="0c9fa-126">Regulární výrazy .NET</span><span class="sxs-lookup"><span data-stu-id="0c9fa-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
