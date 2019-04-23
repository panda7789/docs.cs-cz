---
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 51de041a4b06d5da31071ea2b3cb31c86feff137
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294442"
---
# <a name="cast-entity-sql"></a>CAST (Entity SQL)
Převede výraz jednoho datového typu na jiný.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz, který lze převést na `data_type`.  
  
 `data_type`  
 Cíl poskytnuté systémem datového typu. Musí být primitivního typu (skalární). `data_type` Používá závisí na dotaz místa. Pokud je dotaz proveden s <xref:System.Data.EntityClient.EntityCommand>, datový typ je typ definovaný v konceptuálním modelu. Další informace najdete v tématu [specifikace CSDL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Pokud je dotaz proveden s <xref:System.Data.Objects.ObjectQuery%601>, datový typ je společný typ language runtime (CLR).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí stejnou hodnotu jako `data_type`.  
  
## <a name="remarks"></a>Poznámky  
 Výraz cast má podobnou sémantiku [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] převést výraz. Výraz cast se používá k převodu hodnoty jednoho typu na hodnotu jiného typu.  
  
```  
CAST( e as T )  
```  
  
 Pokud je e nějakého typu je lze převést na T elementům a potom výše uvedeném výrazu je výraz přetypování platný. T musí být primitivního typu (skalární).  
  
 Hodnoty pro omezující vlastnosti hodnot precision a scale může volitelně zadat při přetypování na `Edm.Decimal`. Pokud není explicitně zadán, výchozí hodnoty pro hodnot precision a scale jsou 18 a 0. Konkrétně se podporují následující přetížení pro `Decimal`:  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Použití výrazu přetypování se považuje za explicitní převod. Explicitní převody mohou zkrátit data nebo ztratit přesnost.  
  
> [!NOTE]
>  PŘETYPOVÁNÍ je podporována pouze primitivní typy a typy členů výčtu.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor PŘETYPOVÁNÍ k přetypování výrazu jednoho datového typu na jiný. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
