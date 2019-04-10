---
title: 'Postupy: Znázornění sloupců jako sloupců časového razítka nebo verze'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: db73bf4880d8f5556247f7b037fca24b0ddc56d6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297886"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Postupy: Znázornění sloupců jako sloupců časového razítka nebo verze
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení pole nebo vlastnost jako představuje sloupci databáze, který obsahuje čísla časová razítka nebo verze databáze.  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>K určení pole nebo vlastnost jako sloupec časového razítka nebo verze  
  
1. Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2. Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> hodnoty vlastnosti `true`.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
