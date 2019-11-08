---
title: Přetypování (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: b7778d6a2e0b0dd15b2911f2d1cee36208e13328
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738513"
---
# <a name="cast-entity-sql"></a>Přetypování (Entity SQL)
Převede výraz jednoho datového typu na jiný.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz, který lze převést na `data_type`.  
  
 `data_type`  
 Cílový datový typ zadaný systémem. Musí se jednat o primitivní (skalární) typ. Použitá `data_type` závisí na prostoru dotazu. Pokud je dotaz spuštěn s <xref:System.Data.EntityClient.EntityCommand>, datový typ je typ definovaný v koncepčním modelu. Další informace najdete v tématu [specifikace CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec). Pokud je dotaz spuštěn s <xref:System.Data.Objects.ObjectQuery%601>, datový typ je typ modulu CLR (Common Language Runtime).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací stejnou hodnotu jako `data_type`.  
  
## <a name="remarks"></a>Poznámky  
 Výraz přetypování má podobnou sémantiku jako výraz převodu Transact-SQL. Výraz přetypování se používá k převodu hodnoty jednoho typu na hodnotu jiného typu.  
  
```csharp
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
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
