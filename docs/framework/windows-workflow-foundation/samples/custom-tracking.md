---
title: Vlastní sledování
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 7e275af046013dcd76cb61c25ace1d96fd7e4b93
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307610"
---
# <a name="custom-tracking"></a><span data-ttu-id="49698-102">Vlastní sledování</span><span class="sxs-lookup"><span data-stu-id="49698-102">Custom Tracking</span></span>
<span data-ttu-id="49698-103">Tento příklad znázorňuje způsob vytvoření vlastního účastníka sledování a zapisovat obsah data sledování do konzoly.</span><span class="sxs-lookup"><span data-stu-id="49698-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="49698-104">Kromě toho Ukázka předvádí, jak vygenerovat <xref:System.Activities.Tracking.CustomTrackingRecord> objekty vyplní s uživatelem definovaná data.</span><span class="sxs-lookup"><span data-stu-id="49698-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="49698-105">Filtry účastníka sledování pomocí konzoly <xref:System.Activities.Tracking.TrackingRecord> objekty, protože ho vygeneroval pracovního postupu pomocí profilu sledování objekt vytvořený v kódu.</span><span class="sxs-lookup"><span data-stu-id="49698-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="49698-106">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="49698-106">Sample Details</span></span>
 <span data-ttu-id="49698-107">Windows Workflow Foundation (WF) poskytuje sledování infrastruktury pro sledování spuštění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49698-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="49698-108">Modul runtime sledování implementuje instance pracovního postupu ke generování událostí souvisejících s životního cyklu pracovního postupu, události z aktivit pracovního postupu a vlastního sledování událostí.</span><span class="sxs-lookup"><span data-stu-id="49698-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="49698-109">Následující tabulka obsahuje podrobnosti o primární součásti sledování infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="49698-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="49698-110">Součást</span><span class="sxs-lookup"><span data-stu-id="49698-110">Component</span></span>|<span data-ttu-id="49698-111">Popis</span><span class="sxs-lookup"><span data-stu-id="49698-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="49698-112">Sledování modulu runtime</span><span class="sxs-lookup"><span data-stu-id="49698-112">Tracking runtime</span></span>|<span data-ttu-id="49698-113">Poskytuje infrastrukturu pro vydávání záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="49698-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="49698-114">Sledování účastníci</span><span class="sxs-lookup"><span data-stu-id="49698-114">Tracking participants</span></span>|<span data-ttu-id="49698-115">Využívá sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="49698-115">Consumes the tracking records.</span></span> [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] <span data-ttu-id="49698-116">se dodává s účastníkem sledování, která zapíše záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="49698-116">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="49698-117">Profil sledování Tracking profile</span><span class="sxs-lookup"><span data-stu-id="49698-117">Tracking profile</span></span>|<span data-ttu-id="49698-118">Filtrování mechanismus, který umožňuje sledování účastník přihlásit pouze podmnožinu záznamů sledování vyzařováno instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49698-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="49698-119">Následující tabulka obsahuje podrobnosti o sledování záznamů, které generuje modul runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49698-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="49698-120">Záznam sledování</span><span class="sxs-lookup"><span data-stu-id="49698-120">Tracking Record</span></span>|<span data-ttu-id="49698-121">Popis</span><span class="sxs-lookup"><span data-stu-id="49698-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="49698-122">Pracovní postup instance sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="49698-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="49698-123">Popisuje životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49698-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="49698-124">Například záznam instance je vygenerován při spuštění pracovního postupu nebo dokončení.</span><span class="sxs-lookup"><span data-stu-id="49698-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="49698-125">Stav sledování záznamů aktivit.</span><span class="sxs-lookup"><span data-stu-id="49698-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="49698-126">Podrobnosti provádění aktivity.</span><span class="sxs-lookup"><span data-stu-id="49698-126">Details activity execution.</span></span> <span data-ttu-id="49698-127">Tyto záznamy ukazují stav pracovního postupu aktivity, jako je například kdy je naplánováno aktivitu nebo při dokončení aktivity nebo kdy je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="49698-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="49698-128">Záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="49698-128">Bookmark resumption record.</span></span>|<span data-ttu-id="49698-129">Pokaždé, když obnovení záložku v instanci pracovního postupu, protože ho.</span><span class="sxs-lookup"><span data-stu-id="49698-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="49698-130">Vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="49698-130">Custom Tracking Records.</span></span>|<span data-ttu-id="49698-131">Autor pracovního postupu můžete vytvořit vlastní záznamy sledování a generovat vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="49698-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="49698-132">Účastník sledování přihlásí pro podmnožinu vygenerovanou <xref:System.Activities.Tracking.TrackingRecord> objekty pomocí sledování profilů.</span><span class="sxs-lookup"><span data-stu-id="49698-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="49698-133">Profil sledování obsahuje sledování dotazy, které umožňují přihlášení k odběru pro sledování konkrétní typ záznamu.</span><span class="sxs-lookup"><span data-stu-id="49698-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="49698-134">Sledování profily se dá nastavit v kódu nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="49698-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="49698-135">Vlastní sledování účastník</span><span class="sxs-lookup"><span data-stu-id="49698-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="49698-136">Umožňuje sledování účastník rozhraní API rozšíření modulu runtime sledování pomocí sledování účastník zadaného uživatelem, který může obsahovat vlastní logiku ke zpracování <xref:System.Activities.Tracking.TrackingRecord> objekty, protože ho vygeneroval modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49698-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="49698-137">Zapsat sledování účastníka uživatel musí implementovat <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="49698-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="49698-138">Konkrétně <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> musí implementovat vlastní účastníka.</span><span class="sxs-lookup"><span data-stu-id="49698-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="49698-139">Tato metoda je volána, když <xref:System.Activities.Tracking.TrackingRecord> je vygenerován pomocí modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49698-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="49698-140">Účastník sledování dokončení je implementováno v souboru ConsoleTrackingParticipant.cs. Následující ukázka kódu je <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metodu pro vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="49698-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

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

 <span data-ttu-id="49698-141">Následující příklad kódu přidá účastníka konzoly původce volání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49698-141">The following code example adds the console participant to the workflow invoker.</span></span>

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

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="49698-142">Generování vlastní záznamy sledování</span><span class="sxs-lookup"><span data-stu-id="49698-142">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="49698-143">Tento příklad také ukazuje možnost generování <xref:System.Activities.Tracking.CustomTrackingRecord> objekty z vlastního pracovního postupu aktivity:</span><span class="sxs-lookup"><span data-stu-id="49698-143">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

-   <span data-ttu-id="49698-144"><xref:System.Activities.Tracking.CustomTrackingRecord> Objekty jsou vytvořeny a naplněny s uživatelem definované datové části, který je žádoucí, aby měl vyzařovaného se záznamem.</span><span class="sxs-lookup"><span data-stu-id="49698-144">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

-   <span data-ttu-id="49698-145"><xref:System.Activities.Tracking.CustomTrackingRecord> Je vygenerován pomocí volání metody sledování <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="49698-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="49698-146">Následující příklad ukazuje, jak vygenerovat <xref:System.Activities.Tracking.CustomTrackingRecord> objektů v rámci vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="49698-146">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="49698-147">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="49698-147">To use this sample</span></span>

1. <span data-ttu-id="49698-148">Pomocí sady Visual Studio 2010, otevřete soubor řešení CustomTrackingSample.sln.</span><span class="sxs-lookup"><span data-stu-id="49698-148">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="49698-149">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="49698-149">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="49698-150">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="49698-150">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="49698-151">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="49698-151">The samples may already be installed on your computer.</span></span> <span data-ttu-id="49698-152">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="49698-152">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="49698-153">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="49698-153">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="49698-154">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="49698-154">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="49698-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49698-155">See also</span></span>

- [<span data-ttu-id="49698-156">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="49698-156">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
