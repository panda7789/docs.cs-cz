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
# <a name="custom-tracking"></a>Vlastní sledování
Tento příklad ukazuje, jak vytvořit vlastního účastníka sledování a zapsat obsah sledování dat do konzoly. Kromě toho Ukázka ukazuje, jak vygenerovat <xref:System.Activities.Tracking.CustomTrackingRecord> objekty naplněné uživatelsky definovanými daty. Účastník sledování na základě konzoly filtruje objekty <xref:System.Activities.Tracking.TrackingRecord> generované pracovním postupem pomocí objektu sledování profilu vytvořeného v kódu.

## <a name="sample-details"></a>Podrobnosti ukázky
 Programovací model Windows Workflow Foundation (WF) poskytuje sledovací infrastrukturu pro sledování provádění instance pracovního postupu. Sledovací modul sledování implementuje instanci pracovního postupu k vygenerování událostí souvisejících s životním cyklem pracovního postupu, událostí z aktivit pracovního postupu a vlastními událostmi sledování. Následující tabulka podrobně popisuje primární součásti infrastruktury sledování.

|Komponenta|Popis|
|---------------|-----------------|
|Sledování – modul runtime|Poskytuje infrastrukturu pro vygenerování záznamů sledování.|
|Sledování účastníků|Využívá záznamy sledování. .NET Framework 4 jsou dodávány s účastníkem sledování, který zapisuje záznamy sledování jako události ETW (Event Tracing for Windows).|
|Profil sledování|Mechanismus filtrování, který umožňuje sledování účastníka přihlásit k odběru podmnožiny sledovacích záznamů emitovaných z instance pracovního postupu.|

 Následující tabulka podrobně popisuje záznamy sledování, které modul runtime pracovního postupu generuje.

|Záznam sledování|Popis|
|---------------------|-----------------|
|Záznamy sledování instance pracovního postupu.|Popisuje životní cyklus instance pracovního postupu. Například záznam instance je generován při spuštění nebo dokončení pracovního postupu.|
|Záznamy sledování stavu aktivity.|Podrobnosti provádění aktivity. Tyto záznamy označují stav aktivity pracovního postupu, například když je naplánována aktivita nebo když se aktivita dokončí nebo když je vyvolána chyba.|
|Záznam opětovného pokračování záložky|Vygenerováno pokaždé, když je obnovena záložka v instanci pracovního postupu.|
|Vlastní záznamy sledování.|Autor pracovního postupu může vytvořit vlastní záznamy sledování a vygenerovat je v rámci vlastní aktivity.|

 Účastník sledování přihlašuje odběr podmnožiny vygenerovaných <xref:System.Activities.Tracking.TrackingRecord> objektů pomocí sledování profilů. Profil sledování obsahuje sledovací dotazy, které umožňují přihlášení k odběru konkrétního typu záznamu sledování. Sledování profilů lze zadat v kódu nebo v konfiguraci.

### <a name="custom-tracking-participant"></a>Účastník vlastního sledování
 Rozhraní API sledování účastníka umožňuje rozšíření sledovacího modulu Sledování s účastníkem sledování, které může zahrnovat vlastní logiku pro zpracování <xref:System.Activities.Tracking.TrackingRecord> objektů generovaných modulem runtime pracovního postupu.

 K zápisu účastníka sledování musí uživatel implementovat <xref:System.Activities.Tracking.TrackingParticipant>. Konkrétně musí být metoda <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> implementovaná vlastním účastníkem. Tato metoda je volána, když je <xref:System.Activities.Tracking.TrackingRecord> vyvolána modulem runtime pracovního postupu.

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 Dokončený účastník sledování je implementován v souboru ConsoleTrackingParticipant.cs. Následující příklad kódu je metoda <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> pro vlastního účastníka sledování.

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

- Objekty <xref:System.Activities.Tracking.CustomTrackingRecord> jsou vytvořeny a naplněny uživatelsky definovanými daty, která mají být vygenerována záznamem.

- <xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerována voláním metody Track <xref:System.Activities.ActivityContext>.

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
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Viz také

- [Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
