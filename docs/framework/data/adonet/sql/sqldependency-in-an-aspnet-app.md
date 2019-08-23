---
title: SqlDependency v aplikaci ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: a93cb9da44985fa29a4975875564b384117ce76f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938457"
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency v aplikaci ASP.NET
Příklad v této části ukazuje, jak nepřímo použít <xref:System.Data.SqlClient.SqlDependency> objekt ASP.NET. <xref:System.Web.Caching.SqlCacheDependency> <xref:System.Web.Caching.SqlCacheDependency> Objekt<xref:System.Data.SqlClient.SqlDependency> používá k naslouchání oznámení a k správné aktualizaci mezipaměti.  
  
> [!NOTE]
> Vzorový kód předpokládá, že jste povolili oznámení dotazů spuštěním skriptů v části [Povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>O ukázkové aplikaci  
 Ukázková aplikace používá jednu webovou stránku ASP.NET k zobrazení informací o produktu z databáze **AdventureWorks** SQL Server v <xref:System.Web.UI.WebControls.GridView> ovládacím prvku. Při načtení stránky kód zapíše aktuální čas do <xref:System.Web.UI.WebControls.Label> ovládacího prvku. Pak definuje <xref:System.Web.Caching.SqlCacheDependency> objekt a nastaví vlastnosti <xref:System.Web.Caching.Cache> objektu pro uložení dat mezipaměti až po dobu tří minut. Kód se pak připojí k databázi a načte data. Po načtení stránky a spuštění aplikace ASP.NET se načtou data z mezipaměti, kterou můžete ověřit tak, že si myslíte, že se čas na stránce nemění. Pokud se data monitorují, ASP.NET zruší platnost mezipaměti a znovu naplní `GridView` ovládací prvek novými daty a aktualizuje čas zobrazený `Label` v ovládacím prvku.  
  
## <a name="creating-the-sample-application"></a>Vytvoření ukázkové aplikace  
 Pomocí těchto kroků vytvořte a spusťte ukázkovou aplikaci:  
  
1. Vytvořte nový web ASP.NET.  
  
2. Přidejte ovládací<xref:System.Web.UI.WebControls.GridView> prvek aanastránkuDefault.aspx.<xref:System.Web.UI.WebControls.Label>  
  
3. Otevřete modul třídy stránky a přidejte následující direktivy:  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. Do `Page_Load` události stránky přidejte následující kód:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. Přidejte dvě pomocné metody `GetConnectionString` a. `GetSQL` Připojovací řetězec definovaný pomocí integrovaného zabezpečení. Musíte ověřit, že účet, který používáte, má potřebná databázová oprávnění a že má ukázková databáze **AdventureWorks**povolená oznámení.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Testování aplikace  
 Aplikace ukládá do mezipaměti data zobrazená ve webovém formuláři a aktualizuje je každé tři minuty, pokud neexistuje žádná aktivita. Pokud dojde ke změně v databázi, mezipaměť se okamžitě aktualizuje. Spusťte aplikaci ze sady Visual Studio, která načte stránku do prohlížeče. Zobrazený čas aktualizace mezipaměti indikuje, kdy se mezipaměť naposledy aktualizovala. Počkejte tři minuty a pak aktualizujte stránku, což způsobí, že dojde k události zpětného odeslání. Všimněte si, že se čas zobrazený na stránce změnil. Pokud stránku aktualizujete za méně než tři minuty, čas zobrazený na stránce zůstane stejný.  
  
 Teď aktualizujte data v databázi pomocí příkazu Transact-SQL UPDATE a aktualizujte stránku. Čas zobrazený nyní indikuje, že se mezipaměť aktualizovala novými daty z databáze. Všimněte si, že i když je mezipaměť aktualizována, čas zobrazený na stránce se nemění, dokud nedojde k události zpětného odeslání.  
  
## <a name="see-also"></a>Viz také:

- [Oznámení pro dotazy na SQL Serveru](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
