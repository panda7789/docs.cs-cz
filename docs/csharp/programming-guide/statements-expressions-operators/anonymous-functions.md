---
title: "Anonymní funkce (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 888743bb1c49df123b57b4d09e0251dbe1e049d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="be065-102">Anonymní funkce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="be065-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="be065-103">Anonymní funkce je "vložené" příkaz nebo výraz, který lze použít bez ohledu na očekáván je typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="be065-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="be065-104">Můžete ji k inicializaci pojmenované delegáta nebo předat místo typu s názvem delegáta jako parametr metody.</span><span class="sxs-lookup"><span data-stu-id="be065-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="be065-105">Existují dva druhy anonymní funkce, které jsou jednotlivě popsané v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="be065-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="be065-106">[Lambda – výrazy](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="be065-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="be065-107">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="be065-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="be065-108">Lambda – výrazy mohou být vázány stromů výrazů a delegáti.</span><span class="sxs-lookup"><span data-stu-id="be065-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="be065-109">Vývoj Delegáti v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="be065-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="be065-110">V C# 1.0 jste vytvořili instanci delegáta pomocí explicitní inicializaci pomocí metody, která byla definována někde v kódu.</span><span class="sxs-lookup"><span data-stu-id="be065-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="be065-111">C# 2.0 zaveden koncept anonymní metody jako způsob, jak zapisuje nepojmenované vložené příkaz bloky, které mohou být provedeny v vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="be065-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="be065-112">Lambda – výrazy, které jsou v principu podobná anonymní metody ale výrazovou a stručným se zavedl C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="be065-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="be065-113">Tyto dvě funkce se souhrnně označují jako *anonymní funkce*.</span><span class="sxs-lookup"><span data-stu-id="be065-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="be065-114">Obecně platí, aplikace, jejichž cílem verze 3.5 nebo novější z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] by použití výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="be065-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="be065-115">Následující příklad ukazuje vývoj delegáta vytvoření z jazyka C# 1.0 pro C# 3.0:</span><span class="sxs-lookup"><span data-stu-id="be065-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="be065-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="be065-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="be065-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="be065-117">See Also</span></span>  
 [<span data-ttu-id="be065-118">Příkazy, výrazy a operátory</span><span class="sxs-lookup"><span data-stu-id="be065-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [<span data-ttu-id="be065-119">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="be065-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="be065-120">Delegáti</span><span class="sxs-lookup"><span data-stu-id="be065-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="be065-121">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="be065-121">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
