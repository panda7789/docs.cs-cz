---
title: "bool (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1d52955d64a6c8063e4ea93ceb096459c1c5e984
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bool-c-reference"></a><span data-ttu-id="b3a7b-102">bool (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b3a7b-102">bool (C# Reference)</span></span>
<span data-ttu-id="b3a7b-103">`bool` – Klíčové slovo je zástupce <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b3a7b-104">Se používá k deklaraci proměnné, které chcete uložit logické hodnoty [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="b3a7b-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3a7b-105">Pokud požadujete logická hodnota proměnné, která může mít hodnotu `null`, použijte `bool?`.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="b3a7b-106">Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3a7b-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="b3a7b-107">Literály</span><span class="sxs-lookup"><span data-stu-id="b3a7b-107">Literals</span></span>  
 <span data-ttu-id="b3a7b-108">Můžete přiřadit logickou hodnotu k `bool` proměnné.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="b3a7b-109">Je také možné přiřadit výraz, který se vyhodnocuje `bool` k `bool` proměnné.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 <span data-ttu-id="b3a7b-110">Výchozí hodnota `bool` proměnná `false`.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-110">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="b3a7b-111">Výchozí hodnota `bool?` proměnná `null`.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-111">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="b3a7b-112">Převody</span><span class="sxs-lookup"><span data-stu-id="b3a7b-112">Conversions</span></span>  
 <span data-ttu-id="b3a7b-113">V jazyce C++ hodnotu typu `bool` lze převést na hodnotu typu `int`; jinými slovy, `false` se rovná nule a `true` je ekvivalentní nenulové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-113">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="b3a7b-114">V jazyce C#, neexistuje žádný převod mezi `bool` typu a dalších typů.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-114">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="b3a7b-115">Například následující `if` příkaz je neplatný v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="b3a7b-115">For example, the following `if` statement is invalid in C#:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 <span data-ttu-id="b3a7b-116">K testování proměnné typu `int`, budete muset explicitně porovnávají ho na hodnotu, jako je například nula, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b3a7b-116">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="b3a7b-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3a7b-117">Example</span></span>  
 <span data-ttu-id="b3a7b-118">V tomto příkladu zadejte znak z klávesnice a program ověří, zda vstupní znak je písmeno.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-118">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="b3a7b-119">Pokud je písmeno, zkontroluje, pokud je malá nebo velká písmena.</span><span class="sxs-lookup"><span data-stu-id="b3a7b-119">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="b3a7b-120">Tyto kontroly se provádějí pomocí <xref:System.Char.IsLetter%2A>, a <xref:System.Char.IsLower%2A>, obě které vrátit `bool` typ:</span><span class="sxs-lookup"><span data-stu-id="b3a7b-120">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b3a7b-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b3a7b-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b3a7b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3a7b-122">See Also</span></span>  
 [<span data-ttu-id="b3a7b-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b3a7b-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b3a7b-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b3a7b-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b3a7b-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b3a7b-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b3a7b-126">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="b3a7b-126">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="b3a7b-127">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="b3a7b-127">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="b3a7b-128">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="b3a7b-128">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="b3a7b-129">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="b3a7b-129">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
