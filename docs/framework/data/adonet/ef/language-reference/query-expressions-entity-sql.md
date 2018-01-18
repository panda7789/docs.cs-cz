---
title: "Výrazy dotazů (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 46777cbe47e7d97fd3baaa1353787f33cff9f0aa
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="1f9da-102">Výrazy dotazů (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="1f9da-102">Query Expressions (Entity SQL)</span></span>
<span data-ttu-id="1f9da-103">Výraz dotazu kombinuje operátory mnoho různých dotazu do jednoho syntaxe.</span><span class="sxs-lookup"><span data-stu-id="1f9da-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1f9da-104">poskytuje různé druhy výrazů, včetně následujících: [literály](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [proměnné](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operátory, [funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), nastavte operátory a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1f9da-104"> provides various kinds of expressions, including the following: [literals](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parameters](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [variables](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operators, [functions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="1f9da-105">Další informace najdete v tématu [odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="1f9da-105">For more information, see [Entity SQL Reference](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="1f9da-106">Klauzule</span><span class="sxs-lookup"><span data-stu-id="1f9da-106">Clauses</span></span>  
 <span data-ttu-id="1f9da-107">Výraz dotazu se skládá z řady klauzule, která se týkají po sobě jdoucích operací na kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="1f9da-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="1f9da-108">Jsou založené na stejné klauzule nalezena ve verzi standard vyberte příkaz SQL: [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [kde](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [s](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), a [řadit podle](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1f9da-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), and [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="1f9da-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1f9da-109">Scope</span></span>  
 <span data-ttu-id="1f9da-110">Názvy definované v klauzuli FROM vydávají do oboru FROM v pořadí podle vzhled, zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="1f9da-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="1f9da-111">V seznamu připojení výrazy mohou odkazovat na názvy definované výše v seznamu.</span><span class="sxs-lookup"><span data-stu-id="1f9da-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="1f9da-112">Veřejné vlastnosti elementů určené v klauzuli FROM nejsou přidány do oboru FROM: musí být vždy odkazuje prostřednictvím alias kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="1f9da-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="1f9da-113">Za normálních okolností jsou považovány všechny části vyberte výrazu za v rámci oboru FROM.</span><span class="sxs-lookup"><span data-stu-id="1f9da-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9da-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f9da-114">See Also</span></span>  
 [<span data-ttu-id="1f9da-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1f9da-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
