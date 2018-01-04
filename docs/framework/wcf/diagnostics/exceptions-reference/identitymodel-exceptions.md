---
title: "Výjimky IdentityModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26bf6cb88d77fc9890a23c482913514f1dc856aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="identitymodel-exceptions"></a>Výjimky IdentityModel
Toto téma uvádí všechny výjimky generované IdentityModel.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Aktuálního řetězce|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|Hodnota argumentu musí být jedním z těchto dvou typů.|  
|SAMLSubjectNameIdentifierRequiresNameValue|Název zadaný pro třídu SamlNameIdentifier nemůže být null nebo délku 0.|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|Poskytovatel IssuanceTokenProvider dokončení vyjednávání zabezpečení.|  
|TraceCodeSecurityNewServerSessionKeyIssued|Vytvoření nové relace zabezpečení klíč byl vydán serverem.|  
|SAMLAttributeMissingNameAttributeOnRead|"Název" pro SamlAttribute načítán chybí nebo má délku 0.|  
|UnknownICryptoType|Implementace ICrypto není podporována.|  
|TraceCodeSecurityTokenProviderClosed|Došlo k ukončení poskytovatele tokenu zabezpečení.|  
|SAMLUnableToLoadAdvice|Nepodařilo se načíst \<saml:advice > elementu.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|Atribut 'AuthenticationMethod' pro třídu SamlAuthenticationStatement chybí nebo má délku 0.|  
|UnsupportedTransformAlgorithm|Nepodporované transformace nebo kanonizace algoritmus.|  
|SAMLAudienceRestrictionShouldHaveOneAudience|Třída SamlAudienceRestrictionCondition musí obsahovat alespoň jeden (identifikátor URI cílové skupiny).|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence musí odkazovat aspoň jeden SamlAssertion buď Id, nebo odkaz.|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|Načítaná třída SamlAudienceRestrictionCondition chybí hodnota v elementu 'Cílové skupiny'.|  
|X509ChainBuildFail|Konkrétní řetěz certifikátů X.509 sestavení se nezdařilo. Certifikát, který byl použit má důvěryhodný řetězec, který nelze ověřit. Nahradit certifikát, nebo změňte certificateValidationMode.|  
|XDCannotFindValueInDictionaryString|Konkrétní hodnotu id nebyl nalezen v řetězci slovníku.|  
|TraceCodeImportSecurityChannelBindingEntry|Spuštění vazby zabezpečení ImportChannelBinding.|  
|PrivateKeyExchangeNotSupported|Privátní klíč nepodporuje exchange specifikace klíče.|  
|TokenProviderUnableToGetToken|Konkrétního zprostředkovatele tokenu se nepodařilo poskytnout token zabezpečení.|  
|SAMLEntityCannotBeNullOrEmpty|Konkrétní entitu SamlAssertion nemůže být null nebo prázdný.|  
|SAMLAssertionRequireOneStatement|SamlAssertion vyžaduje alespoň jeden příkaz. Ujistěte se, že jste přidali alespoň jeden SamlStatement do SamlAssertion, kterou vytváříte.|  
|AESInvalidInputBlockSize|Vstupní velikost musí být násobkem konkrétní bajtů.|  
|AESCryptAcquireContextFailed|Nepodařilo se získat kontext zprostředkovatele kryptografických služeb.|  
|SAMLAssertionRequireOneStatementOnRead|Při čtení SamlAssertion neobsahuje žádné SamlStatement. SamlAssertion musí obsahovat alespoň jeden SamlStatement.|  
|TraceCodeSecuritySessionClosedFaultReceived|Relace zabezpečení klienta obdržel chybu při zavírání relace ze serveru.|  
|TraceCodeIssuanceTokenProviderRedirectApplied|Poskytovatel IssuanceTokenProvider použil záhlaví přesměrování.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|Při odesílání relaci zabezpečení zavření selhání klientovi došlo k chybě.|  
|ValueMustBeZero|Hodnota argumentu musí být 0.|  
|SAMLUnableToResolveSignatureKey|Nelze SecurityKeyIdentifier nalezený v označení SamlAssertion. Nelze ověřit podpis SamlAssertion pro konkrétní vystavitele.|  
|X509IsNotInTrustedStore|Konkrétní certifikát X.509 není v úložišti důvěryhodných osob.|  
|SAMLElementNotRecognized|Konkrétní elementu není podporován.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|Daný prostředek atribut pro třídu SamlAuthorizationDecisionStatement chybí nebo má délku 0.|  
|SamlTokenMissingSignature|SamlAssertion není podepsaná. SamlAssertions může být označen nastavením SigningCredentials.|  
|ExpectedElementMissing|Byl očekáván prvek s konkrétní obor názvů nebyl nalezen.|  
|NoKeyIdentifierClauseFound|V třídě SecurityKeyIdentifier nebyla nalezena žádná klauzule konkrétního typu.|  
|MissingPrivateKey|Privátní klíč není přítomen v certifikátu X.509.|  
|UnexpectedEOFFromReader|Neočekávané EOF ze čtečky XML.|  
|UnsupportedKeyDerivationAlgorithm|Algoritmus konkrétní odvození klíče není podporován.|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|Konkrétní token nepodporuje vytváření klauzule konkrétní identifikátor klíče.|  
|LastMessageNumberExceeded|Bylo zjištěno porušení protokolu pořadových čísel.|  
|SymmetricKeyLengthTooShort|Délka zadané symetrický klíč je příliš krátký.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|Probíhá SamlAuthorityBinding číst nenašel tak, aby obsahovala AuthorityKind, který byl chybí nebo má délku 0.  Toto není povoleno.|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer je prázdný.|  
|InvalidXmlQualifiedName|Byl očekáván kvalifikovaný název Xml, ale byl nalezen neplatný název.|  
|SAMLAuthorityKindMissingName|Třída XmlQualifiedName, která představuje 'AuthorityKind' ve třídě SamlAuthorityBinding nemůže být null nebo délku 0.|  
|AESCryptEncryptFailed|Nepodařilo se zašifrovat konkrétní data.|  
|AuthorizationContextCreated|Autorizační kontext s konkrétním id se vytvoří.|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|SamlSerializer neobsahuje SecurityTokenSerializer schopný čtení SecurityKeyIdentifier. Pokud používáte vlastní SecurityKeyIdentifier, je nutné zadat vlastní SecurityTokenSerializer.|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|Poskytovatel IssuanceTokenProvider snížit mezipaměť tokenu služby.|  
|TraceCodeSecurityTokenProviderOpened|Byl otevřen poskytovatele tokenu zabezpečení.|  
|PublicKeyNotRSA|Veřejný klíč není klíč RSA.|  
|InvalidReaderState|Konkrétní stav není platný pro zadaný vstupní čtečku.|  
|UnableToResolveReferenceUriForSignature|Nelze vyřešit konkrétní URI v podpis pro výpočet přehledu.|  
|EmptyBase64Attribute|Pro požadovaný název atributu base64 a obor názvů nebyl nalezen prázdnou hodnotu.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|SAML SubjectConfirmation vyžaduje potvrzení metodu, pokud je zadána potvrzení Data nebo KeyInfo.|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|Načítaná třída SamlAudienceRestrictionCondition musí obsahovat alespoň jeden, cílová skupina' hodnotu. Nebyl nalezen žádný.|  
|TokenProviderUnableToRenewToken|Konkrétního zprostředkovatele tokenu se nepodařilo obnovit token zabezpečení.|  
|AESIVLengthNotSupported|IV konkrétní bits není podporováno. Je podporován pouze IV 128 bitů.|  
|SAMLAuthorityBindingMissingAuthorityKind|Třída SamlAuthorityBinding musí obsahovat 'AuthorityKind, který není null.|  
|TraceCodeSecuritySessionDemuxFailure|Příchozí zpráva není součástí existující relaci zabezpečení.|  
|TokenRenewalNotSupported|Konkrétního zprostředkovatele tokenu nepodporuje obnovení tokenu.|  
|AtLeastOneReferenceRequired|V podpisu je vyžadován alespoň jeden odkaz.|  
|SAMLSignatureAlreadyRead|Podpis je již pro čtení kontrolního výrazu SAML.|  
|AlgorithmAndPrivateKeyMisMatch|Algoritmus zadané a privátní klíč nesouhlasí.|  
|EmptyTransformChainNotSupported|Prázdný řetězec transformace není podporováno.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper::EncryptDecryptHelper &#124;. Posun "je mimo rozsah.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper::EncryptDecryptHelper &#124;. velikost "je mimo rozsah. SecurityTokenManagerCannotCreateAuthenticatorForRequirement = zabezpečení tokenu manager nemůže vytvořit ověřovací data tokenu pro konkrétní požadavky.|  
|UnableToCreateKeyedHashAlgorithm|Nelze vytvořit KeyedHashAlgorithm z konkrétní hodnoty pro konkrétní podpisový algoritmus.|  
|SAMLUnableToLoadAssertion|\<Saml:assertion > elementu se nepodařilo načíst.|  
|X509FindValueMismatchMulti|Konkrétní X509FindType vyžaduje typ argumentu findValue být jedna z hodnot 2. Argument findValue je jiného typu.|  
|TraceCodeSecurityIdentityDeterminationSuccess|Byla určena pro EndpointAddress.|  
|UndefinedUseOfPrefixAtElement|Konkrétní předponu, která se používá v elementu nemá definován obor názvů.|  
|TraceCodeSecuritySessionResponderOperationFailure|Na serveru se nezdařila operace relace zabezpečení.|  
|CannotFindCert|Nepodařilo se najít certifikát X.509 pomocí kritérií hledání: StoreName, StoreLocation, FindType, FindValue.|  
|X509InvalidUsageTime|Určený čas využití certifikát X.509 je neplatný. Doba využití nespadá mezi čas potřebný před a neplatí po dobu.|  
|TraceCodeSecurityIdentityDeterminationFailure|Identitu nelze určit pro EndpointAddress.|  
|AsyncObjectAlreadyEnded|Metoda End již byla volána s tímto objektem asynchronní výsledek.|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|Externí slovník neobsahuje definice pro všechny požadované řetězce. Konkrétní řetězec není k dispozici ve slovníku vzdálené.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|Relace zabezpečení klienta přijala chybu obnovení klíče ze serveru.|  
|SAMLActionNameRequired|Řetězec, který představuje SamlAction nemůže být null nebo délku 0.|  
|SignatureVerificationFailed|Ověření podpisu se nezdařilo.|  
|TraceCodeSecurityContextTokenCacheFull|Paměť SecurityContextSecurityToken je plná.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|MajorVersion pro SamlAssertion, který je čten chybí nebo má délku 0.|  
|SamlAttributeClaimRightShouldBePossessProperty|Tento konstruktor SamlAttribute vyžaduje, aby měl napravo od deklarace hodnotu System.IdentityModel.Claims.Rights.PossessProperty.|  
|AuthorizationPolicyEvaluated|Zásada s konkrétním id vyhodnotí.|  
|SAMLUnableToLoadCondtions|\<Saml:conditions > elementu se nepodařilo načíst.|  
|AESKeyLengthNotSupported|Klíč konkrétní bits není podporován. Pouze 128, 192 a 256 bitů klíč je podporována.|  
|UserNameCannotBeEmpty|Uživatelské jméno nesmí být prázdný.|  
|AlgorithmAndPublicKeyMisMatch|Algoritmus zadané a veřejný klíč se neshodují.|  
|SAMLUnableToLoadCondtion|\<Saml:conditions > elementu se nepodařilo načíst.|  
|SamlAssertionMissingSigningCredentials|SigningCredentials nebyly nastaveny na SamlAssertion. SamlAssertions musí být podepsané, nastavte prosím platné SigningCredentials na SamlAssertion pro pokračování.|  
|SspiPayloadNotEncrypted|Binární data nebyla šifrován kontext zabezpečení rozhraní SSPI.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|Třída SamlAuthorizationDecisionStatement načítán neobsahuje žádnou SamlAction.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|Protokol zabezpečení nelze ho zabezpečit odchozí zprávy.|  
|UndefinedUseOfPrefixAtAttribute|Konkrétní Předpona použitá na konkrétní atribut nemá definován obor názvů.|  
|NoInputIsSetForCanonicalization|Žádný vstup není nastaveno pro zápis kanonizovaného výstupu.|  
|TraceCodeSecurityPendingServerSessionAdded|Čekající relace zabezpečení je přidána na server.|  
|AsyncCallbackException|AsyncCallback došlo k výjimce.|  
|PrivateKeyNotRSA|Privátní klíč není klíčem RSA.|  
|TraceCodeSecurityClientSessionKeyRenewed|Relace zabezpečení klienta obnovit klíč relace.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|"Rozhodnutí" pro třídu SamlAuthorizationDecisionStatement chybí, nebo má délku 0.|  
|SAMLAttributeNameAttributeRequired|Název zadaný pro třídu SamlAttribute nemůže být null nebo délku 0.|  
|SamlSerializerRequiresExternalSerializers|SamlSerializer vyžaduje SecurityTokenSerializer k serializaci SecurityKeyIdentifier uvedené v tokenu.|  
|UnableToResolveKeyReference|Překladač tokenu se nepodařilo vyřešit odkaz na konkrétní bezpečnostní klíč.|  
|UnsupportedKeyWrapAlgorithm|Algoritmus konkrétní zabalení klíče není podporován.|  
|SAMLAssertionMissingIssuerAttributeOnRead|'Vystavitele, pro SamlAssertion, který je čten chybí nebo má délku 0.|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|Poskytovatel IssuanceTokenProvider používá token v mezipaměti služby.|  
|AESCryptGetKeyParamFailed|Nepodařilo se získat parametr konkrétní klíče.|  
|InvalidNamespaceForEmptyPrefix|Obor názvů je neplatný pro prázdnou předponu.|  
|AESCipherModeNotSupported|Režim konkrétní šifrování není podporován. Je podporován pouze CBC.|  
|ArgumentCannotBeEmptyString|Argument musí být neprázdný řetězec.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|MinorVersion pro SamlAssertion, který je čten chybí nebo má délku 0.|  
|SpecifiedStringNotAvailableInDictionary|Zadaný řetězec není položku ve slovníku aktuální.|  
|KerberosApReqInvalidOrOutOfMemory|Asie a Tichomoří-REQ je neplatný nebo systém nemá dostatek paměti.|  
|FailLogonUser|LogonUser se nezdařila pro zadaného uživatele. Ujistěte se, že uživatel má platný účet systému Windows.|  
|ValueMustBeNonNegative|Hodnota argumentu musí být nezáporná.|  
|X509ValidationFail|Zadaný ověření certifikátu X.509 se nezdařilo.|  
|TraceCodeSecuritySessionRequestorOperationSuccess|Operace relace zabezpečení byla úspěšně dokončena na straně klienta.|  
|SAMLActionNameRequiredOnRead|Řetězec, který je pro čtení pro SamlAction chybí nebo má délku 0.|  
|KerberosMultilegsNotSupported|Identita je zadán jako hlavní název uživatele. Ověřování služby spuštěné pod uživatelským účtem vyžaduje více stehýnka protokolu Kerberos, který není podporován.|  
|SAMLAssertionIdRequired|'AssertionId' pro SamlAssertion nemůže být null nebo prázdný.|  
|InvalidOperationForWriterState|Zadaná operace není platná v zadaném stavu XmlWriter.|  
|CannotValidateSecurityTokenType|Ověřovací data tokenu zadaný zabezpečení nelze ověřit token zadaného typu.|  
|X509FindValueMismatch|Zadaný X509FindType vyžaduje typ argumentu findValue být zadaná hodnota. Argument findValue je jiného typu.|  
|TraceCodeSecurityClientSessionCloseSent|Relace zabezpečení klienta odeslala zprávu zavřete.|  
|SuiteDoesNotAcceptAlgorithm|Pro zadanou operaci zadaný algoritmus neakceptuje zadaný algoritmus suite|  
|TraceCodeSecuritySessionRequestorOperationFailure|Operace relace zabezpečení klienta se nezdařila.|  
|SAMLUnableToLoadStatement|Nepodařilo se načíst SamlStatement.|  
|InnerReaderMustBeAtElement|Vnitřní čtečky musí být v elementu.|  
|UnableToCreateTokenReference|Nelze vytvořit odkaz tokenu zabezpečení.|  
|TraceCodeSecurityBindingIncomingMessageVerified|Protokol zabezpečení ověřit příchozí zprávy.|  
|ObjectIsReadOnly|Objekt je jen pro čtení.|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|Relace zabezpečení klienta zahodí klíč předchozí relace.|  
|SAMLTokenTimeInvalid|SamlToken není chvíli platný. Aktuální čas je mimo dobu platnosti a vypršení platnosti tokenu.|  
|TraceCodeSecurityIdentityVerificationSuccess|Ověření identity bylo úspěšné.|  
|SigningTokenHasNoKeys|Zadaný token podpisový nemá žádné klíče.|  
|TraceCodeSecurityIdentityVerificationFailure|Ověření identity se nezdařilo.|  
|AESCryptImportKeyFailed|Nepodařilo se importovat materiál klíče.|  
|FailInitializeSecurityContext|Funkce InitializeSecurityContent se nezdařila. Zkontrolujte, zda že je správný hlavní název služby.|  
|TraceCodeStreamSecurityUpgradeAccepted|Upgrade zabezpečení datový proud byl úspěšně přijatá.|  
|SAMLAuthorityBindingRequiresLocation|Atribut 'Umístění', který je zadaný na třídě SamlAuthorityBinding nemůže být null nebo délku 0.|  
|PublicKeyNotDSA|Veřejný klíč není klíč DSA.|  
|ImpersonationLevelNotSupported|Režimy ověřování pomocí protokolu Kerberos nepodporuje úroveň zosobnění zadaný. Zadejte platnou úroveň identifikaci nebo zosobnění.|  
|RequiredTargetNotSigned|Element se zadaným id je potřeba podepsat, ale nebyla.|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|Atribut 'AuthenticationInstant' pro třídu SamlAuthenticationStatement chybí nebo má délku 0.|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|Načítaná třída SamlEvidence neobsahuje odkaz na nebo vložené SamlAssertion.|  
|LengthOfArrayToConvertMustGreaterThanZero|Délka pole převést na celé číslo musí být větší než 0.|  
|InvalidAsyncResult|Neplatný AsyncResult.|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|Poskytovatel IssuanceTokenProvider odebrat token služby vypršela platnost.|  
|IncorrectUserNameFormat|Uživatelské jméno je v neplatném formátu. Musí být ve formátu uživatelské jméno ve tvaru "uživatelského jména ' nebo ' domény\\\username'.|  
|TraceCodeExportSecurityChannelBindingEntry|Spuštění vazby zabezpečení ExportChannelBinding.|  
|UnsupportedInputTypeForTransform|Zadaný vstupní typ není podporován pro transformaci.|  
|CannotFindDocumentRoot|Kořen dokumentu se nenašel.|  
|XmlBufferQuotaExceeded|Potřeba ukládat do vyrovnávací paměti obsah XML velikost překročila kvótu pro vyrovnávací paměti.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|Při odesílání odpovědi zavřít relace zabezpečení klienta došlo k selhání.|  
|UnableToResolveReferenceInSamlSignature|Nelze vyřešit zadaný odkaz v podpis SAML s AssertionID.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|SamlSubject vyžaduje, aby byl specifikován 'NameIdentifier' nebo 'ConfirmationMethod'. Obě chyběly.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|Namespace pro SamlAttribute načítán chybí, nebo má délku 0.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|'ConfirmationMethod' nebyl nalezen na třídě SamlSubjectConfirmation.|  
|SecurityTokenRequirementHasInvalidTypeForProperty|Požadavek na token má neočekávaný typ pro zadanou vlastnost. Vlastnost očekávaný typ je jinou hodnotu.|  
|TraceCodeNegotiationTokenProviderAttached|Byl připojen poskytovatel NegotiationTokenProvider.|  
|TraceCodeSpnegoClientNegotiationCompleted|Poskytovatel SpnegoTokenProvider dokončil vyjednávání SSPI.|  
|SAMLUnableToLoadUnknownElement|Vybraný SamlSerializer nelze deserializovat tento element. Zaregistrujte vlastní SamlSerializer k deserializaci vlastní elementy.|  
|CreateSequenceRefused|Cíl služby RM odmítla požadavek na vytvoření sekvence.|  
|TraceCodeSecuritySessionRedirectApplied|Relace zabezpečení klienta byla přesměrována.|  
|SecurityTokenRequirementDoesNotContainProperty|Požadavek na token neobsahuje zadanou vlastnost.|  
|SAMLAttributeValueCannotBeNull|Jedna z hodnot atributů nalezených ve třídě SamlAttribute byl nalezen hodnotu null. Ujistěte se, že seznamy nejsou null, při vytváření třídy SamlAttribute.|  
|ValueMustBeGreaterThanZero|Hodnota argumentu musí být větší než 0.|  
|TraceCodeNegotiationAuthenticatorAttached|Byl připojen ověřovatel NegotiationTokenAuthenticator.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Třída SamlAuthorizationDecisionStatement musí mít alespoň jeden SamlAction.|  
|TraceCodeSecurityTokenAuthenticatorClosed|Došlo k ukončení ověřovacího modulu tokenu zabezpečení.|  
|TraceCodeSecurityAuditWrittenSuccess|Protokol auditu zabezpečení se nezapíše úspěšně.|  
|PrivateKeyNotDSA|Privátní klíč není klíč DSA.|  
|MessageNumberRollover|Byla překročena maximální pořadové číslo pro toto pořadí.|  
|AESPaddingModeNotSupported|Zadané odsazení režim není podporován. Je podporováno pouze PKCS7 a ISO10126.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|Požadované NameIdentifier a elementy 'ConfirmationMethod' nebyl nalezen pro SamlSubject, který je čten.|  
|TraceCodeSecurityAuditWrittenFailure|Došlo k chybě při zápisu do protokolu auditování zabezpečení.|  
|UnsupportedCryptoAlgorithm|Zadaný kryptografický algoritmus není podporován v tomto kontextu.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|Podpisový token má žádný klíč, který podporuje sadu zadaný algoritmus.|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|Chybí řetězec "Identifikátor" pro třídu SamlNameIdentifier.|  
|SAMLSubjectStatementRequiresSubject|Příkaz subjektu SAML vyžaduje předmět SAML, který chcete zadat.|  
|TraceCodeSslClientCertMissing|Klient vzdálené SSL se nepodařilo poskytnout požadovaný certifikát.|  
|SAMLTokenVersionNotSupported|Zadaný hlavní verze a podverze nejsou podporovány.|  
|TraceCodeConfigurationIsReadOnly|Konfigurace je jen pro čtení.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|Při odesílání chyby obnovení na klíč relace zabezpečení klientovi došlo k selhání.|  
|TraceCodeSecurityInactiveSessionFaulted|Neaktivní relaci zabezpečení došlo k chybě, serverem.|  
|SAMLUnableToLoadAttribute|Nepodařilo se načíst třídu SamlAttribute.|  
|Psha1KeyLengthInvalid|Zadaná délka klíče PSHA1 je neplatný.|  
|KeyIdentifierCannotCreateKey|Tato třída SecurityKeyIdentifier nemá žádnou klauzuli, která můžete vytvořit klíč.|  
|X509IsInUntrustedStore|Zadaný certifikát X.509 je v úložišti nedůvěryhodný certifikát.|  
|UnexpectedXmlChildNode|Zadaný podřízený uzel XML zadaný typ neočekávaný u daného elementu.|  
|TokenDoesNotMeetKeySizeRequirements|Pomocí zadaného tokenu nejsou splněny požadavky na velikost klíče pro zadaný algoritmus suite.|  
|TraceCodeSecuritySessionRequestorStartOperation|Operace relace zabezpečení byla spuštěna na straně klienta.|  
|InvalidHexString|Neplatný formát šestnáctkového řetězce.|  
|SamlAttributeClaimResourceShouldBeAString|Tento konstruktor SamlAttribute vyžaduje, aby prostředků deklarace identity typu 'řetězec'.|  
|SamlSigningTokenNotFound|SamlAssertion je ale token, který podepsal SamlAssertion nebyl nalezen. Ujistěte se, že SecurityTokenResolver obsahuje token, který podepsal SamlAssertion.|  
|TraceCodeSecuritySpnToSidMappingFailure|ServicePrincipalName nelze namapovat na SecurityIdentifier.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Nelze vytvořit podpis formátování pro zadaný algoritmus z zadaný asymetrického kódování.|  
|TraceCodeSecurityServerSessionClosedFaultSent|Relace zabezpečení serveru může odeslat klientovi chybu při zavírání relace.|  
|UnableToFindPrefix|Nepodařilo se najít předponu pro Zadaná předpona viditelně použité v daného elementu.|  
|TraceCodeSecurityTokenAuthenticatorOpened|Byl otevřen ověřovacího modulu tokenu zabezpečení.|  
|RequiredAttributeMissing|Zadaný atribut je požadován u daného elementu.|  
|LocalIdCannotBeEmpty|LocalId nemůže být prázdný. Zadejte platný 'localId'.|  
|ValueMustBeInRange|Hodnota argumentu musí být v zadaném rozsahu.|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|Poskytovatel IssuanceTokenProvider spustit nové vyjednávání zabezpečení.|  
|InvalidNtMapping|Zadaný certifikát X.509 nelze mapovat na účet systému Windows. Alternativní název subjektu UPN je povinný.|  
|AESCryptSetKeyParamFailed|Nepodařilo se nastavit parametr zadaného klíče.|  
|TraceCodeSecuritySessionClosedResponseReceived|Relace zabezpečení klienta obdržel uzavřené odpověď ze serveru.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Nelze vytvořit deformátovač pro zadaný algoritmus z zadaný asymetrického kódování.|  
|TraceCodeIdentityModelAsyncCallbackThrewException|Asynchronní zpětné volání došlo k výjimce.|  
|LengthMustBeGreaterThanZero|Délka argumentu musí být větší než 0.|  
|FoundMultipleCerts|Nalezeno více certifikátů X.509 pomocí zadaná kritéria vyhledávání: StoreName, StoreLocation, FindType, FindValue. Zadejte hodnotu konkrétnější najít.|  
|AtLeastOneTransformRequired|Element transformace musí obsahovat alespoň jeden transformace.|  
|SAMLTokenNotSerialized|SamlAssertion se nedá serializovat na XML. Podrobnosti viz vnitřní výjimka.|  
|TraceCodeSecurityBindingOutgoingMessageSecured|Protokol zabezpečení zabezpečené odchozí zprávy.|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|SecurityKeyIdentifierClause nepodporuje vytvoření klíče.|  
|UnableToResolveTokenReference|Překladač tokenu se nepodařilo vyřešit zadaný odkaz na tokenu.|  
|UnsupportedEncryptionAlgorithm|Zadané šifrovací algoritmus nepodporuje.|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|SamlSerializer neobsahuje SecurityTokenSerializer schopný serializace daného SecurityKeyIdentifier. Pokud používáte vlastní SecurityKeyIdentifier, je nutné zadat vlastní SecurityTokenSerializer.|  
|SAMLAttributeShouldHaveOneValue|Nebyly nalezeny žádné hodnoty atributu. Atribut třídy SamlAttribute musí mít hodnotu alespoň jeden atribut.|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|Protokol zabezpečení nelze ověřit příchozí zprávy.|  
|SamlSigningTokenMissing|SamlAssertion předaný Třída SamlSecurityTokenAuthenticator neobsahuje podpisový token.|  
|NoPrivateKeyAvailable|Žádný privátní klíč je k dispozici.|  
|ValueMustBeOne|Hodnota argumentu musí být 1.|  
|TraceCodeSecurityPendingServerSessionRemoved|Čekající relace zabezpečení byla provedena aktivní server.|  
|TraceCodeImportSecurityChannelBindingExit|Vazby zabezpečení dokončení ImportChannelBinding.|  
|X509CertStoreLocationNotValid|StoreLocation musí být buď LocalMachine nebo CurrentUser.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|Nastavení zapisovače může změnit pouze v případě, že modul pro zápis je ve stavu spuštění.|  
|ArgumentInvalidCertificate|Certifikát je neplatný.|  
|DigestVerificationFailedForReference|Pro zadaný odkaz se nezdařilo ověření obsahu.|  
|SAMLAuthorityBindingRequiresBinding|V třídě SamlAuthorityBinding zadán atribut 'Vazby' nemůže být null nebo délku 0.|  
|AESInsufficientOutputBuffer|Výstupní vyrovnávací paměť musí být větší než zadaný počet bajtů.|  
|SAMLAuthorityBindingMissingBindingOnRead|Je vazba atributu pro třídu SamlAuthorityBinding chybí, nebo má délku 0.|  
|SAMLAuthorityBindingInvalidAuthorityKind|Třídu SamlAuthorityBinding má neplatný AuthorityKind. QName musí být ve formátu AuthorityKind.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|NetworkCredentials poskytnuté pro Token protokolu Kerberos nemá platné uživatelské jméno.|  
|SSPIPackageNotSupported|Zadaný balíček SSPI není podporován.|  
|TokenCancellationNotSupported|Zadaný zprostředkovatel tokenu nepodporuje tokenu zrušení.|  
|UnboundPrefixInQName|Volná předpona se používá v zadané kvalifikovaný název.|  
|SAMLAuthorizationDecisionResourceRequired|'' Zadaný prostředek pro třídu SamlAuthorizationDecisionStatement nemůže být null nebo délku 0.|  
|TraceCodeSecurityNegotiationProcessingFailure|Chyba zpracování vyjednávání zabezpečení služby.|  
|SAMLAssertionIssuerRequired|'Vystavitele, určený pro SamlAssertion nemůže být null nebo prázdný.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Nelze vytvořit algoritmus has pro zadaný algoritmus z zadaný asymetrického kódování.|  
|SamlUnableToExtractSubjectKey|SecurityKeyIdentifier, která byla nalezena v SamlSubject nelze přeložit na třídu SecurityToken. SecurityTokenResolver musí obsahovat SecurityToken, který se třída SecurityKeyIdentifier.|  
|ChildNodeTypeMissing|Zadaný element XML nemá žádné podřízené zadaného typu.|  
|TraceCodeSecurityPendingServerSessionClosed|Čekající zabezpečení relace byla ukončena serverem.|  
|TraceCodeSecuritySessionCloseResponseSent|Relace zabezpečení serveru odeslala Zavřít odpověď klientovi.|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|Část názvu hostitele adresy koncového bodu nelze normalizovat.|  
|FailAcceptSecurityContext|Funkce AcceptSecurityContext se nezdařila.|  
|EmptyXmlElementError|Zadaný element nesmí být prázdný.|  
|PrefixNotDefinedForNamespace|Předpona pro zadaný obor názvů není definován v tomto kontextu a nelze deklarovat.|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|Byl nalezen třídu SamlAuthorizationDecisionStatement obsahovat více než jeden důkaz. Toto není povoleno.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|Třída SamlSecurityTokenAuthenticator může zpracovat pouze tokeny třídy SamlSecurit. Zadaný typ SecurityTokenType byla přijata.|  
|SAMLAttributeStatementMissingAttributeOnRead|Načítaná třída SamlAttributeStatement neobsahuje žádné elementy, SamlAttribute'. Toto není povoleno.|  
|CouldNotFindNamespaceForPrefix|Nelze vyhledat obor názvů pro zadané předpony.|  
|TraceCodeExportSecurityChannelBindingExit|Vazby zabezpečení dokončení ExportChannelBinding.|  
|AESCryptDecryptFailed|Nepodařilo se dešifrovat zadaná data.|  
|SAMLAttributeNamespaceAttributeRequired|'Namespace' zadaná pro třídu SamlAttribute nemůže být null nebo délku 0.|  
|TraceCodeSpnegoServiceNegotiationCompleted|Ověřovatel SpnegoTokenAuthenticator dokončil vyjednávání SSPI.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|Relace zabezpečení serveru může odeslat klientovi chybu obnovení klíče.|  
|AlgorithmMismatchForTransform|Na algoritmu pro transformaci došlo k neshodě.|  
|UserNameAuthenticationFailed|Ověřování uživatelského jména a hesla pomocí zadané mechanismus se nezdařilo. Uživatel není ověřen.|  
|SamlInvalidSigningToken|SamlAssertion byl podepsán token, který nebyl ověřen podle protokolu. Pokud používáte certifikáty X.509, zkontrolujte vaši sémantiku ověření.|  
|TraceCodeSecurityServerSessionKeyUpdated|Klíč relace zabezpečení byla aktualizována serverem.|  
|TraceCodeSecurityServerSessionCloseReceived|Relace zabezpečení serveru Zavřít zprávu přijatou od klienta.|  
|SAMLAuthenticationStatementMissingSubject|SamlAuthenticationStatement chybí požadované SamlSubjectStatement.|  
|UnexpectedEndOfFile|Neočekávaný konec souboru.|  
|UnsupportedAlgorithmForCryptoOperation|Zadaný algoritmus nepodporuje pro danou operaci.|  
|XmlLangAttributeMissing|Chybí požadované XML: lang atribut.|  
|TraceCodeSecurityImpersonationSuccess|Zosobnění zabezpečení na serveru bylo úspěšně dokončeno.|  
|SAMLAuthorityBindingMissingLocationOnRead|Umístění atribut pro třídu SamlAuthorityBinding chybí nebo má délku 0.|  
|SAMLAttributeStatementMissingSubjectOnRead|Element 'SamlSubject' pro třídu SamlAttributeStatement chybí.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|Element 'SamlSubject, pro který je čten třída SamlAuthorizationDecisionStatement chybí.|  
|SAMLBadSchema|Při čtení SamlAssertion byl nalezen tento zadaný element nesplňuje schématu.|  
|SAMLAssertionIDIsInvalid|Zadaný 'assertionId' pro SamlAssertion musí začínat písmenem nebo '_'.|  
|TraceCodeSecurityActiveServerSessionRemoved|Aktivní relace zabezpečení byla odebrána serverem.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Nelze vytvořit keyedHashAlgorithm pro zadaný algoritmus ze zadaného symetrického šifrování.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|'AuthenticationMethod' zadaná pro třídu SamlAuthenticationStatement nemůže být null nebo délku 0.|  
|TraceCodeSecurityImpersonationFailure|Na serveru se nezdařilo zosobnění zabezpečení.|  
|Výchozí|(Výchozí)|  
|UnsupportedNodeTypeInReader|Typ zadaný uzel se zadaným názvem není podporován.|
