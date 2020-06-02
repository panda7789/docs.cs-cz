---
title: Oznámení pro dotazy na SQL Serveru
description: Naučte se používat oznámení dotazů k upozorňování aplikací na změnu dat v SQL Server databázi, například na aktualizace zobrazení aplikace.
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 1351c83b6cc5837115321d53e8779c0f364c3099
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286220"
---
# <a name="query-notifications-in-sql-server"></a>Oznámení pro dotazy na SQL Serveru
Oznámení dotazů, která jsou postavená na Service Broker infrastruktuře, umožňují aplikacím upozorňování na změnu dat. Tato funkce je zvláště užitečná pro aplikace, které poskytují mezipaměť informací z databáze aplikace, jako je například webová aplikace, a musí být upozorněni, když se změní zdrojová data.  
  
 Existují tři způsoby, jak můžete implementovat oznámení dotazů pomocí ADO.NET:  
  
1. Implementace nízké úrovně je poskytována `SqlNotificationRequest` třídou, která zveřejňuje na straně serveru, a umožňuje tak spustit příkaz s požadavkem na oznámení.  
  
2. Implementace vysoké úrovně je poskytována `SqlDependency` třídou, což je třída, která poskytuje souhrnnou abstrakci funkcí oznamování mezi zdrojovou aplikací a SQL Server a umožňuje použít závislost ke zjištění změn na serveru. Ve většině případů je to nejjednodušší a nejúčinnější způsob, jak využít SQL Serverch oznámení pomocí spravovaných klientských aplikací pomocí .NET Framework Zprostředkovatel dat pro SQL Server.  
  
3. Kromě toho webové aplikace sestavené pomocí ASP.NET 2,0 nebo novější mohou používat `SqlCacheDependency` pomocné třídy.  
  
 Oznámení dotazů se používají pro aplikace, které vyžadují aktualizaci zobrazení nebo ukládání do mezipaměti v reakci na změny v podkladových datech. Microsoft SQL Server umožňuje aplikacím .NET Framework odeslat příkaz do SQL Server a požádat o oznámení při spuštění stejného příkazu by vzniklé sady výsledků liší od původně načtených. Oznámení vytvořená na serveru jsou odesílána prostřednictvím front ke zpracování později.  
  
 Můžete nastavit oznámení pro příkazy SELECT a EXECUTE. Při použití příkazu EXECUTE SQL Server zaregistruje oznámení pro provedení příkazu, nikoli samotný příkaz EXECUTE. Příkaz musí splňovat požadavky a omezení příkazu SELECT. Když příkaz, který zaregistruje oznámení, obsahuje více než jeden příkaz, vytvoří databázový stroj oznámení pro každý příkaz v dávce.  
  
 Pokud vyvíjíte aplikaci, kde při změně dat potřebujete spolehlivá e-mailová oznámení, přečtěte si část **Plánování efektivní strategie oznámení dotazů** a **alternativy k dotazům na oznámení** v článku [plánování oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) . Další informace o oznámeních a SQL Server Service Brokerech dotazů naleznete v následujících odkazech na články v dokumentaci k SQL Server.  
  
 **Dokumentace SQL Serveru**  
  
- [Pomocí oznámení dotazů](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Vytvoření dotazu pro oznámení](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Vývoj (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [InfoCenter pro vývojáře Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Příručka pro vývojáře (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Povolení oznámení dotazů](enabling-query-notifications.md)  
 Popisuje, jak používat oznámení dotazů, včetně požadavků na jejich povolení a používání.  
  
 [SqlDependency v aplikaci ASP.NET](sqldependency-in-an-aspnet-app.md)  
 Ukazuje, jak používat oznámení dotazů z aplikace ASP.NET.  
  
 [Detekce změn pomocí SqlDependency](detecting-changes-with-sqldependency.md)  
 Ukazuje, jak rozpoznat, kdy se výsledky dotazu budou lišit od původně přijatých.  
  
 [Provádění SqlCommand pomocí SqlNotificationRequest](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Ukazuje konfiguraci <xref:System.Data.SqlClient.SqlCommand> objektu pro práci s oznámením dotazu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Popisuje <xref:System.Data.Sql.SqlNotificationRequest> třídu a všechny její členy.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Popisuje <xref:System.Data.SqlClient.SqlDependency> třídu a všechny její členy.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Popisuje <xref:System.Web.Caching.SqlCacheDependency> třídu a všechny její členy.  
  
## <a name="see-also"></a>Viz také

- [SQL Server a ADO.NET](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
