---
title: 'Postupy: Znázornění sloupců jako členů tříd'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 74966dd1661faa43df334987b2e3b0e84eff3446
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073998"
---
# <a name="how-to-represent-columns-as-class-members"></a>Postupy: Znázornění sloupců jako členů tříd
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> atributu na pole nebo vlastnost přidružit sloupce databáze.  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Mapovat pole nebo vlastnost ke sloupci databáze  
  
-   Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut deklaraci vlastnosti nebo pole.  
  
## <a name="example"></a>Příklad  
 Následující map kódu `CustomerID` pole `Customer` třídu `CustomerID` sloupec v `Customers` databázové tabulky.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Není nutné určit <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> vlastnosti, pokud název jde odvodit. Pokud název nezadáte, název se považuje za stejný název jako vlastnost nebo pole.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
