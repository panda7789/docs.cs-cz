---
title: bool (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 1045a459491b0d0d6a84c60f6e820297b47efd5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215956"
---
# <a name="bool-c-reference"></a><span data-ttu-id="3975f-102">bool (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3975f-102">bool (C# Reference)</span></span>
<span data-ttu-id="3975f-103">`bool` – Klíčové slovo je zástupce <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3975f-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3975f-104">Se používá k deklaraci proměnné, které chcete uložit logické hodnoty [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="3975f-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3975f-105">Pokud požadujete logická hodnota proměnné, která může mít hodnotu `null`, použijte `bool?`.</span><span class="sxs-lookup"><span data-stu-id="3975f-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="3975f-106">Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="3975f-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="3975f-107">Literály</span><span class="sxs-lookup"><span data-stu-id="3975f-107">Literals</span></span>  
 <span data-ttu-id="3975f-108">Můžete přiřadit logickou hodnotu k `bool` proměnné.</span><span class="sxs-lookup"><span data-stu-id="3975f-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="3975f-109">Je také možné přiřadit výraz, který se vyhodnocuje `bool` k `bool` proměnné.</span><span class="sxs-lookup"><span data-stu-id="3975f-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 <span data-ttu-id="3975f-110">Výchozí hodnota `bool` proměnná `false`.</span><span class="sxs-lookup"><span data-stu-id="3975f-110">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="3975f-111">Výchozí hodnota `bool?` proměnná `null`.</span><span class="sxs-lookup"><span data-stu-id="3975f-111">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="3975f-112">Převody</span><span class="sxs-lookup"><span data-stu-id="3975f-112">Conversions</span></span>  
 <span data-ttu-id="3975f-113">V jazyce C++ hodnotu typu `bool` lze převést na hodnotu typu `int`; jinými slovy, `false` se rovná nule a `true` je ekvivalentní nenulové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3975f-113">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="3975f-114">V jazyce C#, neexistuje žádný převod mezi `bool` typu a dalších typů.</span><span class="sxs-lookup"><span data-stu-id="3975f-114">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="3975f-115">Například následující `if` příkaz je neplatný v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="3975f-115">For example, the following `if` statement is invalid in C#:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 <span data-ttu-id="3975f-116">K testování proměnné typu `int`, budete muset explicitně porovnávají ho na hodnotu, jako je například nula, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3975f-116">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="3975f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="3975f-117">Example</span></span>  
 <span data-ttu-id="3975f-118">V tomto příkladu zadejte znak z klávesnice a program ověří, zda vstupní znak je písmeno.</span><span class="sxs-lookup"><span data-stu-id="3975f-118">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="3975f-119">Pokud je písmeno, zkontroluje, pokud je malá nebo velká písmena.</span><span class="sxs-lookup"><span data-stu-id="3975f-119">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="3975f-120">Tyto kontroly se provádějí pomocí <xref:System.Char.IsLetter%2A>, a <xref:System.Char.IsLower%2A>, obě které vrátit `bool` typ:</span><span class="sxs-lookup"><span data-stu-id="3975f-120">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3975f-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3975f-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3975f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="3975f-122">See Also</span></span>  
 [<span data-ttu-id="3975f-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3975f-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3975f-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3975f-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3975f-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3975f-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3975f-126">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="3975f-126">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="3975f-127">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="3975f-127">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="3975f-128">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="3975f-128">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="3975f-129">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="3975f-129">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
