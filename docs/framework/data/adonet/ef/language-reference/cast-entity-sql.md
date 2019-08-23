---
title: Přetypování (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 253dcf092deadd1049d0556af4ea0630602110d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935813"
---
# <a name="cast-entity-sql"></a>Přetypování (Entity SQL)
Převede výraz jednoho datového typu na jiný.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz, který lze převést `data_type`na.  
  
 `data_type`  
 Cílový datový typ zadaný systémem. Musí se jednat o primitivní (skalární) typ. `data_type` Použitá velikost závisí na prostoru dotazu. Pokud je dotaz spuštěn s <xref:System.Data.EntityClient.EntityCommand>, datový typ je typ definovaný v koncepčním modelu. Další informace najdete v tématu [specifikace CSDL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Pokud je spuštěn dotaz s <xref:System.Data.Objects.ObjectQuery%601>, datový typ je typ modulu CLR (Common Language Runtime).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací stejnou hodnotu jako `data_type`.  
  
## <a name="remarks"></a>Poznámky  
 Výraz přetypování má podobnou sémantiku jako výraz převodu Transact-SQL. Výraz přetypování se používá k převodu hodnoty jednoho typu na hodnotu jiného typu.  
  
```  
CAST( e as T )  
```  
  
 Pokud je e v některém typu, a je převoditelné na T, pak je výše uvedený výraz platným výrazem přetypování. T musí být primitivní (skalární) typ.  
  
 Hodnoty omezujících vlastností Precision a Scale mohou být volitelně poskytnuty při přetypování do `Edm.Decimal`. Pokud explicitně neposkytnete, výchozí hodnoty pro přesnost a měřítko jsou 18 a 0 v uvedeném pořadí. Konkrétně jsou podporována následující přetížení pro `Decimal`:  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Použití výrazu přetypování je považováno za explicitní převod. Explicitní převody mohou zkrátit data nebo ztratit přesnost.  
  
> [!NOTE]
> Funkce CAST je podporována pouze u primitivních typů a typů členů výčtu.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor přetypování k přetypování výrazu jednoho datového typu na jiný. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
