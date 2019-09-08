---
title: Události analytického trasování – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 1b44e6b0abf0fc48b43ae17cbd24780e46ae518d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798125"
---
# <a name="analytic-trace-event-reference"></a>Události analytického trasování – přehled
Následující tabulka definuje úrovně událostí, identifikátory a zprávy přidružené k analytickému trasování služby WCF.  
  
## <a name="event-reference"></a>Odkaz na událost  
  
|ID události|Úroveň události|Zpráva události|klíčová slova|  
|--------------|-----------------|-------------------|--------------|  
|[131 – BufferPoolAllocation](131-bufferpoolallocation.md)|Podrobnosti|Fond přiděluje% 1 bajtů.|Infrastruktura|  
|[132 – BufferPoolChangeQuota](132-bufferpoolchangequota.md)|Podrobnosti|Fondu velikosti% 1, mění se kvóta o% 2.|Infrastruktura|  
|[133 – ActionItemScheduled](133-actionitemscheduled.md)|Podrobnosti|Bylo vyvoláno zpětné volání plánovače v/v.|Infrastruktura|  
|[134 – ActionItemCallbackInvoked](134-actionitemcallbackinvoked.md)|Podrobnosti|Bylo vyvoláno zpětné volání plánovače v/v.|Infrastruktura|  
|[201 – ClientMessageInspectorAfterReceiveInvoked](201-clientmessageinspectorafterreceiveinvoked.md)|Informace o|Dispečer vyvolal ' AfterReceiveReply ' na třídy ClientMessageInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[202 – ClientMessageInspectorBeforeSendInvoked](202-clientmessageinspectorbeforesendinvoked.md)|Informace o|Dispečer vyvolal ' BeforeSendRequest ' na třídy ClientMessageInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[203 – ClientParameterInspectorAfterCallInvoked](203-clientparameterinspectoraftercallinvoked.md)|Informace o|Dispečer vyvolal ' AfterCall ' na třídy ClientParameterInspector. typu '% 1 '.|Řešení potíží, ServiceModel|  
|[204 – ClientParameterInspectorBeforeCallInvoked](204-clientparameterinspectorbeforecallinvoked.md)|Informace o|Dispečer vyvolal ' BeforeCall ' na třídy ClientParameterInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[205 – OperationInvoked](205-operationinvoked.md)|Informace o|Metody OperationInvoker vyvolal metodu% 1.|EndToEndMonitoring, řešení potíží, ServiceModel|  
|[206 – ErrorHandlerInvoked](206-errorhandlerinvoked.md)|Informace o|Dispečer vyvolal rutinu ErrorHandler typu% 1 s výjimkou typu% 3.  ErrorHandled = = '% 2 '.|Řešení potíží, ServiceModel|  
|[207 – FaultProviderInvoked](207-faultproviderinvoked.md)|Informace o|Dispečer vyvolal FaultProvider typu% 1 s výjimkou typu% 2.|Řešení potíží, ServiceModel|  
|[208 – MessageInspectorAfterReceiveInvoked](208-messageinspectorafterreceiveinvoked.md)|Informace o|Dispečer vyvolal ' AfterReceiveReply ' na třídy MessageInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[209 – MessageInspectorBeforeSendInvoked](209-messageinspectorbeforesendinvoked.md)|Informace o|Dispečer vyvolal ' BeforeSendRequest ' na třídy MessageInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[210 – MessageThrottleExceeded](210-messagethrottleexceeded.md)|Upozornění|Bylo dosaženo omezení% 1 pro% 2.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[211 – ParameterInspectorAfterCallInvoked](211-parameterinspectoraftercallinvoked.md)|Informace o|Dispečer vyvolal ' AfterCall ' na třídy ParameterInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[212 – ParameterInspectorBeforeCallInvoked](212-parameterinspectorbeforecallinvoked.md)|Informace o|Dispečer vyvolal ' BeforeCall ' na třídy ParameterInspector typu '% 1 '.|Řešení potíží, ServiceModel|  
|[213 – ServiceHostStarted](213-servicehoststarted.md)|LogAlways|Třída ServiceHost byla spuštěna:% 1.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[214 – OperationCompleted](214-operationcompleted.md)|Informace o|Metody OperationInvoker dokončil volání metody% 1.  Doba volání metody byla% 2 MS.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[215 – MessageReceivedByTransport](215-messagereceivedbytransport.md)|Informace o|Přenos přijal zprávu od '% 1 '.|Řešení potíží, ServiceModel|  
|[216 – MessageSentByTransport](216-messagesentbytransport.md)|Informace o|Přenos odeslal zprávu na% 1.|Řešení potíží, ServiceModel|  
|[217 – ClientOperationPrepared](217-clientoperationprepared.md)|Informace o|Klient provádí operaci% 1 definovanou ve kontraktu% 2. Zpráva bude odeslána na '% 3 '.|Řešení potíží, ServiceModel|  
|[218 – ClientOperationCompleted](218-clientoperationcompleted.md)|Informace o|Klient dokončil provádění operace% 1 definované ve kontraktu% 2. Zpráva byla odeslána na '% 3 '.|Řešení potíží, ServiceModel|  
|[219 – ServiceException](219-serviceexception.md)|Chyba|Během zpracování zprávy došlo k neošetřené výjimce typu% 2.  Úplná výjimka ToString:% 1.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[220 – MessageSentToTransport](220-messagesenttotransport.md)|Informace o|Dispečer odeslal zprávu přenosu. ID korelace =% 1.|EndToEndMonitoring, řešení potíží, ServiceModel|  
|[221 – MessageReceivedFromTransport](221-messagereceivedfromtransport.md)|Informace o|Dispečer obdržel zprávu od přenosu. ID korelace =% 1.|EndToEndMonitoring, řešení potíží, ServiceModel|  
|[222 – OperationFailed](222-operationfailed.md)|Upozornění|Metoda '% 1 ' vyvolala neošetřenou výjimku při vyvolání rozhraním metody OperationInvoker. Doba volání metody byla% 2 MS.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[223 – OperationFaulted](223-operationfaulted.md)|Upozornění|Metoda '% 1 ' vyvolala FaultException při vyvolání rozhraním metody OperationInvoker. Doba volání metody byla% 2 MS.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[224 – MessageThrottleAtSeventyPercent](224-messagethrottleatseventypercent.md)|Upozornění|Omezení% 1 pro% 2 je na 70%.|HealthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[226 – IdleServicesClosed](226-idleservicesclosed.md)|LogAlways|% 1 nečinných služeb z celkového počtu% 2 aktivované služby byly uzavřeny.|HealthMonitoring webhost|  
|[301 – UserDefinedErrorOccurred](301-userdefinederroroccurred.md)|Chyba|Název: '% 1 ', odkaz: '% 2 ', datová část:% 3.|UserEvents, healthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[302 – UserDefinedWarningOccurred](302-userdefinedwarningoccurred.md)|Upozornění|Název: '% 1 ', odkaz: '% 2 ', datová část:% 3.|UserEvents, healthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[303 – UserDefinedInformationEventOccured](303-userdefinedinformationeventoccured.md)|Informace o|Název: '% 1 ', odkaz: '% 2 ', datová část:% 3.|UserEvents, healthMonitoring, EndToEndMonitoring, řešení potíží, ServiceModel|  
|[401– StopSignPostEvent](401-stopsignpostevent.md)|Informace o|Hranice aktivity.|Poradce při potížích|  
|[402 – StartSignpostEvent](402-startsignpostevent.md)|Informace o|Hranice aktivity.|Poradce při potížích|  
|[403 – SuspendSignpostEvent](403-suspendsignpostevent.md)|Informace o|Hranice aktivity.|Poradce při potížích|  
|[404 – ResumeSignpostEvent](404-resumesignpostevent.md)|Informace o|Hranice aktivity.|Poradce při potížích|  
|[451 – MessageLogInfo](451-messageloginfo.md)|Informace o|%1|Řešení potíží, WCFMessageLogging|  
|[452 – MessageLogWarning](452-messagelogwarning.md)|Upozornění|%1|Řešení potíží, WCFMessageLogging|  
|[499 – TransferEmitted](499-transferemitted.md)|LogAlways|Byla vyvolána událost přenosu.|Řešení potíží, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 – CompilationStart](501-compilationstart.md)|Informace o|Zahajte kompilaci.|WebHost|  
|[502 – CompilationStop](502-compilationstop.md)|Informace o|Ukončit kompilaci|WebHost|  
|[503 – ServiceHostFactoryCreationStart](503-servicehostfactorycreationstart.md)|Informace o|ServiceHostFactory začít vytvářet.|WebHost|  
|[504 – ServiceHostFactoryCreationStop](504-servicehostfactorycreationstop.md)|Informace o|Vytvoření konce ServiceHostFactory|WebHost|  
|[505 – CreateServiceHostStart](505-createservicehoststart.md)|Informace o|Spusťte metody CreateServiceHost.|WebHost|  
|[506 – CreateServiceHostStop](506-createservicehoststop.md)|Informace o|Konec metody CreateServiceHost|WebHost|  
|[507 – HostedTransportConfigurationManagerConfigInitStart](507-hostedtransportconfigurationmanagerconfiginitstart.md)|Informace o|Správce hostedtransportconfigurationmanager ukončil zahájit inicializaci konfigurace.|WebHost|  
|[508 – HostedTransportConfigurationManagerConfigInitStop](508-hostedtransportconfigurationmanagerconfiginitstop.md)|Informace o|Inicializace konfigurace ukončení správce hostedtransportconfigurationmanager ukončil|WebHost|  
|[509 – ServiceHostOpenStart](509-servicehostopenstart.md)|Informace o|Inicializace konfigurace ukončení správce hostedtransportconfigurationmanager ukončil|ServiceHost|  
|[510 – ServiceHostOpenStop](510-servicehostopenstop.md)|Informace o|Otevření hostitele ServiceHost bylo dokončeno.|ServiceHost|  
|[513 – WebHostRequestStart](513-webhostrequeststart.md)|Informace o|Byl přijat požadavek s virtuální cestou% 2 z domény aplikace% 1.|WebHost|  
|[514 – WebHostRequestStop](514-webhostrequeststop.md)|Informace o|Zastavení ukončení požadavku webhostrequest|WebHost|  
|[601 – CBAEntryRead](601-cbaentryread.md)|Podrobnosti|Relativní adresa prvku ServiceActivation: '% 1 ', normalizovaná relativní adresa '% 2 '.||  
|[602 – CBAMatchFound](602-cbamatchfound.md)|Podrobnosti|Příchozí požadavek odpovídá elementu ServiceActivation s adresou% 1.||  
|[603 – AspNetRoutingService](603-aspnetroutingservice.md)|Podrobnosti|Příchozí požadavek odpovídá službě WCF definované v trase Asp.Net s adresou% 1.|RoutingServices|  
|[604 – AspNetRoute](604-aspnetroute.md)|Podrobnosti|Byla přidána nová trasa Asp.Net '% 1 ' s serviceType '% 2 ' a typem servicehostfactorytype '% 3 '.|RoutingServices|  
|[605 – IncrementBusyCount](605-incrementbusycount.md)|Podrobnosti|Metoda IncrementBusyCount volána. Zdroj:% 1|WebHost|  
|[606 – DecrementBusyCount](606-decrementbusycount.md)|Podrobnosti|Metoda DecrementBusyCount volána. Zdroj:% 1|WebHost|  
|[701 – ServiceChannelOpenStart](701-servicechannelopenstart.md)|Podrobnosti|Operace servicechannelopen se spustil.|WebHost|  
|[702 – ServiceChannelOpenStop](702-servicechannelopenstop.md)|Informace o|Operace servicechannelopen se dokončilo.|ServiceModel|  
|[703 – ServiceChannelCallStart](703-servicechannelcallstart.md)|Informace o|Spuštění servicechannelcall se spustil.|ServiceModel|  
|[704 – ServiceChannelBeginCallStart](704-servicechannelbegincallstart.md)|Informace o|Bylo zahájeno asynchronní volání kanálu ServiceChannel.|ServiceModel|  
|[706 – HttpSendMessageStart](706-httpsendmessagestart.md)|Podrobnosti|Byl zahájen požadavek Send protokolu HTTP.|HTTP|  
|[707 – HttpSendStop](707-httpsendstop.md)|Podrobnosti|Byl ukončen požadavek Send protokolu HTTP.|HTTP|  
|[708 – HttpMessageReceiveStart](708-httpmessagereceivestart.md)|Podrobnosti|Z přenosu HTTP byla přijata zpráva.|HTTP|  
|[709 – DispatchMessageStart](709-dispatchmessagestart.md)|Informace o|Bylo zahájeno odesílání zpráv.|ServiceModel|  
|[710 – HttpContextBeforeProcessAuthentication](710-httpcontextbeforeprocessauthentication.md)|Podrobnosti|Spusťte ověřování pro odeslání zprávy.|ServiceModel|  
|[711 – DispatchMessageBeforeAuthorization](711-dispatchmessagebeforeauthorization.md)|Podrobnosti|Spusťte autorizaci pro odeslání zprávy.|ServiceModel|  
|[712 – DispatchMessageStop](712-dispatchmessagestop.md)|Informace o|Odeslání zprávy bylo dokončeno.|ServiceModel|  
|[715 – ClientChannelOpenStart](715-clientchannelopenstart.md)|Informace o|Kanálu ServiceChannel otevřít Start.|ServiceModel|  
|[716 – ClientChannelOpenStop](716-clientchannelopenstop.md)|Informace o|Kanálu ServiceChannel otevřené zastavení.|ServiceModel|  
|[717 – HttpSendStreamedMessageStart](717-httpsendstreamedmessagestart.md)|Informace o|Začalo streamovaná zpráva odeslání protokolu HTTP.|HTTP|  
|[1400 – ChannelInitializationTimeout](1400-channelinitializationtimeout.md)|Chyba|1%|ServiceModel|  
|[1401 – CloseTimeout](1401-closetimeout.md)|Chyba|1%|ServiceModel|  
|[1402 – IdleTimeout](1402-idletimeout.md)|Chyba|% 1 klíč fondu připojení:% 2|ServiceModel|  
|[1403 – LeaseTimeout](1403-leasetimeout.md)|Informace o|% 1 klíč fondu připojení:% 2|ServiceModel|  
|[1405 – OpenTimeout](1405-opentimeout.md)|Chyba|%1|ServiceModel|  
|[1406 – ReceiveTimeout](1406-receivetimeout.md)|Chyba|%1|ServiceModel|  
|[1407 – SendTimeout](1407-sendtimeout.md)|Chyba|%1|ServiceModel|  
|[1409 – InactivityTimeout](1409-inactivitytimeout.md)|Informace o|%1|ServiceModel|  
|[1416 – MaxReceivedMessageSizeExceeded](1416-maxreceivedmessagesizeexceeded.md)|Chyba|%1|Přidělení|  
|[1417 – MaxSentMessageSizeExceeded](1417-maxsentmessagesizeexceeded.md)|Chyba|%1|Přidělení|  
|[1418 – MaxOutboundConnectionsPerEndpointExceeded](1418-maxoutboundconnectionsperendpointexceeded.md)|Informace o|%1|Přidělení|  
|[1419 – MaxPendingConnectionsExceeded](1419-maxpendingconnectionsexceeded.md)|Informace o|%1|Přidělení|  
|[1420 – ReaderQuotaExceeded](1420-readerquotaexceeded.md)|Chyba|%1|Přidělení|  
|[1422 – NegotiateTokenAuthenticatorStateCacheExceeded](1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Chyba|%1|Přidělení|  
|[1423 – NegotiateTokenAuthenticatorStateCacheRatio](1423-negotiatetokenauthenticatorstatecacheratio.md)|Podrobnosti|Vyjednat poměr mezipaměti stavu ověřovacích dat tokenu:% 1/% 2|Přidělení|  
|[1424 – SecuritySessionRatio](1424-securitysessionratio.md)|Podrobnosti|Poměr relace zabezpečení:% 1/% 2|Přidělení|  
|[1430 – PendingConnectionsRatio](1430-pendingconnectionsratio.md)|Podrobnosti|Poměr nedokončených připojení:% 1/% 2|Přidělení|  
|[1431 – ConcurrentCallsRatio](1431-concurrentcallsratio.md)|Podrobnosti|Poměr souběžných relací:% 1/% 2|Přidělení|  
|[1432 – ConcurrentSessionsRatio](1432-concurrentsessionsratio.md)|Podrobnosti|Poměr souběžných relací:% 1/% 2|Přidělení|  
|[1433 – OutboundConnectionsPerEndpointRatio](1433-outboundconnectionsperendpointratio.md)|Podrobnosti|Poměr odchozích připojení na koncový bod:% 1/% 2|Přidělení|  
|[1436 – PendingMessagesPerChannelRatio](1436-pendingmessagesperchannelratio.md)|Podrobnosti|Poměr nedokončených zpráv na kanál:% 1/% 2|Přidělení|  
|[1438 – ConcurrentInstancesRatio](1438-concurrentinstancesratio.md)|Podrobnosti|Poměr souběžných instancí:% 1/% 2|Přidělení|  
|[1439 – PendingAcceptsAtZero](1439-pendingacceptsatzero.md)|Informace o|Zbývá nula přijetí|Přidělení|  
|[1441 – MaxSessionSizeReached](1441-maxsessionsizereached.md)|Upozornění|1%|Přidělení|  
|[1442 – ReceiveRetryCountReached](1442-receiveretrycountreached.md)|Upozornění|Byl dosažen počet opakování přijetí u zprávy služby MSMQ s ID% 1.|Přidělení|  
|[1443 – MaxRetryCyclesExceededMsmq](1443-maxretrycyclesexceededmsmq.md)|Chyba|Byl překročen maximální počet cyklů opakování u zprávy služby MSMQ s ID% 1.|Přidělení|  
|[1445 – ReadPoolMiss](1445-readpoolmiss.md)|Podrobnosti|Byl vytvořen nový% 1.|Přidělení|  
|[1446 – WritePoolMiss](1446-writepoolmiss.md)|Podrobnosti|Byl vytvořen nový% 1.|Přidělení|  
|[1451 – MaxRetryCyclesExceeded](1451-maxretrycyclesexceeded.md)|Chyba|1%|Přidělení|  
|[3300 – ReceiveContextCompleteFailed](3300-receivecontextcompletefailed.md)|Upozornění|Dokončení% 1 se nezdařilo.|Kanál|  
|[3301 – ReceiveContextAbandonFailed](3301-receivecontextabandonfailed.md)|Upozornění|Nepovedlo se opustit% 1.|Kanál|  
|[3303 – ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|Upozornění|V kontextu Receive došlo k chybě.|ServiceModel|  
|[3303 – ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|Informace o|% 1 byla opuštěna s výjimkou% 2.|Kanál|  
|[3305 – ClientBaseCachedChannelFactoryCount](3305-clientbasecachedchannelfactorycount.md)|Informace o|Počet továrn kanálu v mezipaměti je% 1.  Do mezipaměti lze uložit maximálně% 2 továrny kanálů.|ServiceModel|  
|[3306 – ClientBaseChannelFactoryAgedOutofCache](3306-clientbasechannelfactoryagedoutofcache.md)|Informace o|Objekt pro vytváření kanálů byl vyřazen z mezipaměti, protože mezipaměť dosáhla svého limitu% 1.|ServiceModel|  
|[3307 – ClientBaseChannelFactoryCacheHit](3307-clientbasechannelfactorycachehit.md)|Informace o|V mezipaměti byl nalezen stejný objekt pro vytváření kanálů.|ServiceModel|  
|[3308 – ClientBaseUsingLocalChannelFactory](3308-clientbaseusinglocalchannelfactory.md)|Informace o|Nepoužívá se objekt pro vytváření kanálů z mezipaměti, tj. ukládání do mezipaměti je pro instanci zakázané.|ServiceModel|  
|[3309 – QueryCompositionExecuted](3309-querycompositionexecuted.md)|Informace o|Bylo provedeno složení dotazu s použitím% 1 pro identifikátor URI požadavku:% 2.|ServiceModel|  
|[3310 – DispatchFailed](3310-dispatchfailed.md)|Chyba|Operace% 1 byla odeslána s chybami.|ServiceModel|  
|[3311 – DispatchSuccessful](3311-dispatchsuccessful.md)|Informace o|Operace% 1 byla úspěšně odeslána.|ServiceModel|  
|[3312 – MessageReadByEncoder](3312-messagereadbyencoder.md)|Informace o|Kodér přečetl zprávu o velikosti% 1 bajtů.|Kanál|  
|[3312 – MessageReadByEncoder](3312-messagereadbyencoder.md)|Informace o|Kodér zapsal zprávu o velikosti% 1 bajtů.|Kanál|  
|[3314 – SessionIdleTimeout](3314-sessionidletimeout.md)|Chyba|Přerušení relace pro nečinný kanál na identifikátor URI:% 1.|ServiceModel|  
|[3319 – SocketAcceptEnqueued](3319-socketacceptenqueued.md)|Podrobnosti|Bylo zahájeno přijetí připojení.|TCP|  
|[3320 – SocketAccepted](3320-socketaccepted.md)|Podrobnosti|Naslouchací proces listenerid:% 1 přijal soket socketid:% 2.|TCP|  
|[3321 – ConnectionPoolMiss](3321-connectionpoolmiss.md)|Podrobnosti|Fond pro% 1 nemá k dispozici žádné připojení a zaneprázdněná připojení% 2.|Kanál|  
|[3322 – DispatchFormatterDeserializeRequestStart](3322-dispatchformatterdeserializerequeststart.md)|Podrobnosti|Dispečer zahájil deserializaci zprávy s požadavkem.|ServiceModel|  
|[3323 – DispatchFormatterDeserializeRequestStop](3323-dispatchformatterdeserializerequeststop.md)|Podrobnosti|Dispečer dokončil deserializaci zprávy s požadavkem.|ServiceModel|  
|[3324 – DispatchFormatterSerializeReplyStart](3324-dispatchformatterserializereplystart.md)|Podrobnosti|Dispečer zahájil serializaci zprávy s odpovědí.|ServiceModel|  
|[3325 – DispatchFormatterSerializeReplyStop](3325-dispatchformatterserializereplystop.md)|Podrobnosti|Dispečer dokončil serializaci zprávy s odpovědí.|ServiceModel|  
|[3326 – ClientFormatterSerializeRequestStart](3326-clientformatterserializerequeststart.md)|Podrobnosti|Byla zahájena serializace požadavku klienta.|ServiceModel|  
|[3327 – ClientFormatterSerializeRequestStop](3327-clientformatterserializerequeststop.md)|Podrobnosti|Klient dokončil serializaci zprávy s požadavkem.|ServiceModel|  
|[3328 – ClientFormatterDeserializeReplyStart](3328-clientformatterdeserializereplystart.md)|Podrobnosti|Klient zahájil deserializaci zprávy s odpovědí.|ServiceModel|  
|[3329 – ClientFormatterDeserializeReplyStop](3329-clientformatterdeserializereplystop.md)|Podrobnosti|Klient dokončil deserializaci zprávy s odpovědí.|ServiceModel|  
|[3330 – SecurityNegotiationStart](3330-securitynegotiationstart.md)|Podrobnosti|Bylo zahájeno vyjednávání zabezpečení.|Zabezpečení|  
|[3331 – SecurityNegotiationStop](3331-securitynegotiationstop.md)|Podrobnosti|Vyjednávání zabezpečení bylo dokončeno.|Zabezpečení|  
|[3332 – SecurityTokenProviderOpened](3332-securitytokenprovideropened.md)|Podrobnosti|Otevírání poskytovatel SecurityTokenProvider bylo dokončeno.|Zabezpečení|  
|[3333 – OutgoingMessageSecured](3333-outgoingmessagesecured.md)|Podrobnosti|Odchozí zpráva byla zabezpečena.|Zabezpečení|  
|[3334 – IncomingMessageVerified](3334-incomingmessageverified.md)|Podrobnosti|Příchozí zpráva byla ověřena.|ServiceModel pro zabezpečení|  
|[3335 – GetServiceInstanceStart](3335-getserviceinstancestart.md)|Podrobnosti|Bylo zahájeno načítání instance služby.|ServiceModel|  
|[3336 – GetServiceInstanceStop](3336-getserviceinstancestop.md)|Podrobnosti|Instance služby byla načtena.|ServiceModel|  
|[3337 – ChannelReceiveStart](3337-channelreceivestart.md)|Podrobnosti|Obslužná rutina channelhandlerid:% 1-byla zahájena smyčka příjmu zpráv.|Kanál|  
|[3338 – ChannelReceiveStop](3338-channelreceivestop.md)|Podrobnosti|Obslužná rutina channelhandlerid:% 1-byla zastavena smyčka příjmu zpráv.|Kanál|  
|[3339 – ChannelFactoryCreated](3339-channelfactorycreated.md)|Podrobnosti|Byl vytvořen objekt ChannelFactory.|ServiceModel|  
|[3340 – PipeConnectionAcceptStart](3340-pipeconnectionacceptstart.md)|Podrobnosti|Bylo zahájeno přijetí připojení kanálu na% 1.|Kanál|  
|[3341 – PipeConnectionAcceptStop](3341-pipeconnectionacceptstop.md)|Podrobnosti|Bylo přijato připojení kanálu.|Kanál|  
|[3342 – EstablishConnectionStart](3342-establishconnectionstart.md)|Podrobnosti|Bylo zahájeno vytváření připojení pro% 1.|Kanál|  
|[3343 – EstablishConnectionStop](3343-establishconnectionstop.md)|Podrobnosti|Připojení bylo vytvořeno.|Kanál|  
|[3345 – SessionPreambleUnderstood](3345-sessionpreambleunderstood.md)|Podrobnosti|Preambule relace pro% 1 byla rozpoznána.|Kanál|  
|[3346 – ConnectionReaderSendFault](3346-connectionreadersendfault.md)|Chyba|Čtecí modul připojení odesílá chybu% 1.|Kanál|  
|[3347 – SocketAcceptClosed](3347-socketacceptclosed.md)|Podrobnosti|Bylo zavřeno přijetí soketu.|TCP|  
|[3348 – ServiceHostFaulted](3348-servicehostfaulted.md)|Kritická|V hostiteli služby došlo k chybě.|TCP|  
|[3349 – ListenerOpenStart](3349-listeneropenstart.md)|Podrobnosti|Probíhá spuštění naslouchacího procesu pro '% 1 '.|Kanál|  
|[3350 – ListenerOpenStop](3350-listeneropenstop.md)|Podrobnosti|Spuštění naslouchacího procesu bylo dokončeno.|Kanál|  
|[3351 – ServerMaxPooledConnectionsQuotaReached](3351-servermaxpooledconnectionsquotareached.md)|Podrobnosti|Dosáhlo se maximální kvóty pro připojení ve fondu.|Přidělení|  
|[3352 – TcpConnectionTimedOut](3352-tcpconnectiontimedout.md)|Chyba|Soket socketid:% 1 na vzdálenou adresu% 2 vypršel časový limit.|TCP|  
|[3353 – TcpConnectionResetError](3353-tcpconnectionreseterror.md)|Upozornění|Soket socketid:% 1 na vzdálenou adresu% 2 došlo k chybě resetování připojení.|TCP|  
|[3354 – ServiceSecurityNegotiationCompleted](3354-servicesecuritynegotiationcompleted.md)|Podrobnosti|Vyjednávání zabezpečení služby bylo dokončeno.|Zabezpečení|  
|[3355 – SecurityNegotiationProcessingFailure](3355-securitynegotiationprocessingfailure.md)|Chyba|Zpracování vyjednávání zabezpečení se nezdařilo.|Zabezpečení|  
|[3356 – SecurityIdentityVerificationSuccess](3356-securityidentityverificationsuccess.md)|Podrobnosti|Ověření zabezpečení se zdařilo.|Zabezpečení|  
|[3357 – SecurityIdentityVerificationFailure](3357-securityidentityverificationfailure.md)|Chyba|Ověření zabezpečení se nezdařilo.|Zabezpečení|  
|[3358 – PortSharingDuplicatedSocket](3358-portsharingduplicatedsocket.md)|Podrobnosti|Byl duplikován soket pro% 1.|ActivationServices|  
|[3359 – SecurityImpersonationSuccess](3359-securityimpersonationsuccess.md)|Podrobnosti|Zosobnění zabezpečení se zdařilo.|Zabezpečení|  
|[3360 – SecurityImpersonationFailure](3360-securityimpersonationfailure.md)|Upozornění|Zosobnění zabezpečení se nezdařilo.|Zabezpečení|  
|[3361 – HttpChannelRequestAborted](3361-httpchannelrequestaborted.md)|Upozornění|Požadavek kanálu HTTP byl přerušen.|HTTP|  
|[3362 – HttpChannelResponseAborted](3362-httpchannelresponseaborted.md)|Upozornění|Odpověď kanálu http byla přerušena.|HTTP|  
|[3363 – HttpAuthFailed](3363-httpauthfailed.md)|Upozornění|Ověření protokolu HTTP se nezdařilo.|HTTP|  
|[3364 – SharedListenerProxyRegisterStart](3364-sharedlistenerproxyregisterstart.md)|Podrobnosti|Byla zahájena registrace objektu sharedlistenerproxy pro identifikátor URI% 1.|ActivationServices|  
|[3365 – SharedListenerProxyRegisterStop](3365-sharedlistenerproxyregisterstop.md)|Podrobnosti|Zastavování registru objektu sharedlistenerproxy|ActivationServices|  
|[3366 – SharedListenerProxyRegisterFailed](3366-sharedlistenerproxyregisterfailed.md)|Chyba|Registrace objektu sharedlistenerproxy se nezdařila se stavem% 1.|ActivationServices|  
|[3367 – ConnectionPoolPreambleFailed](3367-connectionpoolpreamblefailed.md)|Chyba|ConnectionPoolPreambleFailed.|Kanál|  
|[3368 – SslOnInitiateUpgrade](3368-ssloninitiateupgrade.md)|Podrobnosti|SslOnAcceptUpgradeStart|Zabezpečení|  
|[3369 – SslOnAcceptUpgrade](3369-sslonacceptupgrade.md)|Podrobnosti|SslOnAcceptUpgradeStop|Zabezpečení|  
|[3370 – BinaryMessageEncodingStart](3370-binarymessageencodingstart.md)|Podrobnosti|Kodér BinaryMessageEncoder zahájil zahájil kódování zprávy.|Kanál|  
|[3371 – MtomMessageEncodingStart](3371-mtommessageencodingstart.md)|Podrobnosti|Kodér mtommessageencoder zahájil zahájil kódování zprávy.|Kanál|  
|[3372 – TextMessageEncodingStart](3372-textmessageencodingstart.md)|Podrobnosti|Kodér textmessageencoder zahájil zahájil kódování zprávy.|Kanál|  
|[3373 – BinaryMessageDecodingStart](3373-binarymessagedecodingstart.md)|Podrobnosti|Kodér BinaryMessageEncoder zahájil zahájil dekódování zprávy.|Kanál|  
|[3374 – MtomMessageDecodingStart](3374-mtommessagedecodingstart.md)|Podrobnosti|Kodér mtommessageencoder zahájil zahájil dekódování zprávy.|Kanál|  
|[3375 – TextMessageDecodingStart](3375-textmessagedecodingstart.md)|Podrobnosti|Kodér textmessageencoder zahájil zahájil dekódování zprávy.|Kanál|  
|[3376 – HttpResponseReceiveStart](3376-httpresponsereceivestart.md)|Informace o|Přenos HTTP zahájil příjem zprávy.|HTTP|  
|[3377 – SocketReadStop](3377-socketreadstop.md)|Podrobnosti|Soket socketid:% 1 přečte% 2 bajtů přečtených z% 3.|TCP|  
|[3378 – SocketAsyncReadStop](3378-socketasyncreadstop.md)|Podrobnosti|Soket socketid:% 1 přečte% 2 bajtů přečtených z% 3.|TCP|  
|[3379 – SocketWriteStart](3379-socketwritestart.md)|Podrobnosti|Soket socketid:% 1 zapisuje% 2 bajtů do% 3.|TCP|  
|[3380 – SocketAsyncWriteStart](3380-socketasyncwritestart.md)|Podrobnosti|Soket socketid:% 1 zapisuje% 2 bajtů do% 3.|TCP|  
|[3381 – SequenceAcknowledgementSent](3381-sequenceacknowledgementsent.md)|Podrobnosti|Bylo odesláno potvrzení relace SessionId% 1.|Kanál|  
|[3382 – ClientReliableSessionReconnect](3382-clientreliablesessionreconnect.md)|Informace o|Probíhá opětovné připojení relace SessionId% 1.|Kanál|  
|[3383 – ReliableSessionChannelFaulted](3383-reliablesessionchannelfaulted.md)|Informace o|V relaci SessionId% 1 došlo k chybě.|Kanál|  
|[3384 – WindowsStreamSecurityOnInitiateUpgrade](3384-windowsstreamsecurityoninitiateupgrade.md)|Podrobnosti|Zabezpečení windowsstreamsecurity zahajuje se upgrade zabezpečení.|Zabezpečení|  
|[3385 – WindowsStreamSecurityOnAcceptUpgrade](3385-windowsstreamsecurityonacceptupgrade.md)|Podrobnosti|Zabezpečení Windows streamování při přijetí upgradu|Zabezpečení|  
|[3386 – SocketConnectionAbort](3386-socketconnectionabort.md)|Upozornění|Soket socketid:% 1 se přerušuje.|TCP|  
|[3388 – HttpGetContextStart](3388-httpgetcontextstart.md)|Podrobnosti|Zahájení kontextu httpgetcontext Start.|HTTP|  
|[3389 – ClientSendPreambleStart](3389-clientsendpreamblestart.md)|Podrobnosti|Bylo zahájeno odesílání preambule klienta.|Kanál|  
|[3390 – ClientSendPreambleStop](3390-clientsendpreamblestop.md)|Podrobnosti|Bylo ukončeno odesílání preambule klienta.|Kanál|  
|[3391 – HttpMessageReceiveFailed](3391-httpmessagereceivefailed.md)|Upozornění|Přijetí zprávy HTTP se nezdařilo.|HTTP|  
|[3392 – TransactionScopeCreate](3392-transactionscopecreate.md)|Informace o|Vytváří se objekt TransactionScope s identifikátorem LocalIdentifier:% 1 a distribuovaného identifikátoru DistributedIdentifier:% 2.|ServiceModel|  
|[3393 – StreamedMessageReadByEncoder](3393-streamedmessagereadbyencoder.md)|Informace o|Kodér přečetl datový proud zprávy.|Kanál|  
|[3394 – StreamedMessageWrittenByEncoder](3394-streamedmessagewrittenbyencoder.md)|Informace o|Kodér zapsal datový proud zprávy.|Kanál|  
|[3395 – MessageWrittenAsynchronouslyByEncoder](3395-messagewrittenasynchronouslybyencoder.md)|Informace o|Kodér asynchronně zapsal zprávu.|Kanál|  
|[3396 – BufferedAsyncWriteStart](3396-bufferedasyncwritestart.md)|Informace o|Vyrovnávací paměť BufferId:% 1 dokončil zápis% 2 bajtů do základního datového proudu.|Kanál|  
|[3397 – BufferedAsyncWriteStop](3397-bufferedasyncwritestop.md)|Informace o|Kodér asynchronně zapsal zprávu.|Kanál|  
|[3398 – PipeSharedMemoryCreated](3398-pipesharedmemorycreated.md)|Podrobnosti|Sdílená paměť kanálu byla vytvořena v '% 1 '.|Kanál|  
|[3399 – NamedPipeCreated](3399-namedpipecreated.md)|Podrobnosti|Pojmenovaný kanál '% 1 ' byl vytvořen.|Kanál|  
|[3401 – SignatureVerificationStart](3401-signatureverificationstart.md)|Podrobnosti|Bylo zahájeno ověřování podpisu.|Zabezpečení|  
|[3402 – SignatureVerificationSuccess](3402-signatureverificationsuccess.md)|Podrobnosti|Ověření podpisu bylo úspěšné.|Zabezpečení|  
|[3403 – WrappedKeyDecryptionStart](3403-wrappedkeydecryptionstart.md)|Podrobnosti|Bylo zahájeno dešifrování zabaleného klíče.|Zabezpečení|  
|[3404 – WrappedKeyDecryptionSuccess](3404-wrappedkeydecryptionsuccess.md)|Podrobnosti|Dešifrování zabaleného klíče proběhlo úspěšně.|Zabezpečení|  
|[3405 – EncryptedDataProcessingStart](3405-encrypteddataprocessingstart.md)|Podrobnosti|Bylo zahájeno šifrované zpracování dat.|Zabezpečení|  
|[3406 – EncryptedDataProcessingSuccess](3406-encrypteddataprocessingsuccess.md)|Podrobnosti|Šifrované zpracování dat bylo úspěšné.|Zabezpečení|  
|[3407 – HttpPipelineProcessInboundRequestStart](3407-httppipelineprocessinboundrequeststart.md)|Podrobnosti|Obslužná rutina zprávy HTTP zahájila zpracování příchozího požadavku.|HTTP|  
|[3408 – HttpPipelineBeginProcessInboundRequestStart](3408-httppipelinebeginprocessinboundrequeststart.md)|Podrobnosti|Obslužná rutina zprávy HTTP zahájila asynchronní zpracování příchozího požadavku.|HTTP|  
|[3409 – HttpPipelineProcessInboundRequestStop](3409-httppipelineprocessinboundrequeststop.md)|Podrobnosti|Obslužná rutina zprávy HTTP dokončila zpracování příchozího požadavku.|HTTP|  
|[3410 – HttpPipelineFaulted](3410-httppipelinefaulted.md)|Upozornění|Obslužná rutina zprávy HTTP skončila chybou.|HTTP|  
|[3411 – HttpPipelineTimeoutException](3411-httppipelinetimeoutexception.md)|Chyba|Vypršel časový limit připojení soketu WebSocket.|HTTP|  
|[3412 – HttpPipelineProcessResponseStart](3412-httppipelineprocessresponsestart.md)|Podrobnosti|Obslužná rutina zprávy HTTP zahájila zpracování odpovědi.|HTTP|  
|[3413 – HttpPipelineBeginProcessResponseStart](3413-httppipelinebeginprocessresponsestart.md)|Podrobnosti|Obslužná rutina zprávy HTTP zahájila asynchronní zpracování odpovědi.|HTTP|  
|[3414 – HttpPipelineProcessResponseStop](3414-httppipelineprocessresponsestop.md)|Podrobnosti|Obslužná rutina zprávy HTTP dokončila zpracování odpovědi.|HTTP|  
|[3415 – WebSocketConnectionRequestSendStart](3415-websocketconnectionrequestsendstart.md)|Podrobnosti|Bylo zahájeno odesílání požadavku na připojení soketu WebSocket příjemci% 1.|HTTP|  
|[3416 – WebSocketConnectionRequestSendStop](3416-websocketconnectionrequestsendstop.md)|Podrobnosti|Požadavek na připojení soketu WebSocketId% 1 byl odeslán.|HTTP|  
|[3417 – WebSocketConnectionAcceptStart](3417-websocketconnectionacceptstart.md)|Podrobnosti|Bylo zahájeno přijímání připojení soketu WebSocket.|HTTP|  
|[3418 – WebSocketConnectionAccepted](3418-websocketconnectionaccepted.md)|Podrobnosti|Připojení soketu WebSocketId% 1 bylo přijato.|HTTP|  
|[3419 – WebSocketConnectionDeclined](3419-websocketconnectiondeclined.md)|Chyba|Připojení soketu WebSocket bylo odmítnuto se stavovým kódem% 1.|HTTP|  
|[3420 – WebSocketConnectionFailed](3420-websocketconnectionfailed.md)|Chyba|Požadavek na připojení soketu WebSocket se nezdařil:% 1|HTTP|  
|[3421 – WebSocketConnectionAborted](3421-websocketconnectionaborted.md)|Chyba|Připojení soketu WebSocketId% 1 bylo přerušeno.|HTTP|  
|[3422 – WebSocketAsyncWriteStart](3422-websocketasyncwritestart.md)|Podrobnosti|Soket WebSocketId% 1 zapisuje% 2 bajtů do:% 3|HTTP|  
|[3423 – WebSocketAsyncWriteStop](3423-websocketasyncwritestop.md)|Podrobnosti|Asynchronní zápis v soketu WebSocketId% 1 byl ukončen.|HTTP|  
|[3424 – WebSocketAsyncReadStart](3424-websocketasyncreadstart.md)|Podrobnosti|Bylo zahájeno čtení z soketu WebSocketId% 1.|HTTP|  
|[3425 – WebSocketAsyncReadStop](3425-websocketasyncreadstop.md)|Podrobnosti|Soket WebSocketId% 1 přečetl% 2 bajtů z% 3.|HTTP|  
|[3426 – WebSocketCloseSent](3426-websocketclosesent.md)|Podrobnosti|Soket WebSocketId% 1 odesílá zprávu ukončení do objektu% 2 s koncovým stavem% 3.|HTTP|  
|[3427 – WebSocketCloseOutputSent](3427-websocketcloseoutputsent.md)|Podrobnosti|Soket WebSocketId% 1 odesílá zprávu ukončení výstupu do% 2 s ukončovacím stavem% 3.|HTTP|  
|[3428 – WebSocketConnectionClosed](3428-websocketconnectionclosed.md)|Podrobnosti|Připojení soketu WebSocketId% 1 bylo ukončeno.|HTTP|  
|[3429 – WebSocketCloseStatusReceived](3429-websocketclosestatusreceived.md)|Podrobnosti|Soket WebSocketId% 1 přijal zprávu ukončení připojení se stavem% 2.|HTTP|  
|[3430 – WebSocketUseVersionFromClientWebSocketFactory](3430-websocketuseversionfromclientwebsocketfactory.md)|Podrobnosti|Použití hodnota WebSocketVersion z objektu WebSocket typu '% 1 ' klienta.|HTTP|  
|[3431 – WebSocketCreateClientWebSocketWithFactory](3431-websocketcreateclientwebsocketwithfactory.md)|Podrobnosti|Vytváření objektu WebSocket pro klienta s továrnou typu% 1.|HTTP|  
|[3553 – XamlServicesLoadStart](3553-xamlservicesloadstart.md)|Informace o|Metody xamlservicesload Start|WebHost|  
|[3554 – XamlServicesLoadStop](3554-xamlservicesloadstop.md)|Informace o|XamlServicesLoad Stop|WebHost|  
|[3555 – CreateWorkflowServiceHostStart](3555-createworkflowservicehoststart.md)|Informace o|Metody CreateWorkflowServiceHost Start|WebHost|  
|[3556 – CreateWorkflowServiceHostStop](3556-createworkflowservicehoststop.md)|Informace o|Zastavení metody CreateWorkflowServiceHost|WebHost|  
|[3558 – ServiceActivationStart](3558-serviceactivationstart.md)|Informace o|Zahájení aktivace služby|WebHost|  
|[3559 – ServiceActivationStop](3559-serviceactivationstop.md)|Informace o|Zastavení aktivace služby|WebHost|  
|[3560 – ServiceActivationAvailableMemory](3560-serviceactivationavailablememory.md)|Podrobnosti|Dostupná paměť (bajty):% 1|Přidělení|  
|[3800 – RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|Informace o|Směrovací služba zavírá klienta% 1.|RoutingServices|  
|[3800 – RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|Upozornění|V klientovi směrovací služby% 1 došlo k chybě.|RoutingServices|  
|[3802 – RoutingServiceCompletingOneWay](3802-routingservicecompletingoneway.md)|Informace o|Jednosměrná zpráva směrovací služby se dokončuje.|RoutingServices|  
|[3803 – RoutingServiceProcessingFailure](3803-routingserviceprocessingfailure.md)|Chyba|Směrovací službě se nepodařilo zpracovat zprávu na koncovém bodu s adresou% 1.|RoutingServices|  
|[3804 – RoutingServiceCreatingClientForEndpoint](3804-routingservicecreatingclientforendpoint.md)|Informace o|Směrovací služba vytváří klienta pro koncový bod:% 1.|RoutingServices|  
|[3805 – RoutingServiceDisplayConfig](3805-routingservicedisplayconfig.md)|Podrobnosti|Směrovací služba je nakonfigurovaná s hodnotami RouteOnHeadersOnly:% 1, SoapProcessingEnabled:% 2, EnsureOrderedDispatch:% 3.|RoutingServices|  
|[3807 – RoutingServiceCompletingTwoWay](3807-routingservicecompletingtwoway.md)|Informace o|Probíhá ukončování zprávy s odpovědí na žádost směrovací služby.|RoutingServices|  
|[3809 – RoutingServiceMessageRoutedToEndpoints](3809-routingservicemessageroutedtoendpoints.md)|Podrobnosti|Směrovací služba směrovala zprávu s ID:% 1 do seznamu koncových bodů% 2.|RoutingServices|  
|[3810 – RoutingServiceConfigurationApplied](3810-routingserviceconfigurationapplied.md)|Informace o|Pro směrovací službu se nastavil nový konfigurace RoutingConfiguration.|RoutingServices|  
|[3815 – RoutingServiceProcessingMessage](3815-routingserviceprocessingmessage.md)|Informace o|Směrovací služba zpracovává zprávu s ID:% 1, akce:% 2, příchozí URL:% 3, přijato v transakci:% 4.|RoutingServices|  
|[3816 – RoutingServiceTransmittingMessage](3816-routingservicetransmittingmessage.md)|Informace o|Směrovací služba přenáší zprávu s ID:% 1 [operace% 2] do% 3.|RoutingServices|  
|[3817 – RoutingServiceCommittingTransaction](3817-routingservicecommittingtransaction.md)|Informace o|Směrovací služba potvrzuje transakci s ID:% 1.|RoutingServices|  
|[3818 – RoutingServiceDuplexCallbackException](3818-routingserviceduplexcallbackexception.md)|Chyba|Komponenta směrovací služby% 1 zjistila výjimku duplexního zpětného volání.|RoutingServices|  
|[3819 – RoutingServiceMovedToBackup](3819-routingservicemovedtobackup.md)|Informace o|Zpráva směrovací služby s ID:% 1 [operace% 2] byla přesunuta do záložního koncového bodu% 3.|RoutingServices|  
|[3820 – RoutingServiceCreatingTransaction](3820-routingservicecreatingtransaction.md)|Informace o|Směrovací služba vytvořila novou transakci s ID% 1 pro zpracování zpráv.|RoutingServices|  
|[3821 – RoutingServiceCloseFailed](3821-routingserviceclosefailed.md)|Upozornění|Směrovací služba selhala při zavírání odchozího klienta% 1.|RoutingServices|  
|[3822 – RoutingServiceSendingResponse](3822-routingservicesendingresponse.md)|Informace o|Směrovací služba posílá zpět zprávu odpovědi s akcí% 1.|RoutingServices|  
|[3823 – RoutingServiceSendingFaultResponse](3823-routingservicesendingfaultresponse.md)|Upozornění|Směrovací služba odesílá zpět zprávu chybové odpovědi s akcí% 1.|RoutingServices|  
|[3824 – RoutingServiceCompletingReceiveContext](3824-routingservicecompletingreceivecontext.md)|Podrobnosti|Směrovací služba volá metodu ReceiveContext. Complete pro zprávu s ID:% 1.|RoutingServices|  
|[3825 – RoutingServiceAbandoningReceiveContext](3825-routingserviceabandoningreceivecontext.md)|Upozornění|Směrovací služba volá metodu ReceiveContext. Abandon pro zprávu s ID:% 1.|RoutingServices|  
|[3826 – RoutingServiceUsingExistingTransaction](3826-routingserviceusingexistingtransaction.md)|Podrobnosti|Směrovací služba bude odesílat zprávy pomocí existující transakce% 1.|RoutingServices|  
|[3827 – RoutingServiceTransmitFailed](3827-routingservicetransmitfailed.md)|Upozornění|Směrovací službě se nepodařilo odeslat do '% 1 '.|RoutingServices|  
|[3828 – RoutingServiceFilterTableMatchStart](3828-routingservicefiltertablematchstart.md)|Informace o|Služba směrování MessageFilterTable – začátek shody|RoutingServices|  
|[3829 – RoutingServiceFilterTableMatchStop](3829-routingservicefiltertablematchstop.md)|Informace o|Služba směrování MessageFilterTable se zastavila.|RoutingServices|  
|[3830 – RoutingServiceAbortingChannel](3830-routingserviceabortingchannel.md)|Podrobnosti|Směrovací služba volá přerušení na kanálu:% 1.|RoutingServices|  
|[3831 – RoutingServiceHandledException](3831-routingservicehandledexception.md)|Podrobnosti|Směrovací služba zpracovala výjimku.|RoutingServices|  
|[3832 – RoutingServiceTransmitSucceeded](3832-routingservicetransmitsucceeded.md)|Informace o|Služba Směrování úspěšně přenesla zprávu s ID:% 1 [operace% 2] do% 3.|RoutingServices|  
|[4001 – TransportListenerSessionsReceived](4001-transportlistenersessionsreceived.md)|Podrobnosti|Byla přijata relace naslouchacího procesu přenosu prostřednictvím% 1.|ActivationServices|  
|[4002 – FailFastException](4002-failfastexception.md)|Kritická|FailFastException.|ActivationServices|  
|[4003 – ServiceStartPipeError](4003-servicestartpipeerror.md)|Chyba|Chyba kanálu při spuštění služby.|ActivationServices|  
|[4008 – DispatchSessionStart](4008-dispatchsessionstart.md)|Podrobnosti|Bylo zahájeno odesílání relace.|ActivationServices|  
|[4008 – DispatchSessionStart](4008-dispatchsessionstart.md)|Upozornění|Odeslání relace pro% 1 se nezdařilo, protože fronta čekajících relací je plná s% 2 čekajícími položkami.|ActivationServices|  
|[4011 – MessageQueueRegisterStart](4011-messagequeueregisterstart.md)|Podrobnosti|Registrace fronty zpráv byla zahájena.|ActivationServices|  
|[4012 – MessageQueueRegisterAbort](4012-messagequeueregisterabort.md)|Chyba|Registrace fronty zpráv byla přerušena se stavem% 1 pro identifikátor URI:% 2.|ActivationServices|  
|[4013 – MessageQueueUnregisterSucceeded](4013-messagequeueunregistersucceeded.md)|Podrobnosti|Zrušení registrace fronty zpráv se zdařilo pro identifikátor URI:% 1.|ActivationServices|  
|[4014 – MessageQueueRegisterFailed](4014-messagequeueregisterfailed.md)|Chyba|Registrace fronty zpráv pro identifikátor URI% 1 se nezdařila se stavem% 2.|ActivationServices|  
|[4015 – MessageQueueRegisterCompleted](4015-messagequeueregistercompleted.md)|Informace o|Registrace fronty zpráv pro identifikátor URI% 1 byla dokončena.|ActivationServices|  
|[4016 – MessageQueueDuplicatedSocketError](4016-messagequeueduplicatedsocketerror.md)|Chyba|Při duplikaci soketu ve frontě zpráv došlo k chybě.|ActivationServices|  
|[4019 – MessageQueueDuplicatedSocketComplete](4019-messagequeueduplicatedsocketcomplete.md)|Podrobnosti|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 – TcpTransportListenerListeningStart](4020-tcptransportlistenerlisteningstart.md)|Podrobnosti|Naslouchací proces přenosu protokolu TCP zahájil naslouchání na identifikátoru URI:% 1.|ActivationServices|  
|[4021 – TcpTransportListenerListeningStop](4021-tcptransportlistenerlisteningstop.md)|Podrobnosti|Naslouchací proces přenosu protokolu TCP naslouchá.|ActivationServices|  
|[4022 – WebhostUnregisterProtocolFailed](4022-webhostunregisterprotocolfailed.md)|Chyba|Kód chyby:% 1|ActivationServices|  
|[4023 – WasCloseAllListenerChannelInstancesCompleted](4023-wasclosealllistenerchannelinstancescompleted.md)|Informace o|Bylo ukončeno všechny instance kanálů naslouchacího procesu.|ActivationServices|  
|[4024 – WasCloseAllListenerChannelInstancesFailed](4024-wasclosealllistenerchannelinstancesfailed.md)|Chyba|Kód chyby:% 1|ActivationServices|  
|[4025 – OpenListenerChannelInstanceFailed](4025-openlistenerchannelinstancefailed.md)|Chyba|Kód chyby:% 1|ActivationServices|  
|[4026 – WasConnected](4026-wasconnected.md)|Podrobnosti|BYL připojen.|ActivationServices|  
|[4027 – WasDisconnected](4027-wasdisconnected.md)|Podrobnosti|BYL odpojen.|ActivationServices|  
|[4028 – PipeTransportListenerListeningStart](4028-pipetransportlistenerlisteningstart.md)|Podrobnosti|Naslouchací proces přenosu kanálu naslouchá od spuštění v identifikátoru URI:% 1.|ActivationServices|  
|[4029 – PipeTransportListenerListeningStop](4029-pipetransportlistenerlisteningstop.md)|Podrobnosti|Naslouchací proces přenosu kanálu ukončil naslouchání.|ActivationServices|  
|[4030 – DispatchSessionSuccess](4030-dispatchsessionsuccess.md)|Informace o|Odeslání relace se zdařilo.|ActivationServices|  
|[4031 – DispatchSessionFailed](4031-dispatchsessionfailed.md)|Chyba|Odeslání relace se nezdařilo.|ActivationServices|  
|[4032 – WasConnectionTimedout](4032-wasconnectiontimedout.md)|Kritická|Vypršel časový limit připojení.|ActivationServices|  
|[4033 – RoutingTableLookupStart](4033-routingtablelookupstart.md)|Podrobnosti|Bylo zahájeno prohledávání směrovací tabulky.|ActivationServices|  
|[4034 – RoutingTableLookupStop](4034-routingtablelookupstop.md)|Podrobnosti|Prohledávání směrovací tabulky bylo dokončeno.|ActivationServices|  
|[4035 – PendingSessionQueueRatio](4035-pendingsessionqueueratio.md)|Podrobnosti|Poměr fronty nedokončených relací:% 1/% 2|Přidělení|  
|[4600 – MessageLogEventSizeExceeded](4600-messagelogeventsizeexceeded.md)|Upozornění|Zprávu se nepodařilo zaznamenat do protokolu, protože přesahuje velikost události ETW.|WCFMessageLogging|  
|[4801 – DiscoveryClientInClientChannelFailedToClose](4801-discoveryclientinclientchannelfailedtoclose.md)|Upozornění|Objektem DiscoveryClient zahozena vytvořené uvnitř DiscoveryClientChannel se nepovedlo zavřít, a proto se přerušilo.|Zjišťování|  
|[4802 – DiscoveryClientProtocolExceptionSuppressed](4802-discoveryclientprotocolexceptionsuppressed.md)|Informace o|Při zavírání objektem DiscoveryClient zahozena došlo k potlačení ProtocolException. Důvodem může být to, že služba DiscoveryService se stále snaží odeslat odpověď objektem DiscoveryClient zahozena.|Zjišťování|  
|[4803 – DiscoveryClientReceivedMulticastSuppression](4803-discoveryclientreceivedmulticastsuppression.md)|Informace o|Objektem DiscoveryClient zahozena přijal z objektu DiscoveryProxy zprávu o potlačení vícesměrového vysílání.|Zjišťování|  
|[4804 – DiscoveryMessageReceivedAfterOperationCompleted](4804-discoverymessagereceivedafteroperationcompleted.md)|Informace o|Zpráva% 1 s parametrem messageId =% 2 byla zahozena objektem DiscoveryClient zahozena, protože byla dokončena odpovídající operace% 3.|Zjišťování|  
|[4805 – DiscoveryMessageWithInvalidContent](4805-discoverymessagewithinvalidcontent.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 byla zahozena, protože její obsah byl neplatný.|Zjišťování|  
|[4806 – DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 a relatesTo =% 3 byla vynechána objektem DiscoveryClient zahozena, protože buď byla dokončena odpovídající operace% 4, nebo hodnota relatesTo není platná.|Zjišťování|  
|[4807 – DiscoveryMessageWithInvalidReplyTo](4807-discoverymessagewithinvalidreplyto.md)|Upozornění|Zpráva požadavku na zjišťování s parametrem messageId =% 1 byla zahozena, protože obsahovala neplatnou adresu ReplyTo.|Zjišťování|  
|[4808 – DiscoveryMessageWithNoContent](4808-discoverymessagewithnocontent.md)|Upozornění|Zpráva% 1 byla zahozena, protože neměla žádný obsah.|Zjišťování|  
|[4809 – DiscoveryMessageWithNullMessageId](4809-discoverymessagewithnullmessageid.md)|Upozornění|Zpráva% 1 byla vyřazena, protože Hlavička zprávy neobsahovala požadovanou vlastnost MessageId.|Zjišťování|  
|[4810 – DiscoveryMessageWithNullMessageSequence](4810-discoverymessagewithnullmessagesequence.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 byla zahozena objektem DiscoveryClient zahozena, protože neobsahovala vlastnost DiscoveryMessageSequence.|Zjišťování|  
|[4811 – DiscoveryMessageWithNullRelatesTo](4811-discoverymessagewithnullrelatesto.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 byla zahozena objektem DiscoveryClient zahozena, protože Hlavička zprávy neobsahovala požadovanou vlastnost RelatesTo.|Zjišťování|  
|[4812 – DiscoveryMessageWithNullReplyTo](4812-discoverymessagewithnullreplyto.md)|Upozornění|Zpráva požadavku na zjišťování s parametrem messageId =% 1 byla zahozena, protože neobsahovala adresu ReplyTo.|Zjišťování|  
|[4813 – DuplicateDiscoveryMessage](4813-duplicatediscoverymessage.md)|Upozornění|Zpráva% 1 s parametrem messageId =% 2 byla zahozena, protože byla duplicitní.|Zjišťování|  
|[4814 – EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|Informace o|Zjistitelnost koncového bodu s parametry EndpointAddress =% 1 a ListenUri =% 2 byla zakázána.|Zjišťování|  
|[4814 – EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|Informace o|Zjistitelnost koncového bodu s parametry EndpointAddress =% 1 a ListenUri =% 2 byla povolena.|Zjišťování|  
|[4816 – FindInitiatedInDiscoveryClientChannel](4816-findinitiatedindiscoveryclientchannel.md)|Podrobnosti|V DiscoveryClientChannel se iniciovala operace hledání pro zjišťování koncových bodů.|Zjišťování|  
|[4817 – InnerChannelCreationFailed](4817-innerchannelcreationfailed.md)|Upozornění|DiscoveryClientChannel se nepodařilo vytvořit kanál se zjištěným koncovým bodem s parametry EndpointAddress =% 1 a Via =% 2. DiscoveryClientChannel se teď pokusí použít další dostupný zjištěný koncový bod.|Zjišťování|  
|[4818 – InnerChannelOpenFailed](4818-innerchannelopenfailed.md)|Upozornění|DiscoveryClientChannel se nepodařilo otevřít kanál se zjištěným koncovým bodem s parametry EndpointAddress =% 1 a Via =% 2. DiscoveryClientChannel se teď pokusí použít další dostupný zjištěný koncový bod.|Zjišťování|  
|[4819 – InnerChannelOpenSucceeded](4819-innerchannelopensucceeded.md)|Informace o|DiscoveryClientChannel úspěšně zjistil koncový bod a otevřel ho pomocí kanálu. Klient je připojen ke službě pomocí EndpointAddress = '% 1 ' a Via = '% 2 '.|Zjišťování|  
|[4820 – SynchronizationContextReset](4820-synchronizationcontextreset.md)|Informace o|Třída SynchronizationContext byl obnoven na původní hodnotu% 1 podle DiscoveryClientChannel.|Zjišťování|  
|[4821 – SynchronizationContextSetToNull](4821-synchronizationcontextsettonull.md)|Informace o|Před zahájením operace Find byl třída SynchronizationContext nastaven na hodnotu null od DiscoveryClientChannel.|Zjišťování|  
|[5001 – DCSerializeWithSurrogateStart](5001-dcserializewithsurrogatestart.md)|Podrobnosti|Bylo zahájeno serializace kontraktu DataContract% 1 s náhradami.|Serializace|  
|[5002 – DCSerializeWithSurrogateStop](5002-dcserializewithsurrogatestop.md)|Podrobnosti|Serializace kontraktu DataContract s náhradami byla zastavena.|Serializace|  
|[5003 – DCDeserializeWithSurrogateStart](5003-dcdeserializewithsurrogatestart.md)|Podrobnosti|Bylo zahájeno deserializace kontraktu DataContract% 1 s náhradami.|Serializace|  
|[5004 – DCDeserializeWithSurrogateStop](5004-dcdeserializewithsurrogatestop.md)|Podrobnosti|Deserializace kontraktu DataContract se zástupnými náhradami byla ukončena.|Serializace|  
|[5005 – ImportKnownTypesStart](5005-importknowntypesstart.md)|Podrobnosti|Operace importknowntypes Start.|Serializace|  
|[5006 – ImportKnownTypesStop](5006-importknowntypesstop.md)|Podrobnosti|Zastavení operace importknowntypes|Serializace|  
|[5007 – DCResolverResolve](5007-dcresolverresolve.md)|Podrobnosti|Bylo zahájeno řešení překladače kontraktu DataContract% 1.|Serializace|  
|[5008 – DCGenWriterStart](5008-dcgenwriterstart.md)|Podrobnosti|Bylo zahájeno vytváření zapisovače% 1 pro DataContract pro% 2.|Serializace|  
|[5009 – DCGenWriterStop](5009-dcgenwriterstop.md)|Podrobnosti|Ukončilo se generování zapisovače DataContract.|Serializace|  
|[5010 – DCGenReaderStart](5010-dcgenreaderstart.md)|Podrobnosti|Operace DataContract vygenerovala% 1 čtečku pro% 2 Start.|Serializace|  
|[5011 – DCGenReaderStop](5011-dcgenreaderstop.md)|Podrobnosti|Bylo ukončeno generování kontraktu DataContract.|Serializace|  
|[5012 – DCJsonGenReaderStart](5012-dcjsongenreaderstart.md)|Podrobnosti|Bylo zahájeno generování čtecího modulu JSON% 1 pro% 2.|Serializace|  
|[5013 – DCJsonGenReaderStop](5013-dcjsongenreaderstop.md)|Podrobnosti|Bylo ukončeno generování čtečky JSON.|Serializace|  
|[5014 – DCJsonGenWriterStart](5014-dcjsongenwriterstart.md)|Podrobnosti|Bylo zahájeno generování JSON% 1 zapisovače pro% 2.|Serializace|  
|[5015 – DCJsonGenWriterStop](5015-dcjsongenwriterstop.md)|Podrobnosti|Ukončilo se generování zapisovače JSON.|Serializace|  
|[5016 – GenXmlSerializableStart](5016-genxmlserializablestart.md)|Podrobnosti|Bylo zahájeno generování serializovatelného kódu XML pro% 1.|Serializace|  
|[5017 – GenXmlSerializableStop](5017-genxmlserializablestop.md)|Podrobnosti|Bylo ukončeno generování serializovatelného kódu XML.|Serializace|  
|[5203 – JsonMessageDecodingStart](5203-jsonmessagedecodingstart.md)|Podrobnosti|Kodér jsonmessageencoder zahájil zahájil dekódování zprávy.|Kanál|  
|[5204 – JsonMessageEncodingStart](5204-jsonmessageencodingstart.md)|Podrobnosti|Kodér jsonmessageencoder zahájil zahájil kódování zprávy.|Kanál|  
|[5402 – TokenValidationStarted](5402-tokenvalidationstarted.md)|Podrobnosti|Bylo zahájeno ověřování tokenu SecurityToken (typ% 1 a ID% 2).|Zabezpečení|  
|[5403 – TokenValidationSuccess](5403-tokenvalidationsuccess.md)|Podrobnosti|Ověření tokenu SecurityToken (typ% 1 a ID% 2) se zdařilo.|Zabezpečení|  
|[5404 – TokenValidationFailure](5404-tokenvalidationfailure.md)|Chyba|Ověření tokenu SecurityToken (typ% 1 a ID% 2) se nezdařilo. %3|Zabezpečení|  
|[5405 – GetIssuerNameSuccess](5405-getissuernamesuccess.md)|Podrobnosti|Načtení názvu vystavitele:% 1 z tokenu tokenId:% 2 bylo úspěšné.|Zabezpečení|  
|[5406 – GetIssuerNameFailure](5406-getissuernamefailure.md)|Chyba|Načtení názvu vystavitele z tokenu tokenId:% 1 se nezdařilo.|Zabezpečení|  
|[5600 – FederationMessageProcessingStarted](5600-federationmessageprocessingstarted.md)|Podrobnosti|Začalo zpracování federační zprávy.|Zabezpečení|  
|[5601 – FederationMessageProcessingSuccess](5601-federationmessageprocessingsuccess.md)|Podrobnosti|Zpracování federační zprávy bylo úspěšné.|Zabezpečení|  
|[5602 – FederationMessageCreationStarted](5602-federationmessagecreationstarted.md)|Podrobnosti|Bylo zahájeno vytváření federační zprávy z odeslaného formuláře.|Zabezpečení|  
|[5603 – FederationMessageCreationSuccess](5603-federationmessagecreationsuccess.md)|Podrobnosti|Vytváření federační zprávy z odeslaného formuláře se zdařilo.|Zabezpečení|  
|[5604 – SessionCookieReadingStarted](5604-sessioncookiereadingstarted.md)|Podrobnosti|Bylo zahájeno načítání tokenu relace ze souboru cookie relace.|Zabezpečení|  
|[5605 – SessionCookieReadingSuccess](5605-sessioncookiereadingsuccess.md)|Podrobnosti|Čtení tokenu relace ze souboru cookie relace bylo úspěšné.|Zabezpečení|  
|[5606 – PrincipalSettingFromSessionTokenStarted](5606-principalsettingfromsessiontokenstarted.md)|Podrobnosti|Bylo zahájeno nastavení objektu zabezpečení z tokenu relace.|Zabezpečení|  
|[5607 – PrincipalSettingFromSessionTokenSuccess](5607-principalsettingfromsessiontokensuccess.md)|Podrobnosti|Nastavení objektu zabezpečení z tokenu relace bylo úspěšné.|Zabezpečení|  
|[57393 – AppDomainUnload](57393-appdomainunload.md)|Informace o|Uvolňování domény AppDomain. AppDomain.FriendlyName %1, ProcessName %2, ProcessId %3.|Infrastruktura|  
|[57394 – HandledException](57394-handledexception.md)|Informace o|Zpracovává se výjimka.|Infrastruktura|  
|[57395 – ShipAssertExceptionMessage](57395-shipassertexceptionmessage.md)|Chyba|Došlo k neočekávané chybě. Aplikace by se neměly pokoušet tuto chybu zpracovat. Pro účely diagnostiky je tato anglická zpráva přidružena k chybě:% 1.|Infrastruktura|  
|[57396 – ThrowingException](57396-throwingexception.md)|Upozornění|Došlo k vyvolání výjimky. Zdroj% 1.|Infrastruktura|  
|[57397 – UnhandledException](57397-unhandledexception.md)|Kritická|Neošetřená výjimka.|Infrastruktura|  
|[57399 – TraceCodeEventLogCritical](57399-tracecodeeventlogcritical.md)|Kritická|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57400 – TraceCodeEventLogError](57400-tracecodeeventlogerror.md)|Chyba|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57401 – TraceCodeEventLogInfo](57401-tracecodeeventloginfo.md)|Informace o|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57402 – TraceCodeEventLogVerbose](57402-tracecodeeventlogverbose.md)|Podrobnosti|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57403 – TraceCodeEventLogWarning](57403-tracecodeeventlogwarning.md)|Upozornění|Zapsáno do protokolu událostí.|Infrastruktura|  
|[57404 – HandledExceptionWarning](57404-handledexceptionwarning.md)|Upozornění|Zpracovává se výjimka.|Infrastruktura|  
|[62326 – HttpHandlerPickedForUrl](62326-httphandlerpickedforurl.md)|Informace o|Adresa URL '% 1 ' je hostitelem dokumentu XAML s typem kořenového elementu '% 2 '. Typ obslužné rutiny protokolu HTTP% 3 je vybrán pro obsluhu všech požadavků provedených na tuto adresu URL.|WebHost|
