---
title: ADO.NET a LINQ to SQL
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 4d2376a2e32ff099497a5dbcd6cb68d8ed526884
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979999"
---
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="491dc-102">ADO.NET a LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="491dc-102">ADO.NET and LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="491dc-103">je součástí řady technologií ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="491dc-103">is part of the ADO.NET family of technologies.</span></span> <span data-ttu-id="491dc-104">Vychází ze služeb poskytovaných modelem poskytovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="491dc-104">It is based on services provided by the ADO.NET provider model.</span></span> <span data-ttu-id="491dc-105">Proto můžete v existujících aplikacích ADO.NET kombinovat kód [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a migrovat aktuální ADO.NET řešení do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="491dc-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing ADO.NET applications and migrate current ADO.NET solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="491dc-106">Následující obrázek poskytuje podrobný pohled na vztah.</span><span class="sxs-lookup"><span data-stu-id="491dc-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="491dc-107">![LINQ to SQL a ADO.NET](./media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="491dc-107">![LINQ to SQL and ADO.NET](./media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="491dc-108">Připojení</span><span class="sxs-lookup"><span data-stu-id="491dc-108">Connections</span></span>  
 <span data-ttu-id="491dc-109">Při vytváření <xref:System.Data.Linq.DataContext>[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete dodat existující připojení ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="491dc-109">You can supply an existing ADO.NET connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="491dc-110">Toto poskytnutá připojení se používají u všech operací proti <xref:System.Data.Linq.DataContext> (včetně dotazů).</span><span class="sxs-lookup"><span data-stu-id="491dc-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="491dc-111">Pokud je připojení už otevřené, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ho po dokončení donechání.</span><span class="sxs-lookup"><span data-stu-id="491dc-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="491dc-112">K připojení můžete vždy přistupovat a jeho zavřením pomocí vlastnosti <xref:System.Data.Linq.DataContext.Connection%2A>, jak je uvedeno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="491dc-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="491dc-113">Transakce</span><span class="sxs-lookup"><span data-stu-id="491dc-113">Transactions</span></span>  
 <span data-ttu-id="491dc-114">Svou <xref:System.Data.Linq.DataContext> můžete dodat s vlastní databázovou transakcí, pokud vaše aplikace už transakci iniciovala a chcete, aby se do <xref:System.Data.Linq.DataContext> podílely.</span><span class="sxs-lookup"><span data-stu-id="491dc-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="491dc-115">Upřednostňovanou metodou provádění transakcí s .NET Framework je použití objektu <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="491dc-115">The preferred method of doing transactions with the .NET Framework is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="491dc-116">Pomocí tohoto přístupu můžete provádět distribuované transakce, které fungují napříč databázemi a dalšími správci prostředků rezidentů v paměti.</span><span class="sxs-lookup"><span data-stu-id="491dc-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="491dc-117">Rozsahy transakcí vyžadují, aby bylo možné spustit několik zdrojů.</span><span class="sxs-lookup"><span data-stu-id="491dc-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="491dc-118">Propagují se na distribuované transakce pouze v případě, že je v rámci oboru transakce více připojení.</span><span class="sxs-lookup"><span data-stu-id="491dc-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="491dc-119">Tento přístup nelze použít pro všechny databáze.</span><span class="sxs-lookup"><span data-stu-id="491dc-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="491dc-120">Připojení SqlClient například nemůže propagovat systémové transakce, když funguje na serveru s SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="491dc-120">For example, the SqlClient connection cannot promote system transactions when it works against a SQL Server 2000 server.</span></span> <span data-ttu-id="491dc-121">Místo toho automaticky zařadí úplnou distribuovanou transakci pokaždé, když uvidí rozsah transakce, který se používá.</span><span class="sxs-lookup"><span data-stu-id="491dc-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="491dc-122">Přímé příkazy SQL</span><span class="sxs-lookup"><span data-stu-id="491dc-122">Direct SQL Commands</span></span>  
 <span data-ttu-id="491dc-123">V době, kdy se můžete setkat s situacemi, kdy je schopnost <xref:System.Data.Linq.DataContext> dotazovat nebo odeslat změny nedostatečná pro specializovanou úlohu, kterou chcete provést.</span><span class="sxs-lookup"><span data-stu-id="491dc-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="491dc-124">V těchto případech můžete použít metodu <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> k vystavení příkazů SQL pro databázi a převést výsledky dotazu na objekty.</span><span class="sxs-lookup"><span data-stu-id="491dc-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="491dc-125">Předpokládejme například, že data pro `Customer` třídy jsou rozložena do dvou tabulek (Customer1 a Customer2).</span><span class="sxs-lookup"><span data-stu-id="491dc-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="491dc-126">Následující dotaz vrací sekvenci `Customer` objektů:</span><span class="sxs-lookup"><span data-stu-id="491dc-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="491dc-127">Pokud názvy sloupců v tabulkových výsledcích odpovídají vlastnostem sloupce vaší třídy entity, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo libovolný dotaz SQL.</span><span class="sxs-lookup"><span data-stu-id="491dc-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="491dc-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="491dc-128">Parameters</span></span>  
 <span data-ttu-id="491dc-129">Metoda <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> akceptuje parametry.</span><span class="sxs-lookup"><span data-stu-id="491dc-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="491dc-130">Následující kód provede parametrizovaný dotaz:</span><span class="sxs-lookup"><span data-stu-id="491dc-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> <span data-ttu-id="491dc-131">Parametry jsou vyjádřeny v textu dotazu pomocí stejné složené notace, kterou používá `Console.WriteLine()` a `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="491dc-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="491dc-132">`String.Format()` převezme řetězec dotazu, který zadáte, a nahradíte parametry složené závorky s generovanými názvy parametrů, jako je `@p0`, `@p1`..., `@p(n)`.</span><span class="sxs-lookup"><span data-stu-id="491dc-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491dc-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="491dc-133">See also</span></span>

- [<span data-ttu-id="491dc-134">Základní informace</span><span class="sxs-lookup"><span data-stu-id="491dc-134">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="491dc-135">Postupy: Opakované použití připojení mezi příkazem ADO.NET a položkou DataContext</span><span class="sxs-lookup"><span data-stu-id="491dc-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
