---
title: Řešení přetížení funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 0248fdd3f3ba6afb5c7edca740d9aad3ca74bd03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302514"
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="b3ddb-102">Řešení přetížení funkce (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b3ddb-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="b3ddb-103">Toto téma popisuje, jak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkce jsou vyřešeny.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="b3ddb-104">Se stejným názvem, lze definovat více než jednu funkci, za předpokladu funkce máte podpisů jedinečný.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="b3ddb-105">Pokud je to tento případ, se musí určit funkci, která odkazuje výraz použít následující kritéria.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="b3ddb-106">Tato kritéria se použijí v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="b3ddb-107">První kritérium, které se vztahuje pouze na jedné funkce je vyřešení funkce.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1. <span data-ttu-id="b3ddb-108">**Číslo parametru**.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-108">**Parameter number**.</span></span> <span data-ttu-id="b3ddb-109">Funkce má stejný počet parametrů zadaných ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2. <span data-ttu-id="b3ddb-110">**Přesná shoda podle typu**.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-110">**Exact match on type**.</span></span> <span data-ttu-id="b3ddb-111">Typ každého argumentu funkce přesně odpovídá typu parametru nebo je literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3. <span data-ttu-id="b3ddb-112">**Se vyhledala shoda podle podtyp**.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-112">**Match on subtype**.</span></span> <span data-ttu-id="b3ddb-113">Typ každého argumentu funkce přesně odpovídá nebo je podtyp typu parametru nebo argument je literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="b3ddb-114">V případě, že několik funkce se liší pouze v čísla převody dílčí typ nejde, funkce s nejmenší počet převody dílčí typ je vyřešení funkce.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4. <span data-ttu-id="b3ddb-115">**Se vyhledala shoda podle typu nebo podtypu povýšení**.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="b3ddb-116">Typ každého argumentu funkce přesně odpovídá, je dílčí typ nebo může být povýšen na typ parametru nebo argument je literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="b3ddb-117">Znovu v události, ke které několik funkcí se liší pouze v počtu dílčí typ převody a propagačních akcí, funkcí s nejmenší počet dílčí typ převody a propagační akce je vyřešení funkce.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="b3ddb-118">Pokud žádná z těchto kritérií výsledkem výběru jedné funkce je nejednoznačný výraz volání funkce.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="b3ddb-119">I v případě jedné funkce může být extrahována pomocí těchto pravidel, argumenty stále nemusí odpovídat parametrům.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="b3ddb-120">V tomto případě je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="b3ddb-121">Pro uživatelsky definované funkce definice pro vloženou funkci dotaz má přednost před i v případě, že funkce definované v modelu existuje s podpisem, který představuje lepší shodu pro uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="b3ddb-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ddb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3ddb-122">See also</span></span>

- [<span data-ttu-id="b3ddb-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b3ddb-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="b3ddb-124">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b3ddb-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="b3ddb-125">Funkce</span><span class="sxs-lookup"><span data-stu-id="b3ddb-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
