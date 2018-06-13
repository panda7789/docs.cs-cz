---
title: Předávání parametrů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: a1ccfff8081d101eee46360009653b0591dfb3ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323102"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="01efe-102">Předávání parametrů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="01efe-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="01efe-103">V jazyce C# argumenty můžete předat parametry hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="01efe-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="01efe-104">Předání odkazem umožňuje funkce členy, metody, vlastnosti, indexery, operátory a konstruktory změna hodnoty parametrů a tato změna uchování v volání prostředí.</span><span class="sxs-lookup"><span data-stu-id="01efe-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="01efe-105">Chcete-li předat parametr odkazem se záměrem změna hodnoty, použijte `ref`, nebo `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="01efe-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="01efe-106">Chcete-li předat odkazem se záměrem vyhnout kopírování, ale není změna hodnoty, použijte `in` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="01efe-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="01efe-107">Pro jednoduchost, jenom `ref` – klíčové slovo se používá v příkladech v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="01efe-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="01efe-108">Další informace o rozdílu mezi `in`, `ref`, a `out`, najdete v části [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), a [ Předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="01efe-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="01efe-109">Následující příklad ukazuje rozdíl mezi parametry hodnoty a odkazu.</span><span class="sxs-lookup"><span data-stu-id="01efe-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="01efe-110">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="01efe-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="01efe-111">Předávání parametrů typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="01efe-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="01efe-112">Předávání parametrů typu odkazu</span><span class="sxs-lookup"><span data-stu-id="01efe-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="01efe-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01efe-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="01efe-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="01efe-114">See Also</span></span>  
 [<span data-ttu-id="01efe-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="01efe-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="01efe-116">Metody</span><span class="sxs-lookup"><span data-stu-id="01efe-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
