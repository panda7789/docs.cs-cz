---
title: Vlastní sledování
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: b53b22b485a7ac340821073d2f2914b13a7b7011
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044305"
---
# <a name="custom-tracking"></a>Vlastní sledování
Tento příklad ukazuje, jak vytvořit vlastního účastníka sledování a zapsat obsah sledování dat do konzoly. Kromě toho Ukázka ukazuje, jak vygenerovat <xref:System.Activities.Tracking.CustomTrackingRecord> objekty naplněné uživatelsky definovanými daty. Účastník sledování na základě konzoly filtruje <xref:System.Activities.Tracking.TrackingRecord> objekty emitované pracovním postupem pomocí objektu sledování profilu vytvořeného v kódu.

## <a name="sample-details"></a>Podrobnosti ukázky
 Programovací model Windows Workflow Foundation (WF) poskytuje sledovací infrastrukturu pro sledování provádění instance pracovního postupu. Sledovací modul sledování implementuje instanci pracovního postupu k vygenerování událostí souvisejících s životním cyklem pracovního postupu, událostí z aktivit pracovního postupu a vlastními událostmi sledování. Následující tabulka podrobně popisuje primární součásti infrastruktury sledování.

|Součást|Popis|
|---------------|-----------------|
|Sledování – modul runtime|Poskytuje infrastrukturu pro vygenerování záznamů sledování.|
|Sledování účastníků|Využívá záznamy sledování. [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]dodává se sledováním účastníka, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW).|
|Profil sledování|Mechanismus filtrování, který umožňuje sledování účastníka přihlásit k odběru podmnožiny sledovacích záznamů emitovaných z instance pracovního postupu.|

 Následující tabulka podrobně popisuje záznamy sledování, které modul runtime pracovního postupu generuje.

|Záznam sledování|Popis|
|---------------------|-----------------|
|Záznamy sledování instance pracovního postupu.|Popisuje životní cyklus instance pracovního postupu. Například záznam instance je generován při spuštění nebo dokončení pracovního postupu.|
|Záznamy sledování stavu aktivity.|Podrobnosti provádění aktivity. Tyto záznamy označují stav aktivity pracovního postupu, například když je naplánována aktivita nebo když se aktivita dokončí nebo když je vyvolána chyba.|
|Záznam opětovného pokračování záložky|Vygenerováno pokaždé, když je obnovena záložka v instanci pracovního postupu.|
|Vlastní záznamy sledování.|Autor pracovního postupu může vytvořit vlastní záznamy sledování a vygenerovat je v rámci vlastní aktivity.|

 Účastník sledování se přihlásí k odběru podmnožiny <xref:System.Activities.Tracking.TrackingRecord> vygenerovaných objektů pomocí sledování profilů. Profil sledování obsahuje sledovací dotazy, které umožňují přihlášení k odběru konkrétního typu záznamu sledování. Sledování profilů lze zadat v kódu nebo v konfiguraci.

### <a name="custom-tracking-participant"></a>Účastník vlastního sledování
 Rozhraní API sledování účastníka umožňuje rozšíření sledovacího modulu Sledování s účastníkem sledování, které může zahrnovat vlastní logiku pro zpracování <xref:System.Activities.Tracking.TrackingRecord> objektů generovaných modulem runtime pracovního postupu.

 Pro zápis účastníka sledování, který musí uživatel <xref:System.Activities.Tracking.TrackingParticipant>implementovat. Konkrétně musí být metoda implementovaná vlastním účastníkem. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> Tato metoda je volána, když <xref:System.Activities.Tracking.TrackingRecord> je vyvolána modulem runtime pracovního postupu.

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 Dokončený účastník sledování je implementován v souboru ConsoleTrackingParticipant.cs. Následující příklad kódu je <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda pro vlastní sledování účastník.

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

 Následující příklad kódu přidá účastníka konzoly do pracovního postupu původce.

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

### <a name="emitting-custom-tracking-records"></a>Emitování vlastních záznamů sledování
 Tato ukázka také ukazuje možnost generovat <xref:System.Activities.Tracking.CustomTrackingRecord> objekty z vlastní aktivity pracovního postupu:

- <xref:System.Activities.Tracking.CustomTrackingRecord> Objekty jsou vytvořeny a naplněny uživatelsky definovanými daty, která mají být vygenerována záznamem.

- Je vyvolána voláním metody Track v <xref:System.Activities.ActivityContext>. <xref:System.Activities.Tracking.CustomTrackingRecord>

 Následující příklad ukazuje, jak vygenerovat <xref:System.Activities.Tracking.CustomTrackingRecord> objekty v rámci vlastní aktivity.

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

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení CustomTrackingSample. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Viz také:

- [Ukázky monitorování technologie AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
