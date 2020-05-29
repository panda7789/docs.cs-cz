---
title: Přehled Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: b4fe852847d8b1b4bc0b80e3ba8e1f5b4aae9ff7
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202252"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="1ee15-102">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1ee15-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1ee15-103">je jazyk podobný SQL, který umožňuje dotazování konceptuálních modelů v Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1ee15-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="1ee15-104">Koncepční modely reprezentují data jako entity a vztahy a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umožňují dotazování těchto entit a vztahů ve formátu, který je známý pro uživatele, kteří použili SQL.</span><span class="sxs-lookup"><span data-stu-id="1ee15-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  

 <span data-ttu-id="1ee15-105">Entity Framework spolupracuje s poskytovateli dat specifických pro úložiště k překladu obecných [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do dotazů specifických pro úložiště.</span><span class="sxs-lookup"><span data-stu-id="1ee15-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="1ee15-106">Zprostředkovatel EntityClient poskytuje způsob, jak spustit příkaz pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] model entity a vracet bohatě formátované typy dat, včetně skalárních výsledků, sad výsledků a grafů objektů.</span><span class="sxs-lookup"><span data-stu-id="1ee15-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="1ee15-107">Při vytváření <xref:System.Data.EntityClient.EntityCommand> objektů můžete zadat název uložené procedury nebo text dotazu přiřazením [!INCLUDE[esql](../../../../../../includes/esql-md.md)] řetězce dotazu k jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1ee15-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1ee15-108"><xref:System.Data.EntityClient.EntityDataReader>Zpřístupňuje výsledky provádění s modelem <xref:System.Data.EntityClient.EntityCommand> EDM.</span><span class="sxs-lookup"><span data-stu-id="1ee15-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="1ee15-109">Chcete-li spustit příkaz, který vrátí <xref:System.Data.EntityClient.EntityDataReader> , zavolejte <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> .</span><span class="sxs-lookup"><span data-stu-id="1ee15-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="1ee15-110">Kromě poskytovatele EntityClient vám Entity Framework umožňuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] spouštět dotazy na koncepčním modelu a vracet data jako objekty CLR se silným typem, které jsou instancemi typů entit.</span><span class="sxs-lookup"><span data-stu-id="1ee15-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="1ee15-111">Další informace naleznete v tématu [práce s objekty](../working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="1ee15-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="1ee15-112">Tato část obsahuje koncepční informace o nástroji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1ee15-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ee15-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1ee15-113">In This Section</span></span>  
 [<span data-ttu-id="1ee15-114">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1ee15-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="1ee15-115">Stručné reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1ee15-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="1ee15-116">Systém typů</span><span class="sxs-lookup"><span data-stu-id="1ee15-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-117">Definice typů</span><span class="sxs-lookup"><span data-stu-id="1ee15-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-118">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="1ee15-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-119">Ukládání do mezipaměti plánu dotazu</span><span class="sxs-lookup"><span data-stu-id="1ee15-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-120">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="1ee15-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-121">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="1ee15-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-122">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ee15-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-123">Proměnné</span><span class="sxs-lookup"><span data-stu-id="1ee15-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-124">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="1ee15-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-125">Literály</span><span class="sxs-lookup"><span data-stu-id="1ee15-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-126">Literály s hodnotou null a odvození typu proměnné</span><span class="sxs-lookup"><span data-stu-id="1ee15-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-127">Vstupní znaková sada</span><span class="sxs-lookup"><span data-stu-id="1ee15-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-128">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="1ee15-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-129">Functions</span><span class="sxs-lookup"><span data-stu-id="1ee15-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-130">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="1ee15-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-131">Stránkování</span><span class="sxs-lookup"><span data-stu-id="1ee15-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-132">Sémantika porovnání</span><span class="sxs-lookup"><span data-stu-id="1ee15-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="1ee15-133">Sestavování dotazů s vnořeným jazykem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1ee15-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="1ee15-134">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="1ee15-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ee15-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ee15-135">See also</span></span>

- [<span data-ttu-id="1ee15-136">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1ee15-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="1ee15-137">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1ee15-137">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="1ee15-138">Specifikace CSDL, SSDL a MSL</span><span class="sxs-lookup"><span data-stu-id="1ee15-138">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
