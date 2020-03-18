---
title: Předávání parametrů – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 60ac7a8d982e7788f07debce114896859385c8e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705467"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="84b8c-102">Předávání parametrů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="84b8c-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="84b8c-103">V c#, argumenty mohou být předány parametry buď hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="84b8c-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="84b8c-104">Předávání odkazem umožňuje členům funkce, metodám, vlastnostem, indexerům, operátorům a konstruktorům změnit hodnotu parametrů a mít tuto změnu v prostředí volání zachovat.</span><span class="sxs-lookup"><span data-stu-id="84b8c-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="84b8c-105">Chcete-li předat parametr odkazem s úmyslem `ref`změnit `out` hodnotu, použijte klíčové slovo nebo klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="84b8c-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="84b8c-106">Chcete-li předat odkaz s úmyslem vyhnout se kopírování, `in` ale nemění hodnotu, použijte modifikátor.</span><span class="sxs-lookup"><span data-stu-id="84b8c-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="84b8c-107">Pro jednoduchost se v `ref` příkladech v tomto tématu používá pouze klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="84b8c-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="84b8c-108">Další informace `in`o rozdílu `ref`mezi `out`, , a , viz [v](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)a [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="84b8c-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="84b8c-109">Následující příklad ilustruje rozdíl mezi parametry hodnoty a referenční parametry.</span><span class="sxs-lookup"><span data-stu-id="84b8c-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="84b8c-110">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="84b8c-110">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="84b8c-111">Předávání parametrů typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="84b8c-111">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="84b8c-112">Předávání parametrů typu odkazu</span><span class="sxs-lookup"><span data-stu-id="84b8c-112">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="84b8c-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84b8c-113">C# Language Specification</span></span>  

<span data-ttu-id="84b8c-114">Další informace naleznete v [tématu Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="84b8c-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="84b8c-115">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="84b8c-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="84b8c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="84b8c-116">See also</span></span>

- [<span data-ttu-id="84b8c-117">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84b8c-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="84b8c-118">Metody</span><span class="sxs-lookup"><span data-stu-id="84b8c-118">Methods</span></span>](./methods.md)
