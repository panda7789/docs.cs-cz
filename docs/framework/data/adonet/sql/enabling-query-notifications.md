---
title: Povolení oznámení dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 9919bad113eb11a38ce137a2cbbf6c67bd5b21ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794082"
---
# <a name="enabling-query-notifications"></a>Povolení oznámení dotazů
Aplikace, které využívají oznámení dotazů, mají společnou sadu požadavků. Váš zdroj dat musí být správně nakonfigurovaný tak, aby podporoval oznamování dotazů SQL, a uživatel musí mít správná oprávnění na straně klienta a na straně serveru.  
  
 Pokud chcete používat oznámení dotazů, musíte:  
  
- Povolí oznámení dotazů pro vaši databázi.  
  
- Ujistěte se, že ID uživatele používané pro připojení k databázi má potřebná oprávnění.  
  
- Použijte objekt ke spuštění platného příkazu SELECT s přidruženým objektem oznámení – buď <xref:System.Data.SqlClient.SqlDependency> nebo <xref:System.Data.Sql.SqlNotificationRequest>. <xref:System.Data.SqlClient.SqlCommand>  
  
- Poskytněte kód pro zpracování oznámení v případě, že se data monitorují.  
  
## <a name="query-notifications-requirements"></a>Požadavky na oznámení dotazů  
 Oznámení dotazů jsou podporována pouze pro příkazy SELECT, které splňují specifické požadavky. Následující tabulka obsahuje odkazy na Service Broker a dokumentaci k oznámením o dotazech v SQL Server Books Online.  
  
 **Dokumentace k SQL Server**  
  
- [Vytvoření dotazu pro oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Požadavky na zabezpečení pro Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Zabezpečení a ochrana (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Bezpečnostní opatření pro služby oznamování](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Oprávnění pro oznamování dotazů](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Mezinárodní požadavky na Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Požadavky na návrh řešení (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [InfoCenter pro vývojáře Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Příručka pro vývojáře (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Povolení oznámení dotazů ke spuštění ukázkového kódu  
 Chcete-li povolit Service Broker v databázi **AdventureWorks** pomocí SQL Server Management Studio, spusťte následující příkaz Transact-SQL:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Aby ukázky oznámení dotazů běžely správně, musí se na databázovém serveru spustit následující příkazy jazyka Transact-SQL.  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Oprávnění pro oznamování dotazů  
 Uživatelé, kteří provádějí příkazy požadující oznámení, musí mít oprávnění k přihlášení k odběru databáze oznámení na serveru.  
  
 Kód na <xref:System.Data.SqlClient.SqlClientPermission>straně klienta, který běží v případě částečné důvěryhodnosti, vyžaduje.  
  
 Následující kód vytvoří <xref:System.Data.SqlClient.SqlClientPermission> objekt a <xref:System.Security.Permissions.PermissionState> nastaví <xref:System.Security.Permissions.PermissionState.Unrestricted>na. Vynutízaběhuvpřípadě,ženavšechvolajícíchvyššíchvzásobníkuvolánínebylaudělenapříslušnáoprávnění.<xref:System.Security.CodeAccessPermission.Demand%2A> <xref:System.Security.SecurityException>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Výběr objektu oznámení  
 Rozhraní API pro oznamování dotazů poskytuje dva objekty pro zpracování <xref:System.Data.SqlClient.SqlDependency> oznámení <xref:System.Data.Sql.SqlNotificationRequest>: a. Obecně platí, že <xref:System.Data.SqlClient.SqlDependency> většina aplikací non-ASP.NET by měla použít objekt. ASP.NET aplikace by měly používat vyšší úroveň <xref:System.Web.Caching.SqlCacheDependency>, která <xref:System.Data.SqlClient.SqlDependency> zabalí a poskytuje rozhraní pro správu oznámení a objektů mezipaměti.  
  
### <a name="using-sqldependency"></a>Použití třídy SqlDependency  
 Aby bylo <xref:System.Data.SqlClient.SqlDependency>možné použít Service Broker musí být povolená pro SQL Server používaná databáze a uživatelé musí mít oprávnění k přijímání oznámení. Service Broker objekty, jako je například fronta oznámení, jsou předdefinovány.  
  
 Kromě toho <xref:System.Data.SqlClient.SqlDependency> automaticky spouští pracovní vlákno ke zpracování oznámení, která jsou publikována do fronty. také analyzuje zprávu Service Broker a zpřístupňuje informace jako data argumentu události. <xref:System.Data.SqlClient.SqlDependency>je nutné inicializovat voláním `Start` metody pro vytvoření závislosti na databázi. Toto je statická metoda, kterou je třeba volat pouze jednou při inicializaci aplikace pro každé požadované připojení databáze. `Stop` Metoda by měla být volána při ukončení aplikace pro každé připojení závislosti, které bylo provedeno.  
  
### <a name="using-sqlnotificationrequest"></a>Použití SqlNotificationRequest  
 Naproti tomu <xref:System.Data.Sql.SqlNotificationRequest> vyžaduje implementaci celé naslouchající infrastruktury sami. Kromě toho musí být definované všechny podpůrné Service Broker objekty, jako jsou fronty, služby a typy zpráv podporované frontou. Tento ruční přístup je užitečný v případě, že vaše aplikace vyžaduje speciální oznamovací zprávy nebo oznamovací chování nebo pokud je vaše aplikace součástí větší Service Broker aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Oznámení pro dotazy na SQL Serveru](query-notifications-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
