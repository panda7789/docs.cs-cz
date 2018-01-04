---
title: "Postupy: závorka odesílání dat pomocí transakce"
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
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3481bcae3c67d08dc372195b6dba65c6b506b7f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Postupy: závorka odesílání dat pomocí transakce
Můžete použít <xref:System.Transactions.TransactionScope> k závorka vaší odesílání do databáze. Další informace najdete v tématu [podpora transakcí](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).  
  
## <a name="example"></a>Příklad  
 Následující kód uzavře odeslání databáze v <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Podpora transakcí](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
