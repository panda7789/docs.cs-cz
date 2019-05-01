---
title: 'Postupy: Přímé spuštění dotazů SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 6423959ed5036cc8ab2a88bb7273ef7aa95c8958
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037762"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="0b1c1-102">Postupy: Přímé spuštění dotazů SQL</span><span class="sxs-lookup"><span data-stu-id="0b1c1-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0b1c1-103">překládá dotazy, který napíšete do parametrizované dotazy jazyka SQL (ve formě textu) a odesílá je do serveru SQL server pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-103">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="0b1c1-104">SQL nelze provést různými metodami, které mohou být místně dostupný vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0b1c1-105">se pokusí převést tyto místní metody na ekvivalentní operacemi a funkcemi, které jsou k dispozici v prostředí SQL.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-105">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="0b1c1-106">Většina metod a operátory na [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] vestavěné typy mají přímé překlady příkazy jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-106">Most methods and operators on [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="0b1c1-107">Některé je možné vytvořit z funkcí, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="0b1c1-108">Ty, které není možné generovat výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="0b1c1-109">Další informace najdete v tématu [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0b1c1-109">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="0b1c1-110">V případech, kde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu není dostatečná pro specializované úlohy, můžete použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> má metoda spustí dotaz SQL a poté převést výsledek dotazu přímo do objektů.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b1c1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b1c1-111">Example</span></span>  
 <span data-ttu-id="0b1c1-112">V následujícím příkladu se předpokládá, že data `Customer` třídy se pak rozdělí více než dvě tabulky (customer1 a customer2).</span><span class="sxs-lookup"><span data-stu-id="0b1c1-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="0b1c1-113">Dotaz vrátí sekvenci `Customer` objekty.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="0b1c1-114">Za předpokladu, názvy sloupců v tabulkové výsledky odpovídají sloupec vlastnosti vaší entity třídy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo jakýkoli dotaz SQL.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b1c1-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b1c1-115">Example</span></span>  
 <span data-ttu-id="0b1c1-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda také umožňuje pro parametry.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="0b1c1-117">Použijte například následující kód k provedení parametrický dotaz.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="0b1c1-118">Parametry jsou vyjádřeny v textu dotazu pomocí stejné složených zápisu používají `Console.WriteLine()` a `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="0b1c1-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="0b1c1-119">Ve skutečnosti `String.Format()` ve skutečnosti je volán na řetězec dotazu, který zadáte, nahraďte složených závorkách parametry s generované názvy parametrů, jako @p0, @p1 ..., @p(n).</span><span class="sxs-lookup"><span data-stu-id="0b1c1-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1c1-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b1c1-120">See also</span></span>

- [<span data-ttu-id="0b1c1-121">Základní informace</span><span class="sxs-lookup"><span data-stu-id="0b1c1-121">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="0b1c1-122">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="0b1c1-122">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
