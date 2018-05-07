---
title: Ověřování v systému SQL Server
ms.date: 03/30/2017
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 8fc6f17cd008fe24e041c52b4e5ee8fd4d261f40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="authentication-in-sql-server"></a>Ověřování v systému SQL Server
Systém SQL Server podporuje dva režimy ověřování a smíšený režim a režim ověřování systému Windows.  
  
-   Ověřování systému Windows je výchozí a se často označuje jako integrované zabezpečení vzhledem k tomu, že tento model zabezpečení systému SQL Server je úzce integrovaná s Windows. Konkrétní účty uživatelů a skupin systému Windows jsou důvěryhodní k přihlášení k systému SQL Server. Uživatelé systému Windows, kteří již byl ověřen nemají k dispozici další přihlašovací údaje.  
  
-   Smíšený režim podporuje ověřování Windows a systémem SQL Server. Dvojice název a heslo uživatele se udržují v systému SQL Server.  
  
> [!IMPORTANT]
>  Doporučujeme použít ověřování systému Windows, pokud je to možné. Ověřování systému Windows používá řadu šifrované zprávy k ověřování uživatelů v systému SQL Server. Když se použije přihlášení serveru SQL, systému SQL Server přihlašovacích jmen a hesel se předávají v síti, který je méně bezpečné.  
  
 Pomocí ověřování systému Windows uživatelé jsou již přihlášeni k systému Windows a nemají samostatně přihlásit k systému SQL Server. Následující `SqlConnection.ConnectionString` Určuje ověřování systému Windows bez nutnosti uživatelské jméno nebo heslo.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Přihlášení se liší od uživatele databáze. Přihlášení nebo skupiny systému Windows je nutné mapovat do databáze uživatelů nebo rolí v samostatné operace. Pak udělíte oprávnění uživatelům nebo role pro přístup k databázové objekty.  
  
## <a name="authentication-scenarios"></a>Scénáře ověřování  
 Ověřování systému Windows je většinou nejlepší volbou v následujících situacích:  
  
-   Je řadič domény.  
  
-   Aplikace a databáze jsou ve stejném počítači.  
  
-   Používáte instance systému SQL Server Express nebo LocalDB.  
  
 Přihlášení serveru SQL se často používají v následujících situacích:  
  
-   Pokud máte pracovní skupiny.  
  
-   Uživatelé připojit z jiné, nedůvěryhodné domény.  
  
-   Internetové aplikace, jako například [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Zadání ověřování systému Windows není zakázána přihlášení serveru SQL. Použijte příkazu ALTER LOGIN zakázat [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkaz Zakázat přihlášení serveru SQL vysokou úrovní oprávnění.  
  
## <a name="login-types"></a>Typy přihlášení  
 Systém SQL Server podporuje tři typy přihlášení:  
  
-   Místní uživatelský účet systému Windows nebo důvěryhodné doméně účtu. SQL Server závisí na systému Windows k ověření uživatelské účty systému Windows.  
  
-   Skupina systému Windows. Udělení přístupu ke skupině Windows uděluje přístup do všech přihlášení uživatele systému Windows, které jsou členy skupiny.  
  
-   Přihlášení systému SQL Server. SQL Server ukládá uživatelské jméno a hodnotu hash hesla v hlavní databázi pomocí interní ověřování metody ověření pokusů o přihlášení.  
  
> [!NOTE]
>  SQL Server poskytuje přihlášení vytvořené z certifikáty nebo asymetrické klíče, které se používají jenom pro podepisování kódu. Nelze použít pro připojení k systému SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Smíšený režim ověřování  
 Pokud je potřeba použít smíšený režim ověřování, musíte vytvořit přihlášení systému SQL Server, které jsou uloženy v systému SQL Server. Pak budete muset zadat uživatelské jméno SQL serveru a heslo v době běhu.  
  
> [!IMPORTANT]
>  SQL Server nainstaluje s přihlašovacími údaji systému SQL Server s názvem `sa` (zkratka "systému správce"). Přiřaďte silné heslo, které `sa` přihlášení a nepoužívejte `sa` přihlášení ve vaší aplikaci. `sa` Přihlášení se mapuje `sysadmin` pevné role serveru, který má neodvolatelný pověření správce pro celý server. Neexistují žádná omezení týkající se možné škody, pokud útočník získá přístup jako správce systému. Všichni členové Windows `BUILTIN\Administrators` skupinu (skupiny local Administrators) jsou členy `sysadmin` roli ve výchozím nastavení, ale můžete odebrat z této role.  
  
 SQL Server poskytuje Windows heslo zásad mechanismy pro přihlášení serveru SQL, když je spuštěn na [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] nebo novější verze. Zásady pro složitost hesla jsou navrženy pro odstraňovat útoky hrubou silou zvýšením počtu možná hesla. Systému SQL Server můžete použít stejné zásady složitost a vypršení platnosti použít v [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] hesla použit v rámci systému SQL Server.  
  
> [!IMPORTANT]
>  Zřetězení řetězců připojení ze vstupu uživatele můžete ponechat vám bude zranitelný vůči útoku vkládání připojovací řetězec. Použití <xref:System.Data.SqlClient.SqlConnectionStringBuilder> vytvořit syntakticky připojovací řetězce v době běhu. Další informace najdete v tématu [Tvůrci řetězců pro připojení](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Objekty](http://msdn.microsoft.com/library/bb543165.aspx) v Online knihách serveru SQL|Popisuje přihlášení a další objekty zabezpečení v systému SQL Server.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Připojení ke zdroji dat](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Připojovací řetězce](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
