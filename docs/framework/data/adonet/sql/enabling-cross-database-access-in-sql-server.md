---
title: Povolení přístupu mezi databázemi na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: bf46d43f5ac9b0a385e9bc6da1546af1d67a282d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040248"
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="910bc-102">Povolení přístupu mezi databázemi na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="910bc-102">Enabling Cross-Database Access in SQL Server</span></span>
<span data-ttu-id="910bc-103">Řetězení vlastnictví mezi databázemi nastane, když procedura v jedné databázi závisí na objektech v jiné databázi.</span><span class="sxs-lookup"><span data-stu-id="910bc-103">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="910bc-104">Řetěz vlastnictví mezi databázemi funguje stejným způsobem jako vlastnictví řetězení v rámci izolované databáze s tím rozdílem, že řetěz vlastnických vlastníků vyžaduje, aby všichni vlastníci objektu byli namapováni na stejný přihlašovací účet.</span><span class="sxs-lookup"><span data-stu-id="910bc-104">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="910bc-105">Pokud zdrojový objekt ve zdrojové databázi a cílové objekty v cílových databázích patří do stejného přihlašovacího účtu, SQL Server nekontrolují oprávnění u cílových objektů.</span><span class="sxs-lookup"><span data-stu-id="910bc-105">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="910bc-106">Vypnuto ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="910bc-106">Off By Default</span></span>  
 <span data-ttu-id="910bc-107">Vlastnictví řetězení napříč databázemi je ve výchozím nastavení vypnuté.</span><span class="sxs-lookup"><span data-stu-id="910bc-107">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="910bc-108">Společnost Microsoft doporučuje, abyste zakázali řetězování vlastnictví mezi databázemi, protože vám odhalí následující rizika zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="910bc-108">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
- <span data-ttu-id="910bc-109">Vlastníci a členové databáze `db_ddladmin` nebo databázové role `db_owners` mohou vytvářet objekty vlastněné ostatními uživateli.</span><span class="sxs-lookup"><span data-stu-id="910bc-109">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="910bc-110">Tyto objekty můžou potenciálně cílit na objekty v jiných databázích.</span><span class="sxs-lookup"><span data-stu-id="910bc-110">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="910bc-111">To znamená, že pokud povolíte řetězení vlastnictví mezi databázemi, musíte těmto uživatelům plně důvěřovat s daty ve všech databázích.</span><span class="sxs-lookup"><span data-stu-id="910bc-111">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
- <span data-ttu-id="910bc-112">Uživatelé s oprávněním vytvořit databázi mohou vytvářet nové databáze a připojovat existující databáze.</span><span class="sxs-lookup"><span data-stu-id="910bc-112">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="910bc-113">Pokud je povoleno řetězení vlastnictví mezi databázemi, mohou tito uživatelé přistupovat k objektům v jiných databázích, ke kterým nemusí mít oprávnění z nově vytvořených nebo připojených databází, které vytvoří.</span><span class="sxs-lookup"><span data-stu-id="910bc-113">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="910bc-114">Povolení řetězení vlastnictví mezi databázemi</span><span class="sxs-lookup"><span data-stu-id="910bc-114">Enabling Cross-database Ownership Chaining</span></span>  
 <span data-ttu-id="910bc-115">Řetězení vlastnictví mezi databázemi by mělo být povoleno pouze v prostředích, kde můžete plně důvěřovat vysoce privilegovaným uživatelům.</span><span class="sxs-lookup"><span data-stu-id="910bc-115">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="910bc-116">Dá se nakonfigurovat při instalaci pro všechny databáze, nebo selektivně pro konkrétní databáze pomocí příkazů jazyka Transact-SQL `sp_configure` a `ALTER DATABASE`.</span><span class="sxs-lookup"><span data-stu-id="910bc-116">It can be configured during setup for all databases, or selectively for specific databases using the Transact-SQL commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="910bc-117">Pokud chcete selektivně nakonfigurovat řetězování vlastnictví mezi databázemi, použijte `sp_configure` k jeho vypnutí pro server.</span><span class="sxs-lookup"><span data-stu-id="910bc-117">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="910bc-118">Pak použijte příkaz ALTER DATABASE s nastavením DB_CHAINING na ke konfiguraci řetězení vlastnictví mezi databázemi pouze pro databáze, které to vyžadují.</span><span class="sxs-lookup"><span data-stu-id="910bc-118">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="910bc-119">Následující ukázka zapne řetězení vlastnictví mezi databázemi pro všechny databáze:</span><span class="sxs-lookup"><span data-stu-id="910bc-119">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="910bc-120">Následující ukázka zapne řetězení vlastnictví mezi databázemi pro konkrétní databáze:</span><span class="sxs-lookup"><span data-stu-id="910bc-120">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="910bc-121">Dynamické SQL</span><span class="sxs-lookup"><span data-stu-id="910bc-121">Dynamic SQL</span></span>  
 <span data-ttu-id="910bc-122">Řetězení vlastnictví mezi databázemi nefunguje v případech, kdy se spustí dynamicky vytvořené příkazy SQL, pokud stejný uživatel v obou databázích neexistuje.</span><span class="sxs-lookup"><span data-stu-id="910bc-122">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="910bc-123">Tuto možnost můžete v SQL Server obejít tak, že vytvoříte uloženou proceduru, která přistupuje k datům v jiné databázi a podepíše postup s certifikátem, který existuje v obou databázích.</span><span class="sxs-lookup"><span data-stu-id="910bc-123">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="910bc-124">Uživatelé tak budou mít přístup k prostředkům databáze použitým postupem bez udělení přístupu k databázi nebo oprávnění.</span><span class="sxs-lookup"><span data-stu-id="910bc-124">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="910bc-125">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="910bc-125">External Resources</span></span>  
 <span data-ttu-id="910bc-126">Další informace najdete v následujících zdrojích informací.</span><span class="sxs-lookup"><span data-stu-id="910bc-126">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="910bc-127">Partner</span><span class="sxs-lookup"><span data-stu-id="910bc-127">Resource</span></span>|<span data-ttu-id="910bc-128">Popis</span><span class="sxs-lookup"><span data-stu-id="910bc-128">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="910bc-129">[Rozšíření zosobnění databáze pomocí možnosti Spustit jako](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) a [řetězení vlastnictví mezi databázemi](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span><span class="sxs-lookup"><span data-stu-id="910bc-129">[Extending Database Impersonation by Using EXECUTE AS](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) and [Cross DB Ownership Chaining Option](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span></span>|<span data-ttu-id="910bc-130">Články popisují, jak nakonfigurovat řetězení vlastnictví mezi databázemi pro instanci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="910bc-130">Articles describe how to configure cross-database ownership chaining for an instance of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="910bc-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="910bc-131">See also</span></span>

- [<span data-ttu-id="910bc-132">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="910bc-132">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="910bc-133">Přehled zabezpečení SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="910bc-133">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="910bc-134">Správa oprávnění pomocí uložených procedur na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="910bc-134">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="910bc-135">Zápis zabezpečené dynamické SQL na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="910bc-135">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="910bc-136">Podepisování uložených procedur na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="910bc-136">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="910bc-137">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="910bc-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
