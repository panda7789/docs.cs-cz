---
title: kompenzace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dd56b41b7b661b58446219d426be1a19edba059
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="compensation"></a><span data-ttu-id="a229a-102">kompenzace</span><span class="sxs-lookup"><span data-stu-id="a229a-102">Compensation</span></span>
<span data-ttu-id="a229a-103">Náhrada v [!INCLUDE[wf](../../../includes/wf-md.md)] mechanismus, pomocí kterého dříve dokončené práce odvolat nebo kompenzované (následující logiky definované aplikací.) Pokud dojde k následující chybě.</span><span class="sxs-lookup"><span data-stu-id="a229a-103">Compensation in [!INCLUDE[wf](../../../includes/wf-md.md)] is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="a229a-104">Tato část popisuje postup použití kompenzace v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="a229a-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="a229a-105">Kompenzace vs. Transakce</span><span class="sxs-lookup"><span data-stu-id="a229a-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="a229a-106">Transakce můžete kombinovat více operací do jedné jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="a229a-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="a229a-107">Pomocí transakce dává možnost přerušit všechny změny, které jsou spuštěny uvnitř transakce při výskytu chyby během libovolná součást procesu transakce (pouze vrácení) vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a229a-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="a229a-108">Použití transakcí však nemusí být vhodné v případě práce dlouho spuštěný.</span><span class="sxs-lookup"><span data-stu-id="a229a-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="a229a-109">Například cesta plánování aplikace je implementováno jako pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="a229a-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="a229a-110">Rezervace letu, čekají na schválení správce a pak platícího pro letu může obsahovat kroky pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a229a-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="a229a-111">Tento proces může trvat dlouho a není praktické kroky rezervace a platebního pro let k účasti ve stejné transakci.</span><span class="sxs-lookup"><span data-stu-id="a229a-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="a229a-112">Ve scénáři jako je tato kompenzace může vrátit zpět rezervaci krok pracovního postupu, pokud dojde k selhání později ve zpracování.</span><span class="sxs-lookup"><span data-stu-id="a229a-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a229a-113">Toto téma popisuje kompenzace v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="a229a-113">This topic covers compensation in workflows.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="a229a-114">transakce v pracovních postupech najdete v části [transakce](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) a <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="a229a-114"> transactions in workflows, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="a229a-115">transakce, najdete v části <xref:System.Transactions?displayProperty=nameWithType> a <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a229a-115"> transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="a229a-116">Pomocí CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="a229a-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="a229a-117"><xref:System.Activities.Statements.CompensableActivity>je základní kompenzace aktivity v [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a229a-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="a229a-118">Všech aktivit, které provádějí práci, kterou muset kompenzovat se umístí do <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="a229a-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="a229a-119">V tomto příkladu je umístěn krok rezervace nákup cestě do <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> a zrušení rezervace je umístěn do <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="a229a-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="a229a-120">Hned <xref:System.Activities.Statements.CompensableActivity> v pracovním postupu jsou dvě aktivity, které čekat na schválení správce a pak dokončete nákupu krok letu.</span><span class="sxs-lookup"><span data-stu-id="a229a-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="a229a-121">Pokud se chybová podmínka způsobí, že v pracovním postupu zrušit po <xref:System.Activities.Statements.CompensableActivity> bylo úspěšně dokončeno, pak aktivity v <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> jsou naplánovány obslužné rutiny a zrušení letu.</span><span class="sxs-lookup"><span data-stu-id="a229a-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="a229a-122">V následujícím příkladu je pracovní postup v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="a229a-122">The following example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="a229a-123">Po vyvolání pracovního postupu se zobrazí následující výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a229a-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="a229a-124">**ReserveFlight: Lístku je vyhrazena.**</span><span class="sxs-lookup"><span data-stu-id="a229a-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="a229a-125">**ManagerApproval: Schválení správce přijata.** </span><span class="sxs-lookup"><span data-stu-id="a229a-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="a229a-126">**PurchaseFlight: Lístku je zakoupili.** </span><span class="sxs-lookup"><span data-stu-id="a229a-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="a229a-127">**Pracovního postupu byla úspěšně dokončena se stavem: uzavřen.**</span><span class="sxs-lookup"><span data-stu-id="a229a-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="a229a-128">Ukázkové aktivity v tomto tématu, jako `ReserveFlight` pro konzolu tak, aby usnadnily vyjádření pořadí, ve kterém jsou prováděny aktivity, když dojde k kompenzace zobrazit jejich název a účel.</span><span class="sxs-lookup"><span data-stu-id="a229a-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="a229a-129">Výchozí kompenzace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a229a-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="a229a-130">Ve výchozím nastavení Pokud pracovní postup se zruší, logice kompenzace se spouští compensable aktivit, které má úspěšně úplně a již není potvrzena nebo kompenzované.</span><span class="sxs-lookup"><span data-stu-id="a229a-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a229a-131">Když <xref:System.Activities.Statements.CompensableActivity> je *potvrzen*, kompenzace aktivity již nelze vyvolat.</span><span class="sxs-lookup"><span data-stu-id="a229a-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="a229a-132">Proces potvrzení najdete dál v této části.</span><span class="sxs-lookup"><span data-stu-id="a229a-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="a229a-133">V tomto příkladu je vyvolána výjimka po letu je vyhrazena, ale před krokem schválení správce.</span><span class="sxs-lookup"><span data-stu-id="a229a-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="a229a-134">V tomto příkladu je pracovní postup v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="a229a-134">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="a229a-135">Po vyvolání pracovního postupu je simulované chyba podmínku výjimka ošetřena hostitele aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, pracovní postup se zruší a logiku kompenzace je volána.</span><span class="sxs-lookup"><span data-stu-id="a229a-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="a229a-136">**ReserveFlight: Lístku je vyhrazena.**</span><span class="sxs-lookup"><span data-stu-id="a229a-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="a229a-137">**SimulatedErrorCondition: Vyvolání ApplicationException –.** </span><span class="sxs-lookup"><span data-stu-id="a229a-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="a229a-138">**Pracovní postup neošetřená výjimka:** </span><span class="sxs-lookup"><span data-stu-id="a229a-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="a229a-139">**System.ApplicationException: Simulované chybový stav v pracovním postupu.** </span><span class="sxs-lookup"><span data-stu-id="a229a-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="a229a-140">**CancelFlight: Lístku je zrušena.** </span><span class="sxs-lookup"><span data-stu-id="a229a-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="a229a-141">**Pracovního postupu byla úspěšně dokončena se stavem: zrušena.**</span><span class="sxs-lookup"><span data-stu-id="a229a-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="a229a-142">Zrušení a CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="a229a-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="a229a-143">Pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> mít není dokončeno a zrušení aktivity aktivity v <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> provedení.</span><span class="sxs-lookup"><span data-stu-id="a229a-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a229a-144"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Je volána, pouze pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> nedokončili a zrušení aktivity.</span><span class="sxs-lookup"><span data-stu-id="a229a-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="a229a-145"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Je spustit pouze pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> úspěšně dokončena a kompenzace je následně vyvolána na aktivity.</span><span class="sxs-lookup"><span data-stu-id="a229a-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="a229a-146"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Dává možnost poskytnout všechny příslušné zrušení logiku autoři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a229a-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="a229a-147">V následujícím příkladu, je vyvolána výjimka při provádění <xref:System.Activities.Statements.CompensableActivity.Body%2A>a potom <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="a229a-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 <span data-ttu-id="a229a-148">V tomto příkladu je pracovní postup v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="a229a-148">This example is the workflow in XAML</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="a229a-149">Po vyvolání pracovního postupu je simulované chyba podmínku výjimka ošetřena hostitele aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, zrušení pracovního postupu a zrušení logiku <xref:System.Activities.Statements.CompensableActivity> je volána.</span><span class="sxs-lookup"><span data-stu-id="a229a-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="a229a-150">V tomto příkladu kompenzace logiku a logiku zrušení mít jiné cíle.</span><span class="sxs-lookup"><span data-stu-id="a229a-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="a229a-151">Pokud <xref:System.Activities.Statements.CompensableActivity.Body%2A> úspěšně dokončit, pak to znamená byl účtovat platební karty, letu zaznamenán, takže vyrovnání by měl vrátit oba kroky.</span><span class="sxs-lookup"><span data-stu-id="a229a-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="a229a-152">(V tomto příkladu zrušení letu automaticky zruší poplatky platební karty.) Ale pokud <xref:System.Activities.Statements.CompensableActivity> se zruší, to znamená <xref:System.Activities.Statements.CompensableActivity.Body%2A> nebyla úplný a tak logiku <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> musí být schopní určit, jak nejlépe zpracovat zrušení.</span><span class="sxs-lookup"><span data-stu-id="a229a-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="a229a-153">V tomto příkladu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zruší poplatků platební karty, ale od té doby `ReserveFlight` byl poslední aktivita v <xref:System.Activities.Statements.CompensableActivity.Body%2A>, se nebude pokoušet o zrušení letu.</span><span class="sxs-lookup"><span data-stu-id="a229a-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="a229a-154">Vzhledem k tomu `ReserveFlight` byl poslední aktivita v <xref:System.Activities.Statements.CompensableActivity.Body%2A>, pokud bylo úspěšně dokončeno potom <xref:System.Activities.Statements.CompensableActivity.Body%2A> by dokončili a žádné zrušení by bylo možné.</span><span class="sxs-lookup"><span data-stu-id="a229a-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="a229a-155">**ChargeCreditCard: Poplatků platební karty pro let.**</span><span class="sxs-lookup"><span data-stu-id="a229a-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="a229a-156">**SimulatedErrorCondition: Vyvolání ApplicationException –.** </span><span class="sxs-lookup"><span data-stu-id="a229a-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="a229a-157">**Pracovní postup neošetřená výjimka:** </span><span class="sxs-lookup"><span data-stu-id="a229a-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="a229a-158">**System.ApplicationException: Simulované chybový stav v pracovním postupu.** </span><span class="sxs-lookup"><span data-stu-id="a229a-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="a229a-159">**CancelCreditCard: Zrušit poplatky platební karty.** </span><span class="sxs-lookup"><span data-stu-id="a229a-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="a229a-160">**Pracovního postupu byla úspěšně dokončena se stavem: zrušena.**</span><span class="sxs-lookup"><span data-stu-id="a229a-160">**Workflow completed successfully with status: Canceled.**</span></span>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="a229a-161">zrušení, najdete v části [zrušení](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="a229a-161"> cancellation, see [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="a229a-162">Pomocí explicitní kompenzace odpovídajícím způsobem aktivity</span><span class="sxs-lookup"><span data-stu-id="a229a-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="a229a-163">V předchozím oddílu byla zahrnutých implicitní honoráře.</span><span class="sxs-lookup"><span data-stu-id="a229a-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="a229a-164">Implicitní kompenzace může být vhodné pro jednoduchého scénáře, ale pokud podrobnější je potřeba řízení nad plánováním kompenzace pak zpracování <xref:System.Activities.Statements.Compensate> lze aktivity.</span><span class="sxs-lookup"><span data-stu-id="a229a-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="a229a-165">Zahájíte proces kompenzace <xref:System.Activities.Statements.Compensate> aktivity, <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> pro které kompenzace se požaduje se používá.</span><span class="sxs-lookup"><span data-stu-id="a229a-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="a229a-166"><xref:System.Activities.Statements.Compensate> Aktivity lze použít k zahájení kompenzace na žádném Dokončit <xref:System.Activities.Statements.CompensableActivity> které nebyly potvrzeny ani kompenzované.</span><span class="sxs-lookup"><span data-stu-id="a229a-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="a229a-167">Například <xref:System.Activities.Statements.Compensate> aktivity může být používány <xref:System.Activities.Statements.TryCatch.Catches%2A> části <xref:System.Activities.Statements.TryCatch> aktivity nebo kdykoli po dokončení <xref:System.Activities.Statements.CompensableActivity> byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="a229a-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="a229a-168">V tomto příkladu <xref:System.Activities.Statements.Compensate> aktivita se používá v <xref:System.Activities.Statements.TryCatch.Catches%2A> části <xref:System.Activities.Statements.TryCatch> aktivitu pro vrácení akce <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="a229a-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="a229a-169">V tomto příkladu je pracovní postup v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="a229a-169">This example is the workflow in XAML.</span></span>  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 <span data-ttu-id="a229a-170">Po vyvolání pracovního postupu se zobrazí následující výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a229a-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="a229a-171">**ReserveFlight: Lístku je vyhrazena.**</span><span class="sxs-lookup"><span data-stu-id="a229a-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="a229a-172">**SimulatedErrorCondition: Vyvolání ApplicationException –.** </span><span class="sxs-lookup"><span data-stu-id="a229a-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="a229a-173">**CancelFlight: Lístku je zrušena.** </span><span class="sxs-lookup"><span data-stu-id="a229a-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="a229a-174">**Pracovního postupu byla úspěšně dokončena se stavem: uzavřen.**</span><span class="sxs-lookup"><span data-stu-id="a229a-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="a229a-175">Potvrzení kompenzace</span><span class="sxs-lookup"><span data-stu-id="a229a-175">Confirming Compensation</span></span>  
 <span data-ttu-id="a229a-176">Ve výchozím nastavení může být compensable aktivity vyrovnávat kdykoli po jejich dokončení.</span><span class="sxs-lookup"><span data-stu-id="a229a-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="a229a-177">V některých případech to nemusí být vhodné.</span><span class="sxs-lookup"><span data-stu-id="a229a-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="a229a-178">V předchozím příkladu vyrovnání pro rezervování lístek se o zrušení vyhrazení.</span><span class="sxs-lookup"><span data-stu-id="a229a-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="a229a-179">Po dokončení letu tento krok kompenzace je však již nebude platný.</span><span class="sxs-lookup"><span data-stu-id="a229a-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="a229a-180">Potvrzení compensable aktivity volá aktivita určeného <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="a229a-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="a229a-181">Možné použití pro tuto je umožnit všechny prostředky, které jsou nezbytné k provedení náhrady k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="a229a-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="a229a-182">Po compensable aktivity je potvrzen, není možné pro něj má být nahrazeno a pokud je tento pokus <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a229a-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="a229a-183">Po úspěšném dokončení pracovního postupu jsou všechny nepotvrzené a kompenzované compensable aktivity, které byl úspěšně dokončen v obráceném pořadí potvrdit dokončení.</span><span class="sxs-lookup"><span data-stu-id="a229a-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="a229a-184">V tomto příkladu je letu vyhrazené, zakoupených a dokončení a potom je potvrzen compensable aktivity.</span><span class="sxs-lookup"><span data-stu-id="a229a-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="a229a-185">Potvrďte <xref:System.Activities.Statements.CompensableActivity>, použijte <xref:System.Activities.Statements.Confirm> aktivity a zadejte <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> potvrďte.</span><span class="sxs-lookup"><span data-stu-id="a229a-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="a229a-186">V tomto příkladu je pracovní postup v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="a229a-186">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
 <span data-ttu-id="a229a-187">Po vyvolání pracovního postupu se zobrazí následující výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a229a-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="a229a-188">**ReserveFlight: Lístku je vyhrazena.**</span><span class="sxs-lookup"><span data-stu-id="a229a-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="a229a-189">**ManagerApproval: Schválení správce přijata.** </span><span class="sxs-lookup"><span data-stu-id="a229a-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="a229a-190">**PurchaseFlight: Lístku je zakoupili.** </span><span class="sxs-lookup"><span data-stu-id="a229a-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="a229a-191">**TakeFlight: Letu byla dokončena.** </span><span class="sxs-lookup"><span data-stu-id="a229a-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="a229a-192">**ConfirmFlight: Letu nebyla provedena, žádné honoráře možné.** </span><span class="sxs-lookup"><span data-stu-id="a229a-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="a229a-193">**Pracovního postupu byla úspěšně dokončena se stavem: uzavřen.**</span><span class="sxs-lookup"><span data-stu-id="a229a-193">**Workflow completed successfully with status: Closed.**</span></span>   
## <a name="nesting-compensation-activities"></a><span data-ttu-id="a229a-194">Vnoření kompenzace aktivity</span><span class="sxs-lookup"><span data-stu-id="a229a-194">Nesting Compensation Activities</span></span>  
 <span data-ttu-id="a229a-195">A <xref:System.Activities.Statements.CompensableActivity> náleží do <xref:System.Activities.Statements.CompensableActivity.Body%2A> části jiného <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="a229a-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="a229a-196">A <xref:System.Activities.Statements.CompensableActivity> nemusí být umístěny do obslužnou rutinu jiného <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="a229a-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="a229a-197">Je zodpovědností nadřazený <xref:System.Activities.Statements.CompensableActivity> zajistit, že, pokud je zrušen, potvrzení nebo kompenzované, všechny aktivity compensable podřízené, které byly úspěšně dokončeny a není již byly potvrzen nebo kompenzované musí být potvrzen nebo vyrovnávat před dokončením nadřazené zrušení, potvrzení nebo honoráře.</span><span class="sxs-lookup"><span data-stu-id="a229a-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="a229a-198">Pokud to není explicitně modelován nadřazené <xref:System.Activities.Statements.CompensableActivity> budou implicitně odpovídajícím způsobem podřízené compensable aktivity, pokud nadřazená přijme Storno nebo odpovídajícím způsobem signál.</span><span class="sxs-lookup"><span data-stu-id="a229a-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="a229a-199">Pokud nadřazená přijala signál potvrdit nadřazené potvrdí implicitně podřízené compensable aktivity.</span><span class="sxs-lookup"><span data-stu-id="a229a-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="a229a-200">Pokud logiku pro zpracování zrušení, potvrzení nebo kompenzace je explicitně modelován v obslužné rutině nadřazené <xref:System.Activities.Statements.CompensableActivity>, budou implicitně potvrzen všechny podřízené není explicitně zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="a229a-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a229a-201">Viz také</span><span class="sxs-lookup"><span data-stu-id="a229a-201">See Also</span></span>  
 <xref:System.Activities.Statements.CompensableActivity>  
 <xref:System.Activities.Statements.Compensate>  
 <xref:System.Activities.Statements.Confirm>  
 <xref:System.Activities.Statements.CompensationToken>  
 [<span data-ttu-id="a229a-202">Kompenzovatelná aktivita</span><span class="sxs-lookup"><span data-stu-id="a229a-202">Compensable Activity</span></span>](../../../docs/framework/windows-workflow-foundation/samples/compensable-activity-sample.md)
