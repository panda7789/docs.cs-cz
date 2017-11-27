---
title: "Známé problémy a aspekty v technologii LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 85fea34f6044c99a58fd27dbf5a03198741294ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="c9748-102">Známé problémy a aspekty v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c9748-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="c9748-103">Tato část obsahuje informace o známých problémech s [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="c9748-103">This section provides information about known issues with [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
-   [<span data-ttu-id="c9748-104">LINQ dotazů, nelze uložit do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="c9748-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
-   [<span data-ttu-id="c9748-105">Ke ztrátě informace o objednávce</span><span class="sxs-lookup"><span data-stu-id="c9748-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
-   [<span data-ttu-id="c9748-106">Znaménka není podporován</span><span class="sxs-lookup"><span data-stu-id="c9748-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
-   [<span data-ttu-id="c9748-107">Chyby při převodu typu</span><span class="sxs-lookup"><span data-stu-id="c9748-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
-   [<span data-ttu-id="c9748-108">Odkazování na Neskalární proměnné není podporován</span><span class="sxs-lookup"><span data-stu-id="c9748-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
-   [<span data-ttu-id="c9748-109">Vnořené dotazy pravděpodobně dojde k chybě systému SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="c9748-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
-   [<span data-ttu-id="c9748-110">Anonymní typ projekce</span><span class="sxs-lookup"><span data-stu-id="c9748-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="c9748-111">LINQ dotazů, nelze uložit do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="c9748-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="c9748-112">Od verze rozhraní .NET Framework 4.5, technologie LINQ to Entities dotazy jsou automaticky uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c9748-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="c9748-113">Však technologie LINQ to Entities dotazy které se týkají `Enumerable.Contains` operátor do kolekcí v paměti neukládají do mezipaměti automaticky.</span><span class="sxs-lookup"><span data-stu-id="c9748-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="c9748-114">Také Parametrizace kolekce v paměti v kompilovaném dotazů LINQ není povoleno.</span><span class="sxs-lookup"><span data-stu-id="c9748-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="c9748-115">Ke ztrátě informace o objednávce</span><span class="sxs-lookup"><span data-stu-id="c9748-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="c9748-116">Projekce sloupce do anonymní typ způsobí, že řazení informace ztraceny v některé dotazy, které jsou spouštěny proti [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] databázi nastavit úroveň kompatibility "80".</span><span class="sxs-lookup"><span data-stu-id="c9748-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] database set to a compatibility level of "80".</span></span>  <span data-ttu-id="c9748-117">Tato situace nastane při název sloupce v seznamu order by odpovídá název sloupce v modulu pro výběr, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c9748-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="c9748-118">Znaménka není podporován</span><span class="sxs-lookup"><span data-stu-id="c9748-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="c9748-119">Určení typ celé číslo bez znaménka v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotaz není podporována, protože [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nepodporuje celých čísel bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="c9748-119">Specifying an unsigned integer type in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="c9748-120">Pokud zadáte celé číslo bez znaménka <xref:System.ArgumentException> dojde k výjimce během překlad výrazu dotazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c9748-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="c9748-121">Tento příklad dotazy pro pořadí s ID 48000.</span><span class="sxs-lookup"><span data-stu-id="c9748-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="c9748-122">Chyby při převodu typu</span><span class="sxs-lookup"><span data-stu-id="c9748-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="c9748-123">V jazyce Visual Basic vlastnost je namapována na sloupec typu verze systému SQL Server s hodnotou 1 pomocí `CByte` funkce, <xref:System.Data.SqlClient.SqlException> je vyvolána se zpráva "Chyba aritmetického přetečení".</span><span class="sxs-lookup"><span data-stu-id="c9748-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="c9748-124">Následující příklad dotazy `Product.MakeFlag` sloupec v ukázkové databázi AdventureWorks a výjimku se vyvolá, když výsledky dotazu jsou vstupní přes.</span><span class="sxs-lookup"><span data-stu-id="c9748-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="c9748-125">Odkazování na Neskalární proměnné není podporován</span><span class="sxs-lookup"><span data-stu-id="c9748-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="c9748-126">Odkazování na neskalární proměnné, jako například entitu v dotazu není podporována.</span><span class="sxs-lookup"><span data-stu-id="c9748-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="c9748-127">Když je takový dotaz spuštěn, <xref:System.NotSupportedException> se zpráva, že je vyvolána výjimka "nejde vytvořit konstantní hodnotu typu `EntityType`.</span><span class="sxs-lookup"><span data-stu-id="c9748-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="c9748-128">Jenom primitivní typy ('například Int32, String a identifikátor Guid') jsou podporovány v tomto kontextu."</span><span class="sxs-lookup"><span data-stu-id="c9748-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9748-129">Odkazování na kolekci skalární proměnné je podporována.</span><span class="sxs-lookup"><span data-stu-id="c9748-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="c9748-130">Vnořené dotazy pravděpodobně dojde k chybě systému SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="c9748-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="c9748-131">Se serverem SQL Server 2000 technologie LINQ to Entities dotazy může selhat, pokud vytvářejí vnořené dotazy jazyka Transact-SQL, které jsou tři nebo více úrovněmi.</span><span class="sxs-lookup"><span data-stu-id="c9748-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="c9748-132">Anonymní typ projekce</span><span class="sxs-lookup"><span data-stu-id="c9748-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="c9748-133">Pokud definujete počátečního dotazu cestu ke zahrnout související objekty pomocí <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metodu <xref:System.Data.Objects.ObjectQuery%601> a pak pomocí LINQ vrácených objektů anonymní typ projektu, objekty uvedené v metodě zahrnout nejsou zahrnuty v dotazu výsledky.</span><span class="sxs-lookup"><span data-stu-id="c9748-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="c9748-134">Chcete-li získat související objekty, není vrácená typy projektů anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="c9748-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="c9748-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9748-135">See Also</span></span>  
 [<span data-ttu-id="c9748-136">Technologie LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c9748-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
