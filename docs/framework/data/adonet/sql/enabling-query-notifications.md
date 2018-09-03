---
title: Povolení oznámení dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: c164490464d839dacefaf570c8956bf15caeb7de
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480539"
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
  
 **SQL Server Books Online**  
  
-   [Vytvoření dotazu pro oznámení](https://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Důležité informace o zabezpečení pro službu Service Broker](https://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [Zabezpečení a ochranu (Service Broker)](https://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [Důležité informace o zabezpečení pro oznámení služby](https://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [Oprávnění pro dotaz oznámení](https://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [Mezinárodní důležité informace týkající se služby Service Broker](https://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [Aspekty návrhu řešení (Service Broker)](https://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [Informační středisko pro vývojáře služby Service Broker](https://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Příručka pro vývojáře (Service Broker)](https://msdn.microsoft.com/library/bb522908.aspx)  
  
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
  
## <a name="see-also"></a>Viz také  
 [Oznámení pro dotazy na SQL Serveru](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
