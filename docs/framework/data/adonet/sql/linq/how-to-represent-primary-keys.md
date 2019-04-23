---
title: 'Postupy: Znázornění primárních klíčů'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: dcb8929c9cd9a7b88f19d760b70117a1092760f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295585"
---
# <a name="how-to-represent-primary-keys"></a>Postupy: Znázornění primárních klíčů
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení vlastnost nebo pole představující primární klíč pro sloupce databáze.  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Počítané sloupce nepodporuje jako primární klíče.  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>Chcete-li určit vlastnost nebo pole jako primární klíč  
  
1. Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2. Zadejte hodnotu jako `true`.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
