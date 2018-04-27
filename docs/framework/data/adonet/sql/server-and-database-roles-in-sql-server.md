---
title: Server a databázových rolí v systému SQL Server
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: b650c61a8d3d0b457bc9d5232c613d47f36ccbfc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="server-and-database-roles-in-sql-server"></a>Server a databázových rolí v systému SQL Server
Všechny verze systému SQL Server pomocí zabezpečení na základě rolí, což umožňuje přiřadit oprávnění k roli nebo skupinu uživatelů, ne pro jednotlivé uživatele. Pevného serveru a pevné databázové role mají pevnou sadu oprávnění, které jsou jim přiřazeny.  
  
## <a name="fixed-server-roles"></a>Role pevného serveru  
 Role pevného serveru mají pevnou sadu oprávnění a obor na úrovni serveru. Ty jsou určené pro správu systému SQL Server a přiřazená oprávnění nelze změnit. Přihlášení lze přiřadit do role pevného serveru bez nutnosti účet uživatele v databázi.  
  
> [!IMPORTANT]
>  `sysadmin` Pevné role serveru zahrnuje všechny ostatní role a má neomezený obor. Nepřidávejte objekty do této role, které nejsou vysoce důvěryhodných. `sysadmin` Členové role mají neodvolatelný oprávnění správce na všech databází serveru a prostředky.  
  
 Vybírejte při přidání uživatelů do role pevného serveru. Například `bulkadmin` role umožňuje uživatelům vložit obsah všech místního souboru do tabulky, jež by mohlo ohrozit integritu dat. Úplný seznam role pevného serveru a oprávnění najdete v části SQL Server Books Online.  
  
## <a name="fixed-database-roles"></a>Pevné databázové role  
 Pevné databázové role mají předem definované sadu oprávnění, které jsou navržené tak, aby bylo možné snadno spravovat skupiny oprávnění. Členové `db_owner` role provádět všechny činnosti konfigurace a údržby na databázi.  
  
 Další informace o SQL serveru předdefinovaných rolí, najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Role serveru úrovni](http://msdn.microsoft.com/library/ms188659.aspx) a [oprávnění role pevného serveru](http://msdn.microsoft.com/library/ms175892.aspx) v Online knihách serveru SQL|Popisuje role pevného serveru a oprávnění spojená s nimi v systému SQL Server.|  
|[Úroveň databáze role](http://msdn.microsoft.com/library/ms189121.aspx) a [oprávnění pevné databázové role](http://msdn.microsoft.com/library/ms189612.aspx) v Online knihách serveru SQL|Popisuje pevné databázové role a oprávnění spojená s nimi|  
  
## <a name="database-roles-and-users"></a>Databázové role a uživatele  
 Přihlášení musí být namapovaný na databázi uživatelských účtů za účelem práce s objekty databáze. Databáze můžete pak aby byli přidáni uživatelé databázové role, která dědí všechny sady oprávnění přidružená k těmto rolím. Všechna oprávnění lze udělit.  
  
 Musíte taky zvážit, `public` role, `dbo` uživatelský účet a `guest` účet při návrhu zabezpečení pro vaši aplikaci.  
  
### <a name="the-public-role"></a>Veřejné Role  
 `public` Role je obsažen v každé databázi, která zahrnuje systémové databáze. Nelze vyřadit, a nelze přidat nebo odebrat uživatele z něj. Oprávnění udělená `public` role se dědí všechny ostatní uživatelé a role, protože náleží do `public` roli ve výchozím nastavení. Udělení `public` pouze oprávnění chcete, aby měli všichni uživatelé.  
  
### <a name="the-dbo-user-account"></a>Dbo uživatelský účet  
 `dbo`, Nebo vlastník databáze, je uživatelský účet, který má implicitní oprávnění k provedení všech aktivit v databázi. Členové `sysadmin` pevné role serveru se automaticky mapují na `dbo`.  
  
> [!NOTE]
>  `dbo` je také název schématu, jak je popsáno v [vlastnictví a oddělení schéma uživatele v systému SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).  
  
 `dbo` Uživatelský účet je často zaměnit s `db_owner` pevné databázové role. Rozsah `db_owner` je databáze; oboru `sysadmin` je celý server. Členství ve skupině `db_owner` role neuděluje `dbo` uživatelská oprávnění.  
  
### <a name="the-guest-user-account"></a>Uživatelský účet guest  
 Po má uživatel ověřený a povoleno přihlásit do instance systému SQL Server, samostatný uživatelský účet musí existovat v každé databázi má uživatel přístup. Vyžaduje uživatelský účet v každé databázi zabrání uživatelům připojení k instanci systému SQL Server a přístup k všechny databáze na serveru. Existence `guest` uživatelský účet v databázi, vyřešíte tento požadavek tím, že se přihlašovací údaje bez účtu správce databáze pro přístup k databázi.  
  
 `guest` Účet je integrovaný účet ve všech verzích systému SQL Server. Ve výchozím nastavení je zakázána v nové databáze. Pokud je povoleno, ji můžete vypnout pomocí odvolání její oprávnění CONNECT spuštěním příkazu Transact-SQL ODVOLAT připojit z hosta.  
  
> [!IMPORTANT]
>  Nepoužívejte `guest` účet; všechny přihlášení bez vlastní oprávnění databáze získat databáze oprávnění udělená k tomuto účtu. Pokud je nutné použít `guest` účet, přidělte ji minimální oprávnění.  
  
 Další informace o přihlášení, uživatelé a role systému SQL Server najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Identity a řízení přístupu](http://msdn.microsoft.com/library/bb510418.aspx) v Online knihách serveru SQL|Obsahuje odkazy na témata, která popisují objekty zabezpečení, role, přihlašovací údaje, zabezpečitelné prostředky a oprávnění.|  
|[Objekty](http://msdn.microsoft.com/library/ms181127.aspx) v Online knihách serveru SQL|Popisuje objekty zabezpečení a obsahuje odkazy na témata, která popisují rolí serveru a databáze.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací na SQL Serveru](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Ověřování v SQL Serveru](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Vlastnictví a oddělení uživatelských schémat na SQL Serveru](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [Autorizace a oprávnění na SQL Serveru](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
