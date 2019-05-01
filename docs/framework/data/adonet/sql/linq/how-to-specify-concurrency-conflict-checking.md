---
title: 'Postupy: Zadání kontroly konfliktů souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: 53d3ba6969705940c403795d3764c021f0829c64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033680"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a>Postupy: Zadání kontroly konfliktů souběžnosti
Můžete určit sloupce, které databáze jsou vráceny na konflikty souběžnosti, při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Další informace najdete v tématu [jak: Zadejte, kteří členové jsou testovat na konflikty souběžnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
## <a name="example"></a>Příklad  
 Následující kód určuje, že `HomePage` člen by měl být testován nikdy během kontroly aktualizací. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
