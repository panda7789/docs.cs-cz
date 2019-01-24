---
title: Udělení oprávnění na úrovni řádků na SQL serveru
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 28e552e005cdfa0b4c69ff95927b938fa3898193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553764"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="2dd88-102">Udělení oprávnění na úrovni řádků na SQL serveru</span><span class="sxs-lookup"><span data-stu-id="2dd88-102">Granting Row-Level Permissions in SQL Server</span></span>
<span data-ttu-id="2dd88-103">V některých případech je potřeba řídit přístup k datům na podrobnější úrovni, než jaké jednoduše udělení, odvolání nebo odepření oprávnění poskytuje.</span><span class="sxs-lookup"><span data-stu-id="2dd88-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="2dd88-104">Nemocnice databázové aplikace může například vyžadovat jednotlivé lékařů omezit přístup k informacím o související s pouze pacientů.</span><span class="sxs-lookup"><span data-stu-id="2dd88-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="2dd88-105">Podobné požadavky nejsou v mnoha prostředích, včetně finance, zákonem, government a aplikacím armády.</span><span class="sxs-lookup"><span data-stu-id="2dd88-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="2dd88-106">K řešení scénářů, SQL Server 2016 poskytuje [zabezpečení na úrovní řádků](https://msdn.microsoft.com/library/dn765131.aspx) funkce, která zjednodušuje a centralizuje logiky přístupu na úrovni řádku v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2dd88-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="2dd88-107">U starších verzí systému SQL Server můžete dosáhnout podobné funkce vydává filtrování na úrovni řádků pomocí zobrazení.</span><span class="sxs-lookup"><span data-stu-id="2dd88-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>  
  
## <a name="implementing-row-level-filtering"></a><span data-ttu-id="2dd88-108">Implementace filtrování na úrovni řádků</span><span class="sxs-lookup"><span data-stu-id="2dd88-108">Implementing Row-level Filtering</span></span>  
 <span data-ttu-id="2dd88-109">Filtrování na úrovni řádků slouží k ukládání informací o do jedné tabulky jako v předchozím příkladu nemocnice aplikací.</span><span class="sxs-lookup"><span data-stu-id="2dd88-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="2dd88-110">K implementaci na úrovni řádků filtrování každý řádek obsahuje sloupce, který definuje odlišující parametr, jako je například uživatelské jméno, popisek nebo jiný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="2dd88-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="2dd88-111">Vytvoření zásad zabezpečení nebo zobrazení v tabulce, který filtruje řádky, které má uživatel přístup.</span><span class="sxs-lookup"><span data-stu-id="2dd88-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="2dd88-112">Pak vytvoříte parametrizované uložené procedury, které řídit typy dotazů, které uživatel může spustit.</span><span class="sxs-lookup"><span data-stu-id="2dd88-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>  
  
 <span data-ttu-id="2dd88-113">Následující příklad popisuje, jak nakonfigurovat filtrování na úrovni řádků na základě názvu uživatele nebo přihlášení:</span><span class="sxs-lookup"><span data-stu-id="2dd88-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>  
  
-   <span data-ttu-id="2dd88-114">Vytvořte tabulku, přidání sloupce pro uložení názvu.</span><span class="sxs-lookup"><span data-stu-id="2dd88-114">Create the table, adding a column to store the name.</span></span>  
  
-   <span data-ttu-id="2dd88-115">Povolte filtrování na úrovni řádků:</span><span class="sxs-lookup"><span data-stu-id="2dd88-115">Enable row-level filtering:</span></span>  
  
    -   <span data-ttu-id="2dd88-116">Pokud používáte SQL Server 2016 nebo novější, nebo [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), vytvořte zásadu zabezpečení, která přidá predikát pro tabulku omezení řádků vrácena na ty, které odpovídají jednomu aktuálního uživatele databáze (pomocí CURRENT_USER() Integrovaná funkce) nebo aktuální přihlašovací jméno (pomocí předdefinované funkci SUSER_SNAME()):</span><span class="sxs-lookup"><span data-stu-id="2dd88-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>  
  
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
  
    -   <span data-ttu-id="2dd88-117">Pokud používáte verzi systému SQL Server 2016, můžete dosáhnout použitím zobrazení podobné funkce:</span><span class="sxs-lookup"><span data-stu-id="2dd88-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   <span data-ttu-id="2dd88-118">Vytvořte uložené procedury k výběru, vložit, aktualizovat a odstranit data.</span><span class="sxs-lookup"><span data-stu-id="2dd88-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="2dd88-119">Pokud filtrování budou přijaty zásady zabezpečení, uložené procedury by měl provádět tyto operace v základní tabulce přímo. v opačném případě Pokud filtrování budou přijaty ve zobrazení, uložené procedury místo toho pracovat na zobrazení.</span><span class="sxs-lookup"><span data-stu-id="2dd88-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="2dd88-120">Zásady zabezpečení nebo zobrazení bude automaticky filtrovat řádky instance vrátí, nebo upravit dotazy uživatelů a uložené procedury bude poskytovat obtížnější hranice zabezpečení úspěšně spuštění dotazů, které dokážou odvodit moct uživatelé s přístupem přímých dotazů existence filtrovaná data.</span><span class="sxs-lookup"><span data-stu-id="2dd88-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>  
  
-   <span data-ttu-id="2dd88-121">Pro uložené procedury, které vkládají data zachytit pomocí stejné funkce určené v zásadách zabezpečení nebo uživatelské jméno a vložte tuto hodnotu do sloupce uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="2dd88-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>  
  
-   <span data-ttu-id="2dd88-122">Zakázat všechna oprávnění pro tabulky (a zobrazení, pokud je k dispozici) na `public` role.</span><span class="sxs-lookup"><span data-stu-id="2dd88-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="2dd88-123">Uživatelé nebudou mít dědění oprávnění z jiné databázové role, protože predikát filtru je založena na uživatele nebo přihlašovací jména, ne na role.</span><span class="sxs-lookup"><span data-stu-id="2dd88-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>  
  
-   <span data-ttu-id="2dd88-124">Udělení spustit na uložené procedury pro databázové role.</span><span class="sxs-lookup"><span data-stu-id="2dd88-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="2dd88-125">Data mohou uživatelé přistupovat pouze prostřednictvím uložené procedury, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2dd88-125">Users can only access data through the stored procedures provided.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd88-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2dd88-126">See also</span></span>
- [<span data-ttu-id="2dd88-127">Zabezpečení na úrovní řádků</span><span class="sxs-lookup"><span data-stu-id="2dd88-127">Row-Level Security</span></span>](https://msdn.microsoft.com/library/dn765131.aspx)
- [<span data-ttu-id="2dd88-128">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2dd88-128">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="2dd88-129">Přehled zabezpečení SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="2dd88-129">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [<span data-ttu-id="2dd88-130">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="2dd88-130">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="2dd88-131">Správa oprávnění pomocí uložených procedur na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="2dd88-131">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="2dd88-132">Zápis zabezpečené dynamické SQL na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="2dd88-132">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="2dd88-133">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="2dd88-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
