---
title: "Architektura služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ced290c0644fcf89fdf3f87778e705794164b0f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="service-framework"></a>Architektura služby
Toto téma uvádí všechny výjimky generované Data architektury služby.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|Instance vazby má byl již přidružené k naslouchání zadaný identifikátor. Pokud dva koncové body chcete sdílet stejnou indikátoru ListenUniform prostředků, musíte také sdílet stejnou instanci objektu vazby. Dva konfliktní koncové body byly zadány v AddServiceEndpoint(), v konfiguračním souboru nebo jejich kombinaci AddServiceEndpoint() a konfigurace.|  
|AChannelServiceEndpointIsNull0|Koncový bod kanálu nebo služby má hodnotu null.|  
|AChannelServiceEndpointSContractSNameIsNull0|Název koncového bodu kontraktu kanálu nebo služby je null nebo prázdný.|  
|AChannelServiceEndpointSContractSNamespace0|Obor názvů kontraktu koncový bod kanálu nebo služby má hodnotu null.|  
|BaseAddressCannotHaveFragment|Základní adresa nesmí obsahovat fragment identifikátoru URI.|  
|BaseAddressCannotHaveQuery|Základní adresa nesmí obsahovat řetězec dotazu identifikátoru URI.|  
|BaseAddressCannotHaveUserInfo|Základní adresa nesmí obsahovat oddíl informace uživatele identifikátor URI.|  
|BaseAddressDuplicateScheme|Tato kolekce již obsahuje adresu s zadané schéma. Pro každé schéma v této kolekci je povolen pouze jednu adresu.|  
|BaseAddressMustBeAbsolute|Jenom identifikátor URI absolutní slouží jako základní adresu.|  
|BindingDoesnTSupportAnyChannelTypes1|Zadaná vazba nepodporuje vytvoření všechny typy kanálu. Prvky vazeb v vlastní vazby jsou nesprávně skládaný nebo v nesprávném pořadí. Je vyžadován v dolní části zásobníku přenos. Je doporučené pořadí elementů vazby: TransactionFlow, ReliableSession, zabezpečení, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, přenos.|  
|BindingDoesnTSupportDuplexButContractRequires1|Kontrakt vyžaduje duplexní režim. Zadaná vazba nepodporuje nebo není správně nakonfigurována pro její podporu.|  
|BindingDoesnTSupportOneWayButContractRequires1|Kontrakt vyžaduje OneWay. Zadaná vazba nepodporuje nebo není správně nakonfigurována pro její podporu.|  
|BindingDoesnTSupportRequestReplyButContract1|Kontrakt vyžaduje požadavek nebo odpověď. Zadaná vazba nepodporuje nebo není správně nakonfigurována pro její podporu.|  
|BindingDoesnTSupportSessionButContractRequires1|Kontrakt vyžaduje relace.  Zadaná vazba nepodporuje nebo není správně nakonfigurována pro její podporu.|  
|BindingDoesnTSupportTwoWayButContractRequires1|Kontrakt vyžaduje obousměrný (požadavek odpověď nebo duplexní režim). Zadaná vazba nepodporuje nebo není správně nakonfigurována pro její podporu.|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|Atribut DeliveryRequirementsAttribute neumožňuje třídu QueuedDelivery. Vazba pro koncový bod je zadaný kontrakt podporuje.|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|Atribut DeliveryRequirementsAttribute vyžaduje třídu QueuedDelivery. Vazba pro koncový bod je zadaný kontrakt ji nepodporuje nebo není správně nakonfigurován pro podporu ho.|  
|channelDoesNotHaveADuplexSession0|Aktuální kanál nepodporuje ukončení relace výstup. Tento kanál neimplementuje třídu ISessionChannel\<IDuplexSession >.|  
|ClientRuntimeRequiresFormatter0|Zadaný ClientOperation vyžaduje formátovací modul, protože třída SerializeRequest a DeserializeReply nejsou oba hodnotu false.|  
|CommunicationObjectAborted1|Objekt zadaný komunikace nelze použít pro komunikaci, protože byla zastavena.|  
|CommunicationObjectAbortedStack2|Objekt zadaný komunikace nelze použít pro komunikaci, protože byla zastavena: {1}|  
|CommunicationObjectBaseClassMethodNotCalled|Objekt zadaný komunikace přepsal {1} virtuální funkce ale nevyvolá verze definované v základní třídě.|  
|ContractIsNotSelfConsistentItHasOneOrMore2|Zadaný smlouva obsahuje jeden nebo více IsTerminating nebo jiných IsInitiating operace. Vlastnost SessionMode nastavenou na hodnotu SessionMode.Required nemá. Atributy IsInitiating a IsTerminating lze použít pouze v kontextu relace.|  
|CouldnTCreateChannelForChannelType2|Typ zadaný kanálu byla požadována, ale Zadaná vazba nepodporuje nebo není správně nakonfigurována pro její podporu.|  
|DispatchRuntimeRequiresFormatter0|Zadaný DispatchOperation vyžaduje formátovací modul, protože třídy DeserializeRequest a SerializeReply nejsou oba hodnotu false.|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|Metoda End nelze použít s OperationContractAttribute při použití vzoru návrhu IAsyncResult. Odpovídající metody Begin použít s OperationContractAttribute. Tento atribut se vztahuje na začátek-End pár metod.|  
|EndpointListenerRequirementsCannotBeMetBy3|Požadavky na ChannelDispatcher nelze splnit třídu IChannelListener pro zadaná vazba protože kontrakt vyžaduje podporu pro jednu z těchto typů specifikovanému kanálu. Ale vazba podporuje pouze tyto typy specifikovanému kanálu.|  
|EndpointsMustHaveAValidBinding0|Koncové body musí mít platnou vazbu.|  
|InvalidOrUnrecognizedAction|Zprávu nelze zpracovat, protože zadaná akce je neplatný nebo nerozpoznaný.|  
|MultipleMebesInParameters|V parametrech vazby byla nalezena více než jedna položka. CustomBinding nemůže mít více MessageEncodingBindingElements. Odeberte všechny kromě jeden z těchto elementů.|  
|MultipleStreamUpgradeProvidersInParameters|V parametrech vazby byla nalezena více IStreamUpgradeProviderElement. CustomBinding nemůže mít více než jeden tříd IStreamUpgradeProviderElement. Odeberte všechny kromě jeden z těchto elementů.|  
|NoChannelBuilderAvailable|Vazbu nelze použít k vytvoření postupu kanálu nebo naslouchací proces kanálu, protože nemá třídu TransportBindingElement. Každá vazba musí mít alespoň jeden element vazby, která je odvozena od třídy TransportBindingElement.|  
|NotAllBindingElementsBuilt|Některé prvky vazby v této vazbě nebyly použít při vytváření kanálu a naslouchací proces kanálu. Prvky vazeb nejsou správně řazení. Je doporučené pořadí elementů vazby: TransactionFlow, ReliableSession, zabezpečení, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, přenos.  Všimněte si, že TransportBindingElement musí být poslední. Elementy zadaný vazby nebyly vytvořeny.|  
|RuntimeRequiresInvoker0|Operace odesílání vyžaduje původce volání.|  
|ServiceHasZeroAppEndpoints|Zadaná služba nemá žádné koncové body (ne infrastruktury) aplikace. To může být, protože nebyl nalezen žádný konfigurační soubor pro vaši aplikaci nebo protože element služby odpovídající názvu služby se nenašel v konfiguračním souboru nebo v elementu služby nebyly definované žádné koncové body.|  
|SFxActionMismatch|Nelze vytvořit zadanou zprávu kvůli neshodě akce. Byla očekávána zadanou akci došlo ale jiné|  
|SFxAnonymousTypeNotSupported|Zadaný součástí určenou zprávu nelze exportovat s RPC nebo kódování, protože jeho typ není anonymní.|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|Adresa URL zadané ServiceMetadataBehavior pomocí vlastnost ExternalMetadataLocation nebo atributu externalMetadataLocation v oddílu serviceMetadata v konfiguračním oddílu byla relativní adresa URL a je základní adresa, kterou je třeba vyřešit ho.|  
|SFxBadMetadataMustBePolicy|Musíte zadat zásady XmlElement, který má zadaný obor názvů a název. Tato XmlElement má zadaný obor názvů a název.|  
|SFxBodyObjectTypeCannotBeInherited|Zadaný typ nemůže Zdědit z jiné třídy než objekt, který chcete použít jako objekt textu ve stylu RPC.|  
|SFxBodyObjectTypeCannotBeInterface|Zadaný typ implementuje dané rozhraní, což není podporováno pro objekt textu ve stylu RPC.|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|Třídy CallbackBehaviorAttribute lze spustit pouze jako chování na koncový bod s duplexního kontraktu. Zadaný kontrakt není duplexní a obsahuje žádné operace zpětného volání.|  
|SFxCallbackRequestReplyInOrder1|Odpověď nemůže být přijato z tuto operaci, až po dokončení zpracování aktuální zprávu. Pokud chcete povolit zpracování zpráv mimo pořadí, zadejte režim ConcurrencyMode vícenásobné nebo více na zadaný.|  
|SfxCallbackTypeCannotBeNull|Chcete-li použít zadaný kontrakt s třídou DuplexChannelFactory, musíte zadat kontrakt kontraktu platný zpětného volání. Pokud vaše smlouvy nemá kontraktu zpětného volání, použijte místo třídy DuplexChannelFactory ChannelFactory.|  
|SFxCannotGetMetadataFromLocation|Třída MetadataExchangeClient může získat metadata pouze z protokolu HTTP a HTTPS třídy MetadataLocations. Ze zadaného nemůže získat metadata.|  
|SFxCannotHttpGetMetadataFromAddress|Třída MetadataExchangeClient může získat metadata pouze z adres protokolu HTTP nebo HTTPS při použití třídy MetadataExchangeClientMode používá. Ze zadaného nemůže získat metadata.|  
|SFxCannotImportAsParameters_Bare|Generování kontrakt zprávy, protože zadaná operace není RPC ani dokumentu uzavřen.|  
|SFxCannotImportAsParameters_DifferentWrapperName|Generování kontrakt zprávy, protože název obálku zadané zprávy neodpovídá výchozí hodnota.|  
|SFxCannotImportAsParameters_DifferentWrapperNs|Generování kontrakt zprávy, protože obálku obor názvů zadané zprávy neodpovídá výchozí hodnota.|  
|SFxCannotImportAsParameters_ElementIsNotNillable|Generování kontrakt zprávy, protože název zadaného elementu ze zadaného oboru názvů není označena povolenou hodnotu Null.|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|Generování kontrakt zprávy, protože zadaná zpráva má hlavičky.|  
|SFxCannotImportAsParameters_Message|Generování kontrakt zprávy, protože zadaná operace má jako argument, nebo návratový typ zprávu bez typu.|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|Generování kontrakt zprávy, protože vyžaduje ochranu zadané zprávy.|  
|SFxCannotImportAsParameters_NamespaceMismatch|Generování kontrakt zprávy, protože část obor názvů zadané zprávy neodpovídá výchozí hodnota.|  
|SFxCannotRequireBothSessionAndDatagram3|Zadaný kontrakt určuje SessionMode.NotAllowed a zadaný kontrakt určuje SessionMode.Required. Změňte jednu z hodnot SessionMode nebo zadejte jinou adresu nebo adrese ListenURI, pro každý koncový bod.|  
|SFxCannotSetExtensionsByIndex|Tato kolekce nepodporuje nastavení rozšíření index. Pomocí metody InsertItem nebo RemoveItem metod.|  
|SFxChannelDispatcherDifferentHost0|Třída ChannelDispatcher není aktuálně připojena k hostiteli služby, který byl poskytnut.|  
|SFxChannelDispatcherMultipleHost0|Třída ChannelDispatcher nelze přidat do více než jeden hostitel služby.|  
|SFxChannelDispatcherNoHost0|Třída ChannelDispatcher nelze otevřít, protože není připojený k hostiteli služby.|  
|SfxChannelFactoryDisposed|Tato ChannelFactory nejde otevřít, protože ChannelFactory již byl zlikvidován. Vytvoření třídy ChannelFactory znovu před jeho použitím.|  
|SFxChannelFactoryNoBinding|Třídy ChannelFactory nelze otevřít, protože nebyla vytvořena žádná vazba byla přidružena svůj koncový bod. Zadejte vazbu pomocí konstruktoru nebo vlastnost koncový bod.|  
|SFxChannelTerminated0|Operace označená jako IsTerminating již byla vyvolána v tomto kanálu způsobí, že kanál připojení ukončit. Žádné další operace může být volána v tomto kanálu. Znovu vytvořte kanál pokračujte komunikace.|  
|SFxCloseTimedOut1|Operace zavření ServiceHost zastavena po zadaný. To může být způsobeno klienta se nezdařilo ukončit kanál s relacemi v požadované době. Čas pro tuto operaci povolená může být součástí delší časový limit.|  
|SfxCloseTimedOutWaitingForDispatchToComplete|Proces zavřít vypršení časového limitu při čekání na dokončení odeslání služby.|  
|SFxCodeGenIsNotAssignableFrom|Nelze přiřadit zadaný.|  
|SFxConfigChannelConfigurationNotFound|Nebyl nalezen element koncového bodu se zadaným názvem a kontrakt v konfiguračním oddílu ServiceModel klienta.|  
|SFxConflictingGlobalElement|Element nejvyšší úrovně Extensible Markup Language se zadaným názvem v určeném oboru názvů nesmí odkazovat na zadaný typ. Již odkazuje na jiný atribut type. Zadejte jiný název pro zpráva nebo zpráva částí pomocí jiné operace název nebo MessageBodyAttribute.|  
|SFxContractHasZeroInitiatingOperations|Kontrakt musí mít alespoň jeden IsInitiating = true operaci.|  
|SFxContractHasZeroOperations|Kontrakt musí mít nejméně jednu operaci.|  
|SFxContractInheritanceRequiresInterfaces|Třída služby zadaného typu definuje třídu ServiceContract a dědí třídu ServiceContract ze zadaného typu. Kontrakt dědičnost lze použít pouze mezi typy rozhraní. Pokud ServiceContractAttribute označeno třídu, musí být jediným typem v hierarchii s ServiceContractAttribute.  Přesunete ServiceContractAttribute na zadaný typ k samostatné rozhraní, které implementuje zadaného typu.|  
|SFxCreateDuplexChannel1|Zpětné volání kontrakt zadaný kontraktu neexistuje nebo nedefinuje žádné operace. Pokud to není duplexního kontraktu, použijte místo třídy DuplexChannelFactory ChannelFactory.|  
|SFxCreateDuplexChannelNoCallback|Přetížení CreateChannel nelze volat v této instanci třídy DuplexChannelFactory. Třída DuplexChannelFactory nebyl inicializován s třídu InstanceContext. Volání CreateChannel přetížení, které přijímá třídu InstanceContext.|  
|SFxCreateDuplexChannelNoCallback1|Přetížení CreateChannel nelze volat v této instanci třídy DuplexChannelFactory. Třída DuplexChannelFactory byl inicializován s typem a nebyl poskytnut žádný platný objekt InstanceContext. Volání CreateChannel přetížení, které přijímá třídu InstanceContext.|  
|SFxCreateDuplexChannelNoCallbackUserObject|Přetížení CreateChannel nelze volat v této instanci třídy DuplexChannelFactory. Parametr InstanceContext poskytnutá třídě DuplexChannelFactory neobsahuje platnou třídu UserObject.|  
|SFxCreateNonDuplexChannel1|ChannelFactory nepodporuje zadaný kontrakt. ChannelFactory definuje kontrakt zpětné volání s jednu nebo více operací. Pomocí třídy DuplexChannelFactory místo ChannelFactory.|  
|SFxCustomBindingNeedsTransport1|CustomBinding na koncového bodu služby je zadaný kontrakt nemá třídu TransportBindingElement. Každá vazba musí mít alespoň jeden element vazby, která je odvozena od třídy TransportBindingElement.|  
|SFxCustomBindingWithoutTransport|Schéma nelze vypočítat pro tuto vlastní vazbu protože nemá třídu TransportBindingElement. Každá vazba musí mít alespoň jeden element vazby, která je odvozena od třídy TransportBindingElement.|  
|SFxDataContractSerializerDoesNotSupportBareArray|DataContractSerializer nepodporuje kolekce zadaná u daného elementu.|  
|SFxDictionaryIsEmpty|Operaci nelze provést, protože adresář je prázdný.|  
|SFxDocEncodedNotSupported|Došlo k chybě odrážející zadaný. Kódovaný jazykem dokumentu není podporována. Změnit, použijte' na literál nebo 'Style' na protokol RPC.|  
|SFxDuplicateInitiatingActionAtSameVia|Tato služba obsahuje několik koncových bodů naslouchání v zadaném. Koncové body sdílejí stejnou Zadaný inicializační akci. Zprávy s Tato akce by vyřadit, protože dispečera nebude schopen určit správná koncový bod pro zpracování zprávy.|  
|SFXEndpointBehaviorUsedOnWrongSide|Zadaný IEndpointBehavior nelze použít na serveru. Toto chování může platí jenom pro klienty.|  
|SFxEndpointNoMatchingScheme|Základní adresa, která odpovídá zadané schéma pro koncový bod s Zadaná vazba nebyl nalezen. Registrovaný základní adresa systémy jsou uvedeny.|  
|SFxErrorCreatingMtomReader|Došlo k chybě při vytváření čtečku pro zprávu mechanismus Optimalizace přenosu zpráv.|  
|SFxErrorDeserializingFault|Server vrátil chybu neplatný objekt jednoduchý přístup protokolu. Další podrobnosti najdete v InnerException.|  
|SFxErrorDeserializingHeader|Při deserializaci jedné z hlaviček v zadané zprávy došlo k chybě. Další podrobnosti najdete ve vlastnosti InnerException.|  
|SFxErrorReflectingOnMethod3|Došlo k chybě při načítání zadaného atributu na zadanou metodu v zadaného typu.  Další podrobnosti najdete v InnerException.|  
|SFxErrorReflectingOnParameter4|Došlo k chybě při načítání zadaného atributu na zadaný parametr zadanou metodu v zadaného typu. Další podrobnosti najdete v InnerException.|  
|SFxErrorReflectingOnType2|Došlo k chybě při načítání zadaný atribut u zadaného typu.  Další podrobnosti najdete v InnerException.|  
|SFxErrorSerializingBody|Došlo k chybě serializaci text zadané zprávy. Další podrobnosti najdete v InnerException.|  
|SFxErrorSerializingHeader|Došlo k chybě při serializaci jedné z hlaviček v zadané zprávy. Další podrobnosti najdete v InnerException.|  
|SFxExpectedIMethodCallMessage|Vnitřní chyba Zpráva musí být platný IMethodCallMessage.|  
|SFxExportMustHaveType|Zadaný součástí zadanou operaci nelze exportovat, protože nemá platný typ CLR.|  
|SFxHeaderNotUnderstood|Zpráva nebyla zpracována. Zadaná hlavička ze zadaného oboru názvů nebyla rozpoznaná příjemce této zprávy. Tato chyba obvykle značí, že odesílatel zprávy povolil komunikační protokol, který příjemce nemůže zpracovat. Ujistěte se, že konfigurace klienta vazby je konzistentní s vazbou služby.|  
|SFxHeadersAreNotSupportedInEncoded|Zadaná zpráva nesmí mít hlavičky pro použití v styl kódovaný volání vzdálených procedur.|  
|SFxInconsistentWsdlOperationStyleInMessageParts|Všechny části zprávy v zadanou operaci musí obsahovat buď typu nebo element.|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|Zadaný styl odvodit z zpráv v určené operace neodpovídá zadané očekávané styl určený pomocí vazby.|  
|SFxInvalidCallbackIAsyncResult|IAsyncResult není k dispozici nebo je nesprávného typu.|  
|SFxInvalidMessageBody|Formátovací modul OperationFormatter došlo textu neplatná zpráva. Byl očekáván typ uzlu 'Element' s určeným názvem a oborem názvů. Byl nalezen typ zadaný uzel s určeným názvem a oborem názvů.|  
|SFxInvalidMessageBodyEmptyMessage|Formátovací modul OperationFormatter nelze deserializovat všechny informace ze zprávy, protože zpráva je prázdná.|  
|SFxInvalidMessageBodyErrorDeserializingParameter|Došlo k chybě při pokusu o deserializaci zadaný parametr. Další informace najdete ve vlastnosti InnerException.|  
|SFxInvalidMessageBodyErrorSerializingParameter|Došlo k chybě při pokusu o serializaci zadaný parametr. Byl zadán zprávy ve vlastnosti InnerException.  Další podrobnosti najdete v InnerException.|  
|SFxInvalidMessageBodyUnexpectedNode|Došlo k zadané neočekávaný uzel ze zadaného oboru názvů při deserializaci parametry.|  
|SFxInvalidMessageContractSignature|Zadaná operace má parametr nebo návratový typ, který je označený MessageContractAttribute. Při použití kontrakt zprávy představující zprávu požadavku, operaci musí mít jeden parametr, který je označené jako MessageContractAttribute. Při použití kontrakt zprávy představující zprávu odpovědi, operace návratová hodnota musí být typ, který je označené jako MessageContractAttribute. Operace nemůže mít žádné 'ref' nebo 'out' parametry.|  
|SFxInvalidReplyAction|Odchozí zprávy odpovědi pro operaci se zadanou akci, ale jiné ReplyAction určuje smlouvu pro tuto operaci. Akci určenou ve zprávě musí odpovídat ReplyAction ve smlouvě nebo kontrakt operaci, musíte zadat ReplyAction ='* '.|  
|SFxInvalidRequestAction|Odchozí zprávy požadavku pro operaci se zadanou akci, ale jiné RequestAction určuje smlouvu pro tuto operaci. Akci určenou ve zprávě musí odpovídat RequestAction ve smlouvě nebo kontrakt operaci, musíte zadat RequestAction ='* '.|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|Statickou metodu CreateChannel nelze použít s zadaný kontrakt, protože tento kontrakt definuje kontrakt zpětného volání. Použijte jednu ze statické přetížení CreateChannel v třídy DuplexChannelFactory\<TChannel >.|  
|SFxInvalidStreamInRequest|Operaci požadavku zadanou operaci jako datový proud, musí mít jeden parametr, jehož typ je datový proud.|  
|SFxInvalidStreamInResponse|Operaci pro odpověď v rámci zadané operace jako datový proud, musíte mít jeden parametr out nebo návratová hodnota, jejíž typ je datový proud.|  
|SFxInvalidStreamInTypedMessage|Použití datových proudů s kontrakt zprávy programovací model, musí mít zadaný typ jednoho člena MessageBody, jejichž typ je datový proud.|  
|SFxInvalidUseOfPrimitiveOperationFormatter|PrimitiveOperationFormatter byl zadán parametr nebo návratový typ, který nepodporuje.|  
|SFxMessageContractBaseTypeNotValid|Zadaný typ definuje parametr MessageContract a je odvozena ze zadaného typu, který nedefinuje MessageContract. Všechny objekty v hierarchii dědičnosti zadaný musí definovat MessageContract.|  
|SFxMethodNotSupported1|Určená metoda není podporována u tohoto objektu. Tomu může dojít, pokud metoda není označen atributem OperationContractAttribute nebo pokud typ rozhraní není označen atributem ServiceContractAttribute.|  
|SFxMethodNotSupportedByType2|Zadaný typ implementace ServiceHost neimplementuje kontrakt zadaná služba.|  
|SFxMethodNotSupportedOnCallback1|Zpětné volání zadaná metoda není podporována. Tomu může dojít, pokud metoda není označen atributem OperationContractAttribute nebo pokud jeho typ rozhraní není cílem třída ServiceContractAttribute CallbackContract.|  
|SFxMismatchedOperationParent|DispatchOperation nebo ClientOperation lze přidat pouze ke své nadřazené úloze DispatchRuntime nebo ClientRuntime v uvedeném pořadí.|  
|SFxNameCannotBeEmpty|Vlastnost Name nemůže být prázdný řetězec.|  
|SfxNoTypeSpecifiedForParameter|Pro parametr, který zabrání operaci generován byl zadán žádný typ CLR.|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute pouze přejít na třídě služby. Nelze se vrátit do rozhraní ServiceContract. Zadanou metodu na zadaný typ v rozporu se to.|  
|SFxOperationContractOnNonServiceContract|Zadanou metodu je označené jako OperationContractAttribute, ale nadřazených zadaný typ není označen atributem ServiceContractAttribute. OperationContractAttribute lze použít pouze na metody v typech ServiceContractAttribute nebo jejich typů CallbackContract.|  
|SFxParameterCountMismatch|Došlo k neshodě mezi počet zadaný argumentů a počet očekávané argumentů. Zadaný argument konkrétně má zadaný počet elementů, zatímco očekávaný argument má zadaný počet elementů.|  
|SFxPartNameMustBeUniqueInRpc|Název součásti zadané zprávy není jedinečné v zprávu volání vzdálených procedur.|  
|SFxReplyActionMismatch3|Byla přijata zpráva odpovědi pro danou operaci spolu s určenou akcí. Váš klientský kód však vyžaduje zadanou akci.|  
|SFxRequestReplyNone|Byla přijata zpráva s hlavičku WS-Addressing ReplyTo nebo FaultTo zaměřený na "Žádný" adresu. Tyto hodnoty nejsou platné pro požadavek odpověď operace. Použít Jednosměrná operace nebo povolte ManualAddressing, pokud budete potřebovat k podpoře ReplyTo nebo FaultTo hodnoty "Žádný".|  
|SFxRequestTimedOut1|Touto operací požadavku nepřijala odpověď v rámci zadané nakonfigurované doby. Časový limit pravděpodobně součástí delší časový limit. Může to být proto, že služba je stále zpracovává operaci nebo službu se nepodařilo odeslat zprávu odpovědi.|  
|SFxRequestTimedOut2|Operace požadavku, odeslané do zadaného umístění nepřijala odpověď v rámci zadané nakonfigurované doby. Časový limit pravděpodobně součástí delší časový limit. Může to být proto, že služba je stále zpracovává operaci nebo službu se nepodařilo odeslat zprávu odpovědi.|  
|SFxSchemaDoesNotContainType|Schéma s oborem názvů zadaný cílový neobsahuje typu se zadaným názvem.|  
|SfxServiceContractAttributeNotFound|Typ zadaný smlouvy není atribut ServiceContractAttribute. K definování kontraktu platný, zadaný typ musí být atribut ServiceContractAttribute. Typ může být buď rozhraní kontraktu nebo třídu služby.|  
|SFxServiceContractGeneratorConfigRequired|Generovat informace o konfiguraci pomocí metody GenerateServiceEndpoint, musí být ServiceContractGenerator instance inicializován s objektem platné konfigurace.|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|Koncové body nejde přidat po hostiteli služby je v některém z následujících stavů:<br /><br /> -Otevřít<br />-S chybou<br />-Byl ukončen<br />-Uzavřený|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Před inicializací vlastnost Popis nelze přidat koncové body.|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|HttpGetEnabled ServiceMetadataBehavior je nastavena na hodnotu true a vlastnost HttpGetUrl je relativní adresa, ale neexistuje žádná základní adresu HTTP. Buď zadejte základní adresu HTTP, nebo nastavte vlastnost HttpGetUrl na absolutní adresu.|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|HttpsGetEnabled ServiceMetadataBehavior je nastavena na hodnotu true a vlastnost HttpsGetUrl je relativní adresa, ale neexistuje žádná základní adresa HTTPS. Buď zadejte základní adresu HTTPS, nebo nastavte vlastnost HttpsGetUrl na absolutní adresu.|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|Adresa Url chování musí být relativní identifikátor nebo identifikátor URI absolutní s zadané schéma. Zadaná adresa Url je absolutní uniform resource identifier s zadané schéma.|  
|SFxStreamRequestMessageClosed|Zpráva, která obsahuje tento datový proud byl uzavřen. Datové proudy požadavek nelze získat přístup, po operaci služby vrátí.|  
|SFxStreamResponseMessageClosed|Zpráva, která obsahuje tento datový proud byl uzavřen.|  
|SFxTerminateRequestProcessingException|Rozšíření v kanálu operaci musí ukončit zpracování této zprávy.|  
|SFxTerminatingOperationAlreadyCalled1|Tento kanál nelze odeslat další zprávy, protože byla volána operace IsTerminating.|  
|SFxThrottleLimitMustBeGreaterThanZero0|Limit omezení musí být větší než nula. Limit omezovače zakázat, nastavte hodnotu na Int32.MaxValue.|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|Při použití styl kódováním RPC, typy kontraktů zpráv nebo typ System.ServiceModel.Channels.Message nelze použít, pokud operace nemá žádné parametry, nebo má void návratovou hodnotu. Přidání typu kontraktu prázdná zpráva jako parametr nebo návratový typ pro danou operaci.|  
|SFxUserCodeThrewException|Zadaný uživatel operaci došlo k výjimce, která je neošetřená v uživatelském kódu. Pokud je opakované problém, může to znamenat chybu při provádění zadanou metodu.|  
|SfxUseTypedMessageForCustomAttributes|Zadaný parametr nemůže být namapovaný na parametr operaci, protože vyžaduje další atributy.|  
|SFxVersionMismatchInOperationContextAndMessage2|Nelze přidat odchozí záhlaví ke zprávě, protože verze MessageVersion v OperationContext.Current neshoduje s verzí hlavičky zpracovává zprávy|  
|SFxWellKnownNonSingleton0|Chcete-li použít jeden z konstruktorů ServiceHost, který přijímá instanci služby, musí být InstanceContextMode služby nastavena na hodnotu InstanceContextMode.Single. Toto můžete nakonfigurovat pomocí ServiceBehaviorAttribute. Jinak použijte konstruktory ServiceHost, které nepřijímají argumentem typu.|  
|SFxWrapperTypeHasMultipleNamespaces|Typ obálku pro zadané zprávy se nedá projektovat jako datový typ smlouvy, protože obsahuje více oborů názvů. Pomocí třídy XmlSerializer.|  
|UriMustBeAbsolute|Musí být absolutní identifikátor URI.|
