---
title: '|| (NEBO) (Entita SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 8c93e68095a0e0ff63532f53152f166d6c3d047c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150090"
---
# <a name="-or-entity-sql"></a>|| (NEBO) (Entita SQL)
Kombinuje dva `Boolean` výrazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `boolean_expression`  
 Libovolný platný výraz, `Boolean`který vrací .  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`pokud je `true`některá z podmínek ; v `false`opačném případě .  
  
## <a name="remarks"></a>Poznámky  
 NEBO je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logický operátor. Používá se ke kombinaci dvou podmínek. Pokud je v příkazu použito více než jeden logický operátor, operátory OR jsou vyhodnoceny po operátorech AND. Pořadí hodnocení však můžete změnit pomocí závorek.  
  
 Dvojité svislé pruhy (&#124;&#124;) mají stejné funkce jako operátor OR.  
  
 V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Příklad  
 Následující dotaz ENTITY SQL používá operátor `Boolean` OR ke sloučení dvou výrazů. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
