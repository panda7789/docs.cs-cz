---
title: checked – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: e6c28ee0c575bd6010a8aad76fc978062c5fc6a4
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948407"
---
# <a name="checked-c-reference"></a><span data-ttu-id="10bda-102">checked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="10bda-102">checked (C# Reference)</span></span>

<span data-ttu-id="10bda-103">`checked` – Klíčové slovo se používá k explicitně povolit přetečení kontrola aritmetické operace typu integrální převody.</span><span class="sxs-lookup"><span data-stu-id="10bda-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="10bda-104">Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty v případě, že výraz vytvoří hodnotu, která je mimo rozsah pro cílový typ způsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="10bda-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="10bda-105">Pokud výraz obsahuje jednu nebo více hodnot nekonstantní, kompilátor nezjistí přetečení.</span><span class="sxs-lookup"><span data-stu-id="10bda-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="10bda-106">Vyhodnocení výrazu přiřazené `i2` v následujícím příkladu nezpůsobí chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="10bda-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="10bda-107">Ve výchozím nastavení tyto není konstantní výrazy nejsou kontrola přetečení v době běhu buď a vyvolají není přetečení výjimky.</span><span class="sxs-lookup"><span data-stu-id="10bda-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="10bda-108">Předchozí příklad zobrazí-2,147,483,639 jako součet dvě kladná celá čísla.</span><span class="sxs-lookup"><span data-stu-id="10bda-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="10bda-109">Kontrola přetečení se dá nastavit podle – možnosti kompilátoru, konfigurace prostředí nebo použití `checked` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="10bda-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="10bda-110">Následující příklady ukazují, jak používat `checked` výraz nebo `checked` bloku ke zjištění přetečení předchozí součet vytvořené v době běhu.</span><span class="sxs-lookup"><span data-stu-id="10bda-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="10bda-111">Oba příklady vyvolání k výjimce přetečení.</span><span class="sxs-lookup"><span data-stu-id="10bda-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="10bda-112">[Nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo lze zabránit kontrola přetečení.</span><span class="sxs-lookup"><span data-stu-id="10bda-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="10bda-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="10bda-113">Example</span></span>

<span data-ttu-id="10bda-114">Tento příklad ukazuje způsob použití `checked` povolit přetečení kontrola za běhu.</span><span class="sxs-lookup"><span data-stu-id="10bda-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="10bda-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10bda-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="10bda-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10bda-116">See also</span></span>

[<span data-ttu-id="10bda-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10bda-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="10bda-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="10bda-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="10bda-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10bda-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="10bda-120">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="10bda-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
[<span data-ttu-id="10bda-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="10bda-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
