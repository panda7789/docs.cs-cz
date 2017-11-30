---
title: "Předávání parametrů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9e0e06d67f9da39c6b55f91e35d4a75b43353f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="7460d-102">Předávání parametrů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="7460d-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="7460d-103">V jazyce C# argumenty můžete předat parametry hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="7460d-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="7460d-104">Předání odkazem umožňuje funkce členy, metody, vlastnosti, indexery, operátory a konstruktory změna hodnoty parametrů a tato změna uchování v volání prostředí.</span><span class="sxs-lookup"><span data-stu-id="7460d-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="7460d-105">Chcete-li předat parametr odkazu, použijte `ref` nebo `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7460d-105">To pass a parameter by reference, use the `ref` or `out` keyword.</span></span> <span data-ttu-id="7460d-106">Pro jednoduchost, jenom `ref` – klíčové slovo se používá v příkladech v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7460d-106">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="7460d-107">Další informace o rozdílu mezi `ref` a `out`, najdete v části [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), a [předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="7460d-107">For more information about the difference between `ref` and `out`, see [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="7460d-108">Následující příklad ukazuje rozdíl mezi parametry hodnoty a odkazu.</span><span class="sxs-lookup"><span data-stu-id="7460d-108">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="7460d-109">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="7460d-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="7460d-110">Předávání parametrů typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="7460d-110">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="7460d-111">Předávání parametrů typu odkazu</span><span class="sxs-lookup"><span data-stu-id="7460d-111">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="7460d-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7460d-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7460d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7460d-113">See Also</span></span>  
 [<span data-ttu-id="7460d-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="7460d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7460d-115">Metody</span><span class="sxs-lookup"><span data-stu-id="7460d-115">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
