---
title: Analyzovat řetězce pomocí String. Split (Průvodce C#)
description: Metoda Split vrátí pole řetězců rozdělené ze sady oddělovačů. Je to snadný způsob, jak analyzovat řetězce.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 7c5d8fa462775c6f3a9981693129997dda6c2286
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324143"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a><span data-ttu-id="6e094-104">Jak analyzovat řetězce pomocí řetězce. rozdělit v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="6e094-104">How to parse strings using String.Split in C\#</span></span>

<span data-ttu-id="6e094-105"><xref:System.String.Split%2A?displayProperty=nameWithType>Metoda vytvoří pole podřetězců rozdělením vstupního řetězce na základě jednoho nebo více oddělovačů.</span><span class="sxs-lookup"><span data-stu-id="6e094-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="6e094-106">Tato metoda je často nejjednodušší způsob, jak oddělit řetězec na hranici slova.</span><span class="sxs-lookup"><span data-stu-id="6e094-106">This method is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="6e094-107">Používá se také k rozdělení řetězců na jiné konkrétní znaky nebo řetězce.</span><span class="sxs-lookup"><span data-stu-id="6e094-107">It's also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="6e094-108">Následující kód rozdělí společnou frázi na pole řetězců pro každé slovo.</span><span class="sxs-lookup"><span data-stu-id="6e094-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="6e094-109">Každá instance znaku oddělovače vytvoří hodnotu ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="6e094-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="6e094-110">Po sobě jdoucí oddělovací znaky vytvoří prázdný řetězec jako hodnotu ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="6e094-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="6e094-111">V následujícím příkladu vidíte, jak se vytvoří prázdný řetězec, který jako oddělovač používá znak mezery.</span><span class="sxs-lookup"><span data-stu-id="6e094-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="6e094-112">Toto chování usnadňuje formátování jako soubory hodnot oddělených čárkami (CSV), které představují tabulková data.</span><span class="sxs-lookup"><span data-stu-id="6e094-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="6e094-113">Po sobě jdoucí čárky představuje prázdný sloupec.</span><span class="sxs-lookup"><span data-stu-id="6e094-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="6e094-114">Můžete předat volitelný <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr pro vyloučení prázdných řetězců ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="6e094-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="6e094-115">Pro složitější zpracování vrácené kolekce můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s pořadím výsledků.</span><span class="sxs-lookup"><span data-stu-id="6e094-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="6e094-116"><xref:System.String.Split%2A?displayProperty=nameWithType>může použít více znaků oddělovače.</span><span class="sxs-lookup"><span data-stu-id="6e094-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="6e094-117">Následující příklad používá mezery, čárky, tečky, dvojtečky a tabulátory jako oddělení znaků, které jsou předány <xref:System.String.Split%2A> v poli.</span><span class="sxs-lookup"><span data-stu-id="6e094-117">The following example uses spaces, commas, periods, colons, and tabs as separating characters, which are passed to <xref:System.String.Split%2A> in an array .</span></span>
<span data-ttu-id="6e094-118">Smyčka v dolní části kódu zobrazí všechna slova ve vráceném poli.</span><span class="sxs-lookup"><span data-stu-id="6e094-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="6e094-119">Po sobě jdoucí instance libovolného oddělovače vyprodukuje prázdný řetězec v výstupním poli:</span><span class="sxs-lookup"><span data-stu-id="6e094-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="6e094-120"><xref:System.String.Split%2A?displayProperty=nameWithType>může převzít pole řetězců (sekvence znaků, které fungují jako oddělovače pro analýzu cílového řetězce místo jednotlivých znaků).</span><span class="sxs-lookup"><span data-stu-id="6e094-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="6e094-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e094-121">See also</span></span>

- [<span data-ttu-id="6e094-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6e094-122">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="6e094-123">Řetězce</span><span class="sxs-lookup"><span data-stu-id="6e094-123">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="6e094-124">Regulární výrazy .NET</span><span class="sxs-lookup"><span data-stu-id="6e094-124">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
