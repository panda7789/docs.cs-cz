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
# <a name="custom-tracking"></a>Vlastní sledování
Tato ukázka ukazuje, jak vytvořit vlastní účastníksledování a zapsat obsah dat sledování do konzoly. Kromě toho ukázka ukazuje, jak <xref:System.Activities.Tracking.CustomTrackingRecord> vyzařovat objekty naplněné uživatelem definovaná data. Účastník sledování na základě <xref:System.Activities.Tracking.TrackingRecord> konzoly filtruje objekty vyzařované pracovním postupem pomocí objektu profilu sledování vytvořeného v kódu.

## <a name="sample-details"></a>Podrobnosti ukázky
 Windows Workflow Foundation (WF) poskytuje infrastrukturu sledování ke sledování provádění instance pracovního postupu. Doba sledování runtime implementuje instanci pracovního postupu k vyzařování událostí souvisejících s životním cyklem pracovního postupu, událostmi z aktivit pracovního postupu a vlastními událostmi sledování. V následující tabulce jsou uvedeny hlavní součásti infrastruktury sledování.

|Komponenta|Popis|
|---------------|-----------------|
|Sledování běhu|Poskytuje infrastrukturu pro vyzařování záznamů sledování.|
|Sledování účastníků|Spotřebovává záznamy sledování. Rozhraní .NET Framework 4 je dodáván s účastníkem sledování, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW).|
|Profil sledování|Mechanismus filtrování, který umožňuje účastníkovi sledování přihlásit se k odběru podmnožiny záznamů sledování vyzařovaných z instance pracovního postupu.|

 V následující tabulce jsou podrobně uvedeny záznamy sledování, které vydává za běhu pracovního postupu.

|Záznam sledování|Popis|
|---------------------|-----------------|
|Záznamy sledování instancí pracovního postupu.|Popisuje životní cyklus instance pracovního postupu. Například záznam instance je emitován při spuštění nebo dokončení pracovního postupu.|
|Záznamy sledování stavu aktivity.|Podrobnosti provádění aktivity. Tyto záznamy označují stav aktivity pracovního postupu, například když je aktivita naplánována nebo když je aktivita dokončena nebo když je vyvolána chyba.|
|Záznam obnovení záložky.|Vydává se vždy, když je záložka v instanci pracovního postupu obnovena.|
|Vlastní záznamy sledování.|Autor pracovního postupu může vytvořit vlastní záznamy sledování a vypouštět je v rámci vlastní aktivity.|

 Účastník sledování se přihlásí k odběru podmnožiny emitovaných <xref:System.Activities.Tracking.TrackingRecord> objektů pomocí profilů sledování. Profil sledování obsahuje sledování dotazů, které umožňují přihlášení k odběru pro konkrétní typ záznamu sledování. Profily sledování lze zadat v kódu nebo v konfiguraci.

### <a name="custom-tracking-participant"></a>Vlastní účastník sledování
 Rozhraní API účastníka sledování umožňuje rozšíření sledování runtime s uživatelem za <xref:System.Activities.Tracking.TrackingRecord> předpokladu, sledování účastníka, který může zahrnovat vlastní logiku pro zpracování objektů vyzařovaných runtime pracovního postupu.

 Chcete-li napsat účastníka <xref:System.Activities.Tracking.TrackingParticipant>sledování, musí uživatel implementovat . Konkrétně <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda musí být implementována vlastní účastník. Tato metoda je <xref:System.Activities.Tracking.TrackingRecord> volána při a je emitován runtime pracovního postupu.

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 Kompletní sledování účastníkje implementována v souboru ConsoleTrackingParticipant.cs. Následující příklad kódu <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> je metoda pro vlastní účastníka sledování.

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

 Následující příklad kódu přidá účastníka konzoly do vyvolávače pracovního postupu.

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

### <a name="emitting-custom-tracking-records"></a>Vyzařování vlastních záznamů sledování
 Tato ukázka také ukazuje schopnost <xref:System.Activities.Tracking.CustomTrackingRecord> vyzařovat objekty z vlastní aktivity pracovního postupu:

- Objekty <xref:System.Activities.Tracking.CustomTrackingRecord> jsou vytvořeny a naplněny uživatelem definovaná data, která je žádoucí, aby byly vydány se záznamem.

- Je <xref:System.Activities.Tracking.CustomTrackingRecord> vydáván voláním track metoda <xref:System.Activities.ActivityContext>.

 Následující příklad ukazuje, jak <xref:System.Activities.Tracking.CustomTrackingRecord> vyzařovat objekty v rámci vlastní aktivity.

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

#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Pomocí visual studia 2010 otevřete soubor řešení CustomTrackingSample.sln.

2. Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.

3. Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
