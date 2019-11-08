---
title: Přehled Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: e0f154ab2d9db1a1fdbaba8c72bc7e43ad71ee0b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738485"
---
# <a name="entity-sql-overview"></a>Přehled Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] je jazyk podobný SQL, který umožňuje dotazování konceptuálních modelů v Entity Framework. Koncepční modely reprezentují data jako entity a vztahy a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňují dotazovat se na tyto entity a vztahy ve formátu, který je známý pro uživatele, kteří použili SQL.  
      
 Entity Framework spolupracuje s poskytovateli dat specifických pro úložiště k překladu obecných [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do dotazů specifických pro úložiště. Zprostředkovatel EntityClient poskytuje způsob, jak spustit příkaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pro model entity a vracet bohatě formátované typy dat, včetně skalárních výsledků, sad výsledků a grafů objektů. Při vytváření objektů <xref:System.Data.EntityClient.EntityCommand> můžete zadat název uložené procedury nebo text dotazu přiřazením [!INCLUDE[esql](../../../../../../includes/esql-md.md)] řetězce dotazu k vlastnosti <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>. <xref:System.Data.EntityClient.EntityDataReader> zpřístupňuje výsledky spuštění <xref:System.Data.EntityClient.EntityCommand> s modelem EDM. Chcete-li spustit příkaz, který vrací <xref:System.Data.EntityClient.EntityDataReader>, zavolejte <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 Kromě poskytovatele EntityClient vám Entity Framework umožňuje používat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k provádění dotazů na koncepčním modelu a vracet data jako objekty CLR se silným typem, které jsou instancemi typů entit. Další informace naleznete v tématu [práce s objekty](../working-with-objects.md).  
  
 Tato část obsahuje koncepční informace o [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
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
  
 [Funkce](functions-entity-sql.md)  
  
 [Priorita operátorů](operator-precedence-entity-sql.md)  
  
 [Stránkování](paging-entity-sql.md)  
  
 [Sémantika porovnání](comparison-semantics-entity-sql.md)  
  
 [Sestavování dotazů s vnořeným jazykem Entity SQL](composing-nested-entity-sql-queries.md)  
  
 [Strukturované typy s možnou hodnotou Null](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Jazyk Entity SQL](entity-sql-language.md)
- [Specifikace CSDL, SSDL a MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
