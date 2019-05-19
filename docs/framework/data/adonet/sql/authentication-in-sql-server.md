---
title: Ověřování v SQL Serveru
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 94de49fe89f2b7f4aabaade624e960202f9973bf
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877451"
---
# <a name="authentication-in-sql-server"></a>Ověřování v SQL Serveru
SQL Server podporuje dva režimy ověřování, režimu ověřování Windows a ve smíšeném režimu.  
  
- Ověřování Windows je výchozí a se často označuje jako integrované zabezpečení tento model zabezpečení systému SQL Server je těsně integrovaná se službami Windows. Určité účty uživatelů a skupin Windows jsou důvěryhodní k přihlášení k SQL serveru. Není potřeba k dispozici další přihlašovací údaje Windows, kteří již byl ověřen.  
  
- Ve smíšeném režimu podporuje ověřování Windows a SQL Server. Dvojice název a heslo uživatele zachovány v rámci SQL serveru.  
  
> [!IMPORTANT]
>  Doporučujeme používat ověřování Windows, kdykoli je to možné. Ověřování Windows k ověřování uživatelů v systému SQL Server používá řadu šifrované zprávy. Při přihlášení serveru SQL Server jsou používány, jsou předány přihlašovací jména systému SQL Server a šifrovaná hesla přes síť, což je méně bezpečné.  
  
 Uživatelé s ověřováním Windows, se už přihlásili do Windows a není nutné samostatně přihlášení k SQL serveru. Následující `SqlConnection.ConnectionString` Určuje ověřování Windows, aniž by uživatelé museli zadat uživatelské jméno nebo heslo.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Přihlášení se liší od uživatele databáze. Přihlašovací jména nebo skupiny Windows je nutné mapovat do databáze uživatelů nebo rolí v samostatné operaci. Pak udělíte oprávnění uživatelům nebo rolí pro přístup k objektům v databázi.  
  
## <a name="authentication-scenarios"></a>Scénáře ověřování  
 Ověřování Windows je obvykle nejlepší volbou v těchto situacích:  
  
- Je řadič domény.  
  
- Aplikace a databáze jsou ve stejném počítači.  
  
- Používáte instanci systému SQL Server Express nebo LocalDB.  
  
 Přihlášení serveru SQL Server se často používají v následujících situacích:  
  
- Pokud máte pracovní skupiny.  
  
- Uživatelé připojovat z jiné, nedůvěryhodné domény.  
  
- Internetové aplikace, jako je například technologie ASP.NET.  
  
> [!NOTE]
>  Zadání ověřování Windows nezakáže přihlášení serveru SQL Server. Použít příkazu ALTER LOGIN zakázat [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkaz Zakázat přihlášení serveru SQL Server s vysokou úrovní oprávnění.  
  
## <a name="login-types"></a>Typy přihlášení  
 SQL Server podporuje tři typy přihlášení:  
  
- Místní uživatelský účet Windows nebo důvěryhodné doméně účtu. SQL Server závisí na Windows k ověření Windows uživatelské účty.  
  
- Skupiny Windows. Udělení přístupu ke skupině Windows uděluje přístup ke všem přihlášení uživatele Windows, které jsou členy skupiny.  
  
- Přihlašovací jméno SQL serveru. SQL Server uchovává uživatelské jméno a hodnotu hash hesla v hlavní databázi pomocí interní ověřovacích metod ověření pokusů o přihlášení.  
  
> [!NOTE]
>  SQL Server poskytuje přihlašovací údaje vytvořené z certifikáty nebo asymetrické klíče, které se používají pouze pro podepisování kódu. Nelze použít pro připojení k SQL serveru.  
  
## <a name="mixed-mode-authentication"></a>Ověřování ve smíšeném režimu  
 Pokud je potřeba použít ve smíšeném režimu ověřování, musíte vytvořit přihlášení systému SQL Server, které jsou uloženy v systému SQL Server. Potom je nutné zadat uživatelské jméno SQL serveru a heslo v době běhu.  
  
> [!IMPORTANT]
>  SQL Server nainstaluje s přihlášením SQL serveru s názvem `sa` (zkratka "správce"). Přiřaďte silné heslo, které `sa` přihlášení a nepoužívají `sa` přihlášení v aplikaci. `sa` Přihlášení se mapuje `sysadmin` pevné role serveru, který má neodvolatelnou přihlašovací údaje pro správu na celý server. Neplatí žádné limity pro možné škody, pokud útočník získá přístup jako správce systému. Všichni členové Windows `BUILTIN\Administrators` skupinu (skupiny local Administrators) jsou členy `sysadmin` roli ve výchozím nastavení, ale můžete odebrat z této role.  
  
 SQL Server poskytuje mechanismy zásady hesla Windows pro přihlášení serveru SQL Server při spuštění [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] nebo novější verze. Zásady pro složitost hesla jsou navrženy pro odstraňovat útoky hrubou silou zvýšením počtu možných hesel. SQL Server můžete použít stejné zásady složitosti a vypršení platnosti používané [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to hesel použitých v SQL serveru.  
  
> [!IMPORTANT]
>  Zřetězení řetězců připojení ze vstupu uživatele můžete nechat je zranitelný vůči útoku prostřednictvím injektáže řetězec připojení. Použití <xref:System.Data.SqlClient.SqlConnectionStringBuilder> k vytváření syntakticky správný připojovací řetězce v době běhu. Další informace najdete v tématu [tvůrci připojovacích řetězců](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Objekty zabezpečení](/sql/relational-databases/security/authentication-access/principals-database-engine)|Popisuje přihlášení a další hlavní služby zabezpečení v systému SQL Server.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Připojení ke zdroji dat](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Připojovací řetězce](../../../../../docs/framework/data/adonet/connection-strings.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
