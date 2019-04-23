---
title: Podpora klienta SqlClient pro vysokou dostupnost a zotavení po havárii
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: 40054378319b81113dcb8f40cb82a8b1d02fc594
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307591"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Podpora klienta SqlClient pro vysokou dostupnost a zotavení po havárii
Toto téma popisuje podpora klienta SqlClient (přidá [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]) pro vysokou dostupnost, zotavení po havárii – skupin dostupnosti AlwaysOn.  Funkce dostupnosti skupin AlwaysOn byl přidán do systému SQL Server 2012. Další informace o skupinách dostupnosti AlwaysOn naleznete v tématu knihy Online SQL Server.  
  
 Teď můžete specifikovat naslouchacího procesu skupiny dostupnosti systému (vysoká dostupnost, zotavení po havárii) availability group (skupina dostupnosti) či Instance clusteru SQL serveru 2012 převzetí služeb při selhání ve vlastnosti připojení. Pokud SqlClient aplikace je připojená k databázi, která převezme služby při selhání AlwaysOn, původní připojení bylo přerušeno a aplikace musíte otevřít nové připojení, chcete-li pokračovat v práci po převzetí služeb.  
  
 Pokud se nepřipojujete k naslouchacího procesu skupiny dostupnosti nebo Instance clusteru převzetí služeb při selhání systému SQL Server 2012 a několik IP adres jsou spojeny s názvem hostitele, bude SqlClient postupně iterovat přes všechny IP adresy přidružené k záznamu DNS. To může být časově náročné Pokud první IP adresu vrácenou serverem DNS není vázán k žádné síťovou kartu (NIC). Při připojování k naslouchacího procesu skupiny dostupnosti nebo Instance clusteru převzetí služeb při selhání systému SQL Server 2012, se pokusí navázat připojení ke všem IP adresám paralelně SqlClient a pokud pokus o připojení bude úspěšné, ovladač se zahodí všechny čekající připojení pokusy.  
  
> [!NOTE]
>  Zvýšení časového limitu připojení a implementovat logiku opakování připojení zvýší pravděpodobnost, že aplikace se připojí ke skupině dostupnosti. Také protože připojení může selhat z důvodu převzetí služeb při selhání, měli byste implementovat logiku opakování připojení, opakování pokusu o připojení se nezdařilo, dokud ho znovu připojí.  
  
 Následující vlastnosti připojení byly přidány do SqlClient v [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]:  
  
-   `ApplicationIntent`  
  
-   `MultiSubnetFailover`  
  
 Můžete programově upravit tato klíčová slova řetězec připojení s:  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
>  Nastavení `MultiSubnetFailover` k `true` není požadován spolu s [!INCLUDE[net_v461](../../../../../includes/net-v461-md.md)] nebo novější verze.
  
## <a name="connecting-with-multisubnetfailover"></a>Propojení s MultiSubnetFailover  
 Vždy zadávat `MultiSubnetFailover=True` při připojování k naslouchacího procesu skupiny dostupnosti SQL Server 2012 nebo Instance clusteru převzetí služeb při selhání systému SQL Server 2012. `MultiSubnetFailover` umožňuje rychlejší převzetí služeb při selhání pro všechny skupiny dostupnosti a nebo Instance clusteru převzetí služeb při selhání v systému SQL Server 2012 a budou výrazně zkrátit čas, převzetí služeb při selhání pro jeden a více podsítí topologie AlwaysOn. Při selhání více podsítí klient se pokusí připojení paralelně. Při selhání podsíť se agresivně pokusí navázat připojení TCP.  
  
 `MultiSubnetFailover` Vlastnost připojení znamená, že aplikace se nasazuje v skupiny dostupnosti nebo Instance clusteru převzetí služeb při selhání systému SQL Server 2012 a že se pokusí připojit k databázi na primární instanci systému SQL Server tak, že zkusíte SqlClient Připojte se ke všem IP adresám. Když `MultiSubnetFailover=True` je určená pro připojení, klient pokus obnovuje pokusy o připojení TCP rychleji než intervaly opakování TCP výchozí operační systém. To umožňuje rychlejší opětovného připojení po převzetí služeb při selhání skupiny dostupnosti AlwaysOn nebo Instance clusteru převzetí služeb při selhání AlwaysOn a vztahuje se na subnet jeden a více skupin dostupnosti i instance clusteru převzetí služeb při selhání.  
  
 Další informace o klíčových slovech řetězec připojení v SqlClient najdete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Určení `MultiSubnetFailover=True` při připojování na něco jiného než naslouchacího procesu skupiny dostupnosti nebo Instance clusteru převzetí služeb při selhání systému SQL Server 2012 může mít za následek negativní dopad na výkon a není podporována.  
  
 Použijte následující pokyny pro připojení k serveru ve skupině dostupnosti nebo Instance clusteru převzetí služeb při selhání systému SQL Server 2012:  
  
-   Použití `MultiSubnetFailover` vlastnost připojení při připojování k podsíti jeden nebo více podsítí; zlepší výkon obou.  
  
-   Pro připojení ke skupině dostupnosti, zadejte naslouchací proces skupiny dostupnosti skupiny dostupnosti jako server v připojovacím řetězci.  
  
-   Připojení k serveru SQL Server instance nakonfigurované s více než 64 IP adresami způsobí selhání připojení.  
  
-   Chování aplikace, která se používá `MultiSubnetFailover` připojení vlastnost nemá vliv na základě typu ověřování: Ověřování systému SQL Server, ověřování protokolu Kerberos nebo ověřování Windows.  
  
-   Zvyšte hodnotu `Connect Timeout` podle pro převzetí služeb při selhání čas a omezit opakované pokusy o připojení aplikace.  
  
-   Distribuované transakce nejsou podporovány.  
  
 Pokud směrování jen pro čtení není platná, připojení k umístění sekundární repliky se nezdaří v následujících situacích:  
  
1. Pokud umístění sekundární replika není nakonfigurovaná tak, aby přijímal připojení.  
  
2. Pokud aplikace používá `ApplicationIntent=ReadWrite` (viz následující popis) a sekundární replika umístění je nakonfigurovaná pro přístup jen pro čtení.  
  
 <xref:System.Data.SqlClient.SqlDependency> na sekundárních replikách jen pro čtení se nepodporuje.  
  
 Připojení se nezdaří, pokud je primární repliky nakonfigurovali odmítnout úlohy jen pro čtení a připojovací řetězec obsahuje `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Upgrade na použití více podsítí clusterů z zrcadlení databáze  
 Chyba připojení (<xref:System.ArgumentException>) dojde, pokud `MultiSubnetFailover` a `Failover Partner` připojení klíčová slova jsou k dispozici v připojovacím řetězci, nebo pokud `MultiSubnetFailover=True` a používá protokol než TCP. Chyba (<xref:System.Data.SqlClient.SqlException>) se vrátí taky `MultiSubnetFailover` se používá a SQL Server vrátí odpověď partnera převzetí služeb při selhání určující je součástí páru zrcadlení databáze.  
  
 Pokud upgradujete SqlClient aplikace, které aktuálně používá zrcadlení databáze pro více podsítí scénář, měli byste odebrat `Failover Partner` připojení vlastnosti a nahraďte ho hodnotou `MultiSubnetFailover` nastavena na `True` a nahradit název serveru v připojovací řetězec s naslouchací proces skupiny dostupnosti. Pokud používáte připojovací řetězec `Failover Partner` a `MultiSubnetFailover=True`, ovladač vygeneruje chybu. Nicméně pokud používá připojovací řetězec `Failover Partner` a `MultiSubnetFailover=False` (nebo `ApplicationIntent=ReadWrite`), bude aplikace používat zrcadlení databáze.  
  
 Ovladač vrátí chybu, pokud se používá zrcadlení databáze u primární databáze v skupina dostupnosti a pokud `MultiSubnetFailover=True` se používá v připojovacím řetězci, který se připojuje k databázi primárních místo pro naslouchací proces skupiny dostupnosti.  
  
## <a name="specifying-application-intent"></a>Určení záměru aplikace  
 Když `ApplicationIntent=ReadOnly`, si klient vyžádá další úlohy, při připojení k databázi povolenou funkcí AlwaysOn. Server bude vynucovat záměr v době připojení a při příkaz databáze USE, ale pouze pro povolené databázi Always On.  
  
 `ApplicationIntent` – Klíčové slovo nefunguje s databázemi starší verze, jen pro čtení.  
  
 Databázi můžete povolit nebo zakázat úlohami pro čtení na cílovou databázi AlwaysOn. (Používá se k tomu `ALLOW_CONNECTIONS` klauzuli `PRIMARY_ROLE` a `SECONDARY_ROLE` [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy.)  
  
 `ApplicationIntent` – Klíčové slovo se používá k povolení směrování jen pro čtení.  
  
## <a name="read-only-routing"></a>Směrování jen pro čtení  
 Směrování jen pro čtení je funkce, která můžete zajistit dostupnost čtení jedinou replikou databáze. Pokud chcete povolit směrování jen pro čtení:  
  
1. Musíte se připojit k naslouchací proces skupiny dostupnosti skupiny dostupnosti Always On.  
  
2. `ApplicationIntent` Klíčové slovo připojovacího řetězce musí být nastaveno na `ReadOnly`.  
  
3. Skupiny dostupnosti musí být nakonfigurované správcem databáze umožňující směrování jen pro čtení.  
  
 Je možné, že více připojení pomocí směrování jen pro čtení se všechny připojit pro stejné repliky jen pro čtení. Změny v databázi synchronizace nebo změny konfigurace směrování na server může způsobit připojení klientů k jiné repliky jen pro čtení. Aby bylo zajištěno, že všechny požadavky jen pro čtení připojit pro stejné repliky jen pro čtení, nepředávejte naslouchací proces skupiny dostupnosti k `Data Source` klíčové slovo připojovacího řetězce. Místo toho zadejte název instance jen pro čtení.  
  
 Směrování jen pro čtení může trvat déle než připojení na primární, protože poprvé připojí k primární směrování jen pro čtení a potom vyhledá nejlepší dostupné čitelné sekundární. Z tohoto důvodu by měl zvýšit limit vaše přihlášení.  
  
## <a name="see-also"></a>Viz také:

- [Funkce SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
