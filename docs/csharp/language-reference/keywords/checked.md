---
title: 'zaškrtnuté: C# odkaz na klíčové slovo'
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713706"
---
# <a name="checked-c-reference"></a><span data-ttu-id="b2fc0-102">checked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b2fc0-102">checked (C# Reference)</span></span>

<span data-ttu-id="b2fc0-103">Klíčové slovo `checked` slouží k explicitnímu povolení kontroly přetečení pro aritmetické operace a převody integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="b2fc0-104">Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty, způsobí chybu kompilátoru, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="b2fc0-105">Pokud výraz obsahuje jednu nebo více nekonstantních hodnot, kompilátor nerozpozná přetečení.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="b2fc0-106">Vyhodnocení výrazu přiřazeného k `i2` v následujícím příkladu nezpůsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="b2fc0-107">Ve výchozím nastavení nejsou tyto nekonstantní výrazy kontrolovány pro přetečení v době běhu a nevyvolávají výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="b2fc0-108">Předchozí příklad zobrazí-2 147 483 639 jako součet dvou kladných celých čísel.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="b2fc0-109">Kontrolu přetečení lze povolit pomocí možností kompilátoru, konfigurace prostředí nebo použití klíčového slova `checked`.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="b2fc0-110">Následující příklady ukazují, jak použít výraz `checked` nebo blok `checked` k detekci přetečení, které je vyrobeno předchozí součtem v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="b2fc0-111">Oba příklady vyvolávají výjimku přetečení.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="b2fc0-112">[Nezaškrtnuté](./unchecked.md) klíčové slovo lze použít k zabránění kontrole přetečení.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-112">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="b2fc0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2fc0-113">Example</span></span>

<span data-ttu-id="b2fc0-114">Tento příklad ukazuje, jak použít `checked` pro povolení kontroly přetečení v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b2fc0-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="b2fc0-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2fc0-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b2fc0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2fc0-116">See also</span></span>

- [<span data-ttu-id="b2fc0-117">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="b2fc0-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b2fc0-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b2fc0-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b2fc0-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2fc0-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b2fc0-120">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="b2fc0-120">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="b2fc0-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="b2fc0-121">unchecked</span></span>](./unchecked.md)
