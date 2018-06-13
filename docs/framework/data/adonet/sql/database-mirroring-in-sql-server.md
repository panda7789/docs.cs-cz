---
title: V systému SQL Server zrcadlení databáze
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: cbb4b729475c8f77c204c3a9250d48d4b0cd3bc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362267"
---
# <a name="database-mirroring-in-sql-server"></a>V systému SQL Server zrcadlení databáze
Zrcadlení databáze v systému SQL Server, můžete ponechat kopii nebo zrcadlení databáze systému SQL Server na pohotovostní server. Zrcadlení zajišťuje, že dvě samostatné kopie dat existují na všechny časy tím vysokou dostupnost a redundanci dat dokončit. Zprostředkovatel dat .NET pro SQL Server podporuje implicitní zrcadlení databáze, tak, aby vývojář není nutné provádět žádnou akci nebo psaní jakéhokoli kódu, jakmile byla nakonfigurována pro databázi systému SQL Server. Kromě toho <xref:System.Data.SqlClient.SqlConnection> objekt podporuje režim explicitní spojení umožňující poskytuje název serveru partnera převzetí služeb při selhání v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Následující zjednodušené posloupnost událostí pro <xref:System.Data.SqlClient.SqlConnection> objekt, který cílí nakonfigurována pro zrcadlení databáze:  
  
1.  Klientská aplikace úspěšně připojí k hlavní databáze, a server odešle zpět název partnerského serveru, které jsou pak uloženy v mezipaměti klienta.  
  
2.  Pokud dojde k selhání serveru, který obsahuje hlavní databázi nebo dojde k přerušení připojení, dojde ke ztrátě stavu připojení a transakce. Klientská aplikace se pokusí znovu navázat připojení k hlavní databáze a selže.  
  
3.  Klientská aplikace pak transparentně pokusí navázat připojení k databázi zrcadlení na partnerském serveru. Pokud se aktivace podaří, připojení se přesměruje na zrcadlení databáze, která se pak stane nový hlavní databáze.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Určení partnerovi převzetí služeb při selhání v připojovacím řetězci  
 Zadáte název partnerského serveru převzetí služeb při selhání v připojovacím řetězci, se klient pokusí připojení s partnerem převzetí služeb při selhání transparentně Pokud hlavní databáze není k dispozici, když se poprvé připojí klientské aplikace.  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 Pokud nezadáte název partnerského serveru, převzetí služeb při selhání a hlavní databáze není k dispozici při klientská aplikace poprvé připojí potom <xref:System.Data.SqlClient.SqlException> je vyvolána.  
  
 Když <xref:System.Data.SqlClient.SqlConnection> je úspěšně otevřen, název partnera převzetí služeb při selhání je vrácená serverem a nahrazuje všechny hodnoty zadané v připojovacím řetězci.  
  
> [!NOTE]
>  Počáteční název katalogu nebo databáze musí explicitně zadáte v připojovacím řetězci pro scénáře zrcadlení databáze. Pokud klient obdrží převzetí služeb při selhání informace o připojení, který nemá explicitně zadaný počáteční katalog ani databáze, informace o převzetí služeb při selhání není uložena v mezipaměti a aplikace nebude pokoušet o převzetí služeb při selhání Pokud hlavní server selže. Pokud připojovací řetězec má hodnotu partnerovi převzetí služeb při selhání, ale žádná hodnota pro úvodního katalogu nebo databáze, `InvalidArgumentException` je vyvolána.  
  
## <a name="retrieving-the-current-server-name"></a>Načítání aktuální název serveru  
 V případě selhání, můžete načíst název serveru, ke které je ve skutečnosti připojený k aktuálnímu připojení pomocí <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> objektu. Následující fragment kódu načte název aktivního serveru, za předpokladu, že proměnná připojení odkazuje otevřenou <xref:System.Data.SqlClient.SqlConnection>.  
  
 Když dojde k převzetí služeb při selhání události a připojení je přepnutá na zrcadlový server, **DataSource** vlastnosti podle názvu zrcadlení.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>Chování zrcadlení SqlClient  
 Klient se vždy pokusí připojit k aktuální objekt zabezpečení serveru. Pokud se nezdaří, se pokusí o partnerovi převzetí služeb při selhání. Pokud zrcadlové databáze již byla přepnuta na hlavní role na partnerském serveru, je připojení úspěšné a nový hlavní zrcadlení mapování odeslat klientovi a v mezipaměti po dobu jeho existence volání <xref:System.AppDomain>. To se neuloží do trvalého úložiště a není k dispozici pro další připojení v jiné **AppDomain** nebo proces. Je však k dispozici pro další připojení v rámci stejné **AppDomain**. Poznámka: to jiný **AppDomain** nebo proces, který běží na stejném nebo na jiném počítači vždy má svůj fond připojení, a tato připojení se neresetují. V takovém případě pokud výpadku primární databázi, každý proces nebo **AppDomain** jednou selže a fondu, jsou automaticky vymazány.  
  
> [!NOTE]
>  Zrcadlení podporu na serveru je konfigurováno na základě jednotlivé databáze. Pokud jsou u jiných databází, které nejsou zahrnuté v sadě hlavní či zrcadla pomocí s více částmi názvů nebo změnou aktuální databázi spustit operace zpracování dat se změny těchto jiných databází nešířily v případě selhání. Při změně dat v databázi, která není zrcadlena, nevygeneruje se žádná chyba. Vývojář se musí vyhodnotit možný účinek těchto operací.  
  
## <a name="database-mirroring-resources"></a>Prostředky zrcadlení databáze  
 Rámcová dokumentace a informace o konfiguraci nasazování a správě zrcadlení, naleznete v následujících zdrojích v SQL Server Books Online.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zrcadlení databáze](http://msdn.microsoft.com/library/bb934127.aspx) v Online knihách serveru SQL|Popisuje, jak nastavit a konfigurovat zrcadlení v systému SQL Server.|  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
