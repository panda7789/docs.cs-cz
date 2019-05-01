---
title: Výjimky IdentityModel
ms.date: 03/30/2017
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
ms.openlocfilehash: ee0b5537a415e1ea53c653ae8e8485e94cc713fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998514"
---
# <a name="identitymodel-exceptions"></a>Výjimky IdentityModel
Toto téma obsahuje seznam generovaných IdentityModel všechny výjimky.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Aktuální řetězce|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|Hodnota tohoto argumentu musí být jeden z těchto dvou typů.|  
|SAMLSubjectNameIdentifierRequiresNameValue|Název zadaný pro třídu SamlNameIdentifier nemůže být null nebo délka je 0.|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|Poskytovatel IssuanceTokenProvider dokončil vyjednávání zabezpečení.|  
|TraceCodeSecurityNewServerSessionKeyIssued|Vytvoření nové relace zabezpečení serveru byl vydán klíč.|  
|SAMLAttributeMissingNameAttributeOnRead|"Název" pro SamlAttribute čtená chybí nebo její délka je 0.|  
|UnknownICryptoType|Implementace ICrypto není podporována.|  
|TraceCodeSecurityTokenProviderClosed|Poskytovatel tokenu zabezpečení byla zavřena.|  
|SAMLUnableToLoadAdvice|Nepovedlo se načíst \<SAML: Advice > element.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|Atribut "AuthenticationMethod" pro třídu SamlAuthenticationStatement chybí nebo má délku 0.|  
|UnsupportedTransformAlgorithm|Nepodporovaný algoritmus transformace nebo převodu do kanonického tvaru.|  
|SAMLAudienceRestrictionShouldHaveOneAudience|Třída SamlAudienceRestrictionCondition musí obsahovat alespoň jeden (identifikátor URI cílové skupiny).|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence musí odkazovat na alespoň jeden výraz SamlAssertion buď podle Id nebo odkaz.|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|Třída SamlAudienceRestrictionCondition čtená chybí hodnota v elementu "Cílová skupina".|  
|X509ChainBuildFail|Nepovedlo se konkrétní vytvoření řetězce certifikátu X.509. Použitý certifikát má řetězec záruky, který nemůže být ověřen. Nahraďte certifikát nebo změňte certificateValidationMode.|  
|XDCannotFindValueInDictionaryString|Konkrétní hodnota id nebyla nalezena v řetězci slovníku.|  
|TraceCodeImportSecurityChannelBindingEntry|Spuštění vazby zabezpečení ImportChannelBinding.|  
|PrivateKeyExchangeNotSupported|Privátní klíč nepodporuje exchange specifikace klíče.|  
|TokenProviderUnableToGetToken|Konkrétní poskytovatele tokenu, kterého nemohl poskytnout token zabezpečení.|  
|SAMLEntityCannotBeNullOrEmpty|Konkrétní Entita SamlAssertion nemůže být null ani prázdný.|  
|SAMLAssertionRequireOneStatement|SamlAssertion vyžaduje alespoň jeden příkaz. Ujistěte se, že jste přidali alespoň jeden příkaz SamlStatement do výrazu SamlAssertion, kterou vytváříte.|  
|AESInvalidInputBlockSize|Velikost vstupu musí být násobkem konkrétní bajtů.|  
|AESCryptAcquireContextFailed|Nepovedlo se získat kontext CSP.|  
|SAMLAssertionRequireOneStatementOnRead|Čtený výraz SamlAssertion neobsahuje žádné příkaz SamlStatement. SamlAssertion musí obsahovat alespoň jeden příkaz SamlStatement.|  
|TraceCodeSecuritySessionClosedFaultReceived|Relace zabezpečení klienta přijala relace byla ukončena selhání ze serveru.|  
|TraceCodeIssuanceTokenProviderRedirectApplied|Poskytovatel IssuanceTokenProvider použil záhlaví přesměrování.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|Při odesílání relace zabezpečení zavření selhání klientovi došlo k chybě.|  
|ValueMustBeZero|Hodnota tohoto argumentu musí být 0.|  
|SAMLUnableToResolveSignatureKey|Nelze přeložit identifikátor SecurityKeyIdentifier nalezený v podpisu SamlAssertion. Pro konkrétní vydavatele nelze ověřit podpis SamlAssertion.|  
|X509IsNotInTrustedStore|Konkrétní certifikát X.509 není v úložišti důvěryhodných osob.|  
|SAMLElementNotRecognized|Konkrétní element není podporován.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|"Prostředek" atribut pro třídu SamlAuthorizationDecisionStatement chybí nebo délka je 0.|  
|SamlTokenMissingSignature|Výraz SamlAssertion není podepsán. Výrazy SamlAssertion lze podepsat nastavením SigningCredentials.|  
|ExpectedElementMissing|Je očekáván element s konkrétní obor názvů chybí.|  
|NoKeyIdentifierClauseFound|V identifikátoru SecurityKeyIdentifier nebyla nalezena žádná klauzule určitého typu.|  
|MissingPrivateKey|Privátní klíč není k dispozici v certifikátu X.509.|  
|UnexpectedEOFFromReader|Neočekávaný znak konce souboru z čtecí funkce XML.|  
|UnsupportedKeyDerivationAlgorithm|Algoritmus odvození konkrétní klíče není podporován.|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|Konkrétní tokenu nepodporuje vytváření klauzule identifikátoru klíče.|  
|LastMessageNumberExceeded|Byla zjištěna narušení protokolu pořadových čísel.|  
|SymmetricKeyLengthTooShort|Délka zadaný symetrický klíč je příliš krátký.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|SamlAuthorityBinding probíhá čtení nalezena tak, aby obsahovala "AuthorityKind", který nebyl nalezen nebo délka je 0.  Toto není povoleno.|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer je prázdný.|  
|InvalidXmlQualifiedName|Byl očekáván plný název Xml, ale byl nalezen neplatný název.|  
|SAMLAuthorityKindMissingName|Třída XmlQualifiedName, která představuje "AuthorityKind" ve třídě SamlAuthorityBinding nemůže být null ani délka je 0.|  
|AESCryptEncryptFailed|Nepodařilo se zašifrovat konkrétní data.|  
|AuthorizationContextCreated|Autorizační kontext s konkrétním id se vytvoří.|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|SamlSerializer neobsahuje schopný načíst SecurityKeyIdentifier SecurityTokenSerializer. Používáte-li vlastní SecurityKeyIdentifier, je nutné poskytnout vlastní SecurityTokenSerializer.|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|Poskytovatel IssuanceTokenProvider snížit mezipaměť tokenu služby.|  
|TraceCodeSecurityTokenProviderOpened|Poskytovatel tokenu zabezpečení byla otevřena.|  
|PublicKeyNotRSA|Veřejný klíč není klíčem RSA.|  
|InvalidReaderState|Konkrétní stav není platný pro zadaný vstupní čtecí zařízení.|  
|UnableToResolveReferenceUriForSignature|Nepovedlo se přeložit konkrétní identifikátor URI v podpisu k vypočtení otisku.|  
|EmptyBase64Attribute|Pro požadovaný název atributu base64 a obor názvů byla nalezena prázdná hodnota.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|SAML SubjectConfirmation vyžaduje metoda potvrzení, pokud je zadána Data potvrzení nebo KeyInfo.|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|Třída SamlAudienceRestrictionCondition čtená musí obsahovat alespoň jeden "cílovou skupinu" hodnotu. Nebyl nalezen žádný.|  
|TokenProviderUnableToRenewToken|Konkrétní poskytovatele tokenu, kterého nemohl obnovit token zabezpečení.|  
|AESIVLengthNotSupported|Vektor IV konkrétní bits se nepodporuje. Je podporován pouze IV 128 bitů.|  
|SAMLAuthorityBindingMissingAuthorityKind|Třída SamlAuthorityBinding musí obsahovat "AuthorityKind", který nemá hodnotu null.|  
|TraceCodeSecuritySessionDemuxFailure|Příchozí zpráva není částí stávající relace zabezpečení.|  
|TokenRenewalNotSupported|Konkrétní poskytovatele tokenu, kterého nepodporuje obnovení tokenu.|  
|AtLeastOneReferenceRequired|V podpisu je vyžadován alespoň jeden odkaz.|  
|SAMLSignatureAlreadyRead|Podpis je již načten v kontrolního výrazu SAML.|  
|AlgorithmAndPrivateKeyMisMatch|Zadaný algoritmus a privátního klíče si neodpovídají.|  
|EmptyTransformChainNotSupported|Prázdný řetězec transformace není podporován.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper::EncryptDecryptHelper&#124;"posun" je mimo rozsah.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper::EncryptDecryptHelper&#124;"velikost" je mimo rozsah. SecurityTokenManagerCannotCreateAuthenticatorForRequirement = zabezpečení Správce tokenů nemůže vytvořit ověřovací data tokenu pro konkrétní požadavek.|  
|UnableToCreateKeyedHashAlgorithm|Nelze vytvořit KeyedHashAlgorithm z konkrétní hodnoty pro konkrétní podpisový algoritmus.|  
|SAMLUnableToLoadAssertion|\<Assertion > element nebylo možné načíst.|  
|X509FindValueMismatchMulti|Konkrétní X509FindType vyžaduje typ argumentu findValue zařadil mezí 2 hodnoty. Argument findValue je jiného typu.|  
|TraceCodeSecurityIdentityDeterminationSuccess|Byla určena identita pro parametry EndpointAddress.|  
|UndefinedUseOfPrefixAtElement|Specifický prefix, který se používá v elementu nemá žádný obor názvů definován.|  
|TraceCodeSecuritySessionResponderOperationFailure|Na serveru se nezdařila operace relace zabezpečení.|  
|CannotFindCert|Nepovedlo se najít certifikát X.509 pomocí kritérií hledání: StoreName, StoreLocation FindType, FindValue.|  
|X509InvalidUsageTime|Určený čas použití certifikátu X.509 je neplatná. Čas využití nespadá mezi požadované časy NotBefore a notafter.|  
|TraceCodeSecurityIdentityDeterminationFailure|Nelze určit identitu pro parametry EndpointAddress.|  
|AsyncObjectAlreadyEnded|U tohoto objektu asynchronní výsledek již byla volána metoda End.|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|Externí slovník obsahuje definice pro všechny požadované řetězce. Konkrétní řetězec není k dispozici ve vzdálené slovníku.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|Relace zabezpečení klienta přijala ze serveru chybu obnovení klíče.|  
|SAMLActionNameRequired|Řetězec, který představuje SamlAction nemůže být null nebo délka je 0.|  
|SignatureVerificationFailed|Ověření podpisu se nezdařilo.|  
|TraceCodeSecurityContextTokenCacheFull|Vyrovnávací paměť SecurityContextSecurityToken je plná.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|Hodnota MajorVersion pro čtený výraz SamlAssertion chybí nebo její délka je 0.|  
|SamlAttributeClaimRightShouldBePossessProperty|Tento konstruktor SamlAttribute vyžaduje, že vpravo od deklarace identity mají hodnotu System.IdentityModel.Claims.Rights.PossessProperty.|  
|AuthorizationPolicyEvaluated|S konkrétním id není vyhodnocováno.|  
|SAMLUnableToLoadCondtions|\<Conditions > element nebylo možné načíst.|  
|AESKeyLengthNotSupported|Klíč konkrétní bits se nepodporuje. Pouze 128, 192 a 256 bitů klíče jsou podporovány.|  
|UserNameCannotBeEmpty|Uživatelské jméno nemůže být prázdný.|  
|AlgorithmAndPublicKeyMisMatch|Zadaný algoritmus a veřejný klíč se neshodují.|  
|SAMLUnableToLoadCondtion|\<Conditions > element nebylo možné načíst.|  
|SamlAssertionMissingSigningCredentials|Ve výrazu SamlAssertion nebyly nastaveny přihlašovací údaje SigningCredentials. Výrazy SamlAssertion musí být podepsané, nastavte prosím platné přihlašovací údaje SigningCredentials ve výrazu SamlAssertion, aby bylo možné pokračovat.|  
|SspiPayloadNotEncrypted|Binární data nebyla zašifrována s kontextem zabezpečení SSPI.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|Třída SamlAuthorizationDecisionStatement, který je čten neobsahuje žádnou SamlAction.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|Protokol zabezpečení nemůže zabezpečit odchozí zprávu.|  
|UndefinedUseOfPrefixAtAttribute|Konkrétní předpony použitý na konkrétní atribut nemá žádný obor názvů definován.|  
|NoInputIsSetForCanonicalization|Žádný vstup nastavený pro zápis kanonizovaného výstupu.|  
|TraceCodeSecurityPendingServerSessionAdded|Čekající relaci zabezpečení je přidána na server.|  
|AsyncCallbackException|Třída AsyncCallback vyvolala výjimku.|  
|PrivateKeyNotRSA|Privátní klíč není klíčem RSA.|  
|TraceCodeSecurityClientSessionKeyRenewed|Relace zabezpečení klienta obnovila klíč relace.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|Rozhodnutí pro třídu SamlAuthorizationDecisionStatement chybí nebo délka je 0.|  
|SAMLAttributeNameAttributeRequired|Název zadaný pro třídu SamlAttribute nemůže být null nebo délka je 0.|  
|SamlSerializerRequiresExternalSerializers|SamlSerializer potřebuje SecurityTokenSerializer serializovat SecurityKeyIdentifier v tokenu.|  
|UnableToResolveKeyReference|Překladač tokenů nejde přeložit odkaz na klíč zabezpečení.|  
|UnsupportedKeyWrapAlgorithm|Algoritmus konkrétní zabalení klíče není podporován.|  
|SAMLAssertionMissingIssuerAttributeOnRead|"Vystavitele" pro čtený výraz SamlAssertion chybí nebo její délka je 0.|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|Poskytovatel IssuanceTokenProvider použil token služby uložený v mezipaměti.|  
|AESCryptGetKeyParamFailed|Nepovedlo se získat konkrétní parametr klíče.|  
|InvalidNamespaceForEmptyPrefix|Obor názvů je neplatný pro prázdnou předponu.|  
|AESCipherModeNotSupported|Režim konkrétní šifrování se nepodporuje. Je podporován pouze CBC.|  
|ArgumentCannotBeEmptyString|Argument musí být neprázdný řetězec.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|MinorVersion pro čtený výraz SamlAssertion chybí nebo její délka je 0.|  
|SpecifiedStringNotAvailableInDictionary|Zadaný řetězec není položka v aktuálním slovníku.|  
|KerberosApReqInvalidOrOutOfMemory|Asie a Tichomoří-REQ je neplatný nebo systém nemá dostatek paměti.|  
|FailLogonUser|Chyba LogonUser pro zadaného uživatele. Ujistěte se, že uživatel má platný účet Windows.|  
|ValueMustBeNonNegative|Hodnota tohoto argumentu musí být nezáporná.|  
|X509ValidationFail|Ověřování zadaného certifikátu X.509 se nezdařilo.|  
|TraceCodeSecuritySessionRequestorOperationSuccess|Operace relace zabezpečení klienta úspěšně dokončena.|  
|SAMLActionNameRequiredOnRead|Řetězec, který je pro čtení pro SamlAction chybí nebo její délka je 0.|  
|KerberosMultilegsNotSupported|Identita je určena jako hlavní název uživatele. Ověřování služby spuštěné pod účtem uživatele vyžaduje více ramena protokolu Kerberos, která se nepodporuje.|  
|SAMLAssertionIdRequired|"AssertionId" pro SamlAssertion nemůže být null ani prázdný.|  
|InvalidOperationForWriterState|Zadaná operace není platná v zadaném stavu XmlWriter.|  
|CannotValidateSecurityTokenType|Ověřovací data tokenu zabezpečení nelze ověřit token zadaného typu.|  
|X509FindValueMismatch|Zadaný X509FindType vyžaduje typ argumentu findValue zadanou hodnotou. Argument findValue je jiného typu.|  
|TraceCodeSecurityClientSessionCloseSent|Relace zabezpečení klienta odeslala zprávu zavřít.|  
|SuiteDoesNotAcceptAlgorithm|Zadaný algoritmus pro zadanou operaci neakceptuje zadaný algoritmus suite|  
|TraceCodeSecuritySessionRequestorOperationFailure|Operace relace zabezpečení klienta se nezdařila.|  
|SAMLUnableToLoadStatement|Nepovedlo se načíst SamlStatement.|  
|InnerReaderMustBeAtElement|V elementu musí být vnitřní čtecí zařízení.|  
|UnableToCreateTokenReference|Nelze vytvořit odkaz tokenu zabezpečení.|  
|TraceCodeSecurityBindingIncomingMessageVerified|Protokol zabezpečení úspěšně ověřil příchozí zprávu.|  
|ObjectIsReadOnly|Objekt je jen pro čtení.|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|Relace zabezpečení klienta zrušila předchozí klíč relace.|  
|SAMLTokenTimeInvalid|SamlToken není čas platný. Aktuální čas je mimo dobu platnosti a vypršení platnosti tokenu.|  
|TraceCodeSecurityIdentityVerificationSuccess|Ověření identity bylo úspěšné.|  
|SigningTokenHasNoKeys|Zadaný podpisový token nemá žádné klíče.|  
|TraceCodeSecurityIdentityVerificationFailure|Ověření identity se nezdařilo.|  
|AESCryptImportKeyFailed|Nepovedlo se importovat materiál klíče.|  
|FailInitializeSecurityContext|Funkce InitializeSecurityContent se nezdařila. Ujistěte se, že hlavní název služby je správný.|  
|TraceCodeStreamSecurityUpgradeAccepted|Upgrade zabezpečení proudu byl úspěšně přijat.|  
|SAMLAuthorityBindingRequiresLocation|Atribut "Umístění", který je zadaný na třídě SamlAuthorityBinding nemůže být null nebo délka je 0.|  
|PublicKeyNotDSA|Veřejný klíč není klíče algoritmu DSA.|  
|ImpersonationLevelNotSupported|Režimy ověřování pomocí protokolu Kerberos nepodporují úroveň zosobnění zadané. Zadejte platnou úroveň identifikaci nebo zosobnění.|  
|RequiredTargetNotSigned|Element se zadaným id je potřeba podepsán, ale nebyl.|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|Atribut "AuthenticationInstant" pro třídu SamlAuthenticationStatement chybí nebo má délku 0.|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|SamlEvidence čtená neobsahuje odkaz na nebo vložený výraz SamlAssertion.|  
|LengthOfArrayToConvertMustGreaterThanZero|Délka pole, které chcete převést na celé číslo musí být větší než 0.|  
|InvalidAsyncResult|Neplatný výsledek AsyncResult|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|Poskytovatel IssuanceTokenProvider odebral token služby vypršela platnost.|  
|IncorrectUserNameFormat|Uživatelské jméno je v neplatném formátu. Formát uživatelského jména musí být ve formě "username" nebo "domény\\\username".|  
|TraceCodeExportSecurityChannelBindingEntry|Spuštění vazby zabezpečení ExportChannelBinding.|  
|UnsupportedInputTypeForTransform|Zadaný vstupní typ není podporován pro transformaci.|  
|CannotFindDocumentRoot|Nejde najít kořen dokumentu.|  
|XmlBufferQuotaExceeded|Velikost nutná k uložení obsahu XML překročena kvóta vyrovnávací paměti.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|Při odesílání odpovědi zavřít relace zabezpečení klientovi došlo k chybě.|  
|UnableToResolveReferenceInSamlSignature|Nejde přeložit odkaz na zadané v podpisu SAML s AssertionID.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|SamlSubject vyžaduje, aby byl specifikován "NameIdentifier" nebo "ConfirmationMethod". Obě chyběly.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|"Namespace" pro SamlAttribute čtená chybí nebo délka je 0.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|'ConfirmationMethod' nebyl nalezen ve třídě SamlSubjectConfirmation.|  
|SecurityTokenRequirementHasInvalidTypeForProperty|Požadavek tokenu má neočekávaný typ pro zadanou vlastnost. Očekávaný typ vlastnosti je jiné hodnoty.|  
|TraceCodeNegotiationTokenProviderAttached|Byl připojen poskytovatel NegotiationTokenProvider.|  
|TraceCodeSpnegoClientNegotiationCompleted|Poskytovatel SpnegoTokenProvider dokončil vyjednávání SSPI.|  
|SAMLUnableToLoadUnknownElement|Vybraný serializátor SamlSerializer nelze deserializovat tento element. Zaregistrujte prosím vlastní SamlSerializer li deserializovat vlastní elementy.|  
|CreateSequenceRefused|Funkce RM Destination odmítla požadavek na vytvoření sekvence.|  
|TraceCodeSecuritySessionRedirectApplied|Relace zabezpečení klienta byla přesměrována.|  
|SecurityTokenRequirementDoesNotContainProperty|Požadavek tokenu neobsahuje zadanou vlastnost.|  
|SAMLAttributeValueCannotBeNull|Jedna z hodnot atributů nalezených ve třídě SamlAttribute bylo zjištěno hodnotu null. Ujistěte se, že seznamy nemají hodnotu null, při vytváření třídy SamlAttribute.|  
|ValueMustBeGreaterThanZero|Hodnota tohoto argumentu musí být větší než 0.|  
|TraceCodeNegotiationAuthenticatorAttached|Data NegotiationTokenAuthenticator.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Třída SamlAuthorizationDecisionStatement musí mít aspoň jeden SamlAction.|  
|TraceCodeSecurityTokenAuthenticatorClosed|Ověřovací data tokenu zabezpečení byla zavřena.|  
|TraceCodeSecurityAuditWrittenSuccess|Úspěšně se zapisují do protokolu auditu zabezpečení.|  
|PrivateKeyNotDSA|Privátní klíč není klíče algoritmu DSA.|  
|MessageNumberRollover|Došlo k překročení maximální pořadové číslo pro toto pořadí.|  
|AESPaddingModeNotSupported|Zadaný režim doplnění není podporován. Je podporováno pouze PKCS7 a ISO10126.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|Požadované "NameIdentifier" a 'ConfirmationMethod' elementy nejsou k dispozici pro SamlSubject, který je čten.|  
|TraceCodeSecurityAuditWrittenFailure|Při zápisu do protokolu auditu zabezpečení došlo k chybě.|  
|UnsupportedCryptoAlgorithm|Zadaný kryptografický algoritmus není v tomto kontextu podporován.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|Podpisový token nemá žádný klíč, který podporuje sadu algoritmů zadané.|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|'Identifier' řetězec pro třídu SamlNameIdentifier nebyl nalezen.|  
|SAMLSubjectStatementRequiresSubject|Příkaz subjektu SAML vyžaduje předmět SAML, který chcete zadat.|  
|TraceCodeSslClientCertMissing|Poskytnutí požadovaného certifikátu vzdáleným klientem SSL se nezdařilo.|  
|SAMLTokenVersionNotSupported|Zadaný hlavní verze a podverze nejsou podporovány.|  
|TraceCodeConfigurationIsReadOnly|Konfigurace je jen pro čtení.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|Při odesílání chyby obnovení klíče relace zabezpečení klientovi došlo k chybě.|  
|TraceCodeSecurityInactiveSessionFaulted|Server chybně zpracoval neaktivní relaci zabezpečení.|  
|SAMLUnableToLoadAttribute|Nepovedlo se načíst SamlAttribute.|  
|Psha1KeyLengthInvalid|Zadaná délka klíče PSHA1 je neplatný.|  
|KeyIdentifierCannotCreateKey|Tento identifikátor SecurityKeyIdentifier neobsahuje žádnou klauzuli, která mohla vytvořit klíč.|  
|X509IsInUntrustedStore|Zadaný certifikát X.509 je v úložišti nedůvěryhodný certifikát.|  
|UnexpectedXmlChildNode|Je zadaný podřízený uzel XML typu zadaný pro zadaný element očekáván.|  
|TokenDoesNotMeetKeySizeRequirements|Zadaný token nesplňuje požadavky na velikost klíče pro zadaný algoritmus suite.|  
|TraceCodeSecuritySessionRequestorStartOperation|U klienta byla zahájena operace relace zabezpečení.|  
|InvalidHexString|Neplatný šestnáctkový řetězec formátu.|  
|SamlAttributeClaimResourceShouldBeAString|Tento konstruktor SamlAttribute vyžaduje, aby prostředků deklarace typu "string".|  
|SamlSigningTokenNotFound|Výraz SamlAssertion je podepsán, ale nebyl nalezen token, který je podepsán výraz SamlAssertion. Ujistěte se, že SecurityTokenResolver obsahuje token, který je podepsán výraz SamlAssertion.|  
|TraceCodeSecuritySpnToSidMappingFailure|Název ServicePrincipalName nelze namapovat na identifikátor SecurityIdentifier.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Nelze vytvořit podpis formátování pro zadaný algoritmus ze zadaného asymetrického šifrování.|  
|TraceCodeSecurityServerSessionClosedFaultSent|Relace zabezpečení serveru odeslala selhání relace byla ukončena do klienta.|  
|UnableToFindPrefix|Nepovedlo se najít předponu pro Zadaná předpona viditelně použité v zadaném elementu.|  
|TraceCodeSecurityTokenAuthenticatorOpened|Ověřovací data tokenu zabezpečení byla otevřena.|  
|RequiredAttributeMissing|Zadaný atribut je požadován na zadaném elementu.|  
|LocalIdCannotBeEmpty|Hodnota localId nemůže být prázdný. Zadejte platný "localId".|  
|ValueMustBeInRange|Hodnota tohoto argumentu musí spadat do zadaného rozsahu.|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|Poskytovatel IssuanceTokenProvider spustit nové vyjednávání zabezpečení.|  
|InvalidNtMapping|Zadaný certifikát X.509 nelze mapovat na účet Windows. Alternativní název subjektu (UPN) je povinný.|  
|AESCryptSetKeyParamFailed|Nepovedlo se nastavit parametr zadaného klíče.|  
|TraceCodeSecuritySessionClosedResponseReceived|Relace zabezpečení klienta přijala uzavřené odpověď ze serveru.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Nelze vytvořit deformátovacím modulem podpis pro zadaný algoritmus ze zadaného asymetrického šifrování.|  
|TraceCodeIdentityModelAsyncCallbackThrewException|Asynchronní zpětné volání vrátilo výjimku.|  
|LengthMustBeGreaterThanZero|Délka tohoto argumentu musí být větší než 0.|  
|FoundMultipleCerts|Bylo nalezeno více certifikátů X.509 pomocí zadaná kritéria vyhledávání: StoreName, StoreLocation FindType, FindValue. Zadejte přesnější hledanou hodnotu.|  
|AtLeastOneTransformRequired|Element transformace musí obsahovat alespoň jedna transformace.|  
|SAMLTokenNotSerialized|Výraz SamlAssertion nebylo možné serializovat na XML. Podrobnosti najdete v informacích o vnitřní výjimce.|  
|TraceCodeSecurityBindingOutgoingMessageSecured|Protokol zabezpečení zabezpečil odchozí zprávu.|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|Tato klauzule SecurityKeyIdentifierClause nepodporuje vytváření klíčů.|  
|UnableToResolveTokenReference|Překladač tokenů nedokáže vyřešit zadaný odkaz na token.|  
|UnsupportedEncryptionAlgorithm|Zadaný šifrovací algoritmus není podporován.|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|SamlSerializer neobsahuje SecurityTokenSerializer, který daný SecurityKeyIdentifier serializace. Používáte-li vlastní SecurityKeyIdentifier, je nutné poskytnout vlastní SecurityTokenSerializer.|  
|SAMLAttributeShouldHaveOneValue|Nenašly se žádné hodnoty atributů. Atribut SamlAttribute musí mít alespoň jednu hodnotu.|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|Protokol zabezpečení nemůže zabezpečit příchozí zprávu.|  
|SamlSigningTokenMissing|Třída SamlSecurityTokenAuthenticator předán výraz SamlAssertion neobsahuje token podepisování.|  
|NoPrivateKeyAvailable|Je k dispozici žádný privátní klíč.|  
|ValueMustBeOne|Hodnota tohoto argumentu musí být 1.|  
|TraceCodeSecurityPendingServerSessionRemoved|Čekající relace zabezpečení byla provedena aktivní server.|  
|TraceCodeImportSecurityChannelBindingExit|Vazby dokončení zabezpečení ImportChannelBinding.|  
|X509CertStoreLocationNotValid|StoreLocation musí být LocalMachine ani CurrentUser.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|Nastavení zapisovače může změnit pouze v případě zapisovač, který je ve stavu spuštění.|  
|ArgumentInvalidCertificate|Certifikát je neplatný.|  
|DigestVerificationFailedForReference|Pro zadaný odkaz se nezdařilo ověřování algoritmem Digest.|  
|SAMLAuthorityBindingRequiresBinding|V třídě SamlAuthorityBinding zadán atribut "Vazba" nemůže být null nebo délka je 0.|  
|AESInsufficientOutputBuffer|Výstupní vyrovnávací paměť musí být větší než zadaný počet bajtů.|  
|SAMLAuthorityBindingMissingBindingOnRead|"Vazba" atribut pro třídu SamlAuthorityBinding chybí nebo délka je 0.|  
|SAMLAuthorityBindingInvalidAuthorityKind|Třídu SamlAuthorityBinding má neplatný AuthorityKind. Formát AuthorityKind musí být QName.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|NetworkCredentials poskytnuté pro Token protokolu Kerberos, který nemá žádné platné uživatelské jméno.|  
|SSPIPackageNotSupported|Zadaný balíček SSPI není podporován.|  
|TokenCancellationNotSupported|Zadaný Poskytovatel tokenu nepodporuje token zrušení.|  
|UnboundPrefixInQName|V zadané kvalifikovaný název je použita nevázaná předpona.|  
|SAMLAuthorizationDecisionResourceRequired|"Prostředek" určený pro třídu SamlAuthorizationDecisionStatement nemůže být null ani délka je 0.|  
|TraceCodeSecurityNegotiationProcessingFailure|Chyba zpracování vyjednávání zabezpečení služby.|  
|SAMLAssertionIssuerRequired|"Vystavitele' zadaná pro SamlAssertion nemůže být null ani prázdný.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Nelze vytvořit HashAlgorithm pro zadaný algoritmus ze zadaného asymetrického šifrování.|  
|SamlUnableToExtractSubjectKey|Nelze přeložit identifikátor SecurityKeyIdentifier nalezený SamlSubject na token SecurityToken. SecurityTokenResolver musí obsahovat token SecurityToken, který se přeloží identifikátor SecurityKeyIdentifier.|  
|ChildNodeTypeMissing|Zadaný element XML neobsahuje podřízený objekt zadaného typu.|  
|TraceCodeSecurityPendingServerSessionClosed|Server zavřel čekající relaci zabezpečení.|  
|TraceCodeSecuritySessionCloseResponseSent|Relace zabezpečení serveru odeslala klientovi odpověď zavřít.|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|Část HostName adresy koncového bodu nelze normalizovat.|  
|FailAcceptSecurityContext|Funkce AcceptSecurityContext se nezdařila.|  
|EmptyXmlElementError|Zadaný element nemůže být prázdný.|  
|PrefixNotDefinedForNamespace|Předpona pro zadaný obor názvů není definovaný v tomto kontextu a nejde použít deklaraci.|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|Bylo zjištěno, že třídu SamlAuthorizationDecisionStatement obsahovat více než jeden důkaz. Toto není povoleno.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|Třída SamlSecurityTokenAuthenticator může zpracovat pouze tokeny třídy SamlSecurit. Zadaný typ SecurityTokenType byla přijata.|  
|SAMLAttributeStatementMissingAttributeOnRead|SamlAttributeStatement čtená neobsahuje žádné prvky "SamlAttribute". Toto není povoleno.|  
|CouldNotFindNamespaceForPrefix|Nelze vyhledat obor názvů pro zadanou předponou.|  
|TraceCodeExportSecurityChannelBindingExit|Vazby dokončení zabezpečení ExportChannelBinding.|  
|AESCryptDecryptFailed|Nepovedlo se dešifrovat zadaná data.|  
|SAMLAttributeNamespaceAttributeRequired|"Namespace" zadaná pro třídu SamlAttribute nemůže být null ani délka je 0.|  
|TraceCodeSpnegoServiceNegotiationCompleted|Ověřovací data SpnegoTokenAuthenticator dokončila vyjednávání SSPI.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|Relace zabezpečení serveru odeslala chybu obnovení klíče do klienta.|  
|AlgorithmMismatchForTransform|Došlo k neshodě na algoritmus transformace.|  
|UserNameAuthenticationFailed|Ověřování uživatelského jména a hesla, pomocí zadané mechanismus se nezdařilo. Uživatel není ověřen.|  
|SamlInvalidSigningToken|Token, který nebyl ověřen podle protokolu byl podepsán výraz SamlAssertion. Pokud používáte certifikáty X.509, zkontrolujte vaši sémantiku ověření.|  
|TraceCodeSecurityServerSessionKeyUpdated|Server aktualizoval klíč relace zabezpečení.|  
|TraceCodeSecurityServerSessionCloseReceived|Relace zabezpečení serveru přijala od klienta zprávu zavřít.|  
|SAMLAuthenticationStatementMissingSubject|SamlAuthenticationStatement chybí požadované SamlSubjectStatement.|  
|UnexpectedEndOfFile|Neočekávaný konec souboru.|  
|UnsupportedAlgorithmForCryptoOperation|Zadaný algoritmus se nepodporuje pro danou operaci.|  
|XmlLangAttributeMissing|Chybí atribut XML: lang – povinné.|  
|TraceCodeSecurityImpersonationSuccess|Zosobnění zabezpečení se zdařilo na serveru.|  
|SAMLAuthorityBindingMissingLocationOnRead|Umístění atributu pro třídu SamlAuthorityBinding chybí nebo délka je 0.|  
|SAMLAttributeStatementMissingSubjectOnRead|Chybí element "SamlSubject" pro třídu SamlAttributeStatement.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|Chybí element "SamlSubject" pro třída SamlAuthorizationDecisionStatement, který je čten.|  
|SAMLBadSchema|Při čtení SamlAssertion byl nalezen tento zadaný element není pro dosažení souladu s schéma.|  
|SAMLAssertionIDIsInvalid|Zadaný "assertionId" pro SamlAssertion musí začínat písmenem nebo podtržítko (_).|  
|TraceCodeSecurityActiveServerSessionRemoved|Aktivní relace zabezpečení byla odebrána serverem.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Nelze vytvořit keyedHashAlgorithm pro zadaný algoritmus ze zadaného symetrickou šifru.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|"AuthenticationMethod' zadaná pro třídu SamlAuthenticationStatement nemůže být null ani délka je 0.|  
|TraceCodeSecurityImpersonationFailure|Zosobnění zabezpečení na serveru se nezdařilo.|  
|Výchozí|(Výchozí)|  
|UnsupportedNodeTypeInReader|Typ zadaný uzel se zadaným názvem není podporován.|
