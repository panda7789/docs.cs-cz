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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71a27ffb1c18f0f5ae6f30cac432d5ffd8712b74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-tracking"></a>Vlastní sledování
Tento příklad znázorňuje, jak vytvořit vlastní sledování účastník a zapisovat obsah data sledování do konzoly. Kromě toho ukázku ukazuje, jak pro vydávání <xref:System.Activities.Tracking.CustomTrackingRecord> naplněný uživatelské objekty definované data. Filtry účastnické sledování pomocí konzoly <xref:System.Activities.Tracking.TrackingRecord> objekty vysílaných použitím pracovního postupu profil sledování objekt vytvořený v kódu.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]poskytuje sledování infrastruktury sledovat vykonávání instance pracovního postupu. Modul runtime sledování implementuje instanci pracovního postupu pro vydávání události související s životního cyklu pracovního postupu, události z aktivit pracovního postupu a sledování vlastních událostí. V následující tabulce jsou primární součásti sledování infrastruktury.  
  
|Součást|Popis|  
|---------------|-----------------|  
|Sledování runtime|Poskytuje infrastrukturu pro vydávání sledování záznamů.|  
|Sledování účastníků|Využívá záznamy sledování. [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]se dodává s účastníkem sledování, která zapisuje sledování záznamů jako události trasování událostí pro Windows (ETW).|  
|Sledování profilu|Filtrační mechanismus, který umožňuje účastníkem sledování k odběru pro podmnožinu sledování záznamy vygenerované z instance pracovního postupu.|  
  
 V následující tabulce jsou záznamy sledování, které vysílá modulu runtime pracovního postupu.  
  
|Sledování záznamu|Popis|  
|---------------------|-----------------|  
|Záznamy sledování instance pracovního postupu.|Popisuje životní cyklus k instanci pracovního postupu. Například je záznam instance vygenerované při spuštění pracovního postupu nebo dokončení.|  
|Stav sledování záznamů aktivit.|Podrobnosti o provádění aktivity. Tyto záznamy označují stav aktivity pracovního postupu, jako je například naplánovaného aktivitu nebo po dokončení aktivity nebo když je vyvolána chybu.|  
|BOOKMARK – obnovení záznamu.|Vygenerované vždy, když je obnoveno záložku v rámci instance pracovního postupu.|  
|Vlastní sledování záznamy.|Autor pracovního postupu můžete vytvořit vlastní záznamy o sledování a posílat je v rámci vlastní aktivity.|  
  
 Přihlásí se k odběru účastník sledování pro podmnožinu emitovaného <xref:System.Activities.Tracking.TrackingRecord> objekty pomocí sledování profilů. Profil sledování obsahuje dotazy pro sledování, které umožňují přihlášení k odběru pro typ záznamu konkrétní sledování. Sledování profily mohou být zadané v kódu nebo v konfiguraci.  
  
### <a name="custom-tracking-participant"></a>Vlastní sledování účastník  
 Sledování účastník rozhraní API umožňuje rozšíření modulu runtime sledování s účastníkem sledování zadáno uživatelem, který může obsahovat vlastní logiky pro zpracování <xref:System.Activities.Tracking.TrackingRecord> objekty vygenerované modulem runtime pracovního postupu.  
  
 K zápisu pro sledování účastnické uživatel musí implementovat <xref:System.Activities.Tracking.TrackingParticipant>. Konkrétně <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda má k implementaci vlastních účastníkem. Tato metoda je volána, když <xref:System.Activities.Tracking.TrackingRecord> je vygenerované modulem runtime pracovního postupu.  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 Dokončení sledování účastník je implementována v souboru ConsoleTrackingParticipant.cs. Následující příklad kódu je <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda pro účastníka vlastní sledování.  
  
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
  
 Následující příklad kódu přidá účastník konzoly původce pracovního postupu.  
  
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
  
### <a name="emitting-custom-tracking-records"></a>Emitování záznamy vlastní sledování  
 Tento příklad znázorňuje také možnost pro vydávání <xref:System.Activities.Tracking.CustomTrackingRecord> objekty z aktivity vlastního pracovního postupu:  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> Objekty jsou vytvořeny a naplněny s uživatelská data, která je žádoucí, aby se vygenerované pomocí záznamu.  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> Je vygenerované voláním metody sledovat <xref:System.Activities.ActivityContext>.  
  
 Následující příklad ukazuje, jak pro vydávání <xref:System.Activities.Tracking.CustomTrackingRecord> objektů v rámci vlastní aktivity.  
  
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
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CustomTrackingSample.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
