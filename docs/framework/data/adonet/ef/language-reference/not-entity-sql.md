---
title: '! (NE) (Entita SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0b69d4cb64adc1f9232631d50ec42af0d1ba47e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150126"
---
# <a name="-not-entity-sql"></a>! (NE) (Entita SQL)
Neguje `Boolean` výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a>Argumenty  
 `boolean_expression`  
 Libovolný platný výraz, který vrací logickou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Vykřičník (!) má stejné funkce jako operátor NOT.  
  
## <a name="example"></a>Příklad  
 Následující dotaz ENTITY SQL používá operátor NOT `Boolean` k negování výrazu. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
