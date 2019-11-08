---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 766dab35541465da15ccb1090d41b22332aafd0e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739050"
---
# <a name="custombinding"></a>\<customBinding >

Poskytuje plnou kontrolu nad zásobníkem zpráv pro uživatele.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customBinding >**  

## <a name="syntax"></a>Syntaxe

```xml
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|closeTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota je uživatelem definovaný řetězec, který slouží jako identifikační řetězec pro vlastní vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|
|openTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|
|receiveTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|
|SendTimeout|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<compositeDuplex >](compositeduplex.md)|Určuje obousměrný způsob zasílání zpráv do vlastní vazby. Používá se s přenosy, které nativně neumožňují duplexní komunikaci, například HTTP. Protokol TCP naopak umožňuje nativně duplexní komunikaci nativně a nevyžaduje použití tohoto elementu vazby, aby služba odesílala zprávy zpátky klientovi.<br /><br /> Klient musí vystavit adresu, aby mohla služba vytvořit kontakt a navázat připojení. Tato adresa klienta je poskytována atributem `ClientBaseAddress`.<br /><br /> Tento prvek je typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.|
|[\<pnrpPeerResolver >](pnrppeerresolver.md)|Určuje překladač názvů partnerských uzlů PNRP (Peer Name Resolution Protocol). Tento prvek je typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.|
|[\<reliableSession >](reliablesession.md)|Určuje nastavení pro zasílání zpráv WS-Reliable. Když se tento prvek přidá do vlastní vazby, může výsledný kanál podporovat pouze zajištění doručení právě jednou. Tento prvek je typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.|
|[> zabezpečení \<](security-of-custombinding.md)|Určuje možnosti pro zabezpečení vlastní vazby. Tento prvek je typu <xref:System.ServiceModel.Configuration.SecurityElement>.|
|[\<sslStreamSecurity >](sslstreamsecurity.md)|Určuje nastavení zabezpečení pro vazbu streamu SSL. Tento prvek je typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.|
|[\<transactionFlow >](transactionflow.md)|Určuje, že vazba podporuje tok transakce a protokol, který má atribut `transactionProtocol` použít. Tento prvek je typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.|
|[\<zabezpečení windowsstreamsecurity >](windowsstreamsecurity.md)|Určuje možnosti pro zabezpečení streamování vlastní vazby. Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|vazby|Obsahuje všechny vazby pro aplikace Windows Communication Foundation.|

## <a name="remarks"></a>Poznámky

Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF. Speciální vazby, které lze přizpůsobit, lze vytvořit přidáním elementů konfigurace pro konkrétní entity. Uživatel může například kombinovat oddíl `httpsTransport`, `reliableSession` oddíl a `security` oddíl a vytvořit tak spolehlivou a zabezpečenou vazbu založenou na protokolu HTTPS.

Jednotlivá vazba definuje zásobník zpráv zadáním elementů konfigurace pro prvky zásobníku v pořadí, v jakém se zobrazují v zásobníku. Každý prvek definuje a nakonfiguruje jeden prvek zásobníku. V každé vlastní vazbě musí být jeden a jenom jeden transportní element. Bez tohoto elementu je zásobník pro zasílání zpráv neúplný.

Pořadí, ve kterém se prvky zobrazí v zásobníku, protože se jedná o pořadí, ve kterém jsou operace pro zprávu aplikovány. Doporučené pořadí prvků zásobníku je následující:

1. Transakce (volitelné)

2. Spolehlivé zasílání zpráv (volitelné)

3. Zabezpečení (volitelné)

4. Přepravu

5. Kodér (volitelné)

Vlastní vazbu použijte v případě, že jedna z vazeb poskytovaných systémem nesplňuje požadavky vaší služby. Vlastní vazbu můžete použít například k povolení použití nového přenosu nebo nového kodéru na koncovém bodu služby.

Vlastní vazba je vytvořena pomocí jedné z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekce prvků vazby, které jsou "skládané" v určitém pořadí:

- V horní části je volitelná <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, která umožňuje přesměrovat transakce.

- Dále je volitelná <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>, která poskytuje mechanismus pro relaci a řazení, jak je definováno ve specifikaci WS-ReliableMessaging. Tento pojem relace může přenášet propojení mezi zprostředkovateli SOAP a přenosu.

- Další je volitelný prvek vazby zabezpečení, který poskytuje funkce zabezpečení jako autorizaci, ověřování, ochranu a důvěrnost. Pomocí Windows Communication Foundation (WCF) jsou k dispozici následující prvky vazby zabezpečení:

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- Dále jsou nepovinné vzory zpráv určené prvky vazby:

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- Dále jsou k dispozici volitelné upgrady přenosu/prvky vazby pomocníků:

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- Další je povinný element vazby kódování zprávy. Můžete použít vlastní přenos nebo použít jednu z následujících vazeb kódování zpráv:

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- V dolní části je požadovaný transportní prvek. Můžete použít vlastní přenos nebo použít jeden z elementů vazby přenosu poskytovaných Windows Communication Foundation (WCF):

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

Následující tabulka shrnuje možnosti pro každou vrstvu.

|Vrstvení|Možnosti|Požadováno|
|-----------|-------------|--------------|
|Tok transakce|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Ne|
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Ne|
|Zabezpečení|Symetrický, asymetrický, transportní úroveň|Ne|
|Změna tvaru|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|Ne|
|Upgrady přenosu|Datový proud SSL, Windows Stream, peer resolver|Ne|
|Kódování|Text, binární, MTOM, vlastní|Ano|
|Přepravu|TCP, pojmenované kanály, HTTP, HTTPS, charakter služby MSMQ, vlastní|Ano|

Kromě toho můžete definovat vlastní prvky vazby a vkládat je mezi kteroukoli z předchozích definovaných vrstev.

Diskuzi o tom, jak používat vlastní vazbu k úpravě vazby zadané systémem, najdete v tématu [How to: Customizing a bindingd a System-dodaná](../../../wcf/extending/how-to-customize-a-system-provided-binding.md)vazba.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [vazba \<](bindings.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [Element customBinding](custombinding.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
