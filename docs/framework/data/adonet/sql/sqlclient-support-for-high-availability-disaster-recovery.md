---
title: "SqlClient podporu pro vysokou dostupnost a zotavení po havárii"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d2a444440af9dfaa2b084a55db9348fa48df7b54
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>SqlClient podporu pro vysokou dostupnost a zotavení po havárii
Toto téma popisuje podporu SqlClient (přidáno v [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]) pro vysokou dostupnost, zotavení po havárii – skupiny dostupnosti AlwaysOn.  Funkce skupin dostupnosti AlwaysOn byla přidána do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012. Další informace o skupinách dostupnosti AlwaysOn najdete v tématu [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] na webu knihy Online.  
  
 Nyní můžete určit naslouchacího procesu skupiny dostupnosti z (vysokou dostupnost, zotavení po havárii) skupiny dostupnosti (AG) nebo [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Instance clusteru převzetí služeb při selhání ve vlastnosti připojení. Pokud aplikace SqlClient je připojen k databázi AlwaysOn, který převezme, původní připojení je přerušené a aplikace, musíte otevřít nové připojení k pokračovat v práci po převzetí.  
  
 Pokud se nedaří připojit k naslouchací proces skupiny dostupnosti nebo [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Instance clusteru převzetí služeb při selhání, a pokud více IP adres přidružený název hostitele, bude SqlClient postupně iterace všechny IP adresy přidružené položky DNS. To může být časově náročná Pokud první IP adresu vrácenou pomocí serveru DNS není vázán na všechny síťová karta (NIC). Při připojování k naslouchací proces skupiny dostupnosti nebo [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Instance clusteru převzetí služeb při selhání, SqlClient pokusí navázat připojení k všechny IP adresy paralelně a pokud se pokus o připojení se podaří, ovladače se zahodí všechny čekající připojení pokusy.  
  
> [!NOTE]
>  Zvýšení časového limitu připojení a implementace logika opakovaných pokusů připojení zvýší pravděpodobnost, že aplikace budou připojovat ke skupině dostupnosti. Navíc vzhledem k tomu, že připojení může selhat z důvodu selhání, měli byste implementovat logiku opakovaných pokusů připojení, opakování pokusu o připojení se nezdařilo, dokud ho znovu připojí.  
  
 Následující vlastnosti připojení byly přidány do SqlClient v [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]:  
  
-   `ApplicationIntent`  
  
-   `MultiSubnetFailover`  
  
 Tato klíčová slova řetězce připojení s můžete upravit prostřednictvím kódu programu:  
  
1.  <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2.  <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  
  
## <a name="connecting-with-multisubnetfailover"></a>Propojení s MultiSubnetFailover  
 Vždycky zadat `MultiSubnetFailover=True` při připojování k [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 naslouchací proces skupiny dostupnosti nebo [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Instance clusteru převzetí služeb při selhání. `MultiSubnetFailover`umožňuje rychlejší převzetí služeb při selhání pro všechny skupiny dostupnosti a nebo Instance clusteru převzetí služeb při selhání v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 a budou výrazně zkrátit čas převzetí služeb při selhání pro jeden a více podsítí AlwaysOn topologie. Během převzetí služeb více podsítí se klient pokusí připojení paralelně. Při selhání podsíť bude intenzivně pokus o připojení protokolu TCP.  
  
 `MultiSubnetFailover` Vlastnost připojení označuje, že aplikace je nasazený ve skupině dostupnosti nebo [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Instance clusteru převzetí služeb při selhání a že SqlClient se pokusí připojit k databázi na primární [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instance pomocí došlo k pokusu o připojení pro všechny IP adresy. Když `MultiSubnetFailover=True` je zadán pro připojení, klient pokus obnovuje pokusy o připojení protokolu TCP rychleji než intervaly opakovaného přenosu TCP výchozí operační systém. To umožňuje rychlejší opětovného připojení po převzetí služeb při selhání skupiny dostupnosti AlwaysOn nebo Instance clusteru převzetí služeb při selhání AlwaysOn a používá se pro subnet jeden a více skupin dostupnosti i instance clusteru převzetí služeb při selhání.  
  
 Další informace o klíčových slovech řetězec připojení v SqlClient najdete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Určení `MultiSubnetFailover=True` při připojování k něco jiného než naslouchací proces skupiny dostupnosti nebo [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Instance clusteru převzetí služeb při selhání může mít za následek negativním dopadem na výkon a není podporována.  
  
 Použijte následující pokyny pro připojení k serveru ve skupině dostupnosti nebo [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Instance clusteru převzetí služeb při selhání 2012:  
  
-   Použití `MultiSubnetFailover` vlastnost připojení při připojování k podsíti jeden nebo více podsítí; zlepší výkon obou.  
  
-   Pro připojení ke skupině dostupnosti, zadejte naslouchacího procesu skupiny dostupnosti skupiny dostupnosti jako server v připojovacím řetězci.  
  
-   Připojování k [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instance, které jsou nakonfigurovány s víc než 64 IP adresami způsobí selhání připojení.  
  
-   Chování aplikace, která používá `MultiSubnetFailover` vlastnost připojení nemá vliv na základě typu ověřování: [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ověřování, ověřování pomocí protokolu Kerberos nebo ověřování systému Windows.  
  
-   Zvýšit hodnotu `Connect Timeout` pro uložení dobu převzetí služeb při selhání a snížit počet pokusů o opakování připojení aplikace.  
  
-   Distribuované transakce nejsou podporovány.  
  
 Pokud jen pro čtení směrování není funkční, připojení k umístění sekundární repliky se nezdaří v následujících situacích:  
  
1.  Pokud umístění sekundární replika není konfigurován na připojení.  
  
2.  Pokud aplikace používá `ApplicationIntent=ReadWrite` (viz následující popis) a umístění sekundární replika je nakonfigurovaný pro přístup jen pro čtení.  
  
 <xref:System.Data.SqlClient.SqlDependency>není podporována na sekundárních replikách jen pro čtení.  
  
 Připojení se nezdaří, pokud je primární replika nakonfigurovaná tak, aby zamítal úlohy jen pro čtení a připojovací řetězec obsahuje `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Upgrade na použití více podsítí clusterů z zrcadlení databáze  
 Chyba připojení (<xref:System.ArgumentException>) dojde v případě `MultiSubnetFailover` a `Failover Partner` klíčová slova připojení jsou k dispozici v připojovacím řetězci, nebo pokud `MultiSubnetFailover=True` a používá jiný protokol než TCP. K chybě (<xref:System.Data.SqlClient.SqlException>) bude také nastat, pokud `MultiSubnetFailover` se používá a [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] vrátí odpověď partnera převzetí služeb při selhání označující je součástí páru zrcadlení databáze.  
  
 Pokud upgradujete aplikaci SqlClient které aktuálně používá zrcadlení databáze pro určitý scénář více podsítí, byste měli odebrat `Failover Partner` vlastnost připojení a nahraďte ho `MultiSubnetFailover` nastavena na `True` a nahraďte název serveru ve připojovací řetězec s naslouchací proces skupiny dostupnosti. Pokud se používá připojovací řetězec `Failover Partner` a `MultiSubnetFailover=True`, ovladače dojde k chybě. Ale pokud používá připojovací řetězec `Failover Partner` a `MultiSubnetFailover=False` (nebo `ApplicationIntent=ReadWrite`), aplikace bude používat zrcadlení databáze.  
  
 Ovladač vrátí chybu, pokud zrcadlení databáze se používá v primární databázi v AG a `MultiSubnetFailover=True` se používá v připojovacím řetězci, který se připojuje k databázi v primární místo pro naslouchací proces skupiny dostupnosti.  
  
## <a name="specifying-application-intent"></a>Určení záměru aplikace  
 Když `ApplicationIntent=ReadOnly`, klient požádá o čtení zatížení při připojení k databázi povolenou funkcí AlwaysOn. Server vynutí záměr v době připojení a během příkaz databáze USE, ale jenom na povoleno databázi Always On.  
  
 `ApplicationIntent` – Klíčové slovo nefunguje s databázemi starší verze, jen pro čtení.  
  
 Databázi můžete povolí nebo zakáže čtení úloh na cílové databázi AlwaysOn. (To je prováděno pomocí `ALLOW_CONNECTIONS` klauzuli `PRIMARY_ROLE` a `SECONDARY_ROLE` [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy.)  
  
 `ApplicationIntent` – Klíčové slovo slouží k povolení směrování jen pro čtení.  
  
## <a name="read-only-routing"></a>Jen pro čtení směrování  
 Jen pro čtení směrování je funkce, která můžete zajistit dostupnost čtení pouze repliky databáze. Chcete-li povolit směrování jen pro čtení:  
  
1.  Musíte se připojit k naslouchací proces skupiny dostupnosti vždy na skupiny dostupnosti.  
  
2.  `ApplicationIntent` Klíčové slovo připojovacího řetězce musí být nastavena na `ReadOnly`.  
  
3.  Skupina dostupnosti musí být nakonfigurované správcem databáze umožňující směrování jen pro čtení.  
  
 Je možné, že více připojení pomocí směrování jen pro čtení se všechny připojí k stejné repliky jen pro čtení. Změny v synchronizaci databáze nebo změny v konfiguraci směrování serveru může způsobit připojení klienta k jiné repliky jen pro čtení. Aby se zajistilo, že všechny požadavky jen pro čtení připojit k stejné repliky jen pro čtení, nepředávejte naslouchací proces skupiny dostupnosti do `Data Source` klíčové slovo připojovacího řetězce. Místo toho zadejte název instance jen pro čtení.  
  
 Jen pro čtení směrování může trvat déle než připojení na primární, protože čtení pouze směrování poprvé připojí k primární a pak hledá nejlépe dostupné čitelný sekundární. Z toho důvodu měli zvýšit limit vaše přihlášení.  
  
## <a name="see-also"></a>Viz také  
 [Funkce SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
