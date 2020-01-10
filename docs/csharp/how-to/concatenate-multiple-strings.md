---
title: Jak zřetězit více řetězců (C# průvodce)
description: Existuje několik způsobů, jak zřetězit řetězce v C#. Seznamte se s možnostmi a důvody za různými volbami.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 9a0640a7ce73fa8454442cd301157bf5c265f9de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713900"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="a69c9-104">Jak zřetězit více řetězců (C# průvodce)</span><span class="sxs-lookup"><span data-stu-id="a69c9-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="a69c9-105">*Zřetězení* je proces připojení jednoho řetězce na konec jiného řetězce.</span><span class="sxs-lookup"><span data-stu-id="a69c9-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="a69c9-106">Řetězení řetězců pomocí operátoru `+`.</span><span class="sxs-lookup"><span data-stu-id="a69c9-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="a69c9-107">Pro řetězcové literály a řetězcové konstanty probíhá zřetězení v době kompilace; nedochází k žádnému zřetězení běhu.</span><span class="sxs-lookup"><span data-stu-id="a69c9-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="a69c9-108">V případě řetězcových proměnných probíhá zřetězení pouze v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a69c9-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="a69c9-109">Následující příklad používá zřetězení pro rozdělení dlouhého řetězcového literálu na menší řetězce, aby bylo možné zlepšit čitelnost ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="a69c9-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="a69c9-110">Tyto části jsou zřetězeny do jednoho řetězce v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a69c9-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="a69c9-111">Neexistují žádné náklady na výkon za běhu bez ohledu na počet zahrnutých řetězců.</span><span class="sxs-lookup"><span data-stu-id="a69c9-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="a69c9-112">Chcete-li zřetězit proměnné řetězce, můžete použít operátory `+` nebo `+=`, [interpolaci řetězců](../language-reference/tokens/interpolated.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a69c9-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="a69c9-113">Operátor `+` se snadno používá a vytváří intuitivní kód.</span><span class="sxs-lookup"><span data-stu-id="a69c9-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="a69c9-114">I v případě, že v jednom příkazu použijete několik operátorů `+`, je obsah řetězce zkopírován pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="a69c9-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="a69c9-115">Následující kód ukazuje příklady použití operátorů `+` a `+=` k zřetězení řetězců:</span><span class="sxs-lookup"><span data-stu-id="a69c9-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="a69c9-116">V některých výrazech je snazší zřetězit řetězce pomocí interpolace řetězců, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="a69c9-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="a69c9-117">V operacích zřetězení řetězců C# kompilátor zpracovává řetězec s hodnotou null stejně jako prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="a69c9-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="a69c9-118">Jinou metodou zřetězení řetězců je <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a69c9-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a69c9-119">Tato metoda funguje dobře při sestavování řetězce z malého počtu řetězců komponent.</span><span class="sxs-lookup"><span data-stu-id="a69c9-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="a69c9-120">V jiných případech může být kombinování řetězců ve smyčce, kde nevíte, kolik zdrojového řetězce se zkombinujete, a skutečný počet zdrojových řetězců může být poměrně velký.</span><span class="sxs-lookup"><span data-stu-id="a69c9-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="a69c9-121">Třída <xref:System.Text.StringBuilder> byla pro tyto scénáře navržena.</span><span class="sxs-lookup"><span data-stu-id="a69c9-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="a69c9-122">Následující kód používá metodu <xref:System.Text.StringBuilder.Append%2A> třídy <xref:System.Text.StringBuilder> k zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="a69c9-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="a69c9-123">Můžete si přečíst další informace o [důvodech pro výběr zřetězení řetězců nebo `StringBuilder` třídy](xref:System.Text.StringBuilder#StringAndSB).</span><span class="sxs-lookup"><span data-stu-id="a69c9-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="a69c9-124">Další možností připojení řetězců z kolekce je použití metody <xref:System.String.Concat%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a69c9-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a69c9-125">Použijte <xref:System.String.Join%2A?displayProperty=nameWithType> metodu, pokud by měly být zdrojové řetězce odděleny oddělovač.</span><span class="sxs-lookup"><span data-stu-id="a69c9-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="a69c9-126">Následující kód kombinuje pole slov pomocí obou metod:</span><span class="sxs-lookup"><span data-stu-id="a69c9-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="a69c9-127">V posledních, můžete použít metodu [LINQ](../programming-guide/concepts/linq/index.md) a <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> k připojení řetězců z kolekce.</span><span class="sxs-lookup"><span data-stu-id="a69c9-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="a69c9-128">Tato metoda kombinuje zdrojové řetězce pomocí výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="a69c9-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="a69c9-129">Výraz lambda dokončí práci pro přidání každého řetězce do stávajícího akumulace.</span><span class="sxs-lookup"><span data-stu-id="a69c9-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="a69c9-130">Následující příklad kombinuje pole slov přidáním mezery mezi jednotlivá slova v poli:</span><span class="sxs-lookup"><span data-stu-id="a69c9-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="a69c9-131">Tyto ukázky můžete vyzkoušet na základě kódu v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="a69c9-131">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="a69c9-132">Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="a69c9-132">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="a69c9-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a69c9-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="a69c9-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a69c9-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="a69c9-135">Řetězce</span><span class="sxs-lookup"><span data-stu-id="a69c9-135">Strings</span></span>](../programming-guide/strings/index.md)
