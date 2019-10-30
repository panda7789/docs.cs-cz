---
title: Povolení oznámení dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 84048a3fba2b32b1ae745160e2b405c04b738c65
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040230"
---
# <a name="enabling-query-notifications"></a>Povolení oznámení dotazů
Aplikace, které využívají oznámení dotazů, mají společnou sadu požadavků. Váš zdroj dat musí být správně nakonfigurovaný tak, aby podporoval oznamování dotazů SQL, a uživatel musí mít správná oprávnění na straně klienta a na straně serveru.  
  
 Pokud chcete používat oznámení dotazů, musíte:  
  
- Povolí oznámení dotazů pro vaši databázi.  
  
- Ujistěte se, že ID uživatele používané pro připojení k databázi má potřebná oprávnění.  
  
- Použijte objekt <xref:System.Data.SqlClient.SqlCommand> k provedení platného příkazu SELECT s přidruženým objektem oznámení – buď <xref:System.Data.SqlClient.SqlDependency> nebo <xref:System.Data.Sql.SqlNotificationRequest>.  
  
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
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Oprávnění pro oznamování dotazů  
 Uživatelé, kteří provádějí příkazy požadující oznámení, musí mít oprávnění k přihlášení k odběru databáze oznámení na serveru.  
  
 Kód na straně klienta, který běží v případě částečné důvěryhodnosti, vyžaduje <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Následující kód vytvoří objekt <xref:System.Data.SqlClient.SqlClientPermission> a nastaví <xref:System.Security.Permissions.PermissionState> na <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> vynutí <xref:System.Security.SecurityException> v době běhu, pokud mu nebyla udělena žádná oprávnění volající vyšší v zásobníku volání.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Výběr objektu oznámení  
 Rozhraní API pro oznamování dotazů poskytuje dva objekty pro zpracování oznámení: <xref:System.Data.SqlClient.SqlDependency> a <xref:System.Data.Sql.SqlNotificationRequest>. Obecně platí, že většina aplikací non-ASP.NET by měla používat objekt <xref:System.Data.SqlClient.SqlDependency>. ASP.NET aplikace by měly používat vyšší úroveň <xref:System.Web.Caching.SqlCacheDependency>, která zabalí <xref:System.Data.SqlClient.SqlDependency> a poskytuje rozhraní pro správu oznámení a objektů mezipaměti.  
  
### <a name="using-sqldependency"></a>Použití třídy SqlDependency  
 Aby bylo možné použít <xref:System.Data.SqlClient.SqlDependency>, musí být pro SQL Server databázi povoleny Service Broker a uživatelé musí mít oprávnění k přijímání oznámení. Service Broker objekty, jako je například fronta oznámení, jsou předdefinovány.  
  
 Kromě toho <xref:System.Data.SqlClient.SqlDependency> automaticky spouští pracovní vlákno pro zpracování oznámení, která jsou publikována do fronty. také analyzuje zprávu Service Broker a zpřístupňuje informace jako data argumentu události. <xref:System.Data.SqlClient.SqlDependency> musí být inicializována voláním metody `Start` k vytvoření závislosti na databázi. Toto je statická metoda, kterou je třeba volat pouze jednou při inicializaci aplikace pro každé požadované připojení databáze. Metoda `Stop` by měla být volána při ukončení aplikace pro každé připojení závislosti, které bylo provedeno.  
  
### <a name="using-sqlnotificationrequest"></a>Použití SqlNotificationRequest  
 Naproti tomu <xref:System.Data.Sql.SqlNotificationRequest> vyžaduje, abyste sami implementovali celou naslouchající infrastrukturu. Kromě toho musí být definované všechny podpůrné Service Broker objekty, jako jsou fronty, služby a typy zpráv podporované frontou. Tento ruční přístup je užitečný v případě, že vaše aplikace vyžaduje speciální oznamovací zprávy nebo oznamovací chování nebo pokud je vaše aplikace součástí větší Service Broker aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Oznámení pro dotazy na SQL Serveru](query-notifications-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
