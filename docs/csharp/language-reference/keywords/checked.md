---
title: checked – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: d148de99d1a1fab40f01e5807d1e7d6488b3186d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244580"
---
# <a name="checked-c-reference"></a><span data-ttu-id="40559-102">checked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="40559-102">checked (C# Reference)</span></span>

<span data-ttu-id="40559-103">`checked` – Klíčové slovo se používá explicitně povolit kontroly pro integrálového typu aritmetické operace a převody přetečení.</span><span class="sxs-lookup"><span data-stu-id="40559-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="40559-104">Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty způsobí chybu kompilátoru, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu.</span><span class="sxs-lookup"><span data-stu-id="40559-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="40559-105">Pokud výraz obsahuje jednu nebo více hodnot, která není konstantní, kompilátor nezjistí přetečení.</span><span class="sxs-lookup"><span data-stu-id="40559-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="40559-106">Vyhodnocení výrazu přiřazená `i2` v následujícím příkladu nezpůsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="40559-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="40559-107">Ve výchozím nastavení tyto není konstantní výrazy nejsou zkontrolovat přetečení v době běhu buď a nevyvolávejte výjimky přetečení.</span><span class="sxs-lookup"><span data-stu-id="40559-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="40559-108">Předchozí příklad zobrazuje-2,147,483,639 jako součet hodnot dvě kladná celá čísla.</span><span class="sxs-lookup"><span data-stu-id="40559-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="40559-109">Kontrola přetečení se dá nastavit možnosti kompilátoru, konfigurace prostředí nebo použití `checked` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="40559-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="40559-110">Následující příklady ukazují, jak používat `checked` výraz nebo `checked` bloku k detekci přetečení, který je vytvořen v době běhu předchozí součet.</span><span class="sxs-lookup"><span data-stu-id="40559-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="40559-111">Oba příklady vyvolat výjimku přetečení.</span><span class="sxs-lookup"><span data-stu-id="40559-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="40559-112">[Nekontrolovaná](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo je možné zabránit kontrola přetečení.</span><span class="sxs-lookup"><span data-stu-id="40559-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="40559-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="40559-113">Example</span></span>

<span data-ttu-id="40559-114">Tento příklad ukazuje způsob použití `checked` povolit kontroly za běhu přetečení.</span><span class="sxs-lookup"><span data-stu-id="40559-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="40559-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40559-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="40559-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40559-116">See also</span></span>

- [<span data-ttu-id="40559-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40559-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="40559-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="40559-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="40559-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40559-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="40559-120">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="40559-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [<span data-ttu-id="40559-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="40559-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
