---
title: Udělení oprávnění na úrovni řádků na SQL Serveru
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: df5fcb4a6c73e12bec2ab17501fdfb02cf672324
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782363"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="7caad-102">Udělení oprávnění na úrovni řádků na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="7caad-102">Granting Row-Level Permissions in SQL Server</span></span>

<span data-ttu-id="7caad-103">V některých scénářích je potřeba řídit přístup k datům na podrobnější úrovni, než jaká oprávnění nabízí jenom udělování, odvolávání nebo odepření.</span><span class="sxs-lookup"><span data-stu-id="7caad-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="7caad-104">Například databázová aplikace v nemocnicích může vyžadovat, aby jednotliví lékaři omezili přístup k informacím, které se týkají pouze svých pacientů.</span><span class="sxs-lookup"><span data-stu-id="7caad-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="7caad-105">Podobné požadavky existují v mnoha prostředích, včetně finančních, zákonných, státních a vojenských aplikací.</span><span class="sxs-lookup"><span data-stu-id="7caad-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="7caad-106">Aby bylo možné tyto scénáře vyřešit, SQL Server 2016 poskytuje funkci [zabezpečení na úrovni řádků](/sql/relational-databases/security/row-level-security) , která zjednodušuje a centralizovat logiku přístupu na úrovni řádků v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7caad-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](/sql/relational-databases/security/row-level-security) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="7caad-107">Pro starší verze SQL Server lze dosáhnout podobných funkcí pomocí zobrazení k přijetí filtrování na úrovni řádků.</span><span class="sxs-lookup"><span data-stu-id="7caad-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>

## <a name="implementing-row-level-filtering"></a><span data-ttu-id="7caad-108">Implementace filtrování na úrovni řádků</span><span class="sxs-lookup"><span data-stu-id="7caad-108">Implementing Row-level Filtering</span></span>

<span data-ttu-id="7caad-109">Filtrování na úrovni řádků se používá pro aplikace, které ukládají informace v jedné tabulce, jako je třeba výše uvedený příklad nemocnice.</span><span class="sxs-lookup"><span data-stu-id="7caad-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="7caad-110">Pro implementaci filtrování na úrovni řádků každý řádek má sloupec, který definuje rozdílový parametr, jako je například uživatelské jméno, popisek nebo jiný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="7caad-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="7caad-111">Vytvoříte buď zásadu zabezpečení, nebo zobrazení v tabulce, které filtruje řádky, ke kterým má uživatel přístup.</span><span class="sxs-lookup"><span data-stu-id="7caad-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="7caad-112">Pak vytvoříte parametrizované uložené procedury, které řídí typy dotazů, které může uživatel provádět.</span><span class="sxs-lookup"><span data-stu-id="7caad-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>

<span data-ttu-id="7caad-113">Následující příklad popisuje, jak nakonfigurovat filtrování na úrovni řádků na základě uživatelského jména nebo přihlašovacího jména:</span><span class="sxs-lookup"><span data-stu-id="7caad-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>

- <span data-ttu-id="7caad-114">Vytvořte tabulku a přidejte do ní sloupec pro uložení názvu.</span><span class="sxs-lookup"><span data-stu-id="7caad-114">Create the table, adding a column to store the name.</span></span>

- <span data-ttu-id="7caad-115">Povolit filtrování na úrovni řádků:</span><span class="sxs-lookup"><span data-stu-id="7caad-115">Enable row-level filtering:</span></span>

  - <span data-ttu-id="7caad-116">Pokud používáte SQL Server 2016 nebo vyšší nebo [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), vytvořte zásadu zabezpečení, která přidá predikát do tabulky s omezením počtu vrácených řádků na ty, které odpovídají buď aktuálnímu uživateli databáze (pomocí integrované funkce CURRENT_USER ()), nebo aktuální přihlašovací jméno (pomocí předdefinované funkce SUSER_SNAME ():</span><span class="sxs-lookup"><span data-stu-id="7caad-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>

      ```sql
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

  - <span data-ttu-id="7caad-117">Pokud používáte verzi SQL Server před 2016, můžete dosáhnout podobných funkcí pomocí zobrazení:</span><span class="sxs-lookup"><span data-stu-id="7caad-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- <span data-ttu-id="7caad-118">Vytvořte uložené procedury pro výběr, vložení, aktualizaci a odstranění dat.</span><span class="sxs-lookup"><span data-stu-id="7caad-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="7caad-119">Pokud je filtrování vydaných zásadami zabezpečení, měly by tyto operace provádět přímo v základní tabulce. v opačném případě, pokud je filtrování vydaným zobrazením, by místo toho měly být uložené procedury použity pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="7caad-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="7caad-120">Pomocí zásad zabezpečení nebo zobrazení budou automaticky filtrovány řádky vracené nebo upravené uživatelskými dotazy a uložený postup bude poskytovat těžší hranici zabezpečení, která uživatelům brání v úspěšném spuštění dotazů, které mohou odvodit existence filtrovaných dat.</span><span class="sxs-lookup"><span data-stu-id="7caad-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>

- <span data-ttu-id="7caad-121">U uložených procedur, které vkládají data, Zachyťte uživatelské jméno pomocí stejné funkce zadané v zásadách nebo zobrazení zabezpečení a vložte tuto hodnotu do sloupce UserName (uživatelské jméno).</span><span class="sxs-lookup"><span data-stu-id="7caad-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>

- <span data-ttu-id="7caad-122">Odepřít všechna oprávnění k tabulkám (a zobrazením, pokud jsou k dispozici) pro `public` roli.</span><span class="sxs-lookup"><span data-stu-id="7caad-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="7caad-123">Uživatelé nebudou moci dědit oprávnění z jiných databázových rolí, protože predikát filtru je založen na uživatelských nebo přihlašovacích jménech a nikoli na rolích.</span><span class="sxs-lookup"><span data-stu-id="7caad-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>

- <span data-ttu-id="7caad-124">Udělte spuštění na uložených procedurách databázovým rolím.</span><span class="sxs-lookup"><span data-stu-id="7caad-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="7caad-125">Uživatelé můžou k datům přistupovat jenom prostřednictvím poskytnutých uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="7caad-125">Users can only access data through the stored procedures provided.</span></span>

## <a name="see-also"></a><span data-ttu-id="7caad-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7caad-126">See also</span></span>

- [<span data-ttu-id="7caad-127">Zabezpečení na úrovni řádků</span><span class="sxs-lookup"><span data-stu-id="7caad-127">Row-Level Security</span></span>](/sql/relational-databases/security/row-level-security)
- [<span data-ttu-id="7caad-128">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7caad-128">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="7caad-129">Přehled zabezpečení SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="7caad-129">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="7caad-130">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="7caad-130">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="7caad-131">Správa oprávnění pomocí uložených procedur na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="7caad-131">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="7caad-132">Zápis zabezpečené dynamické SQL na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="7caad-132">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="7caad-133">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7caad-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
