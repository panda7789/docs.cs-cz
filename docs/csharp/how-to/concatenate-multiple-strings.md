---
title: "Postupy: řetězení více řetězců (Průvodce C#)"
description: "Zřetězení řetězců v jazyce C# několika způsoby. Další možnosti a důvodech různé možnosti."
ms.date: 01/11/2018
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3a083a479928261dd913f290ba3a6575a7164969
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="f11a8-104">Postupy: řetězení více řetězců (Průvodce C#)</span><span class="sxs-lookup"><span data-stu-id="f11a8-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="f11a8-105">*Zřetězení* je proces připojování jeden řetězec na konec jiným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="f11a8-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="f11a8-106">Zřetězení řetězců pomocí + – operátor.</span><span class="sxs-lookup"><span data-stu-id="f11a8-106">You concatenate strings by using the + operator.</span></span> <span data-ttu-id="f11a8-107">Pro textové literály a řetězcové konstanty zřetězení nastane při kompilaci; nastane, bez spuštění zřetězení.</span><span class="sxs-lookup"><span data-stu-id="f11a8-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="f11a8-108">Pro proměnné řetězec zřetězení dojde pouze v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f11a8-108">For string variables, concatenation occurs only at run time.</span></span>

<span data-ttu-id="f11a8-109">Následující příklad používá zřetězení rozdělením dlouhý řetězec literálu menší řetězců za účelem zlepšení čitelnosti ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="f11a8-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="f11a8-110">Tyto části bude zřetězen do jednoho řetězce v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="f11a8-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="f11a8-111">Související se situací je bez nákladů výkon bez ohledu na počet řetězce.</span><span class="sxs-lookup"><span data-stu-id="f11a8-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="f11a8-112">Ke zřetězení proměnné řetězce, můžete použít `+` nebo `+=` operátory, [řetězec interpolace](../tutorials/string-interpolation.md) nebo <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f11a8-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../tutorials/string-interpolation.md) or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="f11a8-113">`+` Operátor se snadno používá a zajišťuje intuitivní kódu.</span><span class="sxs-lookup"><span data-stu-id="f11a8-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="f11a8-114">I když používáte několik + operátory v jednom příkazu, obsah řetězce zkopírován pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="f11a8-114">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="f11a8-115">Následující kód ukazuje dva příklady použití `+` operátor ke zřetězení řetězců:</span><span class="sxs-lookup"><span data-stu-id="f11a8-115">The following code shows two examples of using the `+` operator to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="f11a8-116">V některých výrazy je snazší zřetězení řetězců pomocí řetězce interpolace, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="f11a8-116">In some expressions, it is easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="f11a8-117">V operace s řetězci zřetězení kompilátor jazyka C# zpracovává řetězec null stejné jako prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f11a8-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="f11a8-118">Ostatní metody ke zřetězení řetězců <xref:System.String.Concat%2A?displayProperty=nameWithType> a <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f11a8-118">Other methods to concatenate strings are <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f11a8-119">Tyto metody fungují dobře, pokud vytváříte řetězec z malý počet součástí řetězce.</span><span class="sxs-lookup"><span data-stu-id="f11a8-119">These methods work well when you are building a string from a small number of component strings.</span></span> <span data-ttu-id="f11a8-120">Tyto methdos jsou také skvělou volbou, když víte, počet řetězců, které si spojený řetězec.</span><span class="sxs-lookup"><span data-stu-id="f11a8-120">These methdos are also a great choice when you know the number of strings that make up your concatenated string.</span></span>

<span data-ttu-id="f11a8-121">V jiných případech může být kombinovaných řetězců ve smyčce, kde nevíte, kolik řetězce zdrojů kombinujete a skutečný počet řetězce zdrojů může mít poměrně značnou.</span><span class="sxs-lookup"><span data-stu-id="f11a8-121">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="f11a8-122"><xref:System.Text.StringBuilder> Třída byl navržený pro tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="f11a8-122">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="f11a8-123">Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="f11a8-123">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="f11a8-124">Další informace o [důvodů, proč zvolit zřetězení řetězců nebo `StringBuilder` – třída](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="f11a8-124">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="f11a8-125">Další možností pro připojení řetězce z kolekce, je použít [LINQ](../programming-guide/concepts/linq/index.md) a <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="f11a8-125">Another option to join strings from a collection is to use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f11a8-126">Tato metoda kombinuje řetězce zdrojů pomocí výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="f11a8-126">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="f11a8-127">Výraz lambda funguje pro přidání do existující akumulace každý řetězec.</span><span class="sxs-lookup"><span data-stu-id="f11a8-127">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="f11a8-128">Následující příklad kombinuje pole slov přidáním mezery mezi jednotlivých slov v poli:</span><span class="sxs-lookup"><span data-stu-id="f11a8-128">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]  


## <a name="see-also"></a><span data-ttu-id="f11a8-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="f11a8-129">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="f11a8-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f11a8-130">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="f11a8-131">Řetězce</span><span class="sxs-lookup"><span data-stu-id="f11a8-131">Strings</span></span>](../programming-guide/strings/index.md)
