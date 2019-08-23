---
title: <security> z <customBinding>
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
ms.openlocfilehash: 89fb1f766906c02a5e3ef9a9cdd1aef94ede80fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936717"
---
# <a name="security-of-custombinding"></a>\<> zabezpečení > \<CustomBinding
Určuje možnosti zabezpečení pro vlastní vazbu.  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
\<> zabezpečení  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security allowSerializedSigningTokenOnReply="Boolean"
          authenticationMode="AuthenticationMode"
          defaultAlgorithmSuite="SecurityAlgorithmSuite"
          includeTimestamp="Boolean"
          requireDerivedKeys="Boolean"
          keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
          messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
          messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
          requireDerivedKeys="Boolean"
          requireSecurityContextCancellation="Boolean"
          requireSignatureConfirmation="Boolean"
          securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast">
   <issuedTokenParameters />
   <localClientSettings />
   <localServiceSettings />
   <secureConversationBootstrap />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|Volitelný parametr. Logická hodnota, která určuje, zda lze pro odpověď použít serializovaný token. Výchozí hodnota je `false`. Při použití duální vazby se nastaví výchozí `true` nastavení a jakékoli provedené nastavení bude ignorováno.|  
|authenticationMode|Volitelný parametr. Určuje režim ověřování, který se používá mezi iniciátorem a respondérem. Všechny hodnoty najdete níže.<br /><br /> Výchozí hodnota je `sspiNegotiated`.|  
|defaultAlgorithmSuite|Volitelný parametr. Nastaví šifrování zpráv a algoritmy pro zabalení klíčů. Algoritmy a velikosti klíčů jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídou. Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Možné hodnoty jsou uvedeny níže. Výchozí hodnota je `Basic256`.<br /><br /> Tento atribut se používá při práci s jinou platformou, která se výslovný pro sadu algoritmů, která se liší od výchozí hodnoty. Při provádění úprav tohoto nastavení byste měli být vědomi síly a slabých stránek relevantních algoritmů. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|includeTimestamp|Logická hodnota, která určuje, zda jsou časová razítka obsažena v každé zprávě. Výchozí hodnota je `true`.|  
|keyEntropyMode|Určuje způsob výpočtu klíčů pro zabezpečení zpráv. Klíče můžou být založené jenom na materiálech klientského klíče, jenom v materiálech klíče služby nebo v kombinaci obou. Platné hodnoty jsou<br /><br /> -   `ClientEntropy`: Klíč relace je založen na klíčových datech poskytovaných klientem.<br />-   `ServerEntropy`: Klíč relace je založen na klíčových datech poskytovaných serverem.<br />-   `CombinedEntropy`: Klíč relace je založen na klíčových datech poskytovaných klientem a službou.<br /><br /> Výchozí hodnota je `CombinedEntropy`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|messageProtectionOrder|Nastaví pořadí, ve kterém jsou pro zprávu aplikovány algoritmy zabezpečení na úrovni zprávy. Platné hodnoty jsou následující:<br /><br /> -   `SignBeforeEncrypt`: Nejdřív se podepište a pak zašifrujte.<br />-   `SignBeforeEncryptAndEncryptSignature`: Nejdřív si podepište podpis, zašifrujte ho a pak zašifrujte.<br />-   `EncryptBeforeSign`: Nejprve Zašifrujte a pak podepište.<br /><br /> Výchozí hodnota závisí na používané verzi WS-Security. Výchozí hodnota je `SignBeforeEncryptAndEncryptSignature` při použití protokolu WS-Security 1,1. Výchozí hodnota je `SignBeforeEncrypt` při použití protokolu WS-Security 1,0.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|messageSecurityVersion|Volitelný parametr. Nastaví verzi WS-Security, která se používá. Platné hodnoty jsou následující:<br /><br /> - WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />- WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />- WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> Výchozí hodnota je WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 a může být vyjádřena v XML jako jednoduše `Default`. Tento atribut je typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Logická hodnota, která určuje, zda mohou být klíče odvozeny z původních ověřovacích klíčů. Výchozí hodnota je `true`.|  
|requireSecurityContextCancellation|Volitelný parametr. Logická hodnota, která určuje, zda má být kontext zabezpečení zrušen a ukončen, pokud již není požadován. Výchozí hodnota je `true`.|  
|requireSignatureConfirmation|Volitelný parametr. Logická hodnota, která určuje, zda je povoleno potvrzení podpisu WS-Security. Když je nastavené na `true`, příjemce potvrdí podpisy zpráv.  Když je vlastní vazba nakonfigurovaná pro vzájemné certifikáty nebo je nakonfigurovaná tak, aby používala vydané tokeny (vazby WSS 1,1) `true`tento atribut má výchozí hodnotu. V opačném případě je `false`výchozí hodnota.<br /><br /> Potvrzení podpisu se používá k potvrzení, že služba reaguje v plné povědomí o žádosti.|  
|securityHeaderLayout|Volitelný parametr. Určuje pořadí prvků v záhlaví zabezpečení. Platné hodnoty jsou<br /><br /> -   `Strict`: Položky jsou přidány do záhlaví zabezpečení podle obecné zásady deklarace před použitím.<br />-   `Lax`: Položky se přidají do záhlaví zabezpečení v libovolném pořadí, které potvrdí na WSS: Zabezpečení zprávy SOAP.<br />-   `LaxWithTimestampFirst`: Položky se přidají do záhlaví zabezpečení v libovolném pořadí, které potvrdí na WSS: Zabezpečení zprávy SOAP s výjimkou toho, že první prvek v záhlaví zabezpečení musí být element wsse: Timestamp.<br />-   `LaxWithTimestampLast`: Položky se přidají do záhlaví zabezpečení v libovolném pořadí, které potvrdí na WSS: Zabezpečení zprávy SOAP s výjimkou toho, že poslední prvek v záhlaví zabezpečení musí být element wsse: Timestamp.<br /><br /> Výchozí hodnota je `Strict`.<br /><br /> Tento prvek je typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|String|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Basic128|Pro zabalení klíče použijte šifrování Aes128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.|  
|Basic192|Pro zabalení klíče použijte šifrování Aes192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.|  
|Basic256|Pro zabalení klíče použijte šifrování AES256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.|  
|Basic256Rsa15|Použijte AES256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použijte Aes192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDes|Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.|  
|Basic128Rsa15|Použijte Aes128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.|  
|Basic128Sha256|Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic192Sha256|Pro zabalení klíče použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic256Sha256|Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|TripleDesSha256|Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic128Sha256Rsa15|Použijte Aes128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Určuje aktuální vydaný token. Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](localclientsettings-element.md)|Určuje nastavení zabezpečení místního klienta pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](localservicesettings-element.md)|Určuje nastavení zabezpečení místní služby pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Určuje výchozí hodnoty, které se použijí při inicializaci služby zabezpečené konverzace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> vazby](../../../misc/binding.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o použití tohoto prvku naleznete v tématu [režimy ověřování SecurityBindingElement](../../../wcf/feature-details/securitybindingelement-authentication-modes.md) a [postupy: Vytvořte vlastní vazbu pomocí SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat zabezpečení pomocí vlastní vazby. Ukazuje, jak použít vlastní vazbu k povolení zabezpečení na úrovni zprávy společně se zabezpečeným přenosem. To je užitečné, když zabezpečený přenos vyžaduje k přenosu zpráv mezi klientem a službou a současně musí být zprávy na úrovni zprávy zabezpečené. Tato konfigurace není podporována vazbami poskytovanými systémem.  
  
 Konfigurace služby definuje vlastní vazbu, která podporuje komunikaci TCP chráněnou pomocí protokolu TLS/SSL a zabezpečení zpráv Windows. Vlastní vazba používá k ověření služby na úrovni přenosu certifikát služby a chrání zprávy během přenosu mezi klientem a službou. Toho je dosaženo [ \<prvkem vazby sslStreamSecurity >](sslstreamsecurity.md) . Certifikát služby je nakonfigurovaný pomocí chování služby.  
  
 Navíc vlastní vazba používá zabezpečení zpráv s typem přihlašovacích údajů systému Windows – jedná se o výchozí typ přihlašovacích údajů. To je provedeno prvkem vazby [zabezpečení](security-of-custombinding.md) . Klient i služba jsou ověřovány pomocí zabezpečení na úrovni zpráv, pokud je k dispozici mechanismus ověřování protokolu Kerberos. Pokud ověřovací mechanismus protokolu Kerberos není k dispozici, použije se ověřování NTLM. Protokol NTLM ověřuje klienta služby, ale neověřuje službu pro klienta. Element vazby [zabezpečení](security-of-custombinding.md) je nakonfigurován tak, aby `SecureConversation` používal AuthenticationType, což vede k vytvoření relace zabezpečení v klientovi i ve službě. Tato možnost je nutná k tomu, aby fungovala činnost duplexního kontraktu služby. Další informace o spuštění tohoto příkladu naleznete v tématu [zabezpečení vlastních vazeb](../../../wcf/samples/custom-binding-security.md).  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- use following base address -->
            <add baseAddress="net.tcp://localhost:8000/ServiceModelSamples/Service"/>
          </baseAddresses>
        </host>
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
        <!-- the mex endpoint is exposed at net.tcp://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <!-- configure a custom binding -->
      <customBinding>
        <binding name="Binding1">
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <sslStreamSecurity requireClientCertificate="false" />
          <tcpTransport />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
          <serviceCredentials>
            <serviceCertificate findValue="localhost"
                                storeLocation="LocalMachine"
                                storeName="My"
                                x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.SecurityElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpečení vlastních vazeb](../../../wcf/samples/custom-binding-security.md)
