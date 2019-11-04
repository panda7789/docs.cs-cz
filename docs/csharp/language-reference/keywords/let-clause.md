---
title: klauzule let – C# reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: df3df279d2dbdb59a0a94d9afad37d1a7ddf7b57
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422702"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="2f23a-102">let – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2f23a-102">let clause (C# Reference)</span></span>

<span data-ttu-id="2f23a-103">Ve výrazu dotazu je někdy užitečné ukládat výsledek dílčího výrazu, aby jej bylo možné použít v dalších klauzulích.</span><span class="sxs-lookup"><span data-stu-id="2f23a-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="2f23a-104">Můžete to provést pomocí klíčového slova `let`, které vytvoří novou proměnnou rozsahu a inicializuje ji s výsledkem výrazu, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="2f23a-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="2f23a-105">Po inicializaci s hodnotou nelze proměnnou rozsahu použít k uložení jiné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2f23a-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="2f23a-106">Nicméně pokud proměnná rozsahu obsahuje typ Queryable, může se dotazovat.</span><span class="sxs-lookup"><span data-stu-id="2f23a-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="2f23a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f23a-107">Example</span></span>

<span data-ttu-id="2f23a-108">V následujícím příkladu `let` použít dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="2f23a-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="2f23a-109">Pro vytvoření vyčíslitelného typu, který se může dotazovat sám na sebe.</span><span class="sxs-lookup"><span data-stu-id="2f23a-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="2f23a-110">Chcete-li povolit, aby dotaz vyvolal `ToLower` pouze jednou pro proměnnou rozsahu `word`.</span><span class="sxs-lookup"><span data-stu-id="2f23a-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="2f23a-111">Bez použití `let`byste museli volat `ToLower` v každém predikátu v klauzuli `where`.</span><span class="sxs-lookup"><span data-stu-id="2f23a-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="2f23a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f23a-112">See also</span></span>

- [<span data-ttu-id="2f23a-113">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="2f23a-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="2f23a-114">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="2f23a-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="2f23a-115">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="2f23a-115">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="2f23a-116">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2f23a-116">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
- [<span data-ttu-id="2f23a-117">Zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="2f23a-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
