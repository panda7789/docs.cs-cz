---
title: '&amp;&amp;ANI (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 02e404b73e5a9a9c3963e2d2b58ab7592afabc13
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251318"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp;ANI (Entity SQL)
Vrátí `true` , zda jsou `true`oba výrazy; v `false` opačném případě nebo `NULL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Libovolný platný výraz, který vrací logickou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Dvojité ampersandy (& &) mají stejné funkce jako operátor AND.  
  
 V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|PODMÍNKA|CHYBNÉ|NULL|  
|`FALSE`|CHYBNÉ|CHYBNÉ|CHYBNÉ|  
|`NULL`|NULL|CHYBNÉ|NULL|  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz ukazuje použití operátoru AND. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
