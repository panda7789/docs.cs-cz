---
title: Přehled Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 4d7db9c6a7aaeef900132663a5b0aa7420afe668
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251061"
---
# <a name="entity-sql-overview"></a>Přehled Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]je jazyk podobný SQL, který umožňuje dotazování konceptuálních modelů v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Koncepční modely reprezentují data jako entity a vztahy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a umožňují dotazování těchto entit a vztahů ve formátu, který je známý pro uživatele, kteří použili SQL.  
  
 Spolupracuje s poskytovateli dat specifických pro úložiště k překladu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obecných na dotazy specifických pro úložiště. [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Zprostředkovatel EntityClient poskytuje způsob, jak spustit [!INCLUDE[esql](../../../../../../includes/esql-md.md)] příkaz pro model entity a vracet bohatě formátované typy dat, včetně skalárních výsledků, sad výsledků a grafů objektů. Při vytváření <xref:System.Data.EntityClient.EntityCommand> objektů můžete zadat název uložené procedury nebo text dotazu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] přiřazením řetězce dotazu k jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> vlastnosti. Zpřístupňuje výsledky provádění s <xref:System.Data.EntityClient.EntityCommand> modelem EDM. <xref:System.Data.EntityClient.EntityDataReader> Chcete-li spustit příkaz, který <xref:System.Data.EntityClient.EntityDataReader>vrátí, <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>zavolejte.  
  
 Kromě poskytovatele [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] EntityClient vám umožňuje používat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k provádění dotazů na koncepční model a vracet data jako objekty CLR se silným typem, které jsou instancemi typů entit. Další informace naleznete v tématu [práce s objekty](../working-with-objects.md).  
  
 Tato část obsahuje koncepční informace o [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nástroji.  
  
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
- [Specifikace CSDL, SSDL a MSL](csdl-ssdl-and-msl-specifications.md)
