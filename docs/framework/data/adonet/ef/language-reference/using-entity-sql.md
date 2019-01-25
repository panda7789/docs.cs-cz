---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: a07ee1c32a93ee22b7418784fbd893e7699c553e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744294"
---
# <a name="using-entity-sql"></a>USING (Entity SQL)
Určuje obor názvů použít ve výrazu dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  
 `alias`  
 Určuje kratší alias k určení oboru názvů s.  
  
 `namespace`  
 Libovolný platný obor názvů.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor použití k zadávání oborů názvů použít ve výrazu dotazu. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Viz také:
- [Obory názvů](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
