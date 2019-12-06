---
title: Sledování záznamů
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: d59db7e4c90b3cffe523c89de093f58f3e520bde
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837607"
---
# <a name="tracking-records"></a>Sledování záznamů
Modul runtime pracovního postupu se instrumentuje k vygenerování záznamů sledování, které sledují spuštění instance pracovního postupu.  
  
## <a name="tracking-records"></a>Sledování záznamů  
 Následující tabulka podrobně popisuje záznamy sledování, které modul runtime pracovního postupu generuje.  
  
|Záznam sledování|Popis|  
|---------------------|-----------------|  
|Záznamy životního cyklu pracovního postupu|Vygenerováno během různých fází životního cyklu instance pracovního postupu. Záznam je například generován při zahájení nebo dokončení pracovního postupu.|  
|Záznamy životního cyklu aktivity|Podrobnosti provádění aktivity. Tyto záznamy označují stav aktivity pracovního postupu, například když je naplánována aktivita, kdy se aktivita dokončí nebo když dojde k chybě.|  
|Záložek – obnovení záznamů|Vygenerováno pokaždé, když je obnovena záložka v instanci pracovního postupu.|  
|Vlastní záznamy sledování|Autor pracovního postupu může vytvořit vlastní záznamy sledování a vygenerovat je v rámci vlastní aktivity.|  
  
 Všechny záznamy související se sledováním, které jsou generovány z modulu runtime WF, jsou odvozeny ze základní třídy <xref:System.Activities.Tracking.TrackingRecord>, která obsahuje společnou sadu dat. Sledování záznamů zobrazuje životní cyklus jednoduchého pracovního postupu. Každý záznam sledování obsahuje podrobnosti o přidružené události sledování, například <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>a další informace, které jsou specifické pro daný typ záznamu sledování.  
  
 Následující typy objektů <xref:System.Activities.Tracking.TrackingRecord> jsou generovány modulem runtime pracovního postupu:  
  
- **WorkflowInstanceRecord** – tento <xref:System.Activities.Tracking.TrackingRecord> popisuje životní cyklus instance pracovního postupu. Záznam je například generován při spuštění nebo dokončení pracovního postupu a obsahuje stav instance pracovního postupu. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
- **WorkflowInstanceAbortedRecord** – tato <xref:System.Activities.Tracking.TrackingRecord> je generována při přerušení instance pracovního postupu. Záznam obsahuje důvod přerušení instance pracovního postupu. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
- **WorkflowInstanceUnhandledExceptionRecord** – tato <xref:System.Activities.Tracking.TrackingRecord> je vyvolána, pokud dojde k výjimce v instanci pracovního postupu a není zpracována žádnou aktivitou. Záznam obsahuje podrobnosti o výjimce. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
- **WorkflowInstanceSuspendedRecord** – tato <xref:System.Activities.Tracking.TrackingRecord> se emituje pokaždé, když je instance pracovního postupu pozastavená. Záznam obsahuje důvod pozastavení instance pracovního postupu. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
- **WorkflowInstanceTerminatedRecord** – tato <xref:System.Activities.Tracking.TrackingRecord> je generována při každém ukončení instance pracovního postupu. Záznam obsahuje důvod ukončení instance pracovního postupu. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
- **ActivityStateRecord** – tato <xref:System.Activities.Tracking.TrackingRecord> je generována, když se spustí aktivita v pracovním postupu. Tyto záznamy označují stav aktivity v rámci instance pracovního postupu. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
- **ActivityScheduledRecord** – tato <xref:System.Activities.Tracking.TrackingRecord> se emituje, když aktivita naplánuje podřízenou aktivitu. Tento záznam obsahuje podrobnosti pro nadřazenou aktivitu (aktivitu plánování) i naplánovanou podřízenou aktivitu. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
- **FaultPropagationRecord** – tento <xref:System.Activities.Tracking.TrackingRecord> je vygenerován pro každou obslužnou rutinu, která záznam sleduje, dokud není zpracován. Slouží k označení cesty, kterou v instanci pracovního postupu trvala chyba. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
- **CancelRequestedRecord** – tato <xref:System.Activities.Tracking.TrackingRecord> se emituje vždycky, když se aktivita pokusí zrušit podřízenou aktivitu. Tento záznam obsahuje podrobnosti pro nadřazenou aktivitu i podřízenou aktivitu, která je zrušena. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
- **BookmarkResumptionRecord** – tato <xref:System.Activities.Tracking.TrackingRecord> sleduje všechny úspěšně obnovené záložky. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
- **CustomTrackingRecord** – tato <xref:System.Activities.Tracking.TrackingRecord> vytvořená autorem pracovního postupu v rámci vlastní aktivity pracovního postupu. Vlastní záznamy sledování se můžou naplnit daty, která se mají vysílat společně se záznamy. Podrobnosti o tomto záznamu najdete na adrese <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Může se například jednat o jednoduchou aktivitu <xref:System.Activities.Statements.Sequence>, která obsahuje operaci <xref:System.Activities.Statements.WriteLine> se záznamy sledování, které byly generovány v následujícím pořadí:  
  
1. <xref:System.Activities.Tracking.WorkflowInstanceRecord> označuje, že se pracovní postup spouští.  
  
2. <xref:System.Activities.Tracking.ActivityScheduledRecord> označuje, že byla naplánována aktivita. V tomto případě se jedná o aktivitu <xref:System.Activities.Statements.Sequence>.  
  
3. <xref:System.Activities.Tracking.ActivityScheduledRecord> představuje aktivitu <xref:System.Activities.Statements.WriteLine>.  
  
4. Existují dva <xref:System.Activities.Tracking.ActivityStateRecord> záznamy, které představují dokončování dvou aktivit.  
  
5. <xref:System.Activities.Tracking.WorkflowInstanceRecord> označuje, že se pracovní postup dokončuje.  
  
## <a name="see-also"></a>Viz také:

- [Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
