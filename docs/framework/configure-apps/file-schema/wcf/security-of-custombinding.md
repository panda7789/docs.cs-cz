---
title: "&lt;security&gt; – &lt;customBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
caps.latest.revision: "24"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e35f10071f8931c551645d4d07ca0f2113c52002
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="ltsecuritygt-of-ltcustombindinggt"></a>&lt;security&gt; – &lt;customBinding&gt;
Určuje možnosti zabezpečení u vlastních vazeb.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<zabezpečení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security   
   allowSerializedSigningTokenOnReply="Boolean"  
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
      securityHeaderLayout=  
              "Strict/Lax/LaxTimestampFirst/LaxTimestampLast">  
   <issuedTokenParameters />  
   <localClientSettings />  
   <localServiceSettings />  
   <secureConversationBootstrap />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|Volitelné. Logická hodnota, která určuje, pokud serializovaný token lze použít v odpovědi. Výchozí hodnota je `false`. Při použití duální vazby, nastavení výchozí hodnotu `true` a všechna nastavení provedené budou ignorovány.|  
|authenticationMode|Volitelné. Určuje režim ověřování používá mezi iniciátoru a odpovídající počítač. Všechny hodnoty jsou uvedeny níže.<br /><br /> Výchozí hodnota je `sspiNegotiated`.|  
|defaultAlgorithmSuite|Volitelné. Nastaví zprávu algoritmy šifrování a klíč wrap. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy mapovat platformám zadaným v specifikace jazyka zásady zabezpečení (WS-SecurityPolicy).<br /><br /> Níže jsou uvedeny možné hodnoty. Výchozí hodnota je `Basic256`.<br /><br /> Tento atribut se používá při práci s jinou platformu, která požádá sady algoritmů, které jsou jiné než výchozí. Byste měli být vědomi silné a slabé stránky relevantní algoritmů při provádění změn tohoto nastavení. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|includeTimestamp|Logická hodnota, která určuje, zda časová razítka jsou zahrnuta v každé zprávě. Výchozí hodnota je `true`.|  
|keyEntropyMode|Určuje způsob, že se vypočítávají klíče pro zabezpečení zpráv. Klíče může být založen na klienta materiál klíče pouze na služby materiál klíče pouze nebo jejich kombinaci. Platné hodnoty jsou<br /><br /> -   `ClientEntropy`: Klíč relace podle klíče data zadaná klientem.<br />-   `ServerEntropy`: Klíč relace podle klíče data poskytnutá serverem.<br />-   `CombinedEntropy`: Klíč relace je založena na klíčová data zadaná klientem a služby.<br /><br /> Výchozí hodnota je `CombinedEntropy`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|MessageProtectionOrder|Nastaví pořadí, ve zpráv, které jsou použity algoritmy úrovně zabezpečení ke zprávě. Platné hodnoty patří:<br /><br /> -   `SignBeforeEncrypt`: Přihlášení nejdřív zašifrování.<br />-   `SignBeforeEncryptAndEncryptSignature`: Přihlaste nejprve, šifrování a pak šifrování podpis.<br />-   `EncryptBeforeSign`: Šifrování nejprve pak přihlášení.<br /><br /> Výchozí hodnota závisí na verzi WS-zabezpečení, který se používá. Výchozí hodnota je `SignBeforeEncryptAndEncryptSignature` při použití služby WS-zabezpečení 1.1. Výchozí hodnota je `SignBeforeEncrypt` při použití služby WS-Security 1.0.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|messageSecurityVersion|Volitelné. Nastaví verzi protokolu WS-zabezpečení, který se používá. Platné hodnoty patří:<br /><br /> -WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> Výchozí hodnota je WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 a dají se vyjádřit jako jednoduše v souboru XML `Default`. Tento atribut je typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Logická hodnota, která určuje, pokud klíče může být odvozen od původního doklad klíče. Výchozí hodnota je `true`.|  
|requireSecurityContextCancellation|Volitelné. Logická hodnota, která určuje, pokud kontext zabezpečení by měl být zrušen a byla ukončena, když už ho nepotřebují. Výchozí hodnota je `true`.|  
|RequireSignatureConfirmation|Volitelné. Logická hodnota, která určuje, zda je povoleno potvrzení podpisu WS-zabezpečení. Pokud nastavíte hodnotu `true`, podpisy zpráv potvrdí odpovídající partner.  Pokud vlastní vazby je nakonfigurován pro vzájemnými certifikáty nebo je nakonfigurován pro použití vydané tokeny (WSS 1.1 vazby), použije se výchozí hodnota tohoto atributu `true`. Jinak, výchozí hodnota je `false`.<br /><br /> Potvrzení podpisu se používá pro potvrzení, zda služba reaguje v úplné povědomí o požadavek.|  
|securityHeaderLayout|Volitelné. Určuje pořadí prvků v záhlaví zabezpečení. Platné hodnoty jsou<br /><br /> -   `Strict`: Položky budou přidány do záhlaví zabezpečení podle obecné zásady "deklarovat před použitím".<br />-   `Lax`: Položky budou přidány do záhlaví zabezpečení v libovolném pořadí, který potvrdí k WSS: zabezpečení protokolu SOAP zprávy.<br />-   `LaxWithTimestampFirst`: Položky budou přidány do záhlaví zabezpečení v libovolném pořadí, který potvrdí k WSS: zabezpečení zpráv protokolu SOAP s tím rozdílem, že prvním elementem v záhlaví zabezpečení musí být wsse:Timestamp element.<br />-   `LaxWithTimestampLast`: Položky budou přidány do záhlaví zabezpečení v libovolném pořadí, který potvrdí k WSS: zabezpečení zpráv protokolu SOAP s tím rozdílem, že posledním prvkem v záhlaví zabezpečení musí být wsse:Timestamp element.<br /><br /> Výchozí hodnota je `Strict`.<br /><br /> Tento element je typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Použijte šifrování pomocí algoritmu aes128 za pomoci, Sha1 pro hodnota hash a šifrování Rsa. oaep mgf1p pro zabalení klíče.|  
|Basic192|Použijte šifrování pomocí Aes192, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256|Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Rsa15|Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použijte Aes192 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|TripleDes|Použití šifrování TripleDes, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Rsa15|Pomocí algoritmu aes128 za pomoci pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Použití šifrování TripleDes, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|Basic128Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic192Sha256|Použijte Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|TripleDesSha256|Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Sha256Rsa15|Pomocí algoritmu aes128 za pomoci pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použijte Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<– issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Určuje aktuální vystavený token. Tento element je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Určuje nastavení zabezpečení místního klienta pro tuto vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Určuje nastavení zabezpečení na místní služby pro tuto vazbu. Tento element je typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Určuje výchozí hodnoty používané pro inicializaci služby Zabezpečené konverzaci.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]Pomocí tohoto elementu, najdete v tématu [režimy ověřování SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) a [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat zabezpečení použití vlastní vazby. Ukazuje, jak použít k povolení zabezpečení na úrovni zpráv společně s zabezpečený přenos vlastní vazby. To je užitečné, když zabezpečení přenosu je potřeba k přenosu zpráv mezi klientem a službou a současně zprávy musí být zabezpečení na úrovni zpráv. Tato konfigurace není podporována vazby poskytované systémem.  
  
 Konfigurace služby definuje vlastní vazby, která podporuje komunikaci TCP, které jsou chráněné pomocí protokolu TLS/SSL a zabezpečení zpráv systému Windows. Vlastní vazby používá certifikát služby k ověřování na úrovni přenosu a k ochraně zprávy během přenosu mezi klientem a službou. To lze provést [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) prvku vazby. Certifikát služby je nakonfigurovaný pomocí chování služby.  
  
 Kromě toho používá vlastní vazby zabezpečení zpráv s typ přihlašovacích údajů Windows – jedná se o výchozí typ přihlašovacích údajů. To lze provést [zabezpečení](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) prvku vazby. Klienta a služby se ověřují pomocí zabezpečení na úrovni zpráv, pokud se mechanismus ověřování protokolu Kerberos je k dispozici. Pokud se mechanismus ověřování protokolu Kerberos není k dispozici, je použít ověřování NTLM. NTLM ověřuje klienta pro službu ale neověřuje služby klienta. [Zabezpečení](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) prvku vazby je nakonfigurovaný na použití `SecureConversation` authenticationType, což vede k vytvoření relace zabezpečení na klienta a služby. To je nutné povolit duplexního kontraktu služby pracovat. Další informace o spouštění v tomto příkladu najdete v tématu [vlastní vazby zabezpečení](../../../../../docs/framework/wcf/samples/custom-binding-security.md).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <sslStreamSecurity requireClientCertificate="false"/>  
          <tcpTransport/>  
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
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.SecurityElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
