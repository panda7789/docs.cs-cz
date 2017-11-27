---
title: "Transakce a souběžnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4e06f54ed27a555daa30f16f452cd03c8e188a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="1afff-102">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="1afff-102">Transactions and Concurrency</span></span>
<span data-ttu-id="1afff-103">Transakce se skládá z jednoduchého příkazu nebo skupinu příkazů, které jsou spouštěny jako balíček.</span><span class="sxs-lookup"><span data-stu-id="1afff-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="1afff-104">Transakce umožňují kombinovat více operací do jedné jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="1afff-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="1afff-105">Pokud dojde k selhání v jednom bodě v transakci, všechny aktualizace můžete vrácena zpět do stavu před transakce.</span><span class="sxs-lookup"><span data-stu-id="1afff-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="1afff-106">Transakce musí odpovídat vlastnosti ACID – nedělitelnost, konzistence, izolace a odolnost – Chcete-li zaručit konzistenci dat.</span><span class="sxs-lookup"><span data-stu-id="1afff-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="1afff-107">Většina systémů relační databáze, třeba Microsoft SQL Server, podpora transakcí tím, že poskytuje zamykání, protokolování a transakce správy zařízení vždy, když klientské aplikace provede jeho aktualizaci vložit nebo operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="1afff-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1afff-108">Transakce, které zahrnují několik prostředků můžete nižší souběžnosti, pokud zámky příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="1afff-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="1afff-109">Proto Uchovávejte transakce co nejkratší.</span><span class="sxs-lookup"><span data-stu-id="1afff-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="1afff-110">Pokud transakce zahrnuje více tabulek ve stejné databázi nebo server, pak explicitních transakcí v uložené procedury často provádět lépe.</span><span class="sxs-lookup"><span data-stu-id="1afff-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="1afff-111">Transakce v uložené procedury SQL serveru můžete vytvořit pomocí jazyka Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, a `ROLLBACK TRANSACTION` příkazy.</span><span class="sxs-lookup"><span data-stu-id="1afff-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="1afff-112">Další informace najdete v tématu SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="1afff-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="1afff-113">Transakcí týkajících se správci různých prostředků, jako je například transakce mezi [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] a Oracle, vyžadují distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="1afff-113">Transactions involving different resource managers, such as a transaction between [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1afff-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1afff-114">In This Section</span></span>  
 [<span data-ttu-id="1afff-115">Místní transakce</span><span class="sxs-lookup"><span data-stu-id="1afff-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="1afff-116">Ukazuje, jak provádět transakce proti databázi.</span><span class="sxs-lookup"><span data-stu-id="1afff-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="1afff-117">Distribuované transakce</span><span class="sxs-lookup"><span data-stu-id="1afff-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="1afff-118">Popisuje, jak provádět distribuovaných transakcí v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1afff-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="1afff-119">System.Transactions – integrace s SQL serverem</span><span class="sxs-lookup"><span data-stu-id="1afff-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="1afff-120">Popisuje <xref:System.Transactions> integrace s [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] pro práci s distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="1afff-120">Describes <xref:System.Transactions> integration with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="1afff-121">Optimistickou metodu souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="1afff-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="1afff-122">Popisuje pesimistické a optimistickou metodu souběžného zpracování a jak můžete otestovat pro porušení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="1afff-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1afff-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1afff-123">See Also</span></span>  
 [<span data-ttu-id="1afff-124">Základy transakce</span><span class="sxs-lookup"><span data-stu-id="1afff-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [<span data-ttu-id="1afff-125">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="1afff-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="1afff-126">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="1afff-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="1afff-127">DataAdapters a DataReaders</span><span class="sxs-lookup"><span data-stu-id="1afff-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="1afff-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="1afff-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="1afff-129">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="1afff-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
