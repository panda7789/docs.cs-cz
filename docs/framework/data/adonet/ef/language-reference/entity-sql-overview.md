---
title: Přehled Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 54a3832cffbf3376e6b3ab0826b280b676ccc1a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534641"
---
# <a name="entity-sql-overview"></a>Přehled Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] je, která umožňuje dotazování konceptuálních modelů v jazyce podobném SQL [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Konceptuální modely představují data jako entit a vztahů, a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje dotazování těchto entit a relací ve formátu, který je obeznámen všem uživatelům, kteří používají SQL.  
  
 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Spolupracuje s poskytovateli data specifická pro úložiště pro převod obecný [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do konkrétní úložiště dotazů. Zprostředkovatel EntityClient poskytuje způsob, jak spustit [!INCLUDE[esql](../../../../../../includes/esql-md.md)] příkaz proti modelu entity a návratové typy bohatých dat včetně grafů objektů, skalární výsledky a sad výsledků dotazu. Při sestavování <xref:System.Data.EntityClient.EntityCommand> objekty, můžete zadat název uložené procedury nebo text dotazu přiřazením [!INCLUDE[esql](../../../../../../includes/esql-md.md)] řetězec do dotazu jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> vlastnost. <xref:System.Data.EntityClient.EntityDataReader> Zpřístupňuje výsledky spuštění <xref:System.Data.EntityClient.EntityCommand> proti modelu EDM. K provedení příkazu, který vrací <xref:System.Data.EntityClient.EntityDataReader>, volání <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 Kromě zprostředkovatel EntityClient [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] vám umožní použít [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k provádění dotazů na koncepční model a vrátí data jako silného typu CLR objekty, které jsou instancemi typů entit. Další informace najdete v tématu [práce s objekty](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Tato část obsahuje rámcové informace o [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Jak se Entity SQL liší od Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [Stručné reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [Systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [Definice typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [Vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [Ukládání do mezipaměti plánu dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [Obory názvů](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [Identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [Parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [Proměnné](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [Nepodporované výrazy](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [Literály](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [Literály s hodnotou null a odvození typu proměnné](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [Vstupní znaková sada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [Priorita operátorů](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [Stránkování](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [Sémantika porovnání](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [Sestavování dotazů s vnořeným jazykem Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [Strukturované typy s možnou hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Jazyk Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Specifikace CSDL, SSDL a MSL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
