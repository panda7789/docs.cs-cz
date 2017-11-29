---
title: "Oznámení dotazu v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 854407d2e6d1341d5917cc78664c1f653e55fa35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="query-notifications-in-sql-server"></a>Oznámení dotazu v systému SQL Server
Oznámení dotazů postavená na infrastruktuře služby Service Broker, umožňují aplikacím být upozorněni, když se data změnila. Tato funkce je obzvláště užitečná pro aplikace, které poskytují mezipaměť informací z databáze, např. webové aplikace a musí být upozorněni, když se změní zdrojová data.  
  
 Můžete implementovat oznámení dotazů pomocí ADO.NET třemi způsoby:  
  
1.  Nízké úrovně implementace poskytuje `SqlNotificationRequest` třída, která zveřejňuje funkce na straně serveru, umožňuje spouštění příkazu se žádost o oznámení.  
  
2.  Poskytuje základní implementaci `SqlDependency` třídy, která je třída, která poskytuje vysokou úroveň abstrakce oznámení funkcí mezi zdrojová aplikace a SQL Server, což umožňuje použít ke zjištění změny v závislosti Server. Ve většině případů je to nejjednodušší a co nejúčinnější způsob, jak využívat funkce oznámení systému SQL Server ve spravované klientským aplikacím pomocí zprostředkovatele dat .NET Framework pro SQL Server.  
  
3.  Kromě toho webové aplikace vyvíjené v technologii ASP.NET 2.0 nebo novější můžete použít `SqlCacheDependency` pomocné třídy.  
  
 Oznámení dotazů se používají pro aplikace, které potřebují k aktualizaci zobrazí nebo ukládá do mezipaměti v reakci na změny v základních datech. Microsoft SQL Server umožňuje aplikacím rozhraní .NET Framework pro odeslání příkazu serveru SQL Server a žádost o oznámení, pokud provádění stejný příkaz vytvoří liší od nastavení nejdřív načíst sad výsledků dotazu. Vygenerovat na serveru se posílají oznámení prostřednictvím fronty zpracovat později.  
  
 Můžete nastavit oznámení pro vyberte a příkazy EXECUTE. Při použití příkazu EXECUTE, zaregistruje systému SQL Server oznámení pro příkaz proveden místo příkaz EXECUTE sám sebe. Příkaz musí splňovat požadavky a omezení pro příkaz SELECT. Když příkaz, který registruje oznámení obsahuje více než jednoho příkazu, databázový stroj vytvoří oznámení pro každý příkaz v dávce.  
  
 Pokud vyvíjíte aplikace kde potřebujete spolehlivé dílčí sekundu oznámení při změně dat, přečtěte si oddíly **plánování strategie efektivní oznámení dotazu** a **alternativy k dotazu Oznámení** v [plánování oznámení](http://go.microsoft.com/fwlink/?LinkId=211984) téma v SQL Server Books Online. Další informace o oznámení dotazů a SQL Server Service Broker najdete v následujících odkazů na témata v SQL Server Books Online.  
  
 **SQL Server Books Online**  
  
-   [Pomocí oznámení dotazů](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [Vytváření dotazu pro oznámení](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Služba Service Broker](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [Service Broker vývojáře informační středisko](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Vývoj (Service Broker)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 Popisuje, jak používat oznámení dotazu, včetně požadavků pro povolení a jejich používání.  
  
 [SqlDependency v aplikaci ASP.NET](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 Ukazuje, jak používat oznámení dotazu z aplikace technologie ASP.NET.  
  
 [Detekce změn s SqlDependency](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 Ukazuje, jak zjistit, kdy výsledky dotazu se bude lišit od těch, které původně obdrželi.  
  
 [Provádění SqlCommand s SqlNotificationRequest](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Ukazuje, konfigurace <xref:System.Data.SqlClient.SqlCommand> objekt pro práci s oznámení o dotazu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Popisuje <xref:System.Data.Sql.SqlNotificationRequest> třídy a všechny její členy.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Popisuje <xref:System.Data.SqlClient.SqlDependency> třídy a všechny její členy.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Popisuje <xref:System.Web.Caching.SqlCacheDependency> třídy a všechny její členy.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
