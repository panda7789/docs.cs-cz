---
title: ADO.NET a technologie LINQ to SQL
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
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97cf55419c6e13a497264bcbaa3a546eac37f982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="89b03-102">ADO.NET a technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="89b03-102">ADO.NET and LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="89b03-103">je součástí [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodiny technologií.</span><span class="sxs-lookup"><span data-stu-id="89b03-103"> is part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies.</span></span> <span data-ttu-id="89b03-104">Je založena na služeb poskytovaných [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] zprostředkovatele modelu.</span><span class="sxs-lookup"><span data-stu-id="89b03-104">It is based on services provided by the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] provider model.</span></span> <span data-ttu-id="89b03-105">Proto je možné kombinovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kód s existujícím [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] aplikace a migrovat aktuální [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] řešení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89b03-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] applications and migrate current [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="89b03-106">Následující obrázek poskytuje podrobný pohled relace.</span><span class="sxs-lookup"><span data-stu-id="89b03-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="89b03-107">![Technologie LINQ to SQL a ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="89b03-107">![LINQ to SQL and ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="89b03-108">Připojení</span><span class="sxs-lookup"><span data-stu-id="89b03-108">Connections</span></span>  
 <span data-ttu-id="89b03-109">Můžete zadat existující [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] připojení při vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="89b03-109">You can supply an existing [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="89b03-110">Všechny operace proti <xref:System.Data.Linq.DataContext> (včetně dotazů) použít zadané připojení.</span><span class="sxs-lookup"><span data-stu-id="89b03-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="89b03-111">Pokud připojení je již otevřeno, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ponechá ji jako je po dokončení s ním.</span><span class="sxs-lookup"><span data-stu-id="89b03-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="89b03-112">Kdykoli můžete získat přístup k připojení a zavřete ho sami pomocí <xref:System.Data.Linq.DataContext.Connection%2A> vlastnosti, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="89b03-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="89b03-113">Transakce</span><span class="sxs-lookup"><span data-stu-id="89b03-113">Transactions</span></span>  
 <span data-ttu-id="89b03-114">Můžete zadat vaše <xref:System.Data.Linq.DataContext> s vlastní transakcí databáze, když vaše aplikace již inicioval transakce a chcete, aby vaše <xref:System.Data.Linq.DataContext> zabývajících.</span><span class="sxs-lookup"><span data-stu-id="89b03-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="89b03-115">Upřednostňovaný způsob provádění transakcí pomocí [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] , je použít <xref:System.Transactions.TransactionScope> objektu.</span><span class="sxs-lookup"><span data-stu-id="89b03-115">The preferred method of doing transactions with the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="89b03-116">Když použijete tuto metodu, můžete provést distribuované transakce, které pracují mezi databází a jiným správcům rezidentní prostředků.</span><span class="sxs-lookup"><span data-stu-id="89b03-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="89b03-117">Transakce obory vyžadovat několik prostředků ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="89b03-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="89b03-118">Jejich povýšení sami na distribuovaných transakcí jenom v případě, že je víc připojení v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="89b03-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="89b03-119">Tuto metodu nelze použít pro všechny databáze.</span><span class="sxs-lookup"><span data-stu-id="89b03-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="89b03-120">Například SqlClient připojení se nedá povýšit transakcí systému při funguje proti [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] serveru.</span><span class="sxs-lookup"><span data-stu-id="89b03-120">For example, the SqlClient connection cannot promote system transactions when it works against a [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] server.</span></span> <span data-ttu-id="89b03-121">Místo toho je automaticky zapsán úplné a distribuované transakce vždy, když je detekována oboru transakce používá.</span><span class="sxs-lookup"><span data-stu-id="89b03-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="89b03-122">Přímé SQL příkazy</span><span class="sxs-lookup"><span data-stu-id="89b03-122">Direct SQL Commands</span></span>  
 <span data-ttu-id="89b03-123">V některých případech se můžete setkat situacích kde schopnost <xref:System.Data.Linq.DataContext> dotazu nebo odeslání změn je nedostatečná pro speciální úlohu, kterou chcete provést.</span><span class="sxs-lookup"><span data-stu-id="89b03-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="89b03-124">V těchto případech můžete použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metoda vydávat příkazy SQL databázi a převedeno na objekty výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="89b03-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="89b03-125">Například předpokládejme, že data `Customer` třída je rozdělena ve dvou tabulek (customer1 a customer2).</span><span class="sxs-lookup"><span data-stu-id="89b03-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="89b03-126">Následující dotaz vrátí posloupnost `Customer` objekty:</span><span class="sxs-lookup"><span data-stu-id="89b03-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="89b03-127">Tak dlouho, dokud shodovat s názvy sloupců v tabulkové výsledky sloupce vlastnosti třídy entity [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří vašich objektů mimo jakýkoli dotaz SQL.</span><span class="sxs-lookup"><span data-stu-id="89b03-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="89b03-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="89b03-128">Parameters</span></span>  
 <span data-ttu-id="89b03-129"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda přijímá parametry.</span><span class="sxs-lookup"><span data-stu-id="89b03-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="89b03-130">Následující kód spustí parametrizovaného dotazu:</span><span class="sxs-lookup"><span data-stu-id="89b03-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  <span data-ttu-id="89b03-131">Parametry jsou vyjádřeny v textu dotazu pomocí stejné složené zápisu používané `Console.WriteLine()` a `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="89b03-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="89b03-132">`String.Format()`přebírá řetězec dotazu zadejte a nahradí složené braced parametry s generované názvy parametrů jako `@p0`, `@p1` ..., `@p(n)`.</span><span class="sxs-lookup"><span data-stu-id="89b03-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b03-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="89b03-133">See Also</span></span>  
 [<span data-ttu-id="89b03-134">Základní informace</span><span class="sxs-lookup"><span data-stu-id="89b03-134">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="89b03-135">Postupy: opakované použití připojení mezi příkaz ADO.NET a DataContext</span><span class="sxs-lookup"><span data-stu-id="89b03-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
