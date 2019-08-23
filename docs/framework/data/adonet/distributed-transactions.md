---
title: Distribuované transakce
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: f5ed99928534dc31832ac0baf1bb1bfa7e83ded2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956757"
---
# <a name="distributed-transactions"></a>Distribuované transakce
Transakce je sada souvisejících úloh, které jsou buď úspěšné (potvrzení) nebo neúspěšné (přerušení) jako jednotka mimo jiné. *Distribuovaná transakce* je transakce, která má vliv na několik prostředků. Aby bylo možné odeslat distribuovanou transakci, všichni účastníci musí zaručit, že jakákoli změna dat bude trvalá. Změny musíte zachovat navzdory zhroucení systému nebo jiné nepředvídatelné události. Pokud ani jeden účastník tuto záruku nepovede, celá transakce se nezdařila a všechny změny dat v rámci oboru transakce se vrátí zpět.  
  
> [!NOTE]
> Výjimka bude vyvolána, pokud se pokusíte transakci potvrdit nebo vrátit zpět, pokud `DataReader` je spuštěna v době, kdy je transakce aktivní.  
  
## <a name="working-with-systemtransactions"></a>Práce s System. Transactions  
 V .NET Framework jsou distribuované transakce spravovány prostřednictvím rozhraní API v <xref:System.Transactions> oboru názvů. <xref:System.Transactions> Rozhraní API bude delegovat zpracování distribuovaných transakcí na monitorování transakcí, jako je například služba Microsoft DTC (Distributed Transaction Coordinator) (MS DTC), když se účastní více správců trvalého prostředku. Další informace najdete v tématu [základy transakcí](../../../../docs/framework/data/transactions/transaction-fundamentals.md).  
  
 ADO.NET 2,0 představil podporu pro zařazení do distribuované transakce pomocí `EnlistTransaction` metody, která zařadí připojení <xref:System.Transactions.Transaction> v instanci. V předchozích verzích ADO.NET bylo provedeno explicitní zařazení v distribuovaných transakcích pomocí `EnlistDistributedTransaction` metody připojení k zařazení připojení <xref:System.EnterpriseServices.ITransaction> do instance, které je podporováno pro zpětnou kompatibilitu. Další informace o transakcích služby Enterprise Services najdete v tématu [interoperabilita se službami Enterprise a transakcí modelu COM+](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 Při použití <xref:System.Transactions> transakce se zprostředkovatelem .NET Framework pro SQL Server proti databázi SQL Server se automaticky použije odlehčený <xref:System.Transactions.Transaction> . Transakce se pak dá zvýšit na úplnou distribuovanou transakci podle potřeby. Další informace najdete v tématu [integrace System. Transactions s SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
> Maximální počet distribuovaných transakcí, ve kterých se může databáze Oracle účastnit, je ve výchozím nastavení nastaven na hodnotu 10. Po desáté transakci, která je připojena k databázi Oracle, je vyvolána výjimka. Oracle nepodporuje `DDL` v distribuované transakci.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Automatické zařazení do distribuované transakce  
 Automatické zařazení je výchozí (a upřednostňovaný) způsob integrace připojení ADO.NET s `System.Transactions`. Objekt připojení bude automaticky zařazen do existující distribuované transakce, pokud zjistí, že je transakce aktivní, což `System.Transaction` znamená, že `Transaction.Current` je hodnota null. Automatický zařazení transakce probíhá při otevření připojení. Neproběhne ani v případě, že je proveden příkaz v rámci oboru transakce. Automatické zařazení `Enlist=false` v existujících transakcích můžete zakázat zadáním parametru jako připojovací řetězec <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>pro nebo `OLE DB Services=-7` jako parametru připojovacího řetězce pro <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>. Další informace o parametrech připojovacího řetězce Oracle a ODBC naleznete <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> v <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>tématech a.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>Ruční zařazení do distribuované transakce  
 Pokud je automatické zařazení zakázané nebo potřebujete uvést transakci, která byla zahájena po otevření připojení, můžete zařadit do existující distribuované transakce pomocí `EnlistTransaction` metody <xref:System.Data.Common.DbConnection> objektu pro poskytovatele, kterého pracujete. řetězce. Zařazení do existující distribuované transakce zajišťuje, že pokud je transakce potvrzena nebo vrácena zpět, změny provedené kódem ve zdroji dat budou potvrzeny nebo vráceny i zpět.  
  
 Zařazení do distribuovaných transakcí je zvlášť použitelné při sdružování obchodních objektů. Pokud je obchodní objekt sdružený s otevřeným připojením, při otevření připojení dojde k automatickému zařazení transakce. Pokud se s využitím podnikového objektu spolupracuje s více transakcemi, otevře se připojení pro tento objekt automaticky v nově iniciované transakci. V takovém případě můžete zakázat automatické zařazení transakce pro připojení a zařadit připojení v transakcích pomocí `EnlistTransaction`.  
  
 `EnlistTransaction`přijímá jeden argument typu <xref:System.Transactions.Transaction> , který je odkazem na existující transakci. Po volání `EnlistTransaction` metody připojení budou všechny změny provedené ve zdroji dat pomocí připojení zahrnuty v transakci. Předáním hodnoty null se odřadí připojení od aktuálního zařazení distribuované transakce. Všimněte si, že před voláním `EnlistTransaction`je třeba otevřít připojení.  
  
> [!NOTE]
> Jakmile je připojení explicitně zařazeno na transakci, nemůže být Nezařazeno nebo zařazeno do jiné transakce, dokud nebude dokončena první transakce.  
  
> [!CAUTION]
>  `EnlistTransaction`vyvolá výjimku, pokud připojení již zahájilo transakci pomocí <xref:System.Data.Common.DbConnection.BeginTransaction%2A> metody připojení. Pokud je však transakce místní transakce zahájena ve zdroji dat (například provedení příkazu BEGIN TRANSACTION explicitně pomocí a <xref:System.Data.SqlClient.SqlCommand>), `EnlistTransaction` vrátí místní transakci a zařadí se do existující distribuované transakce podle požadavku. Nebudete dostávat informace o tom, že místní transakce byla vrácena zpět a musí spravovat všechny místní transakce, které nebyly <xref:System.Data.Common.DbConnection.BeginTransaction%2A>spuštěny pomocí. Pokud používáte zprostředkovatel dat .NET Framework pro SQL Server (`SqlClient`) se SQL Server, pokus o zařazení vyvolá výjimku. Všechny ostatní případy se přestanou zjišťovat.  
  
## <a name="promotable-transactions-in-sql-server"></a>Transakce s propagačními operacemi v SQL Server  
 SQL Server podporuje transakce typu promoce, ve kterých lze místní odlehčenou transakci automaticky zvýšit na distribuovanou transakci pouze v případě, že je požadována. Transakce promoící nevyvolává přidanou režii distribuované transakce, pokud není nutná přidaná režie. Další informace a ukázku kódu naleznete v tématu [integrace System. Transactions with SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Konfigurace distribuovaných transakcí  
 Aby bylo možné používat distribuované transakce, možná budete muset povolit koordinátor MS DTC přes síť. Pokud má brána Windows Firewall povolená, musíte službě MS DTC povolit, aby používala síť, nebo otevřít port MS DTC.  
  
## <a name="see-also"></a>Viz také:

- [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [Integrace System.Transactions s SQL Serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
