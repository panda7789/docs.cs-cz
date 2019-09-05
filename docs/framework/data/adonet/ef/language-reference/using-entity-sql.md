---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 9495e5daf88326c5a682172d835c3349fe79e571
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248751"
---
# <a name="using-entity-sql"></a>USING (Entity SQL)
Určuje obory názvů použité ve výrazu dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  
 `alias`  
 Určuje kratší alias pro získání oboru názvů pomocí.  
  
 `namespace`  
 Libovolný platný obor názvů.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru USING určí obory názvů použité ve výrazu dotazu. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Viz také:

- [Obory názvů](namespaces-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
