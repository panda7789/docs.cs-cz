---
title: '&lt;security&gt; – &lt;customBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
author: BrucePerlerMS
ms.openlocfilehash: 848dbf56436e1589697ffdb64d617961f29ac506
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47398008"
---
# <a name="ltsecuritygt-of-ltcustombindinggt"></a>&lt;security&gt; – &lt;customBinding&gt;
Určuje možnosti zabezpečení pro vlastní vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<třídě customBinding >  
\<Vytvoření vazby >  
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
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|Volitelné. Logická hodnota určující, pokud pro odpověď možné použít serializovaný token. Výchozí hodnota je `false`. Při použití duální vazby, výchozí nastavení `true` a ignorují se jakékoli nastavení provedli.|  
|authenticationMode|Volitelné. Určuje režim ověřování mezi iniciátorem a příjemce. Níže jsou pro všechny hodnoty.<br /><br /> Výchozí hodnota je `sspiNegotiated`.|  
|DefaultAlgorithmSuite|Volitelné. Nastaví zprávu algoritmy šifrování a klíč zalamování řádků. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Níže jsou uvedeny možné hodnoty. Výchozí hodnota je `Basic256`.<br /><br /> Tento atribut se používá při práci s jinou platformu, která požádá o pro sadu algoritmů, které jsou jiné než výchozí. Měli byste vědět silné a slabé stránky relevantní algoritmů při provádění změn pro toto nastavení. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|IncludeTimestamp|Logická hodnota určující, zda jsou časová razítka zahrnuta v každé zprávě. Výchozí hodnota je `true`.|  
|KeyEntropyMode|Určuje způsob, že se vypočítávají klíčů pro zabezpečení zpráv. Klíče může být založen na klienta materiál klíče, jenom na klíče materiál služby pouze nebo kombinaci obojího. Platné hodnoty jsou<br /><br /> -   `ClientEntropy`: Klíč relace je podle klíče data zadaná klientem.<br />-   `ServerEntropy`: Klíč relace je na základě klíčových dat server k dispozici.<br />-   `CombinedEntropy`: Klíč relace je podle klíče údaje poskytnuté klientem a službou.<br /><br /> Výchozí hodnota je `CombinedEntropy`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|MessageProtectionOrder|Nastaví pořadí, ve zpráv, které jsou použity algoritmy zabezpečení na úrovni zprávy. Platné hodnoty patří:<br /><br /> -   `SignBeforeEncrypt`: Přihlášení nejprve zašifrování.<br />-   `SignBeforeEncryptAndEncryptSignature`: Podepsat nejprve, šifrování a pak šifrování podpis.<br />-   `EncryptBeforeSign`: Šifrovat nejprve, pak přihlašování.<br /><br /> Výchozí hodnota závisí na verzi WS-Security používá. Výchozí hodnota je `SignBeforeEncryptAndEncryptSignature` při použití 1.1 WS-Security. Výchozí hodnota je `SignBeforeEncrypt` při použití 1.0 WS-Security.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|MessageSecurityVersion|Volitelné. Nastaví verzi WS-Security, který se používá. Platné hodnoty patří:<br /><br /> -WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> Výchozí hodnota je WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 a může být vyjádřena v souboru XML jako jednoduše `Default`. Tento atribut je typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Logická hodnota určující, pokud mohou být klíče odvozeny z původního ověřovacího klíče. Výchozí hodnota je `true`.|  
|requireSecurityContextCancellation|Volitelné. Logická hodnota, která určuje, pokud kontext zabezpečení zrušen a byla ukončena, pokud už je nepotřebujete. Výchozí hodnota je `true`.|  
|RequireSignatureConfirmation|Volitelné. Logická hodnota určující, zda je povoleno potvrzení podpisu WS-Security. Pokud je nastavena na `true`, podpisy zpráv potvrdí straně odpovídajícího.  Pokud vlastní vazby je konfigurován pro vzájemnými certifikáty nebo je nakonfigurovaný na použití vydané tokeny (služby WSS 1.1 vazbami), výchozí hodnota tohoto atributu `true`. V opačném případě výchozí hodnota je `false`.<br /><br /> Potvrzení podpisu se používá pro potvrzení, že je služba reagovat v úplné povědomí o požadavek.|  
|SecurityHeaderLayout|Volitelné. Určuje pořadí prvků v záhlaví zabezpečení. Platné hodnoty jsou<br /><br /> -   `Strict`: Položky jsou přidány do záhlaví zabezpečení podle obecné zásady "deklarovat před použitím".<br />-   `Lax`: Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, která potvrzuje WSS: zabezpečení zpráv SOAP.<br />-   `LaxWithTimestampFirst`: Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, která potvrzuje WSS: zabezpečení zprávy protokolu SOAP s tím rozdílem, že první prvek v záhlaví zabezpečení musí být prvek wsse:Timestamp.<br />-   `LaxWithTimestampLast`: Položky jsou přidány do záhlaví zabezpečení v libovolném pořadí, která potvrzuje WSS: zabezpečení zprávy protokolu SOAP s tím rozdílem, že po posledním prvku v záhlaví zabezpečení musí být prvek wsse:Timestamp.<br /><br /> Výchozí hodnota je `Strict`.<br /><br /> Tento prvek je typu <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|String|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Zabalení klíče použijte Aes128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.|  
|Basic192|Použijte šifrování Aes192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256|Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Rsa15|Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použití Aes192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDes|Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Rsa15|Použití Aes128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic128Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic192Sha256|Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|TripleDesSha256|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Sha256Rsa15|Použití Aes128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Určuje aktuální vydaný token. Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Určuje nastavení zabezpečení místního klienta pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Určuje nastavení zabezpečení místní služby pro tuto vazbu. Tento prvek je typu <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Určuje výchozí hodnoty pro inicializaci služby zabezpečené konverzace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o použití tohoto prvku, naleznete v tématu [režimy ověřování SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) a [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat zabezpečení použití vlastní vazby. Ukazuje, jak povolit zabezpečení na úrovni zprávy spolu s zabezpečeného přenosu pomocí vlastní vazby. To je užitečné, když zabezpečeného přenosu je potřebná pro přenos zpráv mezi klientem a službou a současně zprávy musí být zabezpečení na úrovni zprávy. Tato konfigurace není podporována vazeb poskytovaných systémem.  
  
 Konfigurace služby definuje vlastní vazby, který podporuje komunikaci TCP chráněných pomocí protokolu TLS/SSL a zabezpečení zpráv Windows. Vlastní vazba používá certifikát služby pro ověření služby na úrovni přenosu a k ochraně zprávy během přenosu mezi klientem a službou. Toho lze dosáhnout [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element vazby. Certifikát služby je nakonfigurovaný pomocí chování služby.  
  
 Kromě toho používá vlastní vazby zabezpečení zpráv s typ přihlašovacích údajů Windows – jedná se o výchozí typ přihlašovacích údajů. Toho lze dosáhnout [zabezpečení](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element vazby. Klient a služba ověření pomocí zabezpečení na úrovni zprávy, když mechanismus ověřování protokolu Kerberos je k dispozici. Pokud mechanismus ověřování protokolu Kerberos není k dispozici, bude použito ověřování NTLM. NTLM ověřuje klienta pro službu, ale neověří služby ke klientovi. [Zabezpečení](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element vazby je nakonfigurován na použití `SecureConversation` authenticationType, což vede k vytvoření relace zabezpečení klienta a služby. To je nutné povolit duplexního kontraktu služby pro práci. Další informace o spuštěním tohoto příkladu naleznete v tématu [vlastní vazby zabezpečení](../../../../../docs/framework/wcf/samples/custom-binding-security.md).  
  
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
 [\<třídě customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
