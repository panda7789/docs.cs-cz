---
title: 'Postupy: Vytvoření transakčních sad pro odesílání dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 6a4c5ba7c4938b48fe489e43ff4a3ff806bd8916
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793815"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Postupy: Vytvoření transakčních sad pro odesílání dat
Můžete použít <xref:System.Transactions.TransactionScope> ke závoraci vašich odeslání do databáze. Další informace najdete v tématu [Podpora transakcí](transaction-support.md).  
  
## <a name="example"></a>Příklad  
 Následující kód uzavře odeslání databáze v <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Stažení ukázkových databází](downloading-sample-databases.md)
- [Vytvoření a odeslání změn dat](making-and-submitting-data-changes.md)
- [Podpora transakcí](transaction-support.md)
