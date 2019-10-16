---
title: '|| ANI (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 6437b17fe1c1277701f06988ef6c02f4caf70e62
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319473"
---
# <a name="-or-entity-sql"></a>|| ANI (Entity SQL)
Kombinuje dva výrazy `Boolean`.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
boolean_expression OR boolean_expression  
-- or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Libovolný platný výraz, který vrací `Boolean`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, pokud je některá z podmínek `true`; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 NEBO je logický operátor [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Používá se ke kombinování dvou podmínek. Je-li v příkazu použit více než jeden logický operátor nebo jsou operátory vyhodnoceny po operátoru AND. Pořadí vyhodnocování však můžete změnit pomocí závorek.  
  
 Dvojité svislé čáry (&#124;&#124;) mají stejné funkce jako operátor OR.  
  
 V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|PODMÍNKA|PODMÍNKA|PODMÍNKA|  
|`FALSE`|PODMÍNKA|CHYBNÉ|NULL|  
|`NULL`|PODMÍNKA|NULL|NULL|  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru OR kombinuje dva výrazy `Boolean`. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
