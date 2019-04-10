---
title: 'Postupy: Zadání datových typů v databázi'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: bf53463be8c715fd1c599efac1b19d838be19f86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218040"
---
# <a name="how-to-specify-database-data-types"></a>Postupy: Zadání datových typů v databázi
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnosti <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut zadat přesný text, který definuje sloupce v tabulce deklaraci T-SQL.  
  
 Je nutné zadat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost jenom v případě, že máte v plánu používat <xref:System.Data.Linq.DataContext.CreateDatabase%2A> vytvořit instanci databáze.  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Pokud chcete zadat text k definování typů dat v tabulce T-SQL  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost přesný text, který používá T-SQL.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
