---
title: "operator (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords: operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8fae5487d5daa5ada52d45919598d1abd217aee9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="operator-c-reference"></a><span data-ttu-id="73c03-102">operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="73c03-102">operator (C# Reference)</span></span>
<span data-ttu-id="73c03-103">Použití `operator` – klíčové slovo k přetížení předdefinované operátor nebo poskytovat převodu z uživatelem definované v třídě nebo struktuře deklaraci.</span><span class="sxs-lookup"><span data-stu-id="73c03-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73c03-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="73c03-104">Example</span></span>  
 <span data-ttu-id="73c03-105">Zde je velmi zjednodušené třídu desetinná čísla.</span><span class="sxs-lookup"><span data-stu-id="73c03-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="73c03-106">Ho přetížení + a * operátory k provedení zlomkové sčítání a násobení a také operátor převodu, který převádí typu zlomek typu double.</span><span class="sxs-lookup"><span data-stu-id="73c03-106">It overloads the + and * operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a Fraction type to a double type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="73c03-107">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73c03-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73c03-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="73c03-108">See Also</span></span>  
 [<span data-ttu-id="73c03-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73c03-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="73c03-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="73c03-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="73c03-111">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73c03-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="73c03-112">implicitní</span><span class="sxs-lookup"><span data-stu-id="73c03-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="73c03-113">explicitní</span><span class="sxs-lookup"><span data-stu-id="73c03-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="73c03-114">Postupy: implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="73c03-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
