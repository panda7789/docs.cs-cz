---
title: value (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2501bc8964ed76534dba6c7cc519e095c57cb898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="value-c-reference"></a><span data-ttu-id="3fdf5-102">value (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3fdf5-102">value (C# Reference)</span></span>
<span data-ttu-id="3fdf5-103">Kontextové klíčové slovo `value` se používá v přistupující objekt set v běžné vlastnosti deklarací.</span><span class="sxs-lookup"><span data-stu-id="3fdf5-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="3fdf5-104">Je podobná vstupního parametru pro metodu.</span><span class="sxs-lookup"><span data-stu-id="3fdf5-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="3fdf5-105">Slovo `value` odkazuje na hodnotu, která se pokouší kód klienta přiřadit k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fdf5-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="3fdf5-106">V následujícím příkladu `MyDerivedClass` má vlastnost s názvem `Name` používající `value` parametr přiřadit nového řetězce na pole Základní `name`.</span><span class="sxs-lookup"><span data-stu-id="3fdf5-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="3fdf5-107">Z hlediska kódu klienta je zapsán operaci jako jednoduché přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3fdf5-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="3fdf5-108">Další informace o použití `value`, najdete v části [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="3fdf5-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3fdf5-109">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3fdf5-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3fdf5-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fdf5-110">See Also</span></span>  
 [<span data-ttu-id="3fdf5-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3fdf5-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3fdf5-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="3fdf5-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3fdf5-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3fdf5-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
