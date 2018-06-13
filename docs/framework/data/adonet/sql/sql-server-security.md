---
title: Zabezpečení SQL serveru
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: 418dbd3e677619721b841736f5b4c1b423ada94b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364204"
---
# <a name="sql-server-security"></a>Zabezpečení SQL serveru
Systému SQL Server obsahuje mnoho funkcí, které podporují vytváření aplikací pro zabezpečené databáze.  
  
 Společné aspekty zabezpečení, jako je krádež dat nebo vandalismu, platí bez ohledu na verzi systému SQL Server, kterou používáte. Integritu dat by měly být považovány porušení zabezpečení. Pokud data nejsou chráněna, je možné, že by se mohly stát nemá, pokud je povoleno manipulaci s daty ad hoc a data jsou nechtěně nebo neoprávněnému změnit nesprávné hodnoty nebo odstraní celý. Navíc často existují právní požadavky, které, musí být použito, jako je například správné úložiště důvěrné informace. Ukládání některé druhy osobních údajů je proscribed zcela, v závislosti na právního, které se vztahují v konkrétní příslušnosti.  
  
 Každou verzi systému SQL Server má jiné bezpečnostní funkce, stejně jako jednotlivé verze Windows, s novější verze s rozšířené funkce přes předchozí. Je důležité si uvědomit, že funkce zabezpečení samostatně nemůže zaručit k aplikaci zabezpečené databáze. Každá databáze aplikace je jedinečné požadavky, prostředí pro spuštění, model nasazení, fyzické umístění a počet uživatelů. Některé aplikace, které jsou v oboru místní může potřebovat pouze minimální zabezpečení, zatímco další místní aplikace nebo aplikace nasazené prostřednictvím Internetu může vyžadovat přísné bezpečnostní opatření a průběžné monitorování a vyhodnocení.  
  
 V době návrhu, ne jako chodím měli zvážit požadavky na zabezpečení aplikace databáze systému SQL Server. Vyhodnocení hrozby již v rané fázi v cyklu vývoje vám dává možnost omezit možné škody, bez ohledu na ohrožení zabezpečení související s je zjištěna.  
  
 I když je počáteční návrh aplikace zvuku, může vznikat nové hrozby jako zpracovaní systému. Tím, že vytvoříte více řádků obrany okolo vaší databáze, můžete minimalizovat škody si způsobilo porušení zabezpečení. Vaše první linií obrany je snížit útoku podle nikdy k udělení více oprávnění, než jsou nezbytně nutné.  
  
 Témata v této části stručně popisují funkce zabezpečení v systému SQL Server, které jsou relevantní pro vývojáře, s odkazy na související témata v SQL Server Books Online a dalším prostředkům, které poskytují podrobnější pokrytí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Popisuje funkce architektuře a zabezpečení systému SQL Server.  
  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 Obsahuje témata pojednávající o různé scénáře zabezpečení aplikací pro aplikace ADO.NET a SQL Server.  
  
 [Zabezpečení SQL Serveru Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 Popisuje důležité informace o zabezpečení pro SQL Server Express.  
  
## <a name="related-sections"></a>Související oddíly  
[Centrum zabezpečení pro databázový stroj systému SQL Server a databázi Azure SQL](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Popisuje důležité informace o zabezpečení pro SQL Server a databáze SQL Azure.

[Důležité informace o zabezpečení pro instalaci serveru SQL](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
Popisuje aspekty zabezpečení, které je třeba zvážit před instalací systému SQL Server.

## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
