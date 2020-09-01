---
description: let – Referenční dokumentace jazyka C#
title: let – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3767b9745cccd9802374a8100de19f286c9b55ea
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139590"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="6c650-103">let – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6c650-103">let clause (C# Reference)</span></span>

<span data-ttu-id="6c650-104">Ve výrazu dotazu je někdy užitečné ukládat výsledek dílčího výrazu, aby jej bylo možné použít v dalších klauzulích.</span><span class="sxs-lookup"><span data-stu-id="6c650-104">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="6c650-105">Můžete to provést pomocí `let` klíčového slova, které vytvoří novou proměnnou rozsahu a inicializuje ji s výsledkem výrazu, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="6c650-105">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="6c650-106">Po inicializaci s hodnotou nelze proměnnou rozsahu použít k uložení jiné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6c650-106">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="6c650-107">Nicméně pokud proměnná rozsahu obsahuje typ Queryable, může se dotazovat.</span><span class="sxs-lookup"><span data-stu-id="6c650-107">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="6c650-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c650-108">Example</span></span>

<span data-ttu-id="6c650-109">V následujícím příkladu `let` se používá dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="6c650-109">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="6c650-110">Pro vytvoření vyčíslitelného typu, který se může dotazovat sám na sebe.</span><span class="sxs-lookup"><span data-stu-id="6c650-110">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="6c650-111">Aby dotaz mohl volat `ToLower` pouze jednou pro proměnnou rozsahu `word` .</span><span class="sxs-lookup"><span data-stu-id="6c650-111">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="6c650-112">Bez použití by bylo `let` nutné zavolat `ToLower` do každého predikátu v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6c650-112">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="6c650-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c650-113">See also</span></span>

- [<span data-ttu-id="6c650-114">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6c650-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6c650-115">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6c650-115">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="6c650-116">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="6c650-116">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="6c650-117">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="6c650-117">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="6c650-118">Zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="6c650-118">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
