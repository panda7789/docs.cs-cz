---
title: "Postupy: Analýza řetězců využívajících String.Split (Průvodce C#)"
description: "String.Split vrací pole řetězců rozdělení ze sady oddělovače. Je snadný způsob, jak analyzovat řetězce."
ms.date: 01/03/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
author: BillWagner
ms.author: wiwagn
ms.custom: mvc
ms.openlocfilehash: afaff6f81a1a4240214f738d0fc9f3bafdaf868c
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="96ee7-104">Postupy: Analýza řetězců využívajících String.Split (Průvodce C#)</span><span class="sxs-lookup"><span data-stu-id="96ee7-104">How to: Parse Strings Using String.Split (C# Guide)</span></span>

<span data-ttu-id="96ee7-105"><xref:System.String.Split%2A?displayProperty=nameWithType> Metoda vytvoří pole podřetězců rozdělením vstupní řetězec založený na jeden nebo více oddělovače.</span><span class="sxs-lookup"><span data-stu-id="96ee7-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="96ee7-106">Často je nejjednodušší způsob, jak jednotlivé řetězec na hranicích aplikace word.</span><span class="sxs-lookup"><span data-stu-id="96ee7-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="96ee7-107">Slouží také k rozdělení řetězců na jiné zvláštní znaky nebo řetězce.</span><span class="sxs-lookup"><span data-stu-id="96ee7-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="96ee7-108">Následující kód rozdělí běžné slovní spojení na pole řetězců pro každou aplikaci word.</span><span class="sxs-lookup"><span data-stu-id="96ee7-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="96ee7-109">Všechny instance oddělovací znak slouží k vytvoření hodnoty v poli vráceném.</span><span class="sxs-lookup"><span data-stu-id="96ee7-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="96ee7-110">Po sobě jdoucí oddělovače vytvořit prázdný řetězec jako hodnotu v poli vráceném.</span><span class="sxs-lookup"><span data-stu-id="96ee7-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="96ee7-111">Můžete to vidět v následujícím příkladu, který používá jako oddělovač místa:</span><span class="sxs-lookup"><span data-stu-id="96ee7-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="96ee7-112">Toto chování usnadňuje formáty stejně jako soubory s hodnotami (CSV) oddělený čárkami představující tabulková data.</span><span class="sxs-lookup"><span data-stu-id="96ee7-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="96ee7-113">Po sobě jdoucích čárkami představují sloupec je prázdný.</span><span class="sxs-lookup"><span data-stu-id="96ee7-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="96ee7-114">Abyste mohli předávat volitelný <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr vyloučit všechny prázdné řetězce v poli vráceném.</span><span class="sxs-lookup"><span data-stu-id="96ee7-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="96ee7-115">Pro složitější zpracování vrácená kolekce, můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s pořadí výsledek.</span><span class="sxs-lookup"><span data-stu-id="96ee7-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>    

<span data-ttu-id="96ee7-116"><xref:System.String.Split%2A?displayProperty=nameWithType> můžete použít více znaků oddělovače.</span><span class="sxs-lookup"><span data-stu-id="96ee7-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span> <span data-ttu-id="96ee7-117">Následující příklad používá mezery, čárky, tečky, dvojtečky a karty, všechny předané pole obsahující tyto oddělení znaky, na <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="96ee7-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="96ee7-118">Smyčky v dolní části kód zobrazí každý slova v poli vráceném.</span><span class="sxs-lookup"><span data-stu-id="96ee7-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="96ee7-119">Po sobě jdoucích instancí všechny oddělovače způsobit prázdný řetězec v poli výstup:</span><span class="sxs-lookup"><span data-stu-id="96ee7-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="96ee7-120"><xref:System.String.Split%2A?displayProperty=nameWithType> může trvat pole řetězců (sekvence znaků, které se chovají jako oddělovače pro potřeby analýzy cíl řetězce, místo jedné znaků).</span><span class="sxs-lookup"><span data-stu-id="96ee7-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="96ee7-121">Tyto ukázky můžete zkusit prohlížením kódu v našem [úložiště GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="96ee7-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="96ee7-122">Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="96ee7-122">Or you can download the samples [as a zip file](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="96ee7-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="96ee7-123">See Also</span></span>  
 [<span data-ttu-id="96ee7-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="96ee7-124">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="96ee7-125">Řetězce</span><span class="sxs-lookup"><span data-stu-id="96ee7-125">Strings</span></span>](../programming-guide/strings/index.md)  
 [<span data-ttu-id="96ee7-126">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="96ee7-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
