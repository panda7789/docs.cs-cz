---
title: Sledování záznamů
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: 46b52f6b774d1d692c0e7dec400d369428a9607e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699848"
---
# <a name="tracking-records"></a>Sledování záznamů
Modul runtime pracovního postupu je instrumentováno pro vydávání záznamy sledování, sledovat spuštění instance pracovního postupu.  
  
## <a name="tracking-records"></a>Sledování záznamů  
 Následující tabulka obsahuje podrobnosti o sledování záznamů, které generuje modul runtime pracovního postupu.  
  
|Záznam sledování|Popis|  
|---------------------|-----------------|  
|Životní cyklus záznamů pracovního postupu|Generované různých fázích životního cyklu instance pracovního postupu. Například záznam je vygenerován při spuštění pracovního postupu nebo dokončení.|  
|Životní cyklus záznamů aktivit|Podrobnosti provádění aktivity. Tyto záznamy ukazují stav aktivity pracovního postupu, jako je aktivita plánu, při dokončení aktivity nebo dojde k chybě.|  
|Záložku obnovení záznamů|Pokaždé, když obnovení záložku v instanci pracovního postupu, protože ho.|  
|Vlastní sledování záznamů|Autor pracovního postupu můžete vytvořit vlastní záznamy sledování a generování v rámci vlastní aktivity.|  
  
 Všechny záznamy sledování vyzařovaného z modulu runtime pracovního postupu jsou odvozeny od základní třídy <xref:System.Activities.Tracking.TrackingRecord>, který obsahuje společnou sadu dat. Zobrazit záznamy sledování životního cyklu pro jednoduchý pracovní postup. Každý záznam sledování obsahuje podrobnosti o události přidružené sledování, jako <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>a další informace, které jsou specifické pro daný typ záznamu sledování.  
  
 Následující typy <xref:System.Activities.Tracking.TrackingRecord> objekty jsou emitovány modulem runtime pracovního postupu:  
  
- **WorkflowInstanceRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> popisuje životního cyklu instance pracovního postupu. Záznam je vygenerován například, když se pracovní postup spustí nebo dokončí a obsahuje informace o stavu instance pracovního postupu. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
- **WorkflowInstanceAbortedRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerován při přerušení instance pracovního postupu. Záznam obsahuje důvod pro instanci pracovního postupu přerušení. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
- **WorkflowInstanceUnhandledExceptionRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je aktivováno, pokud výjimka nastane v instanci pracovního postupu a není zpracována žádnou aktivitu. Záznam obsahuje podrobnosti o výjimce. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
- **WorkflowInstanceSuspendedRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerován pokaždé, když se instance pracovního postupu je pozastaveno. Záznam obsahuje důvod pro instanci pracovního postupu bylo pozastaveno. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
- **WorkflowInstanceTerminatedRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerován pokaždé, když se instance pracovního postupu je ukončeno. Záznam obsahuje důvod ukončení instance pracovního postupu. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
- **ActivityStateRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerován, když se spustí aktivita v rámci pracovního postupu. Tyto záznamy ukazují stavu aktivity v rámci instance pracovního postupu. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
- **ActivityScheduledRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerován při plánování podřízená aktivita aktivity. Tento záznam obsahuje podrobnosti o Nadřazená aktivita (plánování aktivit) a plánované podřízené aktivity. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
- **FaultPropagationRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerován pro každou obslužnou rutinu, která srovnává záznam, dokud není zpracována. Používá se k označení cestu, kterou trvalo chybu v rámci instance pracovního postupu. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
- **CancelRequestedRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerován pokaždé, když se pokusí aktivitu pro zrušení podřízené aktivity. Tento záznam obsahuje podrobnosti pro aktivitu nadřazené a podřízené aktivity, která je právě rušen. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
- **BookmarkResumptionRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> sleduje všechny záložky, který se úspěšně obnovil. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
- **CustomTrackingRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> se vytvoří a, protože ho vygeneroval Autor pracovního postupu uvnitř pracovního postupu vlastní aktivity. Vlastní sledování záznamů je možné naplnit data emitování spolu s záznamy. Najdete podrobnosti o tento záznam v <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Například může být ke jednoduchý <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje <xref:System.Activities.Statements.WriteLine> operaci s sledování záznamů, protože ho v následujícím pořadí:  
  
1. <xref:System.Activities.Tracking.WorkflowInstanceRecord> Označuje, že se spouští pracovní postup.  
  
2. <xref:System.Activities.Tracking.ActivityScheduledRecord> Označuje, že byla plánována aktivity. V tomto případě jde <xref:System.Activities.Statements.Sequence> aktivity.  
  
3. <xref:System.Activities.Tracking.ActivityScheduledRecord> představuje <xref:System.Activities.Statements.WriteLine> aktivity.  
  
4. Existují dva <xref:System.Activities.Tracking.ActivityStateRecord> záznamy, které představují dvě aktivity dokončení.  
  
5. <xref:System.Activities.Tracking.WorkflowInstanceRecord> Označuje, že je dokončení pracovního postupu.  
  
## <a name="see-also"></a>Viz také:

- [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
