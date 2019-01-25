---
title: MEZI (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: cface8ab50e53f21293ad54ea6961c7e308080b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690689"
---
# <a name="between-entity-sql"></a>MEZI (Entity SQL)
Určuje, zda výraz výsledkem je hodnota v zadaném rozsahu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Mezi výrazu má stejné funkce jako výraz jazyka Transact-SQL mezi.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz pro testování v rozsahu definovaném touto `begin_expression` a `end_expression`. `expression` musí být stejného typu jako `begin_expression` a `end_expression`.  
  
 `begin_expression`  
 Libovolný platný výraz. `begin_expression` musí být stejného typu jako `expression` a `end_expression`. `begin_expression` by měla být menší než `end_expression`, jinak se bude negovat návratovou hodnotu.  
  
 `end_expression`  
 Libovolný platný výraz. `end_expression` musí být stejného typu jako `expression` a `begin_expression`.  
  
 NOT  
 Určuje, že bude výsledek BETWEEN negovat.  
  
 AND  
 Slouží jako zástupný symbol, který označuje `expression` by měla spadat do rozsahu indikován `begin_expression` a `end_expression`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `expression` mezi rozsah indikovaný `begin_expression` a `end_expression`; v opačném případě `false`. `null` bude vrácen v případě `expression` je `null` nebo, pokud `begin_expression` nebo `end_expression` je `null`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete nastavit jako výhradní rozsah adres, použijte místo BETWEEN větší než (>) a menší než (<) operátory.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá mezi operátor k určení, zda výraz výsledkem je hodnota v zadaném rozsahu. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
