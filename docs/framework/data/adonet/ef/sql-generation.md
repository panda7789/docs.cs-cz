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
# <a name="sql-generation"></a>Generování SQL
Když napíšete poskytovatele pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], musíte převést [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] stromy příkazů do SQL, které konkrétní databáze může pochopit, jako je například Transact-SQL pro SQL Server nebo PL/SQL pro Oracle. V této části se naučíte vyvíjet komponentu generování SQL (pro dotazy SELECT) pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] poskytovatele. Informace o vkládání, aktualizaci a odstraňování dotazů naleznete v tématu [Úprava SQL generování](modification-sql-generation.md).  
  
 Pro pochopení této části byste měli být obeznámeni s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] modelem poskytovatele ADO.NET a. Měli byste taky pochopit stromy příkazů a <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Role modulu generování SQL  
 Modul SQL Generation [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele překládá daný strom příkazů dotazu na jeden příkaz SQL SELECT, který cílí na databázi SQL: 1999. Vygenerovaný SQL by měl mít co nejvíce vnořených dotazů. Modul SQL Generation by neměl zjednodušit strom příkazů výstupního dotazu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Provede to například odstraněním spojení a sbalením po sobě jdoucích uzlů filtru.  
  
 Třída je výchozím bodem pro přístup ke vrstvě generování SQL pro převod stromů příkazů do <xref:System.Data.Common.DbCommand>. <xref:System.Data.Common.DbProviderServices>  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Tvar stromu příkazů](the-shape-of-the-command-trees.md)  
  
 [Generování SQL ze stromů příkazů – osvědčené postupy](generating-sql-from-command-trees-best-practices.md)  
  
 [Generování SQL ve zprostředkovateli ukázek](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Viz také:

- [Zápis zprostředkovatele dat Entity Framework](writing-an-ef-data-provider.md)
