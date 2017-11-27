---
title: '|| (NEBO) (Entita SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba0c376bc0b57013fe4701a1f9e84fdd9a5ed62a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="-or-entity-sql"></a>|| (NEBO) (Entita SQL)
Kombinuje dva `Boolean` výrazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Jakýkoli platný výraz, který vrací `Boolean`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud některá z podmínek je `true`, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 NEBO se [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logický operátor. Umožňuje zkombinovat dvě podmínky. Při více než jeden logický operátor je použít v příkazu, jsou vyhodnoceny nebo operátory a operátory. Můžete však změnit pořadí vyhodnocování pomocí závorek.  
  
 Dvojité svislých pruhů (&#124; &#124;) mají stejnou funkci jako operátor OR.  
  
 Následující tabulka uvádí možné vstupní hodnoty a návratové typy.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|HODNOTA TRUE|HODNOTA TRUE|HODNOTA TRUE|  
|`FALSE`|HODNOTA TRUE|FALSE|NULL|  
|`NULL`|HODNOTA TRUE|NULL|NULL|  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor OR kombinace obou `Boolean` výrazy. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
