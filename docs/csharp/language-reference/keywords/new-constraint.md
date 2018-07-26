---
title: new – omezení (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199456"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="54aa5-102">new – omezení (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="54aa5-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="54aa5-103">`new` Omezení určuje, že každý argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="54aa5-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="54aa5-104">Typ omezení new použít, nemůže být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="54aa5-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54aa5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="54aa5-105">Example</span></span>  
 <span data-ttu-id="54aa5-106">Použít `new` omezení parametru typu, když obecné třídy vytvoří nové instance daného typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="54aa5-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="54aa5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="54aa5-107">Example</span></span>  
 <span data-ttu-id="54aa5-108">Při použití `new()` omezení s jinými omezeními, musí se zadat poslední:</span><span class="sxs-lookup"><span data-stu-id="54aa5-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="54aa5-109">Další informace najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="54aa5-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="54aa5-110">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="54aa5-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54aa5-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="54aa5-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="54aa5-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="54aa5-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="54aa5-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="54aa5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="54aa5-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="54aa5-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="54aa5-115">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="54aa5-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="54aa5-116">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="54aa5-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
