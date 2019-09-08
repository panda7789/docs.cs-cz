---
title: SQL Server – zabezpečení
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: c5fd9cc82a3b1e4ffa217d65c542376fe067db06
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791630"
---
# <a name="sql-server-security"></a>SQL Server – zabezpečení
SQL Server má mnoho funkcí, které podporují vytváření zabezpečených databázových aplikací.  
  
 Běžné požadavky na zabezpečení, jako je například krádež dat nebo neoprávněné používání, platí bez ohledu na verzi SQL Server, kterou používáte. Integrita dat by měla být také považována za bezpečnostní problém. Pokud nejsou data chráněná, může se stát, že se bezcenné, jestli je povolená manipulace s daty ad hoc, a data se nechtěně nebo se zlými úmysly nezměnily na nesprávné hodnoty nebo zcela odstranila. Kromě toho existují často zákonné požadavky, které musí být dodrženy, jako je třeba správné úložiště důvěrných informací. Ukládání některých druhů osobních údajů je zcela zapsaných v závislosti na právních předpisech, které platí pro konkrétní předpis.  
  
 Každá verze SQL Server má jiné funkce zabezpečení, stejně jako každá verze Windows s novějšími verzemi, které mají vyšší funkčnost než dříve. Je důležité pochopit, že funkce zabezpečení samostatně nezaručují zabezpečenou databázovou aplikaci. Každá databázová aplikace je jedinečná ve svých požadavcích, spouštěcím prostředí, modelu nasazení, fyzickém umístění a naplnění uživatele. Některé aplikace, které jsou místní v oboru, můžou potřebovat jenom minimální zabezpečení, zatímco jiné místní aplikace nebo aplikace nasazené přes Internet můžou vyžadovat přísné bezpečnostní míry a průběžné monitorování a vyhodnocení.  
  
 Požadavky na zabezpečení aplikace SQL Server Database by měly být zváženy v době návrhu, nikoli jako dodatečně. Vyhodnocování hrozeb v rané fázi vývoje vám dává možnost zmírnit potenciální škodu při zjištění ohrožení zabezpečení.  
  
 I v případě, že počáteční návrh aplikace je zvuk, můžou se nové hrozby vymezit tím, jak se systém vyvíjí. Vytvořením více řádků obrany v databázi můžete minimalizovat škody způsobené porušením zabezpečení. První linií obrany je snížit prostor pro útoky tím, že nikdy neudělíte více oprávnění, než je nezbytně nutné.  
  
 Témata v této části stručně popisují funkce zabezpečení v SQL Server, které jsou relevantní pro vývojáře, s odkazy na relevantní témata v SQL Server Books Online a další materiály, které poskytují podrobnější pokrytí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled zabezpečení SQL Serveru](overview-of-sql-server-security.md)  
 Popisuje architekturu a funkce zabezpečení SQL Server.  
  
 [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)  
 Obsahuje témata pojednávající o různých scénářích zabezpečení aplikací pro aplikace ADO.NET a SQL Server.  
  
 [Zabezpečení SQL Serveru Express](sql-server-express-security.md)  
 Popisuje požadavky na zabezpečení pro SQL Server Express.  
  
## <a name="related-sections"></a>Související oddíly  
[Security Center pro databázový stroj SQL Server a Azure SQL Database](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Popisuje bezpečnostní opatření pro SQL Server a Azure SQL Database.

[Požadavky na zabezpečení pro instalaci SQL Server](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
Popisuje bezpečnostní otázky, které je třeba zvážit před instalací SQL Server.

## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [SQL Server a ADO.NET](index.md)
