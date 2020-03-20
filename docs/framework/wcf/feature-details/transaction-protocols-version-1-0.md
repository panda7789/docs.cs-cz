---
title: Protokoly transakce verze 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a19329b56bb569a04195b38877a42d635996ff1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184378"
---
# <a name="transaction-protocols-version-10"></a>Protokoly transakce verze 1.0
Windows Communication Foundation (WCF) verze 1 implementuje verzi 1.0 ws-atomic k transakcím a ws-koordinace protokolů. Další informace o verzi 1.1 naleznete [v tématu Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Specifikace/dokument|Odkaz|  
|-----------------------------|----------|  
|WS-Koordinace|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|WS AtomicTransaction|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 Interoperabilita těchto specifikací protokolu je vyžadována na dvou úrovních: mezi aplikacemi a mezi správci transakcí (viz následující obrázek). Specifikace podrobně popisují formáty zpráv a výměnu zpráv pro obě úrovně interoperability. Některé zabezpečení, spolehlivost a kódování pro výměnu mezi aplikacemi platí stejně jako pro pravidelnou výměnu aplikací. Úspěšná interoperabilita mezi správci transakcí však vyžaduje dohodu o konkrétní vazbě, protože ji uživatel obvykle nenakonfiguruje.  
  
 Toto téma popisuje složení specifikace WS-Atomic Transaction (WS-AT) se zabezpečením a popisuje zabezpečenou vazbu používanou pro komunikaci mezi správci transakcí. Přístup popsaný v tomto dokumentu byl úspěšně testován s dalšími implementacemi WS-AT a WS-Coordination, včetně IBM, IONA, Sun Microsystems a dalších.  
  
 Následující obrázek znázorňuje interoperabilitu mezi dvěma správci transakcí, Správcetransakcí 1 a Správce transakcí 2 a dvě aplikace, Aplikace 1 a Aplikace 2:  
  
 ![Snímek obrazovky, který zobrazuje interakci mezi správci transakcí.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 Zvažte typický scénář WS-Coordination/WS-Atomic Transaction s jedním iniciátorem (I) a jedním účastníkem (P). Iniciátor i účastník mají správce transakcí (ITM a PTM). Dvoufázové potvrzení se v tomto tématu označuje jako 2PC.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Odpověď na zprávu aplikace|  
|2. CreateCoordinationContextResponse|13. Potvrzení (dokončení)|  
|3. Registr (dokončení)|14. Příprava (2PC)|  
|4. RegisterResponse|15. Příprava (2PC)|  
|5. Zpráva aplikace|16. Připraveno (2PC)|  
|6. CreateCoordinationContext s kontextem|17. Připraveno (2PC)|  
|7. Registrovat (trvanlivé)|18. Potvrzené (dokončení)|  
|8. RegisterResponse|19. Potvrzení (2PC)|  
|9. CreateCoordinationContextResponse|20. Potvrzení (2PC)|  
|10. Registrovat (trvanlivé)|21.|  
|11. RegisterResponse|22.|  
  
 Tento dokument popisuje složení specifikace WS-AtomicTransaction se zabezpečením a popisuje zabezpečenou vazbu používanou pro komunikaci mezi správci transakcí. Přístup popsaný v tomto dokumentu byl úspěšně testován s dalšími implementacemi WS-AT a WS-Coordination.  
  
 Obrázek a tabulka znázorňují čtyři třídy zpráv z hlediska zabezpečení:  
  
- Aktivační zprávy (CreateCoordinationContext a CreateCoordinationContextResponse).  
  
- Registrační zprávy (Register and RegisterResponse)  
  
- Zprávy protokolu (Příprava, Vrácení zpět, Potvrzení, Přerušeno a tak dále).  
  
- Zprávy aplikace.  
  
 První tři třídy zpráv jsou považovány za zprávy Správce transakcí a jejich konfigurace vazby je popsána v části "Výměna zpráv aplikace" dále v tomto tématu. Čtvrtá třída zprávy je aplikace pro zprávy aplikace a je popsána v části "Příklady zpráv" dále v tomto tématu. Tato část popisuje vazby protokolu používané pro každou z těchto tříd WCF.  
  
 V celém dokumentu se používají následující obory názvů XML a přidružené předpony.  
  
|Předpona|Identifikátor URI oboru názvů|  
|------------|-------------------|  
|S11|http://schemas.xmlsoap.org/soap/envelope|  
|wsa|http://www.w3.org/2004/08/addressing|  
|wscoor řekl:|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|wsat|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|t|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|o|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|Xsd|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a>Vazby správce transakcí  
 R1001: Správci transakcí musí používat SOAP 1.1 a WS-Addressing 2004/08 pro ws-atomické transakce a WS koordinace zprávy výměny.  
  
 Zprávy aplikace nejsou omezeny na tyto vazby a jsou popsány později.  
  
### <a name="transaction-manager-https-binding"></a>Vazba HTTPS správce transakcí  
 Vazba HTTPS správce transakcí závisí výhradně na zabezpečení přenosu k dosažení zabezpečení a vytvoření vztahu důvěryhodnosti mezi jednotlivými dvojicemi odesílatele a příjemce ve stromu transakcí.  
  
#### <a name="https-transport-configuration"></a>Konfigurace přenosu HTTPS  
 Certifikáty X.509 se používají k vytvoření identity správce transakcí. Je vyžadováno ověření klient/server a autorizace klienta/serveru je ponechána jako podrobnost implementace:  
  
- R1111: Certifikáty X.509 prezentované po drátě musí mít název subjektu, který odpovídá plně kvalifikovanému názvu domény (Plně kvalifikovaný název domény) původního počítače.  
  
- B1112: Dns musí být funkční mezi každou dvojici odesílatele a příjemce v systému pro X.509 kontroly názvů předmětů úspěšné.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Konfigurace aktivační a registrační vazby  
 WCF vyžaduje oboustrannou vazbu požadavku a odpovědi s korelací přes protokol HTTPS. (Další informace o korelaci a popisy vzorců výměny zpráv požadavku a odpovědi naleznete v tématu WS-Atomic Transaction, oddíl 8.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfigurace vazby protokolu 2PC  
 WCF podporuje jednosměrné (datagram) zprávy přes HTTPS. Korelace mezi zprávami je ponechána jako podrobnosti implementace.  
  
 B2131: Implementace musí `wsa:ReferenceParameters` podporovat, jak je popsáno v WS-Adresování k dosažení korelace wcf 2PC zprávy.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Vazba smíšeného zabezpečení správce transakcí  
 Toto je alternativní (smíšený režim) vazby, která používá zabezpečení přenosu v kombinaci s WS koordinace vydaný token model pro účely vytváření identit.  Aktivace a registrace jsou pouze prvky, které se liší mezi dvě vazby.  
  
#### <a name="https-transport-configuration"></a>Konfigurace přenosu HTTPS  
 Certifikáty X.509 se používají k vytvoření identity správce transakcí. Je vyžadováno ověření klient/server a autorizace klienta/serveru je ponechána jako detail implementace.  
  
#### <a name="activation-message-binding-configuration"></a>Konfigurace vazby aktivační zprávy  
 Aktivační zprávy se obvykle neúčastní interoperability, protože se obvykle vyskytují mezi aplikací a jejím místním správcem transakcí.  
  
 B1221: WCF používá duplexní vazbu HTTPS (popsanou v [protokolech zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) pro aktivační zprávy. Zprávy požadavku a odpovědi jsou korelovány pomocí WS-Addressing 2004/08.  
  
 WS-Atomic Transaction specifikace, oddíl 8, popisuje další podrobnosti o korelaci a vzory výměny zpráv.  
  
- R1222: Po `CreateCoordinationContext`obdržení a musí `SecurityContextToken` koordinátor vydat `STx`a s přidruženým tajným tajemstvím . Tento token je `t:IssuedTokens` vrácena uvnitř záhlaví podle ws-trust specifikace.  
  
- R1223: Pokud dojde k aktivaci v `t:IssuedTokens` rámci `SecurityContextToken` existující kontextu koordinace, `CreateCoordinationContext` záhlaví s přidružené k existující context musí tok na zprávu.  
  
 Pro `t:IssuedTokens` připojení k odchozí `wscoor:CreateCoordinationContextResponse` zprávě by měla být generována nová hlavička.  
  
#### <a name="registration-message-binding-configuration"></a>Konfigurace vazby registrační zprávy  
 B1231: WCF používá duplexní vazbu HTTPS (popsanou v [protokolech zasílání zpráv).](../../../../docs/framework/wcf/feature-details/messaging-protocols.md) Zprávy požadavku a odpovědi jsou korelovány pomocí WS-Addressing 2004/08.  
  
 WS-AtomicTransaction, Oddíl 8, popisuje další podrobnosti o korelaci a popisy vzorů výměny zpráv.  
  
 R1232: Odchozí `wscoor:Register` zprávy musí `IssuedTokenOverTransport` používat režim ověřování popsaný v [protokolech zabezpečení](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 Prvek `wsse:Timestamp` musí být podepsán `SecurityContextToken STx` pomocí vydané. Tento podpis je dokladem o vlastnictví tokenu přidruženého k určité transakci a používá se k ověření účastníka zařazení do transakce. Zpráva Response RegistrationResponse je odeslána zpět přes protokol HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfigurace vazby protokolu 2PC  
 WCF podporuje jednosměrné (datagram) zprávy přes HTTPS. Korelace mezi zprávami je ponechána jako podrobnosti implementace.  
  
 B2131: Implementace musí `wsa:ReferenceParameters` podporovat, jak je popsáno v WS-Adresování k dosažení korelace wcf 2PC zprávy.  
  
## <a name="application-message-exchange"></a>Výměna zpráv aplikace  
 Aplikace mohou používat určitou vazbu pro zprávy aplikace k aplikaci, pokud vazba splňuje následující požadavky na zabezpečení:  
  
- R2001: Zprávy aplikace k aplikaci `t:IssuedTokens` musí tok záhlaví spolu s `CoordinationContext` v záhlaví zprávy.  
  
- R2002: Musí být zajištěna `t:IssuedToken` integrita a důvěrnost.  
  
 Záhlaví `CoordinationContext` obsahuje `wscoor:Identifier`. Zatímco definice `xsd:AnyURI` umožňuje použití absolutních i relativních identifikátorů `wscoor:Identifiers`URI, WCF podporuje pouze , což jsou absolutní identifikátory URI.  
  
 Pokud `wscoor:Identifier` `wscoor:CoordinationContext` je relativní identifikátor URI, budou vráceny chyby z transakčních služeb WCF.  
  
## <a name="message-examples"></a>Příklady zpráv  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Zprávy požadavků/odpovědí CreateCoordinationContext  
 Následující zprávy postupujte podle vzoru požadavku a odpovědi.  
  
#### <a name="createcoordinationcontext"></a>VytvořitcoordinationContext  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a>Vytvořitodpověď kontextukoordinace  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a>Registrační zprávy  
 Následující zprávy jsou registrační zprávy.  
  
#### <a name="register"></a>Zaregistrovat  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a>Zaregistrovat odpověď  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a>Dvě zprávy protokolu fázového potvrzení  
 Následující zpráva se týká protokolu dvoufázového potvrzení (2PC).  
  
#### <a name="commit"></a>Potvrzení  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a>Zprávy aplikace  
 Následující zprávy jsou zprávy aplikace.  
  
#### <a name="application-message-request"></a>Žádost o zprávu aplikace  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken
          wssu:Id="IA_Certificate"
          ValueType="...#X509v3"
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->
    <e:EncryptedData Id="encrypted_body"
           Type="http://www.w3.org/2001/04/xmlenc#Content"
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
