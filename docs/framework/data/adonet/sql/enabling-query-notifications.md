---
title: "Povolení oznámení dotazů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 473f1ca54d54a1d852edaed424729778e5a7513d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-query-notifications"></a>Povolení oznámení dotazů
Aplikace, které využívají oznámení dotazů mají společnou sadu požadavků. Váš zdroj dat musí být správně nakonfigurované pro podporu oznámení dotazů SQL a uživatel musí mít správná oprávnění na straně klienta a na straně serveru.  
  
 Použití dotazu oznámení, že je potřeba:  
  
-   Povolte oznámení dotazů pro vaši databázi.  
  
-   Ujistěte se, že ID uživatele používané pro připojení k databázi musí mít potřebná oprávnění.  
  
-   Použití <xref:System.Data.SqlClient.SqlCommand> objekt, který chcete spustit platný příkaz SELECT s objektem přidružené oznámení – buď <xref:System.Data.SqlClient.SqlDependency> nebo <xref:System.Data.Sql.SqlNotificationRequest>.  
  
-   Zadejte kód pro zpracování oznámení, pokud data změny.  
  
## <a name="query-notifications-requirements"></a>Požadavky na oznámení dotazu  
 Oznámení dotazů jsou podporována pouze pro příkazy SELECT, které splňují specifické požadavky. Následující tabulka obsahuje odkazy na dokumentaci služby Service Broker a oznámení dotazů v SQL Server Books Online.  
  
 **SQL Server Books Online**  
  
-   [Vytváření dotazu pro oznámení](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Důležité informace o zabezpečení pro služby Service Broker](http://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [Zabezpečení a ochrana (Service Broker)](http://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [Důležité informace o zabezpečení pro služby oznámení](http://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [Oprávnění oznámení dotazu](http://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [Mezinárodní důležité informace týkající se služby Service Broker](http://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [Aspekty návrhu řešení (Service Broker)](http://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [Service Broker vývojáře informační středisko](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Příručka pro vývojáře (Service Broker)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Povolení oznámení dotazů spustit ukázkový kód  
 Chcete-li povolit služby Service Broker na **AdventureWorks** databázi pomocí SQL Server Management Studio, spusťte následující příkaz Transact-SQL:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Pro ukázky oznámení dotazů správné fungování je třeba spustit následující příkazy jazyka Transact-SQL na serveru databáze.  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Oprávnění oznámení dotazu  
 Uživatelé, kteří spuštěním příkazů požadování oznámení musí mít přihlášení k odběru oznámení dotazů v databázi oprávnění na serveru.  
  
 Vyžaduje klienta kód, který běží v situaci, částečné důvěryhodnosti <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Následující kód vytvoří <xref:System.Data.SqlClient.SqlClientPermission> objektu, nastavení <xref:System.Security.Permissions.PermissionState> k <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> Vynutí <xref:System.Security.SecurityException> za běhu, pokud všechny volajícím vyšší v zásobníku volání nebylo uděleno oprávnění.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Výběr objekt oznámení  
 Rozhraní API oznámení dotazů poskytuje dva objekty zpracovat oznámení: <xref:System.Data.SqlClient.SqlDependency> a <xref:System.Data.Sql.SqlNotificationRequest>. Obecně platí, měli používat většinu aplikací technologie ASP.NET <xref:System.Data.SqlClient.SqlDependency> objektu. Aplikace ASP.NET by měly používat vyšší úrovni <xref:System.Web.Caching.SqlCacheDependency>, která zabalí <xref:System.Data.SqlClient.SqlDependency> a poskytuje rozhraní pro správu oznámení a mezipaměti objektů.  
  
### <a name="using-sqldependency"></a>Používání třídy SqlDependency  
 Chcete-li použít <xref:System.Data.SqlClient.SqlDependency>, služby Service Broker musí být povolena pro databázi systému SQL Server používá, a uživatelé musí mít oprávnění pro příjem oznámení. Objekty služby Service Broker, například fronty oznámení jsou předdefinovány.  
  
 Kromě toho <xref:System.Data.SqlClient.SqlDependency> automaticky spustí pracovní vlákna ke zpracování oznámení, když jsou odeslány do fronty, je také analyzuje zpráv služby Service Broker, odhalení příslušných informací jako argument data události. <xref:System.Data.SqlClient.SqlDependency>musí se inicializuje pomocí volání `Start` metodu pro vytvoření závislosti do databáze. Toto je statickou metodu, kterou je lze volat pouze jednou během inicializace aplikace pro každé připojení databáze vyžaduje. `Stop` Metoda by měla být volána při ukončení aplikace pro každé připojení závislost, která byla vytvořená.  
  
### <a name="using-sqlnotificationrequest"></a>Pomocí SqlNotificationRequest  
 Naproti tomu <xref:System.Data.Sql.SqlNotificationRequest> vyžaduje, abyste implementovat celé infrastruktury naslouchání sami. Kromě toho je nutné definovat všechny podpůrné objekty služby Service Broker například fronty, služby a typy nepodporuje fronty zpráv. Tento ruční přístup je užitečné, pokud vaše aplikace vyžaduje speciální oznamující zprávy nebo oznámení chování, nebo pokud je aplikace součástí větší aplikace služby Service Broker.  
  
## <a name="see-also"></a>Viz také  
 [Oznámení pro dotazy na SQL Serveru](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
