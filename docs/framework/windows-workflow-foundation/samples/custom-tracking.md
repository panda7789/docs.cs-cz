---
title: Vlastní sledování
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: c986d9845bb76219ad8b0657a3a7252aaaf4c6cd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886276"
---
# <a name="custom-tracking"></a>Vlastní sledování
Tento příklad znázorňuje způsob vytvoření vlastního účastníka sledování a zapisovat obsah data sledování do konzoly. Kromě toho Ukázka předvádí, jak vygenerovat <xref:System.Activities.Tracking.CustomTrackingRecord> objekty vyplní s uživatelem definovaná data. Filtry účastníka sledování pomocí konzoly <xref:System.Activities.Tracking.TrackingRecord> objekty, protože ho vygeneroval pracovního postupu pomocí profilu sledování objekt vytvořený v kódu.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Windows Workflow Foundation (WF) poskytuje sledování infrastruktury pro sledování spuštění instance pracovního postupu. Modul runtime sledování implementuje instance pracovního postupu ke generování událostí souvisejících s životního cyklu pracovního postupu, události z aktivit pracovního postupu a vlastního sledování událostí. Následující tabulka obsahuje podrobnosti o primární součásti sledování infrastruktury.  
  
|Součást|Popis|  
|---------------|-----------------|  
|Sledování modulu runtime|Poskytuje infrastrukturu pro vydávání záznamy sledování.|  
|Sledování účastníci|Využívá sledování záznamů. [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] se dodává s účastníkem sledování, která zapíše záznamy sledování jako události trasování událostí pro Windows (ETW).|  
|Profil sledování Tracking profile|Filtrování mechanismus, který umožňuje sledování účastník přihlásit pouze podmnožinu záznamů sledování vyzařováno instance pracovního postupu.|  
  
 Následující tabulka obsahuje podrobnosti o sledování záznamů, které generuje modul runtime pracovního postupu.  
  
|Záznam sledování|Popis|  
|---------------------|-----------------|  
|Pracovní postup instance sledování záznamů.|Popisuje životního cyklu instance pracovního postupu. Například záznam instance je vygenerován při spuštění pracovního postupu nebo dokončení.|  
|Stav sledování záznamů aktivit.|Podrobnosti provádění aktivity. Tyto záznamy ukazují stav pracovního postupu aktivity, jako je například kdy je naplánováno aktivitu nebo při dokončení aktivity nebo kdy je vyvolána chyba.|  
|Záložku obnovení záznamů.|Pokaždé, když obnovení záložku v instanci pracovního postupu, protože ho.|  
|Vlastní sledování záznamů.|Autor pracovního postupu můžete vytvořit vlastní záznamy sledování a generovat vlastní aktivity.|  
  
 Účastník sledování přihlásí pro podmnožinu vygenerovanou <xref:System.Activities.Tracking.TrackingRecord> objekty pomocí sledování profilů. Profil sledování obsahuje sledování dotazy, které umožňují přihlášení k odběru pro sledování konkrétní typ záznamu. Sledování profily se dá nastavit v kódu nebo v konfiguraci.  
  
### <a name="custom-tracking-participant"></a>Vlastní sledování účastník  
 Umožňuje sledování účastník rozhraní API rozšíření modulu runtime sledování pomocí sledování účastník zadaného uživatelem, který může obsahovat vlastní logiku ke zpracování <xref:System.Activities.Tracking.TrackingRecord> objekty, protože ho vygeneroval modulu runtime pracovního postupu.  
  
 Zapsat sledování účastníka uživatel musí implementovat <xref:System.Activities.Tracking.TrackingParticipant>. Konkrétně <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> musí implementovat vlastní účastníka. Tato metoda je volána, když <xref:System.Activities.Tracking.TrackingRecord> je vygenerován pomocí modulu runtime pracovního postupu.  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 Účastník sledování dokončení je implementováno v souboru ConsoleTrackingParticipant.cs. Následující ukázka kódu je <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metodu pro vlastní sledování účastník.  
  
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
  
 Následující příklad kódu přidá účastníka konzoly původce volání pracovního postupu.  
  
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
  
### <a name="emitting-custom-tracking-records"></a>Generování vlastní záznamy sledování  
 Tento příklad také ukazuje možnost generování <xref:System.Activities.Tracking.CustomTrackingRecord> objekty z vlastního pracovního postupu aktivity:  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> Objekty jsou vytvořeny a naplněny s uživatelem definované datové části, který je žádoucí, aby měl vyzařovaného se záznamem.  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> Je vygenerován pomocí volání metody sledování <xref:System.Activities.ActivityContext>.  
  
 Následující příklad ukazuje, jak vygenerovat <xref:System.Activities.Tracking.CustomTrackingRecord> objektů v rámci vlastní aktivity.  
  
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
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
