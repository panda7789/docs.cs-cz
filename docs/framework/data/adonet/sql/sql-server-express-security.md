---
title: "SQL Server Express zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2052656a524eafd7b9a137ac7d5006aba53fc075
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-express-security"></a>SQL Server Express zabezpečení
Microsoft SQL Server Express Edition (SQL Server Express) je založený na systému Microsoft SQL Server a podporuje většinu funkcí databázového stroje. Je navržen tak, aby nepotřebných funkcí a připojení k síti jsou vypnuté ve výchozím nastavení. Tím se snižuje oblasti prostor k útoku uživatelem se zlými úmysly.  
  
 SQL Server Express je obvykle nainstalován jako s názvem instance. Výchozí název instance je `SQLExpress`. Pojmenovaná instance je identifikována síťový název počítače a název instance, který zadáte během instalace.  
  
## <a name="network-access"></a>Přístup k síti  
 Z bezpečnostních důvodů síťové protokoly jsou zakázané ve výchozím nastavení v systému SQL Server Express. Tím je zabráněno útokům od mimo uživatelů, které může dojít k ohrožení počítače, který je hostitelem instance systému SQL Server Express. Musíte explicitně povolit připojení k síti a spustit službu SQL Server Browser a připojit k instanci serveru SQL Server Express z jiného počítače.  
  
 Jakmile je povoleno připojení k síti, do instance systému SQL Server Express má stejné požadavky na zabezpečení jako v jiných edicích systému SQL Server.  
  
## <a name="user-instances"></a>Uživatelské instance  
 Uživatelskou instanci je samostatnou instanci serveru SQL Server Express databázový stroj generovaný nástrojem nadřazená instance systému SQL Server Express. Primární cílem uživatelskou instanci je povolit uživatelům, kteří běží pod účtem uživatele nejnižších oprávnění tak, aby měl správce systému Windows (`sysadmin`) oprávnění v instanci systému SQL Server Express na jejich místním počítači. Uživatelské instance nejsou určeny pro uživatele, kteří jsou správci systému v jejich počítačích.  
  
 Uživatelskou instanci se generují z primární instance serveru SQL Server nebo SQL Server Express jménem uživatele. Spustí jako proces uživatele v kontextu zabezpečení Windows uživatele, ne jako službu. Přihlášení systému SQL Server jsou zakázány na úrovni; jsou podporovány pouze přihlášení systému Windows. Tím se zabrání spuštění softwaru na uživatelskou instanci provádět systémové změny, které uživatel nebude mít oprávnění k provádění. Uživatelskou instanci je také označován jako podřízené domény nebo klienta instance a se někdy označuje pomocí zkratku RANU ("Spustit jako normální uživatelské").  
  
 Každá instance uživatele je izolovaná od její nadřazené instance a z jiné uživatelské instance na stejném počítači spuštěna. Databáze nainstalovaná v uživatelských instancích jsou otevřené v jednouživatelském režimu pouze; několik uživatelů se nemůže připojit k nim. Replikace, distribuované dotazy a vzdálená připojení jsou zakázaná pro uživatelské instance. Když se připojí k uživatelské instanci, uživatelé nebudou mít žádné zvláštní oprávnění na nadřazená instance systému SQL Server Express.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o systému SQL Server Express najdete v následujících materiálech.  
  
|||  
|-|-|  
|[SQL Server Books Online](http://msdn.microsoft.com/library/bb543165.aspx)|Obsahuje dokumentaci k systému SQL Server Express.|  
|[Připojení k SQL serveru Express](http://msdn.microsoft.com/library/ms165679.aspx) v Online knihách serveru SQL|Popisuje, jak používat SQL Server Express Edition v síti.|  
|[Microsoft SQL Server 2005 Express Edition Books Online](http://msdn.microsoft.com/library/ms165706.aspx)|Kompletní dokumentaci pro SQL Server 2005 Express Edition.|  
|[Instance uživatele, kteří nejsou správci](http://msdn.microsoft.com/library/ms143684.aspx) v Online knihách serveru SQL|Popisuje, jak vytvářet a nasazovat uživatelské instance.|  
|[Instance systému SQL Server Express uživatele](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|Popisuje možnosti uživatele instance v aplikaci ADO.NET. Poskytuje informace o tom, jak povolit uživatelskou instanci, připojte se k instanci uživatele pomocí <xref:System.Data.SqlClient.SqlConnection>, uživatelské instance životnost a scénáře instance uživatele.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení SQL serveru](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Instance systému SQL Server Express uživatele](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
