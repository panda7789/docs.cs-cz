---
title: 'Postupy: Zadání kontroly konfliktů souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: fd3db5eb5dc9b74d8ea33af56dd522cf2f3fecdb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781584"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a>Postupy: Zadání kontroly konfliktů souběžnosti
Můžete určit, které sloupce databáze mají být kontrolovány pro konflikty souběžnosti při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Další informace najdete v tématu [jak: Určete, kteří členové jsou testováni pro konflikty](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)souběžnosti.  
  
## <a name="example"></a>Příklad  
 Následující kód určuje, že `HomePage` člen by neměl být nikdy testován během kontrol aktualizací. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
