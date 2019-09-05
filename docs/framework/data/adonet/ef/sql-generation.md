---
title: Generování SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 2c18e88967fcba2b8414bfc171412eba908002b3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248403"
---
# <a name="sql-generation"></a><span data-ttu-id="b82dd-102">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="b82dd-102">SQL Generation</span></span>
<span data-ttu-id="b82dd-103">Když napíšete poskytovatele pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], musíte převést [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] stromy příkazů do SQL, které konkrétní databáze může pochopit, jako je například Transact-SQL pro SQL Server nebo PL/SQL pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="b82dd-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="b82dd-104">V této části se naučíte vyvíjet komponentu generování SQL (pro dotazy SELECT) pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="b82dd-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="b82dd-105">Informace o vkládání, aktualizaci a odstraňování dotazů naleznete v tématu [Úprava SQL generování](modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="b82dd-105">For information about insert, update, and delete queries, see [Modification SQL Generation](modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="b82dd-106">Pro pochopení této části byste měli být obeznámeni s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] modelem poskytovatele ADO.NET a.</span><span class="sxs-lookup"><span data-stu-id="b82dd-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="b82dd-107">Měli byste taky pochopit stromy příkazů a <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="b82dd-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="b82dd-108">Role modulu generování SQL</span><span class="sxs-lookup"><span data-stu-id="b82dd-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="b82dd-109">Modul SQL Generation [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele překládá daný strom příkazů dotazu na jeden příkaz SQL SELECT, který cílí na databázi SQL: 1999.</span><span class="sxs-lookup"><span data-stu-id="b82dd-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="b82dd-110">Vygenerovaný SQL by měl mít co nejvíce vnořených dotazů.</span><span class="sxs-lookup"><span data-stu-id="b82dd-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="b82dd-111">Modul SQL Generation by neměl zjednodušit strom příkazů výstupního dotazu.</span><span class="sxs-lookup"><span data-stu-id="b82dd-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="b82dd-112">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Provede to například odstraněním spojení a sbalením po sobě jdoucích uzlů filtru.</span><span class="sxs-lookup"><span data-stu-id="b82dd-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="b82dd-113">Třída je výchozím bodem pro přístup ke vrstvě generování SQL pro převod stromů příkazů do <xref:System.Data.Common.DbCommand>. <xref:System.Data.Common.DbProviderServices></span><span class="sxs-lookup"><span data-stu-id="b82dd-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b82dd-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b82dd-114">In This Section</span></span>  
 [<span data-ttu-id="b82dd-115">Tvar stromu příkazů</span><span class="sxs-lookup"><span data-stu-id="b82dd-115">The Shape of the Command Trees</span></span>](the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="b82dd-116">Generování SQL ze stromů příkazů – osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="b82dd-116">Generating SQL from Command Trees - Best Practices</span></span>](generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="b82dd-117">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="b82dd-117">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="b82dd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b82dd-118">See also</span></span>

- [<span data-ttu-id="b82dd-119">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="b82dd-119">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
