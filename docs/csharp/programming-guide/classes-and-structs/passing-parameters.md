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
ms.openlocfilehash: 22f58bda5aa5b60248902a4130f3ea9b6caa65cf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419128"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="233d0-102">Předávání parametrů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="233d0-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="233d0-103">V C#nástroji mohou být argumenty předány parametrům buď podle hodnoty, nebo podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="233d0-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="233d0-104">Předání odkazem umožňuje členům funkce, metodám, vlastnostem, indexerům, operátorům a konstruktorům změnit hodnotu parametrů a tuto změnu zachovat v volajícím prostředí.</span><span class="sxs-lookup"><span data-stu-id="233d0-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="233d0-105">Chcete-li předat parametr odkazem s záměrem změnit hodnotu, použijte klíčové slovo `ref`nebo `out`.</span><span class="sxs-lookup"><span data-stu-id="233d0-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="233d0-106">Chcete-li předat odkaz s záměrem vyhnout se kopírování, ale nezměnění hodnoty, použijte modifikátor `in`.</span><span class="sxs-lookup"><span data-stu-id="233d0-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="233d0-107">V případě jednoduchosti se v příkladech v tomto tématu používá pouze klíčové slovo `ref`.</span><span class="sxs-lookup"><span data-stu-id="233d0-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="233d0-108">Další informace o rozdílu mezi `in`, `ref`a `out`naleznete [v tématech in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)a [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="233d0-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="233d0-109">Následující příklad znázorňuje rozdíl mezi parametry value a reference.</span><span class="sxs-lookup"><span data-stu-id="233d0-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="233d0-110">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="233d0-110">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="233d0-111">Předávání parametrů typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="233d0-111">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="233d0-112">Předávání parametrů typu odkazu</span><span class="sxs-lookup"><span data-stu-id="233d0-112">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="233d0-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="233d0-113">C# Language Specification</span></span>  

<span data-ttu-id="233d0-114">Další informace naleznete v tématu [seznam argumentů](~/_csharplang/spec/expressions.md#argument-lists) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="233d0-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="233d0-115">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="233d0-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="233d0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="233d0-116">See also</span></span>

- [<span data-ttu-id="233d0-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="233d0-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="233d0-118">Metody</span><span class="sxs-lookup"><span data-stu-id="233d0-118">Methods</span></span>](./methods.md)
