---
title: "Postupy: Zadejte Kontrola konfliktu souběžnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6e69b97de78c469bd252319c49d362fe96af6833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-concurrency-conflict-checking"></a>Postupy: Zadejte Kontrola konfliktu souběžnosti
Můžete určit sloupce, které databáze jsou ke kontrole souběžnosti konflikty při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Další informace najdete v tématu [postup: Určete který členové jsou testovány souběžnosti konflikty](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
## <a name="example"></a>Příklad  
 Následující kód určuje, že `HomePage` člen by měl být vůbec neotestovali během kontroly aktualizací. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
