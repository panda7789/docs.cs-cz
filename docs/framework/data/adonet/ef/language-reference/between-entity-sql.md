---
title: MEZI (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 06008847a564d91d92a596978b90b040b6c508f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="between-entity-sql"></a>MEZI (entita SQL)
Určuje, zda výraz výsledkem hodnota v zadaném rozsahu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Mezi výraz má stejné funkce jako výraz jazyka Transact-SQL mezi.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný výraz pro testování v rozsahu definovaného `begin_expression` a `end_expression`. `expression`musí být stejného typu, jak `begin_expression` a `end_expression`.  
  
 `begin_expression`  
 Jakýkoli platný výraz. `begin_expression`musí být stejného typu, jak `expression` a `end_expression`. `begin_expression`musí být menší než `end_expression`, jinak bude Negované návratovou hodnotu.  
  
 `end_expression`  
 Jakýkoli platný výraz. `end_expression`musí být stejného typu, jak `expression` a `begin_expression`.  
  
 NENÍ  
 Určuje, že se Negované výsledek BETWEEN.  
  
 AND  
 Jako zástupný znak, který označuje `expression` by měla být v rozsahu indikován `begin_expression` a `end_expression`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud `expression` mezi rozsah indikovaný `begin_expression` a `end_expression`, jinak hodnota `false`. `null`bude vrácen v případě `expression` je `null` nebo, pokud `begin_expression` nebo `end_expression` je `null`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete zadat rozsah vylučují, použijte místo BETWEEN větší než (>) a menší než (<) operátory.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá mezi operátor k určení, zda výraz výsledkem hodnota v zadaném rozsahu. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
