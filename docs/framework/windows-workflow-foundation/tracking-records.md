---
title: Sledování záznamů
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: b07175943f85b61024030c1e0251e24d1eb35c86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520276"
---
# <a name="tracking-records"></a>Sledování záznamů
Modul runtime pracovního postupu je instrumentována pro vydávání sledování záznamů sledovat provádění instance pracovního postupu.  
  
## <a name="tracking-records"></a>Sledování záznamů  
 V následující tabulce jsou záznamy sledování, které vysílá modulu runtime pracovního postupu.  
  
|Sledování záznamu|Popis|  
|---------------------|-----------------|  
|Životní cyklus záznamy pracovního postupu|Vygenerované různých fázích životního cyklu instance pracovního postupu. Záznam je například vygenerované při spuštění pracovního postupu nebo dokončení.|  
|Životní cyklus záznamů aktivit|Podrobnosti o provádění aktivity. Tyto záznamy označují stav aktivity pracovního postupu, jako když bude naplánované aktivity, při dokončení aktivity, nebo když dojde k chybě.|  
|BOOKMARK – obnovení záznamů|Vygenerované vždy, když je obnoveno záložku v rámci instance pracovního postupu.|  
|Vlastní sledování záznamů|Autor pracovního postupu můžete vytvořit vlastní sledování záznamů a posílat je v rámci vlastní aktivity.|  
  
 Všechny záznamy sledování vygenerované z modulu runtime pracovního postupu odvozeny od základní třídy <xref:System.Activities.Tracking.TrackingRecord>, který obsahuje společnou sadu dat. Sledování záznamy zobrazit životního cyklu pro jednoduché pracovního postupu. Každý záznam sledování obsahuje podrobnosti o události přidružené sledování, jako <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>a další informace, které jsou specifické pro daný typ sledování záznamu.  
  
 Následující typy <xref:System.Activities.Tracking.TrackingRecord> objekty jsou vygenerované modulem runtime pracovního postupu:  
  
-   **WorkflowInstanceRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> popisuje životní cyklus k instanci pracovního postupu. Záznam je například vygenerované, když se pracovní postup spustí nebo dokončí a obsahuje informace o stavu instance pracovního postupu. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
-   **WorkflowInstanceAbortedRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerované při zrušení instance pracovního postupu. Záznam obsahuje důvod k instanci pracovního postupu přerušení. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
-   **WorkflowInstanceUnhandledExceptionRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> jsou vydávány, pokud k výjimce dojde v instanci pracovního postupu a nejsou zpracovávány pomocí žádné aktivity. Záznam obsahuje podrobnosti o výjimce. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
-   **WorkflowInstanceSuspendedRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerované vždy, když je pozastaveno instanci pracovního postupu. Záznam obsahuje důvod k instanci pracovního postupu se pozastaví. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
-   **WorkflowInstanceTerminatedRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerované vždy, když je ukončen instanci pracovního postupu. Záznam obsahuje důvod k instanci pracovního postupu bude ukončen. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
-   **ActivityStateRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerované při spustí aktivita v rámci pracovního postupu. Tyto záznamy označují stav aktivity v rámci instance pracovního postupu. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
-   **ActivityScheduledRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerované při aktivitě plány podřízené aktivity. Tento záznam obsahuje podrobnosti o nadřazené aktivity (plánování aktivit) a plánovaných podřízené aktivity. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
-   **FaultPropagationRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerované pro každou obslužnou rutinu, která vypadá na záznam, dokud není zpracována. Slouží k označení cestu, kterou trvalo chybu v rámci instance pracovního postupu. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
-   **CancelRequestedRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> je vygenerované vždy, když aktivita pokusí zrušení podřízené aktivity. Tento záznam obsahuje podrobnosti o aktivity nadřazené a podřízené aktivity, která probíhá její zrušení. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
-   **BookmarkResumptionRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> sleduje všechny záložku, na kterou je byl úspěšně obnoven. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
-   **CustomTrackingRecord** – toto <xref:System.Activities.Tracking.TrackingRecord> se vytvoří a vygenerované autorem pracovního postupu uvnitř pracovního postupu vlastní aktivity. Vlastní sledování záznamů je možné importovat s daty pro vypuštění společně s záznamy. Podrobnosti o tento záznam naleznete na adrese <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Například může být ke jednoduchou <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje <xref:System.Activities.Statements.WriteLine> operaci s sledování záznamy vygenerované v následujícím pořadí:  
  
1.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> Označuje, že se spouští pracovní postup.  
  
2.  <xref:System.Activities.Tracking.ActivityScheduledRecord> Označuje, že bylo naplánováno aktivitu. V takovém případě je <xref:System.Activities.Statements.Sequence> aktivity.  
  
3.  <xref:System.Activities.Tracking.ActivityScheduledRecord> představuje <xref:System.Activities.Statements.WriteLine> aktivity.  
  
4.  Existují dva <xref:System.Activities.Tracking.ActivityStateRecord> záznamy, které představují dvě aktivity dokončení.  
  
5.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> Označuje, že je dokončení pracovního postupu.  
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
