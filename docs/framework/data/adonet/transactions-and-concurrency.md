---
title: Transakce a souběžnost
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: c78031150d9b1209372dece49813dfcf0a03b9d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965215"
---
# <a name="transactions-and-concurrency"></a>Transakce a souběžnost
Transakce se skládá z jednoho příkazu nebo skupiny příkazů, které se spouštějí jako balíček. Transakce umožňují zkombinovat více operací do jedné pracovní jednotky. Pokud dojde k selhání v jednom bodě transakce, všechny aktualizace mohou být vráceny zpět do jejich stavu před transakcí.  
  
 Transakce musí odpovídat vlastnostem kyseliny – nedělitelnost, konzistence, izolaci a odolnost, aby se zajistila konzistence dat. Většina relačních databázových systémů, jako je například Microsoft SQL Server, podporuje transakce, které poskytují funkce pro správu uzamčení, protokolování a transakcí pokaždé, když klientská aplikace provede operaci aktualizace, vložení nebo odstranění.  
  
> [!NOTE]
> Pokud se zámky uchovávají příliš dlouho, můžou transakce, které zahrnují víc prostředků, snížit souběžnost. Proto Udržujte transakce co nejkratší.  
  
 Pokud transakce zahrnuje více tabulek ve stejné databázi nebo serveru, pak jsou explicitní transakce v uložených procedurách často lepší. Transakce lze vytvořit v SQL Server uložených procedurách pomocí příkazů Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`a `ROLLBACK TRANSACTION` . Další informace najdete v tématu SQL Server Knihy online.  
  
 Transakce týkající se různých správců prostředků, jako je například transakce mezi SQL Server a Oracle, vyžadují distribuovanou transakci.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Místní transakce](../../../../docs/framework/data/adonet/local-transactions.md)  
 Ukazuje, jak provádět transakce v databázi.  
  
 [Distribuované transakce](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 Popisuje, jak provádět distribuované transakce v ADO.NET.  
  
 [Integrace System.Transactions s SQL Serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 Popisuje <xref:System.Transactions> integraci s SQL Server pro práci s distribuovanými transakcemi.  
  
 [Optimistická metoda souběžného zpracování](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 Popisuje optimistickou a pesimistickou souběžnost a způsob testování pro souběhy souběžnosti.  
  
## <a name="see-also"></a>Viz také:

- [Principy transakcí](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
