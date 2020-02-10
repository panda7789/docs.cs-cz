---
title: Vlastní sledování
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 9a2ad2004c47ce76dcc35baf4ca28aa174409581
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094654"
---
# <a name="custom-tracking"></a><span data-ttu-id="63c25-102">Vlastní sledování</span><span class="sxs-lookup"><span data-stu-id="63c25-102">Custom Tracking</span></span>
<span data-ttu-id="63c25-103">Tento příklad ukazuje, jak vytvořit vlastního účastníka sledování a zapsat obsah sledování dat do konzoly.</span><span class="sxs-lookup"><span data-stu-id="63c25-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="63c25-104">Kromě toho Ukázka ukazuje, jak vygenerovat <xref:System.Activities.Tracking.CustomTrackingRecord> objekty naplněné uživatelsky definovanými daty.</span><span class="sxs-lookup"><span data-stu-id="63c25-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="63c25-105">Účastník sledování na základě konzoly filtruje objekty <xref:System.Activities.Tracking.TrackingRecord> generované pracovním postupem pomocí objektu sledování profilu vytvořeného v kódu.</span><span class="sxs-lookup"><span data-stu-id="63c25-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="63c25-106">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="63c25-106">Sample Details</span></span>
 <span data-ttu-id="63c25-107">Programovací model Windows Workflow Foundation (WF) poskytuje sledovací infrastrukturu pro sledování provádění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="63c25-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="63c25-108">Sledovací modul sledování implementuje instanci pracovního postupu k vygenerování událostí souvisejících s životním cyklem pracovního postupu, událostí z aktivit pracovního postupu a vlastními událostmi sledování.</span><span class="sxs-lookup"><span data-stu-id="63c25-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="63c25-109">Následující tabulka podrobně popisuje primární součásti infrastruktury sledování.</span><span class="sxs-lookup"><span data-stu-id="63c25-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="63c25-110">Komponenta</span><span class="sxs-lookup"><span data-stu-id="63c25-110">Component</span></span>|<span data-ttu-id="63c25-111">Popis</span><span class="sxs-lookup"><span data-stu-id="63c25-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="63c25-112">Sledování – modul runtime</span><span class="sxs-lookup"><span data-stu-id="63c25-112">Tracking runtime</span></span>|<span data-ttu-id="63c25-113">Poskytuje infrastrukturu pro vygenerování záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="63c25-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="63c25-114">Sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="63c25-114">Tracking participants</span></span>|<span data-ttu-id="63c25-115">Využívá záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="63c25-115">Consumes the tracking records.</span></span> <span data-ttu-id="63c25-116">.NET Framework 4 jsou dodávány s účastníkem sledování, který zapisuje záznamy sledování jako události ETW (Event Tracing for Windows).</span><span class="sxs-lookup"><span data-stu-id="63c25-116">.NET Framework 4 ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="63c25-117">Profil sledování</span><span class="sxs-lookup"><span data-stu-id="63c25-117">Tracking profile</span></span>|<span data-ttu-id="63c25-118">Mechanismus filtrování, který umožňuje sledování účastníka přihlásit k odběru podmnožiny sledovacích záznamů emitovaných z instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="63c25-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="63c25-119">Následující tabulka podrobně popisuje záznamy sledování, které modul runtime pracovního postupu generuje.</span><span class="sxs-lookup"><span data-stu-id="63c25-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="63c25-120">Záznam sledování</span><span class="sxs-lookup"><span data-stu-id="63c25-120">Tracking Record</span></span>|<span data-ttu-id="63c25-121">Popis</span><span class="sxs-lookup"><span data-stu-id="63c25-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="63c25-122">Záznamy sledování instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="63c25-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="63c25-123">Popisuje životní cyklus instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="63c25-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="63c25-124">Například záznam instance je generován při spuštění nebo dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="63c25-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="63c25-125">Záznamy sledování stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="63c25-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="63c25-126">Podrobnosti provádění aktivity.</span><span class="sxs-lookup"><span data-stu-id="63c25-126">Details activity execution.</span></span> <span data-ttu-id="63c25-127">Tyto záznamy označují stav aktivity pracovního postupu, například když je naplánována aktivita nebo když se aktivita dokončí nebo když je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="63c25-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="63c25-128">Záznam opětovného pokračování záložky</span><span class="sxs-lookup"><span data-stu-id="63c25-128">Bookmark resumption record.</span></span>|<span data-ttu-id="63c25-129">Vygenerováno pokaždé, když je obnovena záložka v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="63c25-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="63c25-130">Vlastní záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="63c25-130">Custom Tracking Records.</span></span>|<span data-ttu-id="63c25-131">Autor pracovního postupu může vytvořit vlastní záznamy sledování a vygenerovat je v rámci vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="63c25-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="63c25-132">Účastník sledování přihlašuje odběr podmnožiny vygenerovaných <xref:System.Activities.Tracking.TrackingRecord> objektů pomocí sledování profilů.</span><span class="sxs-lookup"><span data-stu-id="63c25-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="63c25-133">Profil sledování obsahuje sledovací dotazy, které umožňují přihlášení k odběru konkrétního typu záznamu sledování.</span><span class="sxs-lookup"><span data-stu-id="63c25-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="63c25-134">Sledování profilů lze zadat v kódu nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="63c25-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="63c25-135">Účastník vlastního sledování</span><span class="sxs-lookup"><span data-stu-id="63c25-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="63c25-136">Rozhraní API sledování účastníka umožňuje rozšíření sledovacího modulu Sledování s účastníkem sledování, které může zahrnovat vlastní logiku pro zpracování <xref:System.Activities.Tracking.TrackingRecord> objektů generovaných modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="63c25-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="63c25-137">K zápisu účastníka sledování musí uživatel implementovat <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="63c25-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="63c25-138">Konkrétně musí být metoda <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> implementovaná vlastním účastníkem.</span><span class="sxs-lookup"><span data-stu-id="63c25-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="63c25-139">Tato metoda je volána, když je <xref:System.Activities.Tracking.TrackingRecord> vyvolána modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="63c25-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="63c25-140">Dokončený účastník sledování je implementován v souboru ConsoleTrackingParticipant.cs.</span><span class="sxs-lookup"><span data-stu-id="63c25-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.</span></span> <span data-ttu-id="63c25-141">Následující příklad kódu je metoda <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> pro vlastního účastníka sledování.</span><span class="sxs-lookup"><span data-stu-id="63c25-141">The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

```csharp
protected override void Track(TrackingRecord record, TimeSpan timeout)
{
    ...
    WorkflowInstanceRecord workflowInstanceRecord = record as WorkflowInstanceRecord;
    if (workflowInstanceRecord != null)
    {
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " Workflow InstanceID: {0} Workflow instance state: {1}",
            record.InstanceId, workflowInstanceRecord.State));
    }

    ActivityStateRecord activityStateRecord = record as ActivityStateRecord;
    if (activityStateRecord != null)
    {
        IDictionary<String, object> variables = activityStateRecord.Variables;
        StringBuilder vars = new StringBuilder();

        if (variables.Count > 0)
        {
            vars.AppendLine("\n\tVariables:");
            foreach (KeyValuePair<string, object> variable in variables)
            {
                vars.AppendLine(String.Format(
                    "\t\tName: {0} Value: {1}", variable.Key, variable.Value));
            }
        }
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " :Activity DisplayName: {0} :ActivityInstanceState: {1} {2}",
                activityStateRecord.Activity.Name, activityStateRecord.State,
            ((variables.Count > 0) ? vars.ToString() : String.Empty)));
    }

    CustomTrackingRecord customTrackingRecord = record as CustomTrackingRecord;

    if ((customTrackingRecord != null) && (customTrackingRecord.Data.Count > 0))
    {
        ...
    }
    Console.WriteLine();

}
```

 <span data-ttu-id="63c25-142">Následující příklad kódu přidá účastníka konzoly do pracovního postupu původce.</span><span class="sxs-lookup"><span data-stu-id="63c25-142">The following code example adds the console participant to the workflow invoker.</span></span>

```csharp
ConsoleTrackingParticipant customTrackingParticipant = new ConsoleTrackingParticipant()
{
    ...
    // The tracking profile is set here, refer to Program.CS
...
}

WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
```

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="63c25-143">Emitování vlastních záznamů sledování</span><span class="sxs-lookup"><span data-stu-id="63c25-143">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="63c25-144">Tato ukázka také ukazuje možnost generovat <xref:System.Activities.Tracking.CustomTrackingRecord> objekty z vlastní aktivity pracovního postupu:</span><span class="sxs-lookup"><span data-stu-id="63c25-144">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

- <span data-ttu-id="63c25-145">Objekty <xref:System.Activities.Tracking.CustomTrackingRecord> jsou vytvořeny a naplněny uživatelsky definovanými daty, která mají být vygenerována záznamem.</span><span class="sxs-lookup"><span data-stu-id="63c25-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

- <span data-ttu-id="63c25-146"><xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerována voláním metody Track <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="63c25-146">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="63c25-147">Následující příklad ukazuje, jak vygenerovat <xref:System.Activities.Tracking.CustomTrackingRecord> objekty v rámci vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="63c25-147">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

```csharp
// Create the Custom Tracking Record
CustomTrackingRecord customRecord = new CustomTrackingRecord("OrderIn")
{
    Data =
    {
        {"OrderId", 200},
        {"OrderDate", "20 Aug 2001"}
    }
};

// Emit custom tracking record
context.Track(customRecord);
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="63c25-148">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="63c25-148">To use this sample</span></span>

1. <span data-ttu-id="63c25-149">Pomocí sady Visual Studio 2010 otevřete soubor řešení CustomTrackingSample. sln.</span><span class="sxs-lookup"><span data-stu-id="63c25-149">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="63c25-150">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="63c25-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="63c25-151">Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="63c25-151">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63c25-152">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="63c25-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="63c25-153">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="63c25-153">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="63c25-154">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="63c25-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="63c25-155">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="63c25-155">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="63c25-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="63c25-156">See also</span></span>

- <span data-ttu-id="63c25-157">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="63c25-157">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
