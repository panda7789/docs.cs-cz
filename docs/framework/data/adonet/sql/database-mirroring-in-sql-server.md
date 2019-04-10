---
title: Zrcadlení databáze na SQL Serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: bdcdce58d78a305493bd698cf4d849e640f14ce0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230990"
---
# <a name="database-mirroring-in-sql-server"></a>Zrcadlení databáze na SQL Serveru
Zrcadlení databáze na SQL serveru umožňuje udržovat kopie nebo zrcadlení databáze systému SQL Server na pohotovostní server. Zrcadlení zajistí, že dvě oddělené kopie dat existují na všechny časy, tím vysokou dostupnost a redundanci dat dokončit. .NET Data Provider pro SQL Server podporuje implicitní zrcadlení databáze, takže vývojáři nemusí provádět žádnou akci nebo psát jakýkoli kód, když je nakonfigurovaná pro databázi serveru SQL Server. Kromě toho <xref:System.Data.SqlClient.SqlConnection> objekt podporuje režim explicitní spojení, která umožňuje zadávání názvu serveru partnera převzetí služeb při selhání v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Následující zjednodušený pořadí událostí dojde k <xref:System.Data.SqlClient.SqlConnection> objekt, který je zaměřen na databázi nakonfigurována pro zrcadlení:  
  
1.  Klientská aplikace se úspěšně připojí k hlavní databázi a server odešle zpět název partnerského serveru, který se pak zapíší do mezipaměti na straně klienta.  
  
2.  Pokud dojde k selhání serveru, který obsahuje hlavní databázi nebo dojde k přerušení připojení, dojde ke ztrátě stavu připojení a transakce. Klientská aplikace se pokusí znovu navázat připojení k hlavní databázi a selže.  
  
3.  Klientská aplikace pak transparentně pokusí navázat připojení k databázi zrcadlení na partnerském serveru. Pokud se aktivace podaří, připojení je přesměrován na zrcadlení databáze, která se pak stane nová primární databáze.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Určení partnera převzetí služeb při selhání v připojovacím řetězci  
 Pokud zadáte název serveru partnera převzetí služeb při selhání v připojovacím řetězci, klient Pokud hlavní databáze není k dispozici, když klientská aplikace poprvé připojí transparentně pokusí připojení s partnerem převzetí služeb při selhání.  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 Pokud nezadáte název partnerského serveru, převzetí služeb při selhání a objektu zabezpečení databáze není k dispozici když klientská aplikace poprvé připojí potom <xref:System.Data.SqlClient.SqlException> je vyvolána.  
  
 Když <xref:System.Data.SqlClient.SqlConnection> je úspěšně otevřen, název partnera převzetí služeb při selhání je vrácená serverem a nahrazuje všechny hodnoty zadané v připojovacím řetězci.  
  
> [!NOTE]
>  V připojovacím řetězci pro databázi zrcadlení scénáře musíte explicitně zadat název počátečního katalogu nebo databáze. Pokud klient obdrží informace o převzetí služeb při selhání na připojení, který nemá explicitně zadaný počáteční katalog ani databáze, informace o převzetí služeb při selhání neukládá do mezipaměti a aplikace nebude pokoušet o převzetí služeb při selhání, pokud dojde k selhání hlavního serveru. Pokud připojovací řetězec má hodnotu pro partnera převzetí služeb při selhání, ale žádná hodnota pro počátečního katalogu nebo databáze, `InvalidArgumentException` je vyvolána.  
  
## <a name="retrieving-the-current-server-name"></a>Získávání aktuální název serveru  
 V případě selhání, můžete načíst název serveru, ke kterému je aktuálního připojení ve skutečnosti připojený pomocí <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> objektu. Následující fragment kódu načte název aktivního serveru, za předpokladu, že připojení proměnná odkazuje otevřenou <xref:System.Data.SqlClient.SqlConnection>.  
  
 Při výskytu události převzetí služeb při selhání a připojení se přepnulo na zrcadlový server, **DataSource** vlastnost aktualizován, aby odrážel název zrcadlení.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>SqlClient zrcadlení chování  
 Klient se vždy pokusí připojit k aktuálnímu objektu zabezpečení serveru. Pokud selže, pokusí partnera převzetí služeb při selhání. Pokud zrcadlové databáze již byla přepnuta na hlavní role na partnerském serveru, připojení bude úspěšné a nové mapování objektu zabezpečení zrcadlení se může odeslat klientovi a uložili do mezipaměti po dobu životnosti volající <xref:System.AppDomain>. Neukládá do trvalého úložiště a není k dispozici pro další připojení v jiné **AppDomain** nebo proces. Je však k dispozici pro další připojení v rámci stejného **AppDomain**. Poznámka: to jiné **AppDomain** nebo proces, který běží na stejném nebo jiném počítači vždy má svůj fond připojení, a tato připojení neresetují. V takovém případě Pokud primární databáze přestane fungovat, každý proces nebo **AppDomain** jednou selže a fond se automaticky vymaže.  
  
> [!NOTE]
>  Zrcadlení podpory na serveru je nakonfigurovaný na základě na databázi. Pokud operace manipulace s daty jsou vykonávány na jiných databází není zahrnuta v sadě objekt zabezpečení/zrcadlení pomocí s více částmi. názvy nebo při změně aktuální databáze, změny se tyto databáze nejsou rozšířena v případě selhání. Při změně dat v databázi, která není zrcadlena, nevygeneruje se žádná chyba. Vývojář musí být vyhodnocen případný dopad těchto operací.  
  
## <a name="database-mirroring-resources"></a>Zrcadlení prostředky databáze  
 Rámcové dokumentaci a informace o konfiguraci nasazování a správě zrcadlení, najdete v následujících zdrojích v dokumentaci k SQL serveru.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zrcadlení databáze](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|Popisuje, jak vytvořit a nakonfigurovat zrcadlení v systému SQL Server.|  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
