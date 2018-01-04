---
title: "Distribuované transakce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6bc9a754325f7d01ee36622a23efde1cbc7c4812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="distributed-transactions"></a>Distribuované transakce
Transakce je sada souvisejících úloh, které buď (Potvrdit) úspěšná nebo neúspěšná (přerušení) jako jednotku, mimo jiné. A *distribuované transakce* je transakci, která ovlivňuje několik prostředků. Pro distribuované transakce potvrzení musí všechny účastníky zaručit, že všechny změny dat bude trvalé. Změny musíte zachovat navzdory zhroucení systému nebo jiné nepředvídatelné události. Pokud jeden účastník neprovede tento záruka, selže celá transakce a všechny změny dat v rámci oboru transakce jsou vráceny zpět.  
  
> [!NOTE]
>  Bude vyvolána výjimka, pokud se pokusíte potvrzení nebo vrácení transakce, pokud `DataReader` je zahájen, když je aktivní transakce.  
  
## <a name="working-with-systemtransactions"></a>Práce s System.Transactions –  
 V rozhraní .NET Framework, distribuované transakce se spravují přes rozhraní API v <xref:System.Transactions> oboru názvů. <xref:System.Transactions> Rozhraní API budou delegovat to zpracování monitorování transakce, jako je například Microsoft Distributed Transaction Coordinator (MS DTC) při více správců prostředků trvalé se účastní distribuované transakce. Další informace najdete v tématu [transakce Základy](../../../../docs/framework/data/transactions/transaction-fundamentals.md).  
  
 ADO.NET 2.0 zavedly podporu pro zapsání v distribuované transakce pomocí `EnlistTransaction` metodu, která využívá připojení v <xref:System.Transactions.Transaction> instance. V předchozích verzích technologie ADO.NET, se provádí pomocí explicitní zařazení v distribuovaných transakcích `EnlistDistributedTransaction` metoda připojení k zařazení připojení v <xref:System.EnterpriseServices.ITransaction> instanci, která je podporována pro zpětné kompatibility. Další informace o transakcích podnikové služby, najdete v části [vzájemná funkční spolupráce s Enterprise služeb a transakcí modelu COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 Při použití <xref:System.Transactions> transakce s zprostředkovatel rozhraní .NET Framework pro SQL Server na databázi systému SQL Server, lehké <xref:System.Transactions.Transaction> se automaticky použije. Transakce lze pak převést na úplné distribuovanou transakci na podle potřeby. Další informace najdete v tématu [System.Transactions – integrace s SQL serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
>  Maximální počet distribuovaných transakcí, které můžete najednou součástí databáze Oracle je ve výchozím nastavení do 10. Po 10 transakce je při připojení k databázi Oracle vyvolána výjimka. Oracle nepodporuje `DDL` uvnitř distribuované transakce.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Automaticky zapsání v distribuované transakce  
 Automatické zařazení je výchozí (a upřednostňovaný) způsob integrace ADO.NET – připojení s `System.Transactions`. Objekt připojení bude automaticky uvést v existující distribuované transakce, pokud zjistí, že transakce je aktivní, který v `System.Transaction` podmínky, znamená, že `Transaction.Current` není null. Automatický zápis do transakce nastane, když je otevřen připojení. Nebude dojít po, i když se příkaz spustí v oboru transakce. Můžete zakázat automatické zařazení ve stávajících transakcí zadáním `Enlist=false` jako parametr s řetězcem připojení pro <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>, nebo `OLE DB Services=-7` jako parametr s řetězcem připojení pro <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>. Další informace o parametrech řetězec připojení Oracle a rozhraní ODBC najdete v tématu <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> a <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>Ručně zapsání v distribuované transakce  
 Pokud je zakázáno automatické zařazení nebo potřebujete zařazení transakci, která byla spuštěna po otevření připojení, můžete zařazení existující distribuovanou transakci pomocí `EnlistTransaction` metodu <xref:System.Data.Common.DbConnection> objekt pro poskytovatele práci s. Uvedení v existující distribuované transakce zajistí, že pokud je transakce potvrzena nebo vrácena zpět, změny provedené kód ve zdroji dat bude možné potvrzena nebo vrácena zpět také.  
  
 Uvedení v distribuovaných transakcích je zvláště použít, když sdružování obchodní objekty. Pokud obchodní objekt je ve fondu s otevřené připojení, automatické transakce zařazení dochází pouze po otevření připojení. Pokud více transakcí se provádí pomocí objektu ve fondu firmy, otevřete připojení pro tento objekt nebude automaticky zapsat do nově initiated transakcí. V takovém případě můžete zakázat automatické transakce zařazení pro připojení a zařazení připojení v transakcích pomocí `EnlistTransaction`.  
  
 `EnlistTransaction`použije jeden argument typu <xref:System.Transactions.Transaction> tedy odkaz na stávající transakce. Po volání metody připojení `EnlistTransaction` metoda, všechny změny provedené v zdroje dat pomocí připojení jsou zahrnuty v transakci. Předání hodnotou null unenlists připojení z jeho aktuálního zařazení distribuované transakce. Všimněte si, že musí být připojení otevřeno před voláním `EnlistTransaction`.  
  
> [!NOTE]
>  Po připojení je explicitně zařazeny do transakce, nemůže být zrušení zařazené nebo zařazené v jiné transakci, dokud nebude dokončeno první transakce.  
  
> [!CAUTION]
>  `EnlistTransaction`vyvolá výjimku, pokud připojení již zahájila transakci pomocí připojení <xref:System.Data.Common.DbConnection.BeginTransaction%2A> metoda. Ale pokud transakce je místní transakce spuštěna ve zdroji dat (například provádění příkazu BEGIN TRANSACTION explicitně pomocí <xref:System.Data.SqlClient.SqlCommand>), `EnlistTransaction` bude místní transakci vrátit zpět a uvést v existující distribuované transakce podle požadavku. Neobdrží Všimněte si, že místní transakce byla vrácena zpět a musí spravovat jakékoli místní transakce nebyla spuštěna pomocí <xref:System.Data.Common.DbConnection.BeginTransaction%2A>. Pokud používáte zprostředkovatele dat .NET Framework pro SQL Server (`SqlClient`) se systémem SQL Server, pokus o zařazení vyvolá výjimku. Všech ostatních případech pokračovat nezjištěné.  
  
## <a name="promotable-transactions-in-sql-server"></a>Možné zvýšit transakcí v systému SQL Server  
 Systém SQL Server podporuje možné zvýšit transakce, ve kterých místní transakce lightweight můžete bude automaticky povýšen na distribuovanou transakci pouze v případě potřeby. Možné zvýšit transakce nevyvolá přidaném starat se o distribuované transakce Pokud přidaném režie není nutné. Další informace a ukázku kódu najdete v tématu [System.Transactions – integrace s SQL serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Konfiguraci distribuovaných transakcí  
 Musíte povolit MS DTC přes síť, aby bylo možné používat distribuované transakce. Pokud máte Windows povolena brána Firewall, musíte povolit službu MS DTC se použití sítě nebo otevřít port MS DTC.  
  
## <a name="see-also"></a>Viz také  
 [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Integrace System.Transactions s SQL Serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
