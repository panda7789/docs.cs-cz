---
title: Oznámení pro dotazy na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: a68c01c7db782a9904ba36edec9d13332cab39a9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645667"
---
# <a name="query-notifications-in-sql-server"></a>Oznámení pro dotazy na SQL Serveru
Oznámení dotazů založené na řešení infrastruktury služby Service Broker, povolit aplikace, která vás upozorní, když se data změnila. Tato funkce je zvláště užitečná pro aplikace, které poskytují mezipaměť informací z databáze, jako je například v případě webové aplikace a nutné upozornit, když je změněna zdrojová data.  
  
 Oznámení dotazů pomocí ADO.NET můžete implementovat třemi způsoby:  
  
1. Nízké úrovně implementace je poskytován `SqlNotificationRequest` třídy, která poskytuje funkce na straně serveru, můžete k provedení příkazu se žádost o oznámení.  
  
2. Poskytuje základní implementaci `SqlDependency` třídu, která je třída, která poskytuje vysokou úroveň abstrakce oznámení funkcí mezi zdrojová aplikace a SQL Server, můžete použít k detekci změn v závislosti Server. Ve většině případů toto je nejjednodušší a nejúčinnější způsob využití možnosti oznámení systému SQL Server ve spravované klientským aplikacím pomocí zprostředkovatele dat .NET Framework pro SQL Server.  
  
3. Kromě toho webových aplikací vytvořených pomocí technologie ASP.NET 2.0 nebo novější můžete použít `SqlCacheDependency` pomocné třídy.  
  
 Oznámení dotazů se používají pro aplikace, které je potřeba aktualizovat zobrazí nebo ukládá do mezipaměti v reakci na změny v podkladových datech. Microsoft SQL Server umožňuje aplikacím rozhraní .NET Framework odeslat příkaz k systému SQL Server a žádost o oznámení, pokud spuštění stejného příkazu byste mohli vytvořit sad výsledků dotazu liší od původně načten. Vygenerovat na serveru oznámení se posílají do fronty mohly být zpracovány později.  
  
 Můžete nastavit oznámení pro výběr a spouštění příkazů. Při použití příkazu EXECUTE, SQL Server zaregistruje oznámení pro příkaz provedený místo samotného příkaz EXECUTE. Příkaz musí splňovat požadavky a omezení pro příkaz SELECT. Pokud příkaz, který registruje upozornění obsahuje více než jeden výraz, databázový stroj vytvoří upozornění pro každý příkaz v dávce.  
  
 Pokud vyvíjíte aplikaci kdy potřebujete spolehlivé sekunda oznámení při změně dat, přečtěte si oddíly **plánování strategie efektivní oznámení dotazů** a **alternativy k dotazu Oznámení** v [plánování oznámení](https://go.microsoft.com/fwlink/?LinkId=211984) téma v SQL Server Books Online. Další informace o oznámení dotazů a SQL Server Service Broker viz následující odkazy na témata v SQL Server Books Online.  
  
 **Dokumentaci k SQL serveru**  
  
- [Použití oznámení dotazů](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Vytvoření dotazu pro oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Vývoj (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Informační středisko pro vývojáře služby Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Příručka pro vývojáře (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 Popisuje, jak používat oznámení dotazů, včetně požadavků na povolení a jejich používání.  
  
 [SqlDependency v aplikaci ASP.NET](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 Ukazuje, jak pomocí dotazu oznámení z aplikace technologie ASP.NET.  
  
 [Detekce změn pomocí SqlDependency](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 Ukazuje, jak zjistit, že výsledky dotazu se bude lišit od těch, které původně obdrželi.  
  
 [Provádění SqlCommand pomocí SqlNotificationRequest](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Ukazuje, konfigurace <xref:System.Data.SqlClient.SqlCommand> objektu pro práci s oznámení o dotazu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Popisuje <xref:System.Data.Sql.SqlNotificationRequest> třídy a všechny její členy.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Popisuje <xref:System.Data.SqlClient.SqlDependency> třídy a všechny její členy.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Popisuje <xref:System.Web.Caching.SqlCacheDependency> třídy a všechny její členy.  
  
## <a name="see-also"></a>Viz také:

- [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
