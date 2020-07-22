---
title: Předávání parametrů – Průvodce programováním v C#
description: Argument můžete předat parametru v jazyce C# podle hodnoty nebo odkazu. Změny argumentu předaného odkazem jsou trvalé. Použijte ref nebo out pro předání odkazem.
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 875a42aacf3d7aa4124684aefafdcb07ff4c87d6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864732"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="662f5-105">Předávání parametrů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="662f5-105">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="662f5-106">V jazyce C# mohou být argumenty předány parametrům buď podle hodnoty, nebo podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="662f5-106">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="662f5-107">Předání odkazem umožňuje členům funkce, metodám, vlastnostem, indexerům, operátorům a konstruktorům změnit hodnotu parametrů a tuto změnu zachovat v volajícím prostředí.</span><span class="sxs-lookup"><span data-stu-id="662f5-107">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="662f5-108">Chcete-li předat parametr odkazem s záměrem změnit hodnotu, použijte `ref` `out` klíčové slovo or.</span><span class="sxs-lookup"><span data-stu-id="662f5-108">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="662f5-109">Chcete-li předat odkaz s záměrem vyhnout se kopírování, ale nikoli změně hodnoty, použijte `in` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="662f5-109">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="662f5-110">Pro jednoduchost se `ref` v příkladech v tomto tématu používá jenom klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="662f5-110">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="662f5-111">Další informace o rozdílu mezi `in` , `ref` a naleznete `out` v části [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)a [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="662f5-111">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="662f5-112">Následující příklad znázorňuje rozdíl mezi parametry value a reference.</span><span class="sxs-lookup"><span data-stu-id="662f5-112">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="662f5-113">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="662f5-113">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="662f5-114">Předávání parametrů typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="662f5-114">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="662f5-115">Předávání parametrů typu odkazu</span><span class="sxs-lookup"><span data-stu-id="662f5-115">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="662f5-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="662f5-116">C# Language Specification</span></span>  

<span data-ttu-id="662f5-117">Další informace naleznete v tématu [seznam argumentů](~/_csharplang/spec/expressions.md#argument-lists) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="662f5-117">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="662f5-118">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="662f5-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="662f5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="662f5-119">See also</span></span>

- [<span data-ttu-id="662f5-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="662f5-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="662f5-121">Metody</span><span class="sxs-lookup"><span data-stu-id="662f5-121">Methods</span></span>](./methods.md)
