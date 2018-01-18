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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6b2d4ba925af61f89b47c494f5fb17f5f9f0d995
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="sql-generation"></a><span data-ttu-id="23e59-102">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="23e59-102">SQL Generation</span></span>
<span data-ttu-id="23e59-103">Při psaní poskytovatele pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], musí překládat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] příkaz stromy do SQL, který můžete porozumět konkrétní databázi, například Transact-SQL pro SQL Server nebo PL/SQL pro databázi Oracle.</span><span class="sxs-lookup"><span data-stu-id="23e59-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="23e59-104">V této části se dozvíte, jak vyvíjet součást generování SQL (pro vyberte dotazy) pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="23e59-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="23e59-105">Informace o vložení, aktualizace a odstranit dotazy najdete [generování SQL úpravy](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="23e59-105">For information about insert, update, and delete queries, see [Modification SQL Generation](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="23e59-106">Zjistit, v této části, měli byste se seznámit s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a Model poskytovatele ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="23e59-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="23e59-107">Také byste měli porozumět stromy příkazů a <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="23e59-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="23e59-108">Role modulu generování jazyka SQL</span><span class="sxs-lookup"><span data-stu-id="23e59-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="23e59-109">Modul generování SQL [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele překládá stromu příkazů daný dotaz do jednoho příkazu SQL SELECT, který se zaměřuje SQL:1999 – databáze kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="23e59-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="23e59-110">Vygenerovaný SQL by měl mít jako několika vnořené dotazy míře.</span><span class="sxs-lookup"><span data-stu-id="23e59-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="23e59-111">Modul generování SQL by neměl zjednodušit strom příkazů výstup dotazu.</span><span class="sxs-lookup"><span data-stu-id="23e59-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="23e59-112">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Se to udělat, například odstraňuje spojení a sbalení uzly po sobě jdoucích filtrů.</span><span class="sxs-lookup"><span data-stu-id="23e59-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="23e59-113"><xref:System.Data.Common.DbProviderServices> Třída je výchozím bodem pro přístup k vrstvě generování SQL pro převod stromy příkazů do <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="23e59-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23e59-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="23e59-114">In This Section</span></span>  
 [<span data-ttu-id="23e59-115">Tvar stromu příkazů</span><span class="sxs-lookup"><span data-stu-id="23e59-115">The Shape of the Command Trees</span></span>](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="23e59-116">Generování SQL ze stromů příkazů – osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="23e59-116">Generating SQL from Command Trees - Best Practices</span></span>](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="23e59-117">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="23e59-117">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="23e59-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="23e59-118">See Also</span></span>  
 [<span data-ttu-id="23e59-119">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="23e59-119">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
