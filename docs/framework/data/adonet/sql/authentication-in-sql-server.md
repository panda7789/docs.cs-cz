---
title: Ověřování v SQL Serveru
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 49835ebf8ebe4d5bd200ed771477edc8af580b7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794290"
---
# <a name="authentication-in-sql-server"></a>Ověřování v SQL Serveru
SQL Server podporuje dva režimy ověřování, režim ověřování systému Windows a smíšený režim.  
  
- Ověřování systému Windows je výchozí a často se označuje jako integrované zabezpečení, protože tento model zabezpečení SQL Server je úzce integrovaný se systémem Windows. Pro přihlášení k SQL Server jsou pro konkrétní účty uživatelů a skupin systému Windows důvěryhodné. Uživatelé systému Windows, kteří už byli ověřeni, nemusejí mít k dispozici další přihlašovací údaje.  
  
- Smíšený režim podporuje ověřování jak v systému Windows, tak pomocí SQL Server. Páry uživatelské jméno a heslo se udržují v SQL Server.  
  
> [!IMPORTANT]
> Pokud je to možné, doporučujeme používat ověřování systému Windows. Ověřování systému Windows používá k ověřování uživatelů v SQL Server řadu šifrovaných zpráv. Při SQL Server používání přihlašovacích jmen SQL Server přihlašovací jména a šifrovaná hesla se předávají přes síť, což snižuje jejich zabezpečení.  
  
 Při ověřování Windows se uživatelé už přihlásili k Windows a nemusíte se k SQL Server přihlašovat samostatně. `SqlConnection.ConnectionString` Toto Určuje ověřování systému Windows, aniž by uživatelé museli zadat uživatelské jméno nebo heslo.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
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
> SQL Server se instaluje s přihlašovacím SQL Server `sa` s názvem (zkratka "správce systému"). Přiřaďte `sa` přihlášení silné heslo a `sa` nepoužívejte přihlašovací údaje ve vaší aplikaci. Přihlašovací údaje se mapují `sysadmin` na pevnou roli serveru, která má nevratná pověření pro správu na celém serveru. `sa` V případě, že útočník získá přístup jako správce systému, neexistují žádná omezení na potenciální škodu. Všichni členové skupiny Windows `BUILTIN\Administrators` (skupina místních správců) jsou ve výchozím nastavení členy `sysadmin` této role, ale je možné je z této role odebrat.  
  
 SQL Server poskytuje mechanismy zásad hesel Windows pro SQL Server přihlášení, když běží v [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] systému nebo novějších verzích. Zásady složitosti hesla jsou navržené tak, aby se zvýšil počet útoků hrubou silou, a to zvýšením počtu možných hesel. SQL Server můžou použít stejné zásady složitosti a vypršení platnosti [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] používané v k heslům použitým v rámci SQL Server.  
  
> [!IMPORTANT]
> Zřetězení připojovacích řetězců ze vstupu uživatele může opustit útok prostřednictvím injektáže připojovacího řetězce. <xref:System.Data.SqlClient.SqlConnectionStringBuilder> Použijte k vytvoření syntakticky platných připojovacích řetězců v době běhu. Další informace najdete v tématu [tvůrci připojovacích řetězců](../connection-string-builders.md).  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Objekty](/sql/relational-databases/security/authentication-access/principals-database-engine)|Popisuje přihlašovací údaje a další objekty zabezpečení v SQL Server.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Připojení ke zdroji dat](../connecting-to-a-data-source.md)
- [Připojovací řetězce](../connection-strings.md)
- [Přehled ADO.NET](../ado-net-overview.md)
