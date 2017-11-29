---
title: "foreach, in (Referenční dokumentace jazyka C#)"
ms.date: 10/11/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5601682d53a01ff07aba7e416aa81ded4c03e4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="ae613-102">foreach, in (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ae613-102">foreach, in (C# Reference)</span></span>
<span data-ttu-id="ae613-103">`foreach` Příkaz opakuje skupinu embedded příkazy pro každý prvek v pole nebo kolekci objekt, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae613-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="ae613-104">`foreach` Příkaz se používá k procházení kolekce se získat informace, které, ale nelze použít k přidání nebo odebrání položky z kolekce zdroj předejdete nepředvídatelným vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="ae613-104">The `foreach` statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="ae613-105">Pokud potřebujete přidat nebo odebrat položky z kolekce zdroje, použijte [pro](for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="ae613-105">If you need to add or remove items from the source collection, use a [for](for.md) loop.</span></span>
  
 <span data-ttu-id="ae613-106">Vložené příkazů pokračovat provést pro každý prvek v poli nebo kolekce.</span><span class="sxs-lookup"><span data-stu-id="ae613-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="ae613-107">Po dokončení iterace pro všechny elementy v kolekci, je ovládací prvek přenesen na další následující příkaz `foreach` bloku.</span><span class="sxs-lookup"><span data-stu-id="ae613-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>
  
 <span data-ttu-id="ae613-108">Kdykoli bodu v rámci `foreach` bloku, můžete rozdělit mimo smyčky pomocí [zalomení](break.md) – klíčové slovo nebo krok do další iterace ve smyčce pomocí [pokračovat](continue.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ae613-108">At any point within the `foreach` block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span>

 <span data-ttu-id="ae613-109">A `foreach` smyčky můžete také měly být byl ukončen ve [goto](goto.md), [vrátit](return.md), nebo [throw](throw.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="ae613-109">A `foreach` loop can also be exited by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

 <span data-ttu-id="ae613-110">Další informace o `foreach` – klíčové slovo a ukázky kódu, najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="ae613-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  

 [<span data-ttu-id="ae613-111">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="ae613-111">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [<span data-ttu-id="ae613-112">Postupy: přístup ke třídě kolekce pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="ae613-112">How to: Access a Collection Class with foreach</span></span>](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a><span data-ttu-id="ae613-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae613-113">Example</span></span>
 <span data-ttu-id="ae613-114">Následující kód ukazuje tři příklady.</span><span class="sxs-lookup"><span data-stu-id="ae613-114">The following code shows three examples.</span></span>

> [!TIP]
> <span data-ttu-id="ae613-115">Příklady a experimentovat s syntaxe zkuste jinou použití, které se více podobají váš případ použití, můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="ae613-115">You can modify the examples to experiment with the syntax and try different usages that are more similar to your use case.</span></span> <span data-ttu-id="ae613-116">Stisknutím klávesy "Spustit" spustit kód, potom upravit a znovu stiskněte "Spustit".</span><span class="sxs-lookup"><span data-stu-id="ae613-116">Press "Run" to run the code, then edit and press "Run" again.</span></span>

-   <span data-ttu-id="ae613-117">Typické `foreach` smyčky, která zobrazí obsah pole celých čísel</span><span class="sxs-lookup"><span data-stu-id="ae613-117">a typical `foreach` loop that displays the contents of an array of integers</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   <span data-ttu-id="ae613-118">[pro](../../../csharp/language-reference/keywords/for.md) smyčky, která má stejnou funkci</span><span class="sxs-lookup"><span data-stu-id="ae613-118">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   <span data-ttu-id="ae613-119">`foreach` smyčky, která udržuje počet prvků v poli</span><span class="sxs-lookup"><span data-stu-id="ae613-119">a `foreach` loop that maintains a count of the number of elements in the array</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a><span data-ttu-id="ae613-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae613-120">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ae613-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae613-121">See Also</span></span>  

[<span data-ttu-id="ae613-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae613-122">C# Reference</span></span>](../index.md)

[<span data-ttu-id="ae613-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ae613-123">C# Programming Guide</span></span>](../../programming-guide/index.md)

[<span data-ttu-id="ae613-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae613-124">C# Keywords</span></span>](index.md)

[<span data-ttu-id="ae613-125">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="ae613-125">Iteration Statements</span></span>](iteration-statements.md)

[<span data-ttu-id="ae613-126">pro</span><span class="sxs-lookup"><span data-stu-id="ae613-126">for</span></span>](for.md)
