---
title: KEY (Entita SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 894a9d41aa3a14ad66b537433aa315823a299f95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150166"
---
# <a name="key-entity-sql"></a>KEY (Entita SQL)
Extrahuje klíč odkazu nebo výrazu entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíč entity obsahuje hodnoty klíče ve správném pořadí zadaného odkazu entity nebo entity. Vzhledem k tomu, že více sad entit může být založeno na stejném typu, může se v každé sadě entit objevit stejný klíč. Chcete-li získat jedinečný `REF`odkaz, použijte . Návratový typ operátoru KEY je typ řádku, který obsahuje jedno pole pro každý klíč entity ve stejném pořadí.  
  
 V následujícím příkladu je operátor klíče předán odkaz na entitu BadOrder a vrátí klíčovou část tohoto odkazu. V tomto případě typ záznamu s přesně `Id` jedním polem odpovídajícím vlastnosti.  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a>Příklad  
 Následující dotaz entity SQL používá operátor KEY k extrahování klíčové části výrazu s odkazem na typ. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [Ref](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
