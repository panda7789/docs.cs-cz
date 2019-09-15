---
title: Přehled událostí sledování
ms.date: 03/30/2017
ms.assetid: c1c1ee87-f80a-449b-acd0-50d81eef116e
ms.openlocfilehash: af0c4441b89345b67c46c714d9ab3e5ceb9e3d6f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988970"
---
# <a name="tracking-events-reference"></a>Přehled událostí sledování
Během provádění pracovní postup v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] nástroji vyvolává sledování událostí při pohybu v různých fázích jejich životního cyklu. Hostitel se může přihlásit k odběru těchto událostí a průběžně aktualizovat stav průběhu pracovního postupu během své životnosti. Vyvolaná události sledování jsou popsány v této části.  
  
## <a name="event-reference"></a>Odkaz na událost  
  
|ID události|Úroveň události|Zpráva události|klíčová slova|  
|--------------|-----------------|-------------------|--------------|  
|[100 – WorkflowInstanceRecord](100-workflowinstancerecord.md)|Informace o|Záznam sledování = WorkflowInstanceRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, stav =% 5, poznámky =% 6, soubor s příponou =% 7|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[101 – WorkflowInstanceUnhandledExceptionRecord](101-workflowinstanceunhandledexceptionrecord.md)|Chyba|Záznam sledování = WorkflowInstanceUnhandledExceptionRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, zdroj =% 5, SourceId =% 6, ID instance zdroje =% 7, SourceType =% 8, výjimka =% 9, poznámky =% 10, profilce = % 11|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[102 – WorkflowInstanceAbortedRecord](102-workflowinstanceabortedrecord.md)|Upozornění|Záznam sledování = WorkflowInstanceAbortedRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, důvod =% 5, poznámky =% 6, soubor s příponou =% 7|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[103 – ActivityStateRecord](103-activitystaterecord.md)|Informace o|Záznam sledování = ActivityStateRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, stav =% 4, název =% 5, ActivityId =% 6, ActivityInstanceId =% 7, ActivityTypeName =% 8, argumenty =% 9, proměnné =% 10, poznámky =% 11, název souboru =% 12|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[104 – ActivityScheduledRecord](104-activityscheduledrecord.md)|Informace o|Záznam sledování = ActivityScheduledRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, název =% 4, ActivityId =% 5, ActivityInstanceId =% 6, ActivityTypeName =% 7, ChildActivityName =% 8, ChildActivityId =% 9, ChildActivityInstanceId =% 10, ChildActivityTypeName =% 11, poznámky =% 12, soubor s příponou =% 13|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[105 – FaultPropagationRecord](105-faultpropagationrecord.md)|Upozornění|Záznam sledování = FaultPropagationRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, FaultSourceActivityName =% 4, FaultSourceActivityId =% 5, FaultSourceActivityInstanceId =% 6, FaultSourceActivityTypeName =% 7, FaultHandlerActivityName =% 8, FaultHandlerActivityId =% 9, FaultHandlerActivityInstanceId =% 10, FaultHandlerActivityTypeName =% 11, chyba =% 12, IsFaultSource =% 13, poznámky =% 14, profilový soubor =% 15|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[106 – CancelRequestRecord](106-cancelrequestrecord.md)|Informace o|Záznam sledování = CancelRequestedRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, název =% 4, ActivityId =% 5, ActivityInstanceId =% 6, ActivityTypeName =% 7, ChildActivityName =% 8, ChildActivityId =% 9, ChildActivityInstanceId =% 10, ChildActivityTypeName =% 11, poznámky =% 12, soubor s příponou =% 13|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[107 –– BookmarkResumptionRecord](107-bookmarkresumptionrecord.md)|Informace o|Záznam sledování = BookmarkResumptionRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, název =% 4, SubInstanceID =% 5, OwnerActivityName =% 6, OwnerActivityId =% 7, OwnerActivityInstanceId =% 8, OwnerActivityTypeName =% 9, poznámky =% 10, název souboru: % 11|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[108 – CustomTrackingRecordInfo](108-customtrackingrecordinfo.md)|Informace o|Záznam sledování = CustomTrackingRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, název =% 4, název aktivity =% 5, ActivityId =% 6, ActivityInstanceId =% 7, ActivityTypeName =% 8, data =% 9, poznámky =% 10, název souboru =% 11|UserEvents, EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[110 – CustomTrackingRecordWarning](110-customtrackingrecordwarning.md)|Upozornění|Záznam sledování = CustomTrackingRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, název =% 4, název aktivity =% 5, ActivityId =% 6, ActivityInstanceId =% 7, ActivityTypeName =% 8, data =% 9, poznámky =% 10, název souboru =% 11|UserEvents, EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[111 – CustomTrackingRecordError](111-customtrackingrecorderror.md)|Chyba|Záznam sledování = CustomTrackingRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, název =% 4, název aktivity =% 5, ActivityId =% 6, ActivityInstanceId =% 7, ActivityTypeName =% 8, data =% 9, poznámky =% 10, název souboru =% 11|UserEvents, EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[112 – WorkflowInstanceSuspendedRecord](112-workflowinstancesuspendedrecord.md)|Informace o|Záznam sledování = WorkflowInstanceSuspendedRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, důvod =% 5, poznámky =% 6, soubor s příponou =% 7|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[113 – WorkflowInstanceTerminatedRecord](113-workflowinstanceterminatedrecord.md)|Chyba|Záznam sledování = WorkflowInstanceTerminatedRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, důvod =% 5, poznámky =% 6, soubor s příponou =% 7|EndToEndMonitoring, řešení potíží, healthMonitoring, WFTracking|  
|[114 – WorkflowInstanceRecordWithId](114-workflowinstancerecordwithid.md)|Informace o|Záznam sledování = WorkflowInstanceRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, stav =% 5, poznámky =% 6, soubor s příponou =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[115 – WorkflowInstanceAbortedRecordWithId](115-workflowinstanceabortedrecordwithid.md)|Upozornění|Záznam sledování = WorkflowInstanceAbortedRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, důvod =% 5, poznámky =% 6, soubor s příponou =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[116 – WorkflowInstanceSuspendedRecordWithId](116-workflowinstancesuspendedrecordwithid.md)|Informace o|Záznam sledování = WorkflowInstanceSuspendedRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, důvod =% 5, poznámky =% 6, soubor s příponou =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[117 – WorkflowInstanceTerminatedRecordWithId](117-workflowinstanceterminatedrecordwithid.md)|Chyba|Záznam sledování = WorkflowInstanceTerminatedRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, důvod =% 5, poznámky =% 6, soubor s příponou =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[118 – WorkflowInstanceUnhandledExceptionRecordWithId](118-workflowinstanceunhandledexceptionrecordwithid.md)|Chyba|Záznam sledování = WorkflowInstanceUnhandledExceptionRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, zdroj =% 5, SourceId =% 6, ID instance zdroje =% 7, SourceType =% 8, výjimka =% 9, poznámky =% 10, profilce = % 11, WorkflowDefinitionIdentity =% 12|HealthMonitoring, WFTrackingHealthMonitoring, WFTracking|  
|[119 – WorkflowInstanceUpdatedRecord](119-workflowinstanceupdatedrecord.md)|Informace o|Záznam sledování = WorkflowInstanceUpdatedRecord, ID instance =% 1, číslo záznamu =% 2, čas události =% 3, ID definice aktivity =% 4, stav =% 5, původní identita definice =% 6, aktualizovaná identita definice =% 7, poznámky =% 8, soubor s příponou =% 9|HealthMonitoring, WFTracking|  
|[225 – TraceCorrelationKeys](225-tracecorrelationkeys.md)|Informace o|Klíč korelace% 1 byl vypočítán pomocí hodnot% 2 v nadřazeném oboru% 3.|Řešení potíží s WFServices|  
|[440 – StartSignpostEvent1](440-startsignpostevent.md)|Informace o|Hranice aktivity.|Řešení potíží s WFServices|  
|[441– StopSignpostEvent1](441-stopsignpostevent.md)|Informace o|Hranice aktivity.|Řešení potíží s WFServices|  
|[1001 – WorkflowApplicationCompleted](1001-workflowapplicationcompleted.md)|Informace o|WorkflowInstance ID:% 1 byl dokončen v zavřeném stavu.|WFRuntime|  
|[1002 – WorkflowApplicationTerminated](1002-workflowapplicationterminated.md)|Informace o|WorkflowApplication ID:% 1 bylo ukončeno. Byla dokončena v chybovém stavu s výjimkou.|WFRuntime|  
|[1003 – WorkflowInstanceCanceled](1003-workflowinstancecanceled.md)|Informace o|WorkflowInstance ID:% 1 byl dokončen ve zrušeném stavu.|WFRuntime|  
|[1004 – WorkflowInstanceAborted](1004-workflowinstanceaborted.md)|Informace o|WorkflowInstance ID:% 1 byl zrušen s výjimkou.|WFRuntime|  
|[1005 – WorkflowApplicationIdled](1005-workflowapplicationidled.md)|Informace o|WorkflowApplication ID:% 1 přechod do nečinného režimu.|WFRuntime|  
|[1006 – WorkflowApplicationUnhandledException](1006-workflowapplicationunhandledexception.md)|Chyba|WorkflowInstance ID:% 1 zjistil neošetřenou výjimku.  Výjimka vznikla z aktivity '% 2 ', DisplayName: '% 3 '.  Bude provedena tato akce:% 4.|WFRuntime|  
|[1007 – WorkflowApplicationPersisted](1007-workflowapplicationpersisted.md)|Informace o|WorkflowApplication ID:% 1 byl trval.|WFRuntime|  
|[1008 – WorkflowApplicationUnloaded](1008-workflowapplicationunloaded.md)|Informace o|WorkflowInstance ID:% 1 byl uvolněn.|WFRuntime|  
|[1009 – ActivityScheduled](1009-activityscheduled.md)|Informace o|Nadřazená aktivita% 1, DisplayName:% 2, InstanceId:% 3 naplánovala podřízenou aktivitu% 4 s názvem DisplayName% 5 a InstanceId% 6.|WFRuntime|  
|[1010 – ActivityCompleted](1010-activitycompleted.md)|Informace o|Nadřazená aktivita% 1, DisplayName:% 2, InstanceId:% 3 naplánovala podřízenou aktivitu% 4 s názvem DisplayName% 5 a InstanceId% 6.|WFRuntime|  
|[1011 – ScheduleExecuteActivityWorkItem](1011-scheduleexecuteactivityworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 bylo naplánováno ExecuteActivityWorkItem.|WFRuntime|  
|[1012 – StartExecuteActivityWorkItem](1012-startexecuteactivityworkitem.md)|Podrobnosti|Spouští se provádění ExecuteActivityWorkItem pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3.|WFRuntime|  
|[1013 – CompleteExecuteActivityWorkItem](1013-completeexecuteactivityworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 byla dokončena ExecuteActivityWorkItem.|WFRuntime|  
|[1014 – ScheduleCompletionWorkItem](1014-schedulecompletionworkitem.md)|Podrobnosti|Pro nadřazenou aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 bylo naplánováno položka CompletionWorkItem.  Dokončená aktivita% 4 s názvem DisplayName% 5 a InstanceId% 6.|WFRuntime|  
|[1015 – StartCompletionWorkItem](1015-startcompletionworkitem.md)|Podrobnosti|Spouští se provádění položka CompletionWorkItem pro nadřazenou aktivitu% 1, DisplayName:% 2, InstanceId:% 3. Dokončená aktivita% 4 s názvem DisplayName% 5 a InstanceId% 6.|WFRuntime|  
|[1016 – CompleteCompletionWorkItem](1016-completecompletionworkitem.md)|Podrobnosti|Položka CompletionWorkItem byl dokončen pro nadřazenou aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3. Dokončená aktivita% 4 s názvem DisplayName% 5 a InstanceId% 6.|WFRuntime|  
|[1017 – ScheduleCancelActivityWorkItem](1017-schedulecancelactivityworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 bylo naplánováno položka CancelActivityWorkItem.|WFRuntime|  
|[1018 – StartCancelActivityWorkItem](1018-startcancelactivityworkitem.md)|Podrobnosti|Spouští se provádění položka CancelActivityWorkItem pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3.|WFRuntime|  
|[1019 – CompleteCancelActivityWorkItem](1019-completecancelactivityworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 byla dokončena položka CancelActivityWorkItem.|WFRuntime|  
|[1020 – CreateBookmark](1020-createbookmark.md)|Podrobnosti|Byla vytvořena Záložka pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3.  Záložka:% 4, BookmarkScope:% 5.|WFRuntime|  
|[1021 – ScheduleBookmarkWorkItem](1021-schedulebookmarkworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 bylo naplánováno položka BookmarkWorkItem.  Záložka:% 4, BookmarkScope:% 5.|WFRuntime|  
|[1022 – StartBookmarkWorkItem](1022-startbookmarkworkitem.md)|Podrobnosti|Spouští se provádění položka BookmarkWorkItem pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3.  Záložka:% 4, BookmarkScope:% 5.|WFRuntime|  
|[1023 – CompleteBookmarkWorkItem](1023-completebookmarkworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 byla dokončena položka BookmarkWorkItem. Záložka:% 4, BookmarkScope:% 5.|WFRuntime|  
|[1024 – CreateBookmarkScope](1024-createbookmarkscope.md)|Podrobnosti|Byl vytvořen BookmarkScope:% 1.|WFRuntime|  
|[1025 – BookmarkScopeInitialized](1025-bookmarkscopeinitialized.md)|Podrobnosti|BookmarkScope, který měl TemporaryId:% 1 byl inicializován s ID% 2.|WFRuntime|  
|[1026 – ScheduleTransactionContextWorkItem](1026-scheduletransactioncontextworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 bylo naplánováno položka TransactionContextWorkItem.|WFRuntime|  
|[1027 – StartTransactionContextWorkItem](1027-starttransactioncontextworkitem.md)|Podrobnosti|Spouští se provádění položka TransactionContextWorkItem pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3.|WFRuntime|  
|[1028 – CompleteTransactionContextWorkItem](1028-completetransactioncontextworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 byla dokončena položka TransactionContextWorkItem.|WFRuntime|  
|[1029 – ScheduleFaultWorkItem](1029-schedulefaultworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 bylo naplánováno položka FaultWorkItem.  Výjimka byla rozšířena z aktivity% 4 s názvem DisplayName% 5 a InstanceId% 6.|WFRuntime|  
|[1030 – StartFaultWorkItem](1030-startfaultworkitem.md)|Podrobnosti|Spouští se provádění položka FaultWorkItem pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3.  Výjimka byla rozšířena z aktivity% 4 s názvem DisplayName% 5 a InstanceId% 6.|WFRuntime|  
|[1031 – CompleteFaultWorkItem](1031-completefaultworkitem.md)|Podrobnosti|Pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3 byla dokončena položka FaultWorkItem. Výjimka byla rozšířena z aktivity% 4 s názvem DisplayName% 5 a InstanceId% 6.|WFRuntime|  
|[1032 – ScheduleRuntimeWorkItem](1032-scheduleruntimeworkitem.md)|Podrobnosti|Běhová pracovní položka byla naplánována pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3.|WFRuntime|  
|[1033 – StartRuntimeWorkItem](1033-startruntimeworkitem.md)|Podrobnosti|Spouští se provádění běhové pracovní položky pro aktivitu% 1 s názvem DisplayName% 2 a InstanceId% 3.|WFRuntime|  
|[1034 – CompleteRuntimeWorkItem](1034-completeruntimeworkitem.md)|Podrobnosti|Běhová pracovní položka byla dokončena pro aktivitu% 1, DisplayName:% 2, InstanceId:% 3.|WFRuntime|  
|[1035 – RuntimeTransactionSet](1035-runtimetransactionset.md)|Podrobnosti|Běhová transakce byla nastavena aktivitou% 1, DisplayName:% 2, InstanceId:% 3.  Provádění bylo izolováno na aktivitu% 4 s názvem DisplayName% 5 a InstanceId% 6.|WFRuntime|  
|[1036 – RuntimeTransactionCompletionRequested](1036-runtimetransactioncompletionrequested.md)|Podrobnosti|Aktivita% 1, DisplayName:% 2, InstanceId:% 3 naplánovala dokončení běhové transakce.|WFRuntime|  
|[1037 – RuntimeTransactionComplete](1037-runtimetransactioncomplete.md)|Podrobnosti|Běhová transakce byla dokončena se stavem '% 1 '.|WFRuntime|  
|[1038 – EnterNoPersistBlock](1038-enternopersistblock.md)|Podrobnosti|Vstup do dočasného bloku|WFRuntime|  
|[1039 – ExitNoPersistBlock](1039-exitnopersistblock.md)|Podrobnosti|Ukončení netrvalého bloku|WFRuntime|  
|[1040 – InArgumentBound](1040-inargumentbound.md)|Podrobnosti|Argument% 1 v aktivitě% 2 s názvem DisplayName% 3 a InstanceId% 4 byl svázán s hodnotou:% 5.|WFActivities|  
|[1041 – WorkflowApplicationPersistableIdle](1041-workflowapplicationpersistableidle.md)|Informace o|WorkflowApplication ID:% 1 je nečinné a trvalé.  Bude provedena tato akce:% 2.|WFRuntime|  
|[1101 – WorkflowActivityStart](1101-workflowactivitystart.md)|Informace o|WorkflowInstance ID:% 1 – aktivita E2E|WFRuntime|  
|[1102 – WorkflowActivityStop](1102-workflowactivitystop.md)|Informace o|WorkflowInstance ID:% 1 – aktivita E2E|WFRuntime|  
|[1103 – WorkflowActivitySuspend](1103-workflowactivitysuspend.md)|Informace o|WorkflowInstance ID:% 1 – aktivita E2E|WFRuntime|  
|[1104 – WorkflowActivityResume](1104-workflowactivityresume.md)|Informace o|WorkflowInstance ID:% 1 – aktivita E2E|WFRuntime|  
|[1124 – InvokeMethodIsStatic](1124-invokemethodisstatic.md)|Informace o|InvokeMethod% 1-metoda je statická.|WFRuntime|  
|[1125 – InvokeMethodIsNotStatic](1125-invokemethodisnotstatic.md)|Informace o|InvokeMethod% 1-metoda není statická.|WFRuntime|  
|[1126 – InvokedMethodThrewException](1126-invokedmethodthrewexception.md)|Informace o|V metodě volané aktivitou% 1 byla vyvolána výjimka. %2|WFRuntime|  
|[1131 – InvokeMethodUseAsyncPattern](1131-invokemethoduseasyncpattern.md)|Informace o|InvokeMethod% 1-metoda používá asynchronní vzorek% 2 a% 3.|WFRuntime|  
|[1132 – InvokeMethodDoesNotUseAsyncPattern](1132-invokemethoddoesnotuseasyncpattern.md)|Informace o|InvokeMethod% 1-metoda nepoužívá asynchronní vzorek.|WFRuntime|  
|[1140 – FlowchartStart](1140-flowchartstart.md)|Informace o|Vývojový diagram% 1-začátek byl naplánován.|WFActivities|  
|[1141 – FlowchartEmpty](1141-flowchartempty.md)|Upozornění|Vývojový diagram% 1 byl spuštěn bez uzlů. V metodě volané aktivitou% 1 byla vyvolána výjimka. %2|WFActivities|  
|[1143 – FlowchartNextNull](1143-flowchartnextnull.md)|Informace o|Vývojový diagram% 1/FlowStep-Next Node má hodnotu null. Spuštění vývojového diagramu skončí.|WFActivities|  
|[1146 – FlowchartSwitchCase](1146-flowchartswitchcase.md)|Informace o|Vývojový diagram% 1/FlowSwitch-případ% 2 byl vybrán.|WFActivities|  
|[1147 – FlowchartSwitchDefault](1147-flowchartswitchdefault.md)|Informace o|Vývojový diagram% 1/FlowSwitch-výchozí příkaz Case byl vybrán.|WFActivities|  
|[1148 – FlowchartSwitchCaseNotFound](1148-flowchartswitchcasenotfound.md)|Informace o|Vývojový diagram% 1/FlowSwitch – nenašly se žádné aktivity Case ani výchozí případ, který by odpovídal výsledku výrazu. Spuštění vývojového diagramu skončí.|WFActivities|  
|[1150 – CompensationState](1150-compensationstate.md)|Informace o|Aktivita CompensableActivity% 1 je ve stavu% 2.|WFActivities|  
|[1223 – SwitchCaseNotFound](1223-switchcasenotfound.md)|Informace o|Aktivita Switch% 1 nenalezla aktivitu Case, která by odpovídala výsledku výrazu.|WFActivities|  
|[1449 – WfMessageReceived](1449-wfmessagereceived.md)|Informace o|Pracovní postup přijal zprávu.|WFServices|  
|[1450 – WfMessageSent](1450-wfmessagesent.md)|Informace o|Z pracovního postupu byla odeslána zpráva.|WFServices|  
|[2021 – ExecuteWorkItemStart](2021-executeworkitemstart.md)|Podrobnosti|Zahájení provádění pracovní položky|WFRuntime|  
|[2022 – ExecuteWorkItemStop](2022-executeworkitemstop.md)|Podrobnosti|Ukončení provádění pracovní položky|WFRuntime|  
|[2023 – SendMessageChannelCacheMiss](2023-sendmessagechannelcachemiss.md)|Podrobnosti|Neúspěšné SendMessageChannelCache|WFRuntime|  
|[2024 – InternalCacheMetadataStart](2024-internalcachemetadatastart.md)|Podrobnosti|InternalCacheMetadata spuštěná u aktivity% 1.|WFRuntime|  
|[2025 – InternalCacheMetadataStop](2025-internalcachemetadatastop.md)|Podrobnosti|InternalCacheMetadata se zastavila u aktivity% 1.|WFRuntime|  
|[2026 – CompileVbExpressionStart](2026-compilevbexpressionstart.md)|Podrobnosti|Probíhá kompilace výrazu jazyka VB% 1.|WFRuntime|  
|[2027 – CacheRootMetadataStart](2027-cacherootmetadatastart.md)|Podrobnosti|Metoda CacheRootMetadata pro spuštěná u aktivity% 1|WFRuntime|  
|[2028 – CacheRootMetadataStop](2028-cacherootmetadatastop.md)|Podrobnosti|Metoda CacheRootMetadata pro se zastavila u aktivity% 1.|WFRuntime|  
|[2029 – CompileVbExpressionStop](2029-compilevbexpressionstop.md)|Podrobnosti|Kompilace výrazu jazyka VB byla dokončena.|WFRuntime|  
|[2576 – TryCatchExceptionFromTry](2576-trycatchexceptionfromtry.md)|Informace o|Aktivita TryCatch% 1 zachytila výjimku typu% 2.|WFActivities|  
|[2577 – TryCatchExceptionDuringCancelation](2577-trycatchexceptionduringcancelation.md)|Upozornění|Podřízená aktivita aktivity TryCatch% 1 vygenerovala výjimku při stornování.|WFActivities|  
|[2578 – TryCatchExceptionFromCatchOrFinally](2578-trycatchexceptionfromcatchorfinally.md)|Upozornění|Aktivita catch nebo finally, která je přidružená k aktivitě TryCatch '% 1 ', vyvolala výjimku.|WFActivities|  
|[3501 – InferredContractDescription](3501-inferredcontractdescription.md)|Informace o|Třída ContractDescription s názvem% 1 a oborem názvů =% 2 byla odvozena od implementace WorkflowService.|WFServices|  
|[3502 – InferredOperationDescription](3502-inferredoperationdescription.md)|Informace o|Vlastnost OperationDescription s názvem% 1 v kontraktu% 2 byla odvozena od implementace WorkflowService. IsOneWay =% 3.|WFServices|  
|[3503 – DuplicateCorrelationQuery](3503-duplicatecorrelationquery.md)|Upozornění|Byl nalezen duplicitní dotaz CorrelationQuery s názvem WHERE = '% 1 '. Při výpočtu korelace se tento duplicitní dotaz nepoužije.|WFServices|  
|[3507 – ServiceEndpointAdded](3507-serviceendpointadded.md)|Informace o|Byl přidán koncový bod služby pro adresu% 1 s vazbou% 2 a kontraktem% 3.|WFServices|  
|[3508 – TrackingProfileNotFound](3508-trackingprofilenotfound.md)|Podrobnosti|Profil TrackingProfile '% 1 ' pro ID definice aktivity '% 2 ' nebyl nalezen. V konfiguračním souboru není nalezen buď profil TrackingProfile, nebo se ID definice aktivity neshoduje.|WFServices|  
|[3550 – BufferOutOfOrderMessageNoInstance](3550-bufferoutofordermessagenoinstance.md)|Informace o|Operace '% 1 ' nemůže být v tuto chvíli provedena. Další pokus bude proveden, jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.|WFServices|  
|[3551 – BufferOutOfOrderMessageNoBookmark](3551-bufferoutofordermessagenobookmark.md)|Informace o|V tuto chvíli nelze provést operaci% 2 v instanci služby% 1. Další pokus bude proveden, jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.|WFServices|  
|[3552 – MaxPendingMessagesPerChannelExceeded](3552-maxpendingmessagesperchannelexceeded.md)|Upozornění|Bylo dosaženo limitu omezení MaxPendingMessagesPerChannel% 1. Pokud chcete tento limit zvýšit, upravte vlastnost MaxPendingMessagesPerChannel na BufferedReceiveServiceBehavior.|WFServices kvót|  
|[3557 – TransactedReceiveScopeEndCommitFailed](3557-transactedreceivescopeendcommitfailed.md)|Informace o|Volání metody EndCommit třídy na CommittableTransaction s ID = '% 1 ' vyvolalo TransactionException s následující zprávou: '% 2 '.|WFServices|  
|[4201 – EndSqlCommandExecute](4201-endsqlcommandexecute.md)|Podrobnosti|Konec provádění příkazu SQL:% 1|WFInstanceStore|  
|[4202 – StartSqlCommandExecute](4202-startsqlcommandexecute.md)|Podrobnosti|Spouštění příkazu SQL:% 1|WFInstanceStore|  
|[4203 – RenewLockSystemError](4203-renewlocksystemerror.md)|Chyba|Nepovedlo se zvětšit vypršení platnosti zámku, vypršení platnosti zámku už vypršelo nebo se odstranil vlastník zámku. Přerušuje se SqlWorkflowInstanceStore.|WFInstanceStore|  
|[4205 – FoundProcessingError](4205-foundprocessingerror.md)|Chyba|Chyba příkazu:% 1|WFInstanceStore|  
|[4206 – UnlockInstanceException](4206-unlockinstanceexception.md)|Chyba|Při pokusu o odemknutí instance byla zjištěna výjimka% 1.|WFInstanceStore|  
|[4207 – MaximumRetriesExceededForSqlCommand](4207-maximumretriesexceededforsqlcommand.md)|Informace o|Při opakovaném pokusu o provedení příkazu SQL, který byl proveden jako maximální počet opakovaných pokusů.|WFInstanceStore kvót|  
|[4208 – RetryingSqlCommandDueToSqlError](4208-retryingsqlcommandduetosqlerror.md)|Informace o|Probíhá pokus o opakování příkazu SQL z důvodu chyby SQL číslo% 1.|WFInstanceStore|  
|[4209 – TimeoutOpeningSqlConnection](4209-timeoutopeningsqlconnection.md)|Chyba|Vypršel časový limit při pokusu o otevření připojení SQL. Operace se nedokončila v přiděleném časovém limitu% 1. Čas přidělený této operaci byl pravděpodobně částí delšího časového limitu.|WFInstanceStore|  
|[4210 – SqlExceptionCaught](4210-sqlexceptioncaught.md)|Upozornění|Byla zachycena výjimka SQL s číslem% 1 a zprávou% 2.|WFInstanceStore|  
|[4211 – QueuingSqlRetry](4211-queuingsqlretry.md)|Upozornění|Opakovaný pokus o zařazení SQL do fronty s prodlevou% 1 ms.|WFInstanceStore|  
|[4212 – LockRetryTimeout](4212-lockretrytimeout.md)|Upozornění|Při pokusu o získání zámku instance vypršel časový limit.  Operace se nedokončila v přiděleném časovém limitu% 1. Čas přidělený této operaci byl pravděpodobně částí delšího časového limitu.|WFInstanceStore|  
|[4213 – RunnableInstancesDetectionError](4213-runnableinstancesdetectionerror.md)|Chyba|Kvůli následující výjimce se nepovedlo detekovat instance spustitelný.|WFInstanceStore|  
|[4214 – InstanceLocksRecoveryError](4214-instancelocksrecoveryerror.md)|Chyba|Obnova zámků instancí se nezdařila z důvodu následující výjimky.|WFInstanceStore|  
|[39456 – TrackingRecordDropped](39456-trackingrecorddropped.md)|Upozornění|Velikost záznamu sledování% 1 překročila maximální hodnotu povolenou relací ETW pro poskytovatele% 2.|WFTracking|  
|[39457 – TrackingRecordRaised](39457-trackingrecordraised.md)|Informace o|Záznam sledování% 1 byl povýšen na% 2.|WFRuntime|  
|[39458 – TrackingRecordTruncated](39458-trackingrecordtruncated.md)|Upozornění|Zkrácený záznam sledování% 1 byl zapsán do relace ETW s poskytovatelem% 2. Byly odebrány proměnné, poznámky a uživatelská data.|WFTracking|  
|[39459 – TrackingDataExtracted](39459-trackingdataextracted.md)|Podrobnosti|Sledovací data% 1 extrahovaná v aktivitě% 2|WFRuntime|  
|[39460 – TrackingValueNotSerializable](39460-trackingvaluenotserializable.md)|Upozornění|Extrahovaný argument nebo proměnnou% 1 nelze serializovat.|WFTracking|  
|[57398 – MaxInstancesExceeded](57398-maxinstancesexceeded.md)|Upozornění|Systém dosáhl limitu nastaveného pro omezení ' MaxConcurrentInstances '. Omezení pro toto omezení bylo nastaveno na% 1. Hodnotu omezení lze změnit úpravou atributu ' maxConcurrentInstances ' v elementu serviceThrottle nebo úpravou vlastnosti ' MaxConcurrentInstances ' u chování ServiceThrottlingBehavior.|WFServices|
