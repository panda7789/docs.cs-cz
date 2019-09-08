---
title: 'Postupy: Odeslání změn do databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: c279d4ed32aed4788ee5866a24572663a1e2f580
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793103"
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="74a55-102">Postupy: Odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="74a55-102">How to: Submit Changes to the Database</span></span>
<span data-ttu-id="74a55-103">Bez ohledu na to, kolik změn provedete v objektech, jsou změny provedeny pouze v replikách v paměti.</span><span class="sxs-lookup"><span data-stu-id="74a55-103">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="74a55-104">Neudělali jste žádné změny v skutečných datech v databázi.</span><span class="sxs-lookup"><span data-stu-id="74a55-104">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="74a55-105">Vaše změny se neodesílají na server, dokud explicitně nebudete <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volat <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="74a55-105">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="74a55-106">Po provedení tohoto volání se <xref:System.Data.Linq.DataContext> pokusí přeložit změny do ekvivalentních příkazů SQL.</span><span class="sxs-lookup"><span data-stu-id="74a55-106">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="74a55-107">Pomocí vlastní logiky můžete tyto akce přepsat, ale pořadí odeslání je Orchestrované pomocí služby <xref:System.Data.Linq.DataContext> známé jako *procesor změn*.</span><span class="sxs-lookup"><span data-stu-id="74a55-107">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="74a55-108">Sekvence událostí je následující:</span><span class="sxs-lookup"><span data-stu-id="74a55-108">The sequence of events is as follows:</span></span>  
  
1. <span data-ttu-id="74a55-109">Když <xref:System.Data.Linq.DataContext.SubmitChanges%2A>zavoláte [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , prověřuje sadu známých objektů a určí, zda jsou k nim připojeny nové instance.</span><span class="sxs-lookup"><span data-stu-id="74a55-109">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="74a55-110">Pokud mají, tyto nové instance se přidají do sady sledovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="74a55-110">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2. <span data-ttu-id="74a55-111">Všechny objekty, které mají probíhající změny, jsou uspořádány do sekvence objektů na základě závislostí mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="74a55-111">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="74a55-112">Objekty, jejichž změny závisí na jiných objektech, se sekvencují po jejich závislosti.</span><span class="sxs-lookup"><span data-stu-id="74a55-112">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3. <span data-ttu-id="74a55-113">Ihned před odesláním jakýchkoli aktuálních změn [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí transakce k zapouzdření řady jednotlivých příkazů.</span><span class="sxs-lookup"><span data-stu-id="74a55-113">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4. <span data-ttu-id="74a55-114">Změny objektů jsou přeloženy jedním z nich na příkazy SQL a odeslány na server.</span><span class="sxs-lookup"><span data-stu-id="74a55-114">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="74a55-115">V tomto okamžiku všechny chyby zjištěné databází způsobují zastavení procesu odeslání a je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="74a55-115">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="74a55-116">Všechny změny v databázi se vrátí zpět, jako by nebyly k dispozici žádné odeslání.</span><span class="sxs-lookup"><span data-stu-id="74a55-116">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="74a55-117"><xref:System.Data.Linq.DataContext> Pořád má úplný záznam o všech změnách.</span><span class="sxs-lookup"><span data-stu-id="74a55-117">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="74a55-118">Proto se můžete pokusit problém vyřešit a zavolat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> znovu, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="74a55-118">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74a55-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="74a55-119">Example</span></span>  
 <span data-ttu-id="74a55-120">Pokud je transakce kolem odeslání úspěšně dokončena, <xref:System.Data.Linq.DataContext> akceptuje změny objektů ignorováním informací o sledování změn.</span><span class="sxs-lookup"><span data-stu-id="74a55-120">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="74a55-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74a55-121">See also</span></span>

- [<span data-ttu-id="74a55-122">Postupy: Zjištění a vyřešení konfliktních odeslání</span><span class="sxs-lookup"><span data-stu-id="74a55-122">How to: Detect and Resolve Conflicting Submissions</span></span>](how-to-detect-and-resolve-conflicting-submissions.md)
- [<span data-ttu-id="74a55-123">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="74a55-123">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="74a55-124">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="74a55-124">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="74a55-125">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="74a55-125">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
