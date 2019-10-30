---
title: Zrcadlení databáze na SQL Serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: b18c67f5573d375fe0872d76d69a1f0aafa7e7f6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040444"
---
# <a name="database-mirroring-in-sql-server"></a>Zrcadlení databáze na SQL Serveru
Zrcadlení databáze v SQL Server umožňuje uchovávat kopii SQL Server databáze na pohotovostním serveru. Zrcadlení zajišťuje, aby dvě samostatné kopie dat existovaly vždy a poskytovaly vysokou dostupnost a úplnou redundanci dat. Rozhraní .NET Zprostředkovatel dat pro SQL Server poskytuje implicitní podporu zrcadlení databáze, takže vývojář nemusí provádět žádné akce ani psát kód, jakmile byl nakonfigurován pro databázi SQL Server. Kromě toho objekt <xref:System.Data.SqlClient.SqlConnection> podporuje explicitní režim připojení, který umožňuje poskytovat název partnerského serveru pro převzetí služeb při selhání v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Pro objekt <xref:System.Data.SqlClient.SqlConnection>, který cílí na databázi nakonfigurovanou pro zrcadlení, dochází k následující zjednodušené posloupnosti událostí:  
  
1. Klientská aplikace se úspěšně připojí k hlavní databázi a server pošle zpátky název partnerského serveru, který je pak uložen do mezipaměti klienta.  
  
2. Pokud dojde k chybě serveru, který obsahuje hlavní databázi nebo přerušení připojení, dojde ke ztrátě stavu připojení a transakce. Klientská aplikace se pokusí znovu navázat připojení k hlavní databázi a dojde k chybě.  
  
3. Klientská aplikace se pak transparentně pokusí vytvořit připojení k zrcadlové databázi na partnerském serveru. V případě úspěchu se připojení přesměruje na zrcadlenou databázi, která se následně stala novou hlavní databází.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Určení partnerského serveru pro převzetí služeb při selhání v připojovacím řetězci  
 Pokud v připojovacím řetězci zadáte název partnerského serveru pro převzetí služeb při selhání, klient se transparentně pokusí připojit k partnerovi převzetí služeb při selhání, pokud primární databáze není k dispozici, když se klientská aplikace poprvé připojí.  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
 Pokud vynecháte název partnerského serveru pro převzetí služeb při selhání a primární databáze není k dispozici, když se klientská aplikace poprvé připojí, dojde k vygenerování <xref:System.Data.SqlClient.SqlException>.  
  
 Po úspěšném otevření <xref:System.Data.SqlClient.SqlConnection> server vrátí název partnera pro převzetí služeb při selhání a nahradí všechny hodnoty zadané v připojovacím řetězci.  
  
> [!NOTE]
> V připojovacím řetězci pro scénáře zrcadlení databáze musíte explicitně zadat výchozí katalog nebo název databáze. Pokud klient obdrží informace o převzetí služeb při selhání u připojení, které nemá explicitně zadaný počáteční katalog nebo databázi, informace o převzetí služeb při selhání se neukládají do mezipaměti a aplikace se nepokusí převzít služby při selhání, pokud hlavní server selže. Pokud má připojovací řetězec hodnotu pro partnera pro převzetí služeb při selhání, ale není k dispozici žádná hodnota pro počáteční katalog nebo databázi, vyvolá se `InvalidArgumentException`.  
  
## <a name="retrieving-the-current-server-name"></a>Načítá se aktuální název serveru.  
 V případě převzetí služeb při selhání můžete načíst název serveru, ke kterému je aktuální připojení skutečně připojeno, pomocí vlastnosti <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> objektu <xref:System.Data.SqlClient.SqlConnection>. Následující fragment kódu načte název aktivního serveru za předpokladu, že proměnná připojení odkazuje na otevřený <xref:System.Data.SqlClient.SqlConnection>.  
  
 Když dojde k události převzetí služeb při selhání a připojení je přepnuto na zrcadlený server, vlastnost **DataSource** se aktualizuje tak, aby odrážela název zrcadla.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>Chování zrcadlení SqlClient  
 Klient se vždycky pokusí připojit k aktuálnímu hlavnímu serveru. Pokud se to nepovede, pokusí se partner převzetí služeb při selhání. Pokud zrcadlení databáze již bylo přepnuto na roli zabezpečení na partnerském serveru, připojení je úspěšné a nové mapování základní-zrcadlení je odesláno klientovi a uloženo do mezipaměti po dobu životnosti volajícího <xref:System.AppDomain>. Není uložen v trvalém úložišti a není k dispozici pro následná připojení v jiné **doméně** nebo procesu. Je však k dispozici pro následná připojení v rámci stejné **domény AppDomain**. Všimněte si, že jiná **doména AppDomain** nebo proces spuštěný ve stejném počítači nebo v jiném počítači má vždy svůj fond připojení a že tato připojení nejsou resetována. V takovém případě, pokud dojde k výpadku primární databáze, každý proces nebo **doména AppDomain** se jednou spustí a fond se automaticky vymaže.  
  
> [!NOTE]
> Podpora zrcadlení na serveru je nakonfigurovaná na bázi jednotlivých databází. Pokud jsou operace manipulace s daty spouštěny proti jiným databázím, které nejsou součástí objektu zabezpečení nebo zrcadlení, buď pomocí názvů v částech nebo změnou aktuální databáze, změny v těchto ostatních databázích nebudou rozšířeny v případě selhání. Při změně dat v databázi, která není zrcadlena, není generována žádná chyba. Vývojář musí vyhodnotit možný dopad takových operací.  
  
## <a name="database-mirroring-resources"></a>Prostředky zrcadlení databáze  
 Koncepční dokumentaci a informace o konfiguraci, nasazení a správě zrcadlení najdete v následujících zdrojích informací v dokumentaci SQL Server.  
  
|Partner|Popis|  
|--------------|-----------------|  
|[Zrcadlení databáze](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|Popisuje, jak nastavit a nakonfigurovat zrcadlení v SQL Server.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)
