---
title: "N-vrstvá a vzdálené aplikace s dotazy LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f44b6da8ecc8d036a9550856f71b2981770e9478
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N-vrstvá a vzdálené aplikace s dotazy LINQ to SQL
Můžete vytvořit n vrstvá nebo vícevrstvé aplikace, které používají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Obvykle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kontextu dat, tříd entit a konstrukce logiku dotazu se nacházejí ve střední vrstvě jako vrstva přístupu k datům (DAL). Obchodní logika a žádná dočasnou data můžou se implementovat zcela v částečné třídy a metody entity a kontext dat, nebo se dá implementovat v samostatné třídy.  
  
 Klient nebo prezentační vrstva volá metody na střední vrstvě pro vzdálené rozhraní a v této vrstvě DAL, budou spuštěny dotazy nebo uložené procedury, které jsou mapované na <xref:System.Data.Linq.DataContext> metody. Střední vrstva vrátí data o klientům obvykle jako reprezentace XML entity nebo objekty proxy.  
  
 Ve střední vrstvě jsou entity vytvořené pomocí kontextu dat, která sleduje jejich stavu a spravuje odložené načítání z a odeslání změn do databáze. Tyto entity jsou "připojené" k `DataContext`. Ale po entity, které se odesílají na jinou vrstvu prostřednictvím serializace, budou odpojit, což znamená, že `DataContext` už ke sledování stavu. Entit, které klient odešle zpět aktualizací musí být znovu připojit ke kontextu dat před [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete odeslat provedené změny do databáze. Klient zodpovídá za poskytování původní hodnoty nebo časová razítka zpět střední vrstvy, pokud těch, které jsou požadovány pro optimistickou metodu souběžného kontroly.  
  
 V aplikacích ASP.NET <xref:System.Web.UI.WebControls.LinqDataSource> spravuje většinu této složitost. Další informace najdete v tématu [NIB: Přehled ovládacího prvku webového serveru LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="additional-resources"></a>Další prostředky  
 Další informace o tom, jak implementovat vícevrstvé aplikace, které používají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], najdete v následujících tématech:  
  
-   [Technologie LINQ to SQL N-vrstvá s technologií ASP.NET](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [Technologie LINQ to SQL N-vrstvá s webovými službami](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [Technologie LINQ to SQL s aplikacemi úzce párované Klient Server](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [Implementace vícevrstvé obchodní logiky](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [Operace vytvoření ve víceúrovňových aplikacích (technologie LINQ to SQL) a načtení dat](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 Další informace o vícevrstvé aplikace, které používají datové ADO.NET naleznete v tématu [pracovat s datovými sadami ve vícevrstvých aplikacích](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
