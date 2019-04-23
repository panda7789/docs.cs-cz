---
title: 'Postupy: Znázornění tabulek jako tříd'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 49e7d6768d8739bba94c9e8d38bcc582c8bd6e4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073132"
---
# <a name="how-to-represent-tables-as-classes"></a>Postupy: Znázornění tabulek jako tříd
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atribut k určení třídy jako třídu entity přidružené k databázové tabulky.  
  
### <a name="to-map-a-class-to-a-database-table"></a>K mapování třídy do tabulky databáze  
  
-   Přidat <xref:System.Data.Linq.Mapping.TableAttribute> atribut deklarace třídy.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří `Customer` třída jako třída entity, který je přidružen `Customers` databázové tabulky.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Není nutné určit <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> vlastnosti, pokud název jde odvodit. Pokud název nezadáte, název se považuje za stejný název jako vlastnost nebo pole.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
