---
title: 'Postupy: Přímé spuštění příkazů SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: eeac6272f176ac8e780b72b0076d032ad9e8f108
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903224"
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
