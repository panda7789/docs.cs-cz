---
title: '|| ANI (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: c88e041638fbe6f32717ce9c4f9c2ff6fb56d803
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249763"
---
# <a name="-or-entity-sql"></a>|| ANI (Entity SQL)
Kombinuje dva `Boolean` výrazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Libovolný platný výraz, který vrátí `Boolean`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je `true`jedna z podmínek, `false`v opačném případě.  
  
## <a name="remarks"></a>Poznámky  
 Nebo je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logický operátor. Používá se ke kombinování dvou podmínek. Je-li v příkazu použit více než jeden logický operátor nebo jsou operátory vyhodnoceny po operátoru AND. Pořadí vyhodnocování však můžete změnit pomocí závorek.  
  
 Dvojité svislé čáry (&#124;&#124;) mají stejné funkce jako operátor OR.  
  
 V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|PODMÍNKA|PODMÍNKA|PODMÍNKA|  
|`FALSE`|PODMÍNKA|CHYBNÉ|NULL|  
|`NULL`|PODMÍNKA|NULL|NULL|  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru OR kombinuje dva `Boolean` výrazy. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
