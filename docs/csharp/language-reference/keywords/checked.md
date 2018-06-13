---
title: checked (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: b05af798217a4f312bcf134d531135713efa8c66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216605"
---
# <a name="checked-c-reference"></a><span data-ttu-id="cb3dc-102">checked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cb3dc-102">checked (C# Reference)</span></span>
<span data-ttu-id="cb3dc-103">`checked` – Klíčové slovo se používá k explicitně povolit přetečení kontrola aritmetické operace typu integrální převody.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="cb3dc-104">Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty v případě, že výraz vytvoří hodnotu, která je mimo rozsah pro cílový typ způsobí chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="cb3dc-105">Pokud výraz obsahuje jednu nebo více hodnot nekonstantní, kompilátor nezjistí přetečení.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="cb3dc-106">Vyhodnocení výrazu přiřazené `i2` v následujícím příkladu nezpůsobí chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 <span data-ttu-id="cb3dc-107">Ve výchozím nastavení tyto není konstantní výrazy nejsou kontrola přetečení v době běhu buď a vyvolají není přetečení výjimky.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="cb3dc-108">Předchozí příklad zobrazí-2,147,483,639 jako součet dvě kladná celá čísla.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>  
  
 <span data-ttu-id="cb3dc-109">Kontrola přetečení se dá nastavit podle – možnosti kompilátoru, konfigurace prostředí nebo použití `checked` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="cb3dc-110">Následující příklady ukazují, jak používat `checked` výraz nebo `checked` bloku ke zjištění přetečení předchozí součet vytvořené v době běhu.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="cb3dc-111">Oba příklady vyvolání k výjimce přetečení.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-111">Both examples raise an overflow exception.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 <span data-ttu-id="cb3dc-112">[Nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo lze zabránit kontrola přetečení.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb3dc-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb3dc-113">Example</span></span>  
 <span data-ttu-id="cb3dc-114">Tento příklad ukazuje způsob použití `checked` povolit přetečení kontrola za běhu.</span><span class="sxs-lookup"><span data-stu-id="cb3dc-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="cb3dc-115">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cb3dc-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb3dc-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb3dc-116">See Also</span></span>  
 [<span data-ttu-id="cb3dc-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cb3dc-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cb3dc-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cb3dc-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cb3dc-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cb3dc-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="cb3dc-120">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="cb3dc-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="cb3dc-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="cb3dc-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
