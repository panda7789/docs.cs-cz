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
ms.workload: dotnet
ms.openlocfilehash: 4301a232e2b38d44ecb288e76439742f7fe4d58f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transactions-and-concurrency"></a>Transakce a souběžnost
Transakce se skládá z jednoduchého příkazu nebo skupinu příkazů, které jsou spouštěny jako balíček. Transakce umožňují kombinovat více operací do jedné jednotky práce. Pokud dojde k selhání v jednom bodě v transakci, všechny aktualizace můžete vrácena zpět do stavu před transakce.  
  
 Transakce musí odpovídat vlastnosti ACID – nedělitelnost, konzistence, izolace a odolnost – Chcete-li zaručit konzistenci dat. Většina systémů relační databáze, třeba Microsoft SQL Server, podpora transakcí tím, že poskytuje zamykání, protokolování a transakce správy zařízení vždy, když klientské aplikace provede jeho aktualizaci vložit nebo operace odstranění.  
  
> [!NOTE]
>  Transakce, které zahrnují několik prostředků můžete nižší souběžnosti, pokud zámky příliš dlouhý. Proto Uchovávejte transakce co nejkratší.  
  
 Pokud transakce zahrnuje více tabulek ve stejné databázi nebo server, pak explicitních transakcí v uložené procedury často provádět lépe. Transakce v uložené procedury SQL serveru můžete vytvořit pomocí jazyka Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, a `ROLLBACK TRANSACTION` příkazy. Další informace najdete v tématu SQL Server Books Online.  
  
 Transakcí týkajících se správci různých prostředků, jako je například transakce mezi [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] a Oracle, vyžadují distribuované transakce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Místní transakce](../../../../docs/framework/data/adonet/local-transactions.md)  
 Ukazuje, jak provádět transakce proti databázi.  
  
 [Distribuované transakce](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 Popisuje, jak provádět distribuovaných transakcí v ADO.NET.  
  
 [Integrace System.Transactions s SQL Serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 Popisuje <xref:System.Transactions> integrace s [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] pro práci s distribuované transakce.  
  
 [Optimistická metoda souběžného zpracování](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 Popisuje pesimistické a optimistickou metodu souběžného zpracování a jak můžete otestovat pro porušení souběžnosti.  
  
## <a name="see-also"></a>Viz také  
 [Principy transakcí](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
