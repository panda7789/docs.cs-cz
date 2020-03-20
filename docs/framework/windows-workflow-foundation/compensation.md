---
title: Kompenzace
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 75c5ed2f5e5c3a93834632ce499a2c8195fbc6bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183005"
---
# <a name="compensation"></a><span data-ttu-id="7cd35-102">Kompenzace</span><span class="sxs-lookup"><span data-stu-id="7cd35-102">Compensation</span></span>
<span data-ttu-id="7cd35-103">Kompenzace v základech pracovních postupů systému Windows (WF) je mechanismus, kterým lze dříve dokončenou práci vrátit zpět nebo kompenzovat (podle logiky definované aplikací) při následné chybě.</span><span class="sxs-lookup"><span data-stu-id="7cd35-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="7cd35-104">Tato část popisuje použití kompenzace v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="7cd35-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="7cd35-105">Kompenzace vs. transakce</span><span class="sxs-lookup"><span data-stu-id="7cd35-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="7cd35-106">Transakce umožňuje kombinovat více operací do jedné jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="7cd35-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="7cd35-107">Použití transakce dává vaší aplikaci možnost přerušit (vrátit zpět) všechny změny provedené v rámci transakce, pokud dojde k chybám během jakékoli části procesu transakce.</span><span class="sxs-lookup"><span data-stu-id="7cd35-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="7cd35-108">Použití transakcí však nemusí být vhodné, pokud je práce dlouho spuštěna.</span><span class="sxs-lookup"><span data-stu-id="7cd35-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="7cd35-109">Například aplikace plánování cesty je implementována jako pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="7cd35-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="7cd35-110">Kroky pracovního postupu se mohou skládat z rezervace letu, čekání na schválení manažerem a následné platby za let.</span><span class="sxs-lookup"><span data-stu-id="7cd35-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="7cd35-111">Tento proces může trvat mnoho dní a není praktické, aby se kroky rezervace a placení za let účastnily stejné transakce.</span><span class="sxs-lookup"><span data-stu-id="7cd35-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="7cd35-112">V takovém případě může být kompenzace použita k vrácení kroku rezervace pracovního postupu, pokud dojde k selhání později při zpracování.</span><span class="sxs-lookup"><span data-stu-id="7cd35-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cd35-113">Toto téma popisuje kompenzace v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="7cd35-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="7cd35-114">Další informace o transakcích v pracovních <xref:System.Activities.Statements.TransactionScope>postupech naleznete v [tématu Transakce](workflow-transactions.md) a .</span><span class="sxs-lookup"><span data-stu-id="7cd35-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="7cd35-115">Další informace o transakcích <xref:System.Transactions?displayProperty=nameWithType> <xref:System.Transactions.Transaction?displayProperty=nameWithType>naleznete v tématu a .</span><span class="sxs-lookup"><span data-stu-id="7cd35-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="7cd35-116">Použití compensableActivity</span><span class="sxs-lookup"><span data-stu-id="7cd35-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="7cd35-117"><xref:System.Activities.Statements.CompensableActivity>je hlavní kompenzační [!INCLUDE[wf1](../../../includes/wf1-md.md)]činností v oblasti .</span><span class="sxs-lookup"><span data-stu-id="7cd35-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="7cd35-118">Všechny činnosti, které vykonávají práci, kterou může <xref:System.Activities.Statements.CompensableActivity.Body%2A> být <xref:System.Activities.Statements.CompensableActivity>nutné kompenzovat, jsou umístěny do .</span><span class="sxs-lookup"><span data-stu-id="7cd35-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="7cd35-119">V tomto příkladu je rezervační krok nákupu <xref:System.Activities.Statements.CompensableActivity.Body%2A> letu <xref:System.Activities.Statements.CompensableActivity> umístěn do a a zrušení <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>rezervace je umístěno do .</span><span class="sxs-lookup"><span data-stu-id="7cd35-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="7cd35-120">Bezprostředně následující <xref:System.Activities.Statements.CompensableActivity> v pracovním postupu jsou dvě aktivity, které čekají na schválení manažera a pak dokončí nákupní krok letu.</span><span class="sxs-lookup"><span data-stu-id="7cd35-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="7cd35-121">Pokud chybový stav způsobí, že pracovní <xref:System.Activities.Statements.CompensableActivity> postup bude zrušen po úspěšném dokončení, jsou naplánovány aktivity v <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obslužné rutině a let je zrušen.</span><span class="sxs-lookup"><span data-stu-id="7cd35-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="7cd35-122">Následující příklad je pracovní postup v XAML.</span><span class="sxs-lookup"><span data-stu-id="7cd35-122">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="7cd35-123">Při vyvolání pracovního postupu se zobrazí následující výstup konzoly.</span><span class="sxs-lookup"><span data-stu-id="7cd35-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="7cd35-124">**ReserveFlight: Vstupenka je rezervována.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="7cd35-125">**Schválení manažera: Bylo přijato schválení správcem.** 
 **PurchaseFlight: Vstupenka je zakoupena.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Uzavřeno.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-125">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**Workflow completed successfully with status: Closed.**</span></span>
> [!NOTE]
> <span data-ttu-id="7cd35-126">Ukázkové aktivity v `ReserveFlight` tomto tématu, jako je například zobrazení jejich název a účel konzoly pomoci ilustrovat pořadí, ve kterém jsou prováděny aktivity, když dojde k kompenzaci.</span><span class="sxs-lookup"><span data-stu-id="7cd35-126">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="7cd35-127">Výchozí kompenzace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="7cd35-127">Default Workflow Compensation</span></span>  
 <span data-ttu-id="7cd35-128">Ve výchozím nastavení, pokud je pracovní postup zrušen, logika kompenzace je spuštěna pro všechny kompenzační aktivity, která byla úspěšně zcela a již nebyla potvrzena nebo kompenzována.</span><span class="sxs-lookup"><span data-stu-id="7cd35-128">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cd35-129">Pokud <xref:System.Activities.Statements.CompensableActivity> je *a potvrzena*, nelze již vyvolat kompenzaci za aktivitu.</span><span class="sxs-lookup"><span data-stu-id="7cd35-129">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="7cd35-130">Proces potvrzení je popsán dále v této části.</span><span class="sxs-lookup"><span data-stu-id="7cd35-130">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="7cd35-131">V tomto příkladu je vyvolána výjimka po letu je vyhrazena, ale před krokem schválení vedoucího.</span><span class="sxs-lookup"><span data-stu-id="7cd35-131">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="7cd35-132">Tento příklad je pracovní postup v XAML.</span><span class="sxs-lookup"><span data-stu-id="7cd35-132">This example is the workflow in XAML.</span></span>  
  
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
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="7cd35-133">Při vyvolání pracovního postupu je výjimka simulovaného chybového <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>stavu zpracována hostitelskou aplikací v aplikaci , pracovní postup je zrušen a je vyvolána logika kompenzace.</span><span class="sxs-lookup"><span data-stu-id="7cd35-133">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="7cd35-134">**ReserveFlight: Vstupenka je rezervována.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-134">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="7cd35-135">**SimulatedErrorCondition: Vyvolání applicationexception.** 
 **Neošetřená výjimka pracovního postupu:**
**System.ApplicationException: Simulovaná chybová podmínka v pracovním postupu.** 
 **CancelFlight: Letenka je zrušena.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Zrušeno.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-135">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Canceled.**</span></span>
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="7cd35-136">Zrušení a kompenzační aktivita</span><span class="sxs-lookup"><span data-stu-id="7cd35-136">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="7cd35-137">Pokud aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> v <xref:System.Activities.Statements.CompensableActivity> of a nebyly dokončeny a aktivita <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> je zrušena, aktivity v jsou prováděny.</span><span class="sxs-lookup"><span data-stu-id="7cd35-137">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cd35-138">Je <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> vyvolána pouze v případě, že aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> v rámci nebyly dokončeny <xref:System.Activities.Statements.CompensableActivity> a aktivita je zrušena.</span><span class="sxs-lookup"><span data-stu-id="7cd35-138">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="7cd35-139">Je <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> proveden pouze v případě, <xref:System.Activities.Statements.CompensableActivity.Body%2A> že <xref:System.Activities.Statements.CompensableActivity> aktivity v mají úspěšně dokončena a kompenzace je následně vyvolána na aktivitu.</span><span class="sxs-lookup"><span data-stu-id="7cd35-139">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="7cd35-140">Poskytuje <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> autorům pracovního postupu možnost poskytnout odpovídající logiku zrušení.</span><span class="sxs-lookup"><span data-stu-id="7cd35-140">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="7cd35-141">V následujícím příkladu je vyvolána výjimka <xref:System.Activities.Statements.CompensableActivity.Body%2A>během provádění <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , a potom je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="7cd35-141">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="7cd35-142">Tento příklad je pracovní postup v XAML</span><span class="sxs-lookup"><span data-stu-id="7cd35-142">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="7cd35-143">Při vyvolání pracovního postupu je výjimka simulovaného chybového <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>stavu zpracována hostitelskou aplikací v <xref:System.Activities.Statements.CompensableActivity> aplikaci , pracovní postup je zrušen a je vyvolána logika zrušení.</span><span class="sxs-lookup"><span data-stu-id="7cd35-143">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="7cd35-144">V tomto příkladu logiky kompenzace a zrušení logiky mají různé cíle.</span><span class="sxs-lookup"><span data-stu-id="7cd35-144">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="7cd35-145">Pokud <xref:System.Activities.Statements.CompensableActivity.Body%2A> byl úspěšně dokončen, znamená to, že kreditní karta byla naúčtována a let rezervován, takže kompenzace by měla vrátit oba kroky.</span><span class="sxs-lookup"><span data-stu-id="7cd35-145">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="7cd35-146">(V tomto příkladu zrušení letu automaticky zruší poplatky za kreditní kartu.) Však pokud <xref:System.Activities.Statements.CompensableActivity> je zrušena, to <xref:System.Activities.Statements.CompensableActivity.Body%2A> znamená, že nebyla <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> dokončena, a proto logika musí být schopen určit, jak nejlépe zpracovat zrušení.</span><span class="sxs-lookup"><span data-stu-id="7cd35-146">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="7cd35-147">V tomto příkladu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zruší poplatek za `ReserveFlight` platební kartu, ale <xref:System.Activities.Statements.CompensableActivity.Body%2A>protože byla poslední aktivita v , se nepokouší zrušit let.</span><span class="sxs-lookup"><span data-stu-id="7cd35-147">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="7cd35-148">Vzhledem k `ReserveFlight` tomu, <xref:System.Activities.Statements.CompensableActivity.Body%2A>že byla poslední aktivitou <xref:System.Activities.Statements.CompensableActivity.Body%2A> v oblasti , pokud by byla úspěšně dokončena, byla by dokončena a nebylo by možné zrušit.</span><span class="sxs-lookup"><span data-stu-id="7cd35-148">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="7cd35-149">**ChargeCreditCard: Strhávat kreditní kartu za let.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-149">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="7cd35-150">**SimulatedErrorCondition: Vyvolání applicationexception.** 
 **Neošetřená výjimka pracovního postupu:**
**System.ApplicationException: Simulovaná chybová podmínka v pracovním postupu.** 
 **CancelCreditCard: Zrušit poplatky za kreditní kartu.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Zrušeno.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-150">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelCreditCard: Cancel credit card charges.**
**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="7cd35-151">Další informace o zrušení naleznete v tématu [Zrušení](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="7cd35-151">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="7cd35-152">Explicitní kompenzace pomocí kompenzované aktivity</span><span class="sxs-lookup"><span data-stu-id="7cd35-152">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="7cd35-153">V předchozí části byla pokryta implicitní kompenzace.</span><span class="sxs-lookup"><span data-stu-id="7cd35-153">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="7cd35-154">Implicitní kompenzace může být vhodná pro jednoduché scénáře, ale pokud <xref:System.Activities.Statements.Compensate> je vyžadována více explicitní kontrola nad plánováním zpracování kompenzace, lze aktivitu použít.</span><span class="sxs-lookup"><span data-stu-id="7cd35-154">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="7cd35-155">Chcete-li zahájit <xref:System.Activities.Statements.Compensate> proces kompenzace s aktivitou, <xref:System.Activities.Statements.CompensationToken> používá <xref:System.Activities.Statements.CompensableActivity> se pro které je požadována kompenzace.</span><span class="sxs-lookup"><span data-stu-id="7cd35-155">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="7cd35-156">Aktivitu <xref:System.Activities.Statements.Compensate> lze použít k zahájení <xref:System.Activities.Statements.CompensableActivity> kompenzace za všechny dokončené, které nebyly potvrzeny nebo kompenzovány.</span><span class="sxs-lookup"><span data-stu-id="7cd35-156">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="7cd35-157">Aktivita <xref:System.Activities.Statements.Compensate> může být například <xref:System.Activities.Statements.TryCatch.Catches%2A> použita <xref:System.Activities.Statements.TryCatch> v části aktivity <xref:System.Activities.Statements.CompensableActivity> nebo kdykoli po dokončení.</span><span class="sxs-lookup"><span data-stu-id="7cd35-157">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="7cd35-158">V tomto příkladu se <xref:System.Activities.Statements.Compensate> aktivita používá v <xref:System.Activities.Statements.TryCatch.Catches%2A> části <xref:System.Activities.Statements.TryCatch> aktivity <xref:System.Activities.Statements.CompensableActivity>ke stornování akce .</span><span class="sxs-lookup"><span data-stu-id="7cd35-158">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="7cd35-159">Tento příklad je pracovní postup v XAML.</span><span class="sxs-lookup"><span data-stu-id="7cd35-159">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="7cd35-160">Při vyvolání pracovního postupu se zobrazí následující výstup konzoly.</span><span class="sxs-lookup"><span data-stu-id="7cd35-160">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="7cd35-161">**ReserveFlight: Vstupenka je rezervována.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-161">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="7cd35-162">**SimulatedErrorCondition: Vyvolání applicationexception.** 
 **CancelFlight: Letenka je zrušena.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Uzavřeno.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-162">**SimulatedErrorCondition: Throwing an ApplicationException.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Closed.**</span></span>
### <a name="confirming-compensation"></a><span data-ttu-id="7cd35-163">Potvrzení kompenzace</span><span class="sxs-lookup"><span data-stu-id="7cd35-163">Confirming Compensation</span></span>  
 <span data-ttu-id="7cd35-164">Ve výchozím nastavení mohou být kompenzační aktivity kompenzovány kdykoli po jejich dokončení.</span><span class="sxs-lookup"><span data-stu-id="7cd35-164">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="7cd35-165">V některých případech to nemusí být vhodné.</span><span class="sxs-lookup"><span data-stu-id="7cd35-165">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="7cd35-166">V předchozím příkladu bylo kompenzací za rezervaci letenky zrušení rezervace.</span><span class="sxs-lookup"><span data-stu-id="7cd35-166">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="7cd35-167">Po dokončení letu však tento kompenzační krok již není platný.</span><span class="sxs-lookup"><span data-stu-id="7cd35-167">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="7cd35-168">Potvrzení kompenzační aktivity vyvolá aktivitu určenou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>parametrem .</span><span class="sxs-lookup"><span data-stu-id="7cd35-168">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="7cd35-169">Jedním z možných použití pro toto je umožnit všechny prostředky, které jsou nezbytné k provedení kompenzace, které mají být uvolněny.</span><span class="sxs-lookup"><span data-stu-id="7cd35-169">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="7cd35-170">Po potvrzení kompenzační aktivity není možné, aby byla kompenzována, a pokud se <xref:System.InvalidOperationException> o to pokusíte, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7cd35-170">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="7cd35-171">Po úspěšném dokončení pracovního postupu jsou potvrzeny všechny nepotvrzené a nekompenzované kompenzační aktivity, které byly úspěšně dokončeny, v opačném pořadí dokončení.</span><span class="sxs-lookup"><span data-stu-id="7cd35-171">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="7cd35-172">V tomto příkladu je let rezervován, zakoupen a dokončen a poté je potvrzena kompenzační aktivita.</span><span class="sxs-lookup"><span data-stu-id="7cd35-172">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="7cd35-173">Chcete-li <xref:System.Activities.Statements.CompensableActivity>potvrdit <xref:System.Activities.Statements.Confirm> , použijte <xref:System.Activities.Statements.CompensationToken> aktivitu <xref:System.Activities.Statements.CompensableActivity> a zadejte potvrzení.</span><span class="sxs-lookup"><span data-stu-id="7cd35-173">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="7cd35-174">Tento příklad je pracovní postup v XAML.</span><span class="sxs-lookup"><span data-stu-id="7cd35-174">This example is the workflow in XAML.</span></span>  
  
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
  
<span data-ttu-id="7cd35-175">Při vyvolání pracovního postupu se zobrazí následující výstup konzoly.</span><span class="sxs-lookup"><span data-stu-id="7cd35-175">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="7cd35-176">**ReserveFlight: Vstupenka je rezervována.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-176">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="7cd35-177">**Schválení manažera: Bylo přijato schválení správcem.** 
 **PurchaseFlight: Vstupenka je zakoupena.** 
 **TakeFlight: Let je dokončen.** 
 **ConfirmFlight: Let byl přijat, žádná kompenzace není možná.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Uzavřeno.**</span><span class="sxs-lookup"><span data-stu-id="7cd35-177">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**TakeFlight: Flight is completed.**
**ConfirmFlight: Flight has been taken, no compensation possible.**
**Workflow completed successfully with status: Closed.**</span></span>

## <a name="nesting-compensation-activities"></a><span data-ttu-id="7cd35-178">Aktivity kompenzace vnoření</span><span class="sxs-lookup"><span data-stu-id="7cd35-178">Nesting Compensation Activities</span></span>  

<span data-ttu-id="7cd35-179">A <xref:System.Activities.Statements.CompensableActivity> může být <xref:System.Activities.Statements.CompensableActivity.Body%2A> umístěn do <xref:System.Activities.Statements.CompensableActivity>sekce jiného .</span><span class="sxs-lookup"><span data-stu-id="7cd35-179">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="7cd35-180">A <xref:System.Activities.Statements.CompensableActivity> nesmí být umístěndo obslužné rutiny jiného <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="7cd35-180">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="7cd35-181">Je odpovědností rodiče <xref:System.Activities.Statements.CompensableActivity> zajistit, aby při zrušení, potvrzení nebo kompenzaci byly všechny podřízené kompenzační činnosti, které úspěšně dokončily a které ještě nebyly potvrzeny nebo kompenzovány, potvrzeny nebo kompenzovány dříve, než rodič dokončí zrušení, potvrzení nebo náhradu.</span><span class="sxs-lookup"><span data-stu-id="7cd35-181">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="7cd35-182">Pokud to není modelováno <xref:System.Activities.Statements.CompensableActivity> explicitně nadřazený bude implicitně kompenzovat podřízené kompenzační aktivity, pokud nadřazený obdržel signál cancel nebo kompenziční.</span><span class="sxs-lookup"><span data-stu-id="7cd35-182">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="7cd35-183">Pokud rodič obdržel potvrzení signálu rodič implicitně potvrdí podřízené kompenzační činnosti.</span><span class="sxs-lookup"><span data-stu-id="7cd35-183">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="7cd35-184">Pokud logika pro zpracování zrušení, potvrzení nebo kompenzace je <xref:System.Activities.Statements.CompensableActivity>explicitně modelován v obslužné rutině nadřazené , všechny podřízené není explicitně zpracována bude implicitně potvrzena.</span><span class="sxs-lookup"><span data-stu-id="7cd35-184">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cd35-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cd35-185">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
