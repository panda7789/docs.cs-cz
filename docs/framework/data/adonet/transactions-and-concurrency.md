---
title: Transakce a souběžnost
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: 837fe6c42d64f7416dbd895e56a38d1a409e567a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791315"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="a79c8-102">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="a79c8-102">Transactions and Concurrency</span></span>
<span data-ttu-id="a79c8-103">Transakce se skládá z jednoho příkazu nebo skupiny příkazů, které se spouštějí jako balíček.</span><span class="sxs-lookup"><span data-stu-id="a79c8-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="a79c8-104">Transakce umožňují zkombinovat více operací do jedné pracovní jednotky.</span><span class="sxs-lookup"><span data-stu-id="a79c8-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="a79c8-105">Pokud dojde k selhání v jednom bodě transakce, všechny aktualizace mohou být vráceny zpět do jejich stavu před transakcí.</span><span class="sxs-lookup"><span data-stu-id="a79c8-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="a79c8-106">Transakce musí odpovídat vlastnostem kyseliny – nedělitelnost, konzistence, izolaci a odolnost, aby se zajistila konzistence dat.</span><span class="sxs-lookup"><span data-stu-id="a79c8-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="a79c8-107">Většina relačních databázových systémů, jako je například Microsoft SQL Server, podporuje transakce, které poskytují funkce pro správu uzamčení, protokolování a transakcí pokaždé, když klientská aplikace provede operaci aktualizace, vložení nebo odstranění.</span><span class="sxs-lookup"><span data-stu-id="a79c8-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a79c8-108">Pokud se zámky uchovávají příliš dlouho, můžou transakce, které zahrnují víc prostředků, snížit souběžnost.</span><span class="sxs-lookup"><span data-stu-id="a79c8-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="a79c8-109">Proto Udržujte transakce co nejkratší.</span><span class="sxs-lookup"><span data-stu-id="a79c8-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="a79c8-110">Pokud transakce zahrnuje více tabulek ve stejné databázi nebo serveru, pak jsou explicitní transakce v uložených procedurách často lepší.</span><span class="sxs-lookup"><span data-stu-id="a79c8-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="a79c8-111">Transakce lze vytvořit v SQL Server uložených procedurách pomocí příkazů Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`a `ROLLBACK TRANSACTION` .</span><span class="sxs-lookup"><span data-stu-id="a79c8-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="a79c8-112">Další informace najdete v tématu SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="a79c8-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="a79c8-113">Transakce týkající se různých správců prostředků, jako je například transakce mezi SQL Server a Oracle, vyžadují distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="a79c8-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a79c8-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a79c8-114">In This Section</span></span>  
 [<span data-ttu-id="a79c8-115">Místní transakce</span><span class="sxs-lookup"><span data-stu-id="a79c8-115">Local Transactions</span></span>](local-transactions.md)  
 <span data-ttu-id="a79c8-116">Ukazuje, jak provádět transakce v databázi.</span><span class="sxs-lookup"><span data-stu-id="a79c8-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="a79c8-117">Distribuované transakce</span><span class="sxs-lookup"><span data-stu-id="a79c8-117">Distributed Transactions</span></span>](distributed-transactions.md)  
 <span data-ttu-id="a79c8-118">Popisuje, jak provádět distribuované transakce v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a79c8-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="a79c8-119">Integrace System.Transactions s SQL Serverem</span><span class="sxs-lookup"><span data-stu-id="a79c8-119">System.Transactions Integration with SQL Server</span></span>](system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="a79c8-120">Popisuje <xref:System.Transactions> integraci s SQL Server pro práci s distribuovanými transakcemi.</span><span class="sxs-lookup"><span data-stu-id="a79c8-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="a79c8-121">Optimistická metoda souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="a79c8-121">Optimistic Concurrency</span></span>](optimistic-concurrency.md)  
 <span data-ttu-id="a79c8-122">Popisuje optimistickou a pesimistickou souběžnost a způsob testování pro souběhy souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="a79c8-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a79c8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a79c8-123">See also</span></span>

- [<span data-ttu-id="a79c8-124">Principy transakcí</span><span class="sxs-lookup"><span data-stu-id="a79c8-124">Transaction Fundamentals</span></span>](../transactions/transaction-fundamentals.md)
- [<span data-ttu-id="a79c8-125">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="a79c8-125">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="a79c8-126">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="a79c8-126">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="a79c8-127">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="a79c8-127">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="a79c8-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="a79c8-128">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="a79c8-129">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a79c8-129">ADO.NET Overview</span></span>](ado-net-overview.md)
