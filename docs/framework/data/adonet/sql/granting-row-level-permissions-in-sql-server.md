---
title: Udělení oprávnění na úrovni řádků v systému SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 5f777b47c9b2f92c40fec01b4ff0c35fc28dbd89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361303"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="61947-102">Udělení oprávnění na úrovni řádků v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="61947-102">Granting Row-Level Permissions in SQL Server</span></span>
<span data-ttu-id="61947-103">V některých případech je potřeba řízení přístupu k datům na podrobnější úrovni, než jaké jednoduše udělení, odvolání nebo odepření oprávnění poskytuje.</span><span class="sxs-lookup"><span data-stu-id="61947-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="61947-104">Databázové aplikace měla nemocnice například může vyžadovat jednotlivých lékařů být omezený přístup k informacím o související se pouze jejich pacientů.</span><span class="sxs-lookup"><span data-stu-id="61947-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="61947-105">Podobné požadavky nejsou do mnoha prostředí, včetně finance, zákonem, vládních a vojenský aplikace.</span><span class="sxs-lookup"><span data-stu-id="61947-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="61947-106">Aby vám budou snadněji řešit tyto scénáře, SQL Server 2016 poskytuje [zabezpečení na úrovni řádků](https://msdn.microsoft.com/library/dn765131.aspx) funkce, která zjednodušuje a centralizuje logiku přístup na úrovni řádku v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61947-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="61947-107">U starších verzí systému SQL Server můžete dosáhnout podobné funkce pomocí zobrazení na úrovni řádků filtrování uplatní.</span><span class="sxs-lookup"><span data-stu-id="61947-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>  
  
## <a name="implementing-row-level-filtering"></a><span data-ttu-id="61947-108">Implementace filtrování na úrovni řádků</span><span class="sxs-lookup"><span data-stu-id="61947-108">Implementing Row-level Filtering</span></span>  
 <span data-ttu-id="61947-109">Filtrování na úrovni řádků se používá pro ukládání informací o do jedné tabulky jako v předchozím příkladu měla nemocnice aplikace.</span><span class="sxs-lookup"><span data-stu-id="61947-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="61947-110">K implementaci nízkoúrovňové filtrování každý řádek má sloupec, který definuje rozdílné parametr, jako je například uživatelské jméno, popisek nebo jiné identifikátor.</span><span class="sxs-lookup"><span data-stu-id="61947-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="61947-111">Můžete vytvořit zásady zabezpečení nebo zobrazení v tabulce, která filtruje řádky, na které má uživatel přístup.</span><span class="sxs-lookup"><span data-stu-id="61947-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="61947-112">Pak vytvořte parametrizované uložené procedury, které řídit typy dotazů, které může spustit uživatel.</span><span class="sxs-lookup"><span data-stu-id="61947-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>  
  
 <span data-ttu-id="61947-113">Následující příklad popisuje, jak nakonfigurovat filtrování na základě názvu uživatele nebo přihlášení na úrovni řádků:</span><span class="sxs-lookup"><span data-stu-id="61947-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>  
  
-   <span data-ttu-id="61947-114">Umožňuje vytvořte tabulku, přidání sloupce pro uložení název.</span><span class="sxs-lookup"><span data-stu-id="61947-114">Create the table, adding a column to store the name.</span></span>  
  
-   <span data-ttu-id="61947-115">Povolte filtrování na úrovni řádků:</span><span class="sxs-lookup"><span data-stu-id="61947-115">Enable row-level filtering:</span></span>  
  
    -   <span data-ttu-id="61947-116">Pokud používáte SQL Server 2016 nebo novější, nebo [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), vytvořte zásadu zabezpečení, která přidá vrátil predikát pro tabulku omezení řádky na ty, které odpovídají buď aktuální databáze uživatel (pomocí CURRENT_USER() Integrovaná funkce) nebo aktuální přihlašovací jméno (s použitím předdefinované funkci SUSER_SNAME()):</span><span class="sxs-lookup"><span data-stu-id="61947-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>  
  
        ```tsql  
        CREATE SCHEMA Security  
        GO  
  
        CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)  
            RETURNS TABLE  
            WITH SCHEMABINDING  
        AS  
            RETURN SELECT 1 AS accessResult  
            WHERE @UserName = SUSER_SNAME()  
        GO  
  
        CREATE SECURITY POLICY Security.userAccessPolicy  
            ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,  
            ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable  
        GO  
        ```  
  
    -   <span data-ttu-id="61947-117">Pokud používáte verzi systému SQL Server před 2016, můžete dosáhnout podobné funkce pomocí zobrazení:</span><span class="sxs-lookup"><span data-stu-id="61947-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   <span data-ttu-id="61947-118">Vytvořte uložené procedury vybrat, vložit, aktualizovat a odstranit data.</span><span class="sxs-lookup"><span data-stu-id="61947-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="61947-119">Pokud filtrování budou přijaty pomocí zásad zabezpečení, uložené procedury měli provádět tyto operace u základní tabulky přímo. jinak Pokud filtrování budou přijaty zobrazení, uložené procedury místo pracovat na zobrazení.</span><span class="sxs-lookup"><span data-stu-id="61947-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="61947-120">Zásady zabezpečení nebo zobrazení bude automaticky filtrovat řádků vrácena nebo upraveném uživatelských dotazů a uložené procedury budou poskytovat těžší hranice zabezpečení nebudou moct uživatelé s přístupem přímý dotaz úspěšně spouštět dotazy, které lze odvodit existence filtrovaných dat.</span><span class="sxs-lookup"><span data-stu-id="61947-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>  
  
-   <span data-ttu-id="61947-121">Pro uložené procedury, které vkládání dat, zaznamenat uživatelské jméno pomocí stejné funkce určené zásady zabezpečení nebo zobrazení a vložte tuto hodnotu do sloupce uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="61947-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>  
  
-   <span data-ttu-id="61947-122">Zakázat všechna oprávnění v tabulkách (a zobrazení, pokud je k dispozici) na `public` role.</span><span class="sxs-lookup"><span data-stu-id="61947-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="61947-123">Uživatelé nebudou moci dědí oprávnění od jiných rolí databáze, protože predikát filtru je založena na uživatele nebo přihlašovací jména, nikoli na role.</span><span class="sxs-lookup"><span data-stu-id="61947-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>  
  
-   <span data-ttu-id="61947-124">Udělení provést uložené procedury pro databázové role.</span><span class="sxs-lookup"><span data-stu-id="61947-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="61947-125">Data mohou uživatelé přistupovat pouze prostřednictvím uložené postupy uvedené.</span><span class="sxs-lookup"><span data-stu-id="61947-125">Users can only access data through the stored procedures provided.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="61947-126">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="61947-126">External Resources</span></span>  
 <span data-ttu-id="61947-127">Další informace najdete v následujícím zdroji.</span><span class="sxs-lookup"><span data-stu-id="61947-127">For more information, see the following resource.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61947-128">[Implementace zabezpečení na úrovni řádku a buňky v klasifikovaný databáze pomocí systému SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) na webu TechCenter pro SQL Server lokality.</span><span class="sxs-lookup"><span data-stu-id="61947-128">[Implementing Row- and Cell-Level Security in Classified Databases Using SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) on the SQL Server TechCenter site.</span></span>|<span data-ttu-id="61947-129">Popisuje, jak pomocí zabezpečení na úrovni řádku a buňky splňovat požadavky zabezpečení klasifikovaný databáze.</span><span class="sxs-lookup"><span data-stu-id="61947-129">Describes how to use row- and cell-level security to meet classified database security requirements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61947-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="61947-130">See Also</span></span>  
 [<span data-ttu-id="61947-131">Zabezpečení na úrovni řádků</span><span class="sxs-lookup"><span data-stu-id="61947-131">Row-Level Security</span></span>](https://msdn.microsoft.com/library/dn765131.aspx)  
 [<span data-ttu-id="61947-132">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="61947-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="61947-133">Přehled zabezpečení SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="61947-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="61947-134">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="61947-134">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="61947-135">Správa oprávnění pomocí uložených procedur na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="61947-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="61947-136">Zápis zabezpečené dynamické SQL na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="61947-136">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="61947-137">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="61947-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
