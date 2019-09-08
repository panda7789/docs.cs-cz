---
title: 'Postupy: Určení, kdy se mají objevit výjimky souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: c0f41d23264bbe5c9130cb5a0b03686331bc92b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781617"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="c1cb9-102">Postupy: Určení, kdy se mají objevit výjimky souběžnosti</span><span class="sxs-lookup"><span data-stu-id="c1cb9-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="c1cb9-103">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systému je <xref:System.Data.Linq.ChangeConflictException> vyvolána výjimka, pokud se objekty neaktualizují z důvodu optimistického konfliktu souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="c1cb9-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="c1cb9-104">Další informace najdete v tématu [Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c1cb9-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="c1cb9-105">Před odesláním změn do databáze můžete určit, kdy by měly být vyvolány výjimky souběžnosti:</span><span class="sxs-lookup"><span data-stu-id="c1cb9-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="c1cb9-106">Vyvolat výjimku při prvním selhání (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="c1cb9-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="c1cb9-107">Dokončete všechny pokusy o aktualizaci, nashromáždí všechny selhání a nahlásí shromážděné chyby v výjimce<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>().</span><span class="sxs-lookup"><span data-stu-id="c1cb9-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="c1cb9-108">Při vyvolání <xref:System.Data.Linq.ChangeConflictException> poskytuje výjimka přístup <xref:System.Data.Linq.ChangeConflictCollection> ke kolekci.</span><span class="sxs-lookup"><span data-stu-id="c1cb9-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="c1cb9-109">Tato kolekce obsahuje podrobné informace o každém konfliktu (namapované na jeden neúspěšný pokus o aktualizaci), včetně <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> přístupu ke kolekci.</span><span class="sxs-lookup"><span data-stu-id="c1cb9-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="c1cb9-110">Každý členský konflikt se mapuje na jednoho člena v aktualizaci, u kterého došlo k selhání kontroly souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="c1cb9-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1cb9-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1cb9-111">Example</span></span>  
 <span data-ttu-id="c1cb9-112">Následující kód ukazuje příklady obou hodnot.</span><span class="sxs-lookup"><span data-stu-id="c1cb9-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c1cb9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1cb9-113">See also</span></span>

- [<span data-ttu-id="c1cb9-114">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="c1cb9-114">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="c1cb9-115">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="c1cb9-115">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
