---
title: Distribuované transakce
ms.date: 03/30/2017
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
ms.openlocfilehash: 89d94e94ea74c73a7f68f6052291c95a7c96f0d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150199"
---
# <a name="distributed-transactions"></a>Distribuované transakce
Transakce je sadu související úlohy, která buď (potvrzení) úspěšná nebo neúspěšná (přerušit) jako celek, mimo jiné. A *distribuované transakce* je transakce, která ovlivňuje několik prostředků. Pro distribuovanou transakci potvrdit musí všichni účastníci zaručit, že změny dat bude trvalé. Změny musíte zachovat navzdory zhroucení systému nebo jiné nepředvídatelné události. Pokud ještě jeden účastník neprovede této záruky, celá transakce nezdaří a všechny změny dat v rámci oboru transakce jsou vrácena zpět.  
  
> [!NOTE]
>  Bude vyvolána výjimka, pokud se pokusíte potvrzení nebo vrácení zpět transakcí, pokud `DataReader` je spuštěna, když je aktivní transakce.  
  
## <a name="working-with-systemtransactions"></a>Práce s System.Transactions  
 V rozhraní .NET Framework, jsou distribuované transakce spravované prostřednictvím rozhraní API ve službě <xref:System.Transactions> oboru názvů. <xref:System.Transactions> Rozhraní API budou delegovat to zpracování k monitorování transakce, jako je například Microsoft distribuované transakce koordinátor (MS DTC) při více správci trvalý prostředků se využívá řada distribuované transakce. Další informace najdete v tématu [Principy transakcí](../../../../docs/framework/data/transactions/transaction-fundamentals.md).  
  
 ADO.NET 2.0 zavedl podporu pro uvedení v distribuovaných transakcí pomocí `EnlistTransaction` metodu, která využívá připojení <xref:System.Transactions.Transaction> instance. V předchozích verzích technologie ADO.NET byla provedena pomocí explicitní zařazení do distribuované transakce `EnlistDistributedTransaction` způsob připojení k zařazení připojení <xref:System.EnterpriseServices.ITransaction> instance, která je podporována pro zpětné kompatibility. Další informace o transakcích podnikových služeb, naleznete v tématu [interoperabilita se službami Enterprise Services a transakcemi COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
 Při použití <xref:System.Transactions> transakce s zprostředkovatele .NET Framework pro SQL Server pro databázi systému SQL Server, zjednodušenou <xref:System.Transactions.Transaction> se automaticky použije. Transakce může pak být povýšen na úplná distribuované transakce podle potřeby. Další informace najdete v tématu [integrace System.Transactions s SQL serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
> [!NOTE]
>  Maximální počet distribuovaných transakcí, které databáze Oracle se můžete zúčastnit v okamžiku je ve výchozím nastavení do 10. Po 10. transakce je při připojení k databázi Oracle vyvolána výjimka. Oracle nepodporuje `DDL` uvnitř distribuované transakce.  
  
## <a name="automatically-enlisting-in-a-distributed-transaction"></a>Automaticky uvedení v distribuované transakci  
 Automatické zařazení je výchozí (a upřednostňované) způsob, jak integrace připojení ADO.NET s `System.Transactions`. Objekt připojení se automaticky zařadit do existující distribuovanou transakci, pokud určí, že transakcí je aktivní, který v `System.Transaction` podmínky, znamená to, že `Transaction.Current` nemá hodnotu null. Automatický zápis do transakce nastane při otevření připojení. Nesmí dojít po tomto i v případě, že příkaz je proveden v rámci oboru transakce. Automatické zařazení do existující transakce můžete zakázat tak, že zadáte `Enlist=false` jako parametr řetězec připojení <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>, nebo `OLE DB Services=-7` jako parametr řetězec připojení pro <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=nameWithType>. Další informace o Oracle a rozhraní ODBC parametry připojovacího řetězce, naleznete v tématu <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=nameWithType> a <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=nameWithType>.  
  
## <a name="manually-enlisting-in-a-distributed-transaction"></a>Ručně uvedení v distribuované transakci  
 Pokud je zakázáno automatické zařazení nebo budete potřebovat k zařazení transakce, která byla spuštěna po otevření připojení, může zařazení v existujících distribuovaných transakcí pomocí `EnlistTransaction` metodu <xref:System.Data.Common.DbConnection> objekt poskytovatele pracujete s. Uvedení v existující distribuované transakce zajistí, že pokud je transakce potvrzena nebo vrácena zpět, změny provedené v kódu ve zdroji dat se být potvrzena nebo vrácena zpět také.  
  
 Uvedení v distribuovaných transakcích platí zejména při vytváření fondů pro obchodní objekty. Pokud obchodní objekt je ve fondu s otevřené připojení, automatické transakce zařazení pouze nastane při otevření tohoto připojení. Pokud více transakcí se provádí pomocí ve fondu obchodního objektu, otevřené připojení pro tento objekt nebude automaticky zařadit do nově iniciované transakce. V takovém případě můžete zakázat automatické transakce zařazení pro připojení a zařadit do transakce pomocí připojení `EnlistTransaction`.  
  
 `EnlistTransaction` přijímá jeden argument typu <xref:System.Transactions.Transaction> , který je odkaz na existující transakce. Po volání metody připojení `EnlistTransaction` metoda, všechny změny provedené ve zdroji dat pomocí připojení jsou zahrnuty v transakci. Předání hodnoty null unenlists připojení z jeho aktuálního zařazení distribuované transakce. Všimněte si, že připojení musí být otevřen před voláním `EnlistTransaction`.  
  
> [!NOTE]
>  Po připojení je explicitně zapsána na transakci, nemůže být zrušit zařazených nebo zařazených do jiné transakce až do dokončení první transakce.  
  
> [!CAUTION]
>  `EnlistTransaction` vyvolá výjimku, pokud připojení již začala transakci pomocí připojení <xref:System.Data.Common.DbConnection.BeginTransaction%2A> metody. Ale pokud transakce je spuštěn ve zdroji dat místní transakce (například příkaz BEGIN TRANSACTION explicitně pomocí provádí <xref:System.Data.SqlClient.SqlCommand>), `EnlistTransaction` se vrátit zpět místní transakce a zařazení v existujícím distribuované transakce podle požadavku. Neobdrží Všimněte si, že se místní transakce byla vrácena zpět a spravujte všechny místní transakce nebyla spuštěna pomocí <xref:System.Data.Common.DbConnection.BeginTransaction%2A>. Pokud používáte zprostředkovatele dat .NET Framework pro SQL Server (`SqlClient`) s SQL serverem, pokus o zařazení vyvolá výjimku. Bude pokračovat nezjištěné po všech ostatních případech.  
  
## <a name="promotable-transactions-in-sql-server"></a>Možné zařazení transakce v systému SQL Server  
 SQL Server podporuje možné zařazení transakce, ve kterých místní transakce zjednodušené může být automaticky povýšen na distribuovanou transakci pouze v případě, že je vyžadován. Možné zařazení transakce vyvolat není přidaný režie distribuované transakce, pokud přidaného zatížení je povinný. Další informace a ukázky kódu najdete v tématu [integrace System.Transactions s SQL serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md).  
  
## <a name="configuring-distributed-transactions"></a>Konfigurace distribuované transakce  
 Budete muset povolit MS DTC v síti, abyste mohli používat distribuované transakce. Pokud jste Windows povolena brána Firewall, musíte také povolit službě MS DTC a používat síť a neotevírejte port MS DTC.  
  
## <a name="see-also"></a>Viz také:

- [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [Integrace System.Transactions s SQL Serverem](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
