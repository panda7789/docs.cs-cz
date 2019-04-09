---
title: Přehled zabezpečení SQL Serveru
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: de0c79a95a786f33b05c88ce4ed298837f2a6923
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148587"
---
# <a name="overview-of-sql-server-security"></a>Přehled zabezpečení SQL Serveru
Strategie defense-in-depth s překrývajícími se vrstvy zabezpečení, je nejlepší způsob, jak čítač bezpečnostní hrozby. SQL Server poskytuje zabezpečení architektura, která je navržena k umožnění správci databází a vývojářům vytvářet zabezpečené databázových aplikací a čelit hrozbám. Každá verze systému SQL Server se zvýšil na předchozích verzích systému SQL Server se zavedením nové funkce a funkce. V poli se však nedodává zabezpečení. Každá aplikace je jedinečný v jeho požadavky na zabezpečení. Vývojáři musí pochopit, jaké kombinace funkce a funkce jsou nejvhodnější pro čítače známými hrozbami a předvídat hrozeb, které mohou nastat v budoucnu.  
  
 Instance systému SQL Server obsahuje hierarchickou kolekci entit, spouští se serverem. Každý server obsahuje několik databází a každá databáze obsahuje kolekci zabezpečitelných objektů. Všechny zabezpečitelné SQL Server má přidruženou *oprávnění* , která lze udělit práva *hlavní*, což je jednotlivé, skupiny nebo proces udělen přístup k systému SQL Server. Zabezpečení systému SQL Server spravuje přístup k zabezpečenému entity prostřednictvím *ověřování* a *autorizace*.  
  
-   Ověřování je proces přihlášení k systému SQL Server, pomocí kterého požaduje objekt zabezpečení přístup odesláním přihlašovací údaje, které vyhodnotí server. Ověření určí identitu uživatele nebo proces ověřuje.  
  
-   Autorizace je procesu, který určuje přístup k objektu zabezpečení zabezpečitelné prostředky a operace, které jsou povoleny pro tyto prostředky.  
  
 Témata v této části se týkají Základy zabezpečení systému SQL Server, poskytuje odkazy na kompletní dokumentaci v příslušné verzi systému SQL Server Books Online.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Ověřování v SQL Serveru](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 Popisuje přihlášení a ověření v systému SQL Server a poskytuje odkazy na další zdroje informací.  
  
 [Serverové a databázové role na SQL Serveru](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 Popisuje pevné role serveru a databáze, vlastní databázové role a předdefinované účty a obsahuje odkazy na další zdroje informací.  
  
 [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 Popisuje objekt oddělení vlastnictví a schéma uživatele a poskytuje odkazy na další zdroje informací.  
  
 [Autorizace a oprávnění na SQL Serveru](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 Popisuje udělení oprávnění pomocí principu nejnižší úrovně oprávnění a poskytuje odkazy na další zdroje informací.  
  
 [Šifrování dat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 Popisuje možnosti šifrování dat v SQL serveru a obsahuje odkazy na další zdroje informací.  
  
 [Zabezpečení integrace CLR na SQL Serveru](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 Obsahuje odkazy na prostředky zabezpečení integrace CLR.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server – zabezpečení](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
