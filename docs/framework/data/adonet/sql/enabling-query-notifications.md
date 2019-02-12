---
title: Povolení oznámení dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 2a711ad4779b8c932436ce1886b1a93dda849a94
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093954"
---
# <a name="enabling-query-notifications"></a>Povolení oznámení dotazů
Aplikace, které využívají oznámení dotazů mají společnou sadu požadavků. Zdroj dat musí být správně nakonfigurované pro podporu oznámení dotazů SQL a uživatel musí mít správná oprávnění na straně klienta i stranu serveru.  
  
 Použití oznámení dotazů, že je nutné:  
  
-   Povolení oznámení dotazů pro vaši databázi.  
  
-   Ujistěte se, že ID uživatele pro připojení k databázi má potřebná oprávnění.  
  
-   Použití <xref:System.Data.SqlClient.SqlCommand> pro spuštění platným příkazem SELECT s objektem přidružené oznámení – buď <xref:System.Data.SqlClient.SqlDependency> nebo <xref:System.Data.Sql.SqlNotificationRequest>.  
  
-   Zadejte kód ke zpracování oznámení, pokud data monitoruje změny.  
  
## <a name="query-notifications-requirements"></a>Požadavky na oznámení dotazů  
 Oznámení dotazů jsou podporována pouze pro příkazy SELECT, které splňují specifické požadavky. Následující tabulka obsahuje odkazy na dokumentaci služby Service Broker a oznámení dotazů v SQL Server Books Online.  
  
 **Dokumentaci k SQL serveru**  
  
-   [Vytvoření dotazu pro oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
-   [Důležité informace o zabezpečení pro službu Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
-   [Zabezpečení a ochranu (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
-   [Důležité informace o zabezpečení pro oznámení služby](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
-   [Oprávnění pro dotaz oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
-   [Mezinárodní důležité informace týkající se služby Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
-   [Aspekty návrhu řešení (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
-   [Informační středisko pro vývojáře služby Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
-   [Příručka pro vývojáře (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Povolení oznámení dotazů pro spuštění vzorového kódu  
 Povolí službu Service Broker na **AdventureWorks** databáze pomocí SQL Server Management Studio, spusťte následující příkaz jazyka Transact-SQL:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Pro ukázky oznámení dotazů spuštěn správně musí provést následující příkazy jazyka Transact-SQL na serveru databáze.  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Oprávnění pro dotaz oznámení  
 Uživatelé, kteří příkazy požadování oznámení musí mít odběru oznámení dotazů databáze oprávnění na serveru.  
  
 Kód na straně klienta, který běží v částečném vztahu důvěryhodnosti situace vyžaduje <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Následující kód vytvoří <xref:System.Data.SqlClient.SqlClientPermission> objekt nastavení <xref:System.Security.Permissions.PermissionState> k <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> Vynutí <xref:System.Security.SecurityException> v době běhu, pokud všichni volající v zásobníku volání vyšší nebyla udělena oprávnění.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Výběr objektu oznámení  
 Rozhraní API oznámení dotazů poskytuje dva objekty se zpracovat oznámení: <xref:System.Data.SqlClient.SqlDependency> a <xref:System.Data.Sql.SqlNotificationRequest>. Obecně platí, by měl používat většina aplikací – technologie ASP.NET <xref:System.Data.SqlClient.SqlDependency> objektu. Aplikace ASP.NET by měly používat vyšší úrovni <xref:System.Web.Caching.SqlCacheDependency>, která zabalí <xref:System.Data.SqlClient.SqlDependency> a poskytuje rozhraní pro správu oznámení a mezipaměti objektů.  
  
### <a name="using-sqldependency"></a>Používání třídy SqlDependency  
 Chcete-li použít <xref:System.Data.SqlClient.SqlDependency>, služba Service Broker musí být povolené pro databázi serveru SQL Server používá, a uživatelé musí mít oprávnění k přijímání oznámení. Objekty služby Service Broker, jako jsou fronty oznámení jsou předdefinovány.  
  
 Kromě toho <xref:System.Data.SqlClient.SqlDependency> automaticky spustí pracovní vlákna ke zpracování oznámení, když jsou odeslány do fronty; také analyzuje zpráv služby Service Broker, odhalení příslušných informací jako argument data události. <xref:System.Data.SqlClient.SqlDependency> musí být inicializován pomocí volání `Start` metodu pro vytvoření závislostí do databáze. Toto je statická metoda, která musí být volána pouze jednou během inicializace aplikace pro každé připojení databáze vyžaduje. `Stop` Metoda by měla být volána při ukončení aplikace pro připojení závislost, která byla vytvořena.  
  
### <a name="using-sqlnotificationrequest"></a>Pomocí SqlNotificationRequest  
 Naproti tomu <xref:System.Data.Sql.SqlNotificationRequest> vyžaduje, abyste implementovat celou infrastrukturu naslouchání sami. Kromě toho musí být definovány všechny podpůrné objekty služby Service Broker například fronty, služby a typy podporovaných fronty zpráv. Tento manuální přístup je užitečný, pokud vaše aplikace vyžaduje speciální oznámení zpráv nebo oznámení chování, nebo pokud vaše aplikace je součástí větší aplikace, které služba Service Broker.  
  
## <a name="see-also"></a>Viz také:
- [Oznámení pro dotazy na SQL Serveru](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
