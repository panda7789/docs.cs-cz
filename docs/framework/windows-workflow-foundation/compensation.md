---
title: Kompenzace
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 147da26fd297d41876815cffcc70450ae905ba85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935432"
---
# <a name="compensation"></a><span data-ttu-id="75da2-102">Kompenzace</span><span class="sxs-lookup"><span data-stu-id="75da2-102">Compensation</span></span>
<span data-ttu-id="75da2-103">Kompenzace v programovací model Windows Workflow Foundation (WF) je mechanismus, pomocí kterého se dřív dokončená práce může vrátit zpátky nebo kompenzovat (podle logiky definované aplikací), když dojde k následnému selhání.</span><span class="sxs-lookup"><span data-stu-id="75da2-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="75da2-104">V této části se dozvíte, jak používat kompenzace v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="75da2-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="75da2-105">Kompenzace vs. Transakce</span><span class="sxs-lookup"><span data-stu-id="75da2-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="75da2-106">Transakce umožňuje kombinovat více operací do jediné pracovní jednotky.</span><span class="sxs-lookup"><span data-stu-id="75da2-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="75da2-107">Použití transakce poskytuje vaší aplikaci možnost přerušení (vrácení zpět) všechny změny provedené v rámci transakce, pokud dojde k jakýmkoli chybám během jakékoli části procesu transakce.</span><span class="sxs-lookup"><span data-stu-id="75da2-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="75da2-108">Použití transakcí ale nemusí být vhodné, pokud je práce dlouhodobě spuštěná.</span><span class="sxs-lookup"><span data-stu-id="75da2-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="75da2-109">Například aplikace pro plánování cest je implementována jako pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="75da2-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="75da2-110">Kroky pracovního postupu se můžou skládat z rezervace letu, čekání na schválení manažera a pak za tento let platit.</span><span class="sxs-lookup"><span data-stu-id="75da2-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="75da2-111">Tento proces může trvat mnoho dnů a není praktický pro kroky rezervace a placení za letu, aby se mohl zúčastnit stejné transakce.</span><span class="sxs-lookup"><span data-stu-id="75da2-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="75da2-112">Ve scénářích, jako je to, je možné použít kompenzaci k vrácení kroku rezervace pracovního postupu, pokud dojde k selhání později během zpracování.</span><span class="sxs-lookup"><span data-stu-id="75da2-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75da2-113">Toto téma popisuje kompenzace v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="75da2-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="75da2-114">Další informace o transakcích v pracovních postupech najdete [](workflow-transactions.md) v tématu <xref:System.Activities.Statements.TransactionScope>transakce a.</span><span class="sxs-lookup"><span data-stu-id="75da2-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="75da2-115">Další informace o transakcích naleznete v <xref:System.Transactions?displayProperty=nameWithType> tématu <xref:System.Transactions.Transaction?displayProperty=nameWithType>a.</span><span class="sxs-lookup"><span data-stu-id="75da2-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="75da2-116">Použití aktivita CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="75da2-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="75da2-117"><xref:System.Activities.Statements.CompensableActivity>je základní aktivitou kompenzace [!INCLUDE[wf1](../../../includes/wf1-md.md)]v.</span><span class="sxs-lookup"><span data-stu-id="75da2-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="75da2-118">Všechny aktivity, které provádějí práci, které mohou být potřeba kompenzovat, jsou umístěny do <xref:System.Activities.Statements.CompensableActivity.Body%2A> části <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="75da2-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="75da2-119">V tomto příkladu je krok rezervace při nákupu letu umístěný do <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> a a zrušení <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>rezervace se umístí do.</span><span class="sxs-lookup"><span data-stu-id="75da2-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="75da2-120">Hned po <xref:System.Activities.Statements.CompensableActivity> dokončení pracovního postupu jsou dvě aktivity, které čekají na schválení manažerem a pak dokončí krok nákupu letu.</span><span class="sxs-lookup"><span data-stu-id="75da2-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="75da2-121">Pokud chybový stav způsobí zrušení pracovního postupu po <xref:System.Activities.Statements.CompensableActivity> úspěšném dokončení, aktivity <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> v obslužné rutině se naplánují a let se zruší.</span><span class="sxs-lookup"><span data-stu-id="75da2-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="75da2-122">V následujícím příkladu je pracovní postup v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="75da2-122">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="75da2-123">Po vyvolání pracovního postupu se do konzoly zobrazí následující výstup.</span><span class="sxs-lookup"><span data-stu-id="75da2-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="75da2-124">**ReserveFlight: Lístek je rezervovaný.**</span><span class="sxs-lookup"><span data-stu-id="75da2-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="75da2-125">**ManagerApproval: Bylo přijato schválení správcem.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="75da2-126">**PurchaseFlight: Lístek je koupený.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="75da2-127">**Pracovní postup byl úspěšně dokončen se stavem: Ukončit.**</span><span class="sxs-lookup"><span data-stu-id="75da2-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
> <span data-ttu-id="75da2-128">Ukázkové aktivity v tomto tématu, jako je `ReserveFlight` například zobrazení jejich názvu a účelu pro konzolu, aby pomohly objasnění pořadí, ve kterém jsou aktivity spouštěny, když dojde k kompenzaci.</span><span class="sxs-lookup"><span data-stu-id="75da2-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="75da2-129">Výchozí kompenzace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="75da2-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="75da2-130">Ve výchozím nastavení platí, že pokud je pracovní postup zrušen, je logika kompenzace spuštěna pro všechny aktivity kompenzovatelná, které byly úspěšně dokončeny a dosud nebyly potvrzeny nebo vyrovnány.</span><span class="sxs-lookup"><span data-stu-id="75da2-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75da2-131">Pokud je potvrzeno, kompenzace aktivity již nelze vyvolat. <xref:System.Activities.Statements.CompensableActivity></span><span class="sxs-lookup"><span data-stu-id="75da2-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="75da2-132">Potvrzovací proces je popsán dále v této části.</span><span class="sxs-lookup"><span data-stu-id="75da2-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="75da2-133">V tomto příkladu je vyvolána výjimka po rezervaci letu, ale před krokem schválení vedoucího.</span><span class="sxs-lookup"><span data-stu-id="75da2-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="75da2-134">Tento příklad je pracovní postup v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="75da2-134">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="75da2-135">Při vyvolání pracovního postupu je výjimka simulované chybové podmínky zpracována hostitelskou aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, pracovní postup je zrušen a je vyvolána logika kompenzace.</span><span class="sxs-lookup"><span data-stu-id="75da2-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="75da2-136">**ReserveFlight: Lístek je rezervovaný.**</span><span class="sxs-lookup"><span data-stu-id="75da2-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="75da2-137">**SimulatedErrorCondition: Došlo k vyvolání ApplicationException.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="75da2-138">**Neošetřená výjimka pracovního postupu:**  </span><span class="sxs-lookup"><span data-stu-id="75da2-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="75da2-139">**System. ApplicationException: Simulovaná chybová podmínka v pracovním postupu.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="75da2-140">**CancelFlight: Lístek je zrušený.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="75da2-141">**Pracovní postup byl úspěšně dokončen se stavem: Zrušil.**</span><span class="sxs-lookup"><span data-stu-id="75da2-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="75da2-142">Zrušení a aktivita CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="75da2-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="75da2-143">Pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> nástroji nejsou dokončeny a aktivita je zrušena <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , aktivity v nástroji se spustí.</span><span class="sxs-lookup"><span data-stu-id="75da2-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75da2-144">Je vyvolána pouze v případě, že aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> nejsou dokončeny a aktivita je zrušena. <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A></span><span class="sxs-lookup"><span data-stu-id="75da2-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="75da2-145">Je proveden pouze v případě, že aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> v <xref:System.Activities.Statements.CompensableActivity> nástroji byly úspěšně dokončeny a náhrada je následně vyvolána u aktivity. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A></span><span class="sxs-lookup"><span data-stu-id="75da2-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="75da2-146"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Dává autorům pracovního postupu možnost poskytnout jakoukoli vhodnou logiku zrušení.</span><span class="sxs-lookup"><span data-stu-id="75da2-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="75da2-147">V následujícím příkladu je vyvolána výjimka během provádění <xref:System.Activities.Statements.CompensableActivity.Body%2A>a <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> poté je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="75da2-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="75da2-148">Tento příklad je pracovní postup v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="75da2-148">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="75da2-149">Při vyvolání pracovního postupu je vyvolána výjimka simulované chybové podmínky v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>nástroji, pracovní postup je zrušen a logika <xref:System.Activities.Statements.CompensableActivity> zrušení je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="75da2-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="75da2-150">V tomto příkladu má logika kompenzace a logika zrušení různé cíle.</span><span class="sxs-lookup"><span data-stu-id="75da2-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="75da2-151">Pokud se <xref:System.Activities.Statements.CompensableActivity.Body%2A> úspěšně dokončilo, znamená to, že se dal kreditní karta účtovat a zaúčtuje se let, takže by se měla kompenzace vrátit zpátky oběma kroky.</span><span class="sxs-lookup"><span data-stu-id="75da2-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="75da2-152">(V tomto příkladu zrušení letu automaticky zruší poplatky za platební kartu.) Pokud <xref:System.Activities.Statements.CompensableActivity> je však zrušeno, znamená to, že se <xref:System.Activities.Statements.CompensableActivity.Body%2A> nedokončila, a <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> proto by logika potřeb měla být schopná určit, jak se má toto zrušení vymezit.</span><span class="sxs-lookup"><span data-stu-id="75da2-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="75da2-153">V tomto příkladu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zruší poplatek za platební kartu, ale vzhledem `ReserveFlight` <xref:System.Activities.Statements.CompensableActivity.Body%2A>k tomu, že se jednalo o poslední aktivitu v, se nepokusí o zrušení letu.</span><span class="sxs-lookup"><span data-stu-id="75da2-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="75da2-154">Vzhledem `ReserveFlight` k tomu <xref:System.Activities.Statements.CompensableActivity.Body%2A>, že se jednalo o poslední aktivitu v, pokud byla <xref:System.Activities.Statements.CompensableActivity.Body%2A> úspěšně dokončena, byl pravděpodobně dokončen a žádné zrušení by nebylo možné.</span><span class="sxs-lookup"><span data-stu-id="75da2-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="75da2-155">**ChargeCreditCard: Platební karta se účtuje pro let.**</span><span class="sxs-lookup"><span data-stu-id="75da2-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="75da2-156">**SimulatedErrorCondition: Došlo k vyvolání ApplicationException.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="75da2-157">**Neošetřená výjimka pracovního postupu:**  </span><span class="sxs-lookup"><span data-stu-id="75da2-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="75da2-158">**System. ApplicationException: Simulovaná chybová podmínka v pracovním postupu.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="75da2-159">**CancelCreditCard: Zruší poplatky za platební kartu.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="75da2-160">**Pracovní postup byl úspěšně dokončen se stavem: Zrušil.**</span><span class="sxs-lookup"><span data-stu-id="75da2-160">**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="75da2-161">Další informace o zrušení naleznete v tématu [zrušení](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="75da2-161">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="75da2-162">Explicitní kompenzace pomocí aktivity kompenzace</span><span class="sxs-lookup"><span data-stu-id="75da2-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="75da2-163">V předchozí části se pokryla implicitní kompenzace.</span><span class="sxs-lookup"><span data-stu-id="75da2-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="75da2-164">Implicitní kompenzace může být vhodná pro jednoduché scénáře, ale pokud je při plánování zpracování <xref:System.Activities.Statements.Compensate> kompenzace vyžadovánější ovládací prvek, lze aktivitu použít.</span><span class="sxs-lookup"><span data-stu-id="75da2-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="75da2-165">Chcete-li zahájit proces kompenzace <xref:System.Activities.Statements.Compensate> s aktivitou <xref:System.Activities.Statements.CompensationToken> , <xref:System.Activities.Statements.CompensableActivity> použije se, pro který se náhrada požaduje.</span><span class="sxs-lookup"><span data-stu-id="75da2-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="75da2-166">Aktivitu lze použít k inicializaci kompenzace u všech dokončených <xref:System.Activities.Statements.CompensableActivity> , které nebyly potvrzeny nebo vyrovnány. <xref:System.Activities.Statements.Compensate></span><span class="sxs-lookup"><span data-stu-id="75da2-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="75da2-167"><xref:System.Activities.Statements.Compensate> Aktivitu lze například použít <xref:System.Activities.Statements.TryCatch.Catches%2A> v části <xref:System.Activities.Statements.TryCatch> aktivity nebo kdykoli po jejím <xref:System.Activities.Statements.CompensableActivity> dokončení.</span><span class="sxs-lookup"><span data-stu-id="75da2-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="75da2-168">V tomto příkladu <xref:System.Activities.Statements.Compensate> se aktivita používá <xref:System.Activities.Statements.TryCatch.Catches%2A> v části <xref:System.Activities.Statements.TryCatch> aktivity k vrácení akce <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="75da2-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="75da2-169">Tento příklad je pracovní postup v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="75da2-169">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="75da2-170">Po vyvolání pracovního postupu se do konzoly zobrazí následující výstup.</span><span class="sxs-lookup"><span data-stu-id="75da2-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="75da2-171">**ReserveFlight: Lístek je rezervovaný.**</span><span class="sxs-lookup"><span data-stu-id="75da2-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="75da2-172">**SimulatedErrorCondition: Došlo k vyvolání ApplicationException.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="75da2-173">**CancelFlight: Lístek je zrušený.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="75da2-174">**Pracovní postup byl úspěšně dokončen se stavem: Ukončit.**</span><span class="sxs-lookup"><span data-stu-id="75da2-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="75da2-175">Potvrzení kompenzace</span><span class="sxs-lookup"><span data-stu-id="75da2-175">Confirming Compensation</span></span>  
 <span data-ttu-id="75da2-176">Ve výchozím nastavení je možné aktivity kompenzovatelná kompenzovat kdykoli po jejich dokončení.</span><span class="sxs-lookup"><span data-stu-id="75da2-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="75da2-177">V některých případech to nemusí být vhodné.</span><span class="sxs-lookup"><span data-stu-id="75da2-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="75da2-178">V předchozím příkladu se kompenzace pro rezervaci lístku zrušila.</span><span class="sxs-lookup"><span data-stu-id="75da2-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="75da2-179">Po dokončení tohoto letu ale tento krok kompenzace už není platný.</span><span class="sxs-lookup"><span data-stu-id="75da2-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="75da2-180">Potvrzení aktivity kompenzovatelná vyvolá aktivitu určenou v <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="75da2-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="75da2-181">Jedním z možných použití je umožnit vydání všech prostředků, které jsou nezbytné k vykonání náhrady.</span><span class="sxs-lookup"><span data-stu-id="75da2-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="75da2-182">Po potvrzení aktivity kompenzovatelná není možné ji kompenzovat a v případě, že se pokusíte o <xref:System.InvalidOperationException> výjimku, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="75da2-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="75da2-183">Po úspěšném dokončení pracovního postupu se všechny nepotvrzené a neuhrazené aktivity kompenzovatelná, které byly úspěšně dokončeny, potvrzují v opačném pořadí dokončení.</span><span class="sxs-lookup"><span data-stu-id="75da2-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="75da2-184">V tomto příkladu je let rezervovaný, zakoupený a dokončený a pak se potvrdí aktivita kompenzovatelná.</span><span class="sxs-lookup"><span data-stu-id="75da2-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="75da2-185">Pro potvrzení <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensationToken> použijte aktivitu a zadejte hodnotu propotvrzení.<xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.Confirm></span><span class="sxs-lookup"><span data-stu-id="75da2-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="75da2-186">Tento příklad je pracovní postup v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="75da2-186">This example is the workflow in XAML.</span></span>  
  
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
  
<span data-ttu-id="75da2-187">Po vyvolání pracovního postupu se do konzoly zobrazí následující výstup.</span><span class="sxs-lookup"><span data-stu-id="75da2-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="75da2-188">**ReserveFlight: Lístek je rezervovaný.**</span><span class="sxs-lookup"><span data-stu-id="75da2-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="75da2-189">**ManagerApproval: Bylo přijato schválení správcem.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="75da2-190">**PurchaseFlight: Lístek je koupený.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="75da2-191">**TakeFlight: Let je dokončený.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="75da2-192">**ConfirmFlight: Povedlo se ke letu, není možná žádná náhrada.**  </span><span class="sxs-lookup"><span data-stu-id="75da2-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="75da2-193">**Pracovní postup byl úspěšně dokončen se stavem: Ukončit.**</span><span class="sxs-lookup"><span data-stu-id="75da2-193">**Workflow completed successfully with status: Closed.**</span></span>   

## <a name="nesting-compensation-activities"></a><span data-ttu-id="75da2-194">Vnořování aktivit kompenzace</span><span class="sxs-lookup"><span data-stu-id="75da2-194">Nesting Compensation Activities</span></span>  

<span data-ttu-id="75da2-195">Může být umístěn <xref:System.Activities.Statements.CompensableActivity.Body%2A> do části jiného <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity></span><span class="sxs-lookup"><span data-stu-id="75da2-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="75da2-196">Nesmí být umístěn do obslužné rutiny jiného <xref:System.Activities.Statements.CompensableActivity>typu. <xref:System.Activities.Statements.CompensableActivity></span><span class="sxs-lookup"><span data-stu-id="75da2-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="75da2-197">Je zodpovědností nadřazené položky <xref:System.Activities.Statements.CompensableActivity> , aby se zajistilo, že když se zruší, potvrdí nebo kompenzuje všechny podřízené aktivity kompenzovatelná, které byly úspěšně dokončeny a ještě nebyly potvrzeny nebo vyrovnány, musí být potvrzeny nebo náhrada před dokončením zrušení, potvrzení nebo kompenzace nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="75da2-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="75da2-198">Pokud se nejedná o explicitní modelování, nadřazený <xref:System.Activities.Statements.CompensableActivity> objekt implicitně kompenzuje podřízené aktivity kompenzovatelná, pokud nadřazený objekt obdržel signál pro zrušení nebo kompenzaci.</span><span class="sxs-lookup"><span data-stu-id="75da2-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="75da2-199">Pokud nadřazená položka obdržela potvrzující signál, Nadřazená aktivita bude implicitně potvrzovat podřízené aktivity kompenzovatelná.</span><span class="sxs-lookup"><span data-stu-id="75da2-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="75da2-200">Pokud je logika zpracování zrušení, potvrzení nebo kompenzace explicitně modelována v obslužné rutině nadřazené položky <xref:System.Activities.Statements.CompensableActivity>, všechny podřízené objekty, které explicitně nezpracovává, budou implicitně potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="75da2-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75da2-201">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75da2-201">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
