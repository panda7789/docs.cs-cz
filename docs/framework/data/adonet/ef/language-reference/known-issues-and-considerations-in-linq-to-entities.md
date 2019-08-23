---
title: Známé problémy a aspekty u LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 66af3395d7ba7271323ad6461e8e1fb8c823a1c6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913905"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="66ff3-102">Známé problémy a aspekty u LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="66ff3-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="66ff3-103">V této části najdete informace o známých problémech s LINQ to Entities dotazy.</span><span class="sxs-lookup"><span data-stu-id="66ff3-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="66ff3-104">Dotazy LINQ, které nelze uložit do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="66ff3-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="66ff3-105">Došlo ke ztrátě informací o objednávání.</span><span class="sxs-lookup"><span data-stu-id="66ff3-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="66ff3-106">Celá čísla bez znaménka nejsou podporovaná.</span><span class="sxs-lookup"><span data-stu-id="66ff3-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="66ff3-107">Chyby konverze typu</span><span class="sxs-lookup"><span data-stu-id="66ff3-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="66ff3-108">Odkazování na jiné než skalární proměnné se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="66ff3-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="66ff3-109">Vnořené dotazy mohou selhat s SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="66ff3-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="66ff3-110">Projektování na anonymní typ</span><span class="sxs-lookup"><span data-stu-id="66ff3-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="66ff3-111">Dotazy LINQ, které nelze uložit do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="66ff3-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="66ff3-112">Počínaje .NET Framework 4,5 jsou dotazy LINQ to Entities automaticky ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="66ff3-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="66ff3-113">Nicméně LINQ to Entities dotazy, které aplikují `Enumerable.Contains` operátor na kolekce v paměti, nejsou automaticky ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="66ff3-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="66ff3-114">V kompilovaných dotazech LINQ se taky Parametrizace kolekce v paměti, které se nepovolují.</span><span class="sxs-lookup"><span data-stu-id="66ff3-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="66ff3-115">Došlo ke ztrátě informací o objednávání.</span><span class="sxs-lookup"><span data-stu-id="66ff3-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="66ff3-116">Při projednávání sloupců do anonymního typu dojde ke ztrátě informací o objednávce v některých dotazech, které jsou spouštěny s databází SQL Server 2005 nastavenou na úroveň kompatibility "80".</span><span class="sxs-lookup"><span data-stu-id="66ff3-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="66ff3-117">K tomu dochází, když název sloupce v seznamu ORDER-by odpovídá názvu sloupce v selektoru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="66ff3-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="66ff3-118">Celá čísla bez znaménka nejsou podporovaná.</span><span class="sxs-lookup"><span data-stu-id="66ff3-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="66ff3-119">Určení typu unsigned integer v dotazu LINQ to Entities není podporováno, protože [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nepodporuje celá čísla bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="66ff3-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="66ff3-120">Zadáte-li unsigned integer, <xref:System.ArgumentException> bude vyvolána výjimka během překladu výrazu dotazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="66ff3-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="66ff3-121">V tomto příkladu se dotazuje na objednávku s ID 48000.</span><span class="sxs-lookup"><span data-stu-id="66ff3-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="66ff3-122">Chyby konverze typu</span><span class="sxs-lookup"><span data-stu-id="66ff3-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="66ff3-123">V Visual Basic `CByte` <xref:System.Data.SqlClient.SqlException> je při mapování vlastnosti na sloupec SQL Server bitového typu s hodnotou 1 pomocí funkce vyvolána zpráva "Chyba aritmetického přetečení".</span><span class="sxs-lookup"><span data-stu-id="66ff3-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="66ff3-124">Následující příklad provede dotaz na `Product.MakeFlag` sloupec v ukázkové databázi AdventureWorks a vyvolá výjimku při iteraci výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="66ff3-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="66ff3-125">Odkazování na jiné než skalární proměnné se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="66ff3-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="66ff3-126">Odkazování na jiné než skalární proměnné, jako je například entita, není v dotazu podporováno.</span><span class="sxs-lookup"><span data-stu-id="66ff3-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="66ff3-127">Pokud se takový dotaz spustí, <xref:System.NotSupportedException> je vyvolána výjimka se zprávou, že se zobrazí zpráva "nelze vytvořit konstantní hodnotu typu. `EntityType`</span><span class="sxs-lookup"><span data-stu-id="66ff3-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="66ff3-128">V tomto kontextu jsou podporovány pouze primitivní typy (například Int32, String a GUID). "</span><span class="sxs-lookup"><span data-stu-id="66ff3-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66ff3-129">Odkazování na kolekci skalárních proměnných je podporováno.</span><span class="sxs-lookup"><span data-stu-id="66ff3-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="66ff3-130">Vnořené dotazy mohou selhat s SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="66ff3-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="66ff3-131">V případě SQL Server 2000 mohou dotazy LINQ to Entities selhat, pokud budou vyprodukovány vnořené dotazy Transact-SQL, které mají hloubku tři nebo více úrovní.</span><span class="sxs-lookup"><span data-stu-id="66ff3-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="66ff3-132">Projektování na anonymní typ</span><span class="sxs-lookup"><span data-stu-id="66ff3-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="66ff3-133">Definujete-li počáteční cestu dotazu pro zahrnutí souvisejících objektů pomocí <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metody <xref:System.Data.Objects.ObjectQuery%601> v a poté pomocí LINQ k navrácení vrácených objektů do anonymního typu, objekty zadané v metodě include nejsou zahrnuty v dotazu. důsledk.</span><span class="sxs-lookup"><span data-stu-id="66ff3-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="66ff3-134">Chcete-li získat související objekty, neprojekt vrátí typy do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="66ff3-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="66ff3-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66ff3-135">See also</span></span>

- [<span data-ttu-id="66ff3-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="66ff3-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
