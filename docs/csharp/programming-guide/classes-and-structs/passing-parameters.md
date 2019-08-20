---
title: Předávání parametrů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 1c42ce7b258ca35d4e91e1ef28c71b60fe1f01de
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596251"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="9ecc1-102">Předávání parametrů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9ecc1-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="9ecc1-103">V C#nástroji mohou být argumenty předány parametrům buď podle hodnoty, nebo podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="9ecc1-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="9ecc1-104">Předání odkazem umožňuje členům funkce, metodám, vlastnostem, indexerům, operátorům a konstruktorům změnit hodnotu parametrů a tuto změnu zachovat v volajícím prostředí.</span><span class="sxs-lookup"><span data-stu-id="9ecc1-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="9ecc1-105">Chcete-li předat parametr odkazem s záměrem změnit hodnotu, použijte `ref`klíčové slovo or. `out`</span><span class="sxs-lookup"><span data-stu-id="9ecc1-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="9ecc1-106">Chcete-li předat odkaz s záměrem vyhnout se kopírování, ale nikoli změně hodnoty, použijte `in` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="9ecc1-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="9ecc1-107">Pro jednoduchost se v příkladech v tomto tématu používá jenom `ref` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9ecc1-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="9ecc1-108">Další informace o `in`rozdílu mezi, `out` `ref`a naleznete v části [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)a [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="9ecc1-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="9ecc1-109">Následující příklad znázorňuje rozdíl mezi parametry value a reference.</span><span class="sxs-lookup"><span data-stu-id="9ecc1-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="9ecc1-110">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9ecc1-110">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="9ecc1-111">Předávání parametrů typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="9ecc1-111">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="9ecc1-112">Předávání parametrů typu odkazu</span><span class="sxs-lookup"><span data-stu-id="9ecc1-112">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="9ecc1-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9ecc1-113">C# Language Specification</span></span>  

<span data-ttu-id="9ecc1-114">Další informace naleznete v tématu [seznam argumentů](~/_csharplang/spec/expressions.md#argument-lists) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ecc1-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="9ecc1-115">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9ecc1-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9ecc1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ecc1-116">See also</span></span>

- [<span data-ttu-id="9ecc1-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9ecc1-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9ecc1-118">Metody</span><span class="sxs-lookup"><span data-stu-id="9ecc1-118">Methods</span></span>](./methods.md)
