---
title: 'Postupy: řetězení více řetězců (Průvodce C#)'
description: Zřetězení řetězců v jazyce C# několika způsoby. Další možnosti a důvodech různé možnosti.
ms.date: 02/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 05f4932710870c26256659252fcef3814462d488
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="030cf-104">Postupy: řetězení více řetězců (Průvodce C#)</span><span class="sxs-lookup"><span data-stu-id="030cf-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="030cf-105">*Zřetězení* je proces připojování jeden řetězec na konec jiným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="030cf-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="030cf-106">Zřetězení řetězců pomocí `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="030cf-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="030cf-107">Pro textové literály a řetězcové konstanty zřetězení nastane při kompilaci; nastane, bez spuštění zřetězení.</span><span class="sxs-lookup"><span data-stu-id="030cf-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="030cf-108">Pro proměnné řetězec zřetězení dojde pouze v době běhu.</span><span class="sxs-lookup"><span data-stu-id="030cf-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="030cf-109">Následující příklad používá zřetězení rozdělením dlouhý řetězec literálu menší řetězců za účelem zlepšení čitelnosti ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="030cf-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="030cf-110">Následující části jsou zřetězeny do jednoho řetězce v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="030cf-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="030cf-111">Související se situací je bez nákladů výkon bez ohledu na počet řetězce.</span><span class="sxs-lookup"><span data-stu-id="030cf-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="030cf-112">Ke zřetězení proměnné řetězce, můžete použít `+` nebo `+=` operátory, [řetězec interpolace](../language-reference/tokens/interpolated.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="030cf-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="030cf-113">`+` Operátor se snadno používá a zajišťuje intuitivní kódu.</span><span class="sxs-lookup"><span data-stu-id="030cf-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="030cf-114">I když používáte několik `+` operátory v jednom příkazu, řetězec obsahu zkopíruje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="030cf-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="030cf-115">Následující kód ukazuje příklady použití `+` a `+=` operátory zřetězení řetězců:</span><span class="sxs-lookup"><span data-stu-id="030cf-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="030cf-116">V některých výrazy je snazší zřetězení řetězců pomocí řetězce interpolace, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="030cf-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="030cf-117">V operace s řetězci zřetězení kompilátor jazyka C# zpracovává řetězec null stejné jako prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="030cf-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="030cf-118">Jiné metody ke zřetězení řetězců je <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="030cf-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="030cf-119">Tato metoda funguje dobře, pokud vytváříte řetězec z malý počet součástí řetězce.</span><span class="sxs-lookup"><span data-stu-id="030cf-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="030cf-120">V jiných případech může být kombinovaných řetězců ve smyčce, kde nevíte, kolik řetězce zdrojů kombinujete a skutečný počet řetězce zdrojů může mít poměrně značnou.</span><span class="sxs-lookup"><span data-stu-id="030cf-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="030cf-121"><xref:System.Text.StringBuilder> Třída byl navržený pro tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="030cf-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="030cf-122">Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="030cf-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="030cf-123">Další informace o [důvodů, proč zvolit zřetězení řetězců nebo `StringBuilder` – třída](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="030cf-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="030cf-124">Další možností pro připojení řetězce z kolekce, je použít <xref:System.String.Concat%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="030cf-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="030cf-125">Použití <xref:System.String.Join%2A?displayProperty=nameWithType> metoda Pokud zdrojové řetězce musí být odděleny delimeter.</span><span class="sxs-lookup"><span data-stu-id="030cf-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="030cf-126">Následující kód kombinuje pole slov pomocí obou těchto metod:</span><span class="sxs-lookup"><span data-stu-id="030cf-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="030cf-127">V poslední, můžete použít [LINQ](../programming-guide/concepts/linq/index.md) a <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metoda připojení řetězce z kolekce.</span><span class="sxs-lookup"><span data-stu-id="030cf-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="030cf-128">Tato metoda kombinuje řetězce zdrojů pomocí výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="030cf-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="030cf-129">Výraz lambda funguje pro přidání do existující akumulace každý řetězec.</span><span class="sxs-lookup"><span data-stu-id="030cf-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="030cf-130">Následující příklad kombinuje pole slov přidáním mezery mezi jednotlivých slov v poli:</span><span class="sxs-lookup"><span data-stu-id="030cf-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="030cf-131">Tyto ukázky můžete zkusit prohlížením kódu v našem [úložiště GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="030cf-131">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="030cf-132">Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="030cf-132">Or you can download the samples [as a zip file](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="030cf-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="030cf-133">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="030cf-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="030cf-134">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="030cf-135">Řetězce</span><span class="sxs-lookup"><span data-stu-id="030cf-135">Strings</span></span>](../programming-guide/strings/index.md)
