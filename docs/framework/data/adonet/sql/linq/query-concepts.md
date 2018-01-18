---
title: Koncepty dotazu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a125749-ccb5-49d5-999d-d2db7171d74d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4bea41ad092de4afe1a2fff7927321d63c43278e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="query-concepts"></a><span data-ttu-id="3f73b-102">Koncepty dotazu</span><span class="sxs-lookup"><span data-stu-id="3f73b-102">Query Concepts</span></span>
<span data-ttu-id="3f73b-103">Tato část popisuje klíčové koncepty pro návrh [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f73b-103">This section describes key concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f73b-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3f73b-104">In This Section</span></span>  
 [<span data-ttu-id="3f73b-105">Dotazy LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3f73b-105">LINQ to SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-queries.md)  
 <span data-ttu-id="3f73b-106">Odkazuje na Obecné [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] témata a vysvětluje položky specifické pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f73b-106">Refers to general [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] topics, and explains items specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="3f73b-107">Dotazování napříč relacemi</span><span class="sxs-lookup"><span data-stu-id="3f73b-107">Querying Across Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)  
 <span data-ttu-id="3f73b-108">Vysvětluje, jak použít atributy Association v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="3f73b-108">Explains how to use associations in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="3f73b-109">Vzdálené vs. místní spuštění</span><span class="sxs-lookup"><span data-stu-id="3f73b-109">Remote vs. Local Execution</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)  
 <span data-ttu-id="3f73b-110">Vysvětluje, jak určit, kam chcete dotaz spustit.</span><span class="sxs-lookup"><span data-stu-id="3f73b-110">Explains how to specify where you want your query executed.</span></span>  
  
 [<span data-ttu-id="3f73b-111">Odložené versus okamžité načítání</span><span class="sxs-lookup"><span data-stu-id="3f73b-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)  
 <span data-ttu-id="3f73b-112">Popisuje, jak zadat, když jsou načtena související objekty.</span><span class="sxs-lookup"><span data-stu-id="3f73b-112">Describes how to specify when related objects are loaded.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3f73b-113">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3f73b-113">Related Sections</span></span>  
 [<span data-ttu-id="3f73b-114">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="3f73b-114">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="3f73b-115">Obsahuje odkazy na témata, které vysvětlují [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie.</span><span class="sxs-lookup"><span data-stu-id="3f73b-115">Contains links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology.</span></span>  
  
 [<span data-ttu-id="3f73b-116">Identita objektu</span><span class="sxs-lookup"><span data-stu-id="3f73b-116">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 <span data-ttu-id="3f73b-117">Popisuje koncept identity objektu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f73b-117">Explains the concept of object identity in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="3f73b-118">Úvod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="3f73b-118">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="3f73b-119">Obsahuje úvod do operace dotazů v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f73b-119">Provides an introduction to query operations in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
