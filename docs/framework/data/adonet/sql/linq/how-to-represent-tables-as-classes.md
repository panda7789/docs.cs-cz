---
title: 'Postupy: Znázornění tabulek jako tříd'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 1169def4e0180b1d14103d4a968ff3ed56f63d0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781759"
---
# <a name="how-to-represent-tables-as-classes"></a>Postupy: Znázornění tabulek jako tříd
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Použijteatributkoznačenítřídyjakotřídyentity<xref:System.Data.Linq.Mapping.TableAttribute> přidružené k tabulce databáze.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Mapování třídy na databázovou tabulku  
  
- <xref:System.Data.Linq.Mapping.TableAttribute> Přidejte atribut do deklarace třídy.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří `Customer` třídu jako třídu entity, která je přidružena `Customers` k tabulce databáze.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost není nutné zadávat, pokud je možné název odvodit. Pokud název nezadáte, název se považuje za shodný s názvem vlastnosti nebo pole.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
