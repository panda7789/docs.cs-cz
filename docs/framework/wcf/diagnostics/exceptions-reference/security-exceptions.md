---
title: Výjimky zabezpečení
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 057d01ba918a41df0bdf2acc30c9bb35777ebc27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security-exceptions"></a>Výjimky zabezpečení
Toto téma uvádí všechny výjimky zabezpečení.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|Služba neumožňuje anonymní přihlášení.|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|Zpráva požadavku musí být chráněny. To je vyžadováno operace zadaný kontraktu. Ochranu musí být poskytnuta Zadaná vazba.|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Zpráva odpovědi musí být chráněny. To je vyžadováno operace zadaný kontraktu. Ochranu musí být poskytnuta Zadaná vazba.|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|V záhlaví zabezpečení je povolen pouze jeden primární podpis.|  
|BadContextTokenFaultReason|Token kontextu zabezpečení platnost nebo není platný. Zpráva nebyla zpracována.|  
|BadEncryptionState|EncryptedData nebo EncryptedKey je v neplatném stavu pro tuto operaci.|  
|BasicHttpMessageSecurityRequiresCertificate|BasicHttp vyžaduje, aby třída BasicHttpBinding.Security.Message.ClientCredentialType na pověření BasicHttpMessageCredentialType.Certificate pro zabezpečené zprávy. Vyberte zabezpečení Transport nebo TransportWithMessageCredential pro přihlašovací údaje uživatelského jména.|  
|BasicTokenCannotBeWrittenWithoutEncryption|Základní token nelze zapsat bez šifrování.|  
|BindingDoesNotSupportProtectionForRst|Zadaná vazba pro zadaný kontrakt nastavena SecureConversation, ale režim ověřování není schopen poskytnout založené na požadavku nebo odpovědi integrity a důvěrnosti požadované pro vyjednávání.|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|Zadaný kontrakt operace vyžaduje Windows identity pro automatické zosobnění. Identitu systému Windows, který představuje volající není poskytovaný Zadaná vazba pro zadaný kontrakt.|  
|CachedNegotiationStateQuotaReached|Službu nelze mezipaměti vyjednávání stavu, protože bylo dosaženo zadanou kapacitou. Opakujte žádost.|  
|CacheQuotaReached|Položku nelze přidat. Maximální velikost mezipaměti je zadán.|  
|CannotDetermineSPNBasedOnAddress|Klient nemůže určit že hlavní název služby na základě identity v zadané cílové adresy pro účely účel třídy SspiNegotiation nebo Kerberos. Identitou cílové adresy musí být identitu hlavní název uživatele (například acmedomain\\\alice) nebo identita hlavního názvu služby (např. hostitele/honzuv machine).|  
|CannotFindCert|Nebyl nalezen certifikát X.509 pomocí zadaná kritéria vyhledávání: StoreName, StoreLocation, FindType, FindValue.|  
|CannotFindCertForTarget|Nelze najít certifikát The X.509 pomocí zadaná kritéria vyhledávání: StoreName, StoreLocation, FindType, FindValue pro zadaný cíl.|  
|CannotFindCorrelationStateForApplyingSecurity|Nelze najít korelace stavu pro použití zabezpečení odpoví na odpovídající partner.|  
|CannotFindNegotiationState|Nelze najít stav vyjednávání pro zadaný kontext.|  
|CannotFindSecuritySession|Nelze najít relace zabezpečení se zadaným ID.|  
|CannotImportProtectionLevelForContract|Zásady pro import proces nemůže importovat vazbu pro zadaný kontrakt. Požadavky na ochranu pro vazbu nejsou kompatibilní s vazbu pro daný kontrakt již byla naimportována. Je nutné překonfigurovat vazby.|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|Import zásady zabezpečení se nezdařilo. Zásady zabezpečení obsahuje podporu tokenu požadavky v oblasti operace. Popis smlouvy neurčuje akci pro zprávu požadavku, které jsou přidružené k této operace.|  
|CannotIssueRstTokenType|Typ tokenu určenou, nebo nelze vydat.|  
|CannotObtainIssuedTokenKeySize|Nelze určit velikost klíče vydaného tokenu.|  
|CannotPerformImpersonationOnUsernameToken|Pomocí klienta tokenu zosobnění není možné. Zadaná vazba pro zadaný kontrakt používá Token zabezpečení uživatelské jméno pro ověřování klientů s registrované zprostředkovatele členství. Použijte jiný druh tokenu zabezpečení pro klienta.|  
|CannotPerformS4UImpersonationOnPlatform|Zadaná vazba pro zadaný kontrakt podporuje zosobnění pouze na [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] a novější verze systému Windows. Použít SspiNegotiated ověřování a vazba s zabezpečené konverzace s zrušení povolena.|  
|CannotReadKeyIdentifier|Nelze přečíst KeyIdentifier ze zadaného prvku s zadaného oboru názvů.|  
|CannotReadToken|Nelze přečíst token ze zadaného prvku s zadaný obor názvů pro BinarySecretSecurityToken s zadaný typ hodnoty. Pokud tento element musí být platné, zkontrolujte, že zabezpečení nakonfigurovaná využívat tokeny s názvem, zadat obor názvů a hodnota typu.|  
|CertificateUnsupportedForHttpTransportCredentialOnly|V režimu zabezpečení TransportCredentialOnly nepodporuje ověřování na základě certifikátu klienta. Vyberte režim zabezpečení přenosu.|  
|ClaimTypeCannotBeEmpty|Typ claimType nemůže být prázdný řetězec.|  
|ClientCertificateNotProvided|Nebyl zadán certifikát pro klienta. Certifikát můžete nastavit na ClientCredentials nebo ServiceCredentials.|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|Třída ClientCredentialType.None není platný pro režim zabezpečení TransportWithMessageCredential. Zadejte typ přihlašovacích údajů nebo použijte jiný režim zabezpečení.|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Konfigurační schéma je nedostatečná pro popisují nestandardní konfiguraci následující element vazby zabezpečení:|  
|DerivedKeyTokenGenerationAndLengthTooHigh|Odvozené key zadaný generování a délka výsledek v klauzuli offset odvození klíče, která je větší než maximální povolená posun.|  
|DnsIdentityCheckFailedForIncomingMessage|Kontrola identity se nezdařilo pro příchozí zprávy. Byl zadán název očekávané domény system (DNS) identitu vzdálený koncový bod. Vzdálený koncový bod k dispozici (DNS) zadaný domain name system deklarací identity. Pokud je oprávněné vzdálený koncový bod, můžete opravit problém zadáním identita systémové název domény jako vlastnost identity EndpointAddress při vytváření proxy kanálu.|  
|DnsIdentityCheckFailedForOutgoingMessage|Kontrola identity se nezdařilo pro zprávu, která byla ven. Vzdálený koncový bod měly mít identita systémové název zadané doméně. Vzdálený koncový bod k dispozici deklarace systému názvů domény (DNS). Pokud je oprávněné vzdálený koncový bod, můžete při vytváření proxy kanál explicitním zadáním DNS identity jako vlastnost Identity EndpointAddress potíže vyřešit.|  
|DuplicateIdInMessageToBeVerified|Zadané id dvakrát ve zprávě, která se dodává pro ověření došlo k chybě.|  
|EmptyBase64Attribute|Pro požadovaný atribut base-64 názvem a oborem názvů nebyl nalezen prázdnou hodnotu.|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Export zásad zabezpečení se nezdařilo. Vazba obsahuje AsymmetricSecurityBindingElement i element vazby zabezpečeného přenosu. Export zásad pro takovou vazbu není podporován.|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Export zásad zabezpečení se nezdařilo. Vazba obsahuje třídu SymmetricSecurityBindingElement i element vazby zabezpečeného přenosu. Export zásad pro takovou vazbu není podporován.|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Export zásad zabezpečení se nezdařilo. Vazba obsahuje TransportSecurityBindingElement, ale žádný element vazby přenos, který implementuje ITransportTokenAssertionProvider. Export zásad pro takovou vazbu není podporován. Ujistěte se, že element vazby přenosu vazba implementuje rozhraní ITransportTokenAssertionProvider.|  
|FoundMultipleCerts|Nalezeno více certifikátů X.509 pomocí zadaná kritéria vyhledávání: StoreName, StoreLocation, FindType, FindValue. Zadejte hodnotu konkrétnější najít.|  
|FoundMultipleCertsForTarget|Nalezeno více certifikátů X.509 pomocí zadaná kritéria vyhledávání: StoreName, StoreLocation, FindType, FindValue pro zadaný cíl. Zadejte hodnotu konkrétnější najít.|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|Třída SecurityVersion.WSSecurityJan2004 nepodporuje dešifrování záhlaví. Použít SecurityVersion.WsSecurityXXX2005 a vyšší nebo šifrování celé zprávy pomocí zabezpečení přenosu.|  
|IdentityCheckFailedForIncomingMessage|Kontrola identity se nezdařilo pro příchozí zprávy. Očekávaná identita je určené pro cíl koncový bod.|  
|IdentityCheckFailedForOutgoingMessage|Kontrola identity odchozí zprávy se nezdařila. Očekávaná identita je určené pro cíl koncový bod.|  
|IncorrectSpnOrUpnSpecified|Ověřování zabezpečení rozhraní SSPI (Support Provider Interface) se nezdařilo. Server není spuštěn v účtu, který má zadanou identitou. Pokud je server spuštěn v účtu služby (například síťové služby), zadejte účtu ServicePrincipalName jako identitu ve EndpointAddress pro server. Pokud server běží v uživatelském účtu, zadejte účtu UserPrincipalName jako identitu ve EndpointAddress pro server.|  
|InvalidAttributeInSignedHeader|Zadaná hlavička podepsaný držitelem obsahuje zadaného atributu. Je zadán atribut očekávané.|  
|InvalidCloseResponseAction|Spolu s určenou akcí neplatný byla přijata odpověď zavřít relace zabezpečení.|  
|InvalidQName|Třída QName je neplatný.|  
|InvalidRenewResponseAction|Obnovení relace zabezpečení odpověď byla přijata spolu s určenou akcí neplatný.|  
|InvalidSspiNegotiation|Vyjednávání Security Support Provider Interface se nezdařilo.|  
|IssuerBindingNotPresentInTokenRequirement|Správce tokenů zabezpečení vyžaduje zadání požadavek na token, který popisuje zabezpečené konverzaci prvku vazby bootstrap zabezpečení. Požadavek tokenu je zadán následujícím způsobem.|  
|KeyLengthMustBeMultipleOfEight|Zadaná délka klíče není násobkem 8 pro symetrické klíče.|  
|LsaAuthorityNotContacted|Vnitřní chyba SSL (viz. Win32 stavový kód podrobnosti). Zkontrolujte certifikát serveru, který chcete zjistit, jestli je umožňuje výměnu klíčů.|  
|MaximumPolicyRedirectionsExceeded|Byl dosažen limit načtení rekurzivní zásady. Zkontrolujte, zda existuje smyčka v řetězu služby federation service.|  
|MessagePartSpecificationMustBeImmutable|Specifikace části zprávy musí být provedeny konstantní před nastavením.|  
|MissingCustomCertificateValidator|X509CertificateValidationMode.Custom vyžaduje CustomCertificateValidator. Určete vlastnost CustomCertificateValidator.|  
|MissingCustomUserNamePasswordValidator|Třída UserNamePasswordValidationMode.Custom vyžaduje CustomUserNamePasswordValidator. Určete vlastnost CustomUserNamePasswordValidator.|  
|MissingMembershipProvider|Třída UserNamePasswordValidationMode.MembershipProvider vyžaduje MembershipProvider. Určete vlastnost MembershipProvider.|  
|NoBinaryNegoToSend|Žádné binární vyjednávání byla odeslána na druhé straně.|  
|NoEncryptionPartsSpecified|Pro zprávy spolu s určenou akcí nebyly zadány žádné části zprávy šifrování.|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|Hodnota KeyInfo nebyla nalezena v položce šifrované najít dešifrování tokenů.|  
|NonceLengthTooShort|Zadanou hodnotu nonce je příliš krátký. Minimální požadovaná délka je 4 bajtů.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Žádná odchozí třída EndpointAddress je k dispozici pro kontrolu identity na zprávu k odeslání.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Žádná odchozí třída EndpointAddress je k dispozici pro kontrolu identity v přijaté odpovědi.|  
|NoPartsOfMessageMatchedPartsToSign|Nebyl vytvořen žádný podpis, protože žádná z částí zpráva odpovídá zadané specifikaci části zprávy.|  
|NoPrincipalSpecifiedInAuthorizationContext|Žádný vlastní objekt zabezpečení je zadaný v autorizační kontext.|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Není dostupný v záhlaví zabezpečení poskytoval hodnotu nonce pro rozpoznání opětovného přehrání podpis.|  
|NoSignaturePartsSpecified|Pro zprávy spolu s určenou akcí nebyly zadány žádné části podpis zprávy.|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Žádné podpisový token je k dispozici pro Neověřovat příchozí identity.|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Časové razítko je k dispozici v hlavičce zabezpečení zjišťování opětovného přehrání.|  
|NoTransportTokenAssertionProvided|Poradce zásad zabezpečení se nezdařilo. Zadaný výraz tokenu přenosu zadaného typu nevytvořil výraz tokenu přenosu zahrnout výraz zásad zabezpečení sp:TransportBinding.|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Symetrický protokol zabezpečení můžete nakonfigurovat buď symetrický zprostředkovatele tokenu a symetrický ověřovací data tokenu nebo asymetrický zprostředkovatele tokenu. Nedá se nakonfigurovat pomocí obou.|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Tuto operaci nelze provést, v záhlaví zabezpečení příjemce.|  
|OperationDoesNotAllowImpersonation|Zadaná služba operaci, která patří k smlouvě se zadaným názvem a obor názvů není povoleno zosobnění.|  
|PolicyRequiresConfidentialityWithoutIntegrity|Zásady zabezpečení zpráv pro zadanou akci vyžaduje důvěrnost bez integrity. Důvěrnost bez integrity není podporována.|  
|PrimarySignatureIsRequiredToBeEncrypted|Primární podpis musí být šifrovaný.|  
|PropertySettingErrorOnProtocolFactory|Požadovaná vlastnost v objektu pro vytváření protokol zadaný zabezpečení není nastaven, nebo má neplatnou hodnotu.|  
|ProtocolFactoryCouldNotCreateProtocol|Objekt factory protokolu nelze vytvořit protokol.|  
|PublicKeyNotRSA|Veřejný klíč není klíč RSA.|  
|RequiredMessagePartNotEncrypted|Část zadaný požadované zprávy nebyla šifrována.|  
|RequiredMessagePartNotEncryptedNs|Část zadaný požadované zprávy nebyla šifrována.|  
|RequiredMessagePartNotSigned|Část zadaný požadované zprávy nebyl podepsán.|  
|RequiredMessagePartNotSignedNs|Část zadaný požadované zprávy nebyl podepsán.|  
|RequiredSecurityHeaderElementNotSigned|Element header zadaný zabezpečení se zadaným id musí být podepsané.|  
|RequiredSecurityTokenNotEncrypted|Zadaný, musí být šifrovaný token zabezpečení s režimem zadaný přílohy.|  
|RequiredSecurityTokenNotSigned|Token zadaný zabezpečení s režimem zadaný přílohy musí být podepsané.|  
|RequiredSignatureMissing|Podpis musí být v záhlaví zabezpečení.|  
|RequireNonCookieMode|Zadaná vazba s zadaného oboru názvů je nakonfigurována pro vydávání tokenů kontextu zabezpečení souboru cookie. Integrace COM + services nepodporuje tokenů kontextu zabezpečení souboru cookie.|  
|RevertingPrivilegeFailed|Operace obnovení se nezdařilo se zadanou výjimkou.|  
|RSTRAuthenticatorIncorrect|RequestSecurityTokenResponse CombinedHash je nesprávný.|  
|SecureConversationCancelNotAllowedFaultReason|Zrušení zabezpečené konverzace není vazba povolena.|  
|SecureConversationDriverVersionDoesNotSupportSession|Konfigurovaná verze SecureConversation nepodporuje relace. Použijte třídu WSSecureConversationFeb2005 nebo vyšší.|  
|SecureConversationRequiredByReliableSession|Spolehlivá relace bez zabezpečené konverzaci nelze vytvořit. Povolte zabezpečené konverzaci.|  
|SecurityAuditFailToLoadDll|Zadaný dynamická knihovna (dll) se nepodařilo načíst.|  
|SecurityAuditNotSupportedOnChannelFactory|Třída SecurityAuditBehavior nepodporuje vytváření kanálů.|  
|SecurityAuditPlatformNotSupported|Aktuální platforma nepodporuje zápis zprávy o auditu do protokolu zabezpečení. Musíte zapsat auditní zprávy do protokolu aplikace.|  
|SecurityBindingElementCannotBeExpressedInConfig|Zásady zabezpečení byla importována pro koncový bod. Zásady zabezpečení obsahuje požadavky, které nelze vyjádřit v konfiguraci Windows Communication Foundation. Vyhledejte komentář elementu SecurityBindingElement parametry, které jsou potřeba v konfiguračním souboru, který byl vygenerován. Vytvořte element správné vazby s kódem. Konfigurace vazeb, který je v konfiguračním souboru není zabezpečený.|  
|SecurityBindingSupportsOneWayOnly|SecurityBinding pro zadaná vazba pro zadaný kontrakt podporuje pouze operaci OneWay.|  
|SecurityContextDoesNotAllowImpersonation|Zosobnění nelze spustit, protože není namapovaná hodnotu SecurityContext pro roli UltimateReceiver ze zprávy požadavku spolu s určenou akcí identitu systému Windows.|  
|SecurityListenerClosing|Naslouchací proces nepřijímá nové zabezpečené konverzace, protože je ukončován.|  
|SecurityListenerClosingFaultReason|Server nepřijímá nové zabezpečené konverzace aktuálně vzhledem k tomu, že je ukončován. Zkuste to prosím znovu později.|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|Před provedením této operace musí být nastavena výroba protokolu zabezpečení.|  
|SecuritySessionAbortedFaultReason|Zabezpečení relace byla ukončena. To může být způsobeno nebyly přijaty žádné zprávy v relaci příliš dlouho.|  
|SecuritySessionKeyIsStale|Klíč relace musí být obnoveno, než ho můžete zabezpečit zprávy aplikace.|  
|SecuritySessionLimitReached|Nelze vytvořit relaci zabezpečení. Zkuste to znovu později.|  
|SecuritySessionNotPending|Žádná relace zabezpečení se zadaným id čeká na vyřízení.|  
|SecurityTokenParametersHasIncompatibleInclusionMode|Zadaná vazba nastaven parametr tokenu zabezpečení, který má režim tokenu zahrnutí zadaný nekompatibilní zabezpečení. Zadejte režim tokenu zahrnutí alternativní zabezpečení.|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|Zadaná vazba pro zadaný kontrakt nakonfigurovaný verzí nekompatibilní zabezpečení, která nepodporuje odpojit odkazy na klíčů EncryptedKeys. Použít zadaná hodnota nebo vyšší, jako je verze zabezpečení pro vazbu.|  
|SecurityVersionDoesNotSupportSignatureConfirmation|Zadaná třída SecurityVersion nepodporuje potvrzení podpisu. Použijte pozdější třídu SecurityVersion.|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|Zadaná vazba pro zadaný kontrakt je nakonfigurovaný s verzí zabezpečení, která nepodporuje externí odkazy na X.509 tokeny pomocí hodnoty kryptografického otisku certifikátu. Použít zadaná hodnota nebo vyšší, jako je verze zabezpečení pro vazbu.|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Je třeba zadat parametry tokenu zabezpečení s podpůrnými tokeny pro každou zprávu.|  
|ServerCertificateNotProvided|Příjemce neposkytl svůj certifikát. Tento certifikát je vyžadován protokol TLS. Obě strany musí mít přístup k jejich certifikáty.|  
|SignatureConfirmationNotSupported|Nakonfigurovaná verze SecurityVersion nepodporuje potvrzení podpisu. Použít WSSecurityXXX2005 nebo vyšší.|  
|SignatureConfirmationRequiresRequestReply|Objekt factory protokol musí podporovat zabezpečení požadavek nebo odpověď v rámci potvrzení podpisu.|  
|SignatureNotExpected|Podpis není očekáván pro tuto zprávu.|  
|SigningTokenHasNoKeys|Zadaný token podpisový nemá žádné klíče. Token zabezpečení se používá v kontextu, který vyžaduje, aby se používají ke kryptografickým operacím, ale token neobsahuje žádné kryptografické klíče. Buď typ tokenu nepodporuje kryptografické operace, nebo konkrétní instance tokenu neobsahuje kryptografické klíče. Zkontrolujte konfiguraci k zajištění, které typy tokenů (například UserNameSecurityToken) nejsou zadané v kontextu, který vyžaduje kryptografické operace (například token podporující potvrzení).|  
|SpnegoImpersonationLevelCannotBeSetToNone|Rozhraní poskytovatele podpory zabezpečení nepodporuje zosobnění úrovně 'None'. Zadejte úroveň a zosobnění nebo delegování.|  
|SslClientCertMustHavePrivateKey|Zadaný certifikát musí mít privátní klíč. Proces musíte mít přístupová práva pro privátní klíč.|  
|SslServerCertMustDoKeyExchange|Zadaný certifikát musí mít privátní klíč, který je schopen výměny klíče. Proces musíte mít přístupová práva pro privátní klíč.|  
|StandardsManagerCannotWriteObject|Zadaný objekt nelze serializovat serializátoru tokenů.  Pokud se jedná vlastní typ je třeba zadat vlastní serializátor.|  
|TimeStampHasCreationAheadOfExpiry|Časové razítko zabezpečení je neplatný, protože doba jejího vytvoření je větší než nebo rovna hodnotě jeho čas vypršení platnosti.|  
|TimeStampHasCreationTimeInFuture|Časové razítko zabezpečení je neplatný, protože doba jejího vytvoření je v budoucnu. Aktuální čas je zadána a je zadána zkosení povolené hodiny.|  
|TimeStampHasExpiryTimeInPast|Časové razítko zabezpečení je zastaralý, protože jeho čas vypršení platnosti je v minulosti. Aktuální čas je zadána a je zadána zkosení povolené hodiny.|  
|TimeStampWasCreatedTooLongAgo|Časové razítko zabezpečení je zastaralý, protože doba jejího vytvoření je příliš daleko zpět v minulosti. Aktuální čas, časové razítko maximální doba života a zkosení povolené hodiny nejsou zadány.|  
|TokenProviderCannotGetTokensForTarget|Zprostředkovatel tokenu nelze získat tokeny pro zadaný cíl.|  
|TooManyIssuedSecurityTokenParameters|Větev spojeného řetězce zabezpečení obsahuje více IssuedSecurityTokenParameters. Systém InfoCard podporuje pouze jeden IssuedSecurityTokenParameters pro každou větev.|  
|TransportDoesNotProtectMessage|Zadaná vazba pro zadaný kontrakt nastaven režim ověřování, která vyžaduje transportní úrovni integrity a důvěrnosti. Přenos nemůžete ale zadat integrity a důvěrnosti.|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 nepodporuje vydávající certifikáty X.509 nebo klíčů EncryptedKeys. Použijte WsTrustFeb2005 nebo vyšší.|  
|TrustDriverVersionDoesNotSupportSession|Nakonfigurované verze důvěryhodnosti nepodporuje relace. Použijte WSTrustFeb2005 nebo vyšší.|  
|UnableToCreateICryptoFromTokenForSignatureVerification|Nelze vytvořit rozhraní ICrypto z zadaný token pro ověření podpisu.|  
|UnableToCreateSymmetricAlgorithmFromToken|Nelze vytvořit algoritmus symetrického zadaný z tokenu.|  
|UnableToDeriveKeyFromKeyInfoClause|Zadané Klauzule KeyInfo byl přeložen na zadaný token, který neobsahuje symetrického klíče, který lze použít pro odvození.|  
|UnableToFindTokenAuthenticator|Nelze nalézt ověřovací data tokenu pro zadaný typ tokenu. Tokeny tohoto typu nemůže být přijat podle aktuální nastavení zabezpečení.|  
|UnableToLoadCertificateIdentity|Nelze načíst identitu certifikátu X.509, který je zadaný v konfiguraci.|  
|UnexpectedEmptyElementExpectingClaim|Zadaný element ze zadaného oboru názvů je prázdná a neurčuje platnou deklaraci identity.|  
|UnknownEncodingInBinarySecurityToken|Nerozpoznané kódování došlo k chybě při čtení binárního tokenu zabezpečení.|  
|UnsecuredMessageFaultReceived|Zabezpečená nebo chybně zabezpečená chyba byla přijata z druhé strany. Najdete ve vnitřní výjimce FaultException kód chyby a podrobnosti.|  
|UnsupportedPasswordType|Zadané uživatelské jméno token má nepodporovaný typ hesla.|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|Nelze importovat zásady zabezpečení. Požadavky na ochranu pro zaváděcí vazbu zabezpečené konverzace nejsou podporovány. Požadavky na ochranu pro zavádění zabezpečené konverzace musí vyžadovat požadavek a odpověď na podepsat a zašifrovat.|  
|UnsupportedSecurityPolicyAssertion|Při importu zásady zadaný zabezpečení byla zjištěna nepodporovaný výraz zásad zabezpečení.|
