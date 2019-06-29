---
title: BOOL – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: a6aae34433ee6f5d141d95f0c434af1825e9bf4b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424436"
---
# <a name="bool-c-reference"></a><span data-ttu-id="b1f98-102">bool (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b1f98-102">bool (C# Reference)</span></span>

<span data-ttu-id="b1f98-103">`bool` – Klíčové slovo je alias pro <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1f98-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1f98-104">Se používá k deklaraci proměnné k ukládání logické hodnoty: [true](true-literal.md) a [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b1f98-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b1f98-105">Použití `bool?` typu, pokud budete potřebovat pro podporu s hodnotou tři logiku, například při práci s databázemi, které podporují tři vracející typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="b1f98-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="b1f98-106">Pro `bool?` operandy, předdefinované `&` a `|` operátory podporu logiky s hodnotou tři.</span><span class="sxs-lookup"><span data-stu-id="b1f98-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="b1f98-107">Další informace najdete v tématu [logické operátory s povolenou hodnotou Null logická](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) část [logické logické operátory](../operators/boolean-logical-operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="b1f98-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="b1f98-108">Literály</span><span class="sxs-lookup"><span data-stu-id="b1f98-108">Literals</span></span>

<span data-ttu-id="b1f98-109">Můžete přiřadit logickou hodnotu k `bool` proměnné.</span><span class="sxs-lookup"><span data-stu-id="b1f98-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="b1f98-110">Můžete také přiřadit výraz, který se vyhodnotí `bool` k `bool` proměnné.</span><span class="sxs-lookup"><span data-stu-id="b1f98-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="b1f98-111">Výchozí hodnota `bool` proměnná je `false`.</span><span class="sxs-lookup"><span data-stu-id="b1f98-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="b1f98-112">Výchozí hodnota `bool?` proměnná je `null`.</span><span class="sxs-lookup"><span data-stu-id="b1f98-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="b1f98-113">Převody</span><span class="sxs-lookup"><span data-stu-id="b1f98-113">Conversions</span></span>

<span data-ttu-id="b1f98-114">V jazyce C++ je hodnota typu `bool` lze převést na hodnotu typu `int`; jinými slovy, `false` je ekvivalentní hodnotě nula a `true` odpovídá nenulové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b1f98-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="b1f98-115">V jazyce C#, neexistuje žádný převod mezi `bool` typ a jiné typy.</span><span class="sxs-lookup"><span data-stu-id="b1f98-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="b1f98-116">Například následující `if` příkaz není platný v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="b1f98-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="b1f98-117">K otestování proměnné typu `int`, je nutné explicitně porovnejte ji s hodnotou, jako je nula, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b1f98-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="b1f98-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1f98-118">Example</span></span>

<span data-ttu-id="b1f98-119">V tomto příkladu zadejte znak z klávesnice a program kontroluje, jestli vstupní znak je písmeno.</span><span class="sxs-lookup"><span data-stu-id="b1f98-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="b1f98-120">Pokud je písmeno, se zkontroluje, jestli malá nebo velká písmena.</span><span class="sxs-lookup"><span data-stu-id="b1f98-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="b1f98-121">Tyto kontroly se provádějí s <xref:System.Char.IsLetter%2A>, a <xref:System.Char.IsLower%2A>, jak které návratovou hodnotu `bool` typu:</span><span class="sxs-lookup"><span data-stu-id="b1f98-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="b1f98-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1f98-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b1f98-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1f98-123">See also</span></span>

- [<span data-ttu-id="b1f98-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1f98-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="b1f98-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b1f98-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b1f98-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1f98-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="b1f98-127">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="b1f98-127">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="b1f98-128">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="b1f98-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="b1f98-129">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="b1f98-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="b1f98-130">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="b1f98-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
