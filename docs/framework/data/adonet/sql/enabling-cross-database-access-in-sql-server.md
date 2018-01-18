---
title: "Povolení přístupu mezi databáze v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2a31bddfec44ad4b33f1b595c2746d1a0e841b82
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="b55bc-102">Povolení přístupu mezi databáze v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="b55bc-102">Enabling Cross-Database Access in SQL Server</span></span>
<span data-ttu-id="b55bc-103">Řetězení mezidatabázové vlastnictví nastane, když postup v jedné databáze závisí na objektech v jiné databázi.</span><span class="sxs-lookup"><span data-stu-id="b55bc-103">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="b55bc-104">Řetěz mezidatabázové vlastnictví funguje stejným způsobem jako vlastnictví řetězení v rámci jedné databáze, s tím rozdílem, že řetězce rozděleno vlastnictví vyžaduje, aby všechny vlastníky objektů jsou namapované na stejný účet pro přihlášení.</span><span class="sxs-lookup"><span data-stu-id="b55bc-104">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="b55bc-105">Pokud zdrojový objekt v databázi zdrojové a cílové objekty v cílové databází jsou vlastněny stejný účet pro přihlášení, nekontroluje systém SQL Server oprávnění pro cílové objekty.</span><span class="sxs-lookup"><span data-stu-id="b55bc-105">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="b55bc-106">Ve výchozím nastavení vypnuté</span><span class="sxs-lookup"><span data-stu-id="b55bc-106">Off By Default</span></span>  
 <span data-ttu-id="b55bc-107">Vlastnictví řetězení mezi databázemi je ve výchozím nastavení vypnutý.</span><span class="sxs-lookup"><span data-stu-id="b55bc-107">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="b55bc-108">Společnost Microsoft doporučuje zakázat mezidatabázové vlastnictví řetězení, protože ho budete vystavuje následující rizika zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="b55bc-108">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
-   <span data-ttu-id="b55bc-109">Databáze vlastníků a členy `db_ddladmin` nebo `db_owners` databázové role můžete vytvořit objekty, které vlastní jiní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="b55bc-109">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="b55bc-110">Tyto objekty, můžete vybrat potenciálně objekty v jiných databázích.</span><span class="sxs-lookup"><span data-stu-id="b55bc-110">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="b55bc-111">To znamená, že pokud povolíte mezidatabázové vlastnictví řetězení, je nutné plně důvěřovat tito uživatelé s daty v všechny databáze.</span><span class="sxs-lookup"><span data-stu-id="b55bc-111">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
-   <span data-ttu-id="b55bc-112">Uživatelé s oprávněním Vytvořit databáze můžete vytvářet nové databáze a připojit existující databáze.</span><span class="sxs-lookup"><span data-stu-id="b55bc-112">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="b55bc-113">Pokud mezidatabázové vlastnictví řetězení je povoleno, mohou tito uživatelé přejdou objekty v jiných databázích, které budou pravděpodobně nemá oprávnění z nově vytvořené nebo připojených databází, které vytvoří.</span><span class="sxs-lookup"><span data-stu-id="b55bc-113">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="b55bc-114">Povolení mezidatabázové vlastnictví řetězení</span><span class="sxs-lookup"><span data-stu-id="b55bc-114">Enabling Cross-database Ownership Chaining</span></span>  
 <span data-ttu-id="b55bc-115">Řetězení mezidatabázové vlastnictví by měl Povolit jenom v prostředích, kde můžete důvěřovat plně vysoce privilegovaných uživatelů.</span><span class="sxs-lookup"><span data-stu-id="b55bc-115">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="b55bc-116">Dá se během instalace pro všechny databáze, nebo selektivně pro konkrétní databáze pomocí [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy `sp_configure` a `ALTER DATABASE`.</span><span class="sxs-lookup"><span data-stu-id="b55bc-116">It can be configured during setup for all databases, or selectively for specific databases using the [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="b55bc-117">Pokud chcete konfigurovat selektivně řetězení mezidatabázové vlastnictví, použijte `sp_configure` k vypnutí serveru.</span><span class="sxs-lookup"><span data-stu-id="b55bc-117">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="b55bc-118">Pak použijte příkaz ALTER DATABASE pomocí nastavení ON DB_CHAINING konfigurace mezidatabázové vlastnictví zřetězení pouze databáze, které je vyžadují.</span><span class="sxs-lookup"><span data-stu-id="b55bc-118">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="b55bc-119">Následující příklad se zapne řetězení mezidatabázové vlastnictví pro všechny databáze:</span><span class="sxs-lookup"><span data-stu-id="b55bc-119">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="b55bc-120">Následující příklad se zapne mezidatabázové vlastnictví řetězení pro konkrétní databáze:</span><span class="sxs-lookup"><span data-stu-id="b55bc-120">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="b55bc-121">Dynamic SQL</span><span class="sxs-lookup"><span data-stu-id="b55bc-121">Dynamic SQL</span></span>  
 <span data-ttu-id="b55bc-122">Řetězení mezidatabázové vlastnictví nefunguje, pokud je v případech, kde jsou provést dynamicky vytvořené příkazy SQL, dokud jeden uživatel existuje v obou databází.</span><span class="sxs-lookup"><span data-stu-id="b55bc-122">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="b55bc-123">Můžete obejít v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] vytvořením uložené procedury, která přistupuje k datům v jiné databázi a podepisování postup s certifikátem, který již existuje v obou databází.</span><span class="sxs-lookup"><span data-stu-id="b55bc-123">You can work around this in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="b55bc-124">To umožňuje uživatelům přístup k databázi prostředky využívané třídou postup bez toho, abyste jim přístup k databázi nebo oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b55bc-124">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="b55bc-125">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="b55bc-125">External Resources</span></span>  
 <span data-ttu-id="b55bc-126">Další informace najdete v následujících zdrojích informací.</span><span class="sxs-lookup"><span data-stu-id="b55bc-126">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="b55bc-127">Prostředek</span><span class="sxs-lookup"><span data-stu-id="b55bc-127">Resource</span></span>|<span data-ttu-id="b55bc-128">Popis</span><span class="sxs-lookup"><span data-stu-id="b55bc-128">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b55bc-129">[Rozšíření databáze zosobnění pomocí EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) a [mezi DB vlastnictví řetězení možnost](http://msdn.microsoft.com/library/ms188694.aspx) [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] knihy Online.</span><span class="sxs-lookup"><span data-stu-id="b55bc-129">[Extending Database Impersonation by Using EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) and [Cross DB Ownership Chaining Option](http://msdn.microsoft.com/library/ms188694.aspx)[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>|<span data-ttu-id="b55bc-130">Témata popisují postup konfigurace mezidatabázové vlastnictví řetězení pro instanci [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b55bc-130">Topics describe how to configure cross-database ownership chaining for an instance of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b55bc-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b55bc-131">See Also</span></span>  
 [<span data-ttu-id="b55bc-132">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b55bc-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="b55bc-133">Přehled zabezpečení SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="b55bc-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="b55bc-134">Správa oprávnění pomocí uložených procedur na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="b55bc-134">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="b55bc-135">Zápis zabezpečené dynamické SQL na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="b55bc-135">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="b55bc-136">Podepisování uložených procedur na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="b55bc-136">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="b55bc-137">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="b55bc-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
