---
title: Jak zřetězit více řetězců (Průvodce C#)
description: Existuje několik způsobů, jak zřetězit řetězce v c#. Seznamte se s možnostmi a důvody různých možností.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: bbdeba4ee3526140de29ac0d7c97e9a593729d47
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389524"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="89407-104">Jak zřetězit více řetězců (Průvodce C#)</span><span class="sxs-lookup"><span data-stu-id="89407-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="89407-105">*Zřetězení* je proces připojení jednoho řetězce na konec jiného řetězce.</span><span class="sxs-lookup"><span data-stu-id="89407-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="89407-106">Řetězce můžete zřetězit pomocí `+` operátoru.</span><span class="sxs-lookup"><span data-stu-id="89407-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="89407-107">Pro řetězcové literály a konstanty řetězců dochází k zřetězení v době kompilace; nedojde k žádnému zřetězení za běhu.</span><span class="sxs-lookup"><span data-stu-id="89407-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="89407-108">Pro proměnné řetězce dochází k zřetězení pouze za běhu.</span><span class="sxs-lookup"><span data-stu-id="89407-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="89407-109">Následující příklad používá zřetězení rozdělit dlouhý řetězec literál do menších řetězců s cílem zlepšit čitelnost ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="89407-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="89407-110">Tyto části jsou zřetězeny do jednoho řetězce v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="89407-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="89407-111">Neexistuje žádné náklady na výkon za běhu bez ohledu na počet zapojených řetězců.</span><span class="sxs-lookup"><span data-stu-id="89407-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="89407-112">Chcete-li zřetězit proměnné řetězce, `+` můžete `+=` použít operátory [nebo, interpolaci řetězce](../language-reference/tokens/interpolated.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType>metody <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="89407-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="89407-113">Obsluha `+` se snadno používá a umožňuje intuitivní kód.</span><span class="sxs-lookup"><span data-stu-id="89407-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="89407-114">I v případě, že používáte několik `+` operátorů v jednom příkazu, obsah řetězce se zkopíruje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="89407-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="89407-115">Následující kód ukazuje příklady `+` použití `+=` a operátory zřetězit řetězce:</span><span class="sxs-lookup"><span data-stu-id="89407-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="89407-116">V některých výrazech je snazší zřetězit řetězce pomocí interpolace řetězců, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="89407-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="89407-117">V operacích zřetězení řetězce kompilátor jazyka C# zachází s nulovým řetězcem stejně jako s prázdným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="89407-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="89407-118">Další metodou pro zřetězení <xref:System.String.Format%2A?displayProperty=nameWithType>řetězců je .</span><span class="sxs-lookup"><span data-stu-id="89407-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="89407-119">Tato metoda funguje dobře při vytváření řetězce z malého počtu řetězců komponent.</span><span class="sxs-lookup"><span data-stu-id="89407-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="89407-120">V ostatních případech může být kombinování řetězců ve smyčce, kde nevíte, kolik zdrojových řetězců kombinujete a skutečný počet zdrojových řetězců může být velký.</span><span class="sxs-lookup"><span data-stu-id="89407-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="89407-121">Třída <xref:System.Text.StringBuilder> byla navržena pro tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="89407-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="89407-122">Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="89407-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="89407-123">Můžete si přečíst více o [důvodech, `StringBuilder` proč zvolit zřetězení řetězců nebo třídu](xref:System.Text.StringBuilder#StringAndSB).</span><span class="sxs-lookup"><span data-stu-id="89407-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="89407-124">Další možností pro připojení řetězců z <xref:System.String.Concat%2A?displayProperty=nameWithType> kolekce je použití metody.</span><span class="sxs-lookup"><span data-stu-id="89407-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="89407-125">Metodu použijte, <xref:System.String.Join%2A?displayProperty=nameWithType> pokud by měly být zdrojové řetězce odděleny oddělovačem.</span><span class="sxs-lookup"><span data-stu-id="89407-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="89407-126">Následující kód kombinuje pole slov pomocí obou metod:</span><span class="sxs-lookup"><span data-stu-id="89407-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="89407-127">Nakonec můžete použít [LINQ](../programming-guide/concepts/linq/index.md) a <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metodu pro spojení řetězců z kolekce.</span><span class="sxs-lookup"><span data-stu-id="89407-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="89407-128">Tato metoda kombinuje zdrojové řetězce pomocí výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="89407-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="89407-129">Výraz lambda provádí práci přidat každý řetězec do existující akumulace.</span><span class="sxs-lookup"><span data-stu-id="89407-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="89407-130">Následující příklad kombinuje pole slov přidáním mezery mezi každé slovo v poli:</span><span class="sxs-lookup"><span data-stu-id="89407-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="89407-131">Tyto ukázky můžete vyzkoušet na [ukázkový kód](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="89407-131">You can try these samples by looking at the [sample code](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="89407-132">Nebo si můžete stáhnout ukázky [jako soubor zip](../../../samples/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="89407-132">Or, you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="89407-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="89407-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="89407-134">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="89407-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="89407-135">Řetězce</span><span class="sxs-lookup"><span data-stu-id="89407-135">Strings</span></span>](../programming-guide/strings/index.md)
