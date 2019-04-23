---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: e14b7857a65898683939647c872c48d0b3fe458a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297860"
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
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Viz také:

- [Obory názvů](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
