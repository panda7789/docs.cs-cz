---
title: Podpora klienta SqlClient pro vysokou dostupnost a zotavení po havárii
description: Přečtěte si o podpoře aplikací SqlClient pro vysokou dostupnost a zotavení po havárii v SQL Server pomocí Skupiny dostupnosti AlwaysOn.
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: eba243d37db8262970d161cfa786d3aee4462950
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286207"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Podpora klienta SqlClient pro vysokou dostupnost a zotavení po havárii
Toto téma popisuje podporu SqlClient (přidáno v .NET Framework 4,5) pro zajištění vysoké dostupnosti, zotavení po havárii--Skupiny dostupnosti AlwaysOn.  Do SQL Server 2012 byla přidána funkce Skupiny dostupnosti AlwaysOn. Další informace o Skupiny dostupnosti AlwaysOn najdete v tématu SQL Server Books Online.  
  
 Nyní můžete určit naslouchací proces skupiny dostupnosti pro skupinu dostupnosti (s vysokou dostupností, zotavení po havárii) nebo instanci clusteru s podporou převzetí služeb při selhání SQL Server 2012 ve vlastnosti připojení. Pokud je aplikace SqlClient připojena k databázi AlwaysOn, která převezme služby při selhání, původní připojení je přerušeno a aplikace musí otevřít nové připojení, aby bylo možné pokračovat v práci po převzetí služeb při selhání.  
  
 Pokud se nepřipojujete k naslouchacího procesu skupiny dostupnosti nebo k instanci clusteru SQL Server 2012 s podporou převzetí služeb při selhání, a pokud je k názvu hostitele přidružené víc IP adres, SqlClient projde postupně všemi IP adresami přidruženými k položce DNS. To může být časově náročné, pokud první IP adresa vrácená serverem DNS není vázána na žádnou síťovou kartu (NIC). Když se připojíte ke naslouchacího procesu skupiny dostupnosti nebo instanci clusteru SQL Server 2012 s podporou převzetí služeb při selhání, pokusí se SqlClient navázat připojení k všem IP adresám paralelně a v případě úspěšného pokusu o připojení odstraní ovladač všechny pokusy o připojení.  
  
> [!NOTE]
> Zvýšení časového limitu připojení a implementace logiky opakování připojení zvýší pravděpodobnost, že se aplikace připojí ke skupině dostupnosti. Vzhledem k tomu, že připojení může selhat z důvodu převzetí služeb při selhání, měli byste implementovat logiku opakování připojení, opakovat pokus o připojení, dokud se znovu nepřipojí.  
  
 Do SqlClient v .NET Framework 4,5 se přidaly následující vlastnosti připojení:  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 Tato klíčová slova připojovacího řetězce můžete programově měnit pomocí:  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
> Nastavení `MultiSubnetFailover` na `true` není vyžadováno u .NET Framework 4.6.1 nebo novějších verzí.
  
## <a name="connecting-with-multisubnetfailover"></a>Připojení pomocí MultiSubnetFailover  
 Vždy zadejte `MultiSubnetFailover=True` , když se připojíte ke naslouchacího procesu skupiny dostupnosti SQL Server 2012 nebo instanci clusteru SQL Server 2012 převzetí služeb při selhání. `MultiSubnetFailover`umožňuje rychlejší převzetí služeb při selhání pro všechny skupiny dostupnosti a nebo instanci clusteru s podporou převzetí služeb při selhání v SQL Server 2012 a výrazně zkracuje dobu převzetí služeb při selhání pro topologie AlwaysOn jedné a více podsítí Při převzetí služeb při selhání s více podsítěmi se klient pokusí o připojení paralelně. Během převzetí služeb při selhání v podsíti dojde k agresivnímu opakovanému pokusu o připojení TCP.  
  
 `MultiSubnetFailover`Vlastnost Connection označuje, že aplikace je nasazená ve skupině dostupnosti nebo v instanci clusteru s podporou převzetí služeb při selhání SQL Server 2012 a že se pokusí připojit k databázi na primárním SQL Server instanci, a to tak, že se pokusí připojit ke všem IP adresám. Když `MultiSubnetFailover=True` je parametr zadán pro připojení, klient opakuje pokusy o připojení TCP rychleji než výchozí intervaly opakovaného přenosu protokolu TCP operačního systému. To umožňuje rychlejší opětovné připojení po převzetí služeb při selhání buď skupiny dostupnosti AlwaysOn nebo instance clusteru s podporou převzetí služeb při selhání AlwaysOn, a platí pro skupiny dostupnosti s jedním i několika podsítěmi a instance clusteru s podporou převzetí služeb při selhání.  
  
 Další informace o klíčových slovech připojovacího řetězce v SqlClient naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> .  
  
 Zadání `MultiSubnetFailover=True` při připojování k jinému objektu, než je naslouchací proces skupiny dostupnosti nebo instance clusteru s podporou převzetí služeb při selhání SQL Server 2012, může mít za následek negativní dopad na výkon a není podporováno.  
  
 Pomocí následujících pokynů se připojte k serveru ve skupině dostupnosti nebo v instanci clusteru s podporou převzetí služeb při selhání SQL Server 2012:  
  
- `MultiSubnetFailover`Vlastnost připojení použijte při připojování k jedné podsíti nebo více podsítím, vylepšit výkon pro obojí.  
  
- Pokud se chcete připojit ke skupině dostupnosti, zadejte jako server v připojovacím řetězci naslouchací proces skupiny dostupnosti skupiny dostupnosti.  
  
- Připojením k instanci SQL Server nakonfigurované s více než 64 IP adresami dojde k selhání připojení.  
  
- Chování aplikace, která používá `MultiSubnetFailover` vlastnost připojení, není ovlivněno na základě typu ověřování: SQL Server ověřování, ověřování protokolu Kerberos nebo ověřování systému Windows.  
  
- Zvyšte hodnotu pro `Connect Timeout` dobu převzetí služeb při selhání a snižte počet opakovaných pokusů o připojení k aplikacím.  
  
- Distribuované transakce nejsou podporovány.  
  
 Pokud směrování jen pro čtení není v platnosti, připojení k sekundárnímu umístění repliky selže v následujících situacích:  
  
1. Pokud umístění sekundární repliky není nakonfigurované na přijímání připojení.  
  
2. Pokud aplikace používá `ApplicationIntent=ReadWrite` (popisovaná níže) a umístění sekundární repliky je nakonfigurované pro přístup jen pro čtení.  
  
 <xref:System.Data.SqlClient.SqlDependency>není podporován v sekundárních replikách jen pro čtení.  
  
 Pokud je primární replika nakonfigurovaná tak, aby odmítala úlohy jen pro čtení, a připojovací řetězec obsahuje, připojení se nezdaří `ApplicationIntent=ReadOnly` .  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Upgrade na použití clusterů s více podsítěmi z zrcadlení databáze  
 K chybě připojení ( <xref:System.ArgumentException> ) dojde `MultiSubnetFailover` `Failover Partner` , pokud jsou v připojovacím řetězci přítomna klíčová slova a, nebo pokud se `MultiSubnetFailover=True` používá jiný protokol než TCP. <xref:System.Data.SqlClient.SqlException>Pokud se použije chyba () `MultiSubnetFailover` a SQL Server vrátí odpověď partnera pro převzetí služeb při selhání s oznámením, že je součástí páru zrcadlení databáze.  
  
 Pokud upgradujete aplikaci SqlClient, která aktuálně používá zrcadlení databáze, na scénář s více podsítěmi, měli byste odebrat `Failover Partner` vlastnost připojení a nahradit ji `MultiSubnetFailover` nastavením na `True` a nahradit název serveru v připojovacím řetězci pomocí naslouchacího procesu skupiny dostupnosti. Pokud připojovací řetězec používá `Failover Partner` a `MultiSubnetFailover=True` , ovladač vyvolá chybu. Pokud však připojovací řetězec používá `Failover Partner` a `MultiSubnetFailover=False` (nebo `ApplicationIntent=ReadWrite` ), aplikace bude používat zrcadlení databáze.  
  
 Ovladač vrátí chybu, pokud je zrcadlení databáze použito v primární databázi nástroje AG a pokud `MultiSubnetFailover=True` se používá v připojovacím řetězci, který se připojuje k primární databázi namísto naslouchacího procesu skupiny dostupnosti.  
  
## <a name="specifying-application-intent"></a>Určení záměru aplikace  
 Když `ApplicationIntent=ReadOnly` klient požaduje při připojení k databázi s povolenou funkcí AlwaysOn úlohu čtení. Server vynutil záměr při připojení a během příkazu USE Database, ale pouze pro databázi s povolenou databází Always On.  
  
 `ApplicationIntent`Klíčové slovo nefunguje se staršími databázemi, které jsou jen pro čtení.  
  
 Databáze může v cílové databázi AlwaysOn povolit nebo zakázat úlohy čtení. (To se provádí s `ALLOW_CONNECTIONS` klauzulí `PRIMARY_ROLE` `SECONDARY_ROLE` příkazy jazyka Transact-SQL.)  
  
 `ApplicationIntent`Klíčové slovo slouží k povolení směrování jen pro čtení.  
  
## <a name="read-only-routing"></a>Směrování jen pro čtení  
 Směrování jen pro čtení je funkce, která umožňuje zajistit dostupnost repliky jen pro čtení databáze. Postup povolení směrování jen pro čtení:  
  
1. Musíte se připojit ke naslouchacího procesu skupiny dostupnosti Always On.  
  
2. `ApplicationIntent`Klíčové slovo připojovacího řetězce musí být nastavené na `ReadOnly` .  
  
3. Aby bylo možné povolit směrování jen pro čtení, musí být skupina dostupnosti nakonfigurovaná správcem databáze.  
  
 Je možné, že vícenásobná připojení, která používají směrování jen pro čtení, nebudou připojena ke stejné replice jen pro čtení. Změny v synchronizaci databáze nebo změnách v konfiguraci směrování serveru můžou mít za následek připojení klientů k různým replikám jen pro čtení. Aby se zajistilo, že všechny požadavky jen pro čtení se připojují ke stejné replice jen pro čtení, nepředá do `Data Source` klíčového slova připojovacího řetězce naslouchací proces skupiny dostupnosti. Místo toho zadejte název instance, která je jen pro čtení.  
  
 Směrování jen pro čtení může trvat déle než připojení k primárnímu, protože směrování jen pro čtení se nejdřív připojí k primárnímu a pak vyhledá nejlepší dostupné čtení sekundárního. Z tohoto důvodu byste měli zvýšit svůj časový limit přihlášení.  
  
## <a name="see-also"></a>Viz také

- [Funkce SQL Serveru a ADO.NET](sql-server-features-and-adonet.md)
- [Přehled ADO.NET](../ado-net-overview.md)
