---
title: Anonymní funkce - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: c949bf5af441728b311391ecb42623951d0145ab
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608151"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="43b2a-102">Anonymní funkce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="43b2a-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="43b2a-103">Anonymní funkce je "vloženě" příkaz nebo výraz, který se dá použít, kdykoli se očekává typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="43b2a-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="43b2a-104">Slouží k inicializaci pojmenovaný delegát nebo předat místo pojmenovaný delegát typu jako parametr metody.</span><span class="sxs-lookup"><span data-stu-id="43b2a-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="43b2a-105">Existují dva druhy anonymní funkce, které jsou jednotlivě podrobněji popsána v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="43b2a-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
- <span data-ttu-id="43b2a-106">[Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="43b2a-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
- [<span data-ttu-id="43b2a-107">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="43b2a-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="43b2a-108">Výrazy lambda mohou být vázány na stromy výrazů a také na delegáty.</span><span class="sxs-lookup"><span data-stu-id="43b2a-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="43b2a-109">Vývoj delegátů v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="43b2a-109">The Evolution of Delegates in C\#</span></span>
 <span data-ttu-id="43b2a-110">V jazyce C# 1.0 vytvořeného instanci delegáta explicitně inicializuje s metodu, která byla definována kdekoli v kódu.</span><span class="sxs-lookup"><span data-stu-id="43b2a-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="43b2a-111">2.0 C# představila koncept anonymní metody jako způsob, jak zapsat vložený nepojmenovaný výkazu bloků, které mohou být provedeny v vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="43b2a-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="43b2a-112">C# 3.0 představila výrazy lambda, které jsou v principu podobná anonymní metody, ale výrazová a stručné.</span><span class="sxs-lookup"><span data-stu-id="43b2a-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="43b2a-113">Tyto dvě funkce se souhrnně nazývají *anonymní funkce*.</span><span class="sxs-lookup"><span data-stu-id="43b2a-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="43b2a-114">Obecně platí, aplikace, jejichž cílem verze 3.5 a novější [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] by měl použití výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="43b2a-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="43b2a-115">Následující příklad ukazuje vývoj vytvoření delegáta z 1.0 C# do jazyka C# 3.0:</span><span class="sxs-lookup"><span data-stu-id="43b2a-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="43b2a-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="43b2a-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="43b2a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43b2a-117">See also</span></span>

- [<span data-ttu-id="43b2a-118">Příkazy, výrazy a operátory</span><span class="sxs-lookup"><span data-stu-id="43b2a-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [<span data-ttu-id="43b2a-119">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="43b2a-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="43b2a-120">Delegáti</span><span class="sxs-lookup"><span data-stu-id="43b2a-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="43b2a-121">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="43b2a-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
