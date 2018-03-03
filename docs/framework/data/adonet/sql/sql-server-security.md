---
title: SQL Server Security
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: c186b25aeaa42b7285316d7bc9de913dd7b89af7
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2018
---
# <a name="sql-server-security"></a>SQL Server Security
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] má řadu funkcí, které podporují vytváření aplikace zabezpečené databáze.  
  
 Společné aspekty zabezpečení, jako je krádež dat nebo vandalismu, platí bez ohledu na verzi [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] používáte. Integritu dat by měly být považovány porušení zabezpečení. Pokud data nejsou chráněna, je možné, že by se mohly stát nemá, pokud je povoleno manipulaci s daty ad hoc a data jsou nechtěně nebo neoprávněnému změnit nesprávné hodnoty nebo odstraní celý. Navíc často existují právní požadavky, které, musí být použito, jako je například správné úložiště důvěrné informace. Ukládání některé druhy osobních údajů je proscribed zcela, v závislosti na právního, které se vztahují v konkrétní příslušnosti.  
  
 Každá verze nástroje [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] má jiné bezpečnostní funkce, stejně jako jednotlivé verze Windows, s novější verze s rozšířené funkce přes předchozí. Je důležité si uvědomit, že funkce zabezpečení samostatně nemůže zaručit k aplikaci zabezpečené databáze. Každá databáze aplikace je jedinečné požadavky, prostředí pro spuštění, model nasazení, fyzické umístění a počet uživatelů. Některé aplikace, které jsou v oboru místní může potřebovat pouze minimální zabezpečení, zatímco další místní aplikace nebo aplikace nasazené prostřednictvím Internetu může vyžadovat přísné bezpečnostní opatření a průběžné monitorování a vyhodnocení.  
  
 Požadavky na zabezpečení [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] databáze aplikace považovat v době návrhu, ne jako chodím. Vyhodnocení hrozby již v rané fázi v cyklu vývoje vám dává možnost omezit možné škody, bez ohledu na ohrožení zabezpečení související s je zjištěna.  
  
 I když je počáteční návrh aplikace zvuku, může vznikat nové hrozby jako zpracovaní systému. Tím, že vytvoříte více řádků obrany okolo vaší databáze, můžete minimalizovat škody si způsobilo porušení zabezpečení. Vaše první linií obrany je snížit útoku podle nikdy k udělení více oprávnění, než jsou nezbytně nutné.  
  
 Témata v této části stručně popisují funkce zabezpečení v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] , které jsou relevantní pro vývojáře, s odkazy na související témata v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] na webu knihy Online a dalším prostředkům, které poskytují podrobnější pokrytí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Popisuje funkce architektuře a zabezpečení [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 Obsahuje témata pro technologii ADO.NET pojednávající o různé scénáře zabezpečení aplikací a [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] aplikace.  
  
 [Zabezpečení SQL Serveru Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 Popisuje aspekty zabezpečení [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express.  
  
## <a name="related-sections"></a>Související oddíly  
[Centrum zabezpečení pro databázový stroj systému SQL Server a databázi Azure SQL](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Popisuje důležité informace o zabezpečení pro SQL Server a databáze SQL Azure.

[Důležité informace o zabezpečení pro instalaci serveru SQL](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
Popisuje aspekty zabezpečení, které je třeba zvážit před instalací systému SQL Server.

## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
