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
# <a name="sql-generation"></a>Generování SQL
Když napíšete poskytovatele pro Entity Framework, je nutné překládat Entity Framework stromů příkazů do SQL, které konkrétní databáze může pochopit, jako je například Transact-SQL pro SQL Server nebo PL/SQL pro Oracle. V této části se naučíte vyvíjet komponentu pro generování SQL (pro dotazy SELECT) pro poskytovatele Entity Framework. Informace o vkládání, aktualizaci a odstraňování dotazů naleznete v tématu [Úprava SQL generování](modification-sql-generation.md).  
  
 Pro pochopení této části byste měli být obeznámeni s Entity Framework a modelem poskytovatele ADO.NET. Měli byste taky pochopit stromy příkazů a <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Role modulu generování SQL  
 Modul SQL Generation poskytovatele Entity Framework překládá daný strom příkazů dotazu do jednoho příkazu SELECT jazyka SQL, který cílí na databázi SQL: 1999. Vygenerovaný SQL by měl mít co nejvíce vnořených dotazů. Modul SQL Generation by neměl zjednodušit strom příkazů výstupního dotazu. Entity Framework to udělat, třeba odstraněním spojení a sbalením po sobě jdoucích uzlů filtru.  
  
 Třída je výchozím bodem pro přístup ke vrstvě generování SQL pro převod stromů příkazů do <xref:System.Data.Common.DbCommand>. <xref:System.Data.Common.DbProviderServices>  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Tvar stromu příkazů](the-shape-of-the-command-trees.md)  
  
 [Generování SQL ze stromů příkazů – osvědčené postupy](generating-sql-from-command-trees-best-practices.md)  
  
 [Generování SQL ve zprostředkovateli ukázek](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Viz také:

- [Zápis zprostředkovatele dat Entity Framework](writing-an-ef-data-provider.md)
