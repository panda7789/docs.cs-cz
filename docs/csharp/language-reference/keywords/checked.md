---
title: "checked (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ae77894cdc94e41dfa281b92ed3304e0dc25731
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-reference"></a><span data-ttu-id="4fdd2-102">checked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4fdd2-102">checked (C# Reference)</span></span>
<span data-ttu-id="4fdd2-103">`checked` – Klíčové slovo se používá k explicitně povolit přetečení kontrola aritmetické operace typu integrální převody.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="4fdd2-104">Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty v případě, že výraz vytvoří hodnotu, která je mimo rozsah pro cílový typ způsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="4fdd2-105">Pokud výraz obsahuje jednu nebo více hodnot nekonstantní, kompilátor nezjistí přetečení.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="4fdd2-106">Vyhodnocení výrazu přiřazené `i2` v následujícím příkladu nezpůsobí chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 <span data-ttu-id="4fdd2-107">Ve výchozím nastavení tyto není konstantní výrazy nejsou kontrola přetečení v době běhu buď a vyvolají není přetečení výjimky.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="4fdd2-108">Předchozí příklad zobrazí-2,147,483,639 jako součet dvě kladná celá čísla.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>  
  
 <span data-ttu-id="4fdd2-109">Kontrola přetečení se dá nastavit podle – možnosti kompilátoru, konfigurace prostředí nebo použití `checked` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="4fdd2-110">Následující příklady ukazují, jak používat `checked` výraz nebo `checked` bloku ke zjištění přetečení předchozí součet vytvořené v době běhu.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="4fdd2-111">Oba příklady vyvolání k výjimce přetečení.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-111">Both examples raise an overflow exception.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 <span data-ttu-id="4fdd2-112">[Nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo lze zabránit kontrola přetečení.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fdd2-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fdd2-113">Example</span></span>  
 <span data-ttu-id="4fdd2-114">Tento příklad ukazuje způsob použití `checked` povolit přetečení kontrola za běhu.</span><span class="sxs-lookup"><span data-stu-id="4fdd2-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4fdd2-115">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4fdd2-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4fdd2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fdd2-116">See Also</span></span>  
 [<span data-ttu-id="4fdd2-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4fdd2-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4fdd2-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4fdd2-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4fdd2-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4fdd2-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4fdd2-120">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="4fdd2-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="4fdd2-121">nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="4fdd2-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
