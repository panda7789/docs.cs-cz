---
title: Jak zřetězit více řetězců (Průvodce C#)
description: Existuje několik způsobů, jak zřetězit řetězce v jazyce C#. Seznamte se s možnostmi a důvody za různými volbami.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: ef3d79c5b40d08cb76e58eba1c8831c468fd1fc0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663015"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="0c92c-104">Jak zřetězit více řetězců (Průvodce C#)</span><span class="sxs-lookup"><span data-stu-id="0c92c-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="0c92c-105">*Zřetězení* je proces připojení jednoho řetězce na konec jiného řetězce.</span><span class="sxs-lookup"><span data-stu-id="0c92c-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="0c92c-106">Řetězení řetězců pomocí `+` operátoru.</span><span class="sxs-lookup"><span data-stu-id="0c92c-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="0c92c-107">Pro řetězcové literály a řetězcové konstanty probíhá zřetězení v době kompilace; nedochází k žádnému zřetězení běhu.</span><span class="sxs-lookup"><span data-stu-id="0c92c-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="0c92c-108">V případě řetězcových proměnných probíhá zřetězení pouze v době běhu.</span><span class="sxs-lookup"><span data-stu-id="0c92c-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="0c92c-109">Následující příklad používá zřetězení pro rozdělení dlouhého řetězcového literálu na menší řetězce, aby bylo možné zlepšit čitelnost ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="0c92c-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="0c92c-110">Tyto části jsou zřetězeny do jednoho řetězce v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0c92c-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="0c92c-111">Neexistují žádné náklady na výkon za běhu bez ohledu na počet zahrnutých řetězců.</span><span class="sxs-lookup"><span data-stu-id="0c92c-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet1":::

<span data-ttu-id="0c92c-112">Chcete-li zřetězit řetězcové proměnné, můžete použít `+` `+=` operátory nebo, [interpolování řetězce](../language-reference/tokens/interpolated.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType> metody, <xref:System.String.Concat%2A?displayProperty=nameWithType> <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0c92c-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="0c92c-113">`+`Operátor lze snadno použít a je určen pro intuitivní kód.</span><span class="sxs-lookup"><span data-stu-id="0c92c-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="0c92c-114">I v případě, že `+` v jednom příkazu použijete několik operátorů, je obsah řetězce zkopírován pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="0c92c-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="0c92c-115">Následující kód ukazuje příklady použití `+` `+=` operátorů a k zřetězení řetězců:</span><span class="sxs-lookup"><span data-stu-id="0c92c-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet2":::

<span data-ttu-id="0c92c-116">V některých výrazech je snazší zřetězit řetězce pomocí interpolace řetězců, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="0c92c-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet3":::

> [!NOTE]
> <span data-ttu-id="0c92c-117">V operacích zřetězení řetězců kompilátor jazyka C# zpracuje řetězec null stejný jako prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="0c92c-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="0c92c-118">Jinou metodou zřetězení řetězců je <xref:System.String.Format%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0c92c-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0c92c-119">Tato metoda funguje dobře při sestavování řetězce z malého počtu řetězců komponent.</span><span class="sxs-lookup"><span data-stu-id="0c92c-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="0c92c-120">V jiných případech může být kombinování řetězců ve smyčce, kde nevíte, kolik zdrojových řetězců se zkombinujete, a skutečný počet zdrojových řetězců může být velký.</span><span class="sxs-lookup"><span data-stu-id="0c92c-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="0c92c-121"><xref:System.Text.StringBuilder>Třída byla navržena pro tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="0c92c-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="0c92c-122">Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy pro zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="0c92c-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet4":::

<span data-ttu-id="0c92c-123">Můžete si přečíst další informace o [důvodech pro výběr zřetězení řetězců nebo `StringBuilder` třídy](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).</span><span class="sxs-lookup"><span data-stu-id="0c92c-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).</span></span>

<span data-ttu-id="0c92c-124">Další možností připojení řetězců z kolekce je použití <xref:System.String.Concat%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0c92c-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0c92c-125">Použijte <xref:System.String.Join%2A?displayProperty=nameWithType> metodu, pokud mají být zdrojové řetězce odděleny oddělovačem.</span><span class="sxs-lookup"><span data-stu-id="0c92c-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="0c92c-126">Následující kód kombinuje pole slov pomocí obou metod:</span><span class="sxs-lookup"><span data-stu-id="0c92c-126">The following code combines an array of words using both methods:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet5":::

<span data-ttu-id="0c92c-127">V poslední době můžete [LINQ](../programming-guide/concepts/linq/index.md) <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> k připojení řetězců z kolekce použít LINQ a metodu.</span><span class="sxs-lookup"><span data-stu-id="0c92c-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="0c92c-128">Tato metoda kombinuje zdrojové řetězce pomocí výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="0c92c-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="0c92c-129">Výraz lambda dokončí práci pro přidání každého řetězce do stávajícího akumulace.</span><span class="sxs-lookup"><span data-stu-id="0c92c-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="0c92c-130">Následující příklad kombinuje pole slov přidáním mezery mezi jednotlivá slova v poli:</span><span class="sxs-lookup"><span data-stu-id="0c92c-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet6":::

## <a name="see-also"></a><span data-ttu-id="0c92c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c92c-131">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="0c92c-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="0c92c-132">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="0c92c-133">Řetězce</span><span class="sxs-lookup"><span data-stu-id="0c92c-133">Strings</span></span>](../programming-guide/strings/index.md)
