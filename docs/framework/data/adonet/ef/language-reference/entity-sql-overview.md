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
# <a name="entity-sql-overview"></a><span data-ttu-id="98e1b-102">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="98e1b-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="98e1b-103">je jazyk podobný SQL, který umožňuje dotazovat konceptuální modely v rámci entity.</span><span class="sxs-lookup"><span data-stu-id="98e1b-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="98e1b-104">Koncepční modely představují data jako entity [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a vztahy a umožňuje dotaz na tyto entity a vztahy ve formátu, který je známý těm, kteří používají SQL.</span><span class="sxs-lookup"><span data-stu-id="98e1b-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  

 <span data-ttu-id="98e1b-105">Entity Framework spolupracuje s poskytovateli dat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] specifických pro úložiště převést obecné do dotazů specifických pro úložiště.</span><span class="sxs-lookup"><span data-stu-id="98e1b-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="98e1b-106">Zprostředkovatel EntityClient poskytuje způsob, jak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provést příkaz proti modelu entity a vrátit bohaté typy dat, včetně skalární výsledky, sady výsledků a grafy objektů.</span><span class="sxs-lookup"><span data-stu-id="98e1b-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="98e1b-107">Při vytváření <xref:System.Data.EntityClient.EntityCommand> objektů můžete zadat název uložené procedury nebo text dotazu přiřazením řetězce dotazu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98e1b-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="98e1b-108">Zveřejňuje <xref:System.Data.EntityClient.EntityDataReader> výsledky provádění proti <xref:System.Data.EntityClient.EntityCommand> EDM.</span><span class="sxs-lookup"><span data-stu-id="98e1b-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="98e1b-109">Chcete-li provést příkaz, který vrací <xref:System.Data.EntityClient.EntityDataReader>, volání <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="98e1b-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="98e1b-110">Kromě zprostředkovatele EntityClient umožňuje entity Framework použít [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k provádění dotazů proti konceptuálnímu modelu a vracet data jako objekty CLR silného typu, které jsou instancemi typů entit.</span><span class="sxs-lookup"><span data-stu-id="98e1b-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="98e1b-111">Další informace naleznete v [tématu Práce s objekty](../working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="98e1b-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="98e1b-112">Tato část obsahuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)]rámcové informace o .</span><span class="sxs-lookup"><span data-stu-id="98e1b-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98e1b-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="98e1b-113">In This Section</span></span>  
 [<span data-ttu-id="98e1b-114">Jak se Entity SQL liší od Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="98e1b-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="98e1b-115">Stručné reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="98e1b-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="98e1b-116">Systém typů</span><span class="sxs-lookup"><span data-stu-id="98e1b-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-117">Definice typů</span><span class="sxs-lookup"><span data-stu-id="98e1b-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-118">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="98e1b-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-119">Ukládání do mezipaměti plánu dotazu</span><span class="sxs-lookup"><span data-stu-id="98e1b-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-120">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="98e1b-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-121">Identifikátory</span><span class="sxs-lookup"><span data-stu-id="98e1b-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-122">Parametry</span><span class="sxs-lookup"><span data-stu-id="98e1b-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-123">Proměnné</span><span class="sxs-lookup"><span data-stu-id="98e1b-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-124">Nepodporované výrazy</span><span class="sxs-lookup"><span data-stu-id="98e1b-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-125">Literály</span><span class="sxs-lookup"><span data-stu-id="98e1b-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-126">Literály s hodnotou null a odvození typu proměnné</span><span class="sxs-lookup"><span data-stu-id="98e1b-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-127">Vstupní znaková sada</span><span class="sxs-lookup"><span data-stu-id="98e1b-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-128">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="98e1b-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-129">Functions</span><span class="sxs-lookup"><span data-stu-id="98e1b-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-130">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="98e1b-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-131">Stránkování</span><span class="sxs-lookup"><span data-stu-id="98e1b-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-132">Sémantika porovnání</span><span class="sxs-lookup"><span data-stu-id="98e1b-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="98e1b-133">Sestavování dotazů s vnořeným jazykem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="98e1b-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="98e1b-134">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="98e1b-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="98e1b-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="98e1b-135">See also</span></span>

- [<span data-ttu-id="98e1b-136">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="98e1b-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="98e1b-137">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="98e1b-137">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="98e1b-138">Specifikace CSDL, SSDL a MSL</span><span class="sxs-lookup"><span data-stu-id="98e1b-138">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
