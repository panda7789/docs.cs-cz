---
title: Protokoly zabezpečení verze 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: e22150d21638cffdf804008c32285f900bb1e263
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459040"
---
# <a name="security-protocols-version-10"></a>Protokoly zabezpečení verze 1.0
Protokoly specifikace Web Services Security poskytují mechanismy zabezpečení webových služeb, které pokrývají všechny stávající požadavky na zabezpečení podnikových zpráv. Tato část popisuje podrobnosti o Windows Communication Foundation (WCF) verze 1,0 (implementované v <xref:System.ServiceModel.Channels.SecurityBindingElement>) pro následující protokoly zabezpečení webových služeb.  
  
|Specifikace/dokument|Propojit|  
|-|-|  
|WSS: zabezpečení zpráv SOAP 1,0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|WSS: Profil tokenu uživatelského jména 1,0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: Profil tokenu x509 1,0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|WSS: Profil tokenu SAML 1,1 1,0|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|WSS: zabezpečení zpráv SOAP 1,1|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|Token uživatelského jména WSS – profil 1,1|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: X. 509 – profil tokenu 1,1|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|WSS: Profil tokenu protokolu Kerberos 1,1|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|WSS: Profil tokenu SAML 1,1 1,1|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|Konverzace WS-Secure|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|WS-Trust|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|Poznámka k aplikaci:<br /><br /> Použití WS-Trust pro handshake TLS|K publikování|  
|Poznámka k aplikaci:<br /><br /> Používání WS-Trust pro SPNEGO|K publikování|  
|Poznámka k aplikaci:<br /><br /> Odkazy a identita koncových bodů adresování webových služeb|K publikování|  
|WS-SecurityPolicy 1,1<br /><br /> (2005/07)|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> Jak bylo upraveno službou [Seznam chyb](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) odeslané technickému výboru Oasis ws-sx |  
  
 Služba WCF verze 1 poskytuje 17 režimů ověřování, které lze použít jako základ pro konfiguraci zabezpečení webových služeb. Jednotlivé režimy jsou optimalizované pro společnou sadu požadavků na nasazení, jako například:  
  
- Pověření používaná k ověřování klienta a služby.  
  
- Mechanismy ochrany zabezpečení zpráv nebo přenosů.  
  
- Vzory výměny zpráv.  
  
|Režim ověřování|Ověřování klienta|Ověřování serveru|Režim|  
|-------------------------|---------------------------|---------------------------|----------|  
|UserNameOverTransport|Uživatelské jméno a heslo|X509|Přepravu|  
|CertificateOverTransport|X509|X509|Přepravu|  
|KerberosOverTransport|Windows|X509|Přepravu|  
|IssuedTokenOverTransport|Federované|X509|Přepravu|  
|SspiNegotiatedOverTransport|Vyjednávání SSPI systému Windows|Vyjednávání SSPI systému Windows|Přepravu|  
|AnonymousForCertificate|Žádné|X509|Zpráva|  
|UserNameForCertificate|Uživatelské jméno a heslo|X509|Zpráva|  
|MutualCertificate|X509|X509|Zpráva|  
|MutualCertificateDuplex|X509|X509|Zpráva|  
|IssuedTokenForCertificate|Federované|X509|Zpráva|  
|Sdílené|Windows|Windows|Zpráva|  
|Třídy IssuedToken|Federované|Federované|Zpráva|  
|SspiNegotiated|Vyjednávání SSPI systému Windows|Vyjednávání SSPI systému Windows|Zpráva|  
|AnonymousForSslNegotiated|Žádné|X509, TLS-NEGO|Zpráva|  
|UserNameForSslNegotiated|Uživatelské jméno a heslo|X509, TLS-NEGO|Zpráva|  
|MutualSslNegotiated|X509|X509, TLS-NEGO|Zpráva|  
|IssuedTokenForSslNegotiated|Federované|X509, TLS-NEGO|Zpráva|  
  
 Koncové body využívající takové režimy ověřování mohou vyjádřit požadavky na zabezpečení pomocí WS-SecurityPolicy (WS-SP). Tento dokument popisuje strukturu záhlaví zabezpečení a zpráv infrastruktury pro každý režim ověřování a poskytuje příklady zásad a zpráv.  
  
 WCF využívá WS-SecureConversation k poskytování zabezpečených relací, které umožňují chránit výměny více zpráv mezi aplikacemi.  Podrobnosti o implementaci najdete níže v části "zabezpečené relace".  
  
 Kromě režimů ověřování nabízí WCF nastavení pro řízení běžných mechanismů ochrany, které se vztahují na většinu režimů ověřování založených na zabezpečení zpráv, například: pořadí podpisů a operací šifrování, sady algoritmů, odvození klíče. a potvrzení podpisu.  
  
 V tomto dokumentu se používají následující předpony a obory názvů.  
  
|směr|Obor názvů|  
|------------|---------------|  
|s|<http://www.w3.org/2003/05/soap-envelope/>|
|SP|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|Určitého|<http://www.w3.org/2005/08/addressing>|  
|wsse|TBD – OASIS WSS 1,0 URI|  
|wsse11|TBD – OASIS WSS 1,1 URI|  
|wsu|TBD – identifikátor URI nástroje OASIS WSS 1,0|  
|služby|TBD – XMLDSig URI W3C|  
|WST|TBD – WS-Trust 2005/02 URI|  
|wssc|TBD – WS-SecureConversation 2005/02 URI|  
|wsaw|TBD – obor názvů zásad WS-Addressing|  
|WSP|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|mssp|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
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
  
 R1202 Pokud je v certifikátu x509 k dispozici rozšíření SubjectKeyIdentifier (SKI), wsse: identifikátor klíče by měl být použit pro externí odkazy na token, s atributem ValueType jako #X509SubjectKeyIdentifier a jeho obsahem jako hodnota v kódování Base64 rozšíření LYŽAŘSKÉho certifikátu.  
  
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
 Přítomnost časového razítka je řízena pomocí vlastnosti <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> třídy <xref:System.ServiceModel.Channels.SecurityBindingElement>. WCF vždycky serializace wsse: TimeStamp pomocí polí wsse: created a wsse: Expires. Wsse: časové razítko je vždy podepsáno při použití podepisování.  
  
### <a name="22-protection-order"></a>2,2. pořadí ochrany  
 WCF podporuje pořadí zpráv před zašifrováním a před podepsáním (zásady zabezpečení 1,1). Doporučení "před šifrováním" se doporučují z důvodů, mezi které patří: zprávy chráněné šifrováním před tím, než se přihlásí k zástupným útokům, pokud se nepoužije mechanismus WS-Security 1,1 SignatureConfirmation a signatura přešifrovaného obsahu vytvoří auditování je obtížnější.  
  
### <a name="23-signature-protection"></a>2,3 signatura ochrany  
 Při šifrování před použitím podpisu se doporučuje chránit signaturu, aby nedocházelo k útokům hrubou silou za účelem odhadování šifrovaného obsahu nebo podpisového klíče (zejména pokud se vlastní token používá se slabým materiálem klíče).  
  
### <a name="24-algorithm-suite"></a>Sada algoritmů 2,4  
 WCF podporuje všechny sady algoritmů uvedené v zásadách zabezpečení 1,1.  
  
### <a name="25-key-derivation"></a>2,5 odvození klíče  
 WCF používá odvození klíče pro symetrické klíče, jak je popsáno v tématu WS-SecureConversation.  
  
### <a name="26-signature-confirmation"></a>2,6 potvrzení podpisu  
 Potvrzení podpisu může být ochrany proti útokům ze střední osoby na ochranu sady podpisů.  
  
### <a name="27-security-header-layout"></a>2,7 rozvržení záhlaví zabezpečení  
 Každý režim ověřování popisuje určité rozložení pro záhlaví zabezpečení. Prvky v záhlaví zabezpečení jsou částečně seřazené. Pro definování pořadí podřízených prvků záhlaví zabezpečení definuje zásada WS-Security následující režimy rozvržení záhlaví zabezpečení:  
  
|||  
|-|-|  
|Zásadní|Položky jsou přidány do záhlaví zabezpečení podle pravidel číslovaného rozložení, které jsou popsány v části zásady zabezpečení 7.7.1, podle obecné zásady deklarace před použitím.|  
|LAX|Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, které odpovídá WSS: zabezpečení zpráv SOAP.|  
|LaxTimestampFirst|Stejné jako LAX s tím rozdílem, že první položka v záhlaví zabezpečení musí být wsse: Timestamp|  
|LaxTimestampLast|Stejné jako LAX s tím rozdílem, že poslední položka v záhlaví zabezpečení musí být wsse: Timestamp|  
  
 WCF podporuje všechny čtyři režimy pro rozložení záhlaví zabezpečení. Struktura záhlaví zabezpečení a příklady zpráv pro režimy ověřování níže následují po "striktním" režimu.  
  
## <a name="2-common-message-security-parameters"></a>2. běžné parametry zabezpečení zpráv  
 V této části najdete příklady zásad pro jednotlivé režimy ověřování spolu s příklady zobrazení struktury záhlaví zabezpečení ve zprávách vyměňovaných klientem a službou.  
  
### <a name="61-transport-protection"></a>6,1 Transport Protection  
 WCF nabízí pět režimů ověřování, které používají k ochraně zpráv zabezpečený přenos. UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport a SspiNegotiatedOverTransport.  
  
 Tyto režimy ověřování jsou vytvořeny pomocí přenosové vazby popsané v části SecurityPolicy. Pro režim ověřování UserNameOverTransport je UsernameToken podepsaný podpůrný token. Pro jiné režimy ověřování se token zobrazí jako podepsaný token. Příloha C. 1.2 a C. 1.3 programu SecurityPolicy popisují podrobné rozložení záhlaví zabezpečení. Následující příklady hlaviček zabezpečení znázorňují striktní rozložení pro daný režim ověřování.  
  
 Hodnota vlastnosti "odvozené klíče" pro tokeny ve všech případech je "false".  
  
 Hodnoty různých vlastností transportní vazby jsou následující:  
  
 Časové razítko: true  
  
 Rozložení záhlaví zabezpečení: striktní  
  
 Sada algoritmů: Basic256  
  
#### <a name="611-usernameovertransport"></a>6.1.1 UsernameOverTransport  
 V tomto režimu ověřování se klient ověřuje pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token, který se vždy odesílá z iniciátoru příjemci. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Použitá vazba je přenosová vazba.  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />   
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Rozložení záhlaví zabezpečení  
  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a>6.1.2 CertificateOverTransport  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako připravující token, který se vždycky odesílá z iniciátoru příjemci. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Použitá vazba je přenosová vazba.  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />   
              <sp:WssX509V3Token10 />   
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Rozložení záhlaví zabezpečení  
  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a>6.1.3 IssuedTokenOverTransport  
 V tomto režimu ověřování klient neověřuje službu, například, ale prezentuje token vydaný službou tokenu zabezpečení (STS) a prokáže znalosti sdíleného klíče. Vydaný token se zobrazí ve vrstvě SOAP jako průkazní token, který je vždycky odesílán od iniciátoru příjemci. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Vazba je přenosová vazba.  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>   
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />   
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Rozložení záhlaví zabezpečení  
  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a>6.1.4 KerberosOverTransport  
 V tomto režimu ověřování klient ověřuje službu pomocí lístku Kerberos. Token protokolu Kerberos se zobrazí ve vrstvě SOAP jako token podporující potvrzení. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Vazba je přenosová vazba.  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />   
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Rozložení záhlaví zabezpečení  
  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a>6.1.5 SspiNegotiatedOverTransport  
 V tomto režimu se k ověřování klienta a serveru používá protokol vyjednávání. Kerberos se používá, pokud je to možné, jinak NTLM. Výsledný SCT se zobrazí ve vrstvě SOAP jako průkazní token, který je vždy odeslán od iniciátoru příjemci. Služba se navíc ověřuje na transportní vrstvě pomocí certifikátu X. 509. Použitá vazba je přenosová vazba. "SPNEGO" (vyjednávání) popisuje, jak WCF používá protokol binárního vyjednávání SSPI s WS-Trust. Příklady hlaviček zabezpečení v této části jsou po navázání SCT prostřednictvím metody handshake SPNEGO.  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />   
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a>Příklady záhlaví zabezpečení  
 Jakmile je token kontextu zabezpečení vytvořen pomocí SPNEGO handshake pomocí binárního vyjednávání WS-Trust, budou zprávy aplikace obsahovat záhlaví zabezpečení s následující strukturou.  
  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a>6,2 použití certifikátů X. 509 pro ověřování služby  
 Tato část popisuje následující režimy ověřování: MutualCertificate WSS 1.0, vzájemné CertificateDuplex, MutualCertificate WSS 1.1, AnonymousForCertificate, UserNameForCertificate a IssuedTokenForCertificate.  
  
#### <a name="621-mutualcertificate-wss10"></a>6.2.1 MutualCertificate WSS 1.0  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token iniciátoru. Služba je také ověřena pomocí certifikátu X. 509.  
  
 Použitá vazba je asymetrická vazba s následujícími hodnotami vlastností:  
  
 Token iniciátoru: certifikát X. 509 klienta s režimem zahrnutí nastaveným na. ../IncludeToken/AlwaysToRecipient  
  
 Token příjemce: je nastavený certifikát X. 509 serveru s režimem zahrnutí. ../IncludeToken/Never  
  
 Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Příklady záhlaví zabezpečení: EncryptBeforeSign  
  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a>MutualCertificateDuplex 6.2.2  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token iniciátoru. Služba je také ověřena pomocí certifikátu X. 509.  
  
 Použitá vazba je asymetrická vazba s následujícími hodnotami vlastností:  
  
 Token iniciátoru: certifikát x509 klienta, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToRecipient  
  
 Token příjemce: certifikát x509 serveru, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToInitiator.  
  
 Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Žádost a odpověď  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Žádost a odpověď  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a>6.2.3 s použitím SymmetricBinding s ověřováním služby X. 509  
 "WSS10" poskytl omezená podpora pro scénáře s tokeny x509. Například neexistuje způsob, jak poskytnout podpisovou a šifrovací ochranu pro zprávy pomocí tokenu x509 služby. "WSS11" zavedlo použití EncryptedKey jako symetrického tokenu. Nyní může být pro ochranu požadavků a odpovědí použit dočasný klíč zašifrovaný pro certifikát X. 509 služby. Tento model se používá v režimech ověřování popsaných v části 6,4.  
  
 WS-SecurityPolicy popisuje tento vzor pomocí SymmetricBinding s tokenem x509 Service jako tokenem ochrany.  
  
 Režimy ověřování AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 a IssuedTokenForCertificate všechny používají podobné instance SP: SymmetricBinding s následujícími hodnotami vlastností:  
  
 Token ochrany: certifikát x509 serveru, režim zahrnutí je nastaven na. ../IncludeToken/Never  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 Výše uvedené režimy ověřování se liší pouze podpůrnými tokeny, které používají. AnonymousForCertificate nemá žádné podpůrné tokeny, MutualCertificate WSS 1,1 má certifikát x509 klienta jako přihlášené tokeny pro podporu, UserNameForCertificate má token UserName jako podepsaný podpůrný token a IssuedTokenForCertificate má vydaný token jako token podporující potvrzení.  
  
 politických  
  
 Symetrická vazba  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireThumbprintReference />   
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
          <sp:RequireSignatureConfirmation />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a>6.2.4 AnonymousForCertificate  
 V tomto režimu ověřování je klient anonymní a služba se ověřuje pomocí certifikátu X. 509. Použitá vazba je instancí symetrických vazeb, jak je popsáno v 6.4.2.  
  
 politických  
  
 Podrobnosti o vazbě najdete v části "zásady" v 6.2.3 výše.  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a>6.2.5 UserNameForCertificate  
 V tomto režimu ověřování klient ověřuje službu pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token. Služba se ověřuje pro klienta pomocí certifikátu X. 509. Použitá vazba je symetrická vazba s tokenem ochrany, který je klíčem generovaným klientem, zašifrovaný pomocí veřejného klíče služby.  
  
 politických  
  
 Podrobnosti o vazbě najdete v části "zásady" v 6.2.3 výše.  
  
 Podepsaný podpůrný token  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a>6.2.6 MutualCertificate (WSS 1,1)  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token podporující potvrzení. Služba je také ověřena pomocí certifikátu X. 509. Použitá vazba je symetrická vazba s tokenem ochrany, který je klíčem generovaným klientem, zašifrovaný pomocí veřejného klíče služby.  
  
 politických  
  
 Podrobnosti o vazbě najdete v tématu věnovaném zásadám 6.2.3.  
  
 Schvaluje se podpůrný token.  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a>6.2.7 IssuedTokenForCertificate  
 V tomto režimu ověřování klient neověřuje službu, jako je, ale místo toho prezentuje token vydaný službou STS a prokáže znalosti sdíleného klíče. Vydaný token se zobrazí ve vrstvě SOAP jako token podporující potvrzení. Služba se ověřuje pro klienta pomocí certifikátu X. 509. Použitá vazba je symetrická vazba s tokenem ochrany, který je klíčem generovaným klientem, zašifrovaný pomocí veřejného klíče služby.  
  
 politických  
  
 Podrobnosti o vazbě najdete v tématu zásady v 6.2.3 výše.  
  
 Schvaluje se podpůrný token.  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />   
       <sp:RequireInternalReference />   
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a>protokol Kerberos 6,3  
 V tomto režimu ověřování klient ověřuje službu pomocí lístku Kerberos. Stejný lístek taky zajišťuje ověřování serveru. Použitá vazba je symetrická vazba s následujícími vlastnostmi;  
  
 Token ochrany: lístek protokolu Kerberos, režim zahrnutí je nastaven na. ../IncludeToken/Once  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:WssGssKerberosV5ApReqToken11 />   
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a>6,4 třídy IssuedToken  
 V tomto režimu ověřování klient neověřuje službu, takže klient prezentuje token vydaný službou STS a prokáže znalost sdíleného klíče. Služba není ověřena klientovi, jako by se místo toho služba STS zašifroval sdílený klíč jako součást vydaného tokenu, aby se klíč dešifroval jenom službou. Použitá vazba je jako symetrická vazba s následujícími vlastnostmi;  
  
 Token ochrany: vydaný token, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToRecipient  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>   
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireInternalReference />   
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a>6,5 použití SslNegotiated pro ověřování služby  
 Tato část popisuje skupinu režimů ověřování, které používají symetrickou vazbu s tokenem ochrany, který je tokenem kontextu zabezpečení na WS-SecureConversation (WS-SC), jehož hodnota klíče je vyjednáno spuštěním protokolu TLS prostřednictvím WS-Trust (WS-T) RST/ RSTR zprávy. Podrobnosti implementace TLS handshake pomocí WS-Trust jsou popsány v tématu TLSNEGO. V příkladech zprávy budeme předpokládat, že SCT s přidruženým kontextem zabezpečení je již vytvořen pomocí metody handshake.  
  
 Použitá vazba je symetrická vazba s následujícími vlastnostmi;  
  
 Token ochrany: SslContextToken, režim zahrnutí je nastaven na. ../IncludeToken/Never  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a>zásady 6.5.1 pro ověřování služby SslNegotiated  
 Zásady pro všechny režimy ověřování v této části jsou podobné a liší se pouze konkrétními podepsanými podpůrnými nebo schválenými tokeny.  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>   
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a>6.5.2 AnonymousForSslNegotiated  
 V tomto režimu ověřování je klient anonymní a služba se ověřuje pomocí certifikátu X. 509. Použitá vazba je instance symetrického vazby, jak je popsáno v 6.5.1 výše.  
  
 politických  
  
 Podrobnosti o vazbách najdete v tématu zásady v 6.5.1 výše.  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a>6.5.3 UserNameForSslNegotiated  
 V tomto režimu ověřování se klient ověřuje pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token. Služba se ověřuje pomocí certifikátu X. 509. Použitá vazba je instancí symetrických vazeb, jak je popsáno v 6.5.1.  
  
 politických  
  
 Podrobnosti o vazbě najdete v části 6.5.1 výše.  
  
 Podepsaný podpůrný token  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a>6.5.4 IssuedTokenForSslNegotiated  
 V tomto režimu ověřování klient neověřuje službu, jako by ale místo toho prezentuje token vydaný službou STS a prokáže znalosti sdíleného klíče. Vydaný token se zobrazí ve vrstvě SOAP jako token podporující potvrzení. Služba se ověřuje pomocí certifikátu X. 509. Použitá vazba je instance symetrického vazby, jak je popsáno v 6.5.1 výše.  
  
 politických  
  
 Podrobnosti o vazbě najdete v části 6.5.1 výše.  
  
 Schvaluje se podpůrný token.  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>   
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />   
        <sp:RequireInternalReference />   
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a>6.5.5 MutualSslNegotiated  
 V tomto režimu ověřování se klient a služba ověřují pomocí certifikátů X. 509. Použitá vazba je instance symetrického vazby, jak je popsáno v 6.5.1 výše.  
  
 politických  
  
 Podrobnosti o vazbě najdete v části 6.5.1 výše.  
  
 Schvaluje se podpůrný token.  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a>6,6 SspiNegotiated  
 V tomto režimu ověřování se k ověřování klienta a serveru používá protokol vyjednávání. Kerberos se používá, pokud je to možné, jinak NTLM. Použitá vazba je symetrická vazba s následujícími vlastnostmi;  
  
 Token ochrany: SpnegoContextToken, režim zahrnutí je nastaven na. ../IncludeToken/AlwaysToRecipient  
Ochrana tokenů: false  
  
 Celé záhlaví a podpisy textu: pravda  
  
 Pořadí ochrany: SignBeforeEncrypt  
  
 Šifrovat podpis: true  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a>6,7 SecureConversation  
 Použitá vazba je symetrická vazba s tokenem ochrany, která je SCT na WS-SecureConversation (WS-SC). SCT se vyjednávat pomocí WS-Trust (WS-Trust) nebo WS-SecureConversation (WS-SC) podle vnořené vazby, která je sám symetrickou vazbou, která používá protokol pro vyjednávání. Protokol vyjednávání bude používat protokol Kerberos k ověřování klienta a serveru, pokud je to možné. Pokud se protokol Kerberos nedá použít, přepne se na NTLM.  
  
 politických  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />   
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />   
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />   
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />   
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />   
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />   
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />   
                          <sp:EncryptSignature />   
                          <sp:OnlySignEntireHeadersAndBody />   
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />   
                          <sp:MustSupportRefIssuerSerial />   
                          <sp:MustSupportRefThumbprint />   
                          <sp:MustSupportRefEncryptedKey />   
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />   
                          <sp:RequireClientEntropy />   
                          <sp:RequireServerEntropy />   
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Příklady záhlaví zabezpečení: SignBeforeEncrypt, EncryptSignature  
 Request  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Příklady záhlaví zabezpečení: EncryptBeforeSign  
 Request  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Základě  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
