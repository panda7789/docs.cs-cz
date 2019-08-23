---
title: Místní transakce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: a0cb72913c10712ece188a782095b93f98cdc0b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955775"
---
# <a name="local-transactions"></a>Místní transakce
Transakce v ADO.NET se používají, když chcete propojit více úkolů dohromady, aby byly spouštěny jako jediná jednotka práce. Představte si například, že aplikace provede dvě úlohy. Nejprve aktualizuje tabulku s informacemi o objednávkách. Za druhé se aktualizuje tabulka, která obsahuje informace o inventáři, která má dáti objednaného zboží. Pokud se některá z těchto úloh nezdařila, vrátí se obě aktualizace zpátky.  
  
## <a name="determining-the-transaction-type"></a>Určení typu transakce  
 Transakce je považována za místní transakci, pokud se jedná o transakci s jednou fází a je zpracovávána přímo v databázi. Transakce je považována za distribuovanou transakci, pokud je koordinována monitorováním transakce a používá mechanismy odolné proti selhání (například dvoufázové potvrzení) pro rozlišení transakce.  
  
 Každé poskytovatelé dat .NET Framework má vlastní `Transaction` objekt pro provádění místních transakcí. Pokud vyžadujete, aby transakce byla provedena v SQL Server databázi, vyberte <xref:System.Data.SqlClient> transakci. Pro transakci Oracle použijte <xref:System.Data.OracleClient> poskytovatele. Kromě toho existuje <xref:System.Data.Common.DbTransaction> třída, která je k dispozici pro psaní kódu nezávislého na poskytovateli, který vyžaduje transakce.  
  
> [!NOTE]
> Transakce jsou nejúčinnější při jejich provádění na serveru. Pokud pracujete s SQL Server databází, která poskytuje rozsáhlé použití explicitních transakcí, zvažte jejich zápis jako uložené procedury pomocí příkazu jazyka Transact-SQL BEGIN TRANSACTION.
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Provádění transakcí pomocí jednoho připojení  
 V ADO.NET můžete řídit transakce s `Connection` objektem. Můžete iniciovat místní transakci pomocí `BeginTransaction` metody. Po zahájení transakce můžete zařadit příkaz do transakce s `Transaction` vlastností `Command` objektu. Pak můžete potvrdit nebo vrátit zpět změny provedené ve zdroji dat na základě úspěchu nebo neúspěchu součástí transakce.  
  
> [!NOTE]
> `EnlistDistributedTransaction` Metoda by neměla být použita pro místní transakci.  
  
 Rozsah transakce je omezen na připojení. Následující příklad provádí explicitní transakci, která se skládá ze dvou samostatných příkazů v `try` bloku. Příkazy spouštějí příkazy INSERT v tabulce produkčního. ScrapReason ve vzorové databázi AdventureWorks SQL Server, které jsou potvrzeny, pokud nejsou vyvolány žádné výjimky. Kód v `catch` bloku vrátí zpět transakci, pokud je vyvolána výjimka. Pokud je transakce přerušena nebo je připojení ukončeno před dokončením transakce, bude automaticky vrácena zpět.  
  
## <a name="example"></a>Příklad  
 K provedení transakce použijte následující postup.  
  
1. <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Zavolejte metodu <xref:System.Data.SqlClient.SqlConnection> objektu pro označení začátku transakce. <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Metoda vrátí odkaz na transakci. Tento odkaz je přiřazen k <xref:System.Data.SqlClient.SqlCommand> objektům, které jsou zapsány v transakci.  
  
2. Přiřaďte <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> <xref:System.Data.SqlClient.SqlCommand> objekt k vlastnosti, která má být provedena. `Transaction` Pokud je příkaz proveden v připojení s aktivní transakcí a `Transaction` objekt nebyl přiřazen `Transaction` k vlastnosti `Command` objektu, je vyvolána výjimka.  
  
3. Spusťte požadované příkazy.  
  
4. Voláním <xref:System.Data.SqlClient.SqlTransaction> <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metody objektu Dokončete transakci nebo zavolejte metodu pro ukončení transakce. <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> Pokud je připojení ukončeno nebo odstraněno před provedením <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> těchto <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metod nebo, transakce je vrácena zpět.  
  
 Následující příklad kódu ukazuje transakční logiku s použitím ADO.NET s Microsoft SQL Server.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [Distribuované transakce](../../../../docs/framework/data/adonet/distributed-transactions.md)
- [Integrace System.Transactions s SQL Serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
