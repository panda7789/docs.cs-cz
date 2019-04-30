---
title: Zabezpečení SQL Serveru Express
ms.date: 03/30/2017
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.openlocfilehash: f4291de89b397f60aedd35b89d6aa3130d348be5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876782"
---
# <a name="sql-server-express-security"></a>Zabezpečení SQL Serveru Express
Microsoft SQL Server Express Edition (SQL Server Express) je založena na systému Microsoft SQL Server a podporuje většinu funkcí databázového stroje. Je navržen tak, aby nepotřebných funkcí a připojení k síti je vypnuto ve výchozím nastavení. To snižuje styčné plochy, které je k dispozici pro uživatele se zlými úmysly útoku.  
  
 SQL Server Express je obvykle nainstalován jako pojmenovanou instanci. Výchozí název instance je `SQLExpress`. Pojmenovaná instance je identifikován síťový název počítače a název instance, který zadáte během instalace.  
  
## <a name="network-access"></a>Přístup k síti  
 Z bezpečnostních důvodů jsou zakázané síťové protokoly v serveru SQL Server Express ve výchozím nastavení. Tím je zabráněno útokům mimo uživatelů, které by mohlo ohrozit počítače, který je hostitelem instance serveru SQL Server Express. Musíte explicitně povolit připojení k síti a spustit službu SQL Server Browser se připojit k instanci systému SQL Server Express z jiného počítače.  
  
 Po povolení připojení k síti na instanci systému SQL Server Express má stejné požadavky na zabezpečení jako v jiných edicích systému SQL Server.  
  
## <a name="user-instances"></a>Uživatelské instance  
 Uživatelské instance se samostatnou instanci SQL Server Express. databázový stroj, který je generován nadřazené instancí systému SQL Server Express. Hlavním cílem uživatelskou instanci je umožnit uživatelům, kteří používají Windows pod účtem uživatele nejnižší oprávnění na správce systému (`sysadmin`) oprávnění na instanci systému SQL Server Express na místním počítači. Uživatelské instance nejsou určené pro uživatele, kteří jsou správci systému ve svých počítačích.  
  
 Z primární instance systému SQL Server nebo SQL Server Express jménem uživatele je vygenerovat uživatelskou instanci. Spuštění jako procesu uživatele v kontextu zabezpečení Windows uživatele, ne jako službu. Přihlášení serveru SQL Server jsou zakázány; jsou podporovány pouze přihlašovací údaje Windows. To zabraňuje spuštění softwaru na uživatelskou instanci v provádění, které uživatel nebude mít oprávnění k provedení změny v celém systému. Uživatelské instance se také označuje jako instance podřízené domény nebo klienta a se někdy označuje na pomocí zkratky RANU ("Spustit jako běžný uživatel").  
  
 Každý uživatel instance je izolovaná od své nadřazené instance a z dalších uživatelské instance běží na stejném počítači. Databáze nainstalovaná v uživatelských instancích jsou otevřeny v režimu jednoho uživatele. více uživatelů se nemůže připojit k nim. Replikace, distribuované dotazy a vzdálená připojení jsou zakázané pro uživatelské instance. Při připojení k uživatelské instanci, uživatelé nebudou mít žádná zvláštní oprávnění v instanci systému SQL Server Express nadřazené.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o systému SQL Server Express viz následující prostředky.  
  
|||  
|-|-|  
|[Microsoft SQL Server 2005 Express Edition Books Online](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|Kompletní dokumentaci k SQL serveru 2005 Express Edition.|  
|[Uživatelské instance nejsou jiným uživatelům dovoleny](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100)) v Online knihách serveru SQL|Popisuje, jak vytvářet a nasazovat uživatelské instance.|  
|[Uživatelské instance SQL Serveru Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|Popisuje možnosti uživatele instance v aplikaci ADO.NET. Poskytuje informace o tom, jak povolit uživatelskou instanci, připojení k uživatelské instanci pomocí <xref:System.Data.SqlClient.SqlConnection>, dobu života instance uživatele a scénáře instance pro uživatele.|  
  
## <a name="see-also"></a>Viz také:

- [SQL Server – zabezpečení](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [Uživatelské instance SQL Serveru Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
