---
title: 'Postupy: představují tabulky jako třídy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 363efa4e4a6e3e7cfb757ee554e24a7963882278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-represent-tables-as-classes"></a>Postupy: představují tabulky jako třídy
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atribut určit třídu jako třídu entity, která je přidružená k tabulce databáze.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Pro mapování třídu do databázové tabulky  
  
-   Přidat <xref:System.Data.Linq.Mapping.TableAttribute> atribut deklaraci třídy.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří `Customer` třída jako třídu entity, který je spojen s `Customers` databázové tabulky.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Není nutné zadat <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> vlastnost, pokud název lze odvodit. Pokud název nezadáte, název se předpokládá, že se stejným názvem jako vlastnost nebo pole.  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
