---
title: operator (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: d633a46e21f913aa8c05289dccfb63e71efd697e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267945"
---
# <a name="operator-c-reference"></a><span data-ttu-id="6f0bc-102">operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6f0bc-102">operator (C# Reference)</span></span>
<span data-ttu-id="6f0bc-103">Použití `operator` – klíčové slovo k přetížení předdefinované operátor nebo poskytovat převodu z uživatelem definované v třídě nebo struktuře deklaraci.</span><span class="sxs-lookup"><span data-stu-id="6f0bc-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f0bc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f0bc-104">Example</span></span>  
 <span data-ttu-id="6f0bc-105">Zde je velmi zjednodušené třídu desetinná čísla.</span><span class="sxs-lookup"><span data-stu-id="6f0bc-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="6f0bc-106">Ho přetížení `+` a `*` operátory k provedení zlomkové sčítání a násobení a také poskytuje operátora převodu které převádí `Fraction` typ, který má `double` typu.</span><span class="sxs-lookup"><span data-stu-id="6f0bc-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6f0bc-107">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6f0bc-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6f0bc-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f0bc-108">See Also</span></span>  
 [<span data-ttu-id="6f0bc-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6f0bc-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6f0bc-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6f0bc-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6f0bc-111">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6f0bc-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6f0bc-112">implicit</span><span class="sxs-lookup"><span data-stu-id="6f0bc-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="6f0bc-113">explicit</span><span class="sxs-lookup"><span data-stu-id="6f0bc-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="6f0bc-114">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="6f0bc-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
