---
title: 'Postupy: zjištění a vyřešení konfliktu odesílání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: dfe1fac4285b915c316fb70d1e3bd1e7b99f145a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354391"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="24295-102">Postupy: zjištění a vyřešení konfliktu odesílání</span><span class="sxs-lookup"><span data-stu-id="24295-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="24295-103"> poskytuje mnoho prostředků pro zjišťování a řešení konfliktů, které vyplývají z více uživateli změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="24295-103"> provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="24295-104">Další informace najdete v tématu [postupy: Správa konfliktů změnu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="24295-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24295-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="24295-105">Example</span></span>  
 <span data-ttu-id="24295-106">Následující příklad ukazuje `try` / `catch` blok, který zachytí <xref:System.Data.Linq.ChangeConflictException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="24295-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="24295-107">Informace o jednotlivých konflikt entity a člen se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="24295-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24295-108">Musí zahrnovat `using System.Reflection` – direktiva (`Imports System.Reflection` v jazyce Visual Basic) pro podporu načítání informací.</span><span class="sxs-lookup"><span data-stu-id="24295-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="24295-109">Další informace naleznete v tématu <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="24295-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="24295-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="24295-110">See Also</span></span>  
 [<span data-ttu-id="24295-111">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="24295-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="24295-112">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="24295-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
