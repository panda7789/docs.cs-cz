---
title: Serverové a databázové role v systému SQL Server
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: c7fdac92c2d980669a3cc3bf67119bdbb42509a4
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091809"
---
# <a name="server-and-database-roles-in-sql-server"></a>Serverové a databázové role v systému SQL Server
Všechny verze SQL serveru použít zabezpečení na základě rolí, které vám umožní přiřadit oprávnění pro roli nebo skupinu uživatelů, nikoli pro jednotlivé uživatele. Pevného serveru a pevné databázové role mají pevnou sadu oprávnění, které jsou jim přiřazeny.  
  
## <a name="fixed-server-roles"></a>Role pevného serveru  
 Role pevného serveru mají pevnou sadu oprávnění a rozsahu na úrovni serveru. Ty jsou určené pro správu systému SQL Server a oprávnění přiřazená k nim nedá změnit. Přihlášení můžete přiřadit role pevného serveru bez nutnosti uživatelský účet v databázi.  
  
> [!IMPORTANT]
>  `sysadmin` Pevné role serveru zahrnuje všechny ostatní role a má neomezený obor. Objekty zabezpečení nepřidávejte do této role, které nejsou vysoce důvěryhodné. `sysadmin` Členové role mají neodvolatelnou oprávnění správce pro všechny databáze na serveru a prostředky.  
  
 Vybírejte při přidání uživatelů do role pevného serveru. Například `bulkadmin` rolí umožňuje vložit obsah místního souboru do tabulky, které by mohlo ohrozit integritu dat. Pro úplný seznam role pevného serveru a oprávnění naleznete v tématu knihy Online SQL Server.  
  
## <a name="fixed-database-roles"></a>Pevné databázové role  
 Pevné databázové role mají předem definovanou sadu oprávnění, které jsou navržené tak, aby bylo možné snadno spravovat skupiny oprávnění. Členové `db_owner` role mohou provádět všechny aktivity konfigurace a údržby databáze.  
  
 Další informace o SQL serveru předdefinovaných rolí, najdete v následující prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Role na úrovni serveru](/sql/relational-databases/security/authentication-access/server-level-roles)|Popisuje role pevného serveru a oprávnění k nim má přiřazené v systému SQL Server.|  
|[Role na úrovni databáze](/sql/relational-databases/security/authentication-access/database-level-roles)|Popisuje pevné databázové role a oprávnění k nim má přiřazené|  
  
## <a name="database-roles-and-users"></a>Databázové role a uživatele  
 Přihlašovací jména musí být namapována na uživatelské účty v databázích za účelem práce s databázovými objekty. Uživatelé databáze je potom možné přidat do databázových rolí dědění jakékoli sady oprávnění přidružené k těmto rolím. Všechna oprávnění lze udělit.  
  
 Musíte taky zvážit, `public` role, `dbo` uživatelský účet a `guest` účtu při návrhu zabezpečení pro vaši aplikaci.  
  
### <a name="the-public-role"></a>Veřejné Role  
 `public` Role je obsažen v každé databázi, která zahrnuje systémové databáze. Nelze vyřadit, a nelze přidat nebo odebrat uživatele z něj. Oprávnění udělená `public` role se dědí všechny ostatní uživatelé a role protože náleží do `public` roli ve výchozím nastavení. Udělení `public` pouze oprávnění chcete, aby všichni uživatelé měli.  
  
### <a name="the-dbo-user-account"></a>Uživatelský účet dbo  
 `dbo`, Nebo vlastník databáze, je uživatelský účet, který má implicitní oprávnění provádět všechny aktivity v databázi. Členové `sysadmin` pevné role serveru, se automaticky mapují na `dbo`.  
  
> [!NOTE]
>  `dbo` je také název schématu, jak je popsáno v [vlastnictví a oddělení uživatelských schémat na SQL serveru](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).  
  
 `dbo` Uživatelský účet je často zaměnitelná s `db_owner` pevné databázové role. Rozsah `db_owner` je databáze; obor `sysadmin` je celý server. Členství ve skupině `db_owner` role neuděluje `dbo` uživatelská oprávnění.  
  
### <a name="the-guest-user-account"></a>Uživatelský účet guest  
 Jakmile uživatel byl ověřen a povolena pro přihlášení k instanci systému SQL Server, samostatný uživatelský účet musí existovat v každé databázi, má uživatel přístup. Vyžaduje uživatelský účet v každé databázi zabraňuje uživatelům připojování k instanci systému SQL Server a přístupu do všech databází na serveru. Existence `guest` uživatelský účet v databázi obchází tento požadavek tím, že přihlašovací údaje bez databáze uživatelský účet pro přístup k databázi.  
  
 `guest` Účtu je integrovaný účet ve všech verzích systému SQL Server. Ve výchozím nastavení je zakázána v nové databáze. Pokud je povolené, můžete jej zakázat tak, že odvolání své oprávnění k připojení pomocí provádí příkaz jazyka Transact-SQL ODVOLAT připojit z hosta.  
  
> [!IMPORTANT]
>  Vyhněte se použití `guest` účtu; všechna přihlášení bez jejich vlastní databázi oprávnění získat databázi oprávnění udělená k tomuto účtu. Pokud je nutné použít `guest` účtu, jí udělit minimální oprávnění.  
  
 Další informace o přihlašování, uživatelé a role serveru SQL Server viz následující prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Začínáme s oprávněními modul databáze](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|Obsahuje odkazy na témata popisující objekty zabezpečení, role, přihlašovací údaje, zabezpečitelné objekty a oprávnění.|  
|[Objekty zabezpečení](/sql/relational-databases/security/authentication-access/principals-database-engine)|Popisuje objekty zabezpečení a obsahuje odkazy na témata popisující role serveru a databáze.|  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Ověřování v SQL Serveru](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [Autorizace a oprávnění na SQL Serveru](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
