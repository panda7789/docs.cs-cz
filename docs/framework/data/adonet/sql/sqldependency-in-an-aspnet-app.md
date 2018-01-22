---
title: SqlDependency v aplikaci ASP.NET
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
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9e8bbf6d72e07820256f69a06020354ef3ba3977
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency v aplikaci ASP.NET
Příklad v této části ukazuje, jak používat <xref:System.Data.SqlClient.SqlDependency> nepřímo s využitím technologie ASP.NET <xref:System.Web.Caching.SqlCacheDependency> objektu. <xref:System.Web.Caching.SqlCacheDependency> Objektu používá <xref:System.Data.SqlClient.SqlDependency> čekat na oznámení a správně aktualizace mezipaměti.  
  
> [!NOTE]
>  Ukázkový kód předpokládá, že je povoleno oznámení dotazů spuštěním skriptů v [povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>O ukázkové aplikace  
 Ukázková aplikace používá k zobrazení informací o produktu z jediné stránce rozhraní ASP.NET Web **AdventureWorks** databáze systému SQL Server v <xref:System.Web.UI.WebControls.GridView> ovládacího prvku. Když se stránka načte, kód zapíše aktuální čas <xref:System.Web.UI.WebControls.Label> ovládacího prvku. Pak definuje <xref:System.Web.Caching.SqlCacheDependency> objektu a nastaví vlastnosti pro <xref:System.Web.Caching.Cache> objekt pro uložení dat mezipaměti pro až tři minuty. Kód pak připojí k databázi a načte data. Při načtení stránky a aplikace běží ASP.NET načte data z mezipaměti, který lze ověřit poznamenat, že čas na stránce nezmění. Pokud monitorovaných změny dat, technologie ASP.NET zruší platnost mezipaměti a znovu vytvořit `GridView` ovládacího prvku pomocí čerstvá data, času zobrazeného v aktualizaci `Label` ovládacího prvku.  
  
## <a name="creating-the-sample-application"></a>Vytvoření ukázkové aplikace  
 Postupujte podle těchto kroků vytvořte a spusťte ukázkovou aplikaci:  
  
1.  Vytvoření nového webu ASP.NET.  
  
2.  Přidat <xref:System.Web.UI.WebControls.Label> a <xref:System.Web.UI.WebControls.GridView> ovládacího prvku na stránku Default.aspx.  
  
3.  Otevřete modul třídy stránky a přidejte následující direktivy:  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  Přidejte následující kód na stránce `Page_Load` událostí:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  Přidat dvě metody helper, `GetConnectionString` a `GetSQL`. Připojovací řetězec, který je definován používá integrované zabezpečení. Budete muset ověřte, že používáte účet má oprávnění potřebná databáze a že ukázkové databáze **AdventureWorks**, má oznámení povolena. Další informace najdete v tématu [zvláštní aspekty při používání oznámení dotazů](http://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Testování aplikace  
 Aplikace ukládá data zobrazí ve webovém formuláři do mezipaměti a aktualizuje ji každé tři minuty, pokud nebude žádná aktivita. Pokud dojde ke změně do databáze, je mezipaměť aktualizovat okamžitě. Spusťte aplikaci v sadě Visual Studio, který načte stránku do prohlížeče. Doba aktualizace mezipaměti, který se zobrazí označuje při poslední aktualizaci mezipaměti. Počkejte tři minut a pak aktualizujte stránku, způsobuje na událost zpětného volání. Všimněte si, že došlo ke změně času zobrazený na stránce. Pokud obnovíte stránku za méně než tři minuty, zůstane stejný čas na stránku.  
  
 Teď umožňuje aktualizovat data v databázi, pomocí příkazu Transact-SQL, aktualizovat a aktualizujte stránku. Zobrazuje nyní označuje, že do mezipaměti byly aktualizovány s nová data z databáze. Všimněte si, že i když se aktualizuje mezipaměť, času zobrazený na stránce se nezmění, dokud nedojde k události postback.  
  
## <a name="see-also"></a>Viz také  
 [Oznámení pro dotazy na SQL Serveru](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
