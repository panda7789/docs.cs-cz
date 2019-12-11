---
title: Ověřování v SQL Serveru
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 0fb92f9e854e2a7a800335390d0195243a749b33
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959967"
---
# <a name="authentication-in-sql-server"></a>Ověřování v SQL Serveru
SQL Server supports two authentication modes, Windows authentication mode and mixed mode.  
  
- Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows. Specific Windows user and group accounts are trusted to log in to SQL Server. Windows users who have already been authenticated do not have to present additional credentials.  
  
- Mixed mode supports authentication both by Windows and by SQL Server. User name and password pairs are maintained within SQL Server.  
  
> [!IMPORTANT]
> We recommend using Windows authentication wherever possible. Windows authentication uses a series of encrypted messages to authenticate users in SQL Server. When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.  
  
 With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server. The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> Logins are distinct from database users. You must map logins or Windows groups to database users or roles in a separate operation. You then grant permissions to users or roles to access database objects.  
  
## <a name="authentication-scenarios"></a>Authentication Scenarios  
 Windows authentication is usually the best choice in the following situations:  
  
- There is a domain controller.  
  
- The application and the database are on the same computer.  
  
- You are using an instance of SQL Server Express or LocalDB.  
  
 SQL Server logins are often used in the following situations:  
  
- If you have a workgroup.  
  
- Users connect from different, non-trusted domains.  
  
- Internet applications, such as ASP.NET.  
  
> [!NOTE]
> Specifying Windows authentication does not disable SQL Server logins. Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.  
  
## <a name="login-types"></a>Login Types  
 SQL Server supports three types of logins:  
  
- A local Windows user account or trusted domain account. SQL Server relies on Windows to authenticate the Windows user accounts.  
  
- Windows group. Granting access to a Windows group grants access to all Windows user logins that are members of the group.  
  
- SQL Server login. SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.  
  
> [!NOTE]
> SQL Server poskytuje přihlášení vytvořená z certifikátů nebo asymetrických klíčů, které se používají jenom pro podepisování kódu. Nelze je použít pro připojení k SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Ověřování ve smíšeném režimu  
 Pokud je potřeba použít smíšený režim ověřování, musíte vytvořit SQL Server přihlašovacích údajů, které jsou uložené v SQL Server. Pak je nutné zadejte SQL Server uživatelské jméno a heslo v době běhu.  
  
> [!IMPORTANT]
> SQL Server se nainstaluje s přihlašovacím SQL Server s názvem `sa` (zkratka "správce systému"). Přiřaďte k `sa` přihlášení silné heslo a nepoužívejte přihlášení `sa` ve vaší aplikaci. `sa` přihlašovací údaje se mapují k pevné roli serveru `sysadmin`, která má neodvolatelná pověření pro správu na celém serveru. V případě, že útočník získá přístup jako správce systému, neexistují žádná omezení na potenciální škodu. Všichni členové skupiny Windows `BUILTIN\Administrators` (skupina místních správců) jsou ve výchozím nastavení členy role `sysadmin`, ale je možné je z této role odebrat.  
  
 SQL Server poskytuje mechanismy zásad hesel Windows pro přihlášení SQL Server. Zásady složitosti hesla jsou navržené tak, aby se zvýšil počet útoků hrubou silou, a to zvýšením počtu možných hesel. SQL Server můžou použít stejné zásady složitosti a vypršení platnosti jako hesla používaná v SQL Server.  
  
> [!IMPORTANT]
> Zřetězení připojovacích řetězců ze vstupu uživatele může opustit útok prostřednictvím injektáže připojovacího řetězce. Použijte <xref:System.Data.SqlClient.SqlConnectionStringBuilder> k vytvoření syntakticky platných připojovacích řetězců v době běhu. Další informace najdete v tématu [tvůrci připojovacích řetězců](../connection-string-builders.md).  
  
## <a name="external-resources"></a>Externí prostředky  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Objekty](/sql/relational-databases/security/authentication-access/principals-database-engine)|Popisuje přihlašovací údaje a další objekty zabezpečení v SQL Server.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Připojení ke zdroji dat](../connecting-to-a-data-source.md)
- [Připojovací řetězce](../connection-strings.md)
- [Přehled ADO.NET](../ado-net-overview.md)
