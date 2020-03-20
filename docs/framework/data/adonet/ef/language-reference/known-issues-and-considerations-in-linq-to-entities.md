---
title: Známé problémy a aspekty u LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 90119da0fce7a708323d790f91f28206cac0a0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150139"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="c732d-102">Známé problémy a aspekty u LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c732d-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="c732d-103">Tato část obsahuje informace o známých problémech s dotazy LINQ na entity.</span><span class="sxs-lookup"><span data-stu-id="c732d-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="c732d-104">Dotazy LINQ, které nelze uložit do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="c732d-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="c732d-105">Informace o objednávce ztraceny</span><span class="sxs-lookup"><span data-stu-id="c732d-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="c732d-106">Nepodepsaná celá čísla nejsou podporována</span><span class="sxs-lookup"><span data-stu-id="c732d-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="c732d-107">Chyby převodu typu</span><span class="sxs-lookup"><span data-stu-id="c732d-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="c732d-108">Odkazování na neskalární proměnné není podporováno</span><span class="sxs-lookup"><span data-stu-id="c732d-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="c732d-109">Vnořené dotazy mohou selhat se serverem SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="c732d-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="c732d-110">Promítání na anonymní typ</span><span class="sxs-lookup"><span data-stu-id="c732d-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="c732d-111">Dotazy LINQ, které nelze uložit do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="c732d-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="c732d-112">Počínaje rozhraním .NET Framework 4.5 jsou dotazy LINQ na entity automaticky ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c732d-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="c732d-113">Linq na entity dotazy, které `Enumerable.Contains` platí operátor v kolekcích v paměti nejsou automaticky ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c732d-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="c732d-114">Také parametrizace in-memory kolekce v kompilovaných linq dotazů není povoleno.</span><span class="sxs-lookup"><span data-stu-id="c732d-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>
## <a name="ordering-information-lost"></a><span data-ttu-id="c732d-115">Informace o objednávce ztraceny</span><span class="sxs-lookup"><span data-stu-id="c732d-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="c732d-116">Promítání sloupců do anonymního typu způsobí ztrátu informací o objednávce v některých dotazech, které jsou provedeny proti databázi serveru SQL Server 2005 nastavené na úroveň kompatibility "80".</span><span class="sxs-lookup"><span data-stu-id="c732d-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="c732d-117">K tomu dochází, když název sloupce v seznamu podle pořadí odpovídá názvu sloupce v selektoru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c732d-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="c732d-118">Nepodepsaná celá čísla nejsou podporována</span><span class="sxs-lookup"><span data-stu-id="c732d-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="c732d-119">Zadání nepodepsaného celého typu v dotazu LINQ na entity není podporováno, protože entity Framework nepodporuje nepodepsaná celá čísla.</span><span class="sxs-lookup"><span data-stu-id="c732d-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the Entity Framework does not support unsigned integers.</span></span> <span data-ttu-id="c732d-120">Pokud zadáte nepodepsané celé číslo, <xref:System.ArgumentException> bude během překladu výrazu dotazu vyvolána výjimka, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c732d-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="c732d-121">Tento příklad se dotazuje na objednávku s ID 48000.</span><span class="sxs-lookup"><span data-stu-id="c732d-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>
## <a name="type-conversion-errors"></a><span data-ttu-id="c732d-122">Chyby převodu typu</span><span class="sxs-lookup"><span data-stu-id="c732d-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="c732d-123">V jazyce Visual Basic při namapovat vlastnost na sloupec sql server `CByte` typu bitu s hodnotou 1 pomocí funkce, <xref:System.Data.SqlClient.SqlException> je vyvolána s "aritmetické přetečení chyby" zpráva.</span><span class="sxs-lookup"><span data-stu-id="c732d-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="c732d-124">Následující příklad dotazuje `Product.MakeFlag` sloupec v adventureworks ukázkové databáze a je vyvolána výjimka, když jsou výsledky dotazu iterovány přes.</span><span class="sxs-lookup"><span data-stu-id="c732d-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="c732d-125">Odkazování na neskalární proměnné není podporováno</span><span class="sxs-lookup"><span data-stu-id="c732d-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="c732d-126">Odkazování na neskalární proměnné, jako je entita, v dotazu není podporováno.</span><span class="sxs-lookup"><span data-stu-id="c732d-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="c732d-127">Při spuštění takového dotazu <xref:System.NotSupportedException> je vyvolána výjimka se zprávou "Nelze vytvořit `EntityType`konstantní hodnotu typu .</span><span class="sxs-lookup"><span data-stu-id="c732d-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="c732d-128">V tomto kontextu jsou podporovány pouze primitivní typy (například Int32, String a Guid).</span><span class="sxs-lookup"><span data-stu-id="c732d-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c732d-129">Odkazování na kolekci skalárních proměnných je podporováno.</span><span class="sxs-lookup"><span data-stu-id="c732d-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="c732d-130">Vnořené dotazy mohou selhat se serverem SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="c732d-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="c732d-131">S SQL Server 2000 LINQ entity dotazy může selhat, pokud vytvářejí vnořené transact-SQL dotazy, které jsou tři nebo více úrovní hluboké.</span><span class="sxs-lookup"><span data-stu-id="c732d-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="c732d-132">Promítání na anonymní typ</span><span class="sxs-lookup"><span data-stu-id="c732d-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="c732d-133">Pokud definujete počáteční cestu dotazu zahrnout <xref:System.Data.Objects.ObjectQuery%601.Include%2A> související objekty pomocí metody na <xref:System.Data.Objects.ObjectQuery%601> a potom pomocí LINQ promítat vrácené objekty anonymní typ, objekty zadané v include metoda nejsou zahrnuty ve výsledcích dotazu.</span><span class="sxs-lookup"><span data-stu-id="c732d-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="c732d-134">Chcete-li získat související objekty, nepromítejte vrácené typy anonymnímu typu.</span><span class="sxs-lookup"><span data-stu-id="c732d-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="c732d-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c732d-135">See also</span></span>

- [<span data-ttu-id="c732d-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c732d-136">LINQ to Entities</span></span>](linq-to-entities.md)
