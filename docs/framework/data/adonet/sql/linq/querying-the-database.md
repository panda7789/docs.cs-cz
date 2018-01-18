---
title: "Dotaz na databázi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4e7f2c2a3936fc27e963867a4a4bf4bc210c6b7e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="querying-the-database"></a><span data-ttu-id="0ccec-102">Dotaz na databázi</span><span class="sxs-lookup"><span data-stu-id="0ccec-102">Querying the Database</span></span>
<span data-ttu-id="0ccec-103">Tato skupina témat popisuje, jak vyvíjet a spouštět dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projekty.</span><span class="sxs-lookup"><span data-stu-id="0ccec-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ccec-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0ccec-104">In This Section</span></span>  
 [<span data-ttu-id="0ccec-105">Postupy: Dotaz na informace</span><span class="sxs-lookup"><span data-stu-id="0ccec-105">How to: Query for Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-query-for-information.md)  
 <span data-ttu-id="0ccec-106">Stručně ukazuje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy jsou v podstatě stejný jako [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazuje obecně.</span><span class="sxs-lookup"><span data-stu-id="0ccec-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="0ccec-107">Postupy: Načtení informací ve stavu jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0ccec-107">How to: Retrieve Information As Read-Only</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="0ccec-108">Popisuje, jak zvýšit výkon dotazů, když je plánovaná nijak nemění data.</span><span class="sxs-lookup"><span data-stu-id="0ccec-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="0ccec-109">Postupy: Určení objemu načítaných souvisejících dat</span><span class="sxs-lookup"><span data-stu-id="0ccec-109">How to: Control How Much Related Data Is Retrieved</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="0ccec-110">Popisuje, jak řídit, která související data se načítají společně s hlavní cíl.</span><span class="sxs-lookup"><span data-stu-id="0ccec-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="0ccec-111">Postupy: Filtrování souvisejících dat</span><span class="sxs-lookup"><span data-stu-id="0ccec-111">How to: Filter Related Data</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-related-data.md)  
 <span data-ttu-id="0ccec-112">Popisuje, jak načíst související data pomocí poddotazu.</span><span class="sxs-lookup"><span data-stu-id="0ccec-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="0ccec-113">Postupy: Vypnutí odloženého načítání</span><span class="sxs-lookup"><span data-stu-id="0ccec-113">How to: Turn Off Deferred Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="0ccec-114">Popisuje, jak chcete-li vypnout odložené načítání.</span><span class="sxs-lookup"><span data-stu-id="0ccec-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="0ccec-115">Postupy: Přímé spuštění dotazů SQL</span><span class="sxs-lookup"><span data-stu-id="0ccec-115">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="0ccec-116">Popisuje postup odesílání dotazů pomocí jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="0ccec-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="0ccec-117">Postupy: Uložení a opakované použití dotazů</span><span class="sxs-lookup"><span data-stu-id="0ccec-117">How to: Store and Reuse Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="0ccec-118">Popisuje způsob kompilace dotazu jednou, ale jeho použití vícekrát s odlišnými parametry.</span><span class="sxs-lookup"><span data-stu-id="0ccec-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="0ccec-119">Postupy: Zpracování složených klíčů v dotazech</span><span class="sxs-lookup"><span data-stu-id="0ccec-119">How to: Handle Composite Keys in Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="0ccec-120">Popisuje, jak obsahovat více než jeden sloupec v dotazu, kde operátor přijímá pouze jeden argument.</span><span class="sxs-lookup"><span data-stu-id="0ccec-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="0ccec-121">Postupy: Načtení mnoha objektů najednou</span><span class="sxs-lookup"><span data-stu-id="0ccec-121">How to: Retrieve Many Objects At Once</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="0ccec-122">Popisuje způsob použití <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ccec-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="0ccec-123">Postupy: Filtrování na úrovni DataContext</span><span class="sxs-lookup"><span data-stu-id="0ccec-123">How to: Filter at the DataContext Level</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="0ccec-124">Popisuje použití jiného <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ccec-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="0ccec-125">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="0ccec-125">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="0ccec-126">Poskytuje mnoho příkladů dotazů.</span><span class="sxs-lookup"><span data-stu-id="0ccec-126">Provides many examples of queries.</span></span>
