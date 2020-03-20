---
title: Přehled Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 880b81f2b6d4c4b893d28c919490f88dfb2a42e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150373"
---
# <a name="entity-sql-overview"></a>Přehled Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]je jazyk podobný SQL, který umožňuje dotazovat konceptuální modely v rámci entity. Koncepční modely představují data jako entity [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a vztahy a umožňuje dotaz na tyto entity a vztahy ve formátu, který je známý těm, kteří používají SQL.  

 Entity Framework spolupracuje s poskytovateli dat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] specifických pro úložiště převést obecné do dotazů specifických pro úložiště. Zprostředkovatel EntityClient poskytuje způsob, jak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provést příkaz proti modelu entity a vrátit bohaté typy dat, včetně skalární výsledky, sady výsledků a grafy objektů. Při vytváření <xref:System.Data.EntityClient.EntityCommand> objektů můžete zadat název uložené procedury nebo text dotazu přiřazením řetězce dotazu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> vlastnosti. Zveřejňuje <xref:System.Data.EntityClient.EntityDataReader> výsledky provádění proti <xref:System.Data.EntityClient.EntityCommand> EDM. Chcete-li provést příkaz, který vrací <xref:System.Data.EntityClient.EntityDataReader>, volání <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 Kromě zprostředkovatele EntityClient umožňuje entity Framework použít [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k provádění dotazů proti konceptuálnímu modelu a vracet data jako objekty CLR silného typu, které jsou instancemi typů entit. Další informace naleznete v [tématu Práce s objekty](../working-with-objects.md).  
  
 Tato část obsahuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)]rámcové informace o .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Jak se Entity SQL liší od Transact-SQL](how-entity-sql-differs-from-transact-sql.md)  
  
 [Stručné reference k Entity SQL](entity-sql-quick-reference.md)  
  
 [Systém typů](type-system-entity-sql.md)  
  
 [Definice typů](type-definitions-entity-sql.md)  
  
 [Vytváření typů](constructing-types-entity-sql.md)  
  
 [Ukládání do mezipaměti plánu dotazu](query-plan-caching-entity-sql.md)  
  
 [Obory názvů](namespaces-entity-sql.md)  
  
 [Identifikátory](identifiers-entity-sql.md)  
  
 [Parametry](parameters-entity-sql.md)  
  
 [Proměnné](variables-entity-sql.md)  
  
 [Nepodporované výrazy](unsupported-expressions-entity-sql.md)  
  
 [Literály](literals-entity-sql.md)  
  
 [Literály s hodnotou null a odvození typu proměnné](null-literals-and-type-inference-entity-sql.md)  
  
 [Vstupní znaková sada](input-character-set-entity-sql.md)  
  
 [Výrazy dotazu](query-expressions-entity-sql.md)  
  
 [Functions](functions-entity-sql.md)  
  
 [Priorita operátorů](operator-precedence-entity-sql.md)  
  
 [Stránkování](paging-entity-sql.md)  
  
 [Sémantika porovnání](comparison-semantics-entity-sql.md)  
  
 [Sestavování dotazů s vnořeným jazykem Entity SQL](composing-nested-entity-sql-queries.md)  
  
 [Strukturované typy s možnou hodnotou Null](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
- [Jazyk Entity SQL](entity-sql-language.md)
- [Specifikace CSDL, SSDL a MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
