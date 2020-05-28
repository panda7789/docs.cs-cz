---
title: Protokoly transakce verze 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: 6063c643be4c60e9830a020d10ac9fbcd236dac2
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144770"
---
# <a name="transaction-protocols-version-10"></a>Protokoly transakce verze 1.0
Windows Communication Foundation (WCF) verze 1 implementuje rozhraní WS-Atomic Transaction a WS-koordinační protokol verze 1,0. Další informace o verzi 1,1 najdete v tématu [transakční protokoly](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Specifikace/dokument|Odkaz|  
|-----------------------------|----------|  
|WS-koordinace|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|WS-AtomicTransaction|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 Interoperabilita těchto specifikací protokolu je povinná na dvou úrovních: mezi aplikacemi a mezi správci transakcí (viz následující obrázek). Specifikace popisují Skvělé údaje o formátech zpráv a výměně zpráv pro obě úrovně interoperability. Určité zabezpečení, spolehlivost a kódování pro Exchange mezi aplikacemi platí jako při běžném výměně aplikací. Úspěšná interoperabilita mezi správci transakcí ale vyžaduje souhlas s konkrétní vazbou, protože obvykle není nakonfigurovaná uživatelem.  
  
 Toto téma popisuje složení specifikace WS-Atomic Transaction (WS-AT) se zabezpečením a popisuje zabezpečenou vazbu použitou pro komunikaci mezi správci transakcí. Přístup popsaný v tomto dokumentu byl úspěšně testován s ostatními implementacemi WS-AT a WS-koordinace, včetně IBM, IONA, Sun Microsystems a dalších.  
  
 Následující obrázek znázorňuje interoperabilitu mezi dvěma správci transakcí, správce transakcí 1 a správce transakcí 2 a dvěma aplikacemi, aplikací 1 a aplikací 2:  
  
 ![Snímek obrazovky zobrazující interakci mezi správci transakcí.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 Zvažte Typický scénář transakce WS-koordinační/WS-Atomic s jedním iniciátorem (I) a jedním účastníkem (P). Iniciátor i účastník mají správce transakcí (v uvedeném pořadí) (ITM a PTM). Dvoufázové potvrzení se v tomto tématu označuje jako 2PC.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. odpověď na zprávu aplikace|  
|2. CreateCoordinationContextResponse|13. potvrzení změn (dokončení)|  
|3. Register (dokončení)|14. Prepare (2PC)|  
|4. RegisterResponse|15. Příprava (2PC)|  
|5. zpráva aplikace|16. připraveno (2PC)|  
|6. CreateCoordinationContext s kontextem|17. připraveno (2PC)|  
|7. Register (trvanlivé)|18. potvrzeno (dokončení)|  
|8. RegisterResponse|19. Commit (2PC)|  
|9. CreateCoordinationContextResponse|20. Commit (2PC)|  
|10. Register (trvalý)|21. potvrzeno (2PC)|  
|11. RegisterResponse|22. potvrzeno (2PC)|  
  
 Tento dokument popisuje složení specifikace WS-AtomicTransaction se zabezpečením a popisuje zabezpečenou vazbu použitou pro komunikaci mezi správci transakcí. Přístup popsaný v tomto dokumentu byl úspěšně testován s jinými implementacemi WS-AT a WS-koordinace.  
  
 Obrázek a tabulka znázorňují čtyři třídy zpráv z hlediska zabezpečení:  
  
- Aktivační zprávy (CreateCoordinationContext a CreateCoordinationContextResponse).  
  
- Registrační zprávy (registr a RegisterResponse)  
  
- Zprávy protokolu (příprava, vrácení zpět, potvrzení, přerušení a tak dále).  
  
- Zprávy aplikace.  
  
 První tři třídy zpráv jsou považovány za zprávy správce transakcí a jejich konfigurace vazeb je popsána v části výměna zpráv aplikace dále v tomto tématu. Čtvrtá třída zprávy je aplikace na zprávy aplikace a je popsána v části Příklady zpráv dále v tomto tématu. Tato část popisuje vazby protokolu používané pro každou z těchto tříd pomocí služby WCF.  
  
 V celém tomto dokumentu se používají následující obory názvů XML a přidružené předpony.  
  
|Předpona|Identifikátor URI oboru názvů|  
|------------|-------------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|WSA|`http://www.w3.org/2004/08/addressing`|  
|wscoor|`http://schemas.xmlsoap.org/ws/2004/10/wscoor`|  
|WSAT|`http://schemas.xmlsoap.org/ws/2004/10/wsat`|  
|t|`http://schemas.xmlsoap.org/ws/2005/02/trust`|  
|o|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd`|  
|XSD|`http://www.w3.org/2001/XMLSchema`|  
  
## <a name="transaction-manager-bindings"></a>Vazby správce transakcí  
 R1001: Správci transakcí musí používat protokol SOAP 1,1 a WS-Addressing 2004/08 pro transakce WS-Atomic a výměnu zpráv WS-koordinační.  
  
 Zprávy aplikací nejsou omezeny na tyto vazby a jsou popsány později.  
  
### <a name="transaction-manager-https-binding"></a>Vazba HTTPS správce transakcí  
 Vazba HTTPS správce transakcí spoléhá výhradně na zabezpečení přenosu, aby dosáhla zabezpečení a navázala důvěryhodnost mezi jednotlivými páry odesílatele ve stromu transakcí.  
  
#### <a name="https-transport-configuration"></a>Konfigurace přenosu HTTPS  
 K navázání identity správce transakcí se používají certifikáty X. 509. Ověření klienta a serveru je povinné a autorizace klienta/serveru je popsána jako podrobnosti implementace:  
  
- R1111: certifikáty X. 509 prezentované přes síťový kabel musí mít název subjektu, který odpovídá plně kvalifikovanému názvu domény (FQDN) původního počítače.  
  
- B1112: Služba DNS musí být funkční mezi jednotlivými páry odesílatel-přijímač v systému, aby kontrola názvů subjektu X. 509 byla úspěšná.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Konfigurace aktivace a registrace vazby  
 WCF vyžaduje vazbu mezi požadavkem a odpovědí s korelace přes protokol HTTPS. (Další informace o korelaci a popisech vzorů pro výměnu zpráv požadavků a odpovědí najdete v tématu WS-Atomic Transaction, Section 8.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfigurace vazby protokolu 2PC  
 WCF podporuje jednosměrné (Datagram) zprávy přes protokol HTTPS. Korelace mezi zprávami je ponechána jako podrobnosti implementace.  
  
 B2131: implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v tématu Specifikace WS-Addressing, aby bylo možné dosáhnout korelace zpráv 2PC WCF.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Kombinovaná vazba zabezpečení správce transakcí  
 Toto je alternativní (smíšený režim) vazby, která používá zabezpečení přenosu v kombinaci s modelem tokenu WS-koordinace vydaným pro účely vytvoření identity.  Aktivace a registrace jsou jediné prvky, které se mezi těmito dvěma vazbami liší.  
  
#### <a name="https-transport-configuration"></a>Konfigurace přenosu HTTPS  
 K navázání identity správce transakcí se používají certifikáty X. 509. Ověřování klienta a serveru je povinné a ověřování klienta/serveru je ponecháno jako podrobnosti implementace.  
  
#### <a name="activation-message-binding-configuration"></a>Konfigurace vazby aktivační zprávy  
 Aktivační zprávy obvykle nejsou zapojeny do interoperability, protože se obvykle vyskytují mezi aplikací a jejím místním správcem transakcí.  
  
 B1221: WCF používá duplexní vazbu HTTPS (popsanou v [protokolech zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) pro aktivační zprávy. Zprávy žádosti a odpovědi jsou korelační pomocí WS-Addressing 2004/08.  
  
 Specifikace WS-Atomic transakce, oddíl 8, popisuje další podrobnosti o korelaci a vzorech výměny zpráv.  
  
- R1222: po přijetí a `CreateCoordinationContext` koordinátor musí vystavit `SecurityContextToken` přidružený tajný klíč `STx` . Tento token se vrátí v `t:IssuedTokens` hlavičce za specifikací WS-Trust.  
  
- R1223: Pokud k aktivaci dojde v rámci existujícího koordinačního kontextu, musí se tato zpráva nacházet v `t:IssuedTokens` záhlaví s `SecurityContextToken` přidruženým ke stávajícímu kontextu `CreateCoordinationContext` .  
  
 `t:IssuedTokens`Pro připojení k odchozí zprávě by měla být vygenerována nová hlavička `wscoor:CreateCoordinationContextResponse` .  
  
#### <a name="registration-message-binding-configuration"></a>Konfigurace vazby registrační zprávy  
 B1231: WCF používá duplexní vazbu HTTPS (popsané v [protokolech zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). Zprávy žádosti a odpovědi jsou korelační pomocí WS-Addressing 2004/08.  
  
 WS-AtomicTransaction, část 8, popisuje další podrobnosti o korelaci a popisy schémat výměny zpráv.  
  
 R1232: odchozí `wscoor:Register` zprávy musí používat `IssuedTokenOverTransport` režim ověřování popsaný v [protokolech zabezpečení](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 `wsse:Timestamp`Element musí být podepsán pomocí `SecurityContextToken STx` vydané. Tento podpis je důkazem vlastnictví tokenu přidruženého k konkrétní transakci a slouží k ověření účastníka, který v transakci zařadí. Zpráva RegistrationResponse se pošle zpátky přes HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfigurace vazby protokolu 2PC  
 WCF podporuje jednosměrné (Datagram) zprávy přes protokol HTTPS. Korelace mezi zprávami je ponechána jako podrobnosti implementace.  
  
 B2131: implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v tématu Specifikace WS-Addressing, aby bylo možné dosáhnout korelace zpráv 2PC WCF.  
  
## <a name="application-message-exchange"></a>Výměna zpráv aplikace  
 Aplikace jsou zdarma pro použití jakékoli konkrétní vazby pro zprávy aplikace a aplikace, pokud vazba splňuje následující požadavky na zabezpečení:  
  
- R2001: zprávy typu aplikace a aplikace musí přesměrovat `t:IssuedTokens` hlavičku spolu s `CoordinationContext` v hlavičce zprávy.  
  
- R2002: je nutné zadat integritu a důvěrnost `t:IssuedToken` .  
  
 `CoordinationContext`Hlavička obsahuje `wscoor:Identifier` . I když definice `xsd:AnyURI` umožňuje použití absolutních i relativních identifikátorů URI, podporuje pouze WCF `wscoor:Identifiers` , což jsou absolutní identifikátory URI.  
  
 Pokud `wscoor:Identifier` je v rámci `wscoor:CoordinationContext` RELATIVNÍho identifikátoru URI, chyby se vrátí z transakční služby WCF.  
  
## <a name="message-examples"></a>Příklady zpráv  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Zprávy o žádostech a odpovědích CreateCoordinationContext  
 Následující zprávy následují jako vzor požadavků a odpovědí.  
  
#### <a name="createcoordinationcontext"></a>CreateCoordinationContext  
  
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
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
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
  
#### <a name="createcoordinationcontextresponse"></a>CreateCoordinationContextResponse  
  
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
  
#### <a name="register"></a>Registrovat  
  
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
  
#### <a name="register-response"></a>Registrovat odpověď  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a>Zprávy protokolu dvou fází potvrzení  
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
  
#### <a name="application-message-request"></a>Zpráva aplikace – požadavek  
  
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
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
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
