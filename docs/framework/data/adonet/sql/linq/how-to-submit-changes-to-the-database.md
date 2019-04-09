---
title: 'Postupy: Odeslání změn do databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 572c4427ada06701c5982770ae476bd1c6c2b13a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082539"
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="f2a10-102">Postupy: Odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="f2a10-102">How to: Submit Changes to the Database</span></span>
<span data-ttu-id="f2a10-103">Bez ohledu na to, kolik změny, které provedete do objektů dojde ke změně pouze do replik v paměti.</span><span class="sxs-lookup"><span data-stu-id="f2a10-103">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="f2a10-104">Žádné změny provedené na skutečná data v databázi.</span><span class="sxs-lookup"><span data-stu-id="f2a10-104">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="f2a10-105">Změny nejsou přenášeny do serveru, dokud explicitně volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="f2a10-105">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="f2a10-106">Když provedete toto volání <xref:System.Data.Linq.DataContext> pokusí přeložit změny na ekvivalentní příkazy jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="f2a10-106">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="f2a10-107">Přepsat tyto akce můžete použít vlastní logiku, ale pořadí odeslání je orchestrovaných službou z <xref:System.Data.Linq.DataContext> označované jako *změnit procesoru*.</span><span class="sxs-lookup"><span data-stu-id="f2a10-107">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="f2a10-108">Posloupnost událostí je následující:</span><span class="sxs-lookup"><span data-stu-id="f2a10-108">The sequence of events is as follows:</span></span>  
  
1.  <span data-ttu-id="f2a10-109">Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prověřuje sadu známým objektům k určení, zda byly nové instance připojeny k nim.</span><span class="sxs-lookup"><span data-stu-id="f2a10-109">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="f2a10-110">Pokud ano, tyto nové instance se přidají do sady sledovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="f2a10-110">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2.  <span data-ttu-id="f2a10-111">Všechny objekty, které mají čekající změny jsou uspořádány do sekvence objektů na základě závislostí mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="f2a10-111">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="f2a10-112">Objekty, jejichž změny závisí na jiné objekty jsou seřazeny po jejich závislosti.</span><span class="sxs-lookup"><span data-stu-id="f2a10-112">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3.  <span data-ttu-id="f2a10-113">Bezprostředně před vlastní změny jsou přenášeny, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí transakci zapouzdřit posloupnost jednotlivých příkazů.</span><span class="sxs-lookup"><span data-stu-id="f2a10-113">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4.  <span data-ttu-id="f2a10-114">Změny objektů se přeložený jeden po druhém SQL příkazy a odeslat na server.</span><span class="sxs-lookup"><span data-stu-id="f2a10-114">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="f2a10-115">V tuto chvíli způsobit, že proces odeslání přestane všech chyb zjištěných v databázi a je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="f2a10-115">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="f2a10-116">Všechny změny do databáze se vrátí zpět, jako by se nikdy došlo k žádné příspěvky.</span><span class="sxs-lookup"><span data-stu-id="f2a10-116">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="f2a10-117"><xref:System.Data.Linq.DataContext> Má stále plnou záznam všech změn.</span><span class="sxs-lookup"><span data-stu-id="f2a10-117">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="f2a10-118">Proto můžete zkusit opravit problém a volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> znovu, stejně jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f2a10-118">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2a10-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2a10-119">Example</span></span>  
 <span data-ttu-id="f2a10-120">Když transakce po odeslání se dokončí úspěšně, <xref:System.Data.Linq.DataContext> přijímá změny objektů ignorováním informace sledování změn.</span><span class="sxs-lookup"><span data-stu-id="f2a10-120">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f2a10-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2a10-121">See also</span></span>

- [<span data-ttu-id="f2a10-122">Postupy: Zjištění a vyřešení konfliktních odeslání</span><span class="sxs-lookup"><span data-stu-id="f2a10-122">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)
- [<span data-ttu-id="f2a10-123">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="f2a10-123">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="f2a10-124">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="f2a10-124">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="f2a10-125">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="f2a10-125">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
