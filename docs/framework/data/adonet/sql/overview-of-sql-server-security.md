---
title: Přehled zabezpečení SQL Serveru
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: adc1ce661d49c468de09552ea36a2cd58d6343f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780934"
---
# <a name="overview-of-sql-server-security"></a>Přehled zabezpečení SQL Serveru
Nejlepší způsob, jak vyhodnotit bezpečnostní hrozby, je důkladná strategie, která má překrývající se vrstvy zabezpečení. SQL Server poskytuje architekturu zabezpečení, která je navržena tak, aby správcům databáze a vývojářům umožnila vytvářet zabezpečené databázové aplikace a hrozby čítačů. Každá verze SQL Server se zlepšila v předchozích verzích SQL Server se zavedením nových funkcí a funkcí. Zabezpečení ale nedodá do boxu. Každá aplikace je v požadavcích na zabezpečení jedinečná. Vývojáři musí pochopit, která kombinace funkcí a funkcí je nejvhodnější pro čítače známých hrozeb, a předvídat hrozby, které mohou nastat v budoucnu.  
  
 Instance SQL Server obsahuje hierarchickou kolekci entit počínaje serverem. Každý server obsahuje více databází a každá databáze obsahuje kolekci zabezpečitelné objekty. Každé SQL Server zabezpečit má přidružená *oprávnění* , která je možné udělit *objektu zabezpečení*, který je individuální, skupinový nebo proces, kterému byl udělen přístup k SQL Server. Rozhraní SQL Server Security Framework spravuje přístup k zabezpečeným entitám prostřednictvím *ověřování* a *autorizace*.  
  
- Ověřování je proces přihlášení k SQL Server tím, že objekt zabezpečení požaduje přístup odesláním přihlašovacích údajů, které server vyhodnocuje. Ověřování vytváří identitu ověřovaného uživatele nebo procesu.  
  
- Autorizace je proces určení, ke kterému zabezpečeným prostředkům má primární přístup a které operace jsou pro tyto prostředky povoleny.  
  
 Témata v této části se týkají SQL Server základy zabezpečení a poskytování odkazů na kompletní dokumentaci v příslušné verzi SQL Server Books Online.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Ověřování v SQL Serveru](authentication-in-sql-server.md)  
 Popisuje přihlašovací údaje a ověřování v SQL Server a poskytuje odkazy na další zdroje informací.  
  
 [Serverové a databázové role na SQL Serveru](server-and-database-roles-in-sql-server.md)  
 Popisuje pevné role serveru a databáze, vlastní databázové role a předdefinované účty a poskytuje odkazy na další zdroje informací.  
  
 [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](ownership-and-user-schema-separation-in-sql-server.md)  
 Popisuje vlastnictví objektu a oddělení uživatelských schémat a poskytuje odkazy na další zdroje.  
  
 [Autorizace a oprávnění na SQL Serveru](authorization-and-permissions-in-sql-server.md)  
 Popisuje udělení oprávnění pomocí principu minimálního oprávnění a poskytuje odkazy na další prostředky.  
  
 [Šifrování dat na SQL Serveru](data-encryption-in-sql-server.md)  
 Popisuje možnosti šifrování dat v SQL Server a poskytuje odkazy na další zdroje informací.  
  
 [Zabezpečení integrace CLR na SQL Serveru](clr-integration-security-in-sql-server.md)  
 Obsahuje odkazy na prostředky zabezpečení integrace modulu CLR.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [SQL Server – zabezpečení](sql-server-security.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](application-security-scenarios-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
