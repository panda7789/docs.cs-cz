---
title: Architektura služby
ms.date: 03/30/2017
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
ms.openlocfilehash: 859e718a56ab63c8e012e1851c0730f53cb707be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780754"
---
# <a name="service-framework"></a>Architektura služby
Toto téma uvádí všechny výjimky generované Data architektury služby.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|Instance vazby je už je přidružený k tak, aby naslouchala zadaný identifikátor. Pokud dva koncové body služby chcete sdílet stejný ukazatel ListenUniform prostředku, musejí rovněž sdílet stejnou instanci objektu vazby. Dva konfliktní koncové body byly určeny ve voláních AddServiceEndpoint(), v konfiguračním souboru nebo spojení třídy AddServiceEndpoint() a konfigurace.|  
|AChannelServiceEndpointIsNull0|Koncový bod kanálu nebo služby má hodnotu null.|  
|AChannelServiceEndpointSContractSNameIsNull0|Název kontraktu koncového bodu kanálu nebo služby má hodnotu null nebo prázdný.|  
|AChannelServiceEndpointSContractSNamespace0|Obor názvů kontraktu koncového bodu kanálu nebo služby má hodnotu null.|  
|BaseAddressCannotHaveFragment|Základní adresa nesmí obsahovat fragment identifikátoru URI.|  
|BaseAddressCannotHaveQuery|Základní adresa nesmí obsahovat řetězec dotazu identifikátoru URI.|  
|BaseAddressCannotHaveUserInfo|Základní adresa nesmí obsahovat část URI identifikátor uživatelské informace.|  
|BaseAddressDuplicateScheme|Tato kolekce již obsahuje adresu se zadané schéma. Pro každé schéma v této kolekci je povolena pouze jedna adresa.|  
|BaseAddressMustBeAbsolute|Pouze absolutní URI identifikátor může sloužit jako základní adresu.|  
|BindingDoesnTSupportAnyChannelTypes1|Zadaná vazba nepodporuje vytváření žádných typů kanálů. Elementů vazby ve vlastní vazby jsou uspořádány vedle nesprávně nebo v nesprávném pořadí. Je vyžadován v dolní části zásobníku přenos. Doporučené pořadí elementů vazby je: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.|  
|BindingDoesnTSupportDuplexButContractRequires1|Smlouva vyžaduje vlastnost Duplex. Zadaná vazba není podporován nebo není pro její podporu správně nakonfigurována.|  
|BindingDoesnTSupportOneWayButContractRequires1|Smlouva vyžaduje vlastnost OneWay. Zadaná vazba není podporován nebo není pro její podporu správně nakonfigurována.|  
|BindingDoesnTSupportRequestReplyButContract1|Smlouva vyžaduje požadavek nebo odpověď. Zadaná vazba není podporován nebo není pro její podporu správně nakonfigurována.|  
|BindingDoesnTSupportSessionButContractRequires1|Smlouva vyžaduje relaci.  Zadaná vazba není podporován nebo není pro její podporu správně nakonfigurována.|  
|BindingDoesnTSupportTwoWayButContractRequires1|Smlouva vyžaduje obousměrné (požadavek odpověď nebo duplexní). Zadaná vazba není podporován nebo není pro její podporu správně nakonfigurována.|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|Atribut DeliveryRequirementsAttribute třídu QueuedDelivery nepovoluje. Vazba koncového bodu se zadaným smlouvy ho podporuje.|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|Třída DeliveryRequirementsAttribute vyžaduje třídu QueuedDelivery. Vazba koncového bodu se zadaným kontraktu není podporován nebo není pro její podporu správně nakonfigurována.|  
|channelDoesNotHaveADuplexSession0|Aktuální kanál nepodporuje ukončování výstupní relace. Tento kanál neimplementuje třídu ISessionChannel\<IDuplexSession >.|  
|ClientRuntimeRequiresFormatter0|Zadaná třída ClientOperation vyžaduje formátovací modul, protože třída SerializeRequest a DeserializeReply nejsou obě hodnotu false.|  
|CommunicationObjectAborted1|Objekt zadaný komunikační nelze použít pro komunikaci, protože byla zastavena.|  
|CommunicationObjectAbortedStack2|Objekt zadaný komunikační nelze použít pro komunikaci, protože byla zastavena: {1}|  
|CommunicationObjectBaseClassMethodNotCalled|Objekt zadaný komunikační potlačil virtuální funkci {1} ale nevolá verzi definovanou v základní třídě.|  
|ContractIsNotSelfConsistentItHasOneOrMore2|Zadaná smlouva obsahuje jednu nebo víc operací IsTerminating nebo bez IsInitiating operace. Nemá vlastnost SessionMode nastavenou na hodnotu SessionMode.Required. Atributy IsInitiating a IsTerminating jde použít jenom v kontextu relace.|  
|CouldnTCreateChannelForChannelType2|Typ zadaný kanál byl vyžádán, ale Zadaná vazba není podporován nebo není pro její podporu správně nakonfigurována.|  
|DispatchRuntimeRequiresFormatter0|Zadaná třída DispatchOperation vyžaduje formátovací modul, protože třídy DeserializeRequest a SerializeReply nejsou obě hodnotu false.|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|Metoda End nelze použít třídou OperationContractAttribute, při použití vzoru návrhu IAsyncResult. Lze použít pouze odpovídající metoda Begin třídou OperationContractAttribute. Tento atribut se vztahuje na začátek-konec dvojice metody.|  
|EndpointListenerRequirementsCannotBeMetBy3|Požadavky třídy ChannelDispatcher nelze splnit třídou IChannelListener pro určenou vazbu, protože kontrakt vyžaduje podporu pro jeden z těchto typů Zadaný kanál. Ale vazba podporuje pouze tyto typy Zadaný kanál.|  
|EndpointsMustHaveAValidBinding0|Koncové body musí mít platnou vazbu.|  
|InvalidOrUnrecognizedAction|Zprávu nelze zpracovat, protože zadané akce je neplatná nebo nerozpoznaná.|  
|MultipleMebesInParameters|Více tříd MessageEncodingBindingElement v třídě BindingParameters třídy BindingContext byl nalezen. Třídě CustomBinding nemůže mít více MessageEncodingBindingElements. Odeberte všechny kromě jednoho z těchto elementů.|  
|MultipleStreamUpgradeProvidersInParameters|V třídě BindingParameters třídy BindingContext byl nalezen více tříd IStreamUpgradeProviderElement. Třídě CustomBinding nemůže mít více tříd IStreamUpgradeProviderElement. Odeberte všechny kromě jednoho z těchto elementů.|  
|NoChannelBuilderAvailable|Vazbu nelze použít k vytvoření objektu pro vytváření kanálů nebo modul pro naslouchání kanálu, protože neobsahuje třídu TransportBindingElement. Každá vazba musí mít alespoň jeden element vazby, která je odvozena od třídy TransportBindingElement.|  
|NotAllBindingElementsBuilt|Některé elementy vazby v této vazbě nebyly použity při vytváření objektu pro vytváření kanálů a modul pro naslouchání kanálu. Elementy vazby nejsou seřazené. správně. Doporučené pořadí elementů vazby je: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.  Všimněte si, že třída TransportBindingElement musí být poslední. Elementy zadaného vazby nebyly vytvořeny.|  
|RuntimeRequiresInvoker0|Operace odeslání vyžaduje původce volání.|  
|ServiceHasZeroAppEndpoints|Zadaná služba nemá žádné koncové body aplikace (ne infrastruktury). To může být, protože nebyl nalezen žádný konfigurační soubor aplikace nebo v konfiguračním souboru nebylo možné najít element služby odpovídající názvu služby nebo v elementu služby nebyly definovány žádné koncové body.|  
|SFxActionMismatch|Nelze vytvořit zadanou zprávu, protože došlo k neshodě akcí. Očekává se zadanou akci ale došlo k jiné|  
|SFxAnonymousTypeNotSupported|V určenou zprávu na zadanou část nelze exportovat s RPC nebo kódování, protože její typ je anonymní.|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|Adresa URL dodaná třídě ServiceMetadataBehavior pomocí vlastnosti ExternalMetadataLocation nebo atributu externalMetadataLocation v oddílu serviceMetadata v části Konfigurace byla relativní adresu URL a neexistuje žádná základní adresa, pomocí kterého se má vyřešit ho.|  
|SFxBadMetadataMustBePolicy|Musíte zadat atributy XmlElement, který má zadaný obor názvů a název zásady. Tato třída XmlElement má určený obor názvů a název.|  
|SFxBodyObjectTypeCannotBeInherited|Zadaný typ nemůže dědit z jiné třídy, než je objekt, který se použije jako objekt textu ve stylu RPC.|  
|SFxBodyObjectTypeCannotBeInterface|Zadaný typ implementuje rozhraní zadané, což není podporováno pro objekt textu ve stylu RPC.|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|Třídu CallbackBehaviorAttribute lze spustit pouze jako chování v koncovém bodě s duplexní smlouvou. Zadaná smlouva není duplexní a žádné operace zpětného volání.|  
|SFxCallbackRequestReplyInOrder1|Odpověď nelze přijmout z této operace, dokud aktuální zpráva nedokončí zpracování. Pokud chcete povolit zpracování zpráv mimo pořadí, zadejte ConcurrencyMode režimu Reentrant nebo více stanoveného.|  
|SfxCallbackTypeCannotBeNull|Chcete-li použít zadaný kontraktu s třídou DuplexChannelFactory, musí kontrakt určit platný zpětného volání kontraktu. Pokud vaše Smlouva nemá kontrakt zpětného volání, použití třídy ChannelFactory namísto třídy DuplexChannelFactory.|  
|SFxCannotGetMetadataFromLocation|Třída MetadataExchangeClient může získat metadata pouze z protokolu HTTP a HTTPS třídy MetadataLocations. Nemůže získat metadata z určeného.|  
|SFxCannotHttpGetMetadataFromAddress|Třída MetadataExchangeClient může získat metadata pouze z adres HTTP nebo HTTPS při použití třídu HttpGet. Nemůže získat metadata z určeného.|  
|SFxCannotImportAsParameters_Bare|Probíhá generování kontraktu zprávy, protože zadaná operace není RPC ani není zabalena dokumentem.|  
|SFxCannotImportAsParameters_DifferentWrapperName|Probíhá generování kontraktu zprávy, protože název obálky určenou zprávu se neshoduje s výchozí hodnotu.|  
|SFxCannotImportAsParameters_DifferentWrapperNs|Probíhá generování kontraktu zprávy, protože obor názvů obálky zadané zprávy neodpovídá výchozí hodnotě.|  
|SFxCannotImportAsParameters_ElementIsNotNillable|Generování kontraktu zprávy, protože název zadaného elementu ze zadaného oboru názvů není označen jako nillable.|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|Probíhá generování kontraktu zprávy, protože zadaná zpráva obsahuje záhlaví.|  
|SFxCannotImportAsParameters_Message|Generování kontraktu zprávy, protože zadaná operace má nezadanou zprávu jako argumentů nebo návratového typu.|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|Probíhá generování kontraktu zprávy, protože zadaná zpráva vyžaduje ochranu.|  
|SFxCannotImportAsParameters_NamespaceMismatch|Probíhá generování kontraktu zprávy, protože obor názvů části zadané zprávy se neshoduje s výchozí hodnotu.|  
|SFxCannotRequireBothSessionAndDatagram3|Určuje třídu SessionMode.NotAllowed, zadaný smlouvy a zadané kontrakt určuje SessionMode.Required. Změňte jednu z hodnot SessionMode nebo určit jinou adresu nebo třídu ListenURI, pro každý koncový bod.|  
|SFxCannotSetExtensionsByIndex|Tato kolekce nepodporuje nastavení rozšíření podle indexu. Použití metody InsertItem nebo RemoveItem metody.|  
|SFxChannelDispatcherDifferentHost0|Třída ChannelDispatcher momentálně není připojena k ServiceHost, který byl poskytnut.|  
|SFxChannelDispatcherMultipleHost0|Třída ChannelDispatcher nelze přidat do více než jedné třídě ServiceHost.|  
|SFxChannelDispatcherNoHost0|Třída ChannelDispatcher nelze otevřít, protože není připojená k třídě ServiceHost.|  
|SfxChannelFactoryDisposed|Této třídy ChannelFactory nelze otevřít, protože třídy ChannelFactory už je vyřazený. Vytváření třídy ChannelFactory znovu před jeho použitím.|  
|SFxChannelFactoryNoBinding|Třídy ChannelFactory nelze otevřít, protože žádná vazba byla přidružena svůj koncový bod. Zadání vazby s konstruktorem nebo vlastností koncový bod.|  
|SFxChannelTerminated0|Operace označená jako IsTerminating již byla vyvolána v tomto kanálu způsobí ukončení připojení kanálu. Žádné další operace mohou být vyvolány v tomto kanálu. Znovu vytvořte kanál pokračovat v komunikaci.|  
|SFxCloseTimedOut1|Operaci zavření hostitele ServiceHost zastavena po zadaný. To může být způsobeno klientovi nepodařilo uzavřít kanál s relacemi v požadovaném čase. Čas povolen pro tuto operaci byl pravděpodobně částí delšího časového limitu.|  
|SfxCloseTimedOutWaitingForDispatchToComplete|Zavřít procesu vypršel časový limit při čekání na dokončení odeslání služby.|  
|SFxCodeGenIsNotAssignableFrom|Nelze přiřadit zadaný.|  
|SFxConfigChannelConfigurationNotFound|Nelze najít element koncového bodu se zadaným názvem a smlouvy v oddílu konfigurace klienta třídy ServiceModel.|  
|SFxConflictingGlobalElement|Element nejvyšší úrovně Extensible Markup Language se zadaným názvem v určeném oboru názvů nemůžou odkazovat na zadaného typu. Už odkazuje na jiný typ. Použijte jiný název operace nebo MessageBodyAttribute k určení pro zprávy nebo částí zprávy jiný název.|  
|SFxContractHasZeroInitiatingOperations|Kontrakt musí mít aspoň jeden IsInitiating = true operace.|  
|SFxContractHasZeroOperations|Kontrakt musí mít alespoň jednu operaci.|  
|SFxContractInheritanceRequiresInterfaces|Třídu služby zadaného typu definuje třídu ServiceContract a dědí třídu ServiceContract od zadaného typu. Dědičnost kontraktů lze použít pouze mezi typy rozhraní. Pokud má třída označení ServiceContractAttribute, musí být jediný typ v hierarchii třídou ServiceContractAttribute.  Přesuňte třídu ServiceContractAttribute na zadaný typ samostatné rozhraní, která implementuje zadaný typ.|  
|SFxCreateDuplexChannel1|Smlouva zpětného volání kontraktu zadané neexistuje nebo nedefinuje žádné operace. Pokud to není duplexní kontrakt, použijte třídy ChannelFactory namísto třídy DuplexChannelFactory.|  
|SFxCreateDuplexChannelNoCallback|Přetížení CreateChannel nelze vyvolat v této instanci třídy DuplexChannelFactory. Třída DuplexChannelFactory nebyla inicializována s třídu InstanceContext. Vyvolejte přetížení CreateChannel, které převezme třídu InstanceContext.|  
|SFxCreateDuplexChannelNoCallback1|Přetížení CreateChannel nelze vyvolat v této instanci třídy DuplexChannelFactory. Třída DuplexChannelFactory nebyla inicializována typem a nebyl poskytnut žádný platná třída InstanceContext. Vyvolejte přetížení CreateChannel, které převezme třídu InstanceContext.|  
|SFxCreateDuplexChannelNoCallbackUserObject|Přetížení CreateChannel nelze vyvolat v této instanci třídy DuplexChannelFactory. Třída InstanceContext poskytnutá třídě DuplexChannelFactory neobsahuje platnou třídu UserObject.|  
|SFxCreateNonDuplexChannel1|Třída ChannelFactory nepodporuje kontrakt zadaný. Třídy ChannelFactory definuje kontrakt zpětného volání s jednu nebo více operací. Použití třídy DuplexChannelFactory namísto třídy ChannelFactory.|  
|SFxCustomBindingNeedsTransport1|Třída CustomBinding na třídě ServiceEndpoint se zadaným kontrakt neobsahuje třídu TransportBindingElement. Každá vazba musí mít alespoň jeden element vazby, která je odvozena od třídy TransportBindingElement.|  
|SFxCustomBindingWithoutTransport|Schéma nelze vypočítat pro tuto vlastní vazby protože neobsahuje třídu TransportBindingElement. Každá vazba musí mít alespoň jeden element vazby, která je odvozena od třídy TransportBindingElement.|  
|SFxDataContractSerializerDoesNotSupportBareArray|Třída DataContractSerializer nepodporuje kolekci určenou v zadaného prvku.|  
|SFxDictionaryIsEmpty|Operaci nelze provést, protože slovník je prázdný.|  
|SFxDocEncodedNotSupported|Chyba při reflexi zadaný. Kódování dokumentů se nepodporuje. Změňte "Používá se" na literál nebo 'Style' na RPC.|  
|SFxDuplicateInitiatingActionAtSameVia|Tato služba obsahuje několik koncových bodů naslouchání v zadaném. Koncové body sdílejí stejnou inicializační akci zadané. Zprávy s touto akcí by vyřadit, protože dispečer by nemohl určit správný koncový bod pro zpracování zprávy.|  
|SFXEndpointBehaviorUsedOnWrongSide|Zadanou třídu IEndpointBehavior nelze použít na serveru. Toto chování můžete platí jenom pro klienty.|  
|SFxEndpointNoMatchingScheme|Základní adresa, která odpovídá zadané schéma pro koncový bod s určenou vazbu nebyl nalezen. Základní adresa registrovaná schémata nejsou zadány.|  
|SFxErrorCreatingMtomReader|Při vytváření čtečky zpráv přenosu optimalizace mechanismus zprávy došlo k chybě.|  
|SFxErrorDeserializingFault|Server vrátil chybu neplatná jednoduchý objekt přístup k protokolu. Další podrobnosti najdete u třídy InnerException.|  
|SFxErrorDeserializingHeader|Došlo k chybě při deserializaci jednoho ze záhlaví ve zprávě zadané. Další podrobnosti naleznete u třídy InnerException.|  
|SFxErrorReflectingOnMethod3|Došlo k chybě při načítání zadaný atribut na zadanou metodu v zadaném typu.  Další podrobnosti najdete u třídy InnerException.|  
|SFxErrorReflectingOnParameter4|Došlo k chybě při načítání atribut zadaný u zadaného parametru zadanou metodu v zadaném typu. Další podrobnosti najdete u třídy InnerException.|  
|SFxErrorReflectingOnType2|Došlo k chybě při načítání atribut zadaný u zadaného typu.  Další podrobnosti najdete u třídy InnerException.|  
|SFxErrorSerializingBody|Došlo k chybě při serializaci textu zprávy zadané. Další podrobnosti najdete u třídy InnerException.|  
|SFxErrorSerializingHeader|Došlo k chybě při serializaci jednoho ze záhlaví ve zprávě zadané. Další podrobnosti najdete u třídy InnerException.|  
|SFxExpectedIMethodCallMessage|Vnitřní chyba Zpráva musí být platnou třídou IMethodCallMessage.|  
|SFxExportMustHaveType|Je specifikovaná část v zadané operaci nejde exportovat, protože nemá platný typ CLR.|  
|SFxHeaderNotUnderstood|Zpráva nebyla zpracována. Zadaná hlavička ze zadaného oboru názvů nebyla rozpoznána příjemce této zprávy. Tato chyba obvykle značí, že odesílatel zprávy povolil komunikační protokol, který příjemce nemůže zpracovat. Ujistěte se, že je konfigurace klientovy vazby konzistentní s vazbou službu.|  
|SFxHeadersAreNotSupportedInEncoded|Zadaná zpráva nesmí mít záhlaví určená ve stylu kódování volání vzdálených procedur.|  
|SFxInconsistentWsdlOperationStyleInMessageParts|Všechny části zprávy v zadané operaci musí obsahovat typ nebo element.|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|Určený styl odvozený od zpráv v zadané operaci neodpovídá zadané očekávanému stylu zadat pomocí vazby.|  
|SFxInvalidCallbackIAsyncResult|Třída IAsyncResult není k dispozici nebo je nesprávného typu.|  
|SFxInvalidMessageBody|Formátovací modul OperationFormatter zjistil neplatné pole se zprávy. Byl očekáván typ "Element" uzel se zadaným názvem a oborem názvů. Byl zjištěn typ zadaný uzel se zadaným názvem a oborem názvů.|  
|SFxInvalidMessageBodyEmptyMessage|Třída OperationFormatter nemůže rekonstruovat informace ze zprávy, protože zpráva je prázdná.|  
|SFxInvalidMessageBodyErrorDeserializingParameter|Došlo k chybě při pokusu o deserializaci zadaný parametr. Další informace naleznete u třídy InnerException.|  
|SFxInvalidMessageBodyErrorSerializingParameter|Došlo k chybě při pokusu o deserializaci zadaný parametr. Zpráva InnerException byla zadána.  Další podrobnosti najdete u třídy InnerException.|  
|SFxInvalidMessageBodyUnexpectedNode|Došlo k zadaný neočekávaný uzel ze zadaného oboru názvů při rekonstrukci parametrů.|  
|SFxInvalidMessageContractSignature|Zadaná operace má parametr nebo návratový typ označeného atributem MessageContractAttribute. Při představovat zprávu žádosti pomocí kontraktu zprávy, musí mít operace jeden parametr označeného atributem MessageContractAttribute. Když představovat zprávu odpovědi pomocí kontraktu zprávy, operace vrácená hodnota musí být typ, který je označen MessageContractAttribute. Operace nemůže mít žádné "out" nebo "ref" parametry.|  
|SFxInvalidReplyAction|Odchozí zpráva odpovědi pro operaci se zadanou akci, ale kontrakt pro tuto operaci Určuje třídu ReplyAction jiný. Akce určená ve zprávě musí odpovídat třídě ReplyAction v kontraktu nebo musí kontrakt určovat třídu ReplyAction = "*".|  
|SFxInvalidRequestAction|Odchozí zpráva požadavku pro operaci se zadanou akci, ale kontrakt pro tuto operaci Určuje jinou RequestAction. Akce určená ve zprávě musí odpovídat RequestAction v kontraktu nebo musí kontrakt určovat RequestAction = "*".|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|Statickou metodu CreateChannel nelze použít s kontraktem zadaný, protože tento kontrakt definuje kontrakt zpětného volání. Použijte jednu ze statických přetížení CreateChannel pro třídu DuplexChannelFactory\<TChannel >.|  
|SFxInvalidStreamInRequest|Požadavek v zadané operace bude datový proud, musí mít operace jeden parametr, jehož typ je Stream.|  
|SFxInvalidStreamInResponse|Operace pro odpověď v rámci zadané operace bude datový proud, musí mít jeden parametr nebo návratová hodnota, jejíž typ je Stream.|  
|SFxInvalidStreamInTypedMessage|Použití datových proudů s kontraktu zprávy programovací model, zadaný typ musí mít jeden člen MessageBody, jehož typ je Stream.|  
|SFxInvalidUseOfPrimitiveOperationFormatter|Třídě PrimitiveOperationFormatter byl zadán parametr nebo návratový typ, který nepodporuje.|  
|SFxMessageContractBaseTypeNotValid|Zadaný typ MessageContract definovat a odvozuje se od zadaného typu, který MessageContract nedefinuje. Všechny objekty v hierarchii dědičnosti zadané musí definovat parametr MessageContract.|  
|SFxMethodNotSupported1|Určená metoda není podporována u tohoto objektu. Tomu může dojít, pokud metoda není označena třídou OperationContractAttribute, nebo pokud typ rozhraní není označen třídou ServiceContractAttribute.|  
|SFxMethodNotSupportedByType2|Zadaný typ implementace ServiceHost neimplementuje kontrakt zadaná služba.|  
|SFxMethodNotSupportedOnCallback1|Zadaná metoda zpětného volání není podporován. Tomu může dojít, pokud metoda není označena třídou OperationContractAttribute, nebo pokud typ rozhraní není cílem CallbackContract atribut ServiceContractAttribute.|  
|SFxMismatchedOperationParent|Třída DispatchOperation nebo ClientOperation lze přidat pouze k nadřazené úloze DispatchRuntime nebo ClientRuntime v uvedeném pořadí.|  
|SFxNameCannotBeEmpty|Vlastnost Name nemůže být prázdný řetězec.|  
|SfxNoTypeSpecifiedForParameter|Typ CLR byl zadán pro parametr, který brání operaci. nefunkční.|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute může nacházet pouze na třídu služby. Nelze jej umístit do rozhraní ServiceContract. Zadanou metodu na zadaný typ toto porušuje.|  
|SFxOperationContractOnNonServiceContract|Zadaná metoda je označena třídou OperationContractAttribute, ale nadřazený zadaný typ není označen třídou ServiceContractAttribute. Atribut OperationContractAttribute jde použít jenom u metod v typech ServiceContractAttribute nebo u jejich typů CallbackContract.|  
|SFxParameterCountMismatch|Došlo k neshodě mezi počet dodaných argumentů a počet očekávaných argumentů. Konkrétně zadaný argument má zadaný počet prvků, zatímco očekávaný argument má zadaný počet prvků.|  
|SFxPartNameMustBeUniqueInRpc|Název součásti zadaná zpráva není jedinečný ve zprávě volání vzdálených procedur.|  
|SFxReplyActionMismatch3|Byla přijata zpráva odpovědi pro zadanou operaci se zadanou akci. Váš klientský kód však vyžaduje na zadanou akci.|  
|SFxRequestReplyNone|Byla přijata zpráva se WS-Addressing ReplyTo nebo FaultTo s cílem na "None" adresu. Tyto hodnoty nejsou pro operace požadavek odpověď platné. Použijte jednocestnou operaci nebo povolte vlastnost ManualAddressing, pokud potřebujete podporovat hodnotu ReplyTo nebo FaultTo hodnoty "None".|  
|SFxRequestTimedOut1|Tato operace požadavku nepřijala odpověď v zadaném čase nakonfigurovaná. Čas povolené byl pravděpodobně částí delšího časového limitu. To může být, že služba stále zpracovává operaci nebo že služba nemohla odeslat zprávu s odpovědí.|  
|SFxRequestTimedOut2|Operace požadavku odeslaná do zadaného umístění nepřijala odpověď během určené doby nakonfigurované. Čas povolené byl pravděpodobně částí delšího časového limitu. To může být, že služba stále zpracovává operaci nebo že služba nemohla odeslat zprávu s odpovědí.|  
|SFxSchemaDoesNotContainType|Schéma s oborem názvů zadaný cíl neobsahuje typ se zadaným názvem.|  
|SfxServiceContractAttributeNotFound|Typ zadaný smlouvy nemá atribut ServiceContractAttribute. Chcete-li definován platný kontrakt, zadaný typ musí být atribut ServiceContractAttribute. Typ může být buď rozhraní kontraktu nebo třída služby.|  
|SFxServiceContractGeneratorConfigRequired|Chcete-li generovat informace o konfiguraci pomocí metody GenerateServiceEndpoint, musí být ServiceContractGenerator instance inicializována s platným objektem konfigurace.|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|Koncové body nelze přidat po hostitele ServiceHost je v jednom z následujících stavů:<br /><br /> -Otevřít<br />-Došlo k chybě<br />-Byl ukončen<br />-Uzavřeno|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Koncové body nelze přidat před inicializací vlastnosti popis.|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|HttpGetEnabled atributu ServiceMetadataBehavior je nastavena na hodnotu true a vlastnost HttpGetUrl je relativní adresa, ale neexistuje žádná základní adresa HTTP. Buď poskytněte základní adresu HTTP, nebo nastavte vlastnost HttpGetUrl na absolutní adresu.|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|HttpsGetEnabled atributu ServiceMetadataBehavior je nastavena na hodnotu true a vlastnost HttpsGetUrl je relativní adresa, ale neexistuje žádná základní adresa HTTPS. Buď poskytněte základní adresu HTTPS nebo nastavte vlastnost HttpsGetUrl na absolutní adresu.|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|Chování adresy Url musí být identifikátor URI relativní nebo absolutní URI identifikátoru s zadané schéma. Zadaná adresa Url je absolutní URI identifikátoru s zadané schéma.|  
|SFxStreamRequestMessageClosed|Zpráva obsahující tento proud byla zavřena. Proudy požadavků nelze otevřít po vrácení operace služby.|  
|SFxStreamResponseMessageClosed|Zpráva obsahující tento proud byla zavřena.|  
|SFxTerminateRequestProcessingException|Rozšíření v kanálu operaci musí ukončit zpracování této zprávy.|  
|SFxTerminatingOperationAlreadyCalled1|Tento kanál nemůže odeslat další zprávy, protože byla volána operace IsTerminating.|  
|SFxThrottleLimitMustBeGreaterThanZero0|Limit omezení musí být větší než nula. Limit omezovače zakázat, nastavte hodnotu na hodnotu Int32.MaxValue.|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|Při použití stylu kódováním RPC, typy kontraktů zpráv nebo typ System.ServiceModel.Channels.Message nelze použít, pokud operace nemá žádné parametry nebo návratovou hodnotu typu void. Přidat prázdný typ kontraktu zprávy jako parametr nebo návratový typ na zadané operace.|  
|SFxUserCodeThrewException|Zadaná uživatelská operace došlo k výjimce, která se neošetří v uživatelském kódu. Pokud je to opakované problém, může to znamenat chybu v implementaci zadané metodě.|  
|SfxUseTypedMessageForCustomAttributes|Zadaný parametr nemůže být mapována k parametru operaci, protože vyžaduje další atributy.|  
|SFxVersionMismatchInOperationContextAndMessage2|Nelze přidat odchozí záhlaví ke zprávě, protože verze MessageVersion v parametru OperationContext.Current se neshoduje s verzí záhlaví zpracovávané zprávy|  
|SFxWellKnownNonSingleton0|Chcete-li použít jeden z konstruktorů ServiceHost, který přebírá instanci služby, musí být režim InstanceContextMode služby nastavena na hodnotu InstanceContextMode.Single. To lze konfigurovat pomocí atributu ServiceBehaviorAttribute. Jinak použijte konstruktory ServiceHost, které přebírají argument typ.|  
|SFxWrapperTypeHasMultipleNamespaces|Typ obálky pro zadanou zprávu nelze promítat jako typ kontraktu dat, protože má více oborů názvů. Pomocí třídy XmlSerializer.|  
|UriMustBeAbsolute|Identifikátor URI musí být absolutní.|
