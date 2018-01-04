---
title: "Postupy: určení typů dat databáze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 60f07a629c981eb0ad72f7c3e2d8537d5ca77515
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-database-data-types"></a>Postupy: určení typů dat databáze
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut zadat přesný text, který definuje sloupec v tabulce deklaraci T-SQL.  
  
 Je nutné zadat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost pouze v případě, že máte v úmyslu použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A> k vytvoření instance databáze.  
  
 Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Pokud chcete zadat text k definování typu dat v tabulce T-SQL  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost přesný text, který je používán T-SQL.  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
