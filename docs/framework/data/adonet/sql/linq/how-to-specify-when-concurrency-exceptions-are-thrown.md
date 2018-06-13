---
title: 'Postupy: Zadejte, když nastanou výjimky souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 6890cc130f4f4101c02bb88c5f5666bcd5cf9b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360816"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="36285-102">Postupy: Zadejte, když nastanou výjimky souběžnosti</span><span class="sxs-lookup"><span data-stu-id="36285-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="36285-103">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> při objekty nelze aktualizovat z důvodu konfliktu optimistickou metodu souběžného je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="36285-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="36285-104">Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="36285-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="36285-105">Před odesláním změny do databáze, můžete zadat, když by měl být vyvolány souběžného zpracování výjimky:</span><span class="sxs-lookup"><span data-stu-id="36285-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
-   <span data-ttu-id="36285-106">Throw – výjimka v prvním selhání (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="36285-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
-   <span data-ttu-id="36285-107">Dokončit všechny aktualizace pokusů hromadit všechny chyby a sestavy Akumulovaná selhání v výjimce (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="36285-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="36285-108">Při vyvolání, <xref:System.Data.Linq.ChangeConflictException> výjimka poskytuje přístup k <xref:System.Data.Linq.ChangeConflictCollection> kolekce.</span><span class="sxs-lookup"><span data-stu-id="36285-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="36285-109">Tato kolekce obsahuje podrobné informace pro každý konflikt (namapované na zkuste jeden Chyba aktualizace), včetně přístupu ke <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="36285-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="36285-110">Každý člen konflikt mapuje jednoho člena v aktualizaci, která se nezdařila kontrola souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="36285-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36285-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="36285-111">Example</span></span>  
 <span data-ttu-id="36285-112">Následující kód ukazuje příklady obě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36285-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="36285-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="36285-113">See Also</span></span>  
 [<span data-ttu-id="36285-114">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="36285-114">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="36285-115">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="36285-115">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
