---
title: let – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: a6eee9a23fa28b78343e6479106eaa24ecf4caa6
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795362"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="9588a-102">let – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9588a-102">let clause (C# Reference)</span></span>

<span data-ttu-id="9588a-103">Ve výrazu dotazu je někdy užitečné ukládat výsledek dílčího výrazu, aby jej bylo možné použít v dalších klauzulích.</span><span class="sxs-lookup"><span data-stu-id="9588a-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="9588a-104">Můžete to provést pomocí `let` klíčového slova, které vytvoří novou proměnnou rozsahu a inicializuje ji s výsledkem výrazu, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="9588a-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="9588a-105">Po inicializaci s hodnotou nelze proměnnou rozsahu použít k uložení jiné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9588a-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="9588a-106">Nicméně pokud proměnná rozsahu obsahuje typ Queryable, může se dotazovat.</span><span class="sxs-lookup"><span data-stu-id="9588a-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="9588a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="9588a-107">Example</span></span>

<span data-ttu-id="9588a-108">V následujícím příkladu `let` se používá dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="9588a-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="9588a-109">Pro vytvoření vyčíslitelného typu, který se může dotazovat sám na sebe.</span><span class="sxs-lookup"><span data-stu-id="9588a-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="9588a-110">Aby dotaz mohl volat `ToLower` pouze jednou pro proměnnou `word`rozsahu.</span><span class="sxs-lookup"><span data-stu-id="9588a-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="9588a-111">Bez použití `let`by bylo nutné zavolat `ToLower` do každého predikátu v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9588a-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="9588a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9588a-112">See also</span></span>

- [<span data-ttu-id="9588a-113">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9588a-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9588a-114">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9588a-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="9588a-115">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="9588a-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="9588a-116">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="9588a-116">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="9588a-117">Zpracování výjimek ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="9588a-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
