---
title: SQL Server Common Language Runtime Integration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 06c1f2909658c140b1ad84f3b0ed5d3abdafb6c6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-common-language-runtime-integration"></a>SQL Server Common Language Runtime Integration
SQL Server 2005 zavedl integrace součást společné language runtime (CLR) rozhraní .NET Framework pro Microsoft Windows. To znamená, že můžete napsat uložené procedury, triggery, uživatelem definované typy, uživatelem definované funkce, uživatelem definovaných agregacích a streamování funkce vracející tabulku pomocí žádný jazyk rozhraní .NET Framework, včetně Microsoft Visual Basic .NET a společnosti Microsoft Visual C#. <xref:Microsoft.SqlServer.Server> Obor názvů obsahuje sadu nové aplikačními programovacími rozhraními (API) tak, aby spravovaný kód můžete spolupracovat s prostředím Microsoft SQL Server.  
  
 Tato část popisuje funkce a chování, které jsou specifické pro systému SQL Server common language runtime (CLR) integrace a konkrétní rozšíření v procesu systému SQL Server pro technologii ADO.NET.  
  
 Tato část poskytuje jenom dostatek informací, abyste mohli začít programování s integrace modulu CLR SQL serveru a není určen jako komplexní. Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
1.  [Běžné koncepty programování integrace Language Runtime (CLR)](http://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Úvod k integraci modulu CLR na SQL Serveru](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 Poskytuje úvod do integrace modulu CLR SQL serveru. Obsahuje odkazy na další témata.  
  
 [Uživatelem definované funkce CLR](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 Popisuje, jak k implementaci a použití různých typů CLR funkce: agregační funkce vracející tabulku, skalární a uživatelem definované.  
  
 [Uživatelem definované typy CLR](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 Popisuje, jak k implementaci a použití uživatelem definované typy CLR. Obsahuje odkazy na další témata.  
  
 [Uložené procedury CLR](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 Popisuje, jak k implementaci a použití CLR uložené procedury. Obsahuje odkazy na další témata.  
  
 [Aktivační procedury CLR](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 Popisuje, jak implementovat a použít aktivační procedury modulu CLR. Obsahuje odkazy na další témata.  
  
 [Kontextové připojení](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 Popisuje připojení kontextu.  
  
 [Chování ADO.NET specifické pro proces SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 Popisuje konkrétní rozšíření systému SQL Server v rámci procesu ADO.NET a připojení kontextu. Obsahuje odkazy na další témata.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
