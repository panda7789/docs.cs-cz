---
title: 'Postupy: představují primární klíče'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: dae8603a18318f45182c7148b10b8194e67fd017
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-represent-primary-keys"></a>Postupy: představují primární klíče
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost na <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut a nastavit vlastnost nebo pole představující primární klíč pro sloupci databáze.  
  
 Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Počítané sloupce nepodporuje jako primární klíče.  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>Chcete-li určit vlastnost nebo pole jako primární klíč  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Zadejte hodnotu jako `true`.  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
