---
title: Transakce a souběžnost
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: bd47c5e0e2b2086e5fd0482bf4319ebab5674a54
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777450"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="a2c11-102">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="a2c11-102">Transactions and Concurrency</span></span>
<span data-ttu-id="a2c11-103">Transakce se skládá z jediného příkazu nebo skupině příkazů, které jsou spouštěny jako balíček.</span><span class="sxs-lookup"><span data-stu-id="a2c11-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="a2c11-104">Transakce umožňují kombinovat více operací do jedné jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="a2c11-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="a2c11-105">V případě selhání v jednom bodě v transakci všechny aktualizace může být vrácena zpět do stavu před transakce.</span><span class="sxs-lookup"><span data-stu-id="a2c11-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="a2c11-106">Transakce musí odpovídat vlastnosti ACID – atomicitu, konzistence, izolace a odolnost – kvůli zaručení konzistence dat.</span><span class="sxs-lookup"><span data-stu-id="a2c11-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="a2c11-107">Většina relačních databází systémů, jako je například Microsoft SQL Server, podpora transakcí tím, že poskytuje protokolování a možnosti správy transakce uzamčení pokaždé, když klientská aplikace provede jeho aktualizaci vložení nebo odstranění operace.</span><span class="sxs-lookup"><span data-stu-id="a2c11-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2c11-108">Transakcí, které se týkají více zdrojů může snížit souběžnost, pokud zámky příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="a2c11-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="a2c11-109">Proto se zachovejte transakce co nejkratší.</span><span class="sxs-lookup"><span data-stu-id="a2c11-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="a2c11-110">Pokud transakce zahrnuje více tabulek ve stejném databáze nebo serveru, pak explicitní transakce v uložených procedurách často provádějí lépe.</span><span class="sxs-lookup"><span data-stu-id="a2c11-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="a2c11-111">Transakce v uložených procedur SQL serveru můžete vytvořit pomocí jazyka Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, a `ROLLBACK TRANSACTION` příkazy.</span><span class="sxs-lookup"><span data-stu-id="a2c11-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="a2c11-112">Další informace najdete v tématu knihy Online SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a2c11-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="a2c11-113">Transakce zahrnující správci různých prostředků, jako je například transakce mezi SQL Server a Oracle, vyžadují distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="a2c11-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2c11-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a2c11-114">In This Section</span></span>  
 [<span data-ttu-id="a2c11-115">Místní transakce</span><span class="sxs-lookup"><span data-stu-id="a2c11-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="a2c11-116">Ukazuje, jak provádět transakce proti databázi.</span><span class="sxs-lookup"><span data-stu-id="a2c11-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="a2c11-117">Distribuované transakce</span><span class="sxs-lookup"><span data-stu-id="a2c11-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="a2c11-118">Popisuje, jak provést distribuované transakce v rozhraní ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a2c11-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="a2c11-119">Integrace System.Transactions s SQL Serverem</span><span class="sxs-lookup"><span data-stu-id="a2c11-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="a2c11-120">Popisuje <xref:System.Transactions> integraci se systémem SQL Server pro práci s distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="a2c11-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="a2c11-121">Optimistická metoda souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="a2c11-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="a2c11-122">Popisuje optimistické a Pesimistická souběžnost a jak otestovat pro porušení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="a2c11-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c11-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2c11-123">See Also</span></span>  
 [<span data-ttu-id="a2c11-124">Principy transakcí</span><span class="sxs-lookup"><span data-stu-id="a2c11-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [<span data-ttu-id="a2c11-125">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="a2c11-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="a2c11-126">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="a2c11-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="a2c11-127">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="a2c11-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="a2c11-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="a2c11-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="a2c11-129">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a2c11-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
