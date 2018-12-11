---
title: Potvrzení transakce v jedné fázi a více fázích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: ad0b639aec60fc1dc9b594ff774232699001db5d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53142916"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="f09a3-102">Potvrzení transakce v jedné fázi a více fázích</span><span class="sxs-lookup"><span data-stu-id="f09a3-102">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="f09a3-103">Každý prostředek, který používá v transakci spravuje správce prostředků (SV), jejichž akce jsou koordinovaný správcem transakcí (TM).</span><span class="sxs-lookup"><span data-stu-id="f09a3-103">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="f09a3-104">[Uvedení prostředků jako účastníků v transakci](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) téma popisuje, jak prostředek (nebo více zdrojů) může být uveden v transakci.</span><span class="sxs-lookup"><span data-stu-id="f09a3-104">The [Enlisting Resources as Participants in a Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="f09a3-105">Toto téma popisuje, jak lze koordinovat mezi zařazených prostředků částku transakce.</span><span class="sxs-lookup"><span data-stu-id="f09a3-105">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="f09a3-106">Na konci transakce aplikace požádá o transakce, které má být buď potvrzené nebo vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="f09a3-106">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="f09a3-107">Správce transakcí musí odstranění ohrožení, jako je někteří správci prostředků hlasování se zapsat while ostatním uživatelům hlasování se navrátit transakci.</span><span class="sxs-lookup"><span data-stu-id="f09a3-107">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="f09a3-108">Pokud vaše transakce zahrnuje více než jeden prostředek, je nutné provést dvoufázového potvrzení (2PC).</span><span class="sxs-lookup"><span data-stu-id="f09a3-108">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="f09a3-109">Protokol dvoufázového potvrzení (fáze prepare a potvrzovací fáze) zajišťuje, že při transakci skončí, všechny změny na všechny zdroje jsou buď zcela potvrzené nebo plně vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="f09a3-109">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="f09a3-110">Všichni účastníci jsou pak informováni o konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="f09a3-110">All the participants are then informed of the final result.</span></span> <span data-ttu-id="f09a3-111">Podrobné informace o protokolu dvoufázového potvrzení, naleznete v příručce "*zpracování transakcí: Koncepty a techniky (Nováková Kaufmann řady ve systémů pro správu dat) ISBN: 1558601902*"podle Jima šedá.</span><span class="sxs-lookup"><span data-stu-id="f09a3-111">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="f09a3-112">Můžete také optimalizovat vaši transakci výkon provedením součást v protokolu jedné fáze potvrzení.</span><span class="sxs-lookup"><span data-stu-id="f09a3-112">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="f09a3-113">Další informace najdete v tématu [optimalizace pomocí Jednofázového potvrzení a možné zařazení Jednofázového oznámení](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="f09a3-113">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="f09a3-114">Pokud jste právě chcete být informováni o výsledek transakce a nechcete, aby se účastnit programu hlasování, byste měli zaregistrovat pro <xref:System.Transactions.Transaction.TransactionCompleted> události.</span><span class="sxs-lookup"><span data-stu-id="f09a3-114">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="f09a3-115">Bezdrátové potvrzení (2PC)</span><span class="sxs-lookup"><span data-stu-id="f09a3-115">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="f09a3-116">V první fázi transakce dotazuje správce transakcí každý zdroj k určení, zda transakce potvrzena nebo vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="f09a3-116">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="f09a3-117">Správce transakcí upozorní ve druhé fázi transakce každý zdroj výsledku své dotazy, díky kterému jej provést všechny potřebné vyčištění.</span><span class="sxs-lookup"><span data-stu-id="f09a3-117">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="f09a3-118">K účasti v tento druh transakce, musí implementovat správce prostředků <xref:System.Transactions.IEnlistmentNotification> rozhraní, které poskytuje metody, jež jsou volány správce TM jako oznámení během 2PC.</span><span class="sxs-lookup"><span data-stu-id="f09a3-118">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="f09a3-119">Následující příklad ukazuje příklad tohoto provádění.</span><span class="sxs-lookup"><span data-stu-id="f09a3-119">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="f09a3-120">Připravit fáze (fáze 1)</span><span class="sxs-lookup"><span data-stu-id="f09a3-120">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="f09a3-121">Při přijímání <xref:System.Transactions.CommittableTransaction.Commit%2A> požadavků z aplikace, správce transakcí začíná Příprava fáze zařazených účastníci voláním <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metodu na každý zapsán prostředku, za účelem získání hlas každý zdroj v transakci.</span><span class="sxs-lookup"><span data-stu-id="f09a3-121">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="f09a3-122">Váš správce prostředků, který implementuje <xref:System.Transactions.IEnlistmentNotification> by měl první implementaci rozhraní <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> jako následující jednoduchý příklad ukazuje metodu.</span><span class="sxs-lookup"><span data-stu-id="f09a3-122">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
```csharp
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 <span data-ttu-id="f09a3-123">Pokud správce prostředků trvalý obdrží toto volání, ji má protokolovat informace o obnovení transakce (k dispozici načtením <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> vlastnost) a libovolné informace, které jsou nezbytné pro dokončení transakce na potvrzení.</span><span class="sxs-lookup"><span data-stu-id="f09a3-123">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="f09a3-124">Toto není nutné provádět v rámci <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metoda vzhledem k tomu, že správce prostředků to lze provést v pracovní podproces.</span><span class="sxs-lookup"><span data-stu-id="f09a3-124">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="f09a3-125">Pokud správce prostředků dokončil jeho připravit pracovní, by měl hlasovat potvrzení nebo vrátit zpět voláním <xref:System.Transactions.PreparingEnlistment.Prepared%2A> nebo <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f09a3-125">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="f09a3-126">Všimněte si, že <xref:System.Transactions.PreparingEnlistment> třída dědí <xref:System.Transactions.Enlistment.Done%2A> metody z <xref:System.Transactions.Enlistment> třídy.</span><span class="sxs-lookup"><span data-stu-id="f09a3-126">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="f09a3-127">Pokud tuto metodu lze volat na <xref:System.Transactions.PreparingEnlistment> zpětného volání ve fázi Prepare, informuje správce TM, je jen pro čtení zařazení (to znamená, že správce prostředků, které může číst, ale ochranou transakcí data nelze aktualizovat) a správce prostředků obdrží žádné další oznámení z správce transakcí tak, aby výsledek transakce ve fázi 2.</span><span class="sxs-lookup"><span data-stu-id="f09a3-127">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="f09a3-128">Aplikace je oznámen úspěšné úsilí transakce po hlasovat, že všechny správce prostředků <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span><span class="sxs-lookup"><span data-stu-id="f09a3-128">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="f09a3-129">Potvrzení fáze (fáze 2)</span><span class="sxs-lookup"><span data-stu-id="f09a3-129">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="f09a3-130">Ve druhém fáze transakce, pokud správce transakcí přijme úspěšné připraví z všechny správce prostředků (uplatnit všechny správce prostředků <xref:System.Transactions.PreparingEnlistment.Prepared%2A> na konci fáze 1), vyvolá <xref:System.Transactions.IEnlistmentNotification.Commit%2A> metodu pro každého správce prostředků.</span><span class="sxs-lookup"><span data-stu-id="f09a3-130">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="f09a3-131">Správci prostředků můžete provést změny trvalý a dokončení potvrzení.</span><span class="sxs-lookup"><span data-stu-id="f09a3-131">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="f09a3-132">Pokud některý správce prostředků nahlášena chyba připravit ve fázi 1, vyvolá správce transakcí <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> metodu pro každého správce prostředků a které identifikuje selhání potvrzení do aplikace.</span><span class="sxs-lookup"><span data-stu-id="f09a3-132">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="f09a3-133">Váš správce prostředků tedy měli používat následující metody.</span><span class="sxs-lookup"><span data-stu-id="f09a3-133">Thus, your resource manager should implement the following methods.</span></span>  
  
```csharp
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment    
     enlistment.Done();    
}  
```  
  
 <span data-ttu-id="f09a3-134">Správce prostředků by měl provádět každé dílo, které jsou nezbytné pro dokončení transakce v závislosti na typu oznámení a informovat TM, který byl dokončen voláním <xref:System.Transactions.Enlistment.Done%2A> metodu na <xref:System.Transactions.Enlistment> parametru.</span><span class="sxs-lookup"><span data-stu-id="f09a3-134">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="f09a3-135">Tato práce lze provést na pracovní podproces.</span><span class="sxs-lookup"><span data-stu-id="f09a3-135">This work can be done on a worker thread.</span></span> <span data-ttu-id="f09a3-136">Všimněte si, že oznámení fáze 2 může dojít, vložený ve stejném vlákně, který volal <xref:System.Transactions.PreparingEnlistment.Prepared%2A> metoda ve fázi 1.</span><span class="sxs-lookup"><span data-stu-id="f09a3-136">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="f09a3-137">Jako takové neměli byste každé dílo po <xref:System.Transactions.PreparingEnlistment.Prepared%2A> volání (například uvolňující uzamčení), které očekáváte dokončili před přijímala oznámení fáze 2.</span><span class="sxs-lookup"><span data-stu-id="f09a3-137">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="f09a3-138">Implementace InDoubt</span><span class="sxs-lookup"><span data-stu-id="f09a3-138">Implementing InDoubt</span></span>  
 <span data-ttu-id="f09a3-139">A konečně, měli byste implementovat <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> metody pro správce těkavých prostředků.</span><span class="sxs-lookup"><span data-stu-id="f09a3-139">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="f09a3-140">Tato metoda je volána, pokud správce transakcí ztratí kontaktu s jedním nebo více účastníky, tak jejich stav není znám.</span><span class="sxs-lookup"><span data-stu-id="f09a3-140">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="f09a3-141">V takovém případě je zapotřebí přihlásit tuto skutečnost tak, aby si můžete později zjistit, zda některé z účastníci transakce byla ponechána v nekonzistentním stavu.</span><span class="sxs-lookup"><span data-stu-id="f09a3-141">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="f09a3-142">Optimalizace potvrzení jedna fáze</span><span class="sxs-lookup"><span data-stu-id="f09a3-142">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="f09a3-143">Vzhledem k tomu, že všechny aktualizace jsou provedeno bez explicitního koordinace je efektivnější v době běhu protokol jedné fáze potvrzení.</span><span class="sxs-lookup"><span data-stu-id="f09a3-143">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="f09a3-144">Další informace o tomto protokolu naleznete v tématu [optimalizace pomocí Jednofázového potvrzení a možné zařazení Jednofázového oznámení](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="f09a3-144">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09a3-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="f09a3-145">See Also</span></span>  
 [<span data-ttu-id="f09a3-146">Optimalizace pomocí jednofázového potvrzení a možné zařazení jednofázového oznámení</span><span class="sxs-lookup"><span data-stu-id="f09a3-146">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
 [<span data-ttu-id="f09a3-147">Uvedení prostředků jako účastníků v transakci</span><span class="sxs-lookup"><span data-stu-id="f09a3-147">Enlisting Resources as Participants in a Transaction</span></span>](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
