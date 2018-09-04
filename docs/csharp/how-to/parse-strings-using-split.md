---
title: 'Postupy: Analýza řetězců metodou String.Split (Průvodce v C#)'
description: String.Split vrátí pole řetězců oddělit od sadu oddělovačů. Je snadný způsob, jak parsovat řetězce.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b6170be2dbb3f11906bbaa6e5c3be3e48a976246
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558767"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="59003-104">Postupy: Analýza řetězců metodou String.Split (Průvodce v C#)</span><span class="sxs-lookup"><span data-stu-id="59003-104">How to: Parse Strings Using String.Split (C# Guide)</span></span>

<span data-ttu-id="59003-105"><xref:System.String.Split%2A?displayProperty=nameWithType> Metoda vytvoří pole podřetězců rozdělení vstupního řetězce podle jednoho nebo více oddělovačů.</span><span class="sxs-lookup"><span data-stu-id="59003-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="59003-106">Často je nejjednodušším způsobem rozdělení řetězce na hranicích slov.</span><span class="sxs-lookup"><span data-stu-id="59003-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="59003-107">Používá se také k rozdělení řetězců na jiné určitých znaků nebo řetězce.</span><span class="sxs-lookup"><span data-stu-id="59003-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="59003-108">Následující kód rozdělí běžných frází na pole řetězců pro každé slovo.</span><span class="sxs-lookup"><span data-stu-id="59003-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="59003-109">Každá instance oddělovací znak produkuje hodnotu jako pole vrácené.</span><span class="sxs-lookup"><span data-stu-id="59003-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="59003-110">Po sobě jdoucích oddělovače vytvořit prázdný řetězec jako hodnotu jako pole vrácené.</span><span class="sxs-lookup"><span data-stu-id="59003-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="59003-111">To můžete vidět v následujícím příkladu, který se použije jako oddělovač místo:</span><span class="sxs-lookup"><span data-stu-id="59003-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="59003-112">Toto chování usnadňuje formáty jako oddělený čárkami souborů (CSV) představující tabulková data.</span><span class="sxs-lookup"><span data-stu-id="59003-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="59003-113">Po sobě jdoucích čárek představují sloupec je prázdný.</span><span class="sxs-lookup"><span data-stu-id="59003-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="59003-114">Můžete předat volitelně <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr vyloučit jakékoli prázdné řetězce vrácené jako pole.</span><span class="sxs-lookup"><span data-stu-id="59003-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="59003-115">Pro složitější zpracování vrácená kolekce, můžete použít [LINQ](../programming-guide/concepts/linq/index.md) k manipulaci s výsledkem pořadí.</span><span class="sxs-lookup"><span data-stu-id="59003-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="59003-116"><xref:System.String.Split%2A?displayProperty=nameWithType> můžete použít více znaky oddělovačů.</span><span class="sxs-lookup"><span data-stu-id="59003-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="59003-117">Následující příklad používá mezery, čárky, tečky, dvojtečky a karty, všechny předané pole obsahující tyto znaky, pro oddělení <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="59003-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="59003-118">Smyčka v dolní části kódu zobrazí jednotlivých slov v příspěvcích ve vrácené pole.</span><span class="sxs-lookup"><span data-stu-id="59003-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="59003-119">Po sobě jdoucích instancí žádné oddělovače způsobit prázdný řetězec v poli výstup:</span><span class="sxs-lookup"><span data-stu-id="59003-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="59003-120"><xref:System.String.Split%2A?displayProperty=nameWithType> může trvat pole řetězců (sekvence znaků, které se chovají jako oddělovače pro analýzu cílovém řetězci namísto jednotlivé znaky).</span><span class="sxs-lookup"><span data-stu-id="59003-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="59003-121">Tyto ukázky můžete zkusit pohledem na kód v našich [úložiště GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="59003-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="59003-122">Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="59003-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="59003-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="59003-123">See Also</span></span>

- [<span data-ttu-id="59003-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="59003-124">C# Programming Guide</span></span>](../programming-guide/index.md)  
- [<span data-ttu-id="59003-125">Řetězce</span><span class="sxs-lookup"><span data-stu-id="59003-125">Strings</span></span>](../programming-guide/strings/index.md)  
- [<span data-ttu-id="59003-126">Regulárních výrazů .NET</span><span class="sxs-lookup"><span data-stu-id="59003-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
