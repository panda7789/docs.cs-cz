---
title: 'Postupy: Přímé spuštění příkazů SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 0ca62c0affc282140eb36979baafb8e3f9c89c35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737543"
---
# <a name="how-to-directly-execute-sql-commands"></a>Postupy: Přímé spuštění příkazů SQL
Za předpokladu, že <xref:System.Data.Linq.DataContext> připojení, můžete použít <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> ke spuštění příkazů SQL, které nevracejí objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad způsobí, že SQL Server a zvyšuje UnitPrice 1,00.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Přímé spuštění dotazů SQL](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)
- [Komunikace s databází](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
