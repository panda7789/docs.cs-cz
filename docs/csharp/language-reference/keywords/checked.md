---
title: zaškrtnuté klíčové slovo – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713706"
---
# <a name="checked-c-reference"></a><span data-ttu-id="bbe93-102">checked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bbe93-102">checked (C# Reference)</span></span>

<span data-ttu-id="bbe93-103">Klíčové `checked` slovo se používá k explicitnímu povolení kontroly přetečení pro aritmetické operace a převody integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="bbe93-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="bbe93-104">Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty způsobí chybu kompilátoru, pokud výraz vytváří hodnotu, která je mimo rozsah cílového typu.</span><span class="sxs-lookup"><span data-stu-id="bbe93-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="bbe93-105">Pokud výraz obsahuje jednu nebo více nekonstantních hodnot, kompilátor nezjistí přetečení.</span><span class="sxs-lookup"><span data-stu-id="bbe93-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="bbe93-106">Vyhodnocení výrazu přiřazeného v `i2` následujícím příkladu nezpůsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="bbe93-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="bbe93-107">Ve výchozím nastavení tyto nekonstantní výrazy nejsou kontrolovány pro přetečení v době běhu buď a nevyvolávají výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="bbe93-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="bbe93-108">Předchozí příklad zobrazí -2,147,483,639 jako součet dvou kladných celá čísla.</span><span class="sxs-lookup"><span data-stu-id="bbe93-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="bbe93-109">Kontrola přetečení může být povolena možnostmi kompilátoru, konfigurací prostředí nebo použitím klíčového `checked` slova.</span><span class="sxs-lookup"><span data-stu-id="bbe93-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="bbe93-110">Následující příklady ukazují, jak `checked` použít `checked` výraz nebo blok ke zjištění přetečení, které je produkováno předchozím součtem za běhu.</span><span class="sxs-lookup"><span data-stu-id="bbe93-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="bbe93-111">Oba příklady vyvolávají výjimku přetečení.</span><span class="sxs-lookup"><span data-stu-id="bbe93-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="bbe93-112">[Nezaškrtnuté](./unchecked.md) klíčové slovo lze použít k zabránění přetečení kontroly.</span><span class="sxs-lookup"><span data-stu-id="bbe93-112">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="bbe93-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbe93-113">Example</span></span>

<span data-ttu-id="bbe93-114">Tato ukázka ukazuje, jak použít `checked` k povolení kontroly přetečení za běhu.</span><span class="sxs-lookup"><span data-stu-id="bbe93-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="bbe93-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bbe93-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bbe93-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbe93-116">See also</span></span>

- [<span data-ttu-id="bbe93-117">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bbe93-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bbe93-118">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bbe93-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bbe93-119">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="bbe93-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="bbe93-120">Checked a Unchecked</span><span class="sxs-lookup"><span data-stu-id="bbe93-120">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="bbe93-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="bbe93-121">unchecked</span></span>](./unchecked.md)
