---
title: "Nepodporované výrazy (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c18c726a962d9a29a3dace1ebd5c2073637bb4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unsupported-expressions-entity-sql"></a><span data-ttu-id="4ac70-102">Nepodporované výrazy (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="4ac70-102">Unsupported Expressions (Entity SQL)</span></span>
<span data-ttu-id="4ac70-103">Toto téma popisuje [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazy, které nejsou podporované v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ac70-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="4ac70-104">Další informace najdete v tématu [jak Entity SQL se liší od jazyka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4ac70-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>  
  
## <a name="quantified-predicates"></a><span data-ttu-id="4ac70-105">Kvantitativní predikáty</span><span class="sxs-lookup"><span data-stu-id="4ac70-105">Quantified Predicates</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="4ac70-106">Umožňuje konstrukce v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="4ac70-106"> allows constructs of the following form:</span></span>  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="4ac70-107">, ale nepodporuje takové konstrukce.</span><span class="sxs-lookup"><span data-stu-id="4ac70-107">, however, does not support such constructs.</span></span> <span data-ttu-id="4ac70-108">Ekvivalentní výrazy může být napsán v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4ac70-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## <a name="-operator"></a><span data-ttu-id="4ac70-109">* – operátor</span><span class="sxs-lookup"><span data-stu-id="4ac70-109">* Operator</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="4ac70-110">podporuje použití * operátor v klauzuli SELECT k označení, že všechny sloupce by měl promítat. To není podporováno v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ac70-110"> supports the use of the * operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac70-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ac70-111">See Also</span></span>  
 [<span data-ttu-id="4ac70-112">Přehled SQL entity</span><span class="sxs-lookup"><span data-stu-id="4ac70-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="4ac70-113">Jak se liší od Transact-SQL Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4ac70-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
