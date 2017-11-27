---
title: "PŘETYPOVÁNÍ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 353398f834aff5cefb3aed91899ce042df9df60a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cast-entity-sql"></a>PŘETYPOVÁNÍ (entita SQL)
Převod výrazu jednoho datového typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz, který je převést na `data_type`.  
  
 `data_type`  
 Cíl poskytnuté systémem datového typu. Musí být primitivního typu (skalární). `data_type` Používá závisí na obor dotazu. Pokud je dotaz proveden s <xref:System.Data.EntityClient.EntityCommand>, datový typ je typ definovanou v konceptuálním modelu. Další informace najdete v tématu [CSDL specifikace](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Pokud je dotaz proveden s <xref:System.Data.Objects.ObjectQuery%601>, datový typ je stejného typu language runtime (CLR).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací stejnou hodnotu jako `data_type`.  
  
## <a name="remarks"></a>Poznámky  
 Výraz cast má podobnou sémantiku [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] převést výraz. Výraz cast je použít k převodu hodnoty jednoho typu do hodnoty jiného typu.  
  
```  
CAST( e as T )  
```  
  
 Pokud e je typu je převést na T S a S a potom ve výše uvedené výrazu je výrazem platnou přetypování. T musí být typu primitivní (skalární).  
  
 Hodnoty pro omezující vlastnosti přesnost a měřítko může volitelně zadaný při přetypování na `Edm.Decimal`. Pokud není explicitně k dispozici, výchozí hodnoty pro přesnost a měřítko jsou 18 a 0. Konkrétně, jsou podporovány následující přetížení pro `Decimal`:  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Použití výraz cast je považován za explicitní převod. Explicitní převody může zkrátit dat nebo ztratit přesnost.  
  
> [!NOTE]
>  PŘETYPOVÁNÍ je podporována pouze přes primitivní typy a typy členů výčtu.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor PŘETYPOVÁNÍ k přetypování výrazu jednoho datového typu na jiný. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
