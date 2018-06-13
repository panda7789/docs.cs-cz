---
title: Přehled zabezpečení SQL serveru
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: 84b6724417d03a30c131700e197744839d3a020d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362231"
---
# <a name="overview-of-sql-server-security"></a>Přehled zabezpečení SQL serveru
Strategie obrany zabezpečení s překrývajícími se úrovní zabezpečení, je nejlepší způsob, jak čítač bezpečnostní hrozby. SQL Server poskytuje zabezpečení architekturu, která je navržena k umožnění správce databáze a vývojářům vytvářet aplikace zabezpečené databáze a čítač hrozeb. Každá verze nástroje SQL Server je vylepšený v dřívějších verzích systému SQL Server se zavedením nové funkce a funkce. V poli se však nedodává zabezpečení. Každá aplikace je jedinečné požadavky zabezpečení. Vývojáři muset vědět, která kombinace funkce a funkce jsou nejvhodnější pro čítače známé hrozby a předvídat hrozeb, které může způsobit v budoucnu.  
  
 Instance systému SQL Server obsahuje hierarchické kolekci entit, spouští se serverem. Každý server více databází, a každou databázi obsahuje kolekci zabezpečitelné objekty. Každý Server SQL zabezpečitelné přidruženy *oprávnění* , lze udělit *hlavní*, což je jednotlivých, skupiny nebo proces udělen přístup k systému SQL Server. Zabezpečení systému SQL Server spravuje přístup k zabezpečenému entity prostřednictvím *ověřování* a *autorizace*.  
  
-   Ověřování je proces přihlášení k systému SQL Server, pomocí kterého objekt zabezpečení požaduje přístup odesláním přihlašovací údaje, které vyhodnotí server. Ověřování prokáže identity uživatele nebo procesu ověřovaného.  
  
-   Autorizace je proces pro určení toho, že zabezpečitelné prostředky, ke kterým přístup objekt zabezpečení a operací, které jsou povoleny pro tyto prostředky.  
  
 Témata v této části se týkají Základy zabezpečení systému SQL Server, že poskytuje odkazy na kompletní dokumentaci v příslušné verzi systému SQL Server Books Online.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Ověřování v SQL Serveru](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 Popisuje přihlášení a ověřování v systému SQL Server a poskytuje odkazy na další zdroje.  
  
 [Serverové a databázové role na SQL Serveru](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 Popisuje pevné role serveru a databáze, vlastní databázové role a integrované účty a poskytuje odkazy na další zdroje informací.  
  
 [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 Popisuje objekt oddělení vlastnictví a schéma uživatele a poskytuje odkazy na další zdroje.  
  
 [Autorizace a oprávnění na SQL Serveru](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 Popisuje udělení oprávnění pomocí Princip nejnižších nutných oprávnění a poskytuje odkazy na další zdroje.  
  
 [Šifrování dat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 Popisuje možnosti šifrování dat v systému SQL Server a poskytuje odkazy na další zdroje.  
  
 [Zabezpečení integrace CLR na SQL Serveru](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 Obsahuje odkazy na zdroje zabezpečení integrace modulu CLR.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server – zabezpečení](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
