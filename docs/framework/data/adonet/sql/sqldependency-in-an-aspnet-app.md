---
title: SqlDependency v aplikaci ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 67c1307bb18b3e86e05b56f4853a39f6831ab9cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780286"
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency v aplikaci ASP.NET
Příklad v této části ukazuje, jak používat <xref:System.Data.SqlClient.SqlDependency> nepřímo s využitím technologie ASP.NET <xref:System.Web.Caching.SqlCacheDependency> objektu. <xref:System.Web.Caching.SqlCacheDependency> Objektu používá <xref:System.Data.SqlClient.SqlDependency> naslouchat oznámením a správně aktualizovat mezipaměť.  
  
> [!NOTE]
>  Vzorový kód předpokládá, že jste povolili oznámení dotazů spuštěním skriptů v [povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>O ukázkové aplikace  
 Ukázková aplikace používá k zobrazení informací o produktu z jediné stránce technologie ASP.NET **AdventureWorks** databázi SQL serveru <xref:System.Web.UI.WebControls.GridView> ovládacího prvku. Když se stránka načte, zapíše kód aktuální čas <xref:System.Web.UI.WebControls.Label> ovládacího prvku. Potom definuje <xref:System.Web.Caching.SqlCacheDependency> objekt a nastaví vlastnosti pro <xref:System.Web.Caching.Cache> objekt pro uložení data v mezipaměti pro až 3 minuty. Kód poté se připojí k databázi a načítá data. Při načtení stránky a je spuštěná aplikace ASP.NET se načtou data z mezipaměti, což můžete ověřit tak poznamenat, že čas na stránce nemění. Pokud data monitoruje změní, ASP.NET zruší platnost mezipaměti a znovu vytvořit `GridView` ovládací prvek s čerstvá data, času zobrazeného v aktualizaci `Label` ovládacího prvku.  
  
## <a name="creating-the-sample-application"></a>Vytvoření ukázkové aplikace  
 Postupujte podle těchto kroků k vytvoření a spuštění ukázkové aplikace:  
  
1. Vytvoření nového webu technologie ASP.NET.  
  
2. Přidat <xref:System.Web.UI.WebControls.Label> a <xref:System.Web.UI.WebControls.GridView> ovládacího prvku na stránku Default.aspx.  
  
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
  
4. Přidejte následující kód na stránce `Page_Load` události:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. Přidat dvě metody helper `GetConnectionString` a `GetSQL`. Připojovací řetězec, který je definován používá integrované zabezpečení. Budete muset ověřit, že používáte účet nemá oprávnění potřebné databáze a že ukázkovou databázi **AdventureWorks**, je oznámení jsou povolená.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Testování aplikace  
 Aplikace ukládá do mezipaměti, data zobrazená ve webovém formuláři a aktualizuje se každé 3 minuty, pokud neexistuje žádná aktivita. Pokud dojde ke změně k databázi, do mezipaměti se aktualizují okamžitě. Spuštění aplikace ze sady Visual Studio, který načte stránku do prohlížeče. Čas aktualizace mezipaměti zobrazí označuje při poslední aktualizaci do mezipaměti. Počkejte tři minuty a potom aktualizujte stránku, příčinou událost zpětného odeslání dojde k. Všimněte si, že došlo ke změně času zobrazeného na stránce. Pokud stránku aktualizujete za méně než tři minuty, času zobrazeného na stránce zůstanou stejné.  
  
 Nyní aktualizovat data v databázi, pomocí příkazu jazyka Transact-SQL, aktualizovat a aktualizujte stránku. Času zobrazeného teď označuje, že mezipaměť byl aktualizován novými daty z databáze. Všimněte si, že i když se aktualizuje mezipaměť, času zobrazeného na stránce se nezmění, dokud dojde k události postback.  
  
## <a name="see-also"></a>Viz také:

- [Oznámení pro dotazy na SQL Serveru](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
