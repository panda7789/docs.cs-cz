---
title: 'Postupy: Přímé spuštění dotazů SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: a4971bc05b22c38790c5fd1493e70cccf5eaae16
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793779"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="41041-102">Postupy: Přímé spuštění dotazů SQL</span><span class="sxs-lookup"><span data-stu-id="41041-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="41041-103">přeloží dotazy zapsané do parametrizovaných dotazů SQL (v textovém formátu) a pošle je do SQL serveru pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="41041-103">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="41041-104">SQL nemůže spustit celou řadu metod, které mohou být k dispozici místně pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="41041-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="41041-105">pokusí se převést tyto místní metody na ekvivalentní operace a funkce, které jsou k dispozici v prostředí SQL.</span><span class="sxs-lookup"><span data-stu-id="41041-105">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="41041-106">Většina metod a operátorů v .NET Framework předdefinovaných typů má přímé překlady do příkazů SQL.</span><span class="sxs-lookup"><span data-stu-id="41041-106">Most methods and operators on .NET Framework built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="41041-107">Některé mohou být vytvořeny z dostupných funkcí.</span><span class="sxs-lookup"><span data-stu-id="41041-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="41041-108">Ty, které se nedají vyrobit, generují výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="41041-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="41041-109">Další informace naleznete v tématu [mapování typu SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="41041-109">For more information, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="41041-110">V případech, kdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je dotaz nedostatečný pro specializovanou úlohu, lze <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> použít metodu pro spuštění dotazu SQL a následně převést výsledek dotazu přímo do objektů.</span><span class="sxs-lookup"><span data-stu-id="41041-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41041-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="41041-111">Example</span></span>  
 <span data-ttu-id="41041-112">V následujícím příkladu Předpokládejme, že data pro `Customer` třídu jsou rozložena do dvou tabulek (Customer1 a Customer2).</span><span class="sxs-lookup"><span data-stu-id="41041-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="41041-113">Dotaz vrátí sekvenci `Customer` objektů.</span><span class="sxs-lookup"><span data-stu-id="41041-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="41041-114">Pokud názvy sloupců v tabulkových výsledcích odpovídají vlastnostem sloupce vaší třídy entity, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo libovolný dotaz SQL.</span><span class="sxs-lookup"><span data-stu-id="41041-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41041-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="41041-115">Example</span></span>  
 <span data-ttu-id="41041-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda také umožňuje parametry.</span><span class="sxs-lookup"><span data-stu-id="41041-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="41041-117">Použijte následující kód k provedení parametrizovaného dotazu.</span><span class="sxs-lookup"><span data-stu-id="41041-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="41041-118">Parametry jsou vyjádřeny v textu dotazu pomocí stejného složeného zápisu `Console.WriteLine()` , který používá a. `String.Format()`</span><span class="sxs-lookup"><span data-stu-id="41041-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="41041-119">Ve skutečnosti `String.Format()` je ve skutečnosti volána v řetězci dotazu, který zadáte, a nahrazením složených složených parametrů názvy @p0generovaných parametrů, jako například, @p1 ..., @p(n).</span><span class="sxs-lookup"><span data-stu-id="41041-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41041-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41041-120">See also</span></span>

- [<span data-ttu-id="41041-121">Základní informace</span><span class="sxs-lookup"><span data-stu-id="41041-121">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="41041-122">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="41041-122">Querying the Database</span></span>](querying-the-database.md)
