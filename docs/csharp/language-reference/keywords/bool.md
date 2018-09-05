---
title: BOOL – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2041182dffa0330ea601b30e047c0b09731618f2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747398"
---
# <a name="bool-c-reference"></a><span data-ttu-id="87b0a-102">bool (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="87b0a-102">bool (C# Reference)</span></span>

<span data-ttu-id="87b0a-103">`bool` – Klíčové slovo je alias pro <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87b0a-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87b0a-104">Se používá k deklaraci proměnné k ukládání logické hodnoty [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="87b0a-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>

> [!NOTE]
> <span data-ttu-id="87b0a-105">Pokud požadujete logickou hodnotu, která může také obsahovat hodnotu `null`, použijte `bool?`.</span><span class="sxs-lookup"><span data-stu-id="87b0a-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="87b0a-106">Další informace najdete v tématu [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="87b0a-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>

## <a name="literals"></a><span data-ttu-id="87b0a-107">Literály</span><span class="sxs-lookup"><span data-stu-id="87b0a-107">Literals</span></span>

<span data-ttu-id="87b0a-108">Můžete přiřadit logickou hodnotu k `bool` proměnné.</span><span class="sxs-lookup"><span data-stu-id="87b0a-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="87b0a-109">Můžete také přiřadit výraz, který se vyhodnotí `bool` k `bool` proměnné.</span><span class="sxs-lookup"><span data-stu-id="87b0a-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="87b0a-110">Výchozí hodnota `bool` proměnná je `false`.</span><span class="sxs-lookup"><span data-stu-id="87b0a-110">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="87b0a-111">Výchozí hodnota `bool?` proměnná je `null`.</span><span class="sxs-lookup"><span data-stu-id="87b0a-111">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="87b0a-112">Převody</span><span class="sxs-lookup"><span data-stu-id="87b0a-112">Conversions</span></span>

<span data-ttu-id="87b0a-113">V jazyce C++ je hodnota typu `bool` lze převést na hodnotu typu `int`; jinými slovy, `false` je ekvivalentní hodnotě nula a `true` odpovídá nenulové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="87b0a-113">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="87b0a-114">V jazyce C#, neexistuje žádný převod mezi `bool` typ a jiné typy.</span><span class="sxs-lookup"><span data-stu-id="87b0a-114">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="87b0a-115">Například následující `if` příkaz není platný v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="87b0a-115">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="87b0a-116">K otestování proměnné typu `int`, je nutné explicitně porovnejte ji s hodnotou, jako je nula, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="87b0a-116">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="87b0a-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="87b0a-117">Example</span></span>

<span data-ttu-id="87b0a-118">V tomto příkladu zadejte znak z klávesnice a program kontroluje, jestli vstupní znak je písmeno.</span><span class="sxs-lookup"><span data-stu-id="87b0a-118">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="87b0a-119">Pokud je písmeno, se zkontroluje, jestli malá nebo velká písmena.</span><span class="sxs-lookup"><span data-stu-id="87b0a-119">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="87b0a-120">Tyto kontroly se provádějí s <xref:System.Char.IsLetter%2A>, a <xref:System.Char.IsLower%2A>, jak které návratovou hodnotu `bool` typu:</span><span class="sxs-lookup"><span data-stu-id="87b0a-120">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="87b0a-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="87b0a-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="87b0a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87b0a-122">See also</span></span>

- [<span data-ttu-id="87b0a-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="87b0a-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="87b0a-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="87b0a-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="87b0a-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="87b0a-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="87b0a-126">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="87b0a-126">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="87b0a-127">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="87b0a-127">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="87b0a-128">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="87b0a-128">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="87b0a-129">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="87b0a-129">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  