---
title: ADO.NET a LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 0bebc8d890325ec4ab090470952e11b90d0e37ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248122"
---
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="7f67f-102">ADO.NET a LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7f67f-102">ADO.NET and LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7f67f-103">je součástí řady technologií ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7f67f-103">is part of the ADO.NET family of technologies.</span></span> <span data-ttu-id="7f67f-104">Vychází ze služeb poskytovaných modelem poskytovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7f67f-104">It is based on services provided by the ADO.NET provider model.</span></span> <span data-ttu-id="7f67f-105">Proto můžete kombinovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kód s existujícími aplikacemi ADO.NET a migrovat aktuální ADO.NET řešení do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f67f-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing ADO.NET applications and migrate current ADO.NET solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="7f67f-106">Následující obrázek poskytuje podrobný pohled na vztah.</span><span class="sxs-lookup"><span data-stu-id="7f67f-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="7f67f-107">![LINQ to SQL a ADO.NET](./media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="7f67f-107">![LINQ to SQL and ADO.NET](./media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="7f67f-108">Připojení</span><span class="sxs-lookup"><span data-stu-id="7f67f-108">Connections</span></span>  
 <span data-ttu-id="7f67f-109">Existující připojení ADO.NET můžete při vytváření vytvořit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="7f67f-109">You can supply an existing ADO.NET connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="7f67f-110">Tato dodaná připojení <xref:System.Data.Linq.DataContext> používají všechny operace proti (včetně dotazů).</span><span class="sxs-lookup"><span data-stu-id="7f67f-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="7f67f-111">Pokud je připojení již otevřeno, ponechá ho v době, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kdy jste s ním skončili.</span><span class="sxs-lookup"><span data-stu-id="7f67f-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="7f67f-112">K připojení můžete vždy přistupovat a uzavřít ho pomocí <xref:System.Data.Linq.DataContext.Connection%2A> vlastnosti, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="7f67f-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="7f67f-113">Transakce</span><span class="sxs-lookup"><span data-stu-id="7f67f-113">Transactions</span></span>  
 <span data-ttu-id="7f67f-114">Můžete dodat svou <xref:System.Data.Linq.DataContext> vlastní databázovou transakci, pokud vaše aplikace již transakci iniciovala a <xref:System.Data.Linq.DataContext> chcete, aby byla zahrnuta.</span><span class="sxs-lookup"><span data-stu-id="7f67f-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="7f67f-115">Upřednostňovanou metodou provádění transakcí s .NET Framework je použití <xref:System.Transactions.TransactionScope> objektu.</span><span class="sxs-lookup"><span data-stu-id="7f67f-115">The preferred method of doing transactions with the .NET Framework is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="7f67f-116">Pomocí tohoto přístupu můžete provádět distribuované transakce, které fungují napříč databázemi a dalšími správci prostředků rezidentů v paměti.</span><span class="sxs-lookup"><span data-stu-id="7f67f-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="7f67f-117">Rozsahy transakcí vyžadují, aby bylo možné spustit několik zdrojů.</span><span class="sxs-lookup"><span data-stu-id="7f67f-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="7f67f-118">Propagují se na distribuované transakce pouze v případě, že je v rámci oboru transakce více připojení.</span><span class="sxs-lookup"><span data-stu-id="7f67f-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="7f67f-119">Tento přístup nelze použít pro všechny databáze.</span><span class="sxs-lookup"><span data-stu-id="7f67f-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="7f67f-120">Připojení SqlClient například nemůže propagovat systémové transakce, když funguje na serveru s SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="7f67f-120">For example, the SqlClient connection cannot promote system transactions when it works against a SQL Server 2000 server.</span></span> <span data-ttu-id="7f67f-121">Místo toho automaticky zařadí úplnou distribuovanou transakci pokaždé, když uvidí rozsah transakce, který se používá.</span><span class="sxs-lookup"><span data-stu-id="7f67f-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="7f67f-122">Přímé příkazy SQL</span><span class="sxs-lookup"><span data-stu-id="7f67f-122">Direct SQL Commands</span></span>  
 <span data-ttu-id="7f67f-123">V době, kdy se můžete setkat s situacemi, <xref:System.Data.Linq.DataContext> kdy je schopnost dotazování nebo odeslání změn nedostatečná pro specializovanou úlohu, kterou chcete provést.</span><span class="sxs-lookup"><span data-stu-id="7f67f-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="7f67f-124">V těchto případech můžete použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodu k vystavení příkazů SQL Database a převést výsledky dotazu na objekty.</span><span class="sxs-lookup"><span data-stu-id="7f67f-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="7f67f-125">Předpokládejme například, že data pro `Customer` třídu jsou rozložena do dvou tabulek (Customer1 a Customer2).</span><span class="sxs-lookup"><span data-stu-id="7f67f-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="7f67f-126">Následující dotaz vrátí sekvenci `Customer` objektů:</span><span class="sxs-lookup"><span data-stu-id="7f67f-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="7f67f-127">Pokud názvy sloupců v tabulkových výsledcích odpovídají vlastnostem sloupce vaší třídy entity, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo libovolný dotaz SQL.</span><span class="sxs-lookup"><span data-stu-id="7f67f-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="7f67f-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f67f-128">Parameters</span></span>  
 <span data-ttu-id="7f67f-129"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda přijímá parametry.</span><span class="sxs-lookup"><span data-stu-id="7f67f-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="7f67f-130">Následující kód provede parametrizovaný dotaz:</span><span class="sxs-lookup"><span data-stu-id="7f67f-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> <span data-ttu-id="7f67f-131">Parametry jsou vyjádřeny v textu dotazu pomocí stejného složeného zápisu `Console.WriteLine()` , který používá a. `String.Format()`</span><span class="sxs-lookup"><span data-stu-id="7f67f-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="7f67f-132">`String.Format()`Převede řetězec dotazu, který zadáte, a nahradí parametry složené závorky s generovanými názvy parametrů `@p0`, například, `@p1` ..., `@p(n)`.</span><span class="sxs-lookup"><span data-stu-id="7f67f-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f67f-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f67f-133">See also</span></span>

- [<span data-ttu-id="7f67f-134">Základní informace</span><span class="sxs-lookup"><span data-stu-id="7f67f-134">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="7f67f-135">Postupy: Opakované použití připojení mezi příkazem ADO.NET a DataContext</span><span class="sxs-lookup"><span data-stu-id="7f67f-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
