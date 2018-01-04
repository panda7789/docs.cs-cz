---
title: "Postupy: volání funkce databáze"
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
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7d385917940e1359b2dc5bef24bb1353db707424
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="0963a-102">Postupy: volání funkce databáze</span><span class="sxs-lookup"><span data-stu-id="0963a-102">How to: Call Database Functions</span></span>
<span data-ttu-id="0963a-103"><xref:System.Data.Objects.SqlClient.SqlFunctions> Třída obsahuje metody, které zveřejňují funkce SQL Server pomocí v technologii LINQ dotazů entity.</span><span class="sxs-lookup"><span data-stu-id="0963a-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="0963a-104">Při použití <xref:System.Data.Objects.SqlClient.SqlFunctions> metody v technologii LINQ dotazů entity, odpovídající funkce databáze jsou spouštěny v databázi.</span><span class="sxs-lookup"><span data-stu-id="0963a-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0963a-105">Funkce databáze, které provádět výpočet sadu hodnot a vrátí jednu hodnotu (také označované jako databáze agregační funkce) můžete přímo vyvolat.</span><span class="sxs-lookup"><span data-stu-id="0963a-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="0963a-106">Další kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0963a-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="0963a-107">Chcete-li volat přímo agregační funkci, musíte zadat <xref:System.Data.Objects.ObjectQuery%601> funkce.</span><span class="sxs-lookup"><span data-stu-id="0963a-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="0963a-108">Další informace najdete v druhém níže uvedeném příkladu.</span><span class="sxs-lookup"><span data-stu-id="0963a-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0963a-109">Metody v <xref:System.Data.Objects.SqlClient.SqlFunctions> třídy jsou specifické pro funkce systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0963a-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="0963a-110">Podobně jako třídy, které zveřejňují funkce databáze může být k dispozici prostřednictvím dalších zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="0963a-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0963a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="0963a-111">Example</span></span>  
 <span data-ttu-id="0963a-112">Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="0963a-112">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="0963a-113">V příkladu provede dotazu LINQ to Entities používající <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metody, která vrátí všechny kontakty, jejichž příjmení začíná "Ma":</span><span class="sxs-lookup"><span data-stu-id="0963a-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="0963a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="0963a-114">Example</span></span>  
 <span data-ttu-id="0963a-115">Následující příklad používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="0963a-115">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="0963a-116">V příkladu volá agregace <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> metoda přímo.</span><span class="sxs-lookup"><span data-stu-id="0963a-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="0963a-117">Všimněte si, že <xref:System.Data.Objects.ObjectQuery%601> předaný funkci, která umožňuje volá se, aniž by byly součástí dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0963a-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="0963a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0963a-118">See Also</span></span>  
 [<span data-ttu-id="0963a-119">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0963a-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="0963a-120">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0963a-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
