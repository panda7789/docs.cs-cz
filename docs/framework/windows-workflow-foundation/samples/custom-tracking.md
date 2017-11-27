---
title: "Vlastní sledování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3a32e76bdee87d6f00a5f01893e76ccb3de9ef51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-tracking"></a><span data-ttu-id="6c3d3-102">Vlastní sledování</span><span class="sxs-lookup"><span data-stu-id="6c3d3-102">Custom Tracking</span></span>
<span data-ttu-id="6c3d3-103">Tento příklad znázorňuje, jak vytvořit vlastní sledování účastník a zapisovat obsah data sledování do konzoly.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="6c3d3-104">Kromě toho ukázku ukazuje, jak pro vydávání <xref:System.Activities.Tracking.CustomTrackingRecord> naplněný uživatelské objekty definované data.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="6c3d3-105">Filtry účastnické sledování pomocí konzoly <xref:System.Activities.Tracking.TrackingRecord> objekty vysílaných použitím pracovního postupu profil sledování objekt vytvořený v kódu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="6c3d3-106">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6c3d3-106">Sample Details</span></span>  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="6c3d3-107">poskytuje sledování infrastruktury sledovat vykonávání instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-107"> provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="6c3d3-108">Modul runtime sledování implementuje instanci pracovního postupu pro vydávání události související s životního cyklu pracovního postupu, události z aktivit pracovního postupu a sledování vlastních událostí.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="6c3d3-109">V následující tabulce jsou primární součásti sledování infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-109">The following table details the primary components of the tracking infrastructure.</span></span>  
  
|<span data-ttu-id="6c3d3-110">Součást</span><span class="sxs-lookup"><span data-stu-id="6c3d3-110">Component</span></span>|<span data-ttu-id="6c3d3-111">Popis</span><span class="sxs-lookup"><span data-stu-id="6c3d3-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c3d3-112">Sledování runtime</span><span class="sxs-lookup"><span data-stu-id="6c3d3-112">Tracking runtime</span></span>|<span data-ttu-id="6c3d3-113">Poskytuje infrastrukturu pro vydávání sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-113">Provides the infrastructure to emit tracking records.</span></span>|  
|<span data-ttu-id="6c3d3-114">Sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="6c3d3-114">Tracking participants</span></span>|<span data-ttu-id="6c3d3-115">Využívá záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-115">Consumes the tracking records.</span></span> [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="6c3d3-116">se dodává s účastníkem sledování, která zapisuje sledování záznamů jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="6c3d3-116"> ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|  
|<span data-ttu-id="6c3d3-117">Sledování profilu</span><span class="sxs-lookup"><span data-stu-id="6c3d3-117">Tracking profile</span></span>|<span data-ttu-id="6c3d3-118">Filtrační mechanismus, který umožňuje účastníkem sledování k odběru pro podmnožinu sledování záznamy vygenerované z instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|  
  
 <span data-ttu-id="6c3d3-119">V následující tabulce jsou záznamy sledování, které vysílá modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-119">The following table details the tracking records that the workflow runtime emits.</span></span>  
  
|<span data-ttu-id="6c3d3-120">Sledování záznamu</span><span class="sxs-lookup"><span data-stu-id="6c3d3-120">Tracking Record</span></span>|<span data-ttu-id="6c3d3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6c3d3-121">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="6c3d3-122">Záznamy sledování instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="6c3d3-123">Popisuje životní cyklus k instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="6c3d3-124">Například je záznam instance vygenerované při spuštění pracovního postupu nebo dokončení.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|  
|<span data-ttu-id="6c3d3-125">Stav sledování záznamů aktivit.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="6c3d3-126">Podrobnosti o provádění aktivity.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-126">Details activity execution.</span></span> <span data-ttu-id="6c3d3-127">Tyto záznamy označují stav aktivity pracovního postupu, jako je například naplánovaného aktivitu nebo po dokončení aktivity nebo když je vyvolána chybu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|  
|<span data-ttu-id="6c3d3-128">BOOKMARK – obnovení záznamu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-128">Bookmark resumption record.</span></span>|<span data-ttu-id="6c3d3-129">Vygenerované vždy, když je obnoveno záložku v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|  
|<span data-ttu-id="6c3d3-130">Vlastní sledování záznamy.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-130">Custom Tracking Records.</span></span>|<span data-ttu-id="6c3d3-131">Autor pracovního postupu můžete vytvořit vlastní záznamy o sledování a posílat je v rámci vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|  
  
 <span data-ttu-id="6c3d3-132">Přihlásí se k odběru účastník sledování pro podmnožinu emitovaného <xref:System.Activities.Tracking.TrackingRecord> objekty pomocí sledování profilů.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="6c3d3-133">Profil sledování obsahuje dotazy pro sledování, které umožňují přihlášení k odběru pro typ záznamu konkrétní sledování.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="6c3d3-134">Sledování profily mohou být zadané v kódu nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-134">Tracking profiles can be specified in code or in configuration.</span></span>  
  
### <a name="custom-tracking-participant"></a><span data-ttu-id="6c3d3-135">Vlastní sledování účastník</span><span class="sxs-lookup"><span data-stu-id="6c3d3-135">Custom Tracking Participant</span></span>  
 <span data-ttu-id="6c3d3-136">Sledování účastník rozhraní API umožňuje rozšíření modulu runtime sledování s účastníkem sledování zadáno uživatelem, který může obsahovat vlastní logiky pro zpracování <xref:System.Activities.Tracking.TrackingRecord> objekty vygenerované modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="6c3d3-137">K zápisu pro sledování účastnické uživatel musí implementovat <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="6c3d3-138">Konkrétně <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda má k implementaci vlastních účastníkem.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="6c3d3-139">Tato metoda je volána, když <xref:System.Activities.Tracking.TrackingRecord> je vygenerované modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="6c3d3-140">Dokončení sledování účastník je implementována v souboru ConsoleTrackingParticipant.cs. Následující příklad kódu je <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda pro účastníka vlastní sledování.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>  
  
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
  
 <span data-ttu-id="6c3d3-141">Následující příklad kódu přidá účastník konzoly původce pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-141">The following code example adds the console participant to the workflow invoker.</span></span>  
  
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
  
### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="6c3d3-142">Emitování záznamy vlastní sledování</span><span class="sxs-lookup"><span data-stu-id="6c3d3-142">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="6c3d3-143">Tento příklad znázorňuje také možnost pro vydávání <xref:System.Activities.Tracking.CustomTrackingRecord> objekty z aktivity vlastního pracovního postupu:</span><span class="sxs-lookup"><span data-stu-id="6c3d3-143">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>  
  
-   <span data-ttu-id="6c3d3-144"><xref:System.Activities.Tracking.CustomTrackingRecord> Objekty jsou vytvořeny a naplněny s uživatelská data, která je žádoucí, aby se vygenerované pomocí záznamu.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-144">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>  
  
-   <span data-ttu-id="6c3d3-145"><xref:System.Activities.Tracking.CustomTrackingRecord> Je vygenerované voláním metody sledovat <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>  
  
 <span data-ttu-id="6c3d3-146">Následující příklad ukazuje, jak pro vydávání <xref:System.Activities.Tracking.CustomTrackingRecord> objektů v rámci vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-146">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6c3d3-147">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="6c3d3-147">To use this sample</span></span>  
  
1.  <span data-ttu-id="6c3d3-148">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CustomTrackingSample.sln.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomTrackingSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6c3d3-149">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6c3d3-150">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-150">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c3d3-151">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-151">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6c3d3-152">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6c3d3-152">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6c3d3-153">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-153">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c3d3-154">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c3d3-154">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="6c3d3-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c3d3-155">See Also</span></span>  
 [<span data-ttu-id="6c3d3-156">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="6c3d3-156">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
