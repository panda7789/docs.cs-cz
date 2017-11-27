---
title: "Dotazy křížové tabulky (LINQ na DataSet)"
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
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0b829840257dc2b3b4bbf0b8c3a294a77060e2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cross-table-queries-linq-to-dataset"></a><span data-ttu-id="656b3-102">Dotazy křížové tabulky (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="656b3-102">Cross-Table Queries (LINQ to DataSet)</span></span>
<span data-ttu-id="656b3-103">Kromě dotazování na jednotlivé tabulky, můžete také provést křížové tabulky dotazy v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="656b3-103">In addition to querying a single table, you can also perform cross-table queries in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="656b3-104">To se provádí pomocí *spojení*.</span><span class="sxs-lookup"><span data-stu-id="656b3-104">This is done by using a *join*.</span></span> <span data-ttu-id="656b3-105">Spojení je přidružení objektů v jeden zdroj dat s objekty, které sdílejí společný atribut ve zdroji dat, jako je produkt nebo se obraťte na ID.</span><span class="sxs-lookup"><span data-stu-id="656b3-105">A join is the association of objects in one data source with objects that share a common attribute in another data source, such as a product or contact ID.</span></span> <span data-ttu-id="656b3-106">Relace mezi objekty jsou v objektově orientované programování poměrně snadno přejít, protože každý objekt má člena, který odkazuje na jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="656b3-106">In object-oriented programming, relationships between objects are relatively easy to navigate because each object has a member that references another object.</span></span> <span data-ttu-id="656b3-107">V tabulkách externí databáze ale navigace relací není stejně jednoduché.</span><span class="sxs-lookup"><span data-stu-id="656b3-107">In external database tables, however, navigating relationships is not as straightforward.</span></span> <span data-ttu-id="656b3-108">Databázové tabulky neobsahuje předdefinovaný vztahy.</span><span class="sxs-lookup"><span data-stu-id="656b3-108">Database tables do not contain built-in relationships.</span></span> <span data-ttu-id="656b3-109">V těchto případech operace spojení lze tak, aby odpovídaly elementy z každého zdroje.</span><span class="sxs-lookup"><span data-stu-id="656b3-109">In these cases, the join operation can be used to match elements from each source.</span></span> <span data-ttu-id="656b3-110">Například zadány dvě tabulky, které obsahují informace o produktu a informace o prodeji, můžete použít operace spojení tak, aby odpovídaly informace o prodeji a produktů pro stejné prodeje pořadí.</span><span class="sxs-lookup"><span data-stu-id="656b3-110">For example, given two tables that contain product information and sales information, you could use a join operation to match sales information and products for the same sales order.</span></span>  
  
 <span data-ttu-id="656b3-111">[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework poskytuje dva operátory, připojte <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="656b3-111">The [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] framework provides two join operators, <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="656b3-112">Provedení těchto operátorů *operátorem*: tedy spojení, které odpovídají dvěma datovými zdrojů, pouze když jejich klíče jsou si rovny.</span><span class="sxs-lookup"><span data-stu-id="656b3-112">These operators perform *equi-joins*: that is, joins that match two data sources only when their keys are equal.</span></span> <span data-ttu-id="656b3-113">(Oproti tomu [!INCLUDE[tsql](../../../../includes/tsql-md.md)] podporuje připojení operátory než `equals`, například `less than` operátor.)</span><span class="sxs-lookup"><span data-stu-id="656b3-113">(By contrast, [!INCLUDE[tsql](../../../../includes/tsql-md.md)] supports join operators other than `equals`, such as the `less than` operator.)</span></span>  
  
 <span data-ttu-id="656b3-114">V podmínkách relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení.</span><span class="sxs-lookup"><span data-stu-id="656b3-114">In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join.</span></span> <span data-ttu-id="656b3-115">Vnitřní spojení je typ připojení ve které se vrátí pouze ty objekty, které mají odpovídající v opačné datové sady.</span><span class="sxs-lookup"><span data-stu-id="656b3-115">An inner join is a type of join in which only those objects that have a match in the opposite data set are returned.</span></span>  
  
 <span data-ttu-id="656b3-116"><xref:System.Linq.Enumerable.GroupJoin%2A> Operátory mají ekvivalent v podmínkách relační databáze, je implementace nadmnožinou vnitřní spojení a levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="656b3-116">The <xref:System.Linq.Enumerable.GroupJoin%2A> operators have no direct equivalent in relational database terms; they implement a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="656b3-117">Levé vnější spojení je spojení, která vrací každý prvek první kolekce (levém), i když nemá žádné korelační elementy v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="656b3-117">A left outer join is a join that returns each element of the first (left) collection, even if it has no correlated elements in the second collection.</span></span>  
  
 <span data-ttu-id="656b3-118">Další informace o spojení najdete v tématu [připojení Operations](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span><span class="sxs-lookup"><span data-stu-id="656b3-118">For more information about joins, see [Join Operations](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span></span>  
  
## <a name="example"></a><span data-ttu-id="656b3-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="656b3-119">Example</span></span>  
 <span data-ttu-id="656b3-120">Následující příklad provádí tradiční připojení `SalesOrderHeader` a `SalesOrderDetail` tabulky z ukázkovou databázi AdventureWorks získat online objednávky z srpnu.</span><span class="sxs-lookup"><span data-stu-id="656b3-120">The following example performs a traditional join of the `SalesOrderHeader` and `SalesOrderDetail` tables from the AdventureWorks sample database to obtain online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="656b3-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="656b3-121">See Also</span></span>  
 [<span data-ttu-id="656b3-122">Dotazování datové sady</span><span class="sxs-lookup"><span data-stu-id="656b3-122">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="656b3-123">Dotazy na jedné tabulky</span><span class="sxs-lookup"><span data-stu-id="656b3-123">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="656b3-124">Dotazování typové datové sady</span><span class="sxs-lookup"><span data-stu-id="656b3-124">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [<span data-ttu-id="656b3-125">Operace sjednocení</span><span class="sxs-lookup"><span data-stu-id="656b3-125">Join Operations</span></span>](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [<span data-ttu-id="656b3-126">LINQ na DataSet příklady</span><span class="sxs-lookup"><span data-stu-id="656b3-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
