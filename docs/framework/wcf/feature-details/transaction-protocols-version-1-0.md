---
title: Protokoly transakce verze 1.0
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60867daa7b8519f745c37371604807c51aa1cbb9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="transaction-protocols-version-10"></a>Protokoly transakce verze 1.0
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] verze 1 implementuje verze 1.0 protokoly WS-Atomic Transactions a WS-spolupráce. Další informace o verzi 1.1 najdete v tématu [protokoly transakcí](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Specifikace či dokumentu|Odkaz|  
|-----------------------------|----------|  
|WS-spolupráce|http://msdn.microsoft.com/ws/2005/08/ws-coordination/|  
|WS-AtomicTransaction|http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/|  
  
 Vzájemná funkční spolupráce na tyto specifikace protokolu na dvě úrovně je požadován: mezi aplikacemi a mezi správci transakcí (viz následující obrázek). Specifikace popisují příliš podrobně formáty zpráv a zpráv systému exchange pro obě úrovně interoperability. Některé zabezpečení, spolehlivost a kódování pro aplikace aplikace exchange platí stejně pro regulární aplikace exchange. Úspěšné vzájemná funkční spolupráce mezi správci transakcí však vyžaduje smlouvu na konkrétní vazby, protože obvykle není nakonfigurován uživatel.  
  
 Toto téma popisuje složení specifikace WS-Atomic Transactions (WS-AT) se zabezpečení a popisuje zabezpečené vazby používá pro komunikaci mezi správci transakcí. Postup popsaný v tomto dokumentu byl úspěšně testovaný s jiných implementacích protokolu WS-AT a WS-koordinace včetně IBM, IONA, Sun Microsystems a dalších.  
  
 Následující obrázek znázorňuje spolupráci mezi dvěma správci transakcí transakce Manager 1 a 2 správce transakcí a dvě aplikace, aplikace 1 a 2 aplikace.  
  
 ![Protokoly transakcí](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")  
  
 Zvažte Typický scénář WS-koordinaci/WS-Atomic Transactions s jeden iniciátor (I) a jeden účastník (P). Iniciátor i účastník mají správci transakcí (ITM a druh, v uvedeném pořadí). Dvoufázový zápis se označuje jako 2PC v tomto tématu.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Zpráva odpovědi aplikací|  
|2. CreateCoordinationContextResponse|13. Potvrzení (dokončení)|  
|3. Registrace (dokončení)|14. Příprava (2PC)|  
|4. RegisterResponse|15. Příprava (2PC)|  
|5. Zpráva aplikace|16. Připravené (2PC)|  
|6. CreateCoordinationContext s kontextem|17. Připravené (2PC)|  
|7. Registrace (trvale)|18. Potvrdit (dokončení)|  
|8. RegisterResponse|19. Potvrzení (2PC)|  
|9. CreateCoordinationContextResponse|20. Potvrzení (2PC)|  
|10. Registrace (trvale)|21. Potvrdit (2PC)|  
|11. RegisterResponse|22. Potvrdit (2PC)|  
  
 Tento dokument popisuje složení specifikace WS-AtomicTransaction se zabezpečením a zabezpečené vazby používá pro komunikaci mezi správci transakcí. Postup popsaný v tomto dokumentu byl úspěšně testovaný s jiných implementacích protokolu WS-AT a WS-koordinace.  
  
 Obrázek a tabulka ilustruje čtyři třídy zpráv z hlediska zabezpečení:  
  
-   Aktivace zprávy (CreateCoordinationContext a CreateCoordinationContextResponse).  
  
-   Registrační zprávy (registrace a RegisterResponse)  
  
-   Protokol zprávy (Příprava, vrácení zpět, potvrzení, bylo přerušeno. a tak dále).  
  
-   Zprávy aplikace.  
  
 První tři zpráva třídy jsou považovány za zprávy správce transakcí a jejich vazby konfigurace je popsaná v "Aplikace zpráva Exchange" dál v tomto tématu. Čtvrtý třída zprávy je aplikacích zpráv a je popsaný v části "Příklady zpráva" dál v tomto tématu. Tato část popisuje protokol vazby použít pro každý z těchto tříd pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 V tomto dokumentu se používají následující obory názvů XML a přidružené předpony.  
  
|Předpona|Namespace URI|  
|------------|-------------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|wsa|http://www.w3.org/2004/08/addressing|  
|wscoor|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|WSAT|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|t|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|O|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|XSD|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a>Správce transakcí vazby  
 R1001: Správci transakcí musíte použít SOAP 1.1 a WS-Addressing 2004/08 WS-Atomic Transactions a WS-koordinaci výměny zpráv.  
  
 Zprávy aplikace nejsou omezená na těchto vazeb a jsou popsané později.  
  
### <a name="transaction-manager-https-binding"></a>Vazba HTTPS správce transakcí.  
 Vazba HTTPS správce transakcí využívá výhradně zabezpečení přenosu k zajištění zabezpečení a navázání vztahu důvěryhodnosti mezi jednotlivé příjemce odesílatele páry ve stromové struktuře transakce.  
  
#### <a name="https-transport-configuration"></a>Konfigurace přenosu protokolu HTTPS  
 X.509 – certifikáty se používají k vytvoření Identity správce transakcí. Je požadováno ověřování klienta nebo serveru a klienta nebo serveru autorizace je ponechán jako podrobností implementace:  
  
-   R1111: Certifikáty X.509 poskytované prostřednictvím sítě musí mít název subjektu, který odpovídá plně kvalifikovaný název domény (FQDN) původní počítač.  
  
-   B1112: DNS musí být funkční mezi každý pár odesílatele příjemce v systému pro kontroly název subjektu X.509 proběhla úspěšně.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Aktivace a registrace vazby konfigurace  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyžaduje duplexní vazby požadavek nebo odpověď s korelací přes protokol HTTPS. (Další informace o korelaci a popisy vzoru exchange zprávu požadavku/odpovědi, viz WS-Atomic Transactions části 8.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfigurace vazeb protokolu 2PC  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje jednosměrné (datagram) zpráv přes protokol HTTPS. Korelace mezi zprávy je ponechán jako podrobností implementace.  
  
 B2131: Implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v WS-Addressing k dosažení korelaci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na 2PC zprávy.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Správce transakcí ve smíšeném vazby zabezpečení  
 Toto je alternativní (smíšený režim) vazby tohoto zabezpečení přenosu používá v kombinaci s modelem WS-koordinaci vystavený Token pro účely vytvoření identity.  Aktivace a registrace jsou pouze elementy, které se liší mezi dvě vazby.  
  
#### <a name="https-transport-configuration"></a>Konfigurace přenosu protokolu HTTPS  
 X.509 – certifikáty se používají k vytvoření Identity správce transakcí. Je požadováno ověřování klienta nebo serveru a klienta nebo serveru autorizace je ponechán jako podrobností implementace.  
  
#### <a name="activation-message-binding-configuration"></a>Konfigurace vazeb zpráva aktivace  
 Aktivace zprávy obvykle neúčastnit interoperabilita vzhledem k tomu většinou dochází mezi aplikací a jeho místní správce transakcí.  
  
 B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá duplexní vazbu HTTPS (popsané v [protokoly zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) pro aktivaci zprávy. Požadavek a odpověď zprávy jsou korelační pomocí protokolu WS-Addressing 2004/08.  
  
 Specifikace WS-Atomic Transactions, 8 část popisuje další podrobnosti o korelace a vzorce výměny zpráv.  
  
-   R1222: po přijetí `CreateCoordinationContext`, musíte vydat koordinátorem `SecurityContextToken` s přidružené tajný klíč `STx`. Tento token je vrácen uvnitř `t:IssuedTokens` záhlaví následující specifikace WS-Trust.  
  
-   R1223: Pokud se aktivace vyskytuje v kontextu existující koordinaci `t:IssuedTokens` hlavička s `SecurityContextToken` spojené s existující kontext musí procházet na `CreateCoordinationContext` zprávy.  
  
 Nový `t:IssuedTokens` záhlaví by měl být vygenerován pro připojení k odchozích `wscoor:CreateCoordinationContextResponse` zprávy.  
  
#### <a name="registration-message-binding-configuration"></a>Konfigurace vazeb zpráva registrace  
 B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá duplexní vazbu HTTPS (popsané v [protokoly zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). Požadavek a odpověď zprávy jsou korelační pomocí protokolu WS-Addressing 2004/08.  
  
 WS-AtomicTransaction, 8 část popisuje další podrobnosti o korelaci a popisy vzoru exchange zprávu.  
  
 R1232: Odchozí `wscoor:Register` musí používat zprávy `IssuedTokenOverTransport` režim ověřování popsané v [protokoly zabezpečení](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 `wsse:Timestamp` Element musí být podepsané pomocí `SecurityContextToken``STx` vystavené. Tento podpis je důkazem u sebe tokenu přidružený ke konkrétní transakci a slouží k ověřování účastník zapsání v transakci. Zpráva RegistrationResponse je odeslána zpět přes protokol HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Konfigurace vazeb protokolu 2PC  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje jednosměrné (datagram) zpráv přes protokol HTTPS. Korelace mezi zprávy je ponechán jako podrobností implementace.  
  
 B2131: Implementace musí podporovat `wsa:ReferenceParameters` jak je popsáno v WS-Addressing k dosažení korelaci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na 2PC zprávy.  
  
## <a name="application-message-exchange"></a>Zprávy aplikace Exchange  
 Aplikace jsou volně používat konkrétní vazby pro aplikaci aplikace zprávy, dokud vazbu splňuje následující požadavky na zabezpečení:  
  
-   R2001: Musí procházet aplikace aplikace zprávy `t:IssuedTokens` záhlaví spolu s `CoordinationContext` v záhlaví zprávy.  
  
-   R2002: Integrity a důvěrnosti `t:IssuedToken` musí být zadán.  
  
 `CoordinationContext` Hlavička obsahuje `wscoor:Identifier`. Při definici `xsd:AnyURI` umožňuje použití absolutní a relativní identifikátory URI, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje pouze `wscoor:Identifiers`, které jsou absolutní identifikátory URI.  
  
 Pokud `wscoor:Identifier` z `wscoor:CoordinationContext` je relativní identifikátor URI, bude vrácen chyb z transakcí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
## <a name="message-examples"></a>Příklady zpráv  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Zprávy CreateCoordinationContext požadavků a odpovědí  
 Následující zprávy podle vzoru požadavků a odpovědí.  
  
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
 Tyto zprávy jsou zprávy registrace.  
  
#### <a name="register"></a>Registr  
  
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
  
#### <a name="register-response"></a>Zaregistrovat odpovědi  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a>Dvě fáze potvrzení protokolu zpráv  
 Tato zpráva má vztah k protokolu dvoufázového potvrzení (2PC).  
  
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
 Tyto zprávy jsou zprávy aplikace.  
  
#### <a name="application-message-request"></a>Zpráva žádostí na aplikace  
  
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
