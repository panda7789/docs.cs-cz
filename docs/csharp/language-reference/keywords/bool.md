---
title: bool – klíčové C# slovo – Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 880e8c0b733afbf5c09f543e06a5a4a858d2b456
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771851"
---
# <a name="bool-c-reference"></a><span data-ttu-id="529b6-102">bool (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="529b6-102">bool (C# Reference)</span></span>

<span data-ttu-id="529b6-103">Klíčové slovo `bool` je aliasem <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="529b6-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="529b6-104">Slouží k deklaraci proměnných pro uložení logických hodnot: [true](true-literal.md) a [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="529b6-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="529b6-105">@No__t_0 typ použijte, pokud potřebujete podporovat logiku se třemi hodnotami, například při práci s databázemi, které podporují logický typ se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="529b6-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="529b6-106">Pro operandy `bool?` jsou předdefinované operátory `&` a `|` podporovány v rámci logiky se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="529b6-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="529b6-107">Další informace naleznete v části s [možnou hodnotou null logických operátorů](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="529b6-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="529b6-108">Literály</span><span class="sxs-lookup"><span data-stu-id="529b6-108">Literals</span></span>

<span data-ttu-id="529b6-109">Můžete přiřadit logickou hodnotu k proměnné `bool`.</span><span class="sxs-lookup"><span data-stu-id="529b6-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="529b6-110">Můžete také přiřadit výraz, který se vyhodnotí jako `bool` na `bool` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="529b6-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="529b6-111">Výchozí hodnota `bool` proměnné je `false`.</span><span class="sxs-lookup"><span data-stu-id="529b6-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="529b6-112">Výchozí hodnota `bool?` proměnné je `null`.</span><span class="sxs-lookup"><span data-stu-id="529b6-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="529b6-113">Převody</span><span class="sxs-lookup"><span data-stu-id="529b6-113">Conversions</span></span>

<span data-ttu-id="529b6-114">V C++, hodnota typu `bool` může být převedena na hodnotu typu `int`; Jinými slovy, `false` je ekvivalentem nula a `true` je ekvivalentní nenulovým hodnotám.</span><span class="sxs-lookup"><span data-stu-id="529b6-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="529b6-115">V C#neexistují žádné konverze mezi typem `bool` a dalšími typy.</span><span class="sxs-lookup"><span data-stu-id="529b6-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="529b6-116">Například následující příkaz `if` je neplatný v C#:</span><span class="sxs-lookup"><span data-stu-id="529b6-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="529b6-117">Chcete-li otestovat proměnnou typu `int`, je nutné ji explicitně porovnat s hodnotou, jako je například nula, následovně:</span><span class="sxs-lookup"><span data-stu-id="529b6-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="529b6-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="529b6-118">Example</span></span>

<span data-ttu-id="529b6-119">V tomto příkladu zadáte znak z klávesnice a program zkontroluje, jestli je vstupním znakem písmeno.</span><span class="sxs-lookup"><span data-stu-id="529b6-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="529b6-120">Pokud se jedná o písmeno, zkontroluje, zda se jedná o malá nebo velká písmena.</span><span class="sxs-lookup"><span data-stu-id="529b6-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="529b6-121">Tyto kontroly se provádějí s <xref:System.Char.IsLetter%2A> a <xref:System.Char.IsLower%2A>, jak vrátí `bool` typ:</span><span class="sxs-lookup"><span data-stu-id="529b6-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="529b6-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="529b6-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="529b6-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="529b6-123">See also</span></span>

- [<span data-ttu-id="529b6-124">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="529b6-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="529b6-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="529b6-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="529b6-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="529b6-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="529b6-127">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="529b6-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="529b6-128">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="529b6-128">Built-In Types Table</span></span>](./built-in-types-table.md)
