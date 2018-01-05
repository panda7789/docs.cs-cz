---
title: "Místní transakce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f7b002c1439a95929ca177aeced91164430220c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="local-transactions"></a>Místní transakce
Transakce v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] se používají, když chcete svázat více úkolů společně, aby se spustit jako na jednu jednotku práce. Představte si například, že aplikace provede dvě úlohy. Nejprve se informace o objednávce aktualizuje tabulku. Druhý aktualizuje tabulku, která obsahuje informace o inventáři, připsáním na stranu MD položky seřazené. Pokud selže buď úlohu, pak oba aktualizace jsou vrácena zpět.  
  
## <a name="determining-the-transaction-type"></a>Určení typu transakce  
 Transakce se považuje za místní transakce, když je jednofázové transakce a je zpracovává databázi přímo. Transakce se považuje za distribuovanou transakci, při monitorování transakce koordinuje a používá pohotovostního mechanismy (například dvoufázový zápis) pro rozlišení transakce.  
  
 Každý z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat má svou vlastní `Transaction` objekt pro provedení místní transakce. Pokud budete potřebovat transakce, které budou provedeny v databázi systému SQL Server, vyberte <xref:System.Data.SqlClient> transakce. Pro transakci Oracle, použijte <xref:System.Data.OracleClient> zprostředkovatele. Kromě toho je nový <xref:System.Data.Common.DbTransaction> třída, která je k dispozici pro psaní kódu nezávislé na zprostředkovatele, který vyžaduje transakce.  
  
> [!NOTE]
>  Transakce jsou nejúčinnější, když se provádí na serveru. Pokud pracujete s databází systému SQL Server, která využívá celou explicitních transakcí, vezměte v úvahu jejich zápis jako uložené procedury pomocí příkazu Transact-SQL BEGIN TRANSACTION. Další informace o provedení transakce na straně serveru najdete v části SQL Server Books Online.  
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Provádění transakcí pomocí jednoho připojení  
 V [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], řídit transakce s `Connection` objektu. Můžete spustit místní transakce s `BeginTransaction` metoda. Po zahájení transakce, můžete zařazení příkaz v této transakci s `Transaction` vlastnost `Command` objektu. Můžete pak potvrďte, nebo vrátit zpět změny provedené ve zdroji dat na základě úspěch nebo selhání součástí transakce.  
  
> [!NOTE]
>  `EnlistDistributedTransaction` – Metoda by nemělo být použito pro místní transakce.  
  
 Rozsah transakce je omezený na připojení. Následující příklad provádí explicitní transakce, který se skládá ze dvou samostatných příkazů v `try` bloku. Příkazy spusťte příkazy INSERT s tabulkou Production.ScrapReason v AdventureWorks [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] ukázkové databáze, které jsou potvrzené, pokud jsou vyvolány žádné výjimky. Kód `catch` bloku vrátí zpět transakci Pokud je vyvolána výjimka. Pokud transakce byla přerušena, nebo připojení je ukončeno před transakce byla dokončena, je automaticky vrácena zpět.  
  
## <a name="example"></a>Příklad  
 Postupujte podle těchto kroků k provedení transakce.  
  
1.  Volání <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objekt, který chcete označit zahájení transakce. <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Metoda vrátí odkaz na transakci. Tento odkaz je přiřazena k <xref:System.Data.SqlClient.SqlCommand> objekty, které jsou zařazeny v transakci.  
  
2.  Přiřazení `Transaction` do objektu <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> vlastnost <xref:System.Data.SqlClient.SqlCommand> spouštění. Pokud příkaz proveden u připojení s aktivní transakce a `Transaction` objekt nebyly přiřazeny do `Transaction` vlastnost `Command` objekt, je vyvolána výjimka.  
  
3.  Spusťte požadované příkazy.  
  
4.  Volání <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> metodu <xref:System.Data.SqlClient.SqlTransaction> objekt, který chcete dokončit transakce, nebo volejte <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metoda k ukončení transakce. Pokud je připojení ukončeno nebo zlikvidován před buď <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> nebo <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metody byly provedeny, transakce je vrácena zpět.  
  
 Následující příklad kódu ukazuje, jak pomocí transakční logiku [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] s Microsoft SQL Server.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Distribuované transakce](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 [Integrace System.Transactions s SQL Serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
