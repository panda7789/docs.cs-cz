---
title: '&amp;&amp; (AND) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eab05f7454f8ebc88ed29030503bfa96d0c70756
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308429"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp; (AND) (Entity SQL)
Vrátí `true` Pokud jsou oba výrazy `true`; v opačném případě `false` nebo `NULL`.  
  
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
  
 Následující tabulka uvádí možné vstupní hodnoty a návratové typy.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|HODNOTA TRUE|FALSE|NULL|  
|`FALSE`|FALSE|FALSE|FALSE|  
|`NULL`|NULL|FALSE|NULL|  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL ukazuje, jak použít operátor AND. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
