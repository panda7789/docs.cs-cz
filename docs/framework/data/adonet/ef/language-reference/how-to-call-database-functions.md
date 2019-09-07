---
title: 'Postupy: Volání databázových funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: 115c50f157023b71a916b45b4498f9c59ad744bf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397632"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="b6e8b-102">Postupy: Volání databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="b6e8b-102">How to: Call Database Functions</span></span>
<span data-ttu-id="b6e8b-103"><xref:System.Data.Objects.SqlClient.SqlFunctions> Třída obsahuje metody, které zpřístupňují funkce SQL Server pro použití v LINQ to Entitiesch dotazech.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="b6e8b-104">Když použijete <xref:System.Data.Objects.SqlClient.SqlFunctions> metody v LINQ to Entities dotazy, v databázi se spustí odpovídající funkce databáze.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6e8b-105">Funkce databáze, které provádějí výpočet ze sady hodnot a vracejí jednu hodnotu (známé také jako agregační databázové funkce), lze vyvolat přímo.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="b6e8b-106">Jiné kanonické funkce lze volat pouze jako součást dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="b6e8b-107">Chcete-li volat agregační funkci přímo, musíte předat <xref:System.Data.Objects.ObjectQuery%601> funkci.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="b6e8b-108">Další informace najdete v druhém příkladu níže.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6e8b-109">Metody ve <xref:System.Data.Objects.SqlClient.SqlFunctions> třídě jsou specifické pro funkce SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="b6e8b-110">Podobné třídy, které zveřejňují databázové funkce, mohou být k dispozici prostřednictvím jiných poskytovatelů.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e8b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6e8b-111">Example</span></span>  
 <span data-ttu-id="b6e8b-112">V následujícím příkladu je použit [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="b6e8b-112">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="b6e8b-113">V příkladu se spustí dotaz LINQ to Entities, který používá <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metodu k vrácení všech kontaktů, jejichž příjmení začíná řetězcem "si":</span><span class="sxs-lookup"><span data-stu-id="b6e8b-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b6e8b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6e8b-114">Example</span></span>  
 <span data-ttu-id="b6e8b-115">V následujícím příkladu je použit [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="b6e8b-115">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="b6e8b-116">Příklad volá přímo agregační <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="b6e8b-117">Všimněte si, <xref:System.Data.Objects.ObjectQuery%601> že objekt je předán do funkce, která umožňuje jeho volání bez části dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="b6e8b-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b6e8b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6e8b-118">See also</span></span>

- [<span data-ttu-id="b6e8b-119">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b6e8b-119">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="b6e8b-120">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b6e8b-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
