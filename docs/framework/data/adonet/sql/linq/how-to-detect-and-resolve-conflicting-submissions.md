---
title: 'Postupy: Zjištění a vyřešení konfliktních odeslání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 606231449263f1c26596ca8606a88053c6aded8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877276"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="1c6c1-102">Postupy: Zjištění a vyřešení konfliktních odeslání</span><span class="sxs-lookup"><span data-stu-id="1c6c1-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="1c6c1-103">poskytuje mnoho prostředků pro zjišťování a řešení konfliktů, které vyplývají z více uživatelů změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="1c6c1-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="1c6c1-104">Další informace najdete v tématu [jak: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="1c6c1-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c6c1-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c6c1-105">Example</span></span>  
 <span data-ttu-id="1c6c1-106">Následující příklad ukazuje `try` / `catch` blok, který zachytí <xref:System.Data.Linq.ChangeConflictException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="1c6c1-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="1c6c1-107">V okně konzoly se zobrazí informace o entitě a člen u každého konfliktu.</span><span class="sxs-lookup"><span data-stu-id="1c6c1-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c6c1-108">Je nutné uvést `using System.Reflection` – direktiva (`Imports System.Reflection` v jazyce Visual Basic) pro podporu načítání informací.</span><span class="sxs-lookup"><span data-stu-id="1c6c1-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="1c6c1-109">Další informace naleznete v tématu <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="1c6c1-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1c6c1-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c6c1-110">See also</span></span>

- [<span data-ttu-id="1c6c1-111">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="1c6c1-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="1c6c1-112">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="1c6c1-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
