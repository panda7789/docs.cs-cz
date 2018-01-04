---
title: "Přehled SQL entity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f77e3a5d0073cb13d1904f802c4d6760fc52caa9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="entity-sql-overview"></a>Přehled SQL entity
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]je podobné jazyku SQL jazyk, který umožňuje konceptuální modely v dotazu [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Konceptuální modely představují data jako entity a vztahy, a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje dotazování tyto entity a vztahy ve formátu, který je dobře známé pro ty, kteří použili SQL.  
  
 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Spolupracuje s poskytovateli úložiště specifických dat přeložit Obecné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do úložiště dotazů. Zprostředkovatel EntityClient poskytuje způsob, jak provést [!INCLUDE[esql](../../../../../../includes/esql-md.md)] příkaz proti entity model a vrátí bohaté typy dat, včetně skalární výsledky, sad výsledků dotazu a grafy objektu. Když vytvoříte <xref:System.Data.EntityClient.EntityCommand> objekty, můžete zadat název uložené procedury nebo text dotazu přiřazením [!INCLUDE[esql](../../../../../../includes/esql-md.md)] řetězec k dotazu jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> vlastnost. <xref:System.Data.EntityClient.EntityDataReader> Zpřístupní výsledky provádění <xref:System.Data.EntityClient.EntityCommand> proti modelu EDM. K provedení příkazu, který vrací <xref:System.Data.EntityClient.EntityDataReader>, volání <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 Kromě zprostředkovatel EntityClient [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] umožňuje používat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] spouštění dotazů na koncepční model a vrátí data jako silného typu CLR objekty, které jsou instancemi typy entit. Další informace najdete v tématu [práce s objekty](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Tato část obsahuje koncepční informace o [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
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
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Jazyk Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Specifikace CSDL, SSDL a MSL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
