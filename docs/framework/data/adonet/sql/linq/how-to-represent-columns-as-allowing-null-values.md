---
title: 'Postupy: Znázornění sloupců jako povolujících hodnoty Null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: ba362e45c8694dbb30e977b3d9f25702ee9dea48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715527"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a>Postupy: Znázornění sloupců jako povolujících hodnoty Null
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení, že sloupec přidružená databáze může obsahovat hodnoty null.  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a>K označení sloupce jako povolujících hodnoty null  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> hodnoty vlastnosti `true`.  
  
## <a name="see-also"></a>Viz také:
- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
