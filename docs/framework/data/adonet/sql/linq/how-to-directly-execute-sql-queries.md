---
title: 'Postupy: Přímé spuštění dotazů SQL'
description: Naučte se používat ExecuteQuery ke spuštění dotazu a následnému převedení výsledků přímo do objektů v případech, kdy je LINQ to SQL dotaz nedostatečný.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 59bd404e41f6be1181d6a625c31ee23358db0df3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286362"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="1e79e-103">Postupy: Přímé spuštění dotazů SQL</span><span class="sxs-lookup"><span data-stu-id="1e79e-103">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1e79e-104">přeloží dotazy zapsané do parametrizovaných dotazů SQL (v textovém formátu) a pošle je do SQL serveru pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="1e79e-104">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="1e79e-105">SQL nemůže spustit celou řadu metod, které mohou být k dispozici místně pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1e79e-105">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1e79e-106">pokusí se převést tyto místní metody na ekvivalentní operace a funkce, které jsou k dispozici v prostředí SQL.</span><span class="sxs-lookup"><span data-stu-id="1e79e-106">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="1e79e-107">Většina metod a operátorů v .NET Framework předdefinovaných typů má přímé překlady do příkazů SQL.</span><span class="sxs-lookup"><span data-stu-id="1e79e-107">Most methods and operators on .NET Framework built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="1e79e-108">Některé mohou být vytvořeny z dostupných funkcí.</span><span class="sxs-lookup"><span data-stu-id="1e79e-108">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="1e79e-109">Ty, které se nedají vyrobit, generují výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="1e79e-109">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="1e79e-110">Další informace naleznete v tématu [mapování typu SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="1e79e-110">For more information, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="1e79e-111">V případech, kdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je dotaz nedostatečný pro specializovanou úlohu, lze použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodu pro spuštění dotazu SQL a následně převést výsledek dotazu přímo do objektů.</span><span class="sxs-lookup"><span data-stu-id="1e79e-111">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e79e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e79e-112">Example</span></span>  
 <span data-ttu-id="1e79e-113">V následujícím příkladu Předpokládejme, že data pro `Customer` třídu jsou rozložena do dvou tabulek (Customer1 a Customer2).</span><span class="sxs-lookup"><span data-stu-id="1e79e-113">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="1e79e-114">Dotaz vrátí sekvenci `Customer` objektů.</span><span class="sxs-lookup"><span data-stu-id="1e79e-114">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="1e79e-115">Pokud názvy sloupců v tabulkových výsledcích odpovídají vlastnostem sloupce vaší třídy entity, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo libovolný dotaz SQL.</span><span class="sxs-lookup"><span data-stu-id="1e79e-115">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e79e-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e79e-116">Example</span></span>  
 <span data-ttu-id="1e79e-117"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A>Metoda také umožňuje parametry.</span><span class="sxs-lookup"><span data-stu-id="1e79e-117">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="1e79e-118">Použijte následující kód k provedení parametrizovaného dotazu.</span><span class="sxs-lookup"><span data-stu-id="1e79e-118">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="1e79e-119">Parametry jsou vyjádřeny v textu dotazu pomocí stejného složeného zápisu, který používá `Console.WriteLine()` a `String.Format()` .</span><span class="sxs-lookup"><span data-stu-id="1e79e-119">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="1e79e-120">Ve skutečnosti `String.Format()` je ve skutečnosti volána v řetězci dotazu, který zadáte, a nahrazením složených složených parametrů názvy generovaných parametrů, jako například @p0 , @p1 ..., @p (n).</span><span class="sxs-lookup"><span data-stu-id="1e79e-120">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e79e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e79e-121">See also</span></span>

- [<span data-ttu-id="1e79e-122">Základní informace</span><span class="sxs-lookup"><span data-stu-id="1e79e-122">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="1e79e-123">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="1e79e-123">Querying the Database</span></span>](querying-the-database.md)
