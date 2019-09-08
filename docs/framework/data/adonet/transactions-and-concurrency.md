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
# <a name="transactions-and-concurrency"></a>Transakce a souběžnost
Transakce se skládá z jednoho příkazu nebo skupiny příkazů, které se spouštějí jako balíček. Transakce umožňují zkombinovat více operací do jedné pracovní jednotky. Pokud dojde k selhání v jednom bodě transakce, všechny aktualizace mohou být vráceny zpět do jejich stavu před transakcí.  
  
 Transakce musí odpovídat vlastnostem kyseliny – nedělitelnost, konzistence, izolaci a odolnost, aby se zajistila konzistence dat. Většina relačních databázových systémů, jako je například Microsoft SQL Server, podporuje transakce, které poskytují funkce pro správu uzamčení, protokolování a transakcí pokaždé, když klientská aplikace provede operaci aktualizace, vložení nebo odstranění.  
  
> [!NOTE]
> Pokud se zámky uchovávají příliš dlouho, můžou transakce, které zahrnují víc prostředků, snížit souběžnost. Proto Udržujte transakce co nejkratší.  
  
 Pokud transakce zahrnuje více tabulek ve stejné databázi nebo serveru, pak jsou explicitní transakce v uložených procedurách často lepší. Transakce lze vytvořit v SQL Server uložených procedurách pomocí příkazů Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`a `ROLLBACK TRANSACTION` . Další informace najdete v tématu SQL Server Knihy online.  
  
 Transakce týkající se různých správců prostředků, jako je například transakce mezi SQL Server a Oracle, vyžadují distribuovanou transakci.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Místní transakce](local-transactions.md)  
 Ukazuje, jak provádět transakce v databázi.  
  
 [Distribuované transakce](distributed-transactions.md)  
 Popisuje, jak provádět distribuované transakce v ADO.NET.  
  
 [Integrace System.Transactions s SQL Serverem](system-transactions-integration-with-sql-server.md)  
 Popisuje <xref:System.Transactions> integraci s SQL Server pro práci s distribuovanými transakcemi.  
  
 [Optimistická metoda souběžného zpracování](optimistic-concurrency.md)  
 Popisuje optimistickou a pesimistickou souběžnost a způsob testování pro souběhy souběžnosti.  
  
## <a name="see-also"></a>Viz také:

- [Principy transakcí](../transactions/transaction-fundamentals.md)
- [Připojení ke zdroji dat](connecting-to-a-data-source.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [DbProviderFactories](dbproviderfactories.md)
- [Přehled ADO.NET](ado-net-overview.md)
