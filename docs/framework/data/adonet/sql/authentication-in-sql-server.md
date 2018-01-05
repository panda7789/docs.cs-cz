---
title: "Ověřování v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c462b7c2e888ed0f6394435e0de2131e26dbef08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="authentication-in-sql-server"></a>Ověřování v systému SQL Server
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]podporuje dva režimy ověřování a smíšený režim a režim ověřování systému Windows.  
  
-   Ověřování systému Windows je výchozí a se často označuje jako integrované zabezpečení protože to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] model zabezpečení je úzce integrovaná s Windows. Konkrétní účty uživatelů a skupin systému Windows jsou důvěryhodní k přihlášení k systému SQL Server. Uživatelé systému Windows, kteří již byl ověřen nemají k dispozici další přihlašovací údaje.  
  
-   Smíšený režim podporuje ověřování i v systému Windows a pomocí [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Dvojice název a heslo uživatele se udržují v rámci [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]
>  Doporučujeme použít ověřování systému Windows, pokud je to možné. Ověřování systému Windows používá k ověřování uživatelů v řadu šifrované zprávy [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Když [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] přihlášení používají, [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] přihlašovacích jmen a hesel se předávají v síti, který je méně bezpečné.  
  
 Pomocí ověřování systému Windows, uživatelé jsou již přihlášeni k systému Windows a nemají k přihlášení na samostatně na [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Následující `SqlConnection.ConnectionString` Určuje ověřování systému Windows bez nutnosti uživatelské jméno nebo heslo.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Přihlášení se liší od uživatele databáze. Přihlášení nebo skupiny systému Windows je nutné mapovat do databáze uživatelů nebo rolí v samostatné operace. Pak udělíte oprávnění uživatelům nebo role pro přístup k databázové objekty.  
  
## <a name="authentication-scenarios"></a>Scénáře ověřování  
 Ověřování systému Windows je většinou nejlepší volbou v následujících situacích:  
  
-   Je řadič domény.  
  
-   Aplikace a databáze jsou ve stejném počítači.  
  
-   Používáte-li instanci [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express nebo LocalDB.  
  
 Přihlášení serveru SQL se často používají v následujících situacích:  
  
-   Pokud máte pracovní skupiny.  
  
-   Uživatelé připojit z jiné, nedůvěryhodné domény.  
  
-   Internetové aplikace, jako například [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Určení ověřování systému Windows není zakázána [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] přihlášení. Použijte příkazu ALTER LOGIN zakázat [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkaz zakázat vysoce privilegovaných [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] přihlášení.  
  
## <a name="login-types"></a>Typy přihlášení  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]podporuje tři typy přihlášení:  
  
-   Místní uživatelský účet systému Windows nebo důvěryhodné doméně účtu. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]spoléhá na systému Windows k ověření uživatelské účty systému Windows.  
  
-   Skupina systému Windows. Udělení přístupu ke skupině Windows uděluje přístup do všech přihlášení uživatele systému Windows, které jsou členy skupiny.  
  
-   [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]Přihlaste se. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]ukládá uživatelské jméno a hodnotu hash hesla v hlavní databázi pomocí interní ověřování metody ověření pokusů o přihlášení.  
  
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]poskytuje přihlášení vytvořené z certifikáty nebo asymetrické klíče, které se používají jenom pro podepisování kódu. Nelze se připojit k [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
## <a name="mixed-mode-authentication"></a>Smíšený režim ověřování  
 Pokud je potřeba použít smíšený režim ověřování, musíte vytvořit [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] přihlášení, které jsou uloženy v systému SQL Server. Pak budete muset zadat [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] uživatelské jméno a heslo na dobu běhu.  
  
> [!IMPORTANT]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]nainstaluje se [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] přihlášení s názvem `sa` (zkratka "systému správce"). Přiřaďte silné heslo, které `sa` přihlášení a nepoužívejte `sa` přihlášení ve vaší aplikaci. `sa` Přihlášení se mapuje `sysadmin` pevné role serveru, který má neodvolatelný pověření správce pro celý server. Neexistují žádná omezení týkající se možné škody, pokud útočník získá přístup jako správce systému. Všichni členové Windows `BUILTIN\Administrators` skupinu (skupiny local Administrators) jsou členy `sysadmin` roli ve výchozím nastavení, ale můžete odebrat z této role.  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]poskytuje mechanismy zásady hesel systému Windows pro [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] přihlášení, když je spuštěn na [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] nebo novější verze. Zásady pro složitost hesla jsou navrženy pro odstraňovat útoky hrubou silou zvýšením počtu možná hesla. [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]můžete použít stejné zásady složitost a vypršení platnosti použít v [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] hesla použít uvnitř [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]
>  Zřetězení řetězců připojení ze vstupu uživatele můžete ponechat vám bude zranitelný vůči útoku vkládání připojovací řetězec. Použití <xref:System.Data.SqlClient.SqlConnectionStringBuilder> vytvořit syntakticky připojovací řetězce v době běhu. Další informace najdete v tématu [Tvůrci řetězců pro připojení](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Objekty](http://msdn.microsoft.com/library/bb543165.aspx) v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] zarezervuje Online|Popisuje přihlášení a další objekty zabezpečení v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Připojení ke zdroji dat](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Připojovací řetězce](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
