---
title: "Události analytického trasování – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
caps.latest.revision: "50"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b47456ecea86652e80bb60f155bffd6100e1fc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="analytic-trace-event-reference"></a>Události analytického trasování – přehled
Následující tabulka definuje úrovní událostí, identifikátory a zprávy přidružené [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytické trasování.  
  
## <a name="event-reference"></a>Odkaz na události  
  
|ID události|Úroveň události|Zpráva události|Klíčová slova|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Verbose|Fond přidělování %1 bajtů.|infrastruktury|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Verbose|BufferPool o velikosti %1, změnit kvóty %2.|infrastruktury|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Verbose|Vstupně-výstupní operace vláken scheduler zpětným voláním.|infrastruktury|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Verbose|Vstupně-výstupní operace vláken scheduler zpětným voláním.|infrastruktury|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Informace o|Dispečer vyvolat 'AfterReceiveReply' na ClientMessageInspector typu '%1'.|Řešení potíží s ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Informace o|Dispečer vyvolat 'BeforeSendRequest' na ClientMessageInspector typu '%1'.|Řešení potíží s ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Informace o|Dispečer vyvolat 'AfterCall' na ClientParameterInspector. Typ '%1'.|Řešení potíží s ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Informace o|Dispečer vyvolat 'BeforeCall' na ClientParameterInspector typu '%1'.|Řešení potíží s ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Informace o|OperationInvoker volá metodu '%1'.|EndToEndMonitoring, řešení potíží s ServiceModel|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Informace o|Dispečer vyvolat ZpracováníChyby typu "%1, s výjimkou typu"%3".  ErrorHandled == '%2'.|Řešení potíží s ServiceModel|  
|[207 – FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Informace o|Dispečer vyvolat FaultProvider typu "%1, s výjimkou typu '%2'.|Řešení potíží s ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Informace o|Dispečer vyvolat 'AfterReceiveReply' na MessageInspector typu '%1'.|Řešení potíží s ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Informace o|Dispečer vyvolat 'BeforeSendRequest' na MessageInspector typu '%1'.|Řešení potíží s ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Upozornění|Bylo dosaženo limitu omezení '%1' z '%2'.|HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Informace o|Dispečer vyvolat 'AfterCall' na ParameterInspector typu '%1'.|Řešení potíží s ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Informace o|Dispečer vyvolat 'BeforeCall' na ParameterInspector typu '%1'.|Řešení potíží s ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|Hostitel služby spuštění: '%1'.|HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[214 - metoda OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Informace o|OperationInvoker dokončit volání metody '%1'.  Doba trvání volání metoda byla ms '%2'.|HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Informace o|Přenos přijala zprávu z '%1'.|Řešení potíží s ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Informace o|Přenos neodeslal zprávu na '%1'.|Řešení potíží s ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Informace o|Klient je provádění operace '%1' definované v kontraktu '%2'. Zpráva bude odeslána na "%3".|Řešení potíží s ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Informace o|Klient dokončit, provádění operace '%1' definované v kontraktu '%2'. Zpráva byla odeslána na '%3'.|Řešení potíží s ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Chyba|Při zpracování zprávy došlo k neošetřené výjimce typu '%2'.  ToString – Úplná výjimka: %1.|HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Informace o|Dispečer poslali zprávu o přenos. ID korelace == '%1'.|EndToEndMonitoring, řešení potíží s ServiceModel|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Informace o|Dispečer přijala zprávu z přenosu. ID korelace == '%1'.|EndToEndMonitoring, řešení potíží s ServiceModel|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Upozornění|Metoda "%1, došlo k neošetřené výjimce při vyvolané OperationInvoker. Doba trvání volání metoda byla ms '%2'.|HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Upozornění|Metoda "%1" způsobila FaultException při vyvolané OperationInvoker. Doba trvání volání metoda byla ms '%2'.|HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Upozornění|Limit omezovače '%1' z '%2' je 70 %.|HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|nečinnosti služby %1 z %2 celkový aktivovat služby uzavřen.|Tomuto webovému hostiteli HealthMonitoring|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Chyba|Název: '%1', odkaz na: %2, datové části: %3.|UserEvents HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Upozornění|Název: '%1', odkaz na: %2, datové části: %3.|UserEvents HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Informace o|Název: '%1', odkaz na: %2, datové části: %3.|UserEvents HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel|  
|[401 – StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Informace o|Aktivita hranic.|Poradce při potížích|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Informace o|Aktivita hranic.|Poradce při potížích|  
|[403 – SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Informace o|Aktivita hranic.|Poradce při potížích|  
|[404 - ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Informace o|Aktivita hranic.|Poradce při potížích|  
|[451 - MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Informace o|%1|Řešení potíží s WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Upozornění|%1|Řešení potíží s WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|Vygenerované událost přenosu.|Řešení potíží, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 - CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Informace o|Začněte kompilace.|Tomuto webovému hostiteli|  
|[502 – CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Informace o|Ukončení kompilace.|Tomuto webovému hostiteli|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Informace o|Třídy ServiceHostFactory zahájit vytvoření.|Tomuto webovému hostiteli|  
|[504 – ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Informace o|Vytvoření třídy ServiceHostFactory end.|Tomuto webovému hostiteli|  
|[505 - CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Informace o|Začněte CreateServiceHost.|Tomuto webovému hostiteli|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Informace o|End CreateServiceHost.|Tomuto webovému hostiteli|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Informace o|HostedTransportConfigurationManager začít Inicializace konfigurace.|Tomuto webovému hostiteli|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Informace o|Inicializace konfigurace HostedTransportConfigurationManager end.|Tomuto webovému hostiteli|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Informace o|Inicializace konfigurace HostedTransportConfigurationManager end.|Hostitel služby|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Informace o|Otevřete ServiceHost dokončit.|Hostitel služby|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Informace o|Přijala žádost o s virtuální cestou (%2) z domény aplikace '%1'.|Tomuto webovému hostiteli|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Informace o|WebHostRequest zastaví.|Tomuto webovému hostiteli|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Verbose|Zpracování ServiceActivation Element relativní adresa: '%1' Normalized relativní adresa (%2).||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Verbose|Příchozí požadavek odpovídá ServiceActivation element s adresou '%1'.||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Verbose|Příchozí požadavek odpovídá služby WCF definované v směrování Asp.Net s adresou %1.|RoutingServices|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Verbose|Se přidá novou trasu Asp.Net '%1' serviceType '%2' a serviceHostFactoryType '%3'.|RoutingServices|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Verbose|Volá se IncrementBusyCount. Zdroj: %1|Tomuto webovému hostiteli|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Verbose|Volá se DecrementBusyCount. Zdroj: %1|Tomuto webovému hostiteli|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Verbose|ServiceChannelOpen spustit.|Tomuto webovému hostiteli|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Informace o|ServiceChannelOpen byla dokončena.|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Informace o|ServiceChannelCall spustit.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Informace o|Asynchronní volání ServiceChannel spuštěna.|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Verbose|Počáteční žádost o odeslání protokolu HTTP.|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Verbose|Zastaví odesílání HTTP žádosti.|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Verbose|Zprávu přijatou z přenos http.|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Informace o|Odeslání zprávy spustit.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Verbose|Počáteční ověřování pro odeslání zpráv.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Verbose|Spusťte autorizace pro odeslání zpráv.|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Informace o|Zpráva, odeslání byla dokončena.|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Informace o|Otevřete Start ServiceChannel.|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Informace o|ServiceChannel otevřete zastaví.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Informace o|Odeslání HTTP přenášené datovými proudy zpráva spuštěna.|HTTP|  
|[1400 - ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Chyba|1%|ServiceModel|  
|[1401 - intervalu](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Chyba|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Chyba|%1 klíč fondu připojení: %2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Informace o|%1 klíč fondu připojení: %2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Chyba|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Chyba|%1|ServiceModel|  
|[1407 - SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Chyba|%1|ServiceModel|  
|[1409 - InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Informace o|%1|ServiceModel|  
|[. 1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Chyba|%1|kvóta|  
|[. 1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Chyba|%1|kvóta|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Informace o|%1|kvóta|  
|[. 1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Informace o|%1|kvóta|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Chyba|%1|kvóta|  
|[. 1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Chyba|%1|kvóta|  
|[. 1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Verbose|Vyjednávání poměr mezipaměti stav ověřovacího modulu tokenu: %1 / %2|kvóta|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Verbose|Poměr relace zabezpečení: %1 / %2|kvóta|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Verbose|Čekající na vyřízení poměr připojení: %1 / %2|kvóta|  
|[. 1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Verbose|Poměr souběžných relací: %1 / %2|kvóta|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Verbose|Poměr souběžných relací: %1 / %2|kvóta|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Verbose|Odchozí připojení za poměr koncového bodu: %1 / %2|kvóta|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Verbose|Odchozí připojení za poměr koncového bodu: %1 / %2|kvóta|  
|[. 1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Verbose|Čekajících zpráv za poměr kanálu: %1 / %2|kvóta|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Verbose|Poměr souběžných instancí: %1 / %2|kvóta|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Informace o|Nula čekající na vyřízení přijímá vlevo|kvóta|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Upozornění|1%|kvóta|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Upozornění|Zobrazí počet opakování dostupný MSMQ zprávě s id '%1.|kvóta|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Chyba|Maximální počet opakování cykly překročena na MSMQ zprávě s id '%1.|kvóta|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Verbose|Vytvořit nové '%1.|kvóta|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Verbose|Vytvořit nové '%1.|kvóta|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Chyba|1%|kvóta|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Upozornění|Nepodařilo se dokončit %1.|Kanál|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Upozornění|Nepodařilo se Abandon %1.|Kanál|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Upozornění|Přijímat kontextu došlo k chybě.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Informace o|%1 byla zastavena s výjimkou %2.|Kanál|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Informace o|Počet továren uložené v mezipaměti kanál je: '%1'.  Maximálně továrny kanálu: %2' můžete uložit do mezipaměti.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Informace o|Postup kanálu má byla stará z mezipaměti, protože mezipaměti dosáhl svého limitu '%1'.|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Informace o|Použít odpovídající kanálu nalezených v mezipaměti.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Informace o|Nepoužíváte kanálu z mezipaměti, tj. zakáže ukládání do mezipaměti pro instanci.|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Informace o|Byl proveden sestavení dotazu pomocí '%1' na identifikátor Uri požadavku: '%2'.|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Chyba|Operaci '%1' byl odeslán s chybami.|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Informace o|Operaci '%1' byl úspěšně odeslán.|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informace o|Za zprávou s vlastností '%1' velikost v bajtech byl načten pomocí kodéru.|Kanál|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informace o|Kodér napsal za zprávou s vlastností '%1' velikost v bajtech.|Kanál|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Chyba|Relace přerušení nečinnosti kanál uri: '%1'.|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Verbose|Připojení přijmout spuštěna.|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Verbose|ListenerId:% 1 přijata SocketId:% 2.|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Verbose|Fond pro %1 nemá žádné dostupné připojení a připojení %2 zaneprázdněný.|Kanál|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Verbose|Dispečer spuštění deserializace zprávu požadavku.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Verbose|Dispečer dokončit deserializace zprávu požadavku.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Verbose|Spuštění dispečera serializace odpovědi.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Verbose|Dispečer dokončit serializace odpovědi.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Verbose|Serializace požadavek klienta spustit.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Verbose|Klienta dokončit serializace zprávu požadavku.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Verbose|Klient je spuštěn deserializaci zpráva s odpovědí.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Verbose|Klienta dokončit deserializaci zpráva s odpovědí.|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Verbose|Vyjednávání zabezpečení spustit.|Zabezpečení|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Verbose|Vyjednávání zabezpečení byla dokončena.|Zabezpečení|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Verbose|Otevírání SecurityTokenProvider byla dokončena.|Zabezpečení|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Verbose|Odchozí zprávy byla zabezpečená.|Zabezpečení|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Verbose|Příchozí zpráva byla ověřena.|Zabezpečení ServiceModel|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Verbose|Načtení instance služba spuštěna.|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Verbose|Instance služby načíst.|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Verbose|ChannelHandlerId:% 1 – zpráva zobrazí smyčky spuštěna.|Kanál|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Verbose|ChannelHandlerId:% 1 – zpráva zobrazí smyčky byla zastavena.|Kanál|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Verbose|ChannelFactory vytvořili.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Verbose|Připojení kanálu přijmout spuštěn na %1.|Kanál|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Verbose|Přijaté připojení kanálu.|Kanál|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Verbose|Navázání připojení spustit pro %1.|Kanál|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Verbose|Připojení bylo vytvořeno.|Kanál|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Verbose|Porozumění preambule relace pro '%1'.|Kanál|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Chyba|Čtečka připojení odesílání selhání '%1'.|Kanál|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Verbose|Přijetí uzavřené soketu.|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Kritická|Hostitel služby došlo k chybě.|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Verbose|Naslouchací proces otevření pro '%1'.|Kanál|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Verbose|Otevřete naslouchací proces dokončit.|Kanál|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Verbose|Bylo dosaženo maximálního počtu připojení ve fondu kvóty serveru.|kvóta|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Chyba|SocketId:% 1 vzdálenou adresou %2 vypršel časový limit.|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Upozornění|SocketId:% 1 vzdálenou adresou %2 měla resetovat chyby připojení.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Verbose|Vyjednávání zabezpečení služby byla dokončena.|Zabezpečení|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Chyba|Zpracování vyjednávání zabezpečení se nezdařilo.|Zabezpečení|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Verbose|Zabezpečení ověření bylo úspěšné.|Zabezpečení|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Chyba|Zabezpečení ověření se nezdařilo.|Zabezpečení|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Verbose|Časový limit soketu duplikován pro %1.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Verbose|Zosobnění zabezpečení byla úspěšná.|Zabezpečení|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Upozornění|Zosobnění zabezpečení se nezdařilo.|Zabezpečení|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Upozornění|Kanál požadavek HTTP byl zrušen.|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Upozornění|Odpověď HTTP kanál přerušena.|HTTP|  
|[. 3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Upozornění|Ověřování pomocí protokolu HTTP se nezdařilo.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Verbose|Registrace SharedListenerProxy spustit pro identifikátor uri '%1'.|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Verbose|Zastaví SharedListenerProxy registrace.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Chyba|Registrace SharedListenerProxy se nezdařila se stavem '%1'.|ActivationServices|  
|[. 3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Chyba|ConnectionPoolPreambleFailed.|Kanál|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Verbose|SslOnAcceptUpgradeStart|Zabezpečení|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Verbose|SslOnAcceptUpgradeStop|Zabezpečení|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Verbose|BinaryMessageEncoder spustit kódování zprávy.|Kanál|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Verbose|MtomMessageEncoder spustit kódování zprávy.|Kanál|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Verbose|TextMessageEncoder spustit kódování zprávy.|Kanál|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Verbose|BinaryMessageEncoder spustit dekódování zprávy.|Kanál|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Verbose|MtomMessageEncoder spustit dekódování zprávy.|Kanál|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Verbose|TextMessageEncoder spustit dekódování zprávy.|Kanál|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Informace o|Přenos HTTP spustit přijímání zprávy.|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Verbose|Počet bajtů ke čtení: %2' SocketId:% 1 číst z '%3'.|TCP|  
|[. 3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Verbose|Počet bajtů ke čtení: %2' SocketId:% 1 číst z '%3'.|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Verbose|SocketId:% 1 bajtů zápis "%2" na "%3.|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Verbose|SocketId:% 1 bajtů zápis "%2" na "%3.|TCP|  
|[. 3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Verbose|Potvrzení SessionId:% 1 odeslána.|Kanál|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Informace o|Opětovné připojení SessionId:% 1.|Kanál|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Informace o|SessionId:% 1, došlo k chybě.|Kanál|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Verbose|WindowsStreamSecurity inicializace aktualizace zabezpečení.|Zabezpečení|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Verbose|Streamování zabezpečení na přijímání upgradu systému Windows.|Zabezpečení|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Upozornění|SocketId:% 1 bude předčasně ukončen.|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Verbose|HttpGetContext start.|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Verbose|Klient odesílá počáteční preambule.|Kanál|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Verbose|Klient odesílání preambule zastaví.|Kanál|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Upozornění|Přijímat zprávy HTTP se nezdařilo.|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Informace o|Vytváří se TransactionScope s LocalIdentifier: '%1' a DistributedIdentifier: '%2'.|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Informace o|Přenášené datovými proudy zpráv byl načten pomocí kodéru.|Kanál|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Informace o|Kodér napsal přenášené datovými proudy zpráv.|Kanál|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Informace o|Zpráva byla zapsána asynchronně pomocí kodéru.|Kanál|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Informace o|Zápis BufferId:% 1 dokončena: %2' počet bajtů do základního datového proudu.|Kanál|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Informace o|Zpráva byla zapsána asynchronně pomocí kodéru.|Kanál|  
|[. 3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Verbose|Přesměrováním sdílené paměti vytvořený v '%1'.|Kanál|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Verbose|Pojmenovaný kanál '%1"vytvořil.|Kanál|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Verbose|Ověření podpisu spustit.|Zabezpečení|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Verbose|Ověření podpisu bylo úspěšné.|Zabezpečení|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Verbose|Zabalená klíče dešifrování spuštěna.|Zabezpečení|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Verbose|Zabalená dešifrovací klíče bylo úspěšné.|Zabezpečení|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Verbose|Šifrované zpracování dat spuštěna.|Zabezpečení|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Verbose|Šifrované zpracování dat bylo úspěšně dokončeno.|Zabezpečení|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Verbose|Obslužné rutiny zpráv HTTP zahájeno zpracování příchozí žádosti.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Verbose|Obslužné rutiny zpráv HTTP spustit asynchronně zpracování příchozí žádosti.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Verbose|Obslužné rutiny zpráv HTTP dokončit zpracování příchozí žádosti.|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Upozornění|Obslužné rutiny zpráv HTTP došlo k chybě.|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Chyba|Vypršel časový limit připojení protokolu WebSocket.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Verbose|Obslužné rutiny zpráv HTTP zahájeno zpracování odpovědi.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Verbose|Obslužné rutiny zpráv HTTP spuštění zpracování odpovědi asynchronně.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Verbose|Obslužné rutiny zpráv HTTP dokončit zpracování odpovědi.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Verbose|Požadavek na připojení protokolu WebSocket na '%1' odeslat start.|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Verbose|WebSocketId:% 1 požadavek na připojení.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Verbose|Připojení protokolu WebSocket přijmout start.|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Verbose|Přijaté WebSocketId:% 1 připojení.|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Chyba|Připojení protokolu WebSocket odmítl se stavovým kódem '%1.|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Chyba|Požadavek na připojení protokolu WebSocket se nezdařilo: '%1.|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Chyba|WebSocketId:% 1 připojení byl přerušen.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Verbose|WebSocketId:% 1 bajtů zápis "%2" na "%3.|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Verbose|Zastaví asynchronní zápis WebSocketId:% 1.|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Verbose|Spuštění WebSocketId:% 1 pro čtení.|HTTP|  
|[. 3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Verbose|Počet bajtů: %2' WebSocketId:% 1, přečtěte si z '%3'.|HTTP|  
|[. 3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Verbose|Odesílání WebSocketId:% 1 zavřete zprávu do %2 stavem zavřít '%3'.|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Verbose|Odesílání WebSocketId:% 1 zavřete zprávu výstupu: %2' stavem zavřít '%3'.|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Verbose|WebSocketId:% 1 připojení ukončeno.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Verbose|WebSocketId:% 1 připojení zavřít byla přijata zpráva se stavem '%2'.|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Verbose|Pomocí WebSocketVersion z objekt klienta protokolu WebSocket typu '%1'.|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Verbose|Vytvoření klienta protokolu WebSocket pomocí objekt typu '%1'.|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Informace o|XamlServicesLoad start|Tomuto webovému hostiteli|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Informace o|Zastavení xamlServicesLoad|Tomuto webovému hostiteli|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Informace o|CreateWorkflowServiceHost start|Tomuto webovému hostiteli|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Informace o|Zastavení CreateWorkflowServiceHost|Tomuto webovému hostiteli|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Informace o|Spouštění služby Aktivace|Tomuto webovému hostiteli|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Informace o|Služba Aktivace Stop|Tomuto webovému hostiteli|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Verbose|Dostupná paměť (bajty): %1|kvóta|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Informace o|Směrovací služby ukončuje klienta '%1'.|RoutingServices|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Upozornění|Směrování klienta služby '%1' došlo k chybě.|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Informace o|Jedním ze způsobů zprávu směrovací služby je dokončení.|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Chyba|Služba směrování nemůže při zpracování zprávy v koncovém bodě s adresou '%1'.|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Informace o|Směrovací služby je vytvoření klienta pro koncový bod: '%1'.|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Verbose|Služba Směrování je nakonfigurována s RouteOnHeadersOnly: %1, SoapProcessingEnabled: %2, EnsureOrderedDispatch: %3.|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Informace o|Zpráva s odpovědí požadavku směrování služby je dokončení.|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Verbose|Služba směrování směrovat zprávy s ID: '%1' na seznamy %2 koncový bod.|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Informace o|Nové RoutingConfiguration byla použita ve službě Směrování.|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Informace o|Služba směrování zpracovává zprávy s ID: %1, akce: %2, příchozí adresy URL: '%3' přijaté v transakci: %4.|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Informace o|Směrovací služby je odesláním zprávy s ID: '%1' [operaci %2], k '%3'.|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Informace o|Směrovací služby je potvrzování transakce s id: '%1'.|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Chyba|Směrování součást služby %1 došlo k výjimce duplexní zpětného volání.|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Informace o|Směrování zprávy služby s ID: '%1' [operaci %2] přesunout do zálohování koncový bod '%3'.|RoutingServices|  
|[. 3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Informace o|Směrovací služby vytvořit novou transakci s id '%1' pro zpracování zprávy.|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Upozornění|Směrovací služby se nezdařilo při zavírání odchozí klienta '%1'.|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Informace o|Směrovací služby odesílá zpět zprávu odpovědi pomocí akce '%1'.|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Upozornění|Směrovací služby odesílá zpět zprávu odpovědi o chybě pomocí akce '%1'.|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Verbose|Směrovací služby je volání ReceiveContext.Complete u zprávy s ID: '%1'.|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Upozornění|Směrovací služby je volání ReceiveContext.Abandon u zprávy s ID: '%1'.|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Verbose|Směrovací služby bude odesílat zprávy pomocí stávající transakce '%1'.|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Upozornění|Směrovací služby se nezdařila při odesílání do '%1'.|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Informace o|Směrovací služba MessageFilterTable shodu spustit.|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Informace o|Směrování zastavením služby MessageFilterTable shodu.|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Verbose|Směrovací služby je volání přerušení na kanálu: '%1'.|RoutingServices|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Verbose|Směrovací služby byla zpracována výjimka.|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Informace o|Směrovací služby úspěšně přenesených zprávě s ID: "na"%3. %1 [operaci %2].|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Verbose|Relace naslouchací proces přenosu obdrželi s portálem prostřednictvím '%1.|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Kritická|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Chyba|Došlo k chybě kanálu spuštění služby.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Verbose|Spuštění relace odesílání.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Upozornění|Odesílání relace pro '%1' se nezdařilo, protože čekající na vyřízení relace fronta je plná s '%2' čekající položky.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Verbose|Fronta zpráv zaregistrovat start.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Chyba|Zprávy fronty registrace přerušena se stavem: '%1' pro identifikátor uri: '%2'.|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Verbose|Fronta zpráv zrušit registraci úspěšně pro identifikátor uri: '%1'.|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Chyba|Zprávy fronty registrace pro identifikátor uri: '%1' se nezdařil se stavem: '%2'.|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Informace o|Registrace fronty zpráv byla dokončena pro identifikátor uri '%1'.|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Chyba|Fronta zpráv se nezdařilo duplicitní soketu.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Verbose|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Verbose|Naslouchací proces TCP přenosu spouštění tak, aby naslouchala na uri: '%1'.|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Verbose|Naslouchací proces přenosu TCP naslouchá.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Chyba|Kód chyby: % 1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Informace o|Všechny instance naslouchací proces kanálu dokončit se zavírá.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Chyba|Kód chyby: % 1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Chyba|Kód chyby: % 1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Verbose|BYL připojen.|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Verbose|BYLO přerušeno.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Verbose|Naslouchací proces přenosu kanál naslouchání start na uri:% 1.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Verbose|Kanál přenosu naslouchací proces naslouchání zastaví.|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Informace o|Odesílání relace byla úspěšná.|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Chyba|Relace odeslání se nezdařilo.|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Kritická|Připojení vypršel.|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Verbose|Vyhledávací tabulky směrování spustit.|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Verbose|Směrování vyhledávací tabulka byla dokončena.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Verbose|Čekající na vyřízení poměr fronty relace: %1 / %2|kvóta|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Upozornění|Zprávu nelze se přihlásit, protože přesahuje velikost události trasování událostí pro Windows|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Upozornění|Objekty DiscoveryClient vytvářet v DiscoveryClientChannel Nepodařilo se zavřít a proto byla přerušena.|Zjišťování|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Informace o|Při zavírání objekty DiscoveryClient byl potlačen protocolexception –. To může být způsobeno DiscoveryService je stále pokusu o odeslání odpovědi na objekty DiscoveryClient.|Zjišťování|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Informace o|Objekty DiscoveryClient přijal zprávu vícesměrového vysílání potlačení z DiscoveryProxy.|Zjišťování|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Informace o|Zprávu %1 s messageId = '%2' byla vyřazena pomocí objekty DiscoveryClient, protože odpovídající %3 operace byla dokončena.|Zjišťování|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Upozornění|Zprávu %1 s messageId = '%2' byla vynechána, protože mělo neplatný obsah.|Zjišťování|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Upozornění|Zprávu %1 s messageId = '%2' a související s = '%3' byla vynechána pomocí objekty DiscoveryClient, protože odpovídající %4 operace byla dokončena nebo související s hodnota je neplatná.|Zjišťování|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Upozornění|Zprávu požadavku zjišťování s messageId = '%1' byla vynechána, protože mělo neplatnou adresu ReplyTo.|Zjišťování|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Upozornění|Zprávu %1 byla vyřazena, protože nemá žádný obsah.|Zjišťování|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Upozornění|Zprávu %1 byla vyřazena, protože záhlaví zprávy neobsahuje požadovanou vlastnost MessageId.|Zjišťování|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Upozornění|Zprávu %1 s messageId = '%2' byla vynechána pomocí objekty DiscoveryClient, protože nemá vlastnost DiscoveryMessageSequence.|Zjišťování|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Upozornění|Zprávu %1 s messageId = '%2' byla vyřazena pomocí objekty DiscoveryClient, protože záhlaví zprávy neobsahuje požadovanou vlastnost související s.|Zjišťování|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Upozornění|Zprávu požadavku zjišťování s messageId = '%1' byla vyřazena, protože neobsahovala adresu ReplyTo.|Zjišťování|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Upozornění|Zprávu %1 s messageId = '%2' byla vynechána, protože je duplicitní.|Zjišťování|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informace o|Zjistitelnost koncový bod s EndpointAddress = '%1' a adrese ListenUri = "%2" byla zakázána.|Zjišťování|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informace o|Zjistitelnost koncový bod s EndpointAddress = '%1' a adrese ListenUri = '%2' bylo povoleno.|Zjišťování|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Verbose|Operace hledání byl zahájen v DiscoveryClientChannel ke zjištění koncové.|Zjišťování|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Upozornění|DiscoveryClientChannel Nepodařilo se vytvořit kanál s zjištěných koncový bod s EndpointAddress = '%1' a prostřednictvím = '%2'. DiscoveryClientChannel se nyní pokusí použít další dostupné zjištěných koncový bod.|Zjišťování|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Upozornění|DiscoveryClientChannel se nepodařilo otevřít kanál s zjištěných koncový bod s EndpointAddress = '%1' a prostřednictvím = '%2'. DiscoveryClientChannel se nyní pokusí použít další dostupné zjištěných koncový bod.|Zjišťování|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Informace o|DiscoveryClientChannel úspěšně zjistit koncový bod a otevřít kanál používat. Je klient připojen k službě pomocí EndpointAddress = '%1' a prostřednictvím = '%2'.|Zjišťování|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Informace o|SynchronizationContext byl resetován na původní hodnotu %1 DiscoveryClientChannel.|Zjišťování|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Informace o|SynchronizationContext byla nastavena na hodnotu null ve DiscoveryClientChannel před zahájením operace hledání.|Zjišťování|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Verbose|Kontraktu serializovat %1 s náhrady start.|Serializace|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Verbose|Kontraktu serializovat s náhrady zastavit.|Serializace|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Verbose|Kontraktu deserializovat %1 s náhrady start.|Serializace|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Verbose|Kontraktu deserializovat s náhrady zastavit.|Serializace|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Verbose|ImportKnownTypes spustit.|Serializace|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Verbose|ImportKnownTypes zastavit.|Serializace|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Verbose|Řešitel kontraktu řešení %1 start.|Serializace|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Verbose|Kontraktu generovat zapisovač %1 pro %2 start.|Serializace|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Verbose|Kontraktu generovat zastavení zapisovače.|Serializace|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Verbose|Kontraktu generovat čtečka %1 pro %2 start.|Serializace|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Verbose|Zastaví generování kontraktu.|Serializace|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Verbose|JSON generovat čtečka %1 pro %2 start.|Serializace|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Verbose|Zastaví generaci čtečky JSON.|Serializace|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Verbose|JSON generovat zapisovač %1 pro %2 start.|Serializace|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Verbose|JSON generovat zastavení zapisovače.|Serializace|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Verbose|Generovat Xml serializovatelný pro začátek '%1'.|Serializace|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Verbose|Generovat serializovatelný zastavení Xml.|Serializace|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Verbose|JsonMessageEncoder spustit dekódování zprávy.|Kanál|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Verbose|JsonMessageEncoder spustit kódování zprávy.|Kanál|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Verbose|Spuštění ověření SecurityToken (typ '%1' a id: %2.).|Zabezpečení|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Verbose|SecurityToken (typ '%1' a id: %2.) ověření bylo úspěšné.|Zabezpečení|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Chyba|Ověření SecurityToken (typ '%1' a id: %2.) se nezdařilo. %3|Zabezpečení|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Verbose|Načtení vystavitele. název: % 1 z tokenId:% 2 bylo úspěšné.|Zabezpečení|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Chyba|Název vystavitele z tokenId:% 1 načtení se nezdařilo.|Zabezpečení|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Verbose|Zpracování zpráv federační spustit.|Zabezpečení|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Verbose|Zpracování zpráv federační bylo úspěšné.|Zabezpečení|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Verbose|Vytváření federační zprávy z post formuláře spustit.|Zabezpečení|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Verbose|Vytváření federační zprávy z post formuláře bylo úspěšné.|Zabezpečení|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Verbose|Čtení ze souboru cookie relace token relace spuštění.|Zabezpečení|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Verbose|Token zabezpečení relace čtení ze souboru cookie relace byla úspěšná.|Zabezpečení|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Verbose|Hlavní nastavení z tokenu relace spuštění.|Zabezpečení|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Verbose|Hlavní nastavení z tokenu relace byla úspěšná.|Zabezpečení|  
|[57393 - appDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Informace o|Uvolnění domény aplikace. AppDomain.FriendlyName %1, název_procesu %2, ID procesu %3.|infrastruktury|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Informace o|Zpracování výjimky.|infrastruktury|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Chyba|Došlo k neočekávané chybě. Aplikace se neměli pokoušet o zpracování této chyby. K diagnostickým účelům tuto anglickou zprávu souvisí s chybou: %1.|infrastruktury|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Upozornění|Došlo k výjimce. Zdroj %1.|infrastruktury|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Kritická|Neošetřená výjimka.|infrastruktury|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Kritická|Zapsáno do protokolu událostí.|infrastruktury|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Chyba|Zapsáno do protokolu událostí.|infrastruktury|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Informace o|Zapsáno do protokolu událostí.|infrastruktury|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Verbose|Zapsáno do protokolu událostí.|infrastruktury|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Upozornění|Zapsáno do protokolu událostí.|infrastruktury|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Upozornění|Zpracování výjimky.|infrastruktury|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Informace o|Dokument XAML hostitele adresy url '%1' s kořenový element typ '%2'. Typ obslužné rutiny HTTP: %3' vydán poskytovat všechny požadavky, které jsou vytvořené na tuto adresu url.|Tomuto webovému hostiteli|
