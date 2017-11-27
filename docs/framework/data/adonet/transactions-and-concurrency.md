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
  
 [System.Transactions – integrace s SQL serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 Popisuje <xref:System.Transactions> integrace s [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] pro práci s distribuované transakce.  
  
 [Optimistickou metodu souběžného zpracování](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 Popisuje pesimistické a optimistickou metodu souběžného zpracování a jak můžete otestovat pro porušení souběžnosti.  
  
## <a name="see-also"></a>Viz také  
 [Základy transakce](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapters a DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
