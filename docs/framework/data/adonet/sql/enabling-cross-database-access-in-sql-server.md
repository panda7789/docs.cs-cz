---
title: Povolení přístupu mezi databázemi na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 70b4b7b55311bfc5dba1b537a603e0d15d7f3d9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877692"
---
# <a name="enabling-cross-database-access-in-sql-server"></a>Povolení přístupu mezi databázemi na SQL Serveru
Vlastnictví mezidatabázové řetězení nastane, pokud postup v jedné databázi závisí na objektech v jiné databázi. Řetěz vlastnictví mezi databázemi funguje stejným způsobem jako v rámci jedné databáze řetězení vlastnictví, s tím rozdílem, že řetěz nepřerušený vlastnictví vyžaduje, aby všichni vlastníci objektu jsou namapovány na stejný přihlašovací účet. Pokud zdrojový objekt v databázi zdrojové a cílové objektů v cílové databáze jsou vlastněny stejný přihlašovací účet, nekontroluje systém SQL Server oprávnění u cílové objektů.  
  
## <a name="off-by-default"></a>Ve výchozím nastavení vypnuté  
 Řetězení vlastnictví napříč databázemi je ve výchozím nastavení vypnuté. Společnost Microsoft doporučuje zakázat vlastnictví mezidatabázové řetězení protože seznámí vás se nese následující rizika zabezpečení:  
  
- Vlastníci a členové databáze `db_ddladmin` nebo `db_owners` databázové role můžete vytvořit objekty, které vlastní jiní uživatelé. Tyto objekty může potenciálně cílové objektů v jiných databázích. To znamená, že pokud povolíte vlastnictví mezidatabázové řetězení, je nutné plně důvěřovat tito uživatelé s daty ve všech databázích.  
  
- Uživatelé s oprávněním vytvářet databáze můžete vytvářet nové databáze a připojit existující databáze. Pokud vlastnictví mezidatabázové řetězení je povoleno, mohou tito uživatelé přejdou objekty v jiných databázích, které jsou pravděpodobně nemá oprávnění z nově vytvořených nebo připojených databází, které vytvoří.  
  
## <a name="enabling-cross-database-ownership-chaining"></a>Povolení vlastnictví mezidatabázové řetězení  
 Vlastnictví mezidatabázové řetězení musí být povolené jen v prostředích, kde můžete plně důvěřovat uživatelům s vysokou úrovní oprávnění. Můžete ji nakonfigurovat, během instalace pro všechny databáze nebo selektivně ke konkrétním databázím pomocí [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy `sp_configure` a `ALTER DATABASE`.  
  
 Chcete-li konfigurace selektivním vlastnictví mezidatabázové řetězení, použijte `sp_configure` vypnutí serveru. Pak pomocí příkazu ALTER DATABASE nastavit ON DB_CHAINING konfigurace vlastnictví mezidatabázové řetězení pro databáze, které je vyžadují.  
  
 Následující příklad se zapne vlastnictví mezidatabázové řetězení pro všechny databáze:  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 Následující příklad se zapne vlastnictví mezidatabázové řetězení pro konkrétní databáze:  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a>Dynamic SQL  
 Vlastnictví mezidatabázové řetězení nebude fungovat v případech, ve kterých se spouští dynamicky vytvořené příkazy SQL, pokud existuje v databázi i databázi. Můžete obejít tím v systému SQL Server vytvořením uloženou proceduru, která přistupuje k datům v jiné databázi a podepisování postup certifikátem, který existuje v databázi i databázi. To poskytuje uživatelům přístup k databázi prostředky využívané třídou postupu bez nutnosti přidělit jim přístup k databázi nebo oprávnění.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Rozšíření databáze zosobnění s použitím EXECUTE AS](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) a [různé možnost řetězení vlastnictví DB](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).|Články popisují, jak nakonfigurovat vlastnictví mezidatabázové řetězení pro instanci systému SQL Server.|  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Přehled zabezpečení SQL Serveru](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [Správa oprávnění pomocí uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [Zápis zabezpečené dynamické SQL na SQL Serveru](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [Podepisování uložených procedur na SQL Serveru](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
