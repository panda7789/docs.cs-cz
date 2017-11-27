---
title: "let – klauzule (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 077c5178946b85d0fb85aa8da94966e4c5821736
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="d4909-102">let – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d4909-102">let clause (C# Reference)</span></span>
<span data-ttu-id="d4909-103">Ve výrazu dotazu je někdy užitečné k ukládání výsledků dílčí výrazu, aby bylo možné používat v dalších klauzule.</span><span class="sxs-lookup"><span data-stu-id="d4909-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="d4909-104">Můžete to provést pomocí `let` – klíčové slovo, které vytvoří novou proměnnou rozsahu a inicializuje s výsledkem výrazu zadáte.</span><span class="sxs-lookup"><span data-stu-id="d4909-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="d4909-105">Jakmile inicializovaný s hodnotou, proměnnou rozsahu nelze použít k uložení jinou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d4909-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="d4909-106">Ale pokud proměnnou rozsahu obsahuje dotazovatelné typu, může být dotazován.</span><span class="sxs-lookup"><span data-stu-id="d4909-106">However, if the range variable holds a queryable type, it can be queried.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4909-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4909-107">Example</span></span>  
 <span data-ttu-id="d4909-108">V následujícím příkladu `let` slouží dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="d4909-108">In the following example `let` is used in two ways:</span></span>  
  
1.  <span data-ttu-id="d4909-109">Chcete-li vytvořit vyčíslitelná typ, který je možné samotné dotázat.</span><span class="sxs-lookup"><span data-stu-id="d4909-109">To create an enumerable type that can itself be queried.</span></span>  
  
2.  <span data-ttu-id="d4909-110">Chcete-li povolit dotaz pro volání `ToLower` jenom jednou na proměnnou rozsahu `word`.</span><span class="sxs-lookup"><span data-stu-id="d4909-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="d4909-111">Bez použití `let`, budete muset volat `ToLower` v každé predikát `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="d4909-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d4909-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4909-112">See Also</span></span>  
 [<span data-ttu-id="d4909-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d4909-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d4909-114">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d4909-114">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="d4909-115">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="d4909-115">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="d4909-116">Začínáme s dotazy LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="d4909-116">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="d4909-117">Postupy: zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="d4909-117">How to: Handle Exceptions in Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)
