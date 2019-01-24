---
title: Kompenzace
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: e8a7140e677b553d07014d0ac5a77dd1c7488f53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607602"
---
# <a name="compensation"></a><span data-ttu-id="72420-102">Kompenzace</span><span class="sxs-lookup"><span data-stu-id="72420-102">Compensation</span></span>
<span data-ttu-id="72420-103">Kompenzace ve Windows Workflow Foundation (WF) je mechanismus, pomocí kterého dříve Dokončená práce vrátit zpět nebo kompenzována (následující logiky definované aplikací.) dojde k následující chybě.</span><span class="sxs-lookup"><span data-stu-id="72420-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="72420-104">Tato část popisuje, jak použít náhradu v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="72420-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="72420-105">Kompenzace vs. Transakce</span><span class="sxs-lookup"><span data-stu-id="72420-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="72420-106">Transakce můžete zkombinovat několik operací do jedné jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="72420-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="72420-107">Vaše aplikace pomocí transakce dává možnost zrušit všechny změny, které se spustí z v rámci transakce, pokud dojde k nějaké chybě během jakékoli části procesu transakce (vrácení zpět).</span><span class="sxs-lookup"><span data-stu-id="72420-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="72420-108">Použití transakcí však nemusí být vhodné v případě, že je spuštěna po dlouhou dobu práce.</span><span class="sxs-lookup"><span data-stu-id="72420-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="72420-109">Například plánování cestovní aplikace je implementovaný jako pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="72420-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="72420-110">Rezervace letenky, čeká na schválení správce a pak platíte za letu může obsahovat kroky pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="72420-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="72420-111">Tento proces může trvat dlouho a není praktické kroky rezervace a platit za pochodu k účasti v rámci jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="72420-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="72420-112">Ve scénáři takovou situaci kompenzace může vrátit zpět rezervaci kroku pracovního postupu, pokud dojde k selhání později při zpracování.</span><span class="sxs-lookup"><span data-stu-id="72420-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72420-113">Toto téma popisuje kompenzace v pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="72420-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="72420-114">Další informace o transakcích v pracovních postupech najdete v tématu [transakce](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) a <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="72420-114">For more information about transactions in workflows, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="72420-115">Další informace o transakcích najdete v tématu <xref:System.Transactions?displayProperty=nameWithType> a <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72420-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="72420-116">Aktivita CompensableActivity pomocí</span><span class="sxs-lookup"><span data-stu-id="72420-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="72420-117"><xref:System.Activities.Statements.CompensableActivity> aktivitu kompenzace jader v [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="72420-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="72420-118">Všechny aktivity, které vykonávají práci, která možná bude nutné kompenzována se umístí do <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="72420-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="72420-119">V tomto příkladu je krok rezervace letenky nákupu umístí do <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> a zrušení rezervace se umístí do <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="72420-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="72420-120">Přímo za <xref:System.Activities.Statements.CompensableActivity> v pracovním postupu jsou dvě aktivity, které čekání na schválení správce a pak dokončete nákupní krok letu.</span><span class="sxs-lookup"><span data-stu-id="72420-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="72420-121">Pokud chybová podmínka způsobí, že pracovní postup zruší po <xref:System.Activities.Statements.CompensableActivity> bylo úspěšně dokončeno, pak aktivity v <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obslužné rutiny jsou naplánovány a letu se zruší.</span><span class="sxs-lookup"><span data-stu-id="72420-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="72420-122">V následujícím příkladu je pracovní postup v XAML.</span><span class="sxs-lookup"><span data-stu-id="72420-122">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="72420-123">Když uživatel vyvolá pracovní postup, se zobrazí následující výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="72420-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="72420-124">**ReserveFlight: Lístku je vyhrazená.**</span><span class="sxs-lookup"><span data-stu-id="72420-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="72420-125">**ManagerApproval: Přijetí schválení správcem.** </span><span class="sxs-lookup"><span data-stu-id="72420-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="72420-126">**PurchaseFlight: Jste si koupili lístku.** </span><span class="sxs-lookup"><span data-stu-id="72420-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="72420-127">**Byla úspěšně dokončena se stavem pracovního postupu: Uzavřený.**</span><span class="sxs-lookup"><span data-stu-id="72420-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="72420-128">Ukázkové aktivity v tomto tématu, jako `ReserveFlight` konzolu tak, aby usnadnily pořadí, ve kterém jsou spouštěny aktivity, když dojde k vyrovnání zobrazí jejich název a účel.</span><span class="sxs-lookup"><span data-stu-id="72420-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="72420-129">Výchozí kompenzace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="72420-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="72420-130">Ve výchozím nastavení Pokud dojde ke zrušení pracovního postupu, kompenzační logiky se spouští pro jakékoli kompenzovatelná aktivita, která má úspěšně úplně a ještě není potvrzena nebo kompenzována.</span><span class="sxs-lookup"><span data-stu-id="72420-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72420-131">Když <xref:System.Activities.Statements.CompensableActivity> je *potvrzen*, už může být vyvolána kompenzace aktivity.</span><span class="sxs-lookup"><span data-stu-id="72420-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="72420-132">Procesu potvrzení najdete dál v této části.</span><span class="sxs-lookup"><span data-stu-id="72420-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="72420-133">V tomto příkladu je vyvolána výjimka po vyhrazené letu, ale před krokem schválení správce.</span><span class="sxs-lookup"><span data-stu-id="72420-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="72420-134">V tomto příkladu je pracovní postup v XAML.</span><span class="sxs-lookup"><span data-stu-id="72420-134">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="72420-135">Když uživatel vyvolá pracovní postup, je simulované chybě podmínku výjimka ošetřena hostitele aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, pracovní postup zrušení a je vyvolána kompenzační logiky.</span><span class="sxs-lookup"><span data-stu-id="72420-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="72420-136">**ReserveFlight: Lístku je vyhrazená.**</span><span class="sxs-lookup"><span data-stu-id="72420-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="72420-137">**SimulatedErrorCondition: Došlo ApplicationException.** </span><span class="sxs-lookup"><span data-stu-id="72420-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="72420-138">**Pracovní postup neošetřená výjimka:** </span><span class="sxs-lookup"><span data-stu-id="72420-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="72420-139">**System.ApplicationException: Simulované chybě v pracovním postupu.** </span><span class="sxs-lookup"><span data-stu-id="72420-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="72420-140">**CancelFlight: Lístek se zrušila.** </span><span class="sxs-lookup"><span data-stu-id="72420-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="72420-141">**Byla úspěšně dokončena se stavem pracovního postupu: Bylo zrušeno.**</span><span class="sxs-lookup"><span data-stu-id="72420-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="72420-142">Zrušení a aktivita CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="72420-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="72420-143">Pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> mají nedokončený a aktivity se zruší, aktivity v <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> provádějí.</span><span class="sxs-lookup"><span data-stu-id="72420-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72420-144"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Je vyvolána pouze v případě aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> nedokončili a aktivity se zruší.</span><span class="sxs-lookup"><span data-stu-id="72420-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="72420-145"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Se provede pouze, pokud aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> úspěšně dokončit a kompenzace je následně volána v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="72420-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="72420-146"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Dává příležitost k poskytování logiky pro všechny příslušné zrušení autoři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="72420-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="72420-147">V následujícím příkladu, dojde k výjimce během zpracování <xref:System.Activities.Statements.CompensableActivity.Body%2A>a pak <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="72420-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="72420-148">V tomto příkladu je pracovní postup v XAML</span><span class="sxs-lookup"><span data-stu-id="72420-148">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="72420-149">Když uživatel vyvolá pracovní postup, je simulované chybě podmínku výjimka ošetřena hostitele aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, dojde ke zrušení pracovního postupu a logiku zrušení <xref:System.Activities.Statements.CompensableActivity> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="72420-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="72420-150">V tomto příkladu kompenzační logika a logika zrušení mají různé cíle.</span><span class="sxs-lookup"><span data-stu-id="72420-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="72420-151">Pokud <xref:System.Activities.Statements.CompensableActivity.Body%2A> se nedokončil úspěšně, pak to znamená platební karty se naúčtovala platba a si letu, takže vyrovnání by měl vrátit zpět oba kroky.</span><span class="sxs-lookup"><span data-stu-id="72420-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="72420-152">(V tomto příkladu ruší letu se automaticky zruší poplatky platební karty.) Ale pokud <xref:System.Activities.Statements.CompensableActivity> dojde ke zrušení, to znamená, že <xref:System.Activities.Statements.CompensableActivity.Body%2A> nebyla úplný a tak logiku <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> musí být schopní určit, jak nejlépe zpracovat zrušení.</span><span class="sxs-lookup"><span data-stu-id="72420-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="72420-153">V tomto příkladu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zruší platební kartu poplatek, ale od té doby `ReserveFlight` byl poslední aktivita v <xref:System.Activities.Statements.CompensableActivity.Body%2A>, se nebude pokoušet o zrušení letu.</span><span class="sxs-lookup"><span data-stu-id="72420-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="72420-154">Protože `ReserveFlight` byl poslední aktivita v <xref:System.Activities.Statements.CompensableActivity.Body%2A>, pokud bylo úspěšně dokončeno pak bude <xref:System.Activities.Statements.CompensableActivity.Body%2A> byste dokončili a bez zrušení by bylo možné.</span><span class="sxs-lookup"><span data-stu-id="72420-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="72420-155">**ChargeCreditCard: Platby prostřednictvím platební karty pro let.**</span><span class="sxs-lookup"><span data-stu-id="72420-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="72420-156">**SimulatedErrorCondition: Došlo ApplicationException.** </span><span class="sxs-lookup"><span data-stu-id="72420-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="72420-157">**Pracovní postup neošetřená výjimka:** </span><span class="sxs-lookup"><span data-stu-id="72420-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="72420-158">**System.ApplicationException: Simulované chybě v pracovním postupu.** </span><span class="sxs-lookup"><span data-stu-id="72420-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="72420-159">**CancelCreditCard: Zrušte poplatky.** </span><span class="sxs-lookup"><span data-stu-id="72420-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="72420-160">**Byla úspěšně dokončena se stavem pracovního postupu: Bylo zrušeno.**</span><span class="sxs-lookup"><span data-stu-id="72420-160">**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="72420-161">Další informace o zrušení naleznete v tématu [zrušení](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="72420-161">For more information about cancellation, see [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="72420-162">Pomocí explicitní kompenzaci aktivitu kompenzace</span><span class="sxs-lookup"><span data-stu-id="72420-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="72420-163">V předchozí části zkušebním implicitní kompenzaci.</span><span class="sxs-lookup"><span data-stu-id="72420-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="72420-164">Implicitní kompenzace může být vhodné pro jednoduché scénáře, ale pokud podrobnější je vyžadováno řízení nad plánováním kompenzace pak zpracování <xref:System.Activities.Statements.Compensate> aktivita se dá použít.</span><span class="sxs-lookup"><span data-stu-id="72420-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="72420-165">K zahájení kompenzace s <xref:System.Activities.Statements.Compensate> aktivity, <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> pro které kompenzace je žádoucí se používá.</span><span class="sxs-lookup"><span data-stu-id="72420-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="72420-166"><xref:System.Activities.Statements.Compensate> Aktivita slouží k zahájení kompenzaci na žádném dokončení <xref:System.Activities.Statements.CompensableActivity> , která nebyla potvrzena nebo kompenzována.</span><span class="sxs-lookup"><span data-stu-id="72420-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="72420-167">Například <xref:System.Activities.Statements.Compensate> aktivity se daly použít v <xref:System.Activities.Statements.TryCatch.Catches%2A> část <xref:System.Activities.Statements.TryCatch> aktivity nebo kdykoli po dokončení <xref:System.Activities.Statements.CompensableActivity> byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="72420-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="72420-168">V tomto příkladu <xref:System.Activities.Statements.Compensate> aktivita se používá v <xref:System.Activities.Statements.TryCatch.Catches%2A> část <xref:System.Activities.Statements.TryCatch> aktivitu pro vrácení akce <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="72420-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="72420-169">V tomto příkladu je pracovní postup v XAML.</span><span class="sxs-lookup"><span data-stu-id="72420-169">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="72420-170">Když uživatel vyvolá pracovní postup, se zobrazí následující výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="72420-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="72420-171">**ReserveFlight: Lístku je vyhrazená.**</span><span class="sxs-lookup"><span data-stu-id="72420-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="72420-172">**SimulatedErrorCondition: Došlo ApplicationException.** </span><span class="sxs-lookup"><span data-stu-id="72420-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="72420-173">**CancelFlight: Lístek se zrušila.** </span><span class="sxs-lookup"><span data-stu-id="72420-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="72420-174">**Byla úspěšně dokončena se stavem pracovního postupu: Uzavřený.**</span><span class="sxs-lookup"><span data-stu-id="72420-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="72420-175">Potvrzují se kompenzace</span><span class="sxs-lookup"><span data-stu-id="72420-175">Confirming Compensation</span></span>  
 <span data-ttu-id="72420-176">Ve výchozím nastavení kompenzovatelné aktivity kompenzovat lze kdykoli po jejich dokončení.</span><span class="sxs-lookup"><span data-stu-id="72420-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="72420-177">V některých případech to nemusí být vhodné.</span><span class="sxs-lookup"><span data-stu-id="72420-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="72420-178">V předchozím příkladu byl kompenzace k rezervaci-the-ticket ke zrušení rezervace.</span><span class="sxs-lookup"><span data-stu-id="72420-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="72420-179">Po dokončení letu tento krok kompenzace je však již platná.</span><span class="sxs-lookup"><span data-stu-id="72420-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="72420-180">Potvrzení kompenzovatelné aktivity volá aktivita určené <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="72420-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="72420-181">Jeden využití pro tuto je umožnit všechny prostředky, které jsou nezbytné k provedení náhrady uvolnit.</span><span class="sxs-lookup"><span data-stu-id="72420-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="72420-182">Jakmile se potvrdí kompenzovatelné aktivity není možné, aby se kompenzována a tím dojde k pokusu o <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="72420-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="72420-183">Po úspěšném dokončení pracovního postupu, jsou všechny nepotvrzené a kompenzována kompenzovatelné aktivity, které byla úspěšně dokončena v obráceném pořadí potvrdit dokončení.</span><span class="sxs-lookup"><span data-stu-id="72420-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="72420-184">V tomto příkladu je letu vyhrazené, koupit a dokončit, a pak je potvrzen kompenzovatelné aktivity.</span><span class="sxs-lookup"><span data-stu-id="72420-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="72420-185">Potvrďte <xref:System.Activities.Statements.CompensableActivity>, použijte <xref:System.Activities.Statements.Confirm> aktivity a zadejte <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> potvrďte.</span><span class="sxs-lookup"><span data-stu-id="72420-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="72420-186">V tomto příkladu je pracovní postup v XAML.</span><span class="sxs-lookup"><span data-stu-id="72420-186">This example is the workflow in XAML.</span></span>  
  
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
  
<span data-ttu-id="72420-187">Když uživatel vyvolá pracovní postup, se zobrazí následující výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="72420-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="72420-188">**ReserveFlight: Lístku je vyhrazená.**</span><span class="sxs-lookup"><span data-stu-id="72420-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="72420-189">**ManagerApproval: Přijetí schválení správcem.** </span><span class="sxs-lookup"><span data-stu-id="72420-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="72420-190">**PurchaseFlight: Jste si koupili lístku.** </span><span class="sxs-lookup"><span data-stu-id="72420-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="72420-191">**TakeFlight: Flight je dokončen.** </span><span class="sxs-lookup"><span data-stu-id="72420-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="72420-192">**ConfirmFlight: Letu se nestalo, žádné honoráře je to možné.** </span><span class="sxs-lookup"><span data-stu-id="72420-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="72420-193">**Byla úspěšně dokončena se stavem pracovního postupu: Uzavřený.**</span><span class="sxs-lookup"><span data-stu-id="72420-193">**Workflow completed successfully with status: Closed.**</span></span>   

## <a name="nesting-compensation-activities"></a><span data-ttu-id="72420-194">Vnoření kompenzace aktivity</span><span class="sxs-lookup"><span data-stu-id="72420-194">Nesting Compensation Activities</span></span>  

<span data-ttu-id="72420-195">A <xref:System.Activities.Statements.CompensableActivity> , jde umístit do <xref:System.Activities.Statements.CompensableActivity.Body%2A> části jiného <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="72420-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="72420-196">A <xref:System.Activities.Statements.CompensableActivity> nelze umístit do rutiny jiného <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="72420-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="72420-197">Zodpovídá za nadřazeného <xref:System.Activities.Statements.CompensableActivity> zajistit, že pokud je zrušen, potvrzena nebo kompenzována, všechny podřízené kompenzovatelné aktivity, které byly úspěšně dokončeny a ještě není byla potvrzena nebo kompenzována musí být potvrzeny nebo kompenzována předtím, než nadřazená dokončení zrušení, confirmation nebo kompenzaci.</span><span class="sxs-lookup"><span data-stu-id="72420-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="72420-198">Pokud to není explicitně modelovat nadřazené <xref:System.Activities.Statements.CompensableActivity> bude implicitně kompenzace podřízené kompenzovatelné aktivity, pokud nadřazená dostali zrušení nebo kompenzaci signálu.</span><span class="sxs-lookup"><span data-stu-id="72420-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="72420-199">Pokud nadřazená přijal signál potvrzení nadřazené potvrdí implicitně podřízené kompenzovatelné aktivity.</span><span class="sxs-lookup"><span data-stu-id="72420-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="72420-200">Pokud logiku ke zpracování zrušení, confirmation nebo kompenzace je explicitně modelován v obslužné rutině nadřazené <xref:System.Activities.Statements.CompensableActivity>, všech podřízených nejsou explicitně zpracována bude implicitně potvrzen.</span><span class="sxs-lookup"><span data-stu-id="72420-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72420-201">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72420-201">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
