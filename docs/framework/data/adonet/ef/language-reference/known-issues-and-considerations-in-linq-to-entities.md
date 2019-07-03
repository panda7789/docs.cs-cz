---
title: Známé problémy a aspekty u LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: e84319c60534c3ecf154c3f58973bcc429a73842
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539827"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="c13c5-102">Známé problémy a aspekty u LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c13c5-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="c13c5-103">Tato část obsahuje informace o známých problémech s dotazy LINQ na dotazy na entity.</span><span class="sxs-lookup"><span data-stu-id="c13c5-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="c13c5-104">Dotazy LINQ, nelze uložit do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="c13c5-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="c13c5-105">Informace o ztrátě objednávce</span><span class="sxs-lookup"><span data-stu-id="c13c5-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="c13c5-106">Celá čísla bez znaménka není podporován</span><span class="sxs-lookup"><span data-stu-id="c13c5-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="c13c5-107">Chyby převodu typů</span><span class="sxs-lookup"><span data-stu-id="c13c5-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="c13c5-108">Odkazuje na Neskalární proměnné není podporován</span><span class="sxs-lookup"><span data-stu-id="c13c5-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="c13c5-109">Vnořené dotazy může selhat s SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="c13c5-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="c13c5-110">Promítání na anonymního typu</span><span class="sxs-lookup"><span data-stu-id="c13c5-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="c13c5-111">Dotazy LINQ, nelze uložit do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="c13c5-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="c13c5-112">Od verze rozhraní .NET Framework 4.5, dotazech LINQ to Entities jsou automaticky uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c13c5-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="c13c5-113">Ale dotazech LINQ to Entities, které se týkají `Enumerable.Contains` nejsou v operátoru na kolekce v paměti automaticky uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c13c5-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="c13c5-114">Také Parametrizace kolekce v paměti v kompilované dotazy LINQ není povoleno.</span><span class="sxs-lookup"><span data-stu-id="c13c5-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="c13c5-115">Informace o ztrátě objednávce</span><span class="sxs-lookup"><span data-stu-id="c13c5-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="c13c5-116">Projekce sloupce do anonymního typu způsobí, že pořadí informace, které ztraceno v nějaké dotazy, které jsou spouštěny proti [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] databáze nastavená na úroveň kompatibility "80".</span><span class="sxs-lookup"><span data-stu-id="c13c5-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] database set to a compatibility level of "80".</span></span>  <span data-ttu-id="c13c5-117">Proběhne, když název sloupce v seznamu order by odpovídá názvu sloupce v modulu pro výběr, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c13c5-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="c13c5-118">Celá čísla bez znaménka není podporován</span><span class="sxs-lookup"><span data-stu-id="c13c5-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="c13c5-119">Určení typu celé číslo bez znaménka v technologii LINQ to Entities dotaz se nepodporuje, protože [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nepodporuje celých čísel bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="c13c5-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="c13c5-120">Pokud zadáte celé číslo bez znaménka, <xref:System.ArgumentException> bude vyvolána výjimka při překladu výrazu dotazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c13c5-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="c13c5-121">Tento příklad dotazy pro objednávky s ID 48000.</span><span class="sxs-lookup"><span data-stu-id="c13c5-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="c13c5-122">Chyby převodu typů</span><span class="sxs-lookup"><span data-stu-id="c13c5-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="c13c5-123">V jazyce Visual Basic, když vlastnost je mapováno na sloupec typu verze SQL serveru s hodnotou 1 pomocí `CByte` funkce, <xref:System.Data.SqlClient.SqlException> je vyvolána výjimka se zpráva "Chyba aritmetického přetečení".</span><span class="sxs-lookup"><span data-stu-id="c13c5-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="c13c5-124">Následující příklady dotazů `Product.MakeFlag` sloupec v ukázkové databázi AdventureWorks a výjimka je vyvolána, když jsou procházen výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="c13c5-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="c13c5-125">Odkazuje na Neskalární proměnné není podporován</span><span class="sxs-lookup"><span data-stu-id="c13c5-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="c13c5-126">Odkazování na neskalární proměnných, například entitu v dotazu se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c13c5-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="c13c5-127">Když takový dotaz spuštěn, <xref:System.NotSupportedException> je vyvolána výjimka a zobrazí se zpráva s oznámením "nelze vytvořit konstantní hodnotu typu `EntityType`.</span><span class="sxs-lookup"><span data-stu-id="c13c5-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="c13c5-128">Pouze primitivní typy ("například Int32, String a Guid") jsou v tomto kontextu podporován."</span><span class="sxs-lookup"><span data-stu-id="c13c5-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c13c5-129">Odkazování na sadu skalární proměnné je podporována.</span><span class="sxs-lookup"><span data-stu-id="c13c5-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="c13c5-130">Vnořené dotazy může selhat s SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="c13c5-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="c13c5-131">S SQL Server 2000 dotazech LINQ to Entities může selhat, pokud vytvářejí vnořené dotazy Transact-SQL, které jsou tři nebo více úrovní do hloubky.</span><span class="sxs-lookup"><span data-stu-id="c13c5-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="c13c5-132">Promítání na anonymního typu</span><span class="sxs-lookup"><span data-stu-id="c13c5-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="c13c5-133">Pokud definujete vaší cesty počátečního dotazu, aby zahrnovala související objekty pomocí <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metodu <xref:System.Data.Objects.ObjectQuery%601> a poté použít k projekci vrácených objektů na anonymní typ LINQ, objekty zadané v metodě zahrnout nejsou zahrnuty v dotazu výsledky.</span><span class="sxs-lookup"><span data-stu-id="c13c5-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="c13c5-134">Chcete-li získat související objekty, nejsou vrácené typy projektů do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="c13c5-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="c13c5-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c13c5-135">See also</span></span>

- [<span data-ttu-id="c13c5-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c13c5-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
