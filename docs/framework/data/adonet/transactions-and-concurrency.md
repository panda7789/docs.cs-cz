---
title: Transakce a souběžnost
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: ba857031a54374ee295c2bfd724e7fb8651b7c1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933702"
---
# <a name="transactions-and-concurrency"></a>Transakce a souběžnost
Transakce se skládá z jediného příkazu nebo skupině příkazů, které jsou spouštěny jako balíček. Transakce umožňují kombinovat více operací do jedné jednotky práce. V případě selhání v jednom bodě v transakci všechny aktualizace může být vrácena zpět do stavu před transakce.  
  
 Transakce musí odpovídat vlastnosti ACID – atomicitu, konzistence, izolace a odolnost – kvůli zaručení konzistence dat. Většina relačních databází systémů, jako je například Microsoft SQL Server, podpora transakcí tím, že poskytuje protokolování a možnosti správy transakce uzamčení pokaždé, když klientská aplikace provede jeho aktualizaci vložení nebo odstranění operace.  
  
> [!NOTE]
>  Transakcí, které se týkají více zdrojů může snížit souběžnost, pokud zámky příliš dlouhý. Proto se zachovejte transakce co nejkratší.  
  
 Pokud transakce zahrnuje více tabulek ve stejném databáze nebo serveru, pak explicitní transakce v uložených procedurách často provádějí lépe. Transakce v uložených procedur SQL serveru můžete vytvořit pomocí jazyka Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, a `ROLLBACK TRANSACTION` příkazy. Další informace najdete v tématu knihy Online SQL Server.  
  
 Transakce zahrnující správci různých prostředků, jako je například transakce mezi SQL Server a Oracle, vyžadují distribuovanou transakci.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Místní transakce](../../../../docs/framework/data/adonet/local-transactions.md)  
 Ukazuje, jak provádět transakce proti databázi.  
  
 [Distribuované transakce](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 Popisuje, jak provést distribuované transakce v rozhraní ADO.NET.  
  
 [Integrace System.Transactions s SQL Serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 Popisuje <xref:System.Transactions> integraci se systémem SQL Server pro práci s distribuované transakce.  
  
 [Optimistická metoda souběžného zpracování](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 Popisuje optimistické a Pesimistická souběžnost a jak otestovat pro porušení souběžnosti.  
  
## <a name="see-also"></a>Viz také:

- [Principy transakcí](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
