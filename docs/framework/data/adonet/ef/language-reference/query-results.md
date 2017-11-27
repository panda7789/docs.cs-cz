---
title: "Výsledky dotazu"
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
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 32133d1b6fce619fb9990ab89820b7f19b6a5926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="query-results"></a><span data-ttu-id="60f93-102">Výsledky dotazu</span><span class="sxs-lookup"><span data-stu-id="60f93-102">Query Results</span></span>
<span data-ttu-id="60f93-103">Po [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu je převést na strom příkazů a provést, výsledky dotazu jsou obvykle vrátí jako jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="60f93-103">After a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is converted to command trees and executed, the query results are usually returned as one of the following:</span></span>  
  
-   <span data-ttu-id="60f93-104">Kolekce nula nebo více objektů zadané entity nebo projekci komplexních typů v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="60f93-104">A collection of zero or more typed entity objects or a projection of complex types in the conceptual model.</span></span>  
  
-   <span data-ttu-id="60f93-105">Typy CLR podporované v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="60f93-105">CLR types supported by the conceptual model.</span></span>  
  
-   <span data-ttu-id="60f93-106">Vložené kolekce.</span><span class="sxs-lookup"><span data-stu-id="60f93-106">Inline collections.</span></span>  
  
-   <span data-ttu-id="60f93-107">Anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="60f93-107">Anonymous types.</span></span>  
  
 <span data-ttu-id="60f93-108">Pokud se má spustit dotaz na zdroji dat, jsou výsledky vyhodnocena do typy CLR a vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="60f93-108">When the query has executed against the data source, the results are materialized into CLR types and returned to the client.</span></span> <span data-ttu-id="60f93-109">Všechny materialization objektu provádí [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60f93-109">All object materialization is performed by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="60f93-110">Všechny chyby, které jsou výsledkem nebylo možné mezi [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] a způsobí, že modulu CLR výjimky vyvolání během materialization objektu.</span><span class="sxs-lookup"><span data-stu-id="60f93-110">Any errors that result from an inability to map between the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] and the CLR will cause exceptions to be thrown during object materialization.</span></span>  
  
 <span data-ttu-id="60f93-111">Pokud spuštění dotazu vrátí konceptuálního modelu primitivní typy, výsledky obsahovat typů CLR, které jsou samostatné a odpojená od [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60f93-111">If the query execution returns primitive conceptual model types, the results consist of CLR types that are stand-alone and disconnected from the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="60f93-112">Ale pokud dotaz vrátí kolekci objektů zadané entity, reprezentována <xref:System.Data.Objects.ObjectQuery%601>, tyto typy jsou sledovány objektem do kontextu objektu.</span><span class="sxs-lookup"><span data-stu-id="60f93-112">However, if the query returns a collection of typed entity objects, represented by <xref:System.Data.Objects.ObjectQuery%601>, those types are tracked by the object context.</span></span> <span data-ttu-id="60f93-113">Všechny chování objektu (například podřízeného nebo nadřazeného kolekcí, sledování změn, polymorfismus a tak dále) jsou definované v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60f93-113">All object behavior (such as child/parent collections, change tracking, polymorphism, and so on) are as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="60f93-114">Tato funkce mohou být používány své kapacity, jak jsou definovány v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60f93-114">This functionality can be used in its capacity, as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="60f93-115">Další informace najdete v tématu [práce s objekty](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="60f93-115">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="60f93-116">Struktura typy vráceny z dotazů (například anonymní typy a komplexní typy s možnou hodnotou Null) můžou být `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="60f93-116">Struct types returned from queries (such as anonymous types and nullable complex types) can be of `null` value.</span></span> <span data-ttu-id="60f93-117"><xref:System.Data.Objects.DataClasses.EntityCollection%601> Vlastnost vrácenou entitu může být také z `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="60f93-117">An <xref:System.Data.Objects.DataClasses.EntityCollection%601> property of a returned entity can also be of `null` value.</span></span> <span data-ttu-id="60f93-118">To může být důsledkem projekce vlastnost kolekce entita, která je `null` hodnotu, jako je například volání <xref:System.Linq.Queryable.FirstOrDefault%2A> na <xref:System.Data.Objects.ObjectQuery%601> , nemá žádné elementy.</span><span class="sxs-lookup"><span data-stu-id="60f93-118">This can result from projecting the collection property of an entity that is of `null` value, such as calling <xref:System.Linq.Queryable.FirstOrDefault%2A> on an <xref:System.Data.Objects.ObjectQuery%601> that has no elements.</span></span>  
  
 <span data-ttu-id="60f93-119">V některých situacích může zdát, že dotaz Generovat výsledku materializovaného během jejího provádění, ale dotaz bude proveden na serveru a objekt entity se nikdy vyžaduje v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="60f93-119">In certain situations, a query might appear to generate a materialized result during its execution, but the query will be executed on the server and the entity object will never be materialized in the CLR.</span></span> <span data-ttu-id="60f93-120">To může způsobit problémy, pokud jsou v závislosti na vedlejší účinky materialization objektu.</span><span class="sxs-lookup"><span data-stu-id="60f93-120">This can cause problems if you are depending on side effects of object materialization.</span></span>  
  
 <span data-ttu-id="60f93-121">Následující příklad obsahuje vlastní třídu, `MyContact`, s `LastName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="60f93-121">The following example contains a custom class, `MyContact`, with a `LastName` property.</span></span> <span data-ttu-id="60f93-122">Když `LastName` je vlastnost nastavena, `count` proměnné se zvýší.</span><span class="sxs-lookup"><span data-stu-id="60f93-122">When the `LastName` property is set, a `count` variable is incremented.</span></span> <span data-ttu-id="60f93-123">Pokud spustíte dvě následující dotazy, se zvýší první dotaz `count` při druhého dotazu není.</span><span class="sxs-lookup"><span data-stu-id="60f93-123">If you execute the two following queries, the first query will increment `count` while the second query will not.</span></span> <span data-ttu-id="60f93-124">Důvodem je, že v druhé dotazu `LastName` vlastnost se promítá z výsledků a `MyContact` třída je nikdy vytvořit, protože není potřeba provést dotaz na úložiště.</span><span class="sxs-lookup"><span data-stu-id="60f93-124">This is because in the second query the `LastName` property is projected from the results and the `MyContact` class is never created, because it is not required to execute the query on the store.</span></span>  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
