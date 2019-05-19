---
title: 'Postupy: Opakované použití propojení mezi příkazem ADO.NET a položkou DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 92b0d8cf2c4904fabc17241ef2c31175f0c87baf
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878539"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Postupy: Opakované použití propojení mezi příkazem ADO.NET a položkou DataContext
Protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí rodiny technologie ADO.NET a je podle předpokladu ADO.NET, můžete využít připojení mezi příkazem ADO.NET a <xref:System.Data.Linq.DataContext>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak znovu použít stejné připojení mezi příkazem ADO.NET a <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [ADO.NET a LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [Komunikace s databází](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
