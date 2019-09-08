---
title: Povolení přístupu mezi databázemi na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: f69a405a562bfae3bc283f2b3166812046be868e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794193"
---
# <a name="enabling-cross-database-access-in-sql-server"></a>Povolení přístupu mezi databázemi na SQL Serveru
Řetězení vlastnictví mezi databázemi nastane, když procedura v jedné databázi závisí na objektech v jiné databázi. Řetěz vlastnictví mezi databázemi funguje stejným způsobem jako vlastnictví řetězení v rámci izolované databáze s tím rozdílem, že řetěz vlastnických vlastníků vyžaduje, aby všichni vlastníci objektu byli namapováni na stejný přihlašovací účet. Pokud zdrojový objekt ve zdrojové databázi a cílové objekty v cílových databázích patří do stejného přihlašovacího účtu, SQL Server nekontrolují oprávnění u cílových objektů.  
  
## <a name="off-by-default"></a>Vypnuto ve výchozím nastavení  
 Vlastnictví řetězení napříč databázemi je ve výchozím nastavení vypnuté. Společnost Microsoft doporučuje, abyste zakázali řetězování vlastnictví mezi databázemi, protože vám odhalí následující rizika zabezpečení:  
  
- Vlastníci databáze a členové `db_ddladmin` `db_owners` rolí databáze mohou vytvářet objekty, které vlastní jiní uživatelé. Tyto objekty můžou potenciálně cílit na objekty v jiných databázích. To znamená, že pokud povolíte řetězení vlastnictví mezi databázemi, musíte těmto uživatelům plně důvěřovat s daty ve všech databázích.  
  
- Uživatelé s oprávněním vytvořit databázi mohou vytvářet nové databáze a připojovat existující databáze. Pokud je povoleno řetězení vlastnictví mezi databázemi, mohou tito uživatelé přistupovat k objektům v jiných databázích, ke kterým nemusí mít oprávnění z nově vytvořených nebo připojených databází, které vytvoří.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Povolení řetězení vlastnictví mezi databázemi  
 Řetězení vlastnictví mezi databázemi by mělo být povoleno pouze v prostředích, kde můžete plně důvěřovat vysoce privilegovaným uživatelům. Dá se nakonfigurovat při instalaci pro všechny databáze, nebo selektivně pro konkrétní databáze pomocí příkazů `sp_configure` jazyka Transact-SQL a. `ALTER DATABASE`  
  
 Pokud chcete selektivně nakonfigurovat řetězování vlastnictví mezi databázemi, použijte `sp_configure` ho pro vypnutí serveru. Pak použijte příkaz ALTER DATABASE s nastavením DB_CHAINING na ke konfiguraci řetězení vlastnictví mezi databázemi pouze pro databáze, které to vyžadují.  
  
 Následující ukázka zapne řetězení vlastnictví mezi databázemi pro všechny databáze:  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 Následující ukázka zapne řetězení vlastnictví mezi databázemi pro konkrétní databáze:  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Dynamické SQL  
 Řetězení vlastnictví mezi databázemi nefunguje v případech, kdy se spustí dynamicky vytvořené příkazy SQL, pokud stejný uživatel v obou databázích neexistuje. Tuto možnost můžete v SQL Server obejít tak, že vytvoříte uloženou proceduru, která přistupuje k datům v jiné databázi a podepíše postup s certifikátem, který existuje v obou databázích. Uživatelé tak budou mít přístup k prostředkům databáze použitým postupem bez udělení přístupu k databázi nebo oprávnění.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Rozšíření zosobnění databáze pomocí možnosti Spustit jako](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) a [řetězení vlastnictví mezi databázemi](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).|Články popisují, jak nakonfigurovat řetězení vlastnictví mezi databázemi pro instanci SQL Server.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](overview-of-sql-server-security.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](writing-secure-dynamic-sql-in-sql-server.md)
- [Podepisování uložených procedur na SQL Serveru](signing-stored-procedures-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
