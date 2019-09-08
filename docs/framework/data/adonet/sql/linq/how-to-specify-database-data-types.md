---
title: 'Postupy: Zadání datových typů v databázi'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 09ca8dc6fa440138523bcd2905335a04517dd806
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793268"
---
# <a name="how-to-specify-database-data-types"></a>Postupy: Zadání datových typů v databázi
Použijte vlastnost u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu k určení přesného textu, který definuje sloupec v deklaraci tabulky T-SQL. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Vlastnost je nutné zadat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> pouze v případě, že plánujete použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A> k vytvoření instance databáze.  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Určení textu pro definování datového typu v tabulce T-SQL  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.  
  
2. Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnosti na přesný text, který je používán T-SQL.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
