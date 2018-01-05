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
ms.workload: dotnet
ms.openlocfilehash: d80fc4fa3c0e57cfa10ead494248ae1966e28769
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="unsupported-expressions-entity-sql"></a>Nepodporované výrazy (entita SQL)
Toto téma popisuje [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výrazy, které nejsou podporované v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Další informace najdete v tématu [jak Entity SQL se liší od jazyka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).  
  
## <a name="quantified-predicates"></a>Kvantitativní predikáty  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]Umožňuje konstrukce v následujícím formátu:  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], ale nepodporuje takové konstrukce. Ekvivalentní výrazy může být napsán v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujícím způsobem:  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## <a name="-operator"></a>* – operátor  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]podporuje použití * operátor v klauzuli SELECT k označení, že všechny sloupce by měl promítat. To není podporováno v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Jak se Entity SQL liší od Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
