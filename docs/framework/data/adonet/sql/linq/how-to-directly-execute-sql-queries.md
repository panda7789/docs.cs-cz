---
title: "Postupy: přímo provádění dotazů SQL"
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
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e8bbeb0d7ce040387b263486b947e793eca39d29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="b3bc5-102">Postupy: přímo provádění dotazů SQL</span><span class="sxs-lookup"><span data-stu-id="b3bc5-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b3bc5-103">Přeloží dotazy, které zapisovat do parametrizované dotazy SQL (v textové podobě) a odešle je k systému SQL server pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-103"> translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="b3bc5-104">SQL nelze provést řadu metod, které mohou být místně dostupné pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b3bc5-105">pokusí se převést tyto místní metody na ekvivalentní operací a funkcí, které jsou k dispozici v prostředí SQL.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-105"> tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="b3bc5-106">Většina metody a operátory na [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] vestavěné typy mít přímý převody příkazy SQL.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-106">Most methods and operators on [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="b3bc5-107">Některé je možné vytvořit z funkcí, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="b3bc5-108">Ty, které není možné vygenerovat výjimky v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="b3bc5-109">Další informace najdete v tématu [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="b3bc5-109">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="b3bc5-110">V případech, kde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu je nedostatečná pro úlohu specializované, můžete použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodu pro spuštění příkazu jazyka SQL a pak převést výsledek dotazu přímo do objektů.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3bc5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3bc5-111">Example</span></span>  
 <span data-ttu-id="b3bc5-112">V následujícím příkladu předpokládáme, že data `Customer` třída je rozdělena ve dvou tabulek (customer1 a customer2).</span><span class="sxs-lookup"><span data-stu-id="b3bc5-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="b3bc5-113">Dotaz vrátí posloupnost `Customer` objekty.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="b3bc5-114">Tak dlouho, dokud shodovat s názvy sloupců v tabulkové výsledky sloupce vlastnosti třídy entity [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří vašich objektů mimo jakýkoli dotaz SQL.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3bc5-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3bc5-115">Example</span></span>  
 <span data-ttu-id="b3bc5-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda poskytuje také další parametry.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="b3bc5-117">Použijte například následující kód k provedení parametrizovaného dotazu.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="b3bc5-118">Parametry jsou vyjádřeny v textu dotazu pomocí stejné složené zápisu používané `Console.WriteLine()` a `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="b3bc5-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="b3bc5-119">Ve skutečnosti `String.Format()` se ve skutečnosti volá na řetězec dotazu, který zadáte, nahraďte složené braced parametry se vygeneruje názvy parametrů jako @p0, @p1 ..., @p(ne).</span><span class="sxs-lookup"><span data-stu-id="b3bc5-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bc5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3bc5-120">See Also</span></span>  
 [<span data-ttu-id="b3bc5-121">Základní informace</span><span class="sxs-lookup"><span data-stu-id="b3bc5-121">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="b3bc5-122">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="b3bc5-122">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
