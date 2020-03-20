---
title: Vlastní sledování
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 2b100b877bbc8c6d830f09a4a59decffde511511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182844"
---
# <a name="custom-tracking"></a><span data-ttu-id="0ec8d-102">Vlastní sledování</span><span class="sxs-lookup"><span data-stu-id="0ec8d-102">Custom Tracking</span></span>
<span data-ttu-id="0ec8d-103">Tato ukázka ukazuje, jak vytvořit vlastní účastníksledování a zapsat obsah dat sledování do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="0ec8d-104">Kromě toho ukázka ukazuje, jak <xref:System.Activities.Tracking.CustomTrackingRecord> vyzařovat objekty naplněné uživatelem definovaná data.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="0ec8d-105">Účastník sledování na základě <xref:System.Activities.Tracking.TrackingRecord> konzoly filtruje objekty vyzařované pracovním postupem pomocí objektu profilu sledování vytvořeného v kódu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="0ec8d-106">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="0ec8d-106">Sample Details</span></span>
 <span data-ttu-id="0ec8d-107">Windows Workflow Foundation (WF) poskytuje infrastrukturu sledování ke sledování provádění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="0ec8d-108">Doba sledování runtime implementuje instanci pracovního postupu k vyzařování událostí souvisejících s životním cyklem pracovního postupu, událostmi z aktivit pracovního postupu a vlastními událostmi sledování.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="0ec8d-109">V následující tabulce jsou uvedeny hlavní součásti infrastruktury sledování.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="0ec8d-110">Komponenta</span><span class="sxs-lookup"><span data-stu-id="0ec8d-110">Component</span></span>|<span data-ttu-id="0ec8d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="0ec8d-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="0ec8d-112">Sledování běhu</span><span class="sxs-lookup"><span data-stu-id="0ec8d-112">Tracking runtime</span></span>|<span data-ttu-id="0ec8d-113">Poskytuje infrastrukturu pro vyzařování záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="0ec8d-114">Sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="0ec8d-114">Tracking participants</span></span>|<span data-ttu-id="0ec8d-115">Spotřebovává záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-115">Consumes the tracking records.</span></span> <span data-ttu-id="0ec8d-116">Rozhraní .NET Framework 4 je dodáván s účastníkem sledování, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="0ec8d-116">.NET Framework 4 ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="0ec8d-117">Profil sledování</span><span class="sxs-lookup"><span data-stu-id="0ec8d-117">Tracking profile</span></span>|<span data-ttu-id="0ec8d-118">Mechanismus filtrování, který umožňuje účastníkovi sledování přihlásit se k odběru podmnožiny záznamů sledování vyzařovaných z instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="0ec8d-119">V následující tabulce jsou podrobně uvedeny záznamy sledování, které vydává za běhu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="0ec8d-120">Záznam sledování</span><span class="sxs-lookup"><span data-stu-id="0ec8d-120">Tracking Record</span></span>|<span data-ttu-id="0ec8d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="0ec8d-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="0ec8d-122">Záznamy sledování instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="0ec8d-123">Popisuje životní cyklus instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="0ec8d-124">Například záznam instance je emitován při spuštění nebo dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="0ec8d-125">Záznamy sledování stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="0ec8d-126">Podrobnosti provádění aktivity.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-126">Details activity execution.</span></span> <span data-ttu-id="0ec8d-127">Tyto záznamy označují stav aktivity pracovního postupu, například když je aktivita naplánována nebo když je aktivita dokončena nebo když je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="0ec8d-128">Záznam obnovení záložky.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-128">Bookmark resumption record.</span></span>|<span data-ttu-id="0ec8d-129">Vydává se vždy, když je záložka v instanci pracovního postupu obnovena.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="0ec8d-130">Vlastní záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-130">Custom Tracking Records.</span></span>|<span data-ttu-id="0ec8d-131">Autor pracovního postupu může vytvořit vlastní záznamy sledování a vypouštět je v rámci vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="0ec8d-132">Účastník sledování se přihlásí k odběru podmnožiny emitovaných <xref:System.Activities.Tracking.TrackingRecord> objektů pomocí profilů sledování.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="0ec8d-133">Profil sledování obsahuje sledování dotazů, které umožňují přihlášení k odběru pro konkrétní typ záznamu sledování.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="0ec8d-134">Profily sledování lze zadat v kódu nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="0ec8d-135">Vlastní účastník sledování</span><span class="sxs-lookup"><span data-stu-id="0ec8d-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="0ec8d-136">Rozhraní API účastníka sledování umožňuje rozšíření sledování runtime s uživatelem za <xref:System.Activities.Tracking.TrackingRecord> předpokladu, sledování účastníka, který může zahrnovat vlastní logiku pro zpracování objektů vyzařovaných runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="0ec8d-137">Chcete-li napsat účastníka <xref:System.Activities.Tracking.TrackingParticipant>sledování, musí uživatel implementovat .</span><span class="sxs-lookup"><span data-stu-id="0ec8d-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="0ec8d-138">Konkrétně <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda musí být implementována vlastní účastník.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="0ec8d-139">Tato metoda je <xref:System.Activities.Tracking.TrackingRecord> volána při a je emitován runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="0ec8d-140">Kompletní sledování účastníkje implementována v souboru ConsoleTrackingParticipant.cs.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.</span></span> <span data-ttu-id="0ec8d-141">Následující příklad kódu <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> je metoda pro vlastní účastníka sledování.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-141">The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

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

 <span data-ttu-id="0ec8d-142">Následující příklad kódu přidá účastníka konzoly do vyvolávače pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-142">The following code example adds the console participant to the workflow invoker.</span></span>

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

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="0ec8d-143">Vyzařování vlastních záznamů sledování</span><span class="sxs-lookup"><span data-stu-id="0ec8d-143">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="0ec8d-144">Tato ukázka také ukazuje schopnost <xref:System.Activities.Tracking.CustomTrackingRecord> vyzařovat objekty z vlastní aktivity pracovního postupu:</span><span class="sxs-lookup"><span data-stu-id="0ec8d-144">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

- <span data-ttu-id="0ec8d-145">Objekty <xref:System.Activities.Tracking.CustomTrackingRecord> jsou vytvořeny a naplněny uživatelem definovaná data, která je žádoucí, aby byly vydány se záznamem.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

- <span data-ttu-id="0ec8d-146">Je <xref:System.Activities.Tracking.CustomTrackingRecord> vydáván voláním track metoda <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-146">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="0ec8d-147">Následující příklad ukazuje, jak <xref:System.Activities.Tracking.CustomTrackingRecord> vyzařovat objekty v rámci vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-147">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="0ec8d-148">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="0ec8d-148">To use this sample</span></span>

1. <span data-ttu-id="0ec8d-149">Pomocí visual studia 2010 otevřete soubor řešení CustomTrackingSample.sln.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-149">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="0ec8d-150">Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="0ec8d-151">Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-151">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ec8d-152">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0ec8d-153">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0ec8d-154">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0ec8d-155">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0ec8d-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="0ec8d-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ec8d-156">See also</span></span>

- <span data-ttu-id="0ec8d-157">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0ec8d-157">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
