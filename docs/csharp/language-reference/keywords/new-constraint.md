---
title: "new – omezení (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8557e056a664fd470b1f185b619d81235c8fcba7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="99252-102">new – omezení (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="99252-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="99252-103">`new` Omezení určuje, že některý argument typu v deklaraci – obecná třída musí mít konstruktor public bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="99252-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="99252-104">Pokud chcete používat nové omezení, typ nemůže být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="99252-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99252-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="99252-105">Example</span></span>  
 <span data-ttu-id="99252-106">Použít `new` omezení pro parametr typu když obecná třída vytváří nové instance typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="99252-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="99252-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="99252-107">Example</span></span>  
 <span data-ttu-id="99252-108">Při použití `new()` omezení s jiná omezení, musí být zadaná poslední:</span><span class="sxs-lookup"><span data-stu-id="99252-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="99252-109">Další informace najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="99252-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="99252-110">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="99252-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99252-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="99252-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="99252-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="99252-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="99252-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="99252-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="99252-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="99252-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="99252-115">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="99252-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="99252-116">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="99252-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
