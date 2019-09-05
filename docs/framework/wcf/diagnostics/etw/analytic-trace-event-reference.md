---
title: Události analytického trasování – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: ae792a0b55b0559b13c2394bd27d85f224d1aea0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243977"
---
# <a name="analytic-trace-event-reference"></a>Události analytického trasování – přehled
Následující tabulka definuje úrovně událostí, identifikátory a zprávy přidružené k analytickému trasování služby WCF.  
  
## <a name="event-reference"></a>Odkaz na událost  
  
|ID události|Úroveň události|Zpráva události|klíčová slova|  
|--------------|-----------------|-------------------|--------------|  
|[131 – BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Podrobnosti|Fond přiděluje% 1 bajtů.|Infrastruktura|  
|[132 – BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Podrobnosti|Fondu velikosti% 1, mění se kvóta o% 2.|Infrastruktura|  
|[133 – ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Podrobnosti|Bylo vyvoláno zpětné volání plánovače v/v.|Infrastruktura|  
|[134 – ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Podrobnosti|Bylo vyvoláno zpětné volání plánovače v/v.|Infrastruktura|  
|[201 – ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Informace o|Dispečer vyvolal ' AfterReceiveReply ' na třídy ClientMessageInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[202 – ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Informace o|Dispečer vyvolal ' BeforeSendRequest ' na třídy ClientMessageInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[203 – ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Informace o|Dispečer vyvolal ' AfterCall ' na třídy ClientParameterInspector. typu '% 1 '.|Řešení potíží, ServiceModel|  
|[204 – ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Informace o|Dispečer vyvolal ' BeforeCall ' na třídy ClientParameterInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[205 – OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Informace o|Metody OperationInvoker vyvolal metodu% 1.|EndToEndMonitoring, řešení potíží, ServiceModel|  
|[206 – ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Informace o|Dispečer vyvolal rutinu ErrorHandler typu% 1 s výjimkou typu% 3.  ErrorHandled = = '% 2 '.|Řešení potíží, ServiceModel|  
|[207 – FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Informace o|Dispečer vyvolal FaultProvider typu% 1 s výjimkou typu% 2.|Řešení potíží, ServiceModel|  
|[208 – MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Informace o|Dispečer vyvolal ' AfterReceiveReply ' na třídy MessageInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[209 – MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Informace o|Dispečer vyvolal ' BeforeSendRequest ' na třídy MessageInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[210 – MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Upozornění|Bylo dosaženo omezení% 1 pro% 2.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[211 – ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Informace o|Dispečer vyvolal ' AfterCall ' na třídy ParameterInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[212 – ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Informace o|Dispečer vyvolal ' BeforeCall ' na třídy ParameterInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[213 – ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|Třída ServiceHost byla spuštěna:% 1.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[214 – OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Informace o|Metody OperationInvoker dokončil volání metody% 1.  Doba volání metody byla% 2 MS.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[215 – MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Informace o|Přenos přijal zprávu od '% 1 '.|Řešení potíží, ServiceModel|  
|[216 – MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Informace o|Přenos odeslal zprávu na% 1.|Řešení potíží, ServiceModel|  
|[217 – ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Informace o|Klient provádí operaci% 1 definovanou ve kontraktu% 2. Zpráva bude odeslána na '% 3 '.|Řešení potíží, ServiceModel|  
|[218 – ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Informace o|Klient dokončil provádění operace% 1 definované ve kontraktu% 2. Zpráva byla odeslána na '% 3 '.|Řešení potíží, ServiceModel|  
|[219 – ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Chyba|Během zpracování zprávy došlo k neošetřené výjimce typu% 2.  Úplná výjimka ToString:% 1.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[220 – MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Informace o|Dispečer odeslal zprávu přenosu. ID korelace =% 1.|EndToEndMonitoring, řešení potíží, ServiceModel|  
|[221 – MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Informace o|Dispečer obdržel zprávu od přenosu. ID korelace =% 1.|EndToEndMonitoring, řešení potíží, ServiceModel|  
|[222 – OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Upozornění|Metoda '% 1 ' vyvolala neošetřenou výjimku při vyvolání rozhraním metody OperationInvoker. Doba volání metody byla% 2 MS.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[223 – OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Upozornění|Metoda '% 1 ' vyvolala FaultException při vyvolání rozhraním metody OperationInvoker. Doba volání metody byla% 2 MS.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[224 – MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Upozornění|Omezení% 1 pro% 2 je na 70%.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[226 – IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|% 1 nečinných služeb z celkového počtu% 2 aktivované služby byly uzavřeny.|HealthMonitoring webhost|  
|[301 – UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Chyba|Název: '% 1 ', odkaz: '% 2 ', datová část:% 3.|UserEvents, healthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[302 – UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Upozornění|Název: '% 1 ', odkaz: '% 2 ', datová část:% 3.|UserEvents, healthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[303 – UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Informace o|Název: '% 1 ', odkaz: '% 2 ', datová část:% 3.|UserEvents, healthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[401– StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Informace o|Hranice aktivity.|Poradce při potížích|  
|[402 – StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Informace o|Hranice aktivity.|Poradce při potížích|  
|[403 – SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Informace o|Hranice aktivity.|Poradce při potížích|  
|[404 – ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Informace o|Hranice aktivity.|Poradce při potížích|  
|[451 – MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Informace o|%1|Řešení potíží, WCFMessageLogging|  
|[452 – MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Upozornění|%1|Řešení potíží, WCFMessageLogging|  
|[499 – TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|Byla vyvolána událost přenosu.|Řešení potíží, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 – CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Informace o|Zahajte kompilaci.|WebHost|  
|[502 – CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Informace o|Ukončit kompilaci|WebHost|  
|[503 – ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Informace o|ServiceHostFactory začít vytvářet.|WebHost|  
|[504 – ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Informace o|Vytvoření konce ServiceHostFactory|WebHost|  
|[505 – CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Informace o|Spusťte metody CreateServiceHost.|WebHost|  
|[506 – CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Informace o|Konec metody CreateServiceHost|WebHost|  
|[507 – HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Informace o|Správce hostedtransportconfigurationmanager ukončil zahájit inicializaci konfigurace.|WebHost|  
|[508 – HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Informace o|Inicializace konfigurace ukončení správce hostedtransportconfigurationmanager ukončil|WebHost|  
|[509 – ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Informace o|Inicializace konfigurace ukončení správce hostedtransportconfigurationmanager ukončil|ServiceHost|  
|[510 – ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Informace o|Otevření hostitele ServiceHost bylo dokončeno.|ServiceHost|  
|[513 – WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Informace o|Byl přijat požadavek s virtuální cestou% 2 z domény aplikace% 1.|WebHost|  
|[514 – WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Informace o|Zastavení ukončení požadavku webhostrequest|WebHost|  
|[601 – CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Podrobnosti|Relativní adresa prvku ServiceActivation: '% 1 ', normalizovaná relativní adresa '% 2 '.||  
|[602 – CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Podrobnosti|Příchozí požadavek odpovídá elementu ServiceActivation s adresou% 1.||  
|[603 – AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Podrobnosti|Příchozí požadavek odpovídá službě WCF definované v trase Asp.Net s adresou% 1.|RoutingServices|  
|[604 – AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Podrobnosti|Byla přidána nová trasa Asp.Net '% 1 ' s serviceType '% 2 ' a typem servicehostfactorytype '% 3 '.|RoutingServices|  
|[605 – IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Podrobnosti|Metoda IncrementBusyCount volána. Zdroj:% 1|WebHost|  
|[606 – DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Podrobnosti|Metoda DecrementBusyCount volána. Zdroj:% 1|WebHost|  
|[701 – ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Podrobnosti|Operace servicechannelopen se spustil.|WebHost|  
|[702 – ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Informace o|Operace servicechannelopen se dokončilo.|ServiceModel|  
|[703 – ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Informace o|Spuštění servicechannelcall se spustil.|ServiceModel|  
|[704 – ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Informace o|Bylo zahájeno asynchronní volání kanálu ServiceChannel.|ServiceModel|  
|[706 – HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Podrobnosti|Byl zahájen požadavek Send protokolu HTTP.|HTTP|  
|[707 – HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Podrobnosti|Byl ukončen požadavek Send protokolu HTTP.|HTTP|  
|[708 – HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Podrobnosti|Z přenosu HTTP byla přijata zpráva.|HTTP|  
|[709 – DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Informace o|Bylo zahájeno odesílání zpráv.|ServiceModel|  
|[710 – HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Podrobnosti|Spusťte ověřování pro odeslání zprávy.|ServiceModel|  
|[711 – DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Podrobnosti|Spusťte autorizaci pro odeslání zprávy.|ServiceModel|  
|[712 – DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Informace o|Odeslání zprávy bylo dokončeno.|ServiceModel|  
|[715 – ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Informace o|Kanálu ServiceChannel otevřít Start.|ServiceModel|  
|[716 – ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Informace o|Kanálu ServiceChannel otevřené zastavení.|ServiceModel|  
|[717 – HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Informace o|Začalo streamovaná zpráva odeslání protokolu HTTP.|HTTP|  
|[1400 – ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Chyba|1%|ServiceModel|  
|[1401 – CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Chyba|1%|ServiceModel|  
|[1402 – IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Chyba|% 1 klíč fondu připojení:% 2|ServiceModel|  
|[1403 – LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Informace o|% 1 klíč fondu připojení:% 2|ServiceModel|  
|[1405 – OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Chyba|%1|ServiceModel|  
|[1406 – ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Chyba|%1|ServiceModel|  
|[1407 – SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Chyba|%1|ServiceModel|  
|[1409 – InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Informace o|%1|ServiceModel|  
|[1416 – MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Chyba|%1|Přidělení|  
|[1417 – MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Chyba|%1|Přidělení|  
|[1418 – MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Informace o|%1|Přidělení|  
|[1419 – MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Informace o|%1|Přidělení|  
|[1420 – ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Chyba|%1|Přidělení|  
|[1422 – NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Chyba|%1|Přidělení|  
|[1423 – NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Podrobnosti|Vyjednat poměr mezipaměti stavu ověřovacích dat tokenu:% 1/% 2|Přidělení|  
|[1424 – SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Podrobnosti|Poměr relace zabezpečení:% 1/% 2|Přidělení|  
|[1430 – PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Podrobnosti|Poměr nedokončených připojení:% 1/% 2|Přidělení|  
|[1431 – ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Podrobnosti|Poměr souběžných relací:% 1/% 2|Přidělení|  
|[1432 – ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Podrobnosti|Poměr souběžných relací:% 1/% 2|Přidělení|  
|[1433 – OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Podrobnosti|Poměr odchozích připojení na koncový bod:% 1/% 2|Přidělení|  
|[1436 – PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Podrobnosti|Poměr nedokončených zpráv na kanál:% 1/% 2|Přidělení|  
|[1438 – ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Podrobnosti|Poměr souběžných instancí:% 1/% 2|Přidělení|  
|[1439 – PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Informace o|Zbývá nula přijetí|Přidělení|  
|[1441 – MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Upozornění|1%|Přidělení|  
|[1442 – ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Upozornění|Byl dosažen počet opakování přijetí u zprávy služby MSMQ s ID% 1.|Přidělení|  
|[1443 – MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Chyba|Byl překročen maximální počet cyklů opakování u zprávy služby MSMQ s ID% 1.|Přidělení|  
|[1445 – ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Podrobnosti|Byl vytvořen nový% 1.|Přidělení|  
|[1446 – WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Podrobnosti|Byl vytvořen nový% 1.|Přidělení|  
|[1451 – MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Chyba|1%|Přidělení|  
|[3300 – ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Upozornění|Dokončení% 1 se nezdařilo.|Kanál|  
|[3301 – ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Upozornění|Nepovedlo se opustit% 1.|Kanál|  
|[3303 – ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Upozornění|V kontextu Receive došlo k chybě.|ServiceModel|  
|[3303 – ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Informace o|% 1 byla opuštěna s výjimkou% 2.|Kanál|  
|[3305 – ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Informace o|Počet továrn kanálu v mezipaměti je% 1.  Do mezipaměti lze uložit maximálně% 2 továrny kanálů.|ServiceModel|  
|[3306 – ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Informace o|Objekt pro vytváření kanálů byl vyřazen z mezipaměti, protože mezipaměť dosáhla svého limitu% 1.|ServiceModel|  
|[3307 – ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Informace o|V mezipaměti byl nalezen stejný objekt pro vytváření kanálů.|ServiceModel|  
|[3308 – ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Informace o|Nepoužívá se objekt pro vytváření kanálů z mezipaměti, tj. ukládání do mezipaměti je pro instanci zakázané.|ServiceModel|  
|[3309 – QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Informace o|Bylo provedeno složení dotazu s použitím% 1 pro identifikátor URI požadavku:% 2.|ServiceModel|  
|[3310 – DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Chyba|Operace% 1 byla odeslána s chybami.|ServiceModel|  
|[3311 – DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Informace o|Operace% 1 byla úspěšně odeslána.|ServiceModel|  
|[3312 – MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informace o|Kodér přečetl zprávu o velikosti% 1 bajtů.|Kanál|  
|[3312 – MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informace o|Kodér zapsal zprávu o velikosti% 1 bajtů.|Kanál|  
|[3314 – SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Chyba|Přerušení relace pro nečinný kanál na identifikátor URI:% 1.|ServiceModel|  
|[3319 – SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Podrobnosti|Bylo zahájeno přijetí připojení.|TCP|  
|[3320 – SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Podrobnosti|Naslouchací proces listenerid:% 1 přijal soket socketid:% 2.|TCP|  
|[3321 – ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Podrobnosti|Fond pro% 1 nemá k dispozici žádné připojení a zaneprázdněná připojení% 2.|Kanál|  
|[3322 – DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Podrobnosti|Dispečer zahájil deserializaci zprávy s požadavkem.|ServiceModel|  
|[3323 – DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Podrobnosti|Dispečer dokončil deserializaci zprávy s požadavkem.|ServiceModel|  
|[3324 – DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Podrobnosti|Dispečer zahájil serializaci zprávy s odpovědí.|ServiceModel|  
|[3325 – DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Podrobnosti|Dispečer dokončil serializaci zprávy s odpovědí.|ServiceModel|  
|[3326 – ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Podrobnosti|Byla zahájena serializace požadavku klienta.|ServiceModel|  
|[3327 – ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Podrobnosti|Klient dokončil serializaci zprávy s požadavkem.|ServiceModel|  
|[3328 – ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Podrobnosti|Klient zahájil deserializaci zprávy s odpovědí.|ServiceModel|  
|[3329 – ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Podrobnosti|Klient dokončil deserializaci zprávy s odpovědí.|ServiceModel|  
|[3330 – SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Podrobnosti|Bylo zahájeno vyjednávání zabezpečení.|Zabezpečení|  
|[3331 – SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Podrobnosti|Vyjednávání zabezpečení bylo dokončeno.|Zabezpečení|  
|[3332 – SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Podrobnosti|Otevírání poskytovatel SecurityTokenProvider bylo dokončeno.|Zabezpečení|  
|[3333 – OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Podrobnosti|Odchozí zpráva byla zabezpečena.|Zabezpečení|  
|[3334 – IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Podrobnosti|Příchozí zpráva byla ověřena.|ServiceModel pro zabezpečení|  
|[3335 – GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Podrobnosti|Bylo zahájeno načítání instance služby.|ServiceModel|  
|[3336 – GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Podrobnosti|Instance služby byla načtena.|ServiceModel|  
|[3337 – ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Podrobnosti|Obslužná rutina channelhandlerid:% 1-byla zahájena smyčka příjmu zpráv.|Kanál|  
|[3338 – ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Podrobnosti|Obslužná rutina channelhandlerid:% 1-byla zastavena smyčka příjmu zpráv.|Kanál|  
|[3339 – ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Podrobnosti|Byl vytvořen objekt ChannelFactory.|ServiceModel|  
|[3340 – PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Podrobnosti|Bylo zahájeno přijetí připojení kanálu na% 1.|Kanál|  
|[3341 – PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Podrobnosti|Bylo přijato připojení kanálu.|Kanál|  
|[3342 – EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Podrobnosti|Bylo zahájeno vytváření připojení pro% 1.|Kanál|  
|[3343 – EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Podrobnosti|Připojení bylo vytvořeno.|Kanál|  
|[3345 – SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Podrobnosti|Preambule relace pro% 1 byla rozpoznána.|Kanál|  
|[3346 – ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Chyba|Čtecí modul připojení odesílá chybu% 1.|Kanál|  
|[3347 – SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Podrobnosti|Bylo zavřeno přijetí soketu.|TCP|  
|[3348 – ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Kritická|V hostiteli služby došlo k chybě.|TCP|  
|[3349 – ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Podrobnosti|Probíhá spuštění naslouchacího procesu pro '% 1 '.|Kanál|  
|[3350 – ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Podrobnosti|Spuštění naslouchacího procesu bylo dokončeno.|Kanál|  
|[3351 – ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Podrobnosti|Dosáhlo se maximální kvóty pro připojení ve fondu.|Přidělení|  
|[3352 – TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Chyba|Soket socketid:% 1 na vzdálenou adresu% 2 vypršel časový limit.|TCP|  
|[3353 – TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Upozornění|Soket socketid:% 1 na vzdálenou adresu% 2 došlo k chybě resetování připojení.|TCP|  
|[3354 – ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Podrobnosti|Vyjednávání zabezpečení služby bylo dokončeno.|Zabezpečení|  
|[3355 – SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Chyba|Zpracování vyjednávání zabezpečení se nezdařilo.|Zabezpečení|  
|[3356 – SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Podrobnosti|Ověření zabezpečení se zdařilo.|Zabezpečení|  
|[3357 – SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Chyba|Ověření zabezpečení se nezdařilo.|Zabezpečení|  
|[3358 – PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Podrobnosti|Byl duplikován soket pro% 1.|ActivationServices|  
|[3359 – SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Podrobnosti|Zosobnění zabezpečení se zdařilo.|Zabezpečení|  
|[3360 – SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Upozornění|Zosobnění zabezpečení se nezdařilo.|Zabezpečení|  
|[3361 – HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Upozornění|Požadavek kanálu HTTP byl přerušen.|HTTP|  
|[3362 – HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Upozornění|Odpověď kanálu http byla přerušena.|HTTP|  
|[3363 – HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Upozornění|Ověření protokolu HTTP se nezdařilo.|HTTP|  
|[3364 – SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Podrobnosti|Byla zahájena registrace objektu sharedlistenerproxy pro identifikátor URI% 1.|ActivationServices|  
|[3365 – SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Podrobnosti|Zastavování registru objektu sharedlistenerproxy|ActivationServices|  
|[3366 – SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Chyba|Registrace objektu sharedlistenerproxy se nezdařila se stavem% 1.|ActivationServices|  
|[3367 – ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Chyba|ConnectionPoolPreambleFailed.|Kanál|  
|[3368 – SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Podrobnosti|SslOnAcceptUpgradeStart|Zabezpečení|  
|[3369 – SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Podrobnosti|SslOnAcceptUpgradeStop|Zabezpečení|  
|[3370 – BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Podrobnosti|Kodér BinaryMessageEncoder zahájil zahájil kódování zprávy.|Kanál|  
|[3371 – MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Podrobnosti|Kodér mtommessageencoder zahájil zahájil kódování zprávy.|Kanál|  
|[3372 – TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Podrobnosti|Kodér textmessageencoder zahájil zahájil kódování zprávy.|Kanál|  
|[3373 – BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Podrobnosti|Kodér BinaryMessageEncoder zahájil zahájil dekódování zprávy.|Kanál|  
|[3374 – MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Podrobnosti|Kodér mtommessageencoder zahájil zahájil dekódování zprávy.|Kanál|  
|[3375 – TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Podrobnosti|Kodér textmessageencoder zahájil zahájil dekódování zprávy.|Kanál|  
|[3376 – HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Informace o|Přenos HTTP zahájil příjem zprávy.|HTTP|  
|[3377 – SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Podrobnosti|Soket socketid:% 1 přečte% 2 bajtů přečtených z% 3.|TCP|  
|[3378 – SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Podrobnosti|Soket socketid:% 1 přečte% 2 bajtů přečtených z% 3.|TCP|  
|[3379 – SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Podrobnosti|Soket socketid:% 1 zapisuje% 2 bajtů do% 3.|TCP|  
|[3380 – SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Podrobnosti|Soket socketid:% 1 zapisuje% 2 bajtů do% 3.|TCP|  
|[3381 – SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Podrobnosti|Bylo odesláno potvrzení relace SessionId% 1.|Kanál|  
|[3382 – ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Informace o|Probíhá opětovné připojení relace SessionId% 1.|Kanál|  
|[3383 – ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Informace o|V relaci SessionId% 1 došlo k chybě.|Kanál|  
|[3384 – WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Podrobnosti|Zabezpečení windowsstreamsecurity zahajuje se upgrade zabezpečení.|Zabezpečení|  
|[3385 – WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Podrobnosti|Zabezpečení Windows streamování při přijetí upgradu|Zabezpečení|  
|[3386 – SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Upozornění|Soket socketid:% 1 se přerušuje.|TCP|  
|[3388 – HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Podrobnosti|Zahájení kontextu httpgetcontext Start.|HTTP|  
|[3389 – ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Podrobnosti|Bylo zahájeno odesílání preambule klienta.|Kanál|  
|[3390 – ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Podrobnosti|Bylo ukončeno odesílání preambule klienta.|Kanál|  
|[3391 – HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Upozornění|Přijetí zprávy HTTP se nezdařilo.|HTTP|  
|[3392 – TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Informace o|Vytváří se objekt TransactionScope s identifikátorem LocalIdentifier:% 1 a distribuovaného identifikátoru DistributedIdentifier:% 2.|ServiceModel|  
|[3393 – StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Informace o|Kodér přečetl datový proud zprávy.|Kanál|  
|[3394 – StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Informace o|Kodér zapsal datový proud zprávy.|Kanál|  
|[3395 – MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Informace o|Kodér asynchronně zapsal zprávu.|Kanál|  
|[3396 – BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Informace o|Vyrovnávací paměť BufferId:% 1 dokončil zápis% 2 bajtů do základního datového proudu.|Kanál|  
|[3397 – BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Informace o|Kodér asynchronně zapsal zprávu.|Kanál|  
|[3398 – PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Podrobnosti|Sdílená paměť kanálu byla vytvořena v '% 1 '.|Kanál|  
|[3399 – NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Podrobnosti|Pojmenovaný kanál '% 1 ' byl vytvořen.|Kanál|  
|[3401 – SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Podrobnosti|Bylo zahájeno ověřování podpisu.|Zabezpečení|  
|[3402 – SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Podrobnosti|Ověření podpisu bylo úspěšné.|Zabezpečení|  
|[3403 – WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Podrobnosti|Bylo zahájeno dešifrování zabaleného klíče.|Zabezpečení|  
|[3404 – WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Podrobnosti|Dešifrování zabaleného klíče proběhlo úspěšně.|Zabezpečení|  
|[3405 – EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Podrobnosti|Bylo zahájeno šifrované zpracování dat.|Zabezpečení|  
|[3406 – EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Podrobnosti|Šifrované zpracování dat bylo úspěšné.|Zabezpečení|  
|[3407 – HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Podrobnosti|Obslužná rutina zprávy HTTP zahájila zpracování příchozího požadavku.|HTTP|  
|[3408 – HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Podrobnosti|Obslužná rutina zprávy HTTP zahájila asynchronní zpracování příchozího požadavku.|HTTP|  
|[3409 – HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Podrobnosti|Obslužná rutina zprávy HTTP dokončila zpracování příchozího požadavku.|HTTP|  
|[3410 – HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Upozornění|Obslužná rutina zprávy HTTP skončila chybou.|HTTP|  
|[3411 – HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Chyba|Vypršel časový limit připojení soketu WebSocket.|HTTP|  
|[3412 – HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Podrobnosti|Obslužná rutina zprávy HTTP zahájila zpracování odpovědi.|HTTP|  
|[3413 – HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Podrobnosti|Obslužná rutina zprávy HTTP zahájila asynchronní zpracování odpovědi.|HTTP|  
|[3414 – HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Podrobnosti|Obslužná rutina zprávy HTTP dokončila zpracování odpovědi.|HTTP|  
|[3415 – WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Podrobnosti|Bylo zahájeno odesílání požadavku na připojení soketu WebSocket příjemci% 1.|HTTP|  
|[3416 – WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Podrobnosti|Požadavek na připojení soketu WebSocketId% 1 byl odeslán.|HTTP|  
|[3417 – WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Podrobnosti|Bylo zahájeno přijímání připojení soketu WebSocket.|HTTP|  
|[3418 – WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Podrobnosti|Připojení soketu WebSocketId% 1 bylo přijato.|HTTP|  
|[3419 – WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Chyba|Připojení soketu WebSocket bylo odmítnuto se stavovým kódem% 1.|HTTP|  
|[3420 – WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Chyba|Požadavek na připojení soketu WebSocket se nezdařil:% 1|HTTP|  
|[3421 – WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Chyba|Připojení soketu WebSocketId% 1 bylo přerušeno.|HTTP|  
|[3422 – WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Podrobnosti|Soket WebSocketId% 1 zapisuje% 2 bajtů do:% 3|HTTP|  
|[3423 – WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Podrobnosti|Asynchronní zápis v soketu WebSocketId% 1 byl ukončen.|HTTP|  
|[3424 – WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Podrobnosti|Bylo zahájeno čtení z soketu WebSocketId% 1.|HTTP|  
|[3425 – WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Podrobnosti|Soket WebSocketId% 1 přečetl% 2 bajtů z% 3.|HTTP|  
|[3426 – WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Podrobnosti|Soket WebSocketId% 1 odesílá zprávu ukončení do objektu% 2 s koncovým stavem% 3.|HTTP|  
|[3427 – WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Podrobnosti|Soket WebSocketId% 1 odesílá zprávu ukončení výstupu do% 2 s ukončovacím stavem% 3.|HTTP|  
|[3428 – WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Podrobnosti|Připojení soketu WebSocketId% 1 bylo ukončeno.|HTTP|  
|[3429 – WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Podrobnosti|Soket WebSocketId% 1 přijal zprávu ukončení připojení se stavem% 2.|HTTP|  
|[3430 – WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Podrobnosti|Použití hodnota WebSocketVersion z objektu WebSocket typu '% 1 ' klienta.|HTTP|  
|[3431 – WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Podrobnosti|Vytváření objektu WebSocket pro klienta s továrnou typu% 1.|HTTP|  
|[3553 – XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Informace o|Metody xamlservicesload Start|WebHost|  
|[3554 – XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Informace o|XamlServicesLoad Stop|WebHost|  
|[3555 – CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Informace o|Metody CreateWorkflowServiceHost Start|WebHost|  
|[3556 – CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Informace o|Zastavení metody CreateWorkflowServiceHost|WebHost|  
|[3558 – ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Informace o|Zahájení aktivace služby|WebHost|  
|[3559 – ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Informace o|Zastavení aktivace služby|WebHost|  
|[3560 – ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Podrobnosti|Dostupná paměť (bajty):% 1|Přidělení|  
|[3800 – RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Informace o|Směrovací služba zavírá klienta% 1.|RoutingServices|  
|[3800 – RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Upozornění|V klientovi směrovací služby% 1 došlo k chybě.|RoutingServices|  
|[3802 – RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Informace o|Jednosměrná zpráva směrovací služby se dokončuje.|RoutingServices|  
|[3803 – RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Chyba|Směrovací službě se nepodařilo zpracovat zprávu na koncovém bodu s adresou% 1.|RoutingServices|  
|[3804 – RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Informace o|Směrovací služba vytváří klienta pro koncový bod:% 1.|RoutingServices|  
|[3805 – RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Podrobnosti|Směrovací služba je nakonfigurovaná s hodnotami RouteOnHeadersOnly:% 1, SoapProcessingEnabled:% 2, EnsureOrderedDispatch:% 3.|RoutingServices|  
|[3807 – RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Informace o|Probíhá ukončování zprávy s odpovědí na žádost směrovací služby.|RoutingServices|  
|[3809 – RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Podrobnosti|Směrovací služba směrovala zprávu s ID:% 1 do seznamu koncových bodů% 2.|RoutingServices|  
|[3810 – RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Informace o|Pro směrovací službu se nastavil nový konfigurace RoutingConfiguration.|RoutingServices|  
|[3815 – RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Informace o|Směrovací služba zpracovává zprávu s ID:% 1, akce:% 2, příchozí URL:% 3, přijato v transakci:% 4.|RoutingServices|  
|[3816 – RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Informace o|Směrovací služba přenáší zprávu s ID:% 1 [operace% 2] do% 3.|RoutingServices|  
|[3817 – RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Informace o|Směrovací služba potvrzuje transakci s ID:% 1.|RoutingServices|  
|[3818 – RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Chyba|Komponenta směrovací služby% 1 zjistila výjimku duplexního zpětného volání.|RoutingServices|  
|[3819 – RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Informace o|Zpráva směrovací služby s ID:% 1 [operace% 2] byla přesunuta do záložního koncového bodu% 3.|RoutingServices|  
|[3820 – RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Informace o|Směrovací služba vytvořila novou transakci s ID% 1 pro zpracování zpráv.|RoutingServices|  
|[3821 – RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Upozornění|Směrovací služba selhala při zavírání odchozího klienta% 1.|RoutingServices|  
|[3822 – RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Informace o|Směrovací služba posílá zpět zprávu odpovědi s akcí% 1.|RoutingServices|  
|[3823 – RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Upozornění|Směrovací služba odesílá zpět zprávu chybové odpovědi s akcí% 1.|RoutingServices|  
|[3824 – RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Podrobnosti|Směrovací služba volá metodu ReceiveContext. Complete pro zprávu s ID:% 1.|RoutingServices|  
|[3825 – RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Upozornění|Směrovací služba volá metodu ReceiveContext. Abandon pro zprávu s ID:% 1.|RoutingServices|  
|[3826 – RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Podrobnosti|Směrovací služba bude odesílat zprávy pomocí existující transakce% 1.|RoutingServices|  
|[3827 – RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Upozornění|Směrovací službě se nepodařilo odeslat do '% 1 '.|RoutingServices|  
|[3828 – RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Informace o|Služba směrování MessageFilterTable – začátek shody|RoutingServices|  
|[3829 – RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Informace o|Služba směrování MessageFilterTable se zastavila.|RoutingServices|  
|[3830 – RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Podrobnosti|Směrovací služba volá přerušení na kanálu:% 1.|RoutingServices|  
|[3831 – RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Podrobnosti|Směrovací služba zpracovala výjimku.|RoutingServices|  
|[3832 – RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Informace o|Služba Směrování úspěšně přenesla zprávu s ID:% 1 [operace% 2] do% 3.|RoutingServices|  
|[4001 – TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Podrobnosti|Byla přijata relace naslouchacího procesu přenosu prostřednictvím% 1.|ActivationServices|  
|[4002 – FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Kritická|FailFastException.|ActivationServices|  
|[4003 – ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Chyba|Chyba kanálu při spuštění služby.|ActivationServices|  
|[4008 – DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Podrobnosti|Bylo zahájeno odesílání relace.|ActivationServices|  
|[4008 – DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Upozornění|Odeslání relace pro% 1 se nezdařilo, protože fronta čekajících relací je plná s% 2 čekajícími položkami.|ActivationServices|  
|[4011 – MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Podrobnosti|Registrace fronty zpráv byla zahájena.|ActivationServices|  
|[4012 – MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Chyba|Registrace fronty zpráv byla přerušena se stavem% 1 pro identifikátor URI:% 2.|ActivationServices|  
|[4013 – MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Podrobnosti|Zrušení registrace fronty zpráv se zdařilo pro identifikátor URI:% 1.|ActivationServices|  
|[4014 – MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Chyba|Registrace fronty zpráv pro identifikátor URI% 1 se nezdařila se stavem% 2.|ActivationServices|  
|[4015 – MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Informace o|Registrace fronty zpráv pro identifikátor URI% 1 byla dokončena.|ActivationServices|  
|[4016 – MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Chyba|Při duplikaci soketu ve frontě zpráv došlo k chybě.|ActivationServices|  
|[4019 – MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Podrobnosti|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 – TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Podrobnosti|Naslouchací proces přenosu protokolu TCP zahájil naslouchání na identifikátoru URI:% 1.|ActivationServices|  
|[4021 – TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Podrobnosti|Naslouchací proces přenosu protokolu TCP naslouchá.|ActivationServices|  
|[4022 – WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Chyba|Kód chyby:% 1|ActivationServices|  
|[4023 – WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Informace o|Bylo ukončeno všechny instance kanálů naslouchacího procesu.|ActivationServices|  
|[4024 – WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Chyba|Kód chyby:% 1|ActivationServices|  
|[4025 – OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Chyba|Kód chyby:% 1|ActivationServices|  
|[4026 – WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Podrobnosti|BYL připojen.|ActivationServices|  
|[4027 – WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Podrobnosti|BYL odpojen.|ActivationServices|  
|[4028 – PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Podrobnosti|Naslouchací proces přenosu kanálu naslouchá od spuštění v identifikátoru URI:% 1.|ActivationServices|  
|[4029 – PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Podrobnosti|Naslouchací proces přenosu kanálu ukončil naslouchání.|ActivationServices|  
|[4030 – DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Informace o|Odeslání relace se zdařilo.|ActivationServices|  
|[4031 – DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Chyba|Odeslání relace se nezdařilo.|ActivationServices|  
|[4032 – WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Kritická|Vypršel časový limit připojení.|ActivationServices|  
|[4033 – RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Podrobnosti|Bylo zahájeno prohledávání směrovací tabulky.|ActivationServices|  
|[4034 – RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Podrobnosti|Prohledávání směrovací tabulky bylo dokončeno.|ActivationServices|  
|[4035 – PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Podrobnosti|Poměr fronty nedokončených relací:% 1/% 2|Přidělení|  
|[4600 – MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Upozornění|Zprávu se nepodařilo zaznamenat do protokolu, protože přesahuje velikost události ETW.|WCFMessageLogging|  
|[4801 – DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Upozornění|Objektem DiscoveryClient zahozena vytvořené uvnitř DiscoveryClientChannel se nepovedlo zavřít, a proto se přerušilo.|Zjišťování|  
|[4802 – DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Informace o|Při zavírání objektem DiscoveryClient zahozena došlo k potlačení ProtocolException. Důvodem může být to, že služba DiscoveryService se stále snaží odeslat odpověď objektem DiscoveryClient zahozena.|Zjišťování|  
|[4803 – DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Informace o|Objektem DiscoveryClient zahozena přijal z objektu DiscoveryProxy zprávu o potlačení vícesměrového vysílání.|Zjišťování|  
|[4804 – DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Informace o|Zpráva% 1 s parametrem messageId =% 2 byla zahozena objektem DiscoveryClient zahozena, protože byla dokončena odpovídající operace% 3.|Zjišťování|  
|[4805 – DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 byla zahozena, protože její obsah byl neplatný.|Zjišťování|  
|[4806 – DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 a relatesTo =% 3 byla vynechána objektem DiscoveryClient zahozena, protože buď byla dokončena odpovídající operace% 4, nebo hodnota relatesTo není platná.|Zjišťování|  
|[4807 – DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Upozornění|Zpráva požadavku na zjišťování s parametrem messageId =% 1 byla zahozena, protože obsahovala neplatnou adresu ReplyTo.|Zjišťování|  
|[4808 – DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Upozornění|Zpráva% 1 byla zahozena, protože neměla žádný obsah.|Zjišťování|  
|[4809 – DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Upozornění|Zpráva% 1 byla vyřazena, protože Hlavička zprávy neobsahovala požadovanou vlastnost MessageId.|Zjišťování|  
|[4810 – DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 byla zahozena objektem DiscoveryClient zahozena, protože neobsahovala vlastnost DiscoveryMessageSequence.|Zjišťování|  
|[4811 – DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 byla zahozena objektem DiscoveryClient zahozena, protože Hlavička zprávy neobsahovala požadovanou vlastnost RelatesTo.|Zjišťování|  
|[4812 – DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Upozornění|Zpráva požadavku na zjišťování s parametrem messageId =% 1 byla zahozena, protože neobsahovala adresu ReplyTo.|Zjišťování|  
|[4813 – DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 byla zahozena, protože byla duplicitní.|Zjišťování|  
|[4814 – EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informace o|Zjistitelnost koncového bodu s parametry EndpointAddress =% 1 a ListenUri =% 2 byla zakázána.|Zjišťování|  
|[4814 – EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informace o|Zjistitelnost koncového bodu s parametry EndpointAddress =% 1 a ListenUri =% 2 byla povolena.|Zjišťování|  
|[4816 – FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Podrobnosti|V DiscoveryClientChannel se iniciovala operace hledání pro zjišťování koncových bodů.|Zjišťování|  
|[4817 – InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Upozornění|DiscoveryClientChannel se nepodařilo vytvořit kanál se zjištěným koncovým bodem s parametry EndpointAddress =% 1 a Via =% 2. DiscoveryClientChannel se teď pokusí použít další dostupný zjištěný koncový bod.|Zjišťování|  
|[4818 – InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Upozornění|DiscoveryClientChannel se nepodařilo otevřít kanál se zjištěným koncovým bodem s parametry EndpointAddress =% 1 a Via =% 2. DiscoveryClientChannel se teď pokusí použít další dostupný zjištěný koncový bod.|Zjišťování|  
|[4819 – InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Informace o|DiscoveryClientChannel úspěšně zjistil koncový bod a otevřel ho pomocí kanálu. Klient je připojen ke službě pomocí EndpointAddress = '% 1 ' a Via = '% 2 '.|Zjišťování|  
|[4820 – SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Informace o|Třída SynchronizationContext byl obnoven na původní hodnotu% 1 podle DiscoveryClientChannel.|Zjišťování|  
|[4821 – SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Informace o|Před zahájením operace Find byl třída SynchronizationContext nastaven na hodnotu null od DiscoveryClientChannel.|Zjišťování|  
|[5001 – DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Podrobnosti|Bylo zahájeno serializace kontraktu DataContract% 1 s náhradami.|Serializace|  
|[5002 – DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Podrobnosti|Serializace kontraktu DataContract s náhradami byla zastavena.|Serializace|  
|[5003 – DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Podrobnosti|Bylo zahájeno deserializace kontraktu DataContract% 1 s náhradami.|Serializace|  
|[5004 – DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Podrobnosti|Deserializace kontraktu DataContract se zástupnými náhradami byla ukončena.|Serializace|  
|[5005 – ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Podrobnosti|Operace importknowntypes Start.|Serializace|  
|[5006 – ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Podrobnosti|Zastavení operace importknowntypes|Serializace|  
|[5007 – DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Podrobnosti|Bylo zahájeno řešení překladače kontraktu DataContract% 1.|Serializace|  
|[5008 – DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Podrobnosti|Bylo zahájeno vytváření zapisovače% 1 pro DataContract pro% 2.|Serializace|  
|[5009 – DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Podrobnosti|Ukončilo se generování zapisovače DataContract.|Serializace|  
|[5010 – DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Podrobnosti|Operace DataContract vygenerovala% 1 čtečku pro% 2 Start.|Serializace|  
|[5011 – DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Podrobnosti|Bylo ukončeno generování kontraktu DataContract.|Serializace|  
|[5012 – DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Podrobnosti|Bylo zahájeno generování čtecího modulu JSON% 1 pro% 2.|Serializace|  
|[5013 – DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Podrobnosti|Bylo ukončeno generování čtečky JSON.|Serializace|  
|[5014 – DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Podrobnosti|Bylo zahájeno generování JSON% 1 zapisovače pro% 2.|Serializace|  
|[5015 – DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Podrobnosti|Ukončilo se generování zapisovače JSON.|Serializace|  
|[5016 – GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Podrobnosti|Bylo zahájeno generování serializovatelného kódu XML pro% 1.|Serializace|  
|[5017 – GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Podrobnosti|Bylo ukončeno generování serializovatelného kódu XML.|Serializace|  
|[5203 – JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Podrobnosti|Kodér jsonmessageencoder zahájil zahájil dekódování zprávy.|Kanál|  
|[5204 – JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Podrobnosti|Kodér jsonmessageencoder zahájil zahájil kódování zprávy.|Kanál|  
|[5402 – TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Podrobnosti|Bylo zahájeno ověřování tokenu SecurityToken (typ% 1 a ID% 2).|Zabezpečení|  
|[5403 – TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Podrobnosti|Ověření tokenu SecurityToken (typ% 1 a ID% 2) se zdařilo.|Zabezpečení|  
|[5404 – TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Chyba|Ověření tokenu SecurityToken (typ% 1 a ID% 2) se nezdařilo. %3|Zabezpečení|  
|[5405 – GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Podrobnosti|Načtení názvu vystavitele:% 1 z tokenu tokenId:% 2 bylo úspěšné.|Zabezpečení|  
|[5406 – GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Chyba|Načtení názvu vystavitele z tokenu tokenId:% 1 se nezdařilo.|Zabezpečení|  
|[5600 – FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Podrobnosti|Začalo zpracování federační zprávy.|Zabezpečení|  
|[5601 – FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Podrobnosti|Zpracování federační zprávy bylo úspěšné.|Zabezpečení|  
|[5602 – FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Podrobnosti|Bylo zahájeno vytváření federační zprávy z odeslaného formuláře.|Zabezpečení|  
|[5603 – FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Podrobnosti|Vytváření federační zprávy z odeslaného formuláře se zdařilo.|Zabezpečení|  
|[5604 – SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Podrobnosti|Bylo zahájeno načítání tokenu relace ze souboru cookie relace.|Zabezpečení|  
|[5605 – SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Podrobnosti|Čtení tokenu relace ze souboru cookie relace bylo úspěšné.|Zabezpečení|  
|[5606 – PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Podrobnosti|Bylo zahájeno nastavení objektu zabezpečení z tokenu relace.|Zabezpečení|  
|[5607 – PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Podrobnosti|Nastavení objektu zabezpečení z tokenu relace bylo úspěšné.|Zabezpečení|  
|[57393 – AppDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Informace o|Uvolňování domény AppDomain. AppDomain.FriendlyName %1, ProcessName %2, ProcessId %3.|Infrastruktura|  
|[57394 – HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Informace o|Zpracovává se výjimka.|Infrastruktura|  
|[57395 – ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Chyba|Došlo k neočekávané chybě. Aplikace by se neměly pokoušet tuto chybu zpracovat. Pro účely diagnostiky je tato anglická zpráva přidružena k chybě:% 1.|Infrastruktura|  
|[57396 – ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Upozornění|Došlo k vyvolání výjimky. Zdroj% 1.|Infrastruktura|  
|[57397 – UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Kritická|Neošetřená výjimka.|Infrastruktura|  
|[57399 – TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Kritická|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57400 – TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Chyba|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57401 – TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Informace o|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57402 – TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Podrobnosti|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57403 – TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Upozornění|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57404 – HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Upozornění|Zpracovává se výjimka.|Infrastruktura|  
|[62326 – HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Informace o|Adresa URL '% 1 ' je hostitelem dokumentu XAML s typem kořenového elementu '% 2 '. Typ obslužné rutiny protokolu HTTP% 3 je vybrán pro obsluhu všech požadavků provedených na tuto adresu URL.|WebHost|
