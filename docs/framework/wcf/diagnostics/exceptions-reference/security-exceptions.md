---
title: Výjimky zabezpečení
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
ms.openlocfilehash: e96c317862867b9e461eb2d13dce6ede5b30cf13
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348233"
---
# <a name="security-exceptions"></a>Výjimky zabezpečení

V tomto tématu jsou uvedeny všechny výjimky zabezpečení.

## <a name="exception-list"></a>Seznam výjimek

|Kód prostředku|Řetězec prostředku|
|-------------------|---------------------|
|AnonymousLogonsAreNotAllowed|Služba vám neumožňuje anonymní přihlášení.|
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|Zpráva požadavku musí být chráněná. To je vyžadováno operací zadaného kontraktu. Ochranu musí poskytnout Zadaná vazba.|
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Zpráva odpovědi musí být chráněná. To je vyžadováno operací zadaného kontraktu. Ochranu musí poskytnout Zadaná vazba.|
|AtMostOnePrimarySignatureInReceiveSecurityHeader|V záhlaví zabezpečení je povolen pouze jeden primární podpis.|
|BadContextTokenFaultReason|Token kontextu zabezpečení vypršel nebo je neplatný. Zpráva nebyla zpracována.|
|BadEncryptionState|Třída EncryptedData nebo EncryptedKey je pro tuto operaci v neplatném stavu.|
|BasicHttpMessageSecurityRequiresCertificate|Vazba BasicHttp vyžaduje, aby BasicHttpBinding. Security. Message. ClientCredentialType byla rovnocenná s typem přihlašovacích údajů BasicHttpMessageCredentialType. Certificate pro zabezpečené zprávy. Pro přihlašovací údaje uživatelského jména vyberte zabezpečení Transport nebo TransportWithMessageCredential.|
|BasicTokenCannotBeWrittenWithoutEncryption|Token Basic nelze zapsat bez šifrování.|
|BindingDoesNotSupportProtectionForRst|Zadaná vazba pro zadanou kontrakt je nakonfigurována pomocí SecureConversation, ale režim ověřování nemůže poskytnout integritu na žádost nebo odpověď na základě odpovědi a utajení vyžadované pro vyjednávání.|
|BindingDoesNotSupportWindowsIdenityForImpersonation|Zadaná operace kontraktu vyžaduje identitu systému Windows pro automatické zosobnění. Identita systému Windows, která představuje volajícího, není poskytnuta specifikovanou vazbou pro zadaný kontrakt.|
|CachedNegotiationStateQuotaReached|Služba nemůže ukládat do mezipaměti stav vyjednávání, protože byla dosažena zadaná kapacita. Opakujte požadavek.|
|CacheQuotaReached|Položku nelze přidat. Je zadaná maximální velikost mezipaměti.|
|CannotDetermineSPNBasedOnAddress|Klient nemůže určit hlavní název služby na základě identity v zadané cílové adrese pro účely SspiNegotiation/Kerberos. Identita cílové adresy musí být Identita hlavního názvu uživatele (UPN) (například například acmedomain\\\alice) nebo Identita hlavního názvu služby (například Host/honzuv-počítač).|
|CannotFindCert|Nelze najít certifikát X. 509 pomocí zadaných kritérií hledání: StoreName, StoreLocation, FindType, FindValue.|
|CannotFindCertForTarget|Nelze najít certifikát X. 509 pomocí zadaných kritérií hledání: StoreName, StoreLocation, FindType, FindValue pro zadaný cíl.|
|CannotFindCorrelationStateForApplyingSecurity|Nejde najít stav korelace pro použití zabezpečení na odpověď na odpovídajícím partnerovi.|
|CannotFindNegotiationState|Nelze nalézt stav vyjednávání pro zadaný kontext.|
|CannotFindSecuritySession|Nejde najít relaci zabezpečení se zadaným ID.|
|CannotImportProtectionLevelForContract|Zásada pro import procesu nemůže importovat vazbu pro zadaný kontrakt. Požadavky na ochranu pro vazbu nejsou kompatibilní s vazbou, která již byla pro daný kontrakt naimportována. Vazbu je nutné překonfigurovat.|
|CannotImportSupportingTokensForOperationWithoutRequestAction|Import zásad zabezpečení se nezdařil. Zásady zabezpečení obsahují požadavky na podporu tokenu v oboru operace. Popis kontraktu neurčuje akci pro zprávu požadavku přidruženou k této operaci.|
|CannotIssueRstTokenType|Nelze vystavit token nebo zadaný typ.|
|CannotObtainIssuedTokenKeySize|Nelze určit velikost klíče vydaného tokenu.|
|CannotPerformImpersonationOnUsernameToken|Zosobnění pomocí tokenu klienta není možné. Zadaná vazba pro zadanou kontrakt používá token zabezpečení uživatelského jména pro ověřování klientů pomocí registrovaného poskytovatele členství. Pro klienta použijte jiný typ tokenu zabezpečení.|
|CannotPerformS4UImpersonationOnPlatform|Zadaná vazba pro zadanou kontrakt podporuje zosobnění pouze v systému Windows Server 2003 a novějších verzích systému Windows. Použijte ověřování SspiNegotiated a vazbu se zabezpečenou konverzací s povoleným zrušením.|
|CannotReadKeyIdentifier|Nelze číst identifikátor elementu ze zadaného elementu se zadaným oborem názvů.|
|CannotReadToken|Nelze načíst token ze zadaného elementu se zadaným oborem názvů pro BinarySecretSecurityToken se zadaným typem ValueType. Pokud se očekává, že je tento element platný, zajistěte, aby bylo zabezpečení nastaveno na využívání tokenů se zadaným názvem, oborem názvů a typem hodnoty.|
|CertificateUnsupportedForHttpTransportCredentialOnly|Ověřování klientů založené na certifikátech není v režimu zabezpečení TransportCredentialOnly podporováno. Vyberte režim zabezpečení přenosu.|
|ClaimTypeCannotBeEmpty|Třídou claimType nesmí být prázdný řetězec.|
|ClientCertificateNotProvided|Nebyl zadán certifikát pro klienta. Certifikát lze nastavit ve třídě ClientCredentials nebo ServiceCredentials.|
|ClientCredentialTypeMustBeSpecifiedForMixedMode|ClientCredentialType. None není platný pro režim zabezpečení TransportWithMessageCredential. Zadejte typ přihlašovacích údajů nebo použijte jiný režim zabezpečení.|
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Schéma konfigurace není dostatečné pro popis nestandardní konfigurace následujícího elementu vazby zabezpečení:|
|DerivedKeyTokenGenerationAndLengthTooHigh|Výsledkem generování a délky odvozeného klíče je posun odvození klíče, který je větší než maximální povolený posun.|
|DnsIdentityCheckFailedForIncomingMessage|Ověření identity příchozí zprávy se nezdařilo. Byla zadána Očekávaná identita systému DNS (Domain Name System) vzdáleného koncového bodu. Vzdálený koncový bod poskytl zadanou deklaraci identity systému DNS (Domain Name System). Pokud se jedná o legitimní vzdálený koncový bod, můžete problém vyřešit tak, že při vytváření proxy kanálu zadáte identitu systému DNS jako vlastnost identity třídy EndpointAddress.|
|DnsIdentityCheckFailedForOutgoingMessage|Kontrolu identity u zprávy, která se nezdařila, se nezdařilo. Vzdálený koncový bod by měl mít zadanou identitu systému názvů domén. Vzdálený koncový bod poskytl deklaraci identity systému DNS (Domain Name System). Pokud se jedná o legitimní vzdálený koncový bod, můžete problém vyřešit tak, že explicitně zadáte identitu DNS jako vlastnost identity třídy EndpointAddress při vytváření proxy kanálu.|
|DuplicateIdInMessageToBeVerified|Ve zprávě, která je zadána k ověření, došlo dvakrát ke konkrétnímu ID.|
|EmptyBase64Attribute|Našla se prázdná hodnota pro požadovaný název atributu Base-64 a obor názvů.|
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Export zásad zabezpečení se nezdařil. Vazba obsahuje element vazby třída AsymmetricSecurityBindingElement i zabezpečený přenos. Export zásad pro takovou vazbu není podporován.|
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Export zásad zabezpečení se nezdařil. Vazba obsahuje element vazby SymmetricSecurityBindingElement i zabezpečený přenos. Export zásad pro takovou vazbu není podporován.|
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Export zásad zabezpečení se nezdařil. Vazba obsahuje TransportSecurityBindingElement, ale žádný element Transport Binding, který implementuje ITransportTokenAssertionProvider. Export zásad pro takovou vazbu není podporován. Ujistěte se, že prvek vazby přenosu ve vazbě implementuje rozhraní ITransportTokenAssertionProvider.|
|FoundMultipleCerts|Bylo nalezeno více certifikátů X. 509 pomocí zadaných kritérií hledání: StoreName, StoreLocation, FindType, FindValue. Zadejte konkrétnější hodnotu hledání.|
|FoundMultipleCertsForTarget|Bylo nalezeno více certifikátů X. 509 pomocí zadaných kritérií hledání: StoreName, StoreLocation, FindType, FindValue pro zadaný cíl. Zadejte konkrétnější hodnotu hledání.|
|HeaderDecryptionNotSupportedInWsSecurityJan2004|Třída SecurityVersion. WSSecurityJan2004 nepodporuje dešifrování hlaviček. Použijte třída SecurityVersion. WsSecurityXXX2005 a vyšší nebo použijte zabezpečení přenosu k zašifrování celé zprávy.|
|IdentityCheckFailedForIncomingMessage|Ověření identity příchozí zprávy se nezdařilo. Pro cílový koncový bod je zadána Očekávaná identita.|
|IdentityCheckFailedForOutgoingMessage|U odchozí zprávy se nepovedlo ověřit identitu. Pro cílový koncový bod je zadána Očekávaná identita.|
|IncorrectSpnOrUpnSpecified|Ověřování rozhraní SSPI (Security Support Provider Interface) se nezdařilo. Server možná není spuštěný v účtu se zadanou identitou. Pokud je server spuštěný v účtu služby (například síťová služba), zadejte v poli EndpointAddress pro server atribut ServicePrincipalName jako identitu. Pokud server běží v uživatelském účtu, zadejte atribut UserPrincipalName účtu jako identitu ve třídě EndpointAddress pro server.|
|InvalidAttributeInSignedHeader|Zadaná podepsaná hlavička obsahuje zadaný atribut. Byl zadán očekávaný atribut.|
|InvalidCloseResponseAction|Odpověď na zavření relace zabezpečení byla přijata se zadanou neplatnou akcí.|
|InvalidQName|Atribut QName je neplatný.|
|InvalidRenewResponseAction|Byla přijata odpověď obnovení relace zabezpečení se zadanou neplatnou akcí.|
|InvalidSspiNegotiation|Vyjednávání rozhraní zprostředkovatele podpory zabezpečení se nezdařilo.|
|IssuerBindingNotPresentInTokenRequirement|Správce tokenů zabezpečení vyžaduje zadání elementu vazby zabezpečení Bootstrap v požadavku tokenu, který popisuje zabezpečenou konverzaci. Požadavek tokenu je určen následujícím způsobem.|
|KeyLengthMustBeMultipleOfEight|Zadaná délka klíče není násobkem osmi pro symetrické klíče.|
|LsaAuthorityNotContacted|Došlo k vnitřní chybě SSL (podrobnosti najdete v kódu stavu Win32). Zkontrolujte certifikát serveru a zjistěte, jestli je schopný výměna klíčů.|
|MaximumPolicyRedirectionsExceeded|Bylo dosaženo limitu načítání rekurzivních zásad. Zkontrolujte, jestli existuje smyčka v řetězu federační služby.|
|MessagePartSpecificationMustBeImmutable|Specifikace části zprávy musí být před nastavením provedena na konstantní.|
|MissingCustomCertificateValidator|X509CertificateValidationMode. Custom vyžaduje CustomCertificateValidator. Zadejte vlastnost CustomCertificateValidator.|
|MissingCustomUserNamePasswordValidator|Třída UserNamePasswordValidationMode. Custom vyžaduje CustomUserNamePasswordValidator. Zadejte vlastnost CustomUserNamePasswordValidator.|
|MissingMembershipProvider|Třída UserNamePasswordValidationMode. MembershipProvider vyžaduje MembershipProvider. Zadejte vlastnost MembershipProvider.|
|NoBinaryNegoToSend|Druhé straně nebylo odesláno žádné binární vyjednávání.|
|NoEncryptionPartsSpecified|Pro zprávy se zadanou akcí nebyly zadány žádné části zprávy šifrování.|
|NoKeyInfoInEncryptedItemToFindDecryptingToken|V zašifrované položce se nepovedlo najít hodnotu KeyInfo pro nalezení dešifrovaného tokenu.|
|NonceLengthTooShort|Zadaná hodnota nonce je příliš krátká. Minimální požadovaná délka hodnoty nonce je 4 bajty.|
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|K dispozici není žádná odchozí třída EndpointAddress pro kontrolu identity na zprávě, která má být odeslána.|
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Žádná odchozí třída EndpointAddress není k dispozici pro kontrolu identity na přijaté odpovědi.|
|NoPartsOfMessageMatchedPartsToSign|Nebyl vytvořen žádný podpis, protože žádná část zprávy neodpovídala zadané specifikaci části zprávy.|
|NoPrincipalSpecifiedInAuthorizationContext|V autorizačním kontextu není zadaný žádný vlastní objekt zabezpečení.|
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|V záhlaví zabezpečení není k dispozici žádný podpis, který by poskytoval hodnotu NONCE pro detekci opakovaného přehrání.|
|NoSignaturePartsSpecified|Pro zprávy se zadanou akcí nebyly zadány žádné části zprávy s podpisem.|
|NoSigningTokenAvailableToDoIncomingIdentityCheck|K provedení kontroly příchozí identity není k dispozici žádný podpisový token.|
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|V záhlaví zabezpečení není k dispozici časové razítko pro detekci opakovaného přehrání.|
|NoTransportTokenAssertionProvided|Odborník na zásady zabezpečení se nezdařil. Zadaný kontrolní výraz tokenu přenosu zadaného typu nevytvořil kontrolní výraz přenosového tokenu, který by zahrnoval kontrolní výraz zásad zabezpečení SP: TransportBinding.|
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Symetrický protokol zabezpečení je možné nakonfigurovat pomocí zprostředkovatele symetrického tokenu a ověřovatele symetrického tokenu nebo poskytovatele asymetrického tokenu. Nedá se nakonfigurovat s oběma.|
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Tuto operaci nelze provést v hlavičkách zabezpečení přijímače.|
|OperationDoesNotAllowImpersonation|Zadaná operace služby, která patří ke kontraktu se zadaným názvem a oborem názvů, nepovoluje zosobnění.|
|PolicyRequiresConfidentialityWithoutIntegrity|Zásada zabezpečení zprávy pro zadanou akci vyžaduje důvěrnost bez integrity. Důvěrnost bez integrity není podporována.|
|PrimarySignatureIsRequiredToBeEncrypted|Primární podpis musí být zašifrovaný.|
|PropertySettingErrorOnProtocolFactory|Požadovaná vlastnost v zadané továrně protokolu zabezpečení není nastavena nebo má neplatnou hodnotu.|
|ProtocolFactoryCouldNotCreateProtocol|Výroba protokolu nemůže vytvořit protokol.|
|PublicKeyNotRSA|Veřejný klíč není klíčem RSA.|
|RequiredMessagePartNotEncrypted|Zadaná část zprávy nebyla zašifrována.|
|RequiredMessagePartNotEncryptedNs|Zadaná část zprávy nebyla zašifrována.|
|RequiredMessagePartNotSigned|Zadaná část zprávy není podepsaná.|
|RequiredMessagePartNotSignedNs|Zadaná část zprávy není podepsaná.|
|RequiredSecurityHeaderElementNotSigned|Zadaný element záhlaví zabezpečení se zadaným ID musí být podepsán.|
|RequiredSecurityTokenNotEncrypted|Zadaný token zabezpečení se zadaným režimem přílohy musí být zašifrovaný.|
|RequiredSecurityTokenNotSigned|Zadaný token zabezpečení se zadaným režimem přílohy musí být podepsán.|
|RequiredSignatureMissing|Signatura musí být v záhlaví zabezpečení.|
|RequireNonCookieMode|Zadaná vazba se zadaným oborem názvů je nakonfigurovaná tak, aby vydávala tokeny kontextu zabezpečení souborů cookie. Integrační služby COM+ nepodporují tokeny kontextu zabezpečení souborů cookie.|
|RevertingPrivilegeFailed|Operace vrácení zpět se nezdařila se zadanou výjimkou.|
|RSTRAuthenticatorIncorrect|Třída RequestSecurityTokenResponse Combinedhash třídy RequestSecurityTokenResponse je nesprávná.|
|SecureConversationCancelNotAllowedFaultReason|Vazba nepovoluje zrušení zabezpečené konverzace.|
|SecureConversationDriverVersionDoesNotSupportSession|Nakonfigurovaná verze SecureConversation nepodporuje relace. Použijte WSSecureConversationFeb2005 nebo vyšší.|
|SecureConversationRequiredByReliableSession|Nejde vytvořit spolehlivou relaci bez zabezpečené konverzace. Povolte zabezpečenou konverzaci.|
|SecurityAuditFailToLoadDll|Zadanou knihovnu DLL (Dynamic Link Library) se nepodařilo načíst.|
|SecurityAuditNotSupportedOnChannelFactory|Třída SecurityAuditBehavior není v továrně kanálu podporován.|
|SecurityAuditPlatformNotSupported|Zápis zpráv auditu do protokolu zabezpečení není aktuální platformou podporován. Je nutné zapsat zprávy o auditu do protokolu aplikace.|
|SecurityBindingElementCannotBeExpressedInConfig|Pro koncový bod se naimportovaly zásady zabezpečení. Zásady zabezpečení obsahují požadavky, které nemohou být reprezentovány v konfiguraci Windows Communication Foundation. Vyhledejte komentář k parametrům SecurityBindingElement, které jsou požadovány v generovaném konfiguračním souboru. Vytvořte správný element vazby s kódem. Konfigurace vazby, která je v konfiguračním souboru, není zabezpečená.|
|SecurityBindingSupportsOneWayOnly|Třída securitybinding vazby pro zadanou vazbu pro zadanou kontrakt podporuje pouze operaci OneWay.|
|SecurityContextDoesNotAllowImpersonation|Nelze spustit zosobnění, protože třída SecurityContext pro roli UltimateReceiver ze zprávy požadavku se zadanou akcí není namapována na identitu systému Windows.|
|SecurityListenerClosing|Naslouchací proces nepřijímá nové zabezpečené konverzace, protože je ukončován.|
|SecurityListenerClosingFaultReason|Server momentálně nepřijímá nové zabezpečené konverzace, protože je ukončován. Zkuste to prosím znovu později.|
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|Výroba protokolu zabezpečení musí být nastavena před provedením této operace.|
|SecuritySessionAbortedFaultReason|Relace zabezpečení byla ukončena. To může být způsobeno tím, že v relaci nejsou v relaci příliš dlouho přijaty žádné zprávy.|
|SecuritySessionKeyIsStale|Klíč relace musí být obnoven dříve, než bude moci zabezpečit zprávy aplikace.|
|SecuritySessionLimitReached|Nelze vytvořit relaci zabezpečení. Zkuste to znovu později.|
|SecuritySessionNotPending|Žádná relace zabezpečení se zadaným ID nečeká na vyřízení.|
|SecurityTokenParametersHasIncompatibleInclusionMode|Zadaná vazba je nakonfigurovaná s parametrem tokenu zabezpečení, který má zadaný nekompatibilní režim zahrnutí tokenu zabezpečení. Zadejte jiný režim zahrnutí tokenu zabezpečení.|
|SecurityVersionDoesNotSupportEncryptedKeyBinding|Zadaná vazba pro zadanou kontrakt je nakonfigurovaná s nekompatibilní verzí zabezpečení, která nepodporuje nepřipojené odkazy na EncryptedKeys. Použijte zadanou hodnotu nebo vyšší jako verzi zabezpečení pro vazbu.|
|SecurityVersionDoesNotSupportSignatureConfirmation|Zadaný třída SecurityVersion nepodporuje potvrzení podpisu. Použijte pozdější třída SecurityVersion.|
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|U zadané vazby pro zadanou kontrakt je nakonfigurována verze zabezpečení, která nepodporuje externí odkazy na tokeny X. 509 s použitím hodnoty kryptografického otisku certifikátu. Použijte zadanou hodnotu nebo vyšší jako verzi zabezpečení pro vazbu.|
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Parametry tokenu zabezpečení musí být určeny s podpůrnými tokeny pro každou zprávu.|
|ServerCertificateNotProvided|Příjemce neposkytl svůj certifikát. Tento certifikát je vyžadován protokolem TLS. Obě strany musí mít přístup k jejich certifikátům.|
|SignatureConfirmationNotSupported|Nakonfigurovaný třída SecurityVersion nepodporuje potvrzení podpisu. Použijte WSSecurityXXX2005 nebo vyšší.|
|SignatureConfirmationRequiresRequestReply|Výroba protokolu musí podporovat zabezpečení požadavku/odpovědi, aby nabízela potvrzení podpisu.|
|SignatureNotExpected|Pro tuto zprávu není očekáván podpis.|
|SigningTokenHasNoKeys|Zadaný podpisový token nemá žádné klíče. Token zabezpečení se používá v kontextu, který vyžaduje, aby prováděl kryptografické operace, ale token neobsahuje žádné kryptografické klíče. Buď typ tokenu nepodporuje kryptografické operace, nebo konkrétní instance tokenu neobsahuje kryptografické klíče. Zkontrolujte konfiguraci, abyste zajistili, že kryptograficky zakázané typy tokenů (například třída UserNameSecurityToken) nejsou zadány v kontextu, který vyžaduje kryptografické operace (například přidávajícím tokenem podpory).|
|SpnegoImpersonationLevelCannotBeSetToNone|Rozhraní zprostředkovatele podpory zabezpečení nepodporuje úroveň zosobnění None. Zadejte úroveň identifikace, zosobnění nebo delegování.|
|SslClientCertMustHavePrivateKey|Zadaný certifikát musí mít privátní klíč. Proces musí mít přístupová práva k privátnímu klíči.|
|SslServerCertMustDoKeyExchange|Zadaný certifikát musí mít privátní klíč, který podporuje výměnu klíčů. Proces musí mít přístupová práva k privátnímu klíči.|
|StandardsManagerCannotWriteObject|Serializátor tokenu nemůže serializovat zadaný objekt.  Pokud se jedná o vlastní typ, musíte zadat vlastní serializátor.|
|TimeStampHasCreationAheadOfExpiry|Časové razítko zabezpečení není platné, protože jeho čas vytvoření je větší nebo roven času jeho vypršení platnosti.|
|TimeStampHasCreationTimeInFuture|Časové razítko zabezpečení není platné, protože jeho čas vytvoření je v budoucnosti. Aktuální čas je zadaný a je povolený časový posun.|
|TimeStampHasExpiryTimeInPast|Časové razítko zabezpečení je zastaralé, protože jeho čas vypršení platnosti je v minulosti. Aktuální čas je zadaný a je povolený časový posun.|
|TimeStampWasCreatedTooLongAgo|Časové razítko zabezpečení je zastaralé, protože jeho čas vytvoření je příliš daleko zpátky v minulosti. Aktuální čas, maximální životnost časového razítka a povolený časový posun je zadaný.|
|TokenProviderCannotGetTokensForTarget|Poskytovatel tokenů nemůže získat tokeny pro zadaný cíl.|
|TooManyIssuedSecurityTokenParameters|Nožka řetězce federovaného zabezpečení obsahuje několik parametrů IssuedSecurityTokenParameters. Systém InfoCard pro každou nožku podporuje pouze jeden parametrů IssuedSecurityTokenParameters.|
|TransportDoesNotProtectMessage|Zadaná vazba pro zadanou kontrakt je nakonfigurována s režimem ověřování, který vyžaduje integritu a důvěrnost na úrovni přenosu. Přenos ale nemůže poskytnout integritu a důvěrnost.|
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 nepodporuje vydávání certifikátů X. 509 nebo EncryptedKeys. Použijte WsTrustFeb2005 nebo vyšší.|
|TrustDriverVersionDoesNotSupportSession|Nakonfigurovaná verze vztahu důvěryhodnosti nepodporuje relace. Použijte WSTrustFeb2005 nebo vyšší.|
|UnableToCreateICryptoFromTokenForSignatureVerification|Nelze vytvořit rozhraní ICrypto ze zadaného tokenu pro ověření podpisu.|
|UnableToCreateSymmetricAlgorithmFromToken|Z tokenu nelze vytvořit zadaný symetrický algoritmus.|
|UnableToDeriveKeyFromKeyInfoClause|Zadaná klauzule KeyInfo byla přeložena na zadaný token, který neobsahuje symetrický klíč, který lze použít k odvození.|
|UnableToFindTokenAuthenticator|Nejde najít ověřovací data tokenu pro zadaný typ tokenu. V souladu s aktuálním nastavením zabezpečení nelze tokeny daného typu přijmout.|
|UnableToLoadCertificateIdentity|Nelze načíst identitu certifikátu X. 509 zadanou v konfiguraci.|
|UnexpectedEmptyElementExpectingClaim|Zadaný element ze zadaného oboru názvů je prázdný a neudává platnou deklaraci identity identity.|
|UnknownEncodingInBinarySecurityToken|Při čtení binárního tokenu zabezpečení došlo k nerozpoznanému kódování.|
|UnsecuredMessageFaultReceived|Od druhé strany byla přijata nezabezpečená nebo nesprávně zabezpečená chyba. Viz vnitřní FaultException pro kód chyby a podrobnosti.|
|UnsupportedPasswordType|Zadaný token uživatelského jména má nepodporovaný typ hesla.|
|UnsupportedSecureConversationBootstrapProtectionRequirements|Nelze importovat zásady zabezpečení. Požadavky na ochranu pro spouštěcí vazby zabezpečené konverzace nejsou podporovány. Požadavky na ochranu pro zavedení zabezpečené konverzace musí vyžadovat, aby požadavek i odpověď byly podepsány a zašifrované.|
|UnsupportedSecurityPolicyAssertion|Během zadaného importu zásad zabezpečení byl zjištěn nepodporovaný kontrolní výraz zásad zabezpečení.|
