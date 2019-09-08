---
title: Zabezpečení SQL Serveru Express
ms.date: 03/30/2017
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.openlocfilehash: 55f1d141e50ed7afd851d7330cfaf2e3b6380f18
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791687"
---
# <a name="sql-server-express-security"></a>Zabezpečení SQL Serveru Express
Edice Microsoft SQL Server Express (SQL Server Express) je založená na Microsoft SQL Server a podporuje většinu funkcí databázového stroje. Je navržený tak, aby nepostradatelné funkce a připojení k síti byly ve výchozím nastavení vypnuté. Tím se snižuje plocha dostupná pro útok uživatele se zlými úmysly.  
  
 SQL Server Express je obvykle nainstalován jako pojmenovaná instance. Výchozí název instance je `SQLExpress`. Pojmenovaná instance je identifikována síťovým názvem počítače a názvem instance, kterou zadáte během instalace.  
  
## <a name="network-access"></a>Přístup k síti  
 Z bezpečnostních důvodů jsou síťové protokoly ve výchozím nastavení v SQL Server Express zakázané. Tím zabráníte útokům z externích uživatelů, kteří by mohli ohrozit počítač, který je hostitelem instance SQL Server Express. Musíte explicitně povolit připojení k síti a spustit službu SQL Server Browser pro připojení k instanci SQL Server Express z jiného počítače.  
  
 Po povolení připojení k síti má instance SQL Server Express stejné požadavky na zabezpečení jako ostatní edice SQL Server.  
  
## <a name="user-instances"></a>Uživatelské instance  
 Uživatelská instance je samostatná instance SQL Server Express databázového stroje, který je generován nadřazenou instancí SQL Server Express. Hlavním cílem uživatelské instance je dovolit uživatelům, kteří používají Windows pod uživatelským účtem s minimálním oprávněním, mít oprávnění správce systému (`sysadmin`) na instanci SQL Server Express v místním počítači. Uživatelské instance nejsou určeny pro uživatele, kteří jsou správci systému na svých počítačích.  
  
 Uživatelská instance je vygenerována z primární instance SQL Server nebo SQL Server Express jménem uživatele. Spouští se jako proces uživatele v kontextu zabezpečení systému Windows uživatele, nikoli jako služba. Přihlášení SQL Server nejsou povolena. podporují se jenom přihlašovací údaje systému Windows. Tím se zabrání tomu, aby software spuštěný na uživatelské instanci prováděl změny v rámci systému, které by uživatel neměl mít oprávnění k provedení. Uživatelská instance je také označována jako podřízená nebo klientská instance a je někdy označována pomocí zkratky RANU ("spustit jako normální uživatel").  
  
 Jednotlivé uživatelské instance jsou izolované od své nadřazené instance a z jiných instancí uživatelů spuštěných ve stejném počítači. Databáze nainstalované v uživatelských instancích jsou otevřené jenom v jednouživatelském režimu. k nim se nelze připojit více uživatelů. Replikace, distribuované dotazy a vzdálená připojení jsou pro uživatelské instance zakázané. Při připojení k uživatelské instanci nemají uživatelé žádná zvláštní oprávnění pro nadřazenou instanci SQL Server Express.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o SQL Server Express najdete v následujících zdrojích informací.  
  
|||  
|-|-|  
|[Online knihy pro edice Microsoft SQL Server 2005 Express](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|Dokončete dokumentaci pro SQL Server 2005 Express Edition.|  
|[Uživatelské instance pro uživatele bez oprávnění správce](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100)) v SQL Server Knihy online|Popisuje, jak vytvořit a nasadit uživatelské instance.|  
|[Uživatelské instance SQL Serveru Express](sql-server-express-user-instances.md)|Popisuje schopnosti uživatelské instance v aplikaci ADO.NET. Poskytuje informace o tom, jak povolit uživatelské instance, připojení k uživatelské instanci pomocí <xref:System.Data.SqlClient.SqlConnection>scénářů, uživatelské instance a scénářů uživatelské instance.|  
  
## <a name="see-also"></a>Viz také:

- [SQL Server – zabezpečení](sql-server-security.md)
- [Uživatelské instance SQL Serveru Express](sql-server-express-user-instances.md)
- [Přehled ADO.NET](../ado-net-overview.md)
