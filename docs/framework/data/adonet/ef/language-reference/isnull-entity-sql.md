---
title: ISNULL (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31e0b77e397bd4f190119a01719da185211f7715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isnull-entity-sql"></a>ISNULL (entita SQL)
Určuje, pokud má hodnotu null výrazu dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný dotaz výraz. Nemůže být kolekce, mít členy kolekce, nebo typ záznamu s kolekcí vlastnosti typu.  
  
 NENÍ  
 Neguje EDM. Logická hodnota výsledek je NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud `expression` vrátí hodnotu null; jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Použití `IS NULL` k určení, pokud element vnějšího spojení je null:  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Použití `IS NULL` k určení, zda člen má skutečnou hodnotu:  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Následující tabulka uvádí chování `IS NULL` přes některé vzory. Všechny výjimky jsou vyvolány ze strany klienta předtím, než získá volá zprostředkovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|NULL je NULL.|Vrátí `true`.|  
|ZPRACOVÁVAT (null AS EntityType) je NULL|Vrátí `true`.|  
|ZPRACOVÁVAT (null AS ComplexType) je NULL|Vrátí chybu.|  
|ZPRACOVÁVAT (null AS RowType) je NULL|Vrátí chybu.|  
|Typ EntityType má hodnotu NULL.|Vrátí `true` nebo `false`.|  
|Typ ComplexType má hodnotu NULL.|Vrátí chybu.|  
|RowType má hodnotu NULL.|Vrátí chybu.|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu pomocí operátoru IS NOT NULL k určení, pokud výraz dotazu není null. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
