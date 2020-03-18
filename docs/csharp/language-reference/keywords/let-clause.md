---
title: let klauzule - C# Reference
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173585"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="7ba5e-102">let – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7ba5e-102">let clause (C# Reference)</span></span>

<span data-ttu-id="7ba5e-103">Ve výrazu dotazu je někdy užitečné uložit výsledek dílčího výrazu, aby bylo možné jej použít v následujících klauzulích.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="7ba5e-104">Můžete to provést `let` pomocí klíčového slova, které vytvoří novou proměnnou rozsahu a inicializuje ji s výsledkem výrazu, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="7ba5e-105">Po inicializování s hodnotou nelze proměnnou rozsahu použít k uložení jiné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="7ba5e-106">Pokud však proměnná rozsahu obsahuje dotazovatelný typ, může být dotazován.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="7ba5e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ba5e-107">Example</span></span>

<span data-ttu-id="7ba5e-108">V následujícím `let` příkladu se používá dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="7ba5e-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="7ba5e-109">Chcete-li vytvořit výčet typu, který může být sám dotazován.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="7ba5e-110">Chcete-li povolit `ToLower` dotaz volat pouze `word`jednou na proměnné rozsahu .</span><span class="sxs-lookup"><span data-stu-id="7ba5e-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="7ba5e-111">Bez `let`použití , budete `ToLower` muset volat v každém `where` predikátu v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="7ba5e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ba5e-112">See also</span></span>

- [<span data-ttu-id="7ba5e-113">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7ba5e-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="7ba5e-114">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7ba5e-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="7ba5e-115">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7ba5e-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="7ba5e-116">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="7ba5e-116">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="7ba5e-117">Zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="7ba5e-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
