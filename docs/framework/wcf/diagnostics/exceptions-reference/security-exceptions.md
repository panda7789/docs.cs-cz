---
title: Výjimky zabezpečení
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
ms.openlocfilehash: c1eeca9111837b9833de54ecafbc981d1c2b6343
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201371"
---
# <a name="security-exceptions"></a>Výjimky zabezpečení
Toto téma obsahuje seznam všech bezpečnostním výjimkám.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|Služba neumožňuje nedovoluje anonymní přihlášení.|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|Musí být chráněné zprávy s požadavkem. Vyžaduje to operace kontraktu zadané. Ochranu musí poskytnout určenou vazbu.|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Zprávy s odpovědí musí být chráněné. Vyžaduje to operace kontraktu zadané. Ochranu musí poskytnout určenou vazbu.|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|V záhlaví zabezpečení je povolen pouze jeden primární podpis.|  
|BadContextTokenFaultReason|Token kontextu zabezpečení vypršela nebo není platný. Zpráva nebyla zpracována.|  
|BadEncryptionState|Třída EncryptedData nebo EncryptedKey je v neplatném stavu pro tuto operaci.|  
|BasicHttpMessageSecurityRequiresCertificate|Vazba BasicHttp vyžaduje, aby třída BasicHttpBinding.Security.Message.ClientCredentialType na pověření BasicHttpMessageCredentialType.Certificate pro zabezpečené zprávy. Vyberte zabezpečení Transport nebo TransportWithMessageCredential pro pověření uživatelských jmen.|  
|BasicTokenCannotBeWrittenWithoutEncryption|Základní token nelze zapsat bez šifrování.|  
|BindingDoesNotSupportProtectionForRst|Zadaná vazba pro zadaný smlouvy je nakonfigurována s SecureConversation, ale režim ověřování není schopen poskytnout integritu založené na požadavku/odpovědi a důvěrnost požadovanou pro vyjednávání.|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|Operace zadané kontrakt vyžaduje Windows identity pro automatické zosobnění. Zadaný vazbou pro zadanou kontraktu není k dispozici identita Windows, která představuje volajícího.|  
|CachedNegotiationStateQuotaReached|Službu nelze stav vyjednávání mezipaměti, protože byla dosažena určená kapacita. Zkuste požadavek.|  
|CacheQuotaReached|Položku nelze přidat. Je zadaná maximální velikost mezipaměti.|  
|CannotDetermineSPNBasedOnAddress|Klient nemůže určit že hlavní název služby založený na identitě zadané cílové adresy pro účely účel třídy SspiNegotiation nebo protokolu Kerberos. Identitou cílové adresy musí být identita UPN (jako například acmedomain\\\alice) nebo identita SPN (například host/honzuv pocitac).|  
|CannotFindCert|Nelze najít certifikát X.509 pomocí kritérií zadaného hledání: StoreName, StoreLocation, FindType, FindValue.|  
|CannotFindCertForTarget|Nelze najít certifikát X.509 pomocí kritérií zadaného hledání: StoreName, StoreLocation, FindType, FindValue pro zadaný cíl.|  
|CannotFindCorrelationStateForApplyingSecurity|Nelze najít stav korelace pro použití zabezpečení na odpověď na straně odpovídajícího.|  
|CannotFindNegotiationState|Nelze najít stav vyjednávání pro zadaný kontext.|  
|CannotFindSecuritySession|Nelze najít relaci zabezpečení se zadaným ID.|  
|CannotImportProtectionLevelForContract|Zásada pro import procesu nemůže importovat vazbu pro zadaný kontrakt. Požadavky na ochranu pro vazbu nejsou slučitelné s vazbou již byla naimportována pro kontrakt. Vazbu je nutné překonfigurovat.|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|Import zásady zabezpečení se nezdařilo. Zásada zabezpečení zahrnuje požadavky podpůrného tokenu v rámci operace. Popis kontraktu neurčuje akci pro zprávu s požadavkem asociovanou s touto operací.|  
|CannotIssueRstTokenType|Nelze vydat typ tokenu nebo zadaný.|  
|CannotObtainIssuedTokenKeySize|Nelze určit velikost klíče vydaného tokenu.|  
|CannotPerformImpersonationOnUsernameToken|Zosobnění pomocí tokenu klienta není možné. Určenou vazbu pro zadaný kontrakt používá Token zabezpečení pro ověřování klientů s zprostředkovatelem členství zaregistrovaný. Použijte jiný typ tokenu zabezpečení pro klienta.|  
|CannotPerformS4UImpersonationOnPlatform|Zadaná vazba pro zadaný kontraktu podporuje zosobnění pouze pro [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] a novější verze systému Windows. Použijte ověření SspiNegotiated a vazbu se zabezpečenou konverzací s povoleným zrušením.|  
|CannotReadKeyIdentifier|Nelze číst identifikátoru klíče ze zadaného prvku s určený obor názvů.|  
|CannotReadToken|Nelze přečíst token ze zadaného prvku s určený obor názvů pro třídu BinarySecretSecurityToken s zadaný typ hodnoty. Pokud tento prvek se očekává platný, zkontrolujte, zda je zabezpečení nakonfigurováno pro využívání tokenů s názvem, obor názvů a hodnota typu zadaný.|  
|CertificateUnsupportedForHttpTransportCredentialOnly|Ověřování pomocí certifikátu klienta se nepodporuje v režimu zabezpečení TransportCredentialOnly. Vyberte režim zabezpečení Transport.|  
|ClaimTypeCannotBeEmpty|Třídou claimType nesmí být prázdný řetězec.|  
|ClientCertificateNotProvided|Certifikát pro klienta nebyl uveden. Certifikát lze nastavit ve třídě ClientCredentials nebo ServiceCredentials.|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|Třída ClientCredentialType.None není pro režim zabezpečení TransportWithMessageCredential platný. Zadejte typ přihlašovacích údajů nebo použijte jiný režim zabezpečení.|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Konfigurační schéma je pro popis nestandardní konfigurace následujícího elementu vazby zabezpečení nedostatečné:|  
|DerivedKeyTokenGenerationAndLengthTooHigh|Odvozeného klíče podle generace a délka výsledku, který je větší než maximální povolený posun posun odvození klíče.|  
|DnsIdentityCheckFailedForIncomingMessage|Kontrola identity příchozí zprávy se nezdařila. Byla zadána identita system (DNS) očekávané domény název vzdáleného koncového bodu. Vzdálený koncový bod vydal, deklarace identity v systému názvů zadané doméně (DNS). Pokud se jedná o legitimní vzdálený koncový bod, můžete problém vyřešit tak, že zadáte identitu systému název domény jako vlastnosti identita třídy EndpointAddress při vytváření kanálu proxy.|  
|DnsIdentityCheckFailedForOutgoingMessage|Kontrola identity se nezdařila pro zprávu, která se objeví. Vzdálený koncový bod by měl identita zadaná doména název systému. Vzdálený koncový bod vydal, deklarace identity v systému názvů domény (DNS). Pokud se jedná o legitimní vzdálený koncový bod, můžete problém vyřešit explicitním určením DNS identity jako vlastnosti identita třídy EndpointAddress při vytváření kanálu proxy.|  
|DuplicateIdInMessageToBeVerified|Zadané id se vyskytl dvakrát ve zprávě dodané k ověření.|  
|EmptyBase64Attribute|Pro požadovaný atribut base-64 názvem a oborem názvů byla nalezena prázdná hodnota.|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Export zásad zabezpečení se nezdařilo. Vazba obsahuje AsymmetricSecurityBindingElement i element vazby zabezpečení přenosu. Export zásad pro takovou vazbu není podporován.|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Export zásad zabezpečení se nezdařilo. Vazba obsahuje třídu SymmetricSecurityBindingElement i element vazby zabezpečení přenosu. Export zásad pro takovou vazbu není podporován.|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Export zásad zabezpečení se nezdařilo. Vazba obsahuje třídu TransportSecurityBindingElement, ale žádný element vazby přenosu, který implementuje třídu ITransportTokenAssertionProvider. Export zásad pro takovou vazbu není podporován. Zkontrolujte, zda že element vazby přenosu ve vazbě implementuje rozhraní ITransportTokenAssertionProvider.|  
|FoundMultipleCerts|Bylo nalezeno více certifikátů X.509 pomocí kritérií zadaného hledání: StoreName, StoreLocation, FindType, FindValue. Zadejte přesnější hledanou hodnotu.|  
|FoundMultipleCertsForTarget|Bylo nalezeno více certifikátů X.509 pomocí kritérií zadaného hledání: StoreName, StoreLocation, FindType, FindValue pro zadaný cíl. Zadejte přesnější hledanou hodnotu.|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|Třída SecurityVersion.WSSecurityJan2004 nepodporuje dešifrování záhlaví. Použít SecurityVersion.WsSecurityXXX2005 a vyšší nebo pro šifrování celé zprávy použijte zabezpečení přenosu.|  
|IdentityCheckFailedForIncomingMessage|Kontrola identity příchozí zprávy se nezdařila. Očekávaná identita je určena pro cílový koncový bod.|  
|IdentityCheckFailedForOutgoingMessage|Kontrola identity odchozí zprávy se nezdařila. Očekávaná identita je určena pro cílový koncový bod.|  
|IncorrectSpnOrUpnSpecified|Ověření Security Support Provider Interface (SSPI) se nezdařilo. Na serveru není spuštěna v rámci účtu se zadanou identitou. Pokud je server spuštěn v účtu služby (například síťové služby), zadejte účtu ServicePrincipalName jako identitu ve třídě EndpointAddress pro server. Pokud server běží v uživatelském účtu, zadejte účtu UserPrincipalName jako identitu ve třídě EndpointAddress pro server.|  
|InvalidAttributeInSignedHeader|Zadaná hlavička podepsaný držitelem obsahuje zadaného atributu. Očekávaný atribut je zadán.|  
|InvalidCloseResponseAction|Odpověď zavřít relace zabezpečení byla přijata s zadaná neplatná akce.|  
|InvalidQName|Název QName je neplatná.|  
|InvalidRenewResponseAction|Odpověď na obnovení relace zabezpečení byla přijata s zadaná neplatná akce.|  
|InvalidSspiNegotiation|Vyjednávání rozhraní zprostředkovatele podpory zabezpečení se nezdařilo.|  
|IssuerBindingNotPresentInTokenRequirement|Správce tokenů zabezpečení vyžaduje zadání požadavek na token, který popisuje zabezpečené konverzace prvku vazby zabezpečení samozavádění. Požadavek tokenu je určena následujícím způsobem.|  
|KeyLengthMustBeMultipleOfEight|Zadaná délka klíče není násobkem 8 pro symetrické klíče.|  
|LsaAuthorityNotContacted|Vnitřní chyba SSL (viz část o kódu stavů Win32). Ověřit certifikát serveru k určení, zda je schopen výměny klíče.|  
|MaximumPolicyRedirectionsExceeded|Byl dosažen limit načtení rekurzivní zásady. Zaškrtněte, pokud chcete zjistit, zda je smyčka v řetězu služby federation service.|  
|MessagePartSpecificationMustBeImmutable|Specifikace části zprávy musí být změněna na konstantní před nastavením.|  
|MissingCustomCertificateValidator|Třída X509CertificateValidationMode.Custom vyžaduje CustomCertificateValidator. Určete vlastnost CustomCertificateValidator.|  
|MissingCustomUserNamePasswordValidator|Třída UserNamePasswordValidationMode.Custom vyžaduje CustomUserNamePasswordValidator. Určete vlastnost CustomUserNamePasswordValidator.|  
|MissingMembershipProvider|Třída UserNamePasswordValidationMode.MembershipProvider vyžaduje MembershipProvider. Určete vlastnost MembershipProvider.|  
|NoBinaryNegoToSend|Žádné binární vyjednávání se odeslala na druhou stranu.|  
|NoEncryptionPartsSpecified|Pro zprávy s určenou akcí nebyly určeny žádné části zprávy šifrování.|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|Hodnota KeyInfo nebyla nalezena v zašifrované položce pro nalezení dešifrovaného tokenu.|  
|NonceLengthTooShort|Určená hodnota nonce je příliš krátký. Minimální požadovaná délka hodnoty nonce je 4 bajty.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Žádná odchozí třída EndpointAddress je k dispozici pro kontrolu identity ve zprávě k odeslání.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Žádná odchozí třída EndpointAddress je k dispozici pro kontrolu identity na byla přijata odpověď.|  
|NoPartsOfMessageMatchedPartsToSign|Nebyl vytvořen žádný podpis, protože žádná část zprávy neodpovídají zadané specifikaci části zprávy.|  
|NoPrincipalSpecifiedInAuthorizationContext|V kontextu autorizace není určena žádná vlastní hlavní.|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Není dostupný v záhlaví zabezpečení by poskytoval hodnotu nonce pro zjišťování opakování podpis.|  
|NoSignaturePartsSpecified|Pro zprávy s určenou akcí nebyly určeny žádné části zpráv podpis.|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Žádný podpisový token je možné provést kontroly příchozí identity.|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Žádné časové razítko není k dispozici v záhlaví zabezpečení pro zjišťování opětovného přehrání.|  
|NoTransportTokenAssertionProvided|Poradce zásad zabezpečení selhal. Zadaný kontrolní výraz tokenu přenosu zadaného typu nevytvořil kontrolní výraz tokenu přenosu zahrnout kontrolního výrazu zásad zabezpečení SP: TransportBinding.|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Symetrický protokol zabezpečení lze konfigurovat s poskytovatelem symetrického tokenu a symetrický ověřovací data tokenu nebo symetrickým poskytovatelem tokenu. Nelze jej konfigurovat s oběma.|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Tuto operaci nelze provést v záhlaví zabezpečení příjemce.|  
|OperationDoesNotAllowImpersonation|Zadaná služba operaci, která náleží ke kontraktu s zadaný název a obor názvů nedovoluje zosobnění.|  
|PolicyRequiresConfidentialityWithoutIntegrity|Zásada zabezpečení zprávy pro zadanou akci vyžaduje důvěrnost bez integrity. Důvěrnost bez integrity není podporována.|  
|PrimarySignatureIsRequiredToBeEncrypted|Primární podpis musí být zašifrován.|  
|PropertySettingErrorOnProtocolFactory|Požadovaná vlastnost na Výroba protokolu zabezpečení není nastavena nebo má neplatnou hodnotu.|  
|ProtocolFactoryCouldNotCreateProtocol|Výroba protokolu nemůže vytvořit protokol.|  
|PublicKeyNotRSA|Veřejný klíč není klíčem RSA.|  
|RequiredMessagePartNotEncrypted|Část zprávy zadané požadované nebyla zašifrována.|  
|RequiredMessagePartNotEncryptedNs|Část zprávy zadané požadované nebyla zašifrována.|  
|RequiredMessagePartNotSigned|Část zprávy zadané požadované nebyla podepsána.|  
|RequiredMessagePartNotSignedNs|Část zprávy zadané požadované nebyla podepsána.|  
|RequiredSecurityHeaderElementNotSigned|Element header zadaná zabezpečení se zadaným id musí být podepsané.|  
|RequiredSecurityTokenNotEncrypted|Zadaný "token zabezpečení s režimem zadané přílohy musí být zašifrován.|  
|RequiredSecurityTokenNotSigned|Musí být podepsán token zadaný zabezpečení s režimem zadané přílohy.|  
|RequiredSignatureMissing|Podpis se musí nacházet v záhlaví zabezpečení.|  
|RequireNonCookieMode|Určenou vazbu s určený obor názvů je konfigurována pro vydávání tokenů kontextu zabezpečení souborů cookie. Služby integrace modelu COM + nepodporují tokeny kontextu zabezpečení souborů cookie.|  
|RevertingPrivilegeFailed|Operace obnovení selhala se zadanou výjimkou.|  
|RSTRAuthenticatorIncorrect|Třída combinedhash třídy RequestSecurityTokenResponse je nesprávná.|  
|SecureConversationCancelNotAllowedFaultReason|Vazba nedovoluje zrušení zabezpečené konverzace.|  
|SecureConversationDriverVersionDoesNotSupportSession|Konfigurovaná verze SecureConversation nepodporuje relace. Použijte třídu WSSecureConversationFeb2005 nebo vyšší.|  
|SecureConversationRequiredByReliableSession|Nelze vytvořit stabilní relaci bez zabezpečené konverzace. Povolení zabezpečené konverzace.|  
|SecurityAuditFailToLoadDll|Zadaný dynamická knihovna (dll) se nepodařilo načíst.|  
|SecurityAuditNotSupportedOnChannelFactory|Třída SecurityAuditBehavior není ve výrobě kanálu podporována.|  
|SecurityAuditPlatformNotSupported|Zápis zpráv auditu do protokolu zabezpečení aktuální platforma není podporován. Musí zapsat auditní zprávy do protokolu aplikace.|  
|SecurityBindingElementCannotBeExpressedInConfig|Pro koncový bod byly importovány zásady zabezpečení. Zásady zabezpečení zahrnují požadavky, které nelze reprezentovat v konfiguraci Windows Communication Foundation. Vyhledejte poznámku o parametrech třídy SecurityBindingElement, které jsou nutné v konfiguračním souboru, který byl vygenerován. Vytvořte správný element vazby s kódem. Konfigurace vazby, který je v konfiguračním souboru není zabezpečený.|  
|SecurityBindingSupportsOneWayOnly|SecurityBinding určenou vazbu pro kontrakt zadané podporuje pouze operaci (OneWay).|  
|SecurityContextDoesNotAllowImpersonation|Nelze spustit zosobnění, protože třída SecurityContext pro roli UltimateReceiver ze zprávy požadavku s určenou akcí není mapována na identitu Windows.|  
|SecurityListenerClosing|Modul pro naslouchání nepřijímá nové zabezpečené konverzace, protože je ukončován.|  
|SecurityListenerClosingFaultReason|Server aktuálně nepřijímá nové zabezpečené konverzace protože je ukončován. Zkuste to prosím znovu později.|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|Výroba protokolu zabezpečení musí být nastavena před prováděním této operace.|  
|SecuritySessionAbortedFaultReason|Relace zabezpečení byla ukončena. Důvodem může být nebyly přijaty žádné zprávy v relaci příliš dlouho.|  
|SecuritySessionKeyIsStale|Klíč relace musí být obnoveno, než bude moci zabezpečovat zprávy aplikace.|  
|SecuritySessionLimitReached|Nelze vytvořit relaci zabezpečení. Zkuste to znovu později.|  
|SecuritySessionNotPending|Žádná relace zabezpečení se zadaným id čeká na vyřízení.|  
|SecurityTokenParametersHasIncompatibleInclusionMode|Zadaná vazba je nakonfigurována s parametrem tokenu zabezpečení, který má zadaný zabezpečení nekompatibilní režim zahrnutí tokenu. Zadejte režim zahrnutí tokenu alternativní zabezpečení.|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|Určenou vazbu pro kontrakt zadané byla nakonfigurována s nekompatibilní verzí zabezpečení, která nepodporuje nepřipojené odkazy na třídu EncryptedKeys. Použít konkrétní hodnotu nebo vyšší jako verzi zabezpečení vazby.|  
|SecurityVersionDoesNotSupportSignatureConfirmation|Zadaná verze SecurityVersion nepodporuje potvrzení podpisu. Použijte pozdější třídu SecurityVersion.|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|Určenou vazbu pro kontrakt zadané je nakonfigurována s verzí zabezpečení, která nepodporuje externí odkazy na tokeny X.509 používající hodnotu kryptografického otisku certifikátu. Použít konkrétní hodnotu nebo vyšší jako verzi zabezpečení vazby.|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Parametry tokenu zabezpečení musí být určeny s podpůrnými tokeny pro každou zprávu.|  
|ServerCertificateNotProvided|Příjemce neposkytl svůj certifikát. Tento certifikát je vyžadován protokol TLS. Obě strany musí mít přístup ke svým certifikátům.|  
|SignatureConfirmationNotSupported|Nakonfigurovaná verze SecurityVersion nepodporuje potvrzení podpisu. Použít WSSecurityXXX2005 nebo vyšší.|  
|SignatureConfirmationRequiresRequestReply|Výroba protokolu musí podporovat zabezpečení požadavku/odpovědi, aby nabízela potvrzení podpisu.|  
|SignatureNotExpected|Pro tuto zprávu není očekáván podpis.|  
|SigningTokenHasNoKeys|Zadaný podpisový token nemá žádné klíče. Token zabezpečení se používá v kontextu, který jej vyžaduje k provedení kryptografických operací, ale token neobsahuje žádné kryptografické klíče. Typ tokenu nepodporuje kryptografické operace nebo konkrétní instance tokenu neobsahuje kryptografické klíče. Zkontrolujte konfiguraci a ujistěte se, které typy tokenů (například UserNameSecurityToken) nejsou zadaná v kontextu, který vyžaduje kryptografické operace (například token podporující potvrzení).|  
|SpnegoImpersonationLevelCannotBeSetToNone|Rozhraní zprostředkovatele podpory zabezpečení nepodporuje zosobnění úrovně 'None'. Zadejte úroveň identifikace, zosobnění nebo delegování.|  
|SslClientCertMustHavePrivateKey|Zadaný certifikát musí mít privátní klíč. Proces musí mít přístupová práva k privátnímu klíči.|  
|SslServerCertMustDoKeyExchange|Zadaný certifikát musí mít privátní klíč, který je schopen výměny klíče. Proces musí mít přístupová práva k privátnímu klíči.|  
|StandardsManagerCannotWriteObject|Zadaný objekt nelze serializovat serializátoru tokenů.  Pokud se jedná vlastní typ, je nutné zadat vlastní serializátor.|  
|TimeStampHasCreationAheadOfExpiry|Časové razítko zabezpečení je neplatný, protože jeho čas vytvoření je větší než nebo roven jeho času vypršení platnosti.|  
|TimeStampHasCreationTimeInFuture|Časové razítko zabezpečení je neplatný, protože jeho čas vytvoření je v budoucnosti. Je zadaný aktuální čas a povolený časový posun je zadán.|  
|TimeStampHasExpiryTimeInPast|Časové razítko zabezpečení je zastaralé, protože jeho čas vypršení platnosti je v minulosti. Je zadaný aktuální čas a povolený časový posun je zadán.|  
|TimeStampWasCreatedTooLongAgo|Časové razítko zabezpečení je zastaralé, protože jeho čas vytvoření je příliš daleko v minulosti. Aktuální čas, maximální životnost časového razítka a povolený časový posun jsou určeny.|  
|TokenProviderCannotGetTokensForTarget|Poskytovatel tokenů nemůže získat tokeny pro zadaný cíl.|  
|TooManyIssuedSecurityTokenParameters|Větev spojeného řetězce zabezpečení obsahuje více parametrů IssuedSecurityTokenParameters. Systém InfoCard podporuje pro každou větev pouze jeden IssuedSecurityTokenParameters.|  
|TransportDoesNotProtectMessage|Určenou vazbu pro kontrakt zadané je nakonfigurované s režimem ověření, která vyžaduje přenos úrovni integrity a důvěrnosti. Přenos ale nemůže poskytnout integritu a důvěrnost.|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 nepodporuje vydávající certifikáty X.509 nebo třídu EncryptedKeys. Použijte verzi WsTrustFeb2005 nebo novější.|  
|TrustDriverVersionDoesNotSupportSession|Nakonfigurovaná verze Trust nepodporuje relace. Použijte verzi WSTrustFeb2005 nebo novější.|  
|UnableToCreateICryptoFromTokenForSignatureVerification|Nelze vytvořit rozhraní ICrypto z zadaný token pro ověření podpisu.|  
|UnableToCreateSymmetricAlgorithmFromToken|Zadaný symetrický algoritmus nelze vytvořit z tokenu.|  
|UnableToDeriveKeyFromKeyInfoClause|Zadaná klauzule třídy KeyInfo přeložit na zadaný token, který neobsahuje symetrický klíč, který lze použít k odvození.|  
|UnableToFindTokenAuthenticator|Nelze najít ověřovací data tokenu pro zadaný typ tokenu. Tokeny tohoto typu nemůže být přijat podle aktuálního nastavení zabezpečení.|  
|UnableToLoadCertificateIdentity|Nelze načíst identitu certifikátu X.509 zadanou v konfiguraci.|  
|UnexpectedEmptyElementExpectingClaim|Zadaný prvek z určený obor názvů je prázdný a neudává platnou deklaraci identity.|  
|UnknownEncodingInBinarySecurityToken|Nerozpoznané kódování došlo k chybě při čtení binárního tokenu zabezpečení.|  
|UnsecuredMessageFaultReceived|Od druhé strany byla přijata nezabezpečená nebo chybně zabezpečená chyba. Naleznete ve vnitřní výjimce FaultException kód chyby a podrobnosti.|  
|UnsupportedPasswordType|Zadané uživatelské jméno token má nepodporovaný typ hesla.|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|Nelze importovat zásady zabezpečení. Požadavky na ochranu pro zaváděcí vazbu zabezpečené konverzace nejsou podporovány. Požadavky na ochranu pro zavádění zabezpečené konverzace musí vyžadovat požadavek i odpověď na byly podepsány a šifrovány.|  
|UnsupportedSecurityPolicyAssertion|Kontrolní výraz zásad nepodporované zabezpečení byla zjištěna při importu zásad zabezpečení.|
