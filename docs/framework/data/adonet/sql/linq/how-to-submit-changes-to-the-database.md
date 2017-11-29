---
title: "Postupy: odeslání změn do databáze"
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
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 039eaac26833651fbd82dc1a69a31f394c1464c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="23063-102">Postupy: odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="23063-102">How to: Submit Changes to the Database</span></span>
<span data-ttu-id="23063-103">Bez ohledu na to, kolik změny k objektům jsou provedeny změny jenom pro repliky v paměti.</span><span class="sxs-lookup"><span data-stu-id="23063-103">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="23063-104">Žádné změny provedené na skutečná data v databázi.</span><span class="sxs-lookup"><span data-stu-id="23063-104">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="23063-105">Změny nejsou přenášeny do serveru, dokud explicitně volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="23063-105">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="23063-106">Pokud provedete toto volání <xref:System.Data.Linq.DataContext> pokusí přeložit změny do ekvivalentní příkazy SQL.</span><span class="sxs-lookup"><span data-stu-id="23063-106">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="23063-107">Vlastní logiky můžete přepsat tyto akce, ale pořadí odeslání je řízená službu <xref:System.Data.Linq.DataContext> známé jako *změnit procesoru*.</span><span class="sxs-lookup"><span data-stu-id="23063-107">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="23063-108">Posloupnost událostí je následující:</span><span class="sxs-lookup"><span data-stu-id="23063-108">The sequence of events is as follows:</span></span>  
  
1.  <span data-ttu-id="23063-109">Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prověřuje sadu objektů známé k určení, zda byly nové instance připojeny k nim.</span><span class="sxs-lookup"><span data-stu-id="23063-109">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="23063-110">Pokud budou mít, jsou tyto nové instance přidat do sady sledovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="23063-110">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2.  <span data-ttu-id="23063-111">Všechny objekty, které jsou čekající změny, jsou uspořádány do posloupnost objekty podle jejich vzájemné závislosti.</span><span class="sxs-lookup"><span data-stu-id="23063-111">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="23063-112">Objekty jejichž změny závisí na jiné objekty jsou seřazeny po jejich závislosti.</span><span class="sxs-lookup"><span data-stu-id="23063-112">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3.  <span data-ttu-id="23063-113">Bezprostředně před změny skutečné přenášejí, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí transakci zapouzdření řadu jednotlivé příkazy.</span><span class="sxs-lookup"><span data-stu-id="23063-113">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4.  <span data-ttu-id="23063-114">Změny objektů jsou přeložený postupně na příkazy SQL a odesílá na server.</span><span class="sxs-lookup"><span data-stu-id="23063-114">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="23063-115">V tomto okamžiku všech chyb zjištěných při databáze způsobit zastavení procesu odeslání a dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="23063-115">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="23063-116">Všechny změny do databáze jsou vráceny zpět, jako by se někdy došlo k chybě bez odesílání.</span><span class="sxs-lookup"><span data-stu-id="23063-116">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="23063-117"><xref:System.Data.Linq.DataContext> Má stále úplný záznam všech změn.</span><span class="sxs-lookup"><span data-stu-id="23063-117">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="23063-118">Proto můžete zkusit opravit problém a volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> znovu, jako v příkladu kódu, který následuje dále.</span><span class="sxs-lookup"><span data-stu-id="23063-118">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23063-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="23063-119">Example</span></span>  
 <span data-ttu-id="23063-120">Pokud transakce kolem odesílání je dokončeno, <xref:System.Data.Linq.DataContext> přijímá změny objektů, které informace o sledování změn je ignorována.</span><span class="sxs-lookup"><span data-stu-id="23063-120">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="23063-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="23063-121">See Also</span></span>  
 [<span data-ttu-id="23063-122">Postupy: zjištění a vyřešení konfliktu odesílání</span><span class="sxs-lookup"><span data-stu-id="23063-122">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 [<span data-ttu-id="23063-123">Postupy: Správa je v konfliktu změn</span><span class="sxs-lookup"><span data-stu-id="23063-123">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="23063-124">Stažení ukázkové databáze</span><span class="sxs-lookup"><span data-stu-id="23063-124">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="23063-125">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="23063-125">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
