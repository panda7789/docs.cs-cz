---
title: '&amp;&amp; (a) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: be6e7120e6c19714f151aa38a8b9a1355de29d1a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039954"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp; (a) (Entity SQL)
Vrátí `true`, pokud jsou oba výrazy `true`; v opačném případě `false` nebo `NULL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
boolean_expression AND boolean_expression
```
 
or  

```csharp
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
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
