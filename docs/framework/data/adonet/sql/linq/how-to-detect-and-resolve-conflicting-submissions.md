---
title: 'Postupy: Zjištění a vyřešení konfliktních odeslání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ff33196f83e2c0d8d759e4ffc3fb7442e8ba0e3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940098"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="8fae5-102">Postupy: Zjištění a vyřešení konfliktních odeslání</span><span class="sxs-lookup"><span data-stu-id="8fae5-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8fae5-103">poskytuje mnoho prostředků pro zjišťování a řešení konfliktů, které vyplývají ze změn více uživatelů v databázi.</span><span class="sxs-lookup"><span data-stu-id="8fae5-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="8fae5-104">Další informace najdete v tématu [jak: Spravujte konflikty](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)změn.</span><span class="sxs-lookup"><span data-stu-id="8fae5-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fae5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fae5-105">Example</span></span>  
 <span data-ttu-id="8fae5-106">Následující `try` příklad ukazuje / <xref:System.Data.Linq.ChangeConflictException> blok, který zachycuje výjimku. `catch`</span><span class="sxs-lookup"><span data-stu-id="8fae5-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="8fae5-107">Informace o entitách a členech pro každý konflikt se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="8fae5-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fae5-108">Pro podporu načítání informací `using System.Reflection` musíte použít`Imports System.Reflection` direktivu (v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8fae5-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="8fae5-109">Další informace naleznete v tématu <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="8fae5-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8fae5-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fae5-110">See also</span></span>

- [<span data-ttu-id="8fae5-111">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="8fae5-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="8fae5-112">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="8fae5-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
