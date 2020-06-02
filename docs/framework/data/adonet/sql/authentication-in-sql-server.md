---
title: Ověřování v SQL Serveru
description: Přečtěte si o ověřování pomocí SQL Server pro ADO.NET, včetně režimu ověřování systému Windows a smíšeného režimu.
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: e9915598acfbdefb59069d6a9c6ef4b7c824e4c6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286543"
---
# <a name="authentication-in-sql-server"></a>Ověřování v SQL Serveru
SQL Server podporuje dva režimy ověřování, režim ověřování systému Windows a smíšený režim.  
  
- Ověřování systému Windows je výchozí a často se označuje jako integrované zabezpečení, protože tento model zabezpečení SQL Server je úzce integrovaný se systémem Windows. Pro přihlášení k SQL Server jsou pro konkrétní účty uživatelů a skupin systému Windows důvěryhodné. Uživatelé systému Windows, kteří už byli ověřeni, nemusejí mít k dispozici další přihlašovací údaje.  
  
- Smíšený režim podporuje ověřování jak v systému Windows, tak pomocí SQL Server. Páry uživatelské jméno a heslo se udržují v SQL Server.  
  
> [!IMPORTANT]
> Pokud je to možné, doporučujeme používat ověřování systému Windows. Ověřování systému Windows používá k ověřování uživatelů v SQL Server řadu šifrovaných zpráv. Při SQL Server používání přihlašovacích jmen SQL Server přihlašovací jména a šifrovaná hesla se předávají přes síť, což snižuje jejich zabezpečení.  
  
 Při ověřování Windows se uživatelé už přihlásili k Windows a nemusíte se k SQL Server přihlašovat samostatně. Toto `SqlConnection.ConnectionString` Určuje ověřování systému Windows, aniž by uživatelé museli zadat uživatelské jméno nebo heslo.  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> Přihlášení se liší od uživatelů databáze. Přihlašovací jména nebo skupiny systému Windows je nutné namapovat na uživatele databáze nebo role v samostatné operaci. Pak uživatelům nebo rolím udělíte oprávnění pro přístup k objektům databáze.  
  
## <a name="authentication-scenarios"></a>Scénáře ověřování  
 Ověřování systému Windows je obvykle nejlepší volbou v následujících situacích:  
  
- Existuje řadič domény.  
  
- Aplikace a databáze jsou ve stejném počítači.  
  
- Používáte instanci SQL Server Express nebo LocalDB.  
  
 Přihlašovací jména SQL Server se často používají v následujících situacích:  
  
- Máte-li pracovní skupinu.  
  
- Uživatelé se připojují z různých nedůvěryhodných domén.  
  
- Internetové aplikace, například ASP.NET.  
  
> [!NOTE]
> Zadání ověřování systému Windows nezakáže SQL Server přihlašovacích údajů. Pomocí příkazu ALTER LOGIN DISABLE příkaz Transact-SQL zakážete SQL Server přihlašovacích údajů s vysokou úrovní oprávnění.  
  
## <a name="login-types"></a>Typy přihlášení  
 SQL Server podporuje tři typy přihlášení:  
  
- Místní uživatelský účet systému Windows nebo účet důvěryhodné domény. SQL Server spoléhá na Windows k ověření uživatelských účtů systému Windows.  
  
- Skupina systému Windows. Udělení přístupu skupině systému Windows uděluje přístup všem uživatelským přihlašováním systému Windows, která jsou členy skupiny.  
  
- SQL Server přihlášení. SQL Server ukládá uživatelské jméno i hodnotu hash hesla v hlavní databázi, a to pomocí metod interního ověřování pro ověření pokusů o přihlášení.  
  
> [!NOTE]
> SQL Server poskytuje přihlášení vytvořená z certifikátů nebo asymetrických klíčů, které se používají jenom pro podepisování kódu. Nelze je použít pro připojení k SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Ověřování ve smíšeném režimu  
 Pokud je potřeba použít smíšený režim ověřování, musíte vytvořit SQL Server přihlašovacích údajů, které jsou uložené v SQL Server. Pak je nutné zadejte SQL Server uživatelské jméno a heslo v době běhu.  
  
> [!IMPORTANT]
> SQL Server se instaluje s přihlašovacím SQL Server s názvem `sa` (zkratka "správce systému"). Přiřaďte přihlášení silné heslo `sa` a nepoužívejte `sa` přihlašovací údaje ve vaší aplikaci. `sa`Přihlašovací údaje se mapují na `sysadmin` pevnou roli serveru, která má nevratná pověření pro správu na celém serveru. V případě, že útočník získá přístup jako správce systému, neexistují žádná omezení na potenciální škodu. Všichni členové `BUILTIN\Administrators` skupiny Windows (skupina místních správců) jsou `sysadmin` ve výchozím nastavení členy této role, ale je možné je z této role odebrat.  
  
 SQL Server poskytuje mechanismy zásad hesel Windows pro přihlášení SQL Server. Zásady složitosti hesla jsou navržené tak, aby se zvýšil počet útoků hrubou silou, a to zvýšením počtu možných hesel. SQL Server můžou použít stejné zásady složitosti a vypršení platnosti jako hesla používaná v SQL Server.  
  
> [!IMPORTANT]
> Zřetězení připojovacích řetězců ze vstupu uživatele může opustit útok prostřednictvím injektáže připojovacího řetězce. Použijte <xref:System.Data.SqlClient.SqlConnectionStringBuilder> k vytvoření syntakticky platných připojovacích řetězců v době běhu. Další informace najdete v tématu [tvůrci připojovacích řetězců](../connection-string-builders.md).  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Objekty zabezpečení](/sql/relational-databases/security/authentication-access/principals-database-engine)|Popisuje přihlašovací údaje a další objekty zabezpečení v SQL Server.|  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Připojení ke zdroji dat](../connecting-to-a-data-source.md)
- [Připojovací řetězce](../connection-strings.md)
- [Přehled ADO.NET](../ado-net-overview.md)
