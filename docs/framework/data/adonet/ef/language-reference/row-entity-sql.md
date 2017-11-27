---
title: "ŘÁDEK (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 396b81e01d057f1d5c357f18d833a973777c07ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="row-entity-sql"></a>ŘÁDEK (entita SQL)
Vytvoří anonymní, strukturálně typové záznamů z jednoho nebo více hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který vrátí hodnotu, můžete vytvořit v typ řádku.  
  
 `alias`  
 Určuje alias z hodnoty zadané v typ řádku. Pokud není k dispozici alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí generovat alias na základě [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pravidel pro vytvoření aliasu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Typ řádku.  
  
## <a name="remarks"></a>Poznámky  
 Použití konstruktorů řádek v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vytvořit anonymní, strukturálně typové záznamů z jednoho nebo více hodnot. Výsledný typ konstruktor row je typu řádek, jehož typy polí odpovídají typům hodnot, které jste použili k vytvoření řádek. Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Pokud nezadáte alias pro výraz v konstruktoru row, rozhraní Entity Framework se pokusí vygenerovat. Další informace najdete v části "Pravidla pro aliasy" [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) tématu.  
  
 Následující pravidla platí při aliasy výrazu v konstruktoru řádku:  
  
-   Výrazy v konstruktoru row nelze odkazovat na jiné aliasy v konstruktoru stejné.  
  
-   Dvou výrazů ve stejné konstruktor row nemůže mít stejný alias.  
  
 Další informace o dotazu konstruktory najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru řádek vytvořit anonymní, strukturálně typové záznamy. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>Viz také  
 [Vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Definice typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
