---
title: 'Postupy: Volání databázových funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: 5b3af3b74f79d436f39ca0515661b69d66d2d191
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825573"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="bc9a1-102">Postupy: Volání databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="bc9a1-102">How to: Call Database Functions</span></span>
<span data-ttu-id="bc9a1-103"><xref:System.Data.Objects.SqlClient.SqlFunctions> Třída obsahuje metody, které zpřístupnění funkcí systému SQL Server pomocí v technologii LINQ dotazy na entity.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="bc9a1-104">Při použití <xref:System.Data.Objects.SqlClient.SqlFunctions> metody v jazyce LINQ dotazy na entity, odpovídající funkce databáze jsou provedeny v databázi.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc9a1-105">Databázové funkce, které provádí výpočet na sadu hodnot a vrací jedinou hodnotu (označované také jako databáze agregační funkce) lze vyvolat přímo.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="bc9a1-106">Jiné kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="bc9a1-107">Agregační funkci volat přímo, je nutné předat <xref:System.Data.Objects.ObjectQuery%601> funkci.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="bc9a1-108">Další informace najdete ve druhém příkladu níže.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc9a1-109">Metody v <xref:System.Data.Objects.SqlClient.SqlFunctions> třídy jsou specifické pro funkce serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="bc9a1-110">Podobně jako třídy, která zpřístupňují funkce databáze může být k dispozici prostřednictvím dalších poskytovatelů.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc9a1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc9a1-111">Example</span></span>  
 <span data-ttu-id="bc9a1-112">V následujícím příkladu [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="bc9a1-112">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="bc9a1-113">V příkladu provede LINQ to Entities dotaz, který používá <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metody, která vrátí všechny kontakty, jejichž příjmení začíná "Si":</span><span class="sxs-lookup"><span data-stu-id="bc9a1-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="bc9a1-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc9a1-114">Example</span></span>  
 <span data-ttu-id="bc9a1-115">V následujícím příkladu [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="bc9a1-115">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="bc9a1-116">Příklad volá agregace <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> metoda přímo.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="bc9a1-117">Všimněte si, že <xref:System.Data.Objects.ObjectQuery%601> je předán do funkce, což umožňuje volat bez se zapojil dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="bc9a1-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bc9a1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc9a1-118">See also</span></span>
- [<span data-ttu-id="bc9a1-119">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="bc9a1-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="bc9a1-120">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="bc9a1-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
