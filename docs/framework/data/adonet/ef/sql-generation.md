---
title: Generování SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854353"
---
# <a name="sql-generation"></a><span data-ttu-id="2ca5b-102">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="2ca5b-102">SQL Generation</span></span>
<span data-ttu-id="2ca5b-103">Když napíšete poskytovatele pro Entity Framework, je nutné překládat Entity Framework stromů příkazů do SQL, které konkrétní databáze může pochopit, jako je například Transact-SQL pro SQL Server nebo PL/SQL pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="2ca5b-103">When you write a provider for the Entity Framework, you must translate Entity Framework command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="2ca5b-104">V této části se naučíte vyvíjet komponentu pro generování SQL (pro dotazy SELECT) pro poskytovatele Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2ca5b-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an Entity Framework provider.</span></span> <span data-ttu-id="2ca5b-105">Informace o vkládání, aktualizaci a odstraňování dotazů naleznete v tématu [Úprava SQL generování](modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="2ca5b-105">For information about insert, update, and delete queries, see [Modification SQL Generation](modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="2ca5b-106">Pro pochopení této části byste měli být obeznámeni s Entity Framework a modelem poskytovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="2ca5b-106">To understand this section, you should be familiar with the Entity Framework and the ADO.NET Provider Model.</span></span> <span data-ttu-id="2ca5b-107">Měli byste taky pochopit stromy příkazů a <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="2ca5b-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="2ca5b-108">Role modulu generování SQL</span><span class="sxs-lookup"><span data-stu-id="2ca5b-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="2ca5b-109">Modul SQL Generation poskytovatele Entity Framework překládá daný strom příkazů dotazu do jednoho příkazu SELECT jazyka SQL, který cílí na databázi SQL: 1999.</span><span class="sxs-lookup"><span data-stu-id="2ca5b-109">The SQL generation module of an Entity Framework provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="2ca5b-110">Vygenerovaný SQL by měl mít co nejvíce vnořených dotazů.</span><span class="sxs-lookup"><span data-stu-id="2ca5b-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="2ca5b-111">Modul SQL Generation by neměl zjednodušit strom příkazů výstupního dotazu.</span><span class="sxs-lookup"><span data-stu-id="2ca5b-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="2ca5b-112">Entity Framework to udělat, třeba odstraněním spojení a sbalením po sobě jdoucích uzlů filtru.</span><span class="sxs-lookup"><span data-stu-id="2ca5b-112">The Entity Framework will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="2ca5b-113">Třída je výchozím bodem pro přístup ke vrstvě generování SQL pro převod stromů příkazů do <xref:System.Data.Common.DbCommand>. <xref:System.Data.Common.DbProviderServices></span><span class="sxs-lookup"><span data-stu-id="2ca5b-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ca5b-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2ca5b-114">In This Section</span></span>  
 [<span data-ttu-id="2ca5b-115">Tvar stromu příkazů</span><span class="sxs-lookup"><span data-stu-id="2ca5b-115">The Shape of the Command Trees</span></span>](the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="2ca5b-116">Generování SQL ze stromů příkazů – osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="2ca5b-116">Generating SQL from Command Trees - Best Practices</span></span>](generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="2ca5b-117">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="2ca5b-117">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ca5b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ca5b-118">See also</span></span>

- [<span data-ttu-id="2ca5b-119">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2ca5b-119">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
