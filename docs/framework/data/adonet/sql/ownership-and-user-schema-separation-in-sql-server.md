---
title: "Vlastnictví a oddělení schéma uživatele v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 168eaf9bc0bbac80cbd1e2bb0538aab89d262a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a><span data-ttu-id="43e99-102">Vlastnictví a oddělení schéma uživatele v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="43e99-102">Ownership and User-Schema Separation in SQL Server</span></span>
<span data-ttu-id="43e99-103">Koncept základní zabezpečení systému SQL Server je, že vlastníky objektů mít neodvolatelný oprávnění ke správě je.</span><span class="sxs-lookup"><span data-stu-id="43e99-103">A core concept of SQL Server security is that owners of objects have irrevocable permissions to administer them.</span></span> <span data-ttu-id="43e99-104">Oprávnění nelze odstranit z objektu vlastníka a z databáze nelze vyřadit uživatele, pokud vlastní objekty v něm.</span><span class="sxs-lookup"><span data-stu-id="43e99-104">You cannot remove privileges from an object owner, and you cannot drop users from a database if they own objects in it.</span></span>  
  
## <a name="user-schema-separation"></a><span data-ttu-id="43e99-105">Schéma uživatele oddělení</span><span class="sxs-lookup"><span data-stu-id="43e99-105">User-Schema Separation</span></span>  
 <span data-ttu-id="43e99-106">Oddělení schéma uživatele umožňuje větší flexibilitu při správě oprávnění objektu databáze.</span><span class="sxs-lookup"><span data-stu-id="43e99-106">User-schema separation allows for more flexibility in managing database object permissions.</span></span> <span data-ttu-id="43e99-107">A *schématu* je pojmenované kontejner pro databázové objekty, které vám umožní do objektů skupiny do samostatné obory názvů.</span><span class="sxs-lookup"><span data-stu-id="43e99-107">A *schema* is a named container for database objects, which allows you to group objects into separate namespaces.</span></span> <span data-ttu-id="43e99-108">Například ukázkovou databázi AdventureWorks obsahuje schémata pro produkční, prodej a Lidskézdroje.</span><span class="sxs-lookup"><span data-stu-id="43e99-108">For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.</span></span>  
  
 <span data-ttu-id="43e99-109">Odkazy na objekty sestávající ze čtyř částí pojmenování syntaxe Určuje název schématu.</span><span class="sxs-lookup"><span data-stu-id="43e99-109">The four-part naming syntax for referring to objects specifies the schema name.</span></span>  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a><span data-ttu-id="43e99-110">Vlastníci schématu a oprávnění</span><span class="sxs-lookup"><span data-stu-id="43e99-110">Schema Owners and Permissions</span></span>  
 <span data-ttu-id="43e99-111">Schémata můžete vlastnit žádné objekt zabezpečení databáze, a jeden objekt může vlastní více schématy.</span><span class="sxs-lookup"><span data-stu-id="43e99-111">Schemas can be owned by any database principal, and a single principal can own multiple schemas.</span></span> <span data-ttu-id="43e99-112">Můžete použít pravidla zabezpečení na schéma, které jsou zdědí všechny objekty ve schématu.</span><span class="sxs-lookup"><span data-stu-id="43e99-112">You can apply security rules to a schema, which are inherited by all objects in the schema.</span></span> <span data-ttu-id="43e99-113">Až nastavíte přístupová oprávnění pro schéma, tato oprávnění budou automaticky použita jako schématu se přidají nové objekty.</span><span class="sxs-lookup"><span data-stu-id="43e99-113">Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.</span></span> <span data-ttu-id="43e99-114">Uživatelé se dají přiřadit výchozí schéma a více uživatelů databáze můžete sdílet stejné schéma.</span><span class="sxs-lookup"><span data-stu-id="43e99-114">Users can be assigned a default schema, and multiple database users can share the same schema.</span></span>  
  
 <span data-ttu-id="43e99-115">Ve výchozím nastavení když vývojáři vytvářet objekty ve schématu, objekty jsou vlastněny objekt zabezpečení, která vlastní schéma, není vývojář.</span><span class="sxs-lookup"><span data-stu-id="43e99-115">By default, when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.</span></span> <span data-ttu-id="43e99-116">Vlastnictví objektů lze převést pomocí příkazu ALTER AUTORIZACE Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="43e99-116">Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.</span></span> <span data-ttu-id="43e99-117">Schéma může také obsahovat objekty, které jsou vlastněny různým uživatelům a podrobnější oprávnění než ty, které jsou přiřazené k schématu, i když se to nedoporučuje, protože přidá složitost správy oprávnění.</span><span class="sxs-lookup"><span data-stu-id="43e99-117">A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.</span></span> <span data-ttu-id="43e99-118">Objekty lze přesunout mezi schémata a schéma vlastnictví, dají se přenášet mezi objekty zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="43e99-118">Objects can be moved between schemas, and schema ownership can be transferred between principals.</span></span> <span data-ttu-id="43e99-119">Uživatelé databáze můžete vyřadit, aniž by to ovlivnilo schémat.</span><span class="sxs-lookup"><span data-stu-id="43e99-119">Database users can be dropped without affecting schemas.</span></span>  
  
### <a name="built-in-schemas"></a><span data-ttu-id="43e99-120">Předdefinovaných schémat.</span><span class="sxs-lookup"><span data-stu-id="43e99-120">Built-In Schemas</span></span>  
 <span data-ttu-id="43e99-121">SQL Server se dodává s deset předdefinovaných schémat, které mají stejné názvy jako integrovanou databází uživatelů a rolí.</span><span class="sxs-lookup"><span data-stu-id="43e99-121">SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles.</span></span> <span data-ttu-id="43e99-122">Tyto existovat především z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="43e99-122">These exist mainly for backward compatibility.</span></span> <span data-ttu-id="43e99-123">Můžete vložit schémat, které mají stejné názvy jako pevné databázové role, pokud je nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="43e99-123">You can drop the schemas that have the same names as the fixed database roles if you do not need them.</span></span> <span data-ttu-id="43e99-124">Nelze vyřadit následujících schémat:</span><span class="sxs-lookup"><span data-stu-id="43e99-124">You cannot drop the following schemas:</span></span>  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 <span data-ttu-id="43e99-125">Pokud je vyřadit z modelová databáze, nezobrazí se v nové databáze.</span><span class="sxs-lookup"><span data-stu-id="43e99-125">If you drop them from the model database, they will not appear in new databases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43e99-126">`sys` a `INFORMATION_SCHEMA` schémata jsou vyhrazené pro systémové objekty.</span><span class="sxs-lookup"><span data-stu-id="43e99-126">The `sys` and `INFORMATION_SCHEMA` schemas are reserved for system objects.</span></span> <span data-ttu-id="43e99-127">Nelze vytvořit objekty v těchto schémata a nelze vyřadit, je.</span><span class="sxs-lookup"><span data-stu-id="43e99-127">You cannot create objects in these schemas and you cannot drop them.</span></span>  
  
#### <a name="the-dbo-schema"></a><span data-ttu-id="43e99-128">Dbo schématu</span><span class="sxs-lookup"><span data-stu-id="43e99-128">The dbo Schema</span></span>  
 <span data-ttu-id="43e99-129">`dbo` Schéma je výchozí schéma pro nově vytvořené databáze.</span><span class="sxs-lookup"><span data-stu-id="43e99-129">The `dbo` schema is the default schema for a newly created database.</span></span> <span data-ttu-id="43e99-130">`dbo` Schématu je vlastníkem `dbo` uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="43e99-130">The `dbo` schema is owned by the `dbo` user account.</span></span> <span data-ttu-id="43e99-131">Ve výchozím nastavení, mají uživatelé byla vytvořena pomocí příkazu Vytvořit uživateli Transact-SQL `dbo` jako jejich výchozí schéma.</span><span class="sxs-lookup"><span data-stu-id="43e99-131">By default, users created with the CREATE USER Transact-SQL command have `dbo` as their default schema.</span></span>  
  
 <span data-ttu-id="43e99-132">Uživatelé, kteří jsou přiřazeny `dbo` schématu nedědí oprávnění `dbo` uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="43e99-132">Users who are assigned the `dbo` schema do not inherit the permissions of the `dbo` user account.</span></span> <span data-ttu-id="43e99-133">Žádné oprávnění zdědí ze schématu uživatelé; oprávnění schématu jsou zděděny databázové objekty obsažené ve schématu.</span><span class="sxs-lookup"><span data-stu-id="43e99-133">No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43e99-134">Když jsou databázové objekty pomocí názvu složené z jedné části, SQL Server nejprve hledá v výchozí schéma uživatele.</span><span class="sxs-lookup"><span data-stu-id="43e99-134">When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema.</span></span> <span data-ttu-id="43e99-135">Pokud objekt existuje nenajde, podívá do systému SQL Server `dbo` schématu.</span><span class="sxs-lookup"><span data-stu-id="43e99-135">If the object is not found there, SQL Server looks next in the `dbo` schema.</span></span> <span data-ttu-id="43e99-136">Pokud objekt se nenachází `dbo` schématu, je vrácena chyba.</span><span class="sxs-lookup"><span data-stu-id="43e99-136">If the object is not in the `dbo` schema, an error is returned.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="43e99-137">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="43e99-137">External Resources</span></span>  
 <span data-ttu-id="43e99-138">Další informace o vlastnictví objektů a schémat najdete v následujících materiálech.</span><span class="sxs-lookup"><span data-stu-id="43e99-138">For more information on object ownership and schemas, see the following resources.</span></span>  
  
|<span data-ttu-id="43e99-139">Prostředek</span><span class="sxs-lookup"><span data-stu-id="43e99-139">Resource</span></span>|<span data-ttu-id="43e99-140">Popis</span><span class="sxs-lookup"><span data-stu-id="43e99-140">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="43e99-141">[Schéma uživatele oddělení](http://msdn.microsoft.com/library/ms190387.aspx) v Online knihách serveru SQL</span><span class="sxs-lookup"><span data-stu-id="43e99-141">[User-Schema Separation](http://msdn.microsoft.com/library/ms190387.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="43e99-142">Popisuje změny zavedené oddělení schéma uživatele.</span><span class="sxs-lookup"><span data-stu-id="43e99-142">Describes the changes introduced by user-schema separation.</span></span> <span data-ttu-id="43e99-143">Zahrnuje nové chování, jeho dopad na vlastnictví, zobrazení katalogu a oprávnění.</span><span class="sxs-lookup"><span data-stu-id="43e99-143">Includes new behavior, its impact on ownership, catalog views, and permissions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43e99-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="43e99-144">See Also</span></span>  
 [<span data-ttu-id="43e99-145">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43e99-145">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="43e99-146">Scénáře zabezpečení aplikací v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="43e99-146">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="43e99-147">Ověřování v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="43e99-147">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [<span data-ttu-id="43e99-148">Server a databázových rolí v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="43e99-148">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [<span data-ttu-id="43e99-149">Autorizace a oprávnění v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="43e99-149">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [<span data-ttu-id="43e99-150">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="43e99-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
