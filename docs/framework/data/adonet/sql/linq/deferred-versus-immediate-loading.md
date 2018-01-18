---
title: "Odložení versus okamžitou načítání"
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
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f40f6c3d94aeeae41c4cce00bac8de863226f287
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="deferred-versus-immediate-loading"></a><span data-ttu-id="662cd-102">Odložení versus okamžitou načítání</span><span class="sxs-lookup"><span data-stu-id="662cd-102">Deferred versus Immediate Loading</span></span>
<span data-ttu-id="662cd-103">Při dotazu pro objekt, načíst ve skutečnosti jenom na objekt, který jste požádali.</span><span class="sxs-lookup"><span data-stu-id="662cd-103">When you query for an object, you actually retrieve only the object you requested.</span></span> <span data-ttu-id="662cd-104">*Související* objekty nejsou automaticky načtených ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="662cd-104">The *related* objects are not automatically fetched at the same time.</span></span> <span data-ttu-id="662cd-105">(Další informace najdete v tématu [dotazování napříč vztahy](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Nejde zobrazit, že skutečnost, že souvisejících objektů, které ještě nejsou načíst, protože pokus o přístup k těmto vytváří požadavek, který je načte.</span><span class="sxs-lookup"><span data-stu-id="662cd-105">(For more information, see [Querying Across Relationships](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) You cannot see the fact that the related objects are not already loaded, because an attempt to access them produces a request that retrieves them.</span></span>  
  
 <span data-ttu-id="662cd-106">Můžete například chtít dotazovat na konkrétní sadu objednávek a jen občas odesílat e-mailové oznámení pro konkrétní zákazníky.</span><span class="sxs-lookup"><span data-stu-id="662cd-106">For example, you might want to query for a particular set of orders and then only occasionally send an e-mail notification to particular customers.</span></span> <span data-ttu-id="662cd-107">Můžete nemusí nutně nejdřív načíst všechna data zákazníků s každou pořadí.</span><span class="sxs-lookup"><span data-stu-id="662cd-107">You would not necessarily need initially to retrieve all customer data with every order.</span></span> <span data-ttu-id="662cd-108">Odložené načítání můžete použít k odložení načtení doplňující informace, dokud je nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="662cd-108">You can use deferred loading to defer retrieval of extra information until you absolutely have to.</span></span> <span data-ttu-id="662cd-109">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="662cd-109">Consider the following example:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 <span data-ttu-id="662cd-110">Naopak může být také hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="662cd-110">The opposite might also be true.</span></span> <span data-ttu-id="662cd-111">Máte aplikaci, která se má zobrazit zákazníka a pořadí dat ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="662cd-111">You might have an application that has to view customer and order data at the same time.</span></span> <span data-ttu-id="662cd-112">Víte, že je nutné, aby obě sady dat.</span><span class="sxs-lookup"><span data-stu-id="662cd-112">You know you need both sets of data.</span></span> <span data-ttu-id="662cd-113">Víte, že aplikace musí pro každého zákazníka a informace o objednávce také získat výsledky.</span><span class="sxs-lookup"><span data-stu-id="662cd-113">You know your application needs order information for each customer as soon as you get the results.</span></span> <span data-ttu-id="662cd-114">Byste neměli chtít odeslat jednotlivé dotazy na objednávky pro každý zákazníka.</span><span class="sxs-lookup"><span data-stu-id="662cd-114">You would not want to submit individual queries for orders for every customer.</span></span> <span data-ttu-id="662cd-115">Co chcete je načíst data pořadí společně s zákazníků.</span><span class="sxs-lookup"><span data-stu-id="662cd-115">What you really want is to retrieve the order data together with the customers.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 <span data-ttu-id="662cd-116">Tím, které tvoří smíšený produkt a načítání relativní bity data jako jeden velký projekce můžete také spojení zákazníci a objednávky v dotazu.</span><span class="sxs-lookup"><span data-stu-id="662cd-116">You can also join customers and orders in a query by forming the cross-product and retrieving all the relative bits of data as one large projection.</span></span> <span data-ttu-id="662cd-117">Ale tyto výsledky nejsou entity.</span><span class="sxs-lookup"><span data-stu-id="662cd-117">But these results are not entities.</span></span> <span data-ttu-id="662cd-118">(Další informace najdete v tématu [technologii LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)).</span><span class="sxs-lookup"><span data-stu-id="662cd-118">(For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)).</span></span> <span data-ttu-id="662cd-119">Entity jsou objekty, které mají identity a že můžete upravit, zatímco tyto výsledky by měli být projekce, které nelze změnit a trvalé.</span><span class="sxs-lookup"><span data-stu-id="662cd-119">Entities are objects that have identity and that you can modify, whereas these results would be projections that cannot be changed and persisted.</span></span> <span data-ttu-id="662cd-120">I horší můžete by být načítání velké množství redundantních dat jako každého zákazníka a opakuje pro každý pořadí, ve výstupu plochou spojení.</span><span class="sxs-lookup"><span data-stu-id="662cd-120">Even worse, you would be retrieving lots of redundant data as each customer repeats for each order in the flattened join output.</span></span>  
  
 <span data-ttu-id="662cd-121">Je třeba je způsob, jak načíst sadu souvisejících objektů, které ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="662cd-121">What you really need is a way to retrieve a set of related objects at the same time.</span></span> <span data-ttu-id="662cd-122">Sada je vymezen oddíl graf tak, aby vám by nikdy být načítání vyšší nebo nižší než to bylo nezbytné pro zamýšlený účel.</span><span class="sxs-lookup"><span data-stu-id="662cd-122">The set is a delineated section of a graph so that you would never be retrieving more or less than was necessary for your intended use.</span></span> <span data-ttu-id="662cd-123">Pro tento účel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje <xref:System.Data.Linq.DataLoadOptions> pro okamžité načítání oblasti objektový model.</span><span class="sxs-lookup"><span data-stu-id="662cd-123">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides <xref:System.Data.Linq.DataLoadOptions> for immediate loading of a region of your object model.</span></span> <span data-ttu-id="662cd-124">Metody patří:</span><span class="sxs-lookup"><span data-stu-id="662cd-124">Methods include:</span></span>  
  
-   <span data-ttu-id="662cd-125"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Metoda okamžitě načíst data související s hlavní cíl.</span><span class="sxs-lookup"><span data-stu-id="662cd-125">The  <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method, to immediately load data related to the main target.</span></span>  
  
-   <span data-ttu-id="662cd-126"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Metodu, filtrovat objekty načtené pro konkrétní relace.</span><span class="sxs-lookup"><span data-stu-id="662cd-126">The <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method, to filter objects retrieved for a particular relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662cd-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="662cd-127">See Also</span></span>  
 [<span data-ttu-id="662cd-128">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="662cd-128">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
