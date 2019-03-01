---
title: Předávání parametrů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: c8da86d2a8f5101acf5b9cc1bcc2f9ad50378fa4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969541"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="530e1-102">Předávání parametrů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="530e1-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="530e1-103">V jazyce C# argumenty lze předat parametry podle hodnoty nebo odkazu.</span><span class="sxs-lookup"><span data-stu-id="530e1-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="530e1-104">Předávání odkazem umožňuje funkce členy, metody, vlastnosti, indexery, operátory a konstruktory měnit hodnoty parametrů a jste tuto změnu uchování v volajícího prostředí.</span><span class="sxs-lookup"><span data-stu-id="530e1-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="530e1-105">Chcete-li předat parametr odkazem s cílem změnit hodnotu, použijte `ref`, nebo `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="530e1-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="530e1-106">Předávání pomocí odkazu s cílem vyhnout kopírování, ale nemění hodnoty, použijte `in` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="530e1-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="530e1-107">Pro jednoduchost, pouze `ref` – klíčové slovo se používá v příkladech v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="530e1-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="530e1-108">Další informace o rozdílech mezi `in`, `ref`, a `out`, naleznete v tématu [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), a [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="530e1-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="530e1-109">Následující příklad ukazuje rozdíl mezi hodnotou a odkaz na parametry.</span><span class="sxs-lookup"><span data-stu-id="530e1-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="530e1-110">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="530e1-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="530e1-111">Předávání parametrů typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="530e1-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="530e1-112">Předávání parametrů typu odkazu</span><span class="sxs-lookup"><span data-stu-id="530e1-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="530e1-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="530e1-113">C# Language Specification</span></span>  

<span data-ttu-id="530e1-114">Další informace najdete v tématu [seznamy argumentů](~/_csharplang/spec/expressions.md#argument-lists) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="530e1-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="530e1-115">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="530e1-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="530e1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="530e1-116">See also</span></span>

- [<span data-ttu-id="530e1-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="530e1-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="530e1-118">Metody</span><span class="sxs-lookup"><span data-stu-id="530e1-118">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
