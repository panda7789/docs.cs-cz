---
title: "Rozlišení přetížení funkce (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cafbdd1a06ce506516fa985e9af147f55b4ea3d4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="f0798-102">Rozlišení přetížení funkce (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="f0798-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="f0798-103">Toto téma popisuje, jak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkce jsou vyřešeny.</span><span class="sxs-lookup"><span data-stu-id="f0798-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="f0798-104">Se stejným názvem, lze definovat více než jednu funkci, tak dlouho, dokud funkce mít jedinečné podpisy.</span><span class="sxs-lookup"><span data-stu-id="f0798-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="f0798-105">Pokud to tento případ, musí provést následující kritéria k určení, funkci, která odkazuje daném výrazu.</span><span class="sxs-lookup"><span data-stu-id="f0798-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="f0798-106">Tato kritéria použijí v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f0798-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="f0798-107">První kritérium, které se vztahují pouze k jedné funkce je vyřešen funkce.</span><span class="sxs-lookup"><span data-stu-id="f0798-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1.  <span data-ttu-id="f0798-108">**Parametr číslo**.</span><span class="sxs-lookup"><span data-stu-id="f0798-108">**Parameter number**.</span></span> <span data-ttu-id="f0798-109">Funkce má stejný počet parametrů zadaný ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="f0798-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2.  <span data-ttu-id="f0798-110">**Přesná shoda podle typu**.</span><span class="sxs-lookup"><span data-stu-id="f0798-110">**Exact match on type**.</span></span> <span data-ttu-id="f0798-111">Každý typ argumentu funkce přesně odpovídá typ parametru, nebo je literál null.</span><span class="sxs-lookup"><span data-stu-id="f0798-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3.  <span data-ttu-id="f0798-112">**Shoda podle dílčí**.</span><span class="sxs-lookup"><span data-stu-id="f0798-112">**Match on subtype**.</span></span> <span data-ttu-id="f0798-113">Každý typ argumentu funkce přesně odpovídá nebo je typu dílčí parametr typu nebo argument je literál null.</span><span class="sxs-lookup"><span data-stu-id="f0798-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="f0798-114">V případě, že několik funkcí se liší pouze v počet dílčí typ převody vyžadovaných, funkce se nejmenší počet převody dílčí typ je vyřešen funkce.</span><span class="sxs-lookup"><span data-stu-id="f0798-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4.  <span data-ttu-id="f0798-115">**Shoda podle dílčí nebo typu povýšení**.</span><span class="sxs-lookup"><span data-stu-id="f0798-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="f0798-116">Každý typ argumentu funkce přesně odpovídá, je dílčí typ nebo můžete zvýšit na typ parametru nebo argument je literál null.</span><span class="sxs-lookup"><span data-stu-id="f0798-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="f0798-117">Znovu, v případě, že několik funkcí liší pouze v počtu dílčí typ převody a reklamními nabídkami, funkce se nejmenší počet dílčí typ převody a reklamními nabídkami je vyřešen funkce.</span><span class="sxs-lookup"><span data-stu-id="f0798-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="f0798-118">Pokud žádná z těchto kritérií výsledek v jedné vybrat funkce, je výraz volání funkce nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="f0798-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="f0798-119">I v případě jedné funkce lze extrahovat pomocí těchto pravidel, argumenty stále nemusí odpovídat parametrům.</span><span class="sxs-lookup"><span data-stu-id="f0798-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="f0798-120">V takovém případě je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="f0798-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="f0798-121">Pro uživatelsky definované funkce definici vložená funkce dotazu má přednost před i v případě, že funkce definované v modelu existuje podpisem, který představuje lepší shodu pro uživatelsky definované funkce.</span><span class="sxs-lookup"><span data-stu-id="f0798-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0798-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0798-122">See Also</span></span>  
 [<span data-ttu-id="f0798-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f0798-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="f0798-124">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f0798-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="f0798-125">Funkce</span><span class="sxs-lookup"><span data-stu-id="f0798-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
