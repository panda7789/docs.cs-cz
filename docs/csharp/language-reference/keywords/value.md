---
title: Hodnota – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: f0b9e2927eb288a27f926a740a967742b8cdaa9e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236460"
---
# <a name="value-c-reference"></a><span data-ttu-id="7640c-102">value (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7640c-102">value (C# Reference)</span></span>
<span data-ttu-id="7640c-103">Kontextové klíčové slovo `value` se používá v přístupový objekt set v deklaracích běžnou vlastností.</span><span class="sxs-lookup"><span data-stu-id="7640c-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="7640c-104">Je to podobné do vstupního parametru pro metodu.</span><span class="sxs-lookup"><span data-stu-id="7640c-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="7640c-105">Slovo `value` odkazuje na hodnotu, která kód klienta se pokouší přiřadit vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7640c-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="7640c-106">V následujícím příkladu `MyDerivedClass` má vlastnost s názvem `Name` , která používá `value` parametr přiřadit nový řetězec pro pole zálohování `name`.</span><span class="sxs-lookup"><span data-stu-id="7640c-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="7640c-107">Z hlediska kódu klienta je zapsán operace jako jednoduchého přiřazení.</span><span class="sxs-lookup"><span data-stu-id="7640c-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="7640c-108">Další informace o použití `value`, naleznete v tématu [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="7640c-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7640c-109">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7640c-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7640c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7640c-110">See Also</span></span>

- [<span data-ttu-id="7640c-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7640c-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7640c-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7640c-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7640c-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7640c-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
