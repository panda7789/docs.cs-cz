---
title: Protokoly zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], protocols
ms.assetid: 57ffcbea-807c-4e43-a41c-44b3db8ed2af
ms.openlocfilehash: d09dd6bcb8564f770df6b87751aee4cdb04cd12c
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144614"
---
# <a name="security-protocols"></a>Protokoly zabezpečení
Protokoly specifikace Web Services Security poskytují mechanismy zabezpečení webových služeb, které pokrývají všechny stávající požadavky na zabezpečení podnikových zpráv. Tato část popisuje informace o Windows Communication Foundation (WCF) (implementované v nástroji <xref:System.ServiceModel.Channels.SecurityBindingElement> ) pro následující protokoly zabezpečení webových služeb.  
  
|Specifikace/dokument|Odkaz|  
|-|-|  
|WSS: zabezpečení zpráv SOAP 1,0|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|  
|WSS: Profil tokenu uživatelského jména 1,0|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|  
|WSS: Profil tokenu x509 1,0|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|  
|WSS: Profil tokenu SAML 1,1 1,0|<http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|  
|WSS: zabezpečení zpráv SOAP 1,1|<http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|  
|Token uživatelského jména WSS – profil 1,1|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|  
|WSS: X. 509 – profil tokenu 1,1|<http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|  
|WSS: Profil tokenu protokolu Kerberos 1,1|<http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|  
|WSS: Profil tokenu SAML 1,1 1,1|<http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|  
|WS-Secure – konverzace 1,3|<http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512/ws-secureconversation-1.3-os.pdf>|  
|WS-Trust 1,3|<http://docs.oasis-open.org/ws-sx/ws-trust/200512/ws-trust-1.3-os.pdf>|  
|Poznámka k aplikaci:<br /><br /> Použití WS-Trust pro handshake TLS|K publikování|  
|Poznámka k aplikaci:<br /><br /> Používání WS-Trust pro SPNEGO|K publikování|  
|Poznámka k aplikaci:<br /><br /> Odkazy a identita koncových bodů adresování webových služeb|K publikování|  
|WS-SecurityPolicy 1,2 (2007/04)|<http://www.oasis-open.org/committees/download.php/23821/ws-securitypolicy-1.2-spec-cs.pdf>|  
  
 Služba WCF verze 1 poskytuje 17 režimů ověřování, které lze použít jako základ pro konfiguraci zabezpečení webových služeb. Jednotlivé režimy jsou optimalizované pro společnou sadu požadavků na nasazení, jako například:  
  
- Pověření používaná k ověřování klienta a služby.  
  
- Mechanismy ochrany zabezpečení zpráv nebo přenosů.  
  
- Vzory výměny zpráv.  
  
|Režim ověřování|Ověření klienta|Ověřování serveru|Mode|  
|-------------------------|---------------------------|---------------------------|----------|  
|UserNameOverTransport|Uživatelské jméno a heslo|X509|Přenos|  
|CertificateOverTransport|X509|X509|Přenos|  
|KerberosOverTransport|Windows|X509|Přenos|  
|IssuedTokenOverTransport|Federovaní|X509|Přenos|  
|SspiNegotiatedOverTransport|Vyjednávání SSPI systému Windows|Vyjednávání SSPI systému Windows|Přenos|  
|AnonymousForCertificate|Žádné|X509|Zpráva|  
|UserNameForCertificate|Uživatelské jméno a heslo|X509|Zpráva|  
|MutualCertificate|X509|X509|Zpráva|  
|MutualCertificateDuplex|X509|X509|Zpráva|  
|IssuedTokenForCertificate|Federovaní|X509|Zpráva|  
|Kerberos|Windows|Windows|Zpráva|  
|Třídy IssuedToken|Federovaní|Federovaní|Zpráva|  
|SspiNegotiated|Vyjednávání SSPI systému Windows|Vyjednávání SSPI systému Windows|Zpráva|  
|AnonymousForSslNegotiated|Žádné|X509, TLS-NEGO|Zpráva|  
|UserNameForSslNegotiated|Uživatelské jméno a heslo|X509, TLS-NEGO|Zpráva|  
|MutualSslNegotiated|X509|X509, TLS-NEGO|Zpráva|  
|IssuedTokenForSslNegotiated|Federovaní|X509, TLS-NEGO|Zpráva|  
  
 Koncové body využívající takové režimy ověřování mohou vyjádřit požadavky na zabezpečení pomocí WS-SecurityPolicy (WS-SP). Tento dokument popisuje strukturu záhlaví zabezpečení a zpráv infrastruktury pro každý režim ověřování a poskytuje příklady zásad a zpráv.  
  
 WCF využívá WS-SecureConversation k poskytování zabezpečených relací, které umožňují chránit výměny více zpráv mezi aplikacemi.  Podrobnosti o implementaci najdete níže v části "zabezpečené relace".  
  
 Kromě režimů ověřování nabízí WCF nastavení pro řízení běžných mechanismů ochrany, které se vztahují na většinu režimů ověřování založených na zabezpečení zpráv, například: pořadí podpisů a operací šifrování, sady algoritmů, odvození klíče a potvrzení podpisu.  
  
 V tomto dokumentu se používají následující předpony a obory názvů.  
  
|Předpona|Obor názvů|  
|------------|---------------|  
|s|`http://www.w3.org/2003/05/soap-envelope`|  
|sp|`http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702`|  
|a|`http://www.w3.org/2005/08/addressing`|  
|wsse|TBD – OASIS WSS 1,0 URI|  
|wsse11|TBD – OASIS WSS 1,1 URI|  
|wsu|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd`|  
|služby|TBD – XMLDSig URI W3C|  
|WST|TBD – WS-Trust 2005/02 URI|  
|wssc|TBD – WS-SecureConversation 2005/02 URI|  
|wsaw|`http://www.w3.org/2006/05/addressing/wsdl`|  
|WSP|`http://schemas.xmlsoap.org/ws/2004/09/policy`|  
|mssp|`http://schemas.microsoft.com/ws/2005/07/securitypolicy`|  
  
## <a name="1-token-profiles"></a>1. profily tokenů  
 Specifikace specifikace Web Services Security reprezentují přihlašovací údaje jako tokeny zabezpečení. WCF podporuje následující typy tokenů:  
  
### <a name="11-usernametoken"></a>1,1 UsernameToken  
 WCF sleduje profily UsernameToken10 a UsernameToken11 s následujícími omezeními:  
  
 Atribut R1101 PasswordType elementu UsernameToken\Password musí být buď vynechán, nebo musí mít hodnotu #PasswordText (výchozí).  
  
 Jeden může implementovat #PasswordDigest s využitím rozšiřitelnosti. Zjistilo se, že #PasswordDigest bylo často zaměněno jako zabezpečený dostatečný mechanismus ochrany heslem. #PasswordDigest ale nemůžou sloužit jako náhrada za šifrování UsernameToken. Primárním cílem #PasswordDigest je ochrana před útoky přes opakované přehrání. V režimech ověřování WCF se hrozby útoku na opakování sníží pomocí podpisů zpráv.  
  
 B1102 WCF nikdy negeneruje hodnoty nonce a vytvořil dílčí prvky pro UsernameToken.  
  
 Tyto dílčí prvky jsou určeny k detekci opětovného přehrání. WCF místo toho používá podpisy zpráv.  
  
 OASIS WSS protokolu SOAP Message Security UsernameToken Profile 1,1 (UsernameToken11) zavedla odvození klíče z funkce Password.  
  
 Heslo B1103 UsernameToken nesmí být použito pro odvození klíče, a proto pro kryptografické operace.  
  
 Odůvodnění: hesla se obecně považují za příliš slabá, aby je bylo možné použít pro kryptografické operace.  
  
### <a name="12-x509-token"></a>Token x509 1,2  
 WCF podporuje certifikáty X509v3 jako typ přihlašovacích údajů a sleduje X509TokenProfile 1.0 a X509TokenProfile 1.1 s následujícími omezeními:  
  
 R1201 atribut ValueType elementu BinarySecurityToken musí mít hodnotu #X509v3, pokud obsahuje certifikát X509v3.  
  
 Definice tokenu WSS x509 1,0 a 1,1 také #X509PKIPathv1 a #PKCS7 jako typy hodnot. WCF tyto typy nepodporuje.  
  
 R1202 Pokud je v certifikátu x509 k dispozici rozšíření SubjectKeyIdentifier (SKI), wsse: identifikátor klíče by měl být použit pro externí odkazy na token, s atributem ValueType nastaveným jako #X509SubjectKeyIdentifier a jeho obsahem je hodnota kódovaná rozšíření certifikátu ve formátu base64.  
  
 Odkazy na SKI jsou široce implementovány a ověřeny jako vysoce interoperabilní externí typ odkazu.  
  
 R1203 externí odkaz na token zabezpečení x509 by neměl používat DS: X509IssuerSerial.  
  
 R1204 Pokud se používá X509TokenProfile 1.1, externí odkaz na token zabezpečení x509 by měl používat kryptografický otisk, který zavádí WS-Security 1,1.  
  
 WCF podporuje X509IssuerSerial. Existují však problémy interoperability s X509IssuerSerial: WCF používá řetězec k porovnání dvou hodnot X509IssuerSerial. Proto pokud jedna změna pořadí součástí názvu subjektu a odesílá do služby WCF odkaz na certifikát, nemusí být nalezena.  
  
### <a name="13-kerberos-token"></a>Token protokolu Kerberos 1,3  
 WCF podporuje KerberosTokenProfile 1.1 pro účely ověřování systému Windows s těmito omezeními:  
  
 R1301 token protokolu Kerberos musí mít hodnotu zabaleného protokolu Kerberos v4 AP_REQ, jak je definováno v GSS_API a specifikace protokolu Kerberos, a musí mít atribut ValueType s hodnotou #GSS_Kerberosv5_AP_REQ.  
  
 WCF používá zabalené ověřování pomocí služby GSS AP-REQ, nikoli úplného přístupového bodu-REQ. To je nejlepší postup zabezpečení.  
  
### <a name="14-saml-v11-token"></a>Token SAML v 1.1 1,4  
 WCF podporuje pro tokeny SAML v 1.1 profily tokenů SAML v WSS 1,0 a 1,1. Je možné implementovat jiné verze formátů tokenů SAML.  
  
### <a name="15-security-context-token"></a>Token kontextu zabezpečení 1,5  
 Služba WCF podporuje token kontextu zabezpečení (SCT) představený v WS-SecureConversation. SCT se používá k reprezentaci kontextu zabezpečení vytvořeného v SecureConversation a také binárních protokolů pro vyjednávání TLS a SSPI popsaných níže.  
  
## <a name="2-common-message-security-parameters"></a>2. běžné parametry zabezpečení zpráv  
  
### <a name="21-timestamp"></a>Časové razítko 2,1  
 Přítomnost časového razítka je řízena pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> vlastnosti <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. WCF vždycky serializace wsse: TimeStamp pomocí polí wsse: created a wsse: Expires. Wsse: časové razítko je vždy podepsáno při použití podepisování.  
  
### <a name="22-protection-order"></a>2,2. pořadí ochrany  
 WCF podporuje pořadí zpráv před zašifrováním a před podepsáním (zásady zabezpečení 1,2). Doporučuje se z důvodů, mezi které patří: zprávy chráněné pomocí šifrování před tím, než se nepoužije SignatureConfirmation mechanismus WS-Security 1,1 a signatura šifrovaného obsahu, zajistí, aby auditování bylo těžší.  
  
### <a name="23-signature-protection"></a>2,3 signatura ochrany  
 Při šifrování před použitím podpisu se doporučuje chránit signaturu, aby nedocházelo k útokům hrubou silou za účelem odhadování šifrovaného obsahu nebo podpisového klíče (zejména pokud se vlastní token používá se slabým materiálem klíče).  
  
### <a name="24-algorithm-suite"></a>Sada algoritmů 2,4  
 WCF podporuje všechny sady algoritmů uvedené v zásadách zabezpečení 1,2.  
  
### <a name="25-key-derivation"></a>2,5 odvození klíče  
 WCF používá odvození klíče pro symetrické klíče, jak je popsáno v tématu WS-SecureConversation.  
  
### <a name="26-signature-confirmation"></a>2,6 potvrzení podpisu  
 Potvrzení podpisu se dá použít jako ochrana proti útokům ze střední osoby k ochraně sady podpisů.  
  
### <a name="27-security-header-layout"></a>2,7 rozvržení záhlaví zabezpečení  
 Každý režim ověřování popisuje určité rozložení pro záhlaví zabezpečení. Prvky v záhlaví zabezpečení jsou částečně seřazené. Pro definování pořadí podřízených prvků záhlaví zabezpečení definuje zásada WS-Security následující režimy rozvržení záhlaví zabezpečení:  
  
|||  
|-|-|  
|Striktní|Položky jsou přidány do záhlaví zabezpečení podle pravidel číslovaného rozložení, které jsou popsány v části zásady zabezpečení 7.7.1, podle obecné zásady deklarace před použitím.|  
|LAX|Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, které odpovídá WSS: zabezpečení zpráv SOAP.|  
|LaxTimestampFirst|Stejné jako LAX s tím rozdílem, že první položka v záhlaví zabezpečení musí být wsse: Timestamp|  
|LaxTimestampLast|Stejné jako LAX s tím rozdílem, že poslední položka v záhlaví zabezpečení musí být wsse: Timestamp|  
  
 WCF podporuje všechny čtyři režimy pro rozložení záhlaví zabezpečení. Struktura záhlaví zabezpečení a příklady zpráv pro režimy ověřování níže následují po "striktním" režimu.  
  
## <a name="3-common-message-security-parameters"></a>3. běžné parametry zabezpečení zpráv  
 V této části najdete příklady zásad pro jednotlivé režimy ověřování spolu s příklady zobrazení struktury záhlaví zabezpečení ve zprávách vyměňovaných klientem a službou.  
  
### <a name="31-transport-protection"></a>3,1 Transport Protection  
 WCF nabízí pět režimů ověřování, které používají k ochraně zpráv zabezpečený přenos. UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport a SspiNegotiatedOverTransport.  
  
 Tyto režimy ověřování jsou vytvořeny pomocí přenosové vazby popsané v části SecurityPolicy. Pro režim ověřování UserNameOverTransport je UsernameToken podepsaný podpůrný token. Pro jiné režimy ověřování se token zobrazí jako podepsaný token. Příloha C. 1.2 a C. 1.3 programu SecurityPolicy popisují podrobné rozložení záhlaví zabezpečení. Následující příklady hlaviček zabezpečení znázorňují striktní rozložení pro daný režim ověřování.  
  
 Hodnota vlastnosti "odvozené klíče" pro tokeny ve všech případech je "false".  
  
 Hodnoty různých vlastností transportní vazby jsou následující:  
  
 Časové razítko: true  
  
 Rozložení záhlaví zabezpečení: striktní  
  
 Sada algoritmů: Basic256  
  
#### <a name="311-usernameovertransport"></a>UsernameOverTransport 3.1.1  
 V tomto režimu ověřování se klient ověřuje pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token, který se vždy odesílá z iniciátoru příjemci. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Použitá vazba je přenosová vazba.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="UserNameOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 Rozložení záhlaví zabezpečení  
  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:UsernameToken u:Id="uuid-b96fbb3a-e646-4403-9473-2e5ffc733ff8-1"> ... </o:UsernameToken></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="312-certificateovertransport"></a>3.1.2 CertificateOverTransport  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako připravující token, který se vždycky odesílá z iniciátoru příjemci. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Použitá vazba je přenosová vazba. CertificateOverTransport podepisuje pouze hlavičky SOAP, nikoli tělo SOAP. Jedná se o režim ověřování používaný režimem zabezpečení TransportWithMessageCredentials. Pouze hlavičky SOAP jsou podepsány, protože ověřování je provedeno pomocí pověření zprávy.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="CertificateOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 Rozložení záhlaví zabezpečení  
  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="313-issuedtokenovertransport"></a>IssuedTokenOverTransport 3.1.3  
 V tomto režimu ověřování klient neověřuje službu, například, ale prezentuje token vydaný službou tokenu zabezpečení (STS) a prokáže znalosti sdíleného klíče. Vydaný token se zobrazí ve vrstvě SOAP jako průkazní token, který je vždycky odesílán od iniciátoru příjemci. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Vazba je přenosová vazba.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenOverTransport_policy">
 <wsp:ExactlyOne>
  <wsp:All>
   <sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:TransportToken>
      <wsp:Policy>
       <sp:HttpsToken />
      </wsp:Policy>
     </sp:TransportToken>
     <sp:AlgorithmSuite>
      <wsp:Policy>
       <sp:Basic256 />
      </wsp:Policy>
     </sp:AlgorithmSuite>
     <sp:Layout>
      <wsp:Policy>
       <sp:Strict/>
      </wsp:Policy>
     </sp:Layout>
     <sp:IncludeTimestamp/>
    </wsp:Policy>
   </sp:TransportBinding>
   <sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient">
      <Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
       <Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address>
       <Metadata xmlns="http://www.w3.org/2005/08/addressing">
        <Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
         <wsx:MetadataSection xmlns="">
          <wsx:MetadataReference>
           <Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address>
           <Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity">
            <Dns> ...  </Dns>
           </Identity>
          </wsx:MetadataReference>
         </wsx:MetadataSection>
        </Metadata>
       </Metadata>
      </Issuer>
      <sp:RequestSecurityTokenTemplate>
       <trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType>
      </sp:RequestSecurityTokenTemplate>
      <wsp:Policy>
       <sp:RequireInternalReference/>
      </wsp:Policy>
     </sp:IssuedToken>
     <sp:SignedParts>
      <sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/>
     </sp:SignedParts>
    </wsp:Policy>
   </sp:EndorsingSupportingTokens>
   <sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/>
     <sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/>
    </wsp:Policy>
   </sp:Wss11>
   <sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportIssuedTokens/>
     <sp:RequireClientEntropy/>
     <sp:RequireServerEntropy/>
    </wsp:Policy>
   </sp:Trust13>
   <wsaw:UsingAddressing/>
  </wsp:All>
 </wsp:ExactlyOne>
</wsp:Policy>
```  
  
 Rozložení záhlaví zabezpečení  
  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67692bb6-85b7-4299-8587-3ce60086b0d2-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="314-kerberosovertransport"></a>KerberosOverTransport 3.1.4  
 V tomto režimu ověřování klient ověřuje službu pomocí lístku Kerberos. Token protokolu Kerberos se zobrazí ve vrstvě SOAP jako token podporující potvrzení. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Vazba je přenosová vazba.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="KerberosOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 Rozložení záhlaví zabezpečení  
  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="315-sspinegotiatedovertransport"></a>3.1.5 SspiNegotiatedOverTransport  
 V tomto režimu se k ověřování klienta a serveru používá protokol vyjednávání. Kerberos se používá, pokud je to možné, jinak NTLM. Výsledný SCT se zobrazí ve vrstvě SOAP jako průkazní token, který je vždy odeslán od iniciátoru příjemci. Služba se navíc ověřuje na transportní vrstvě pomocí certifikátu X. 509. Použitá vazba je přenosová vazba. "SPNEGO" (vyjednávání) popisuje, jak WCF používá protokol binárního vyjednávání SSPI s WS-Trust. Příklady hlaviček zabezpečení v této části jsou po navázání SCT prostřednictvím metody handshake SPNEGO.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiatedOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples"></a>Příklady záhlaví zabezpečení  
 Jakmile je token kontextu zabezpečení vytvořen pomocí SPNEGO handshake pomocí binárního vyjednávání WS-Trust, budou zprávy aplikace obsahovat záhlaví zabezpečení s následující strukturou.  
  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-9a29d087-5dae-4d40-bf86-5746d9d30eca-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
### <a name="32-using-x509-certificates-for-service-authentication"></a>3,2 použití certifikátů X. 509 pro ověřování služby  
 Tato část popisuje následující režimy ověřování: MutualCertificate WSS 1.0, vzájemné CertificateDuplex, MutualCertificate WSS 1.1, AnonymousForCertificate, UserNameForCertificate a IssuedTokenForCertificate.  
  
#### <a name="321-mutualcertificate-wss10"></a>3.2.1 MutualCertificate WSS 1.0  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token iniciátoru. Služba je také ověřena pomocí certifikátu X. 509. Hlavičky SOAP i tělo protokolu SOAP jsou podepsané. Vytvoří se symetrický klíč, který se zašifruje pomocí přenosového certifikátu pro příjemce.  
  
 Použitá vazba je asymetrická vazba s následujícími hodnotami vlastností:  
  
 Token iniciátoru: certifikát X. 509 klienta s režimem zahrnutí nastaveným na. ../IncludeToken/AlwaysToRecipient  
  
 Token příjemce: je nastavený certifikát X. 509 serveru s režimem zahrnutí. ../IncludeToken/Never  
  
 Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-39cb393e-9da8-4d5d-b273-540ef614569b-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"> <u:Timestamp u:Id="uuid-3d742930-70d3-4d7e-aa0a-8721128dc115-8"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_5" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-73da3e21-abff-4294-a910-e75303d280cc-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-02f276b6-804f-480d-99e9-2e90fc76ab27-3"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="322-mutualcertificateduplex"></a>3.2.2 MutualCertificateDuplex  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token iniciátoru. Služba je také ověřena pomocí certifikátu X. 509.  
  
 Použitá vazba je asymetrická vazba s následujícími hodnotami vlastností:  
  
 Token iniciátoru: certifikát x509 klienta, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToRecipient  
  
 Token příjemce: certifikát x509 serveru, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToInitiator.  
  
 Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost a odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4dec3da4-b572-4654-ba4d-4a2f84a87510-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost a odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b0e23feb-cd2d-4dc1-bad9-284bc45f3be3-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="323-using-symmetricbinding-with-x509-service-authentication"></a>3.2.3 použití SymmetricBinding s ověřováním služby X. 509  
 "WSS10" poskytl omezená podpora pro scénáře s tokeny x509. Například neexistuje způsob, jak poskytnout podpisovou a šifrovací ochranu pro zprávy pomocí tokenu x509 služby. "WSS11" zavedlo použití EncryptedKey jako symetrického tokenu. Nyní může být pro ochranu požadavků a odpovědí použit dočasný klíč zašifrovaný pro certifikát X. 509 služby. Tento model se používá v režimech ověřování popsaných v části 3,4.  
  
 WS-SecurityPolicy popisuje tento vzor pomocí SymmetricBinding s tokenem x509 Service jako tokenem ochrany.  
  
 Režimy ověřování AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 a IssuedTokenForCertificate všechny používají podobné instance SP: SymmetricBinding s následujícími hodnotami vlastností:  
  
 Token ochrany: certifikát x509 serveru, režim zahrnutí je nastaven na. ../IncludeToken/Never  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 Výše uvedené režimy ověřování se liší pouze podpůrnými tokeny, které používají. AnonymousForCertificate nemá žádné podpůrné tokeny, MutualCertificate WSS 1,1 má certifikát x509 klienta jako přihlášené tokeny, UserNameForCertificate má token uživatelského jména jako podepsaný podpůrný token a IssuedTokenForCertificate má vydaný token jako token podporující potvrzení.  
  
#### <a name="324-anonymousforcertificate"></a>3.2.4 AnonymousForCertificate  
 V tomto režimu ověřování je klient anonymní a služba se ověřuje pomocí certifikátu X. 509. Použitá vazba je instancí symetrických vazeb, jak je popsáno v 3.4.2.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b06cb481-3176-4c56-af35-c38252bb6c78-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-15b48260-23da-424d-8dc4-8f4e150fb8cf-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="ALF+QNGmWn2k3LpWEDIzSBgTkvo=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="325-usernameforcertificate"></a>3.2.5 UserNameForCertificate  
 V tomto režimu ověřování klient ověřuje službu pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token. Služba se ověřuje pro klienta pomocí certifikátu X. 509. Použitá vazba je symetrická vazba s tokenem ochrany, který je klíčem generovaným klientem, zašifrovaný pomocí veřejného klíče služby.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-681226f7-126a-4806-b732-fcca097cd7a8-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8a7ad353-f071-49dc-90dd-5ad2e9abd40a-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="326-mutualcertificate-wss-11"></a>3.2.6 MutualCertificate (WSS 1,1)  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token podporující potvrzení. Služba je také ověřena pomocí certifikátu X. 509. Použitá vazba je symetrická vazba s tokenem ochrany, který je klíčem generovaným klientem, zašifrovaný pomocí veřejného klíče služby.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><o:BinarySecurityToken> ...</o:BinarySecurityToken><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8c73fa91-f95b-40ff-b088-48118e6fadcf-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_3" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature Id="_2" xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67dacc31-4a50-4866-b673-ccc03e156337-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="mYyksUQKkK27Fd6hmgOiqFwvudk=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><k:SignatureConfirmation u:Id="_3" Value="SreOZ4Rr2BcXjFQFvgN55ERypI/1/86hdWThE5lav0eYIxF1OCzQgZF+y7cQ82t+g3CRnLbE3c52DqMpY/HXlrdMct3m3rnpDH+fqdhNY4fE+M2v4zUMFR7uxDKWcEm9zZpmUvJCDfJRfKRaKjy5cTbccRKqSxw7HAqOYnqibA4=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="327-issuedtokenforcertificate"></a>3.2.7 IssuedTokenForCertificate  
 V tomto režimu ověřování klient neověřuje službu, jako je, ale místo toho prezentuje token vydaný službou STS a prokáže znalosti sdíleného klíče. Vydaný token se zobrazí ve vrstvě SOAP jako token podporující potvrzení. Služba se ověřuje pro klienta pomocí certifikátu X. 509. Použitá vazba je symetrická vazba s tokenem ochrany, který je klíčem generovaným klientem, zašifrovaný pomocí veřejného klíče služby.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1d2c03e6-0b69-4483-903a-6ef9b9d286ed-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-de1c51aa-2ecc-4e70-b6bd-9dca58331fa7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
## <a name="33-kerberos"></a>protokol Kerberos 3,3  
 V tomto režimu ověřování klient ověřuje službu pomocí lístku Kerberos. Stejný lístek taky zajišťuje ověřování serveru. Použitá vazba je symetrická vazba s následujícími vlastnostmi;  
  
 Token ochrany: lístek protokolu Kerberos, režim zahrnutí je nastaven na. ../IncludeToken/Once  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e8f6dc3b-407d-4387-bd33-97aedfd8bf13-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7b03568e-66ae-49da-82ee-5d12d372876e-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d29247f0-f220-4e81-9a8d-a15f5ac31072-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9025b930-4f15-42fe-8e78-35d3a3480177-2"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="34-issuedtoken"></a>3,4 třídy IssuedToken  
 V tomto režimu ověřování klient neověřuje službu, takže klient prezentuje token vydaný službou STS a prokáže znalost sdíleného klíče. Služba není ověřena klientovi, jako by se místo toho služba STS zašifroval sdílený klíč jako součást vydaného tokenu, aby se klíč dešifroval jenom službou. Použitá vazba je jako symetrická vazba s následujícími vlastnostmi;  
  
 Token ochrany: vydaný token, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToRecipient  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-61ce3989-bc38-4d67-8262-6232c9d49a26-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1dc8bdef-4202-4e08-8a5e-ab94da579dec-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> </c:DerivedKeyToken> ... <c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="35-using-sslnegotiated-for-service-authentication"></a>3,5 použití SslNegotiated pro ověřování služby  
 Tato část popisuje skupinu režimů ověřování, které používají symetrickou vazbu s tokenem ochrany, který je tokenem kontextu zabezpečení na WS-SecureConversation (WS-SC), jehož hodnota klíče je vyjednáno, spuštěním protokolu TLS přes WS-Trust (WS-T) RST/RSTR Messages. Podrobnosti implementace TLS handshake pomocí WS-Trust jsou popsány v tématu TLSNEGO. V příkladech zprávy budeme předpokládat, že SCT s přidruženým kontextem zabezpečení je již vytvořen pomocí metody handshake.  
  
 Použitá vazba je symetrická vazba s následujícími vlastnostmi;  
  
 Token ochrany: SslContextToken, režim zahrnutí je nastaven na. ../IncludeToken/Never  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
#### <a name="351-policy-for-sslnegotiated-service-authentication"></a>zásada 3.5.1 pro ověřování služby SslNegotiated  
 Zásady pro všechny režimy ověřování v této části jsou podobné a liší se pouze konkrétními podepsanými podpůrnými nebo schválenými tokeny.  
  
#### <a name="352-anonymousforsslnegotiated"></a>3.5.2 AnonymousForSslNegotiated  
 V tomto režimu ověřování je klient anonymní a služba se ověřuje pomocí certifikátu X. 509. Použitá vazba je instance symetrického vazby, jak je popsáno v části 3.5.1 výše.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f4b86ce2-4ba6-4c55-bac1-2e920fc6d5db-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c84b24b9-39e0-4cc3-99e2-cec088f1b9eb-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="353-usernameforsslnegotiated"></a>3.5.3 UserNameForSslNegotiated  
 V tomto režimu ověřování se klient ověřuje pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token. Služba se ověřuje pomocí certifikátu X. 509. Použitá vazba je instancí symetrických vazeb, jak je popsáno v části 3.5.1.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3d1a12c3-e690-474a-a223-a346fc0329a9-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-56e931e8-20c2-457f-a83e-8fcd6b92c258-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="354-issuedtokenforsslnegotiated"></a>3.5.4 IssuedTokenForSslNegotiated  
 V tomto režimu ověřování klient neověřuje službu, jako by ale místo toho prezentuje token vydaný službou STS a prokáže znalosti sdíleného klíče. Vydaný token se zobrazí ve vrstvě SOAP jako token podporující potvrzení. Služba se ověřuje pomocí certifikátu X. 509. Použitá vazba je instance symetrického vazby, jak je popsáno v části 3.5.1 výše.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b19fb2e7-8f0c-45c1-b62c-45d6ff6d57e7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d75104d5-313e-440f-b112-db8aff57a5fe-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="355-mutualsslnegotiated"></a>3.5.5 MutualSslNegotiated  
 V tomto režimu ověřování se klient a služba ověřují pomocí certifikátů X. 509. Použitá vazba je instance symetrického vazby, jak je popsáno v části 3.5.1 výše.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d1e6037e-8a64-494f-9447-07d3125b81b5-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c2a6ab10-889a-4ee1-871d-05410c90fc10-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="36-sspinegotiated"></a>3,6 SspiNegotiated  
 V tomto režimu ověřování se k ověřování klienta a serveru používá protokol vyjednávání. Kerberos se používá, pokud je to možné, jinak NTLM. Použitá vazba je symetrická vazba s následujícími vlastnostmi;  
  
 Token ochrany: SpnegoContextToken, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToRecipient  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9a954fcb-4df2-4610-9800-f542f2b5130a-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f1673773-f9a7-4b43-b13b-405e7dd4a6e3-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="37-secureconversation"></a>3,7 SecureConversation  
 Použitá vazba je symetrická vazba s tokenem ochrany, která je SCT na WS-SecureConversation (WS-SC). SCT se vyjednávat pomocí WS-Trust (WS-Trust) nebo WS-SecureConversation (WS-SC) podle vnořené vazby, která je sám symetrickou vazbou, která používá protokol pro vyjednávání. Protokol vyjednávání bude používat protokol Kerberos k ověřování klienta a serveru, pokud je to možné. Pokud se protokol Kerberos nedá použít, přepne se na NTLM.  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f01c6159-f159-454d-bd97-bbcc9b8e25d3-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Zásada  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d57e6342-1c68-4095-a0c1-41979088a944-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Odpověď  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```
