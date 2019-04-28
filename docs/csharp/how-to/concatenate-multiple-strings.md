---
title: 'Postupy: Řetězení více řetězců (C# průvodce)'
description: Zřetězení řetězců v jazyce C# několika způsoby. Další možnosti a důvodech různé možnosti.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: da83a79f58c236692e284a7920c7b98c3520e5d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672208"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="e78dc-104">Postupy: Řetězení více řetězců (C# průvodce)</span><span class="sxs-lookup"><span data-stu-id="e78dc-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="e78dc-105">*Zřetězení* je proces přidávání jeden řetězec na konci další řetězec.</span><span class="sxs-lookup"><span data-stu-id="e78dc-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="e78dc-106">Zřetězení řetězců s použitím `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="e78dc-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="e78dc-107">Řetězcové literály a řetězcové konstanty zřetězení dochází v době kompilace; Vyvolá se v žádné zřetězení za běhu.</span><span class="sxs-lookup"><span data-stu-id="e78dc-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="e78dc-108">Pro proměnné řetězce zřetězení dochází pouze v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e78dc-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="e78dc-109">Následující příklad používá zřetězení rozdělením dlouhý řetězec literálu řetězce menší za účelem zlepšení čitelnosti ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="e78dc-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="e78dc-110">Tyto části zřetězeny do jednoho řetězce v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="e78dc-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="e78dc-111">Je zahrnutých bez poplatků za běhu výkonu bez ohledu na počet řetězců.</span><span class="sxs-lookup"><span data-stu-id="e78dc-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="e78dc-112">K proměnné řetězce zřetězit, můžete použít `+` nebo `+=` operátory, [interpolace](../language-reference/tokens/interpolated.md) nebo <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e78dc-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e78dc-113">`+` Operátor se snadno používá a zajišťuje intuitivní kódu.</span><span class="sxs-lookup"><span data-stu-id="e78dc-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="e78dc-114">I když použijete několik `+` operátory v jednom příkazu, řetězec obsahu zkopírován pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="e78dc-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="e78dc-115">Následující kód ukazuje příklady použití `+` a `+=` operátory zřetězení řetězců:</span><span class="sxs-lookup"><span data-stu-id="e78dc-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="e78dc-116">V některých výrazů je snazší ke zřetězení řetězců pomocí interpolace řetězců, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="e78dc-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="e78dc-117">V operacích zřetězení řetězec kompilátor jazyka C# považuje za řetězec null stejné prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e78dc-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="e78dc-118">Jiné metody ke zřetězení řetězců je <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e78dc-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e78dc-119">Tato metoda funguje dobře, když vytváříte řetězec z malý počet součástí řetězce.</span><span class="sxs-lookup"><span data-stu-id="e78dc-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="e78dc-120">V ostatních případech může být kombinování řetězců ve smyčce, pokud si nejste jisti, kolik zdrojové řetězce kombinujete a skutečný počet zdrojové řetězce může být poměrně velký.</span><span class="sxs-lookup"><span data-stu-id="e78dc-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="e78dc-121"><xref:System.Text.StringBuilder> Třídy je navržená pro tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="e78dc-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="e78dc-122">Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="e78dc-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="e78dc-123">Další informace o [důvodů, proč zvolit zřetězení řetězců nebo `StringBuilder` třídy](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="e78dc-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="e78dc-124">Další možnost spojit řetězce z kolekce je použití <xref:System.String.Concat%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="e78dc-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e78dc-125">Použití <xref:System.String.Join%2A?displayProperty=nameWithType> metodu, pokud zdrojové řetězce musí být odděleny delimeter.</span><span class="sxs-lookup"><span data-stu-id="e78dc-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="e78dc-126">Následující kód kombinuje pole slov pomocí obou těchto metod:</span><span class="sxs-lookup"><span data-stu-id="e78dc-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="e78dc-127">V poslední, můžete použít [LINQ](../programming-guide/concepts/linq/index.md) a <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> způsob připojit se k řetězce z kolekce.</span><span class="sxs-lookup"><span data-stu-id="e78dc-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="e78dc-128">Tato metoda kombinuje zdrojové řetězce použití výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="e78dc-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="e78dc-129">Výraz lambda funguje přidat do existující akumulací každého řetězce.</span><span class="sxs-lookup"><span data-stu-id="e78dc-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="e78dc-130">V následujícím příkladu jsou k dispozici pole slova přidáním mezeru mezi jednotlivých slov v poli:</span><span class="sxs-lookup"><span data-stu-id="e78dc-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="e78dc-131">Tyto ukázky můžete zkusit pohledem na kód v našich [úložiště GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="e78dc-131">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="e78dc-132">Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="e78dc-132">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="e78dc-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e78dc-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="e78dc-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e78dc-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="e78dc-135">Řetězce</span><span class="sxs-lookup"><span data-stu-id="e78dc-135">Strings</span></span>](../programming-guide/strings/index.md)
