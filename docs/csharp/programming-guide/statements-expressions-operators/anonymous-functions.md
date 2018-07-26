---
title: Anonymní funkce (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: e368105c090f95435a4529470bdf1b41346d039c
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936747"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="77859-102">Anonymní funkce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="77859-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="77859-103">Anonymní funkce je "vloženě" příkaz nebo výraz, který se dá použít, kdykoli se očekává typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="77859-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="77859-104">Slouží k inicializaci pojmenovaný delegát nebo předat místo pojmenovaný delegát typu jako parametr metody.</span><span class="sxs-lookup"><span data-stu-id="77859-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="77859-105">Existují dva druhy anonymní funkce, které jsou jednotlivě podrobněji popsána v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="77859-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="77859-106">[Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="77859-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="77859-107">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="77859-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="77859-108">Výrazy lambda mohou být vázány na stromy výrazů a také na delegáty.</span><span class="sxs-lookup"><span data-stu-id="77859-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="77859-109">Vývoj v jazyce C# delegátů</span><span class="sxs-lookup"><span data-stu-id="77859-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="77859-110">V jazyce C# 1.0 vytvořeného instanci delegáta explicitně inicializuje s metodu, která byla definována kdekoli v kódu.</span><span class="sxs-lookup"><span data-stu-id="77859-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="77859-111">2.0 C# představila koncept anonymní metody jako způsob, jak zapsat vložený nepojmenovaný výkazu bloků, které mohou být provedeny v vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="77859-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="77859-112">C# 3.0 představila výrazy lambda, které jsou v principu podobná anonymní metody, ale výrazová a stručné.</span><span class="sxs-lookup"><span data-stu-id="77859-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="77859-113">Tyto dvě funkce se souhrnně nazývají *anonymní funkce*.</span><span class="sxs-lookup"><span data-stu-id="77859-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="77859-114">Obecně platí, aplikace, jejichž cílem verze 3.5 a novější [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] by měl použití výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="77859-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="77859-115">Následující příklad ukazuje vývoj vytvoření delegáta z 1.0 C# do jazyka C# 3.0:</span><span class="sxs-lookup"><span data-stu-id="77859-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="77859-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="77859-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="77859-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77859-117">See also</span></span>

[<span data-ttu-id="77859-118">Příkazy, výrazy a operátory</span><span class="sxs-lookup"><span data-stu-id="77859-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
[<span data-ttu-id="77859-119">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="77859-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
[<span data-ttu-id="77859-120">Delegáti</span><span class="sxs-lookup"><span data-stu-id="77859-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
[<span data-ttu-id="77859-121">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="77859-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)  
