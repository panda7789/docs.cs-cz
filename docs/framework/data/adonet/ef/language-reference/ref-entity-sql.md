---
title: REF (Entita SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 40a5afd7eb99dba7cae8fe14ed0a45213fda94a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149944"
---
# <a name="ref-entity-sql"></a>REF (Entita SQL)
Vrátí odkaz na instanci entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Libovolný platný výraz, který poskytuje instanci typu entity.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na zadanou instanci entity.  
  
## <a name="remarks"></a>Poznámky  
 Odkaz na entitu se skládá z klíče entity a názvu sady entit. Vzhledem k tomu, že různé sady entit mohou být založeny na stejném typu entity, může se určitý klíč entity zobrazit ve více sadách entit. Odkaz na entitu je však vždy jedinečný. Pokud vstupní výraz představuje trvalou entitu, bude vrácen odkaz na tuto entitu. Pokud vstupní výraz není trvalá entita, bude vrácen nulový odkaz.  
  
 Pokud operátor extrakce vlastnosti (.) se používá pro přístup k vlastnosti entity, odkaz je automaticky dereferenced.  
  
## <a name="example"></a>Příklad  
 Následující dotaz ENTITY SQL používá operátor REF k vrácení odkazu pro argument vstupní entity. Stejný dotaz dereferences odkaz, protože používáme operace extrakce vlastnosti (.) pro přístup k vlastnosti Product entity. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a>Viz také

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [Klíč](key-entity-sql.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [Definice typů](type-definitions-entity-sql.md)
