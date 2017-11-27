---
title: "Generování SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 727aa0ca3e1673a5bbd29884077ed5aa65d792f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="sql-generation"></a><span data-ttu-id="4968e-102">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="4968e-102">SQL Generation</span></span>
<span data-ttu-id="4968e-103">Při psaní poskytovatele pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], musí překládat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] příkaz stromy do SQL, který můžete porozumět konkrétní databázi, například Transact-SQL pro SQL Server nebo PL/SQL pro databázi Oracle.</span><span class="sxs-lookup"><span data-stu-id="4968e-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="4968e-104">V této části se dozvíte, jak vyvíjet součást generování SQL (pro vyberte dotazy) pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="4968e-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="4968e-105">Informace o vložení, aktualizace a odstranit dotazy najdete [generování SQL úpravy](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="4968e-105">For information about insert, update, and delete queries, see [Modification SQL Generation](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="4968e-106">Zjistit, v této části, měli byste se seznámit s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a Model poskytovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="4968e-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="4968e-107">Také byste měli porozumět stromy příkazů a <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="4968e-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="4968e-108">Role modulu generování jazyka SQL</span><span class="sxs-lookup"><span data-stu-id="4968e-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="4968e-109">Modul generování SQL [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele překládá stromu příkazů daný dotaz do jednoho příkazu SQL SELECT, který se zaměřuje SQL:1999 – databáze kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="4968e-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="4968e-110">Vygenerovaný SQL by měl mít jako několika vnořené dotazy míře.</span><span class="sxs-lookup"><span data-stu-id="4968e-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="4968e-111">Modul generování SQL by neměl zjednodušit strom příkazů výstup dotazu.</span><span class="sxs-lookup"><span data-stu-id="4968e-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="4968e-112">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Se to udělat, například odstraňuje spojení a sbalení uzly po sobě jdoucích filtrů.</span><span class="sxs-lookup"><span data-stu-id="4968e-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="4968e-113"><!--zz<xref:System.Data.Common.DBProviderServices> --> `System.Data.Common.DBProviderServices` Třída je výchozím bodem pro přístup k vrstvě generování SQL pro převod stromy příkazů do <!--zz<xref:System.Data.Common.DbCommands>--> `System.Data.Common.DbCommands`.</span><span class="sxs-lookup"><span data-stu-id="4968e-113">The <!--zz<xref:System.Data.Common.DBProviderServices> --> `System.Data.Common.DBProviderServices`  class is the starting point for accessing the SQL generation layer to convert command trees into <!--zz<xref:System.Data.Common.DbCommands>--> `System.Data.Common.DbCommands`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4968e-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4968e-114">In This Section</span></span>  
 [<span data-ttu-id="4968e-115">Obrazec stromy příkazů</span><span class="sxs-lookup"><span data-stu-id="4968e-115">The Shape of the Command Trees</span></span>](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="4968e-116">Generování příkazu SQL ze stromy příkazů – doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="4968e-116">Generating SQL from Command Trees - Best Practices</span></span>](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="4968e-117">Generování SQL ve zprostředkovateli ukázka</span><span class="sxs-lookup"><span data-stu-id="4968e-117">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="4968e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4968e-118">See Also</span></span>  
 [<span data-ttu-id="4968e-119">Zápis poskytovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4968e-119">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
