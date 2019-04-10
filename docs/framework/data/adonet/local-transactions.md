---
title: Místní transakce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: e139cafa168b0a6851e5d8474e6bb4db94f36e9a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339148"
---
# <a name="local-transactions"></a>Místní transakce
Transakce v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] se používají, když chcete vazby společně více úloh, takže se provést jako jednu jednotku práce. Představte si například, že aplikace provede dvě úlohy. Nejprve aktualizuje tabulku s informacemi o pořadí. Za druhé aktualizuje tabulku, která obsahuje informace o inventáři, připsáním na stranu MD položky seřazeny. Pokud buď úloha selže, pak obě aktualizace jsou vrácena zpět.  
  
## <a name="determining-the-transaction-type"></a>Určení typu transakce  
 Transakce se považuje za místní transakce, když je jednofázové transakce a zpracovává přímo v databázi. Transakce se považuje za distribuovanou transakci, když koordinuje přes monitorování transakce a používá pro rozlišení transakce odolný proti selhání mechanismy (například dvoufázového potvrzení).  
  
 Každá z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat má vlastní `Transaction` objekt pro provedení místní transakce. Pokud budete potřebovat transakce provést v databázi serveru SQL Server, vyberte <xref:System.Data.SqlClient> transakce. Transakci Oracle používat <xref:System.Data.OracleClient> zprostředkovatele. Kromě toho existuje <xref:System.Data.Common.DbTransaction> třídu, která je k dispozici pro psaní kódu nezávislé na zprostředkovatele, které vyžadují určitý počet transakcí.  
  
> [!NOTE]
> Transakce jsou nejúčinnější, když se provádí na serveru. Při práci s databází serveru SQL Server, který se příliš často používá explicitní transakce, zvažte vytvoření jako uložené procedury pomocí příkazu jazyka Transact-SQL BEGIN TRANSACTION.
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Provádění transakcí pomocí jednoho připojení  
 V [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], řídit transakce se `Connection` objektu. Můžete spustit místní transakce s `BeginTransaction` metody. Po zahájení transakce, může zařazení v transakci pomocí příkazu `Transaction` vlastnost `Command` objektu. Můžete pak potvrzení nebo vrátit zpět změny provedené ve zdroji dat na základě úspěchu nebo selhání součástí transakce.  
  
> [!NOTE]
>  `EnlistDistributedTransaction` Metoda by neměla používat pro místní transakce.  
  
 Rozsah transakce je omezen na připojení. Následující příklad provádí, který se skládá ze dvou samostatných příkazů v explicitní transakci `try` bloku. Příkazy spustit příkazy INSERT s tabulkou Production.ScrapReason v ukázkové databázi AdventureWorks SQL serveru, které se potvrdí, pokud nejsou vyvolány žádné výjimky. Kód v `catch` bloku vrátí zpět transakce Pokud dojde k výjimce. Pokud transakce je přerušena nebo připojení je ukončené před dokončením transakce, to se automaticky vrátí zpět.  
  
## <a name="example"></a>Příklad  
 Použijte následující postup provedení transakce.  
  
1. Volání <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objektu k označení zahájení transakce. <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Metoda vrátí odkaz na transakci. Je přiřazen tento odkaz <xref:System.Data.SqlClient.SqlCommand> objekty, které jsou v transakci zapsán.  
  
2. Přiřazení `Transaction` objektu <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> vlastnost <xref:System.Data.SqlClient.SqlCommand> má být proveden. Pokud příkaz se provedl u připojení s aktivní transakce a `Transaction` nebyl přiřazen objekt `Transaction` vlastnost `Command` objektu, je vyvolána výjimka.  
  
3. Spusťte požadované příkazy.  
  
4. Volání <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> metodu <xref:System.Data.SqlClient.SqlTransaction> objekt dala dokončit transakce, nebo volání <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metoda k ukončení transakce. Pokud je připojení ukončen nebo odstraněn před buď <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> nebo <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metody spustily, transakce se zrušila.  
  
 Následující příklad kódu ukazuje použití transakční logiky [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] s Microsoft SQL Server.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [Distribuované transakce](../../../../docs/framework/data/adonet/distributed-transactions.md)
- [Integrace System.Transactions s SQL Serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
