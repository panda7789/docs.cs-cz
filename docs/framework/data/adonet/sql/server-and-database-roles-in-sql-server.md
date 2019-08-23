---
title: Serverové a databázové role na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: 97ad04b1d081e5635104bdadb2d1a54402ffcca2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961120"
---
# <a name="server-and-database-roles-in-sql-server"></a>Serverové a databázové role na SQL Serveru
Všechny verze SQL Server používají zabezpečení na základě rolí, které umožňuje přiřadit oprávnění k roli nebo skupině uživatelů namísto jednotlivých uživatelů. Pevné serverové a pevné databázové role mají přiřazenou pevnou sadu oprávnění.  
  
## <a name="fixed-server-roles"></a>Pevné role serveru  
 Pevné role serveru mají pevnou sadu oprávnění a rozsah v rámci serveru. Jsou určené pro použití při správě SQL Server a oprávnění, která jim jsou přiřazena, nelze změnit. Přihlašovací jména se dají přiřadit k pevným rolím serveru bez nutnosti mít uživatelský účet v databázi.  
  
> [!IMPORTANT]
> `sysadmin` Pevná role serveru zahrnuje všechny ostatní role a má neomezený rozsah. Nepřidávejte k této roli objekty zabezpečení, pokud nejsou vysoce důvěryhodné. `sysadmin`Členové role mají neodvolatelná oprávnění správce ve všech databázích a prostředcích serveru.  
  
 Být selektivní, když přidáváte uživatele k pevným rolím serveru. `bulkadmin` Role například umožňuje uživatelům vkládat obsah jakéhokoli místního souboru do tabulky, což by mohlo ohrozit integritu dat. Úplný seznam pevných rolí a oprávnění serveru najdete v tématu SQL Server Books Online.  
  
## <a name="fixed-database-roles"></a>Pevné databázové role  
 Pevné databázové role mají předem definovanou sadu oprávnění, která je navržená tak, aby vám umožnila snadno spravovat skupiny oprávnění. `db_owner` Členové role mohou provádět všechny aktivity konfigurace a údržby databáze.  
  
 Další informace o SQL Server předdefinovaných rolích najdete v následujících zdrojích informací.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Role na úrovni serveru](/sql/relational-databases/security/authentication-access/server-level-roles)|Popisuje pevné role serveru a oprávnění, která jsou k nim přidružená v SQL Server.|  
|[Role na úrovni databáze](/sql/relational-databases/security/authentication-access/database-level-roles)|Popisuje pevné databázové role a oprávnění, která jsou k nim přidružená.|  
  
## <a name="database-roles-and-users"></a>Databázové role a uživatelé  
 Přihlášení musí být mapována na uživatelské účty databáze, aby bylo možné pracovat s databázovými objekty. Uživatele databáze je pak možné přidat k databázovým rolím dědění všech sad oprávnění přidružených k těmto rolím. Je možné udělit všechna oprávnění.  
  
 Také je nutné vzít v `public` úvahu roli `dbo` , `guest` uživatelský účet a účet při návrhu zabezpečení aplikace.  
  
### <a name="the-public-role"></a>Veřejná role  
 `public` Role je obsažena v každé databázi, která zahrnuje systémové databáze. Nelze jej vyřadit a nelze do něj přidávat ani odebírat uživatele. Oprávnění udělená `public` roli jsou děděna všemi ostatními uživateli a rolemi, protože patří do této `public` role ve výchozím nastavení. Udělte `public` pouze oprávnění, která mají mít všichni uživatelé.  
  
### <a name="the-dbo-user-account"></a>Uživatelský účet dbo  
 `dbo`Vlastníkem databáze je uživatelský účet, který má předpokládaná oprávnění k provádění všech aktivit v databázi. Členové pevné role serveru jsou automaticky namapováni na `dbo`. `sysadmin`  
  
> [!NOTE]
> `dbo`je také název schématu, jak je popsáno v části [vlastnictví a oddělení uživatelských schémat v SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).  
  
 Tento `dbo` uživatelský účet se často zaměňuje `db_owner` s pevnou databázovou rolí. Rozsahem `db_owner` je databáze. `sysadmin` obor je celý server. Členství v `db_owner` roli `dbo` neuděluje oprávnění uživatele.  
  
### <a name="the-guest-user-account"></a>Uživatelský účet hosta  
 Po ověření uživatele a povolení přihlášení k instanci SQL Server musí v každé databázi, ke které má uživatel přístup, existovat samostatný uživatelský účet. Vyžadování uživatelského účtu v každé databázi zabraňuje uživatelům v připojení k instanci SQL Server a přístup ke všem databázím na serveru. Existence `guest` uživatelského účtu v databázi tento požadavek obchází, protože pro přístup k databázi umožňuje přihlášení bez uživatelského účtu databáze.  
  
 `guest` Účet je předdefinovaným účtem ve všech verzích SQL Server. Ve výchozím nastavení je v nových databázích zakázaná. Pokud je povolená, můžete ji zakázat tím, že zrušíte její oprávnění k odvolání pomocí příkazu Transact-SQL REVOKE CONNECT z HOSTa.  
  
> [!IMPORTANT]
> Vyhněte se `guest` použití účtu. všechna přihlášení bez vlastních oprávnění databáze získají oprávnění databáze udělená tomuto účtu. Pokud musíte `guest` účet použít, přidělte mu minimální oprávnění.  
  
 Další informace o SQL Server přihlašování, uživatelích a rolích najdete v následujících zdrojích informací.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Začínáme s oprávněním databázového stroje](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|Obsahuje odkazy na témata, která popisují objekty zabezpečení, role, přihlašovací údaje, zabezpečit a oprávnění.|  
|[Objekty](/sql/relational-databases/security/authentication-access/principals-database-engine)|Popisuje objekty zabezpečení a obsahuje odkazy na témata, která popisují role serveru a databáze.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Ověřování v SQL Serveru](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [Autorizace a oprávnění na SQL Serveru](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
