---
title: Řešení přetížení funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 1aeebc501487a6fc443df00c24beb2bc6aa5fc49
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250924"
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="4b199-102">Řešení přetížení funkce (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4b199-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="4b199-103">Toto téma popisuje, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jak jsou funkce vyřešeny.</span><span class="sxs-lookup"><span data-stu-id="4b199-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="4b199-104">Více než jedna funkce může být definována se stejným názvem, pokud funkce mají jedinečné podpisy.</span><span class="sxs-lookup"><span data-stu-id="4b199-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="4b199-105">V takovém případě je nutné použít následující kritéria k určení, na kterou funkci odkazuje daný výraz.</span><span class="sxs-lookup"><span data-stu-id="4b199-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="4b199-106">Tato kritéria se aplikují v pořadí.</span><span class="sxs-lookup"><span data-stu-id="4b199-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="4b199-107">První kritérium, které platí pouze pro jednu funkci, je vyřešená funkce.</span><span class="sxs-lookup"><span data-stu-id="4b199-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1. <span data-ttu-id="4b199-108">**Číslo parametru**</span><span class="sxs-lookup"><span data-stu-id="4b199-108">**Parameter number**.</span></span> <span data-ttu-id="4b199-109">Funkce má stejný počet parametrů, které jsou zadány ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="4b199-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2. <span data-ttu-id="4b199-110">**Přesná shoda typu**</span><span class="sxs-lookup"><span data-stu-id="4b199-110">**Exact match on type**.</span></span> <span data-ttu-id="4b199-111">Každý typ argumentu funkce přesně odpovídá typu parametru, nebo je literál null.</span><span class="sxs-lookup"><span data-stu-id="4b199-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3. <span data-ttu-id="4b199-112">**Shoda s podtypem**</span><span class="sxs-lookup"><span data-stu-id="4b199-112">**Match on subtype**.</span></span> <span data-ttu-id="4b199-113">Každý typ argumentu funkce přesně odpovídá nebo je dílčí typ typu parametru, nebo je argumentem nulový literál.</span><span class="sxs-lookup"><span data-stu-id="4b199-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="4b199-114">V případě, že se několik funkcí liší pouze v případě vyžadovaných převodů dílčího typu, funkce s nejmenším počtem převodů dílčího typu je vyřešená funkce.</span><span class="sxs-lookup"><span data-stu-id="4b199-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4. <span data-ttu-id="4b199-115">**Shoda s podtypem nebo povýšením typu**.</span><span class="sxs-lookup"><span data-stu-id="4b199-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="4b199-116">Každý typ argumentu funkce přesně odpovídá, je dílčí typ, nebo může být povýšen na typ parametru, nebo je argumentem nulový literál.</span><span class="sxs-lookup"><span data-stu-id="4b199-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="4b199-117">V případě, že se několik funkcí liší pouze v počtu převodů dílčích typů a propagačních akcí, funkce s nejmenším počtem převodů dílčích typů a propagační akce je vyřešená funkce.</span><span class="sxs-lookup"><span data-stu-id="4b199-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="4b199-118">Pokud žádný z těchto kritérií nevede k výběru jedné funkce, výraz volání funkce je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="4b199-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="4b199-119">I když může být jedna funkce extrahována pomocí těchto pravidel, argumenty stále nemusí odpovídat parametrům.</span><span class="sxs-lookup"><span data-stu-id="4b199-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="4b199-120">V tomto případě se vyvolá chyba.</span><span class="sxs-lookup"><span data-stu-id="4b199-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="4b199-121">V případě uživatelsky definovaných funkcí má definice vložené funkce dotazu přednost i v případě, že existuje funkce definovaná modelem s podpisem, který je lepší shodou uživatelsky definované funkce.</span><span class="sxs-lookup"><span data-stu-id="4b199-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b199-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b199-122">See also</span></span>

- [<span data-ttu-id="4b199-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4b199-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="4b199-124">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4b199-124">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="4b199-125">Funkce</span><span class="sxs-lookup"><span data-stu-id="4b199-125">Functions</span></span>](functions-entity-sql.md)
