---
description: zaškrtnuté klíčové slovo – Referenční dokumentace jazyka C#
title: zaškrtnuté klíčové slovo – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 4dd8bc02d3af89d6bab3aef55a88cb8b40704da6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138277"
---
# <a name="checked-c-reference"></a><span data-ttu-id="d85b3-103">checked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d85b3-103">checked (C# Reference)</span></span>

<span data-ttu-id="d85b3-104">`checked`Klíčové slovo slouží k explicitnímu povolení kontroly přetečení pro aritmetické operace a převody integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="d85b3-104">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="d85b3-105">Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty, způsobí chybu kompilátoru, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu.</span><span class="sxs-lookup"><span data-stu-id="d85b3-105">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="d85b3-106">Pokud výraz obsahuje jednu nebo více nekonstantních hodnot, kompilátor nerozpozná přetečení.</span><span class="sxs-lookup"><span data-stu-id="d85b3-106">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="d85b3-107">Vyhodnocení výrazu přiřazeného `i2` v následujícím příkladu nezpůsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d85b3-107">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="d85b3-108">Ve výchozím nastavení nejsou tyto nekonstantní výrazy kontrolovány pro přetečení v době běhu a nevyvolávají výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="d85b3-108">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="d85b3-109">Předchozí příklad zobrazí-2 147 483 639 jako součet dvou kladných celých čísel.</span><span class="sxs-lookup"><span data-stu-id="d85b3-109">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="d85b3-110">Kontrolu přetečení lze povolit pomocí možností kompilátoru, konfigurace prostředí nebo použití `checked` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="d85b3-110">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="d85b3-111">Následující příklady ukazují, jak použít `checked` výraz nebo `checked` blok k detekci přetečení, které je vyrobeno předchozí součtem v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d85b3-111">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="d85b3-112">Oba příklady vyvolávají výjimku přetečení.</span><span class="sxs-lookup"><span data-stu-id="d85b3-112">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="d85b3-113">[Nezaškrtnuté](./unchecked.md) klíčové slovo lze použít k zabránění kontrole přetečení.</span><span class="sxs-lookup"><span data-stu-id="d85b3-113">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="d85b3-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d85b3-114">Example</span></span>

<span data-ttu-id="d85b3-115">Tento příklad ukazuje, jak použít `checked` k povolení kontroly přetečení v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d85b3-115">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="d85b3-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d85b3-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d85b3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d85b3-117">See also</span></span>

- [<span data-ttu-id="d85b3-118">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d85b3-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d85b3-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d85b3-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d85b3-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d85b3-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="d85b3-121">Checked a Unchecked</span><span class="sxs-lookup"><span data-stu-id="d85b3-121">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="d85b3-122">unchecked</span><span class="sxs-lookup"><span data-stu-id="d85b3-122">unchecked</span></span>](./unchecked.md)
