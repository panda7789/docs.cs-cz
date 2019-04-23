---
title: Přehled Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 100d616462cd76e1dde8fc855787ec3118842fc8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073467"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="f8aeb-102">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f8aeb-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f8aeb-103">je, která umožňuje dotazování konceptuálních modelů v jazyce podobném SQL [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8aeb-103">is a SQL-like language that enables you to query conceptual models in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="f8aeb-104">Konceptuální modely představují data jako entit a vztahů, a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňuje dotazování těchto entit a relací ve formátu, který je obeznámen všem uživatelům, kteří používají SQL.</span><span class="sxs-lookup"><span data-stu-id="f8aeb-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
  
 <span data-ttu-id="f8aeb-105">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Spolupracuje s poskytovateli data specifická pro úložiště pro převod obecný [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do konkrétní úložiště dotazů.</span><span class="sxs-lookup"><span data-stu-id="f8aeb-105">The [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="f8aeb-106">Zprostředkovatel EntityClient poskytuje způsob, jak spustit [!INCLUDE[esql](../../../../../../includes/esql-md.md)] příkaz proti modelu entity a návratové typy bohatých dat včetně grafů objektů, skalární výsledky a sad výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="f8aeb-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="f8aeb-107">Při sestavování <xref:System.Data.EntityClient.EntityCommand> objekty, můžete zadat název uložené procedury nebo text dotazu přiřazením [!INCLUDE[esql](../../../../../../includes/esql-md.md)] řetězec do dotazu jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f8aeb-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f8aeb-108"><xref:System.Data.EntityClient.EntityDataReader> Zpřístupňuje výsledky spuštění <xref:System.Data.EntityClient.EntityCommand> proti modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="f8aeb-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="f8aeb-109">K provedení příkazu, který vrací <xref:System.Data.EntityClient.EntityDataReader>, volání <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8aeb-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="f8aeb-110">Kromě zprostředkovatel EntityClient [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] vám umožní použít [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k provádění dotazů na koncepční model a vrátí data jako silného typu CLR objekty, které jsou instancemi typů entit.</span><span class="sxs-lookup"><span data-stu-id="f8aeb-110">In addition to the EntityClient provider, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="f8aeb-111">Další informace najdete v tématu [práce s objekty](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f8aeb-111">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="f8aeb-112">Tato část obsahuje rámcové informace o [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8aeb-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8aeb-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f8aeb-113">In This Section</span></span>  
 [<span data-ttu-id="f8aeb-114">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f8aeb-114">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="f8aeb-115">Stručné reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f8aeb-115">Entity SQL Quick Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="f8aeb-116">Systém typů</span><span class="sxs-lookup"><span data-stu-id="f8aeb-116">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-117">Definice typů</span><span class="sxs-lookup"><span data-stu-id="f8aeb-117">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-118">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="f8aeb-118">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-119">Ukládání do mezipaměti plánu dotazu</span><span class="sxs-lookup"><span data-stu-id="f8aeb-119">Query Plan Caching</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-120">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="f8aeb-120">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-121">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="f8aeb-121">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-122">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8aeb-122">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-123">Proměnné</span><span class="sxs-lookup"><span data-stu-id="f8aeb-123">Variables</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-124">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="f8aeb-124">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-125">Literály</span><span class="sxs-lookup"><span data-stu-id="f8aeb-125">Literals</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-126">Literály s hodnotou null a odvození typu proměnné</span><span class="sxs-lookup"><span data-stu-id="f8aeb-126">Null Literals and Type Inference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-127">Vstupní znaková sada</span><span class="sxs-lookup"><span data-stu-id="f8aeb-127">Input Character Set</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-128">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="f8aeb-128">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-129">Funkce</span><span class="sxs-lookup"><span data-stu-id="f8aeb-129">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-130">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="f8aeb-130">Operator Precedence</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-131">Stránkování</span><span class="sxs-lookup"><span data-stu-id="f8aeb-131">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-132">Sémantika porovnání</span><span class="sxs-lookup"><span data-stu-id="f8aeb-132">Comparison Semantics</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="f8aeb-133">Sestavování dotazů s vnořeným jazykem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f8aeb-133">Composing Nested Entity SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="f8aeb-134">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="f8aeb-134">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="f8aeb-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8aeb-135">See also</span></span>

- [<span data-ttu-id="f8aeb-136">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f8aeb-136">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="f8aeb-137">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f8aeb-137">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="f8aeb-138">Specifikace CSDL, SSDL a MSL</span><span class="sxs-lookup"><span data-stu-id="f8aeb-138">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
