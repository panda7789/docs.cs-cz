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
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="3a1b3-102">Postupy: závorka odesílání dat pomocí transakce</span><span class="sxs-lookup"><span data-stu-id="3a1b3-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="3a1b3-103">Můžete použít <xref:System.Transactions.TransactionScope> k závorka vaší odesílání do databáze.</span><span class="sxs-lookup"><span data-stu-id="3a1b3-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="3a1b3-104">Další informace najdete v tématu [podpora transakcí](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="3a1b3-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a1b3-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a1b3-105">Example</span></span>  
 <span data-ttu-id="3a1b3-106">Následující kód uzavře odeslání databáze v <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="3a1b3-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3a1b3-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a1b3-107">See Also</span></span>  
 [<span data-ttu-id="3a1b3-108">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="3a1b3-108">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="3a1b3-109">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="3a1b3-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="3a1b3-110">Podpora transakcí</span><span class="sxs-lookup"><span data-stu-id="3a1b3-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
