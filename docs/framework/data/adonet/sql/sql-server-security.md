---
title: SQL Server Security
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: 33ec28536115f8571bfda47266ed3b5cad1442bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650579"
---
# <a name="sql-server-security"></a>SQL Server Security
SQL Server obsahuje mnoho funkcí, které podporují vytváření zabezpečených databázových aplikací.  
  
 Častá rozhodnutí při zabezpečení, jako je krádež dat nebo vandalismu, platí bez ohledu na verzi SQL serveru, který používáte. Integritu dat by měly být považovány také potíže se zabezpečením. Pokud data nejsou chráněna, je možné, který může být bezcenné. podstatné, pokud je povoleno manipulace s daty ad hoc a data je neúmyslně nebo záměrně – upravit pomocí nesprávné hodnoty nebo zcela odstraněn. Kromě toho existují často zákonné požadavky, které musí být použito, jako je například správné úložiště důvěrných informací. Ukládání některé druhy osobních údajů je proscribed zcela, v závislosti na tom, které se použijí v konkrétním jurisdikci zákony.  
  
 Každá verze systému SQL Server má různé funkce zabezpečení, stejně jako všechny verze Windows, pomocí novější verze s rozšířené funkce nad ty dřívější. Je důležité pochopit, že aplikace zabezpečené databáze nemůže zaručit, funkce zabezpečení samostatně. Každá databáze aplikace je jedinečné požadavky, prostředí pro spouštění, model nasazení, fyzické umístění a uživatelům. Některé aplikace, které jsou v oboru místní může být nutné jenom minimální zabezpečení, že může vyžadovat další místní aplikace nebo aplikace nasazené přes Internet, přísné bezpečnostní opatření a průběžné monitorování a vyhodnocení.  
  
 Požadavky na zabezpečení databáze aplikace SQL Server je třeba zvážit v době návrhu, ne dodatečně. Vyhodnocování hrozeb v rané fázi vývojového cyklu nabízí možnost omezit možné škody bez ohledu na to zjistí ohrožení zabezpečení.  
  
 I v případě, že je počáteční návrh aplikace zvuku, mohou vzniknout nové hrozby, jak systém vyvíjí. Tím vytvoříte více řádků obrany kolem vaší databáze, můžete minimalizovat škody způsobené porušením zabezpečení. Vaše první linie obrany je omezení možností útoku pomocí nikdy k poskytování více oprávnění než je nezbytně nutné.  
  
 Témata v této části stručně popisují funkce zabezpečení v systému SQL Server, které jsou relevantní pro vývojáře, s odkazy na související témata v SQL Server Books Online a další prostředky, které poskytují podrobnější pokrytí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Popisuje funkce architektuře a zabezpečení systému SQL Server.  
  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 Obsahuje témata pojednávající o různé scénáře zabezpečení aplikací pro aplikace, ADO.NET a systému SQL Server.  
  
 [Zabezpečení SQL Serveru Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 Popisuje aspekty zabezpečení pro SQL Server Express.  
  
## <a name="related-sections"></a>Související oddíly  
[Security Center pro databázový stroj SQL serveru a Azure SQL Database](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Popisuje aspekty zabezpečení pro SQL Server a Azure SQL Database.

[Důležité informace o zabezpečení pro instalaci SQL serveru](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
Popisuje otázky zabezpečení, které je třeba zvážit před instalací systému SQL Server.

## <a name="see-also"></a>Viz také:
- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
