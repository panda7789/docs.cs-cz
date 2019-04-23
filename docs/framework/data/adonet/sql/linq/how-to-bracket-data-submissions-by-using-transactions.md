---
title: 'Postupy: Vytvoření transakčních sad pro odesílání dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 3e58c6f2849ed9714b3356662dae313ab9d11696
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134001"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="9ead5-102">Postupy: Vytvoření transakčních sad pro odesílání dat</span><span class="sxs-lookup"><span data-stu-id="9ead5-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="9ead5-103">Můžete použít <xref:System.Transactions.TransactionScope> k vašim příspěvkům poskytnutým prostřednictvím databázi závorka.</span><span class="sxs-lookup"><span data-stu-id="9ead5-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="9ead5-104">Další informace najdete v tématu [podpora transakcí](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="9ead5-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ead5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ead5-105">Example</span></span>  
 <span data-ttu-id="9ead5-106">Následující kód obklopuje odesílání databáze v <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="9ead5-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9ead5-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ead5-107">See also</span></span>

- [<span data-ttu-id="9ead5-108">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="9ead5-108">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="9ead5-109">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="9ead5-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="9ead5-110">Podpora transakcí</span><span class="sxs-lookup"><span data-stu-id="9ead5-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
