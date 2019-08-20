---
title: 'zaškrtnuté: C# odkaz na klíčové slovo'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 69bd8cc95012533a6be279b04dc883a56f6f78ea
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605909"
---
# <a name="checked-c-reference"></a><span data-ttu-id="c69d1-102">checked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c69d1-102">checked (C# Reference)</span></span>

<span data-ttu-id="c69d1-103">`checked` Klíčové slovo slouží k explicitnímu povolení kontroly přetečení pro aritmetické operace a převody integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="c69d1-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="c69d1-104">Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty, způsobí chybu kompilátoru, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu.</span><span class="sxs-lookup"><span data-stu-id="c69d1-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="c69d1-105">Pokud výraz obsahuje jednu nebo více nekonstantních hodnot, kompilátor nerozpozná přetečení.</span><span class="sxs-lookup"><span data-stu-id="c69d1-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="c69d1-106">Vyhodnocení výrazu přiřazeného `i2` v následujícím příkladu nezpůsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c69d1-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="c69d1-107">Ve výchozím nastavení nejsou tyto nekonstantní výrazy kontrolovány pro přetečení v době běhu a nevyvolávají výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="c69d1-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="c69d1-108">Předchozí příklad zobrazí-2 147 483 639 jako součet dvou kladných celých čísel.</span><span class="sxs-lookup"><span data-stu-id="c69d1-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="c69d1-109">Kontrolu přetečení lze povolit pomocí možností kompilátoru, konfigurace prostředí nebo použití `checked` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="c69d1-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="c69d1-110">Následující příklady ukazují, jak použít `checked` výraz `checked` nebo blok k detekci přetečení, které je vyrobeno předchozí součtem v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c69d1-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="c69d1-111">Oba příklady vyvolávají výjimku přetečení.</span><span class="sxs-lookup"><span data-stu-id="c69d1-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="c69d1-112">Nezaškrtnuté klíčové slovo lze použít k zabránění kontrole přetečení. [](./unchecked.md)</span><span class="sxs-lookup"><span data-stu-id="c69d1-112">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="c69d1-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c69d1-113">Example</span></span>

<span data-ttu-id="c69d1-114">Tento příklad ukazuje, jak použít `checked` k povolení kontroly přetečení v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c69d1-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="c69d1-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c69d1-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c69d1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c69d1-116">See also</span></span>

- [<span data-ttu-id="c69d1-117">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="c69d1-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c69d1-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c69d1-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c69d1-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c69d1-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c69d1-120">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="c69d1-120">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="c69d1-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="c69d1-121">unchecked</span></span>](./unchecked.md)
