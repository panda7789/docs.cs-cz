---
title: 'Postupy: Určete, že se že mají objevit výjimky souběžnosti při'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: a6a9fa61685caffb7b2b5d1baf9640cb5ccfa31b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587161"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="e8100-102">Postupy: Určete, že se že mají objevit výjimky souběžnosti při</span><span class="sxs-lookup"><span data-stu-id="e8100-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="e8100-103">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, pokud objekty nelze aktualizovat kvůli konfliktům optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="e8100-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="e8100-104">Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e8100-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="e8100-105">Před odesláním změn databáze můžete zadat při by měl být vyvolání výjimky souběžnosti:</span><span class="sxs-lookup"><span data-stu-id="e8100-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
-   <span data-ttu-id="e8100-106">Vyvolání výjimky v prvním selhání (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="e8100-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
-   <span data-ttu-id="e8100-107">Dokončit všechny pokusy aktualizovat, accumulate všechny chyby a generování sestav nahromaděné chyby do výjimky (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="e8100-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="e8100-108">Při vyvolání, <xref:System.Data.Linq.ChangeConflictException> výjimek poskytuje přístup k <xref:System.Data.Linq.ChangeConflictCollection> kolekce.</span><span class="sxs-lookup"><span data-stu-id="e8100-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="e8100-109">Tato kolekce obsahuje podrobné informace pro každý konflikt (namapované na jedné aktualizace se nezdařila zkuste), včetně přístupu ke <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="e8100-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="e8100-110">Každý člen konflikt mapuje na jeden člen v aktualizaci, která se nezdařila se kontrola souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="e8100-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8100-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8100-111">Example</span></span>  
 <span data-ttu-id="e8100-112">Následující kód ukazuje příklady obě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8100-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e8100-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8100-113">See also</span></span>
- [<span data-ttu-id="e8100-114">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="e8100-114">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="e8100-115">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="e8100-115">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
