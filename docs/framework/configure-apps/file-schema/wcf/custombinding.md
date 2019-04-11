---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 60ce3cdfd7c78d152c71cdd652532cc96a6be296
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481116"
---
# <a name="custombinding"></a>\<customBinding>

Poskytuje plnou kontrolu nad zásobníkem zpráv pro daného uživatele.

\<system.serviceModel>\
\<vazby > \
\<customBinding>

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

Následující části popisují atributy, podřízené prvky a nadřazené elementy

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|closeTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|
|name|Řetězec, který obsahuje konfigurační název vazby. Tato hodnota je uživatelem definovaný řetězec, který funguje jako identifikační řetězec pro vlastní vazbu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|
|SendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<compositeDuplex>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|Určuje obousměrný zasílání zpráv pro vlastní vazbu. Používá se s přenosy, které neumožňují duplexní komunikaci nativně, například HTTP. TCP, naopak umožňuje nativně duplexní komunikaci a nevyžaduje použití tohoto elementu vazby pro služby umožňující odesílání zpráv zpět klientovi.<br /><br /> Klient musí vystavit adresu pro službu kontaktovat a navázat připojení. Tato adresa klienta poskytuje `ClientBaseAddress` atribut.<br /><br /> Tento prvek je typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.|
|[\<pnrpPeerResolver>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|Určuje mechanismus rozpoznávání partnera název řešení protokolu PNRP (Peer Name). Tento prvek je typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.|
|[\<reliableSession>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|Určuje nastavení pro zasílání zpráv WS-Reliable. Pokud tento prvek přidán na vlastní vazby, výsledný kanálu může podporovat přesně-jednou záruky doručení. Tento prvek je typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.|
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Určuje možnosti pro zabezpečení vlastních vazeb. Tento prvek je typu <xref:System.ServiceModel.Configuration.SecurityElement>.|
|[\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|Určuje nastavení zabezpečení pro datový proud vazby SSL. Tento prvek je typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.|
|[\<transactionFlow>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|Určuje, že vazba podporuje tok transakcí a protokol, který se použije `transactionProtocol` atribut. Tento prvek je typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.|
|[\<windowsStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|Určuje možnosti pro datový proud zabezpečení vlastních vazeb. Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|vazby|Obsahuje všechny vazby pro aplikace Windows Communication Foundation.|

## <a name="remarks"></a>Poznámky

Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF. Speciální míru vazby je možné vytvořit Moje Přidání elementů konfigurace pro konkrétní entity. Například můžete kombinovat uživatele `httpsTransport` části `reliableSession` oddílu a `security` část, která vytvoří spolehlivou a zabezpečenou https na základě vazby.

Jednotlivé vazby definuje zásobníku zprávu zadáním elementů konfigurace pro zásobník prvky v pořadí, ve kterém se zobrazují v zásobníku. Každý prvek definuje a konfiguruje jeden prvek zásobníku. Každá vlastní vazby musí být jeden a pouze jeden element přenosu. Bez tohoto elementu je neúplný zásobníkem zpráv.

Je důležité pořadí, v jakém jsou prvky uvedeny v zásobníku, protože je pořadí použití operace u zprávy. Doporučené pořadí elementů zásobníku je následující:

1. Transakce (volitelné)

2. Spolehlivé zasílání zpráv (volitelné)

3. Zabezpečení (volitelné)

4. Přenos

5. Kodér (volitelné)

Použijte vlastní vazby, pokud jedna z vazeb poskytovaných systémem nesplňuje požadavky vaší služby. Vlastní vazby může použít, například umožní použít nový přenos nebo nový kodér na koncový bod služby.

Vlastní vazby je vytvořená pomocí jedné z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekce vazby prvky, které jsou "skládaný" v určitém pořadí:

- V horní části je volitelný <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , která umožňuje toku transakce.

- Dále je volitelný <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> relaci a jak je definováno ve specifikaci WS-ReliableMessaging řazení mechanismus, který poskytuje. Tento pojem relace můžete různé zprostředkovatele protokolu SOAP a přenosu.

- Dále je element volitelný zabezpečení vazby, která poskytuje funkce zabezpečení, jako je ověřování, ověřování, ochrany a důvěrnost. Následující elementy vazby zabezpečení jsou k dispozici ve Windows Communication Foundation (WCF):

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- Dále jsou volitelné vzory zprávy určené elementů vazby:

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- Dále jsou upgrady/pomocné rutiny nepovinný přenosu elementů vazby:

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- Dále je element vazby kódování zprávy vyžaduje. Můžete použít vlastní přenos nebo použijte jednu z následujících vazby kódování zprávy:

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- V dolní části je prvek vyžaduje přenos. Můžete použít vlastní přenos nebo použijte jednu z přenosu, k dispozici ve Windows Communication Foundation (WCF) elementů vazby:

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

Následující tabulka shrnuje možnosti pro každou vrstvu.

|Vrstva|Možnosti|Požadováno|
|-----------|-------------|--------------|
|Tok transakcí|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Ne|
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Ne|
|Zabezpečení|Symetrické, asymetrické, transportní vrstvy|Ne|
|Změna tvaru|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|Ne|
|Upgrady přenosu|Datového proudu protokolu SSL, datového proudu Windows, rozpoznávání partnera|Ne|
|Kódování|Text, binární soubor, MTOM, vlastní|Ano|
|Přenos|Charakteristikami HTTP, HTTPS, TCP, pojmenovaných kanálů služby MSMQ, vlastní|Ano|

Kromě toho můžete definovat vlastní elementy vazby a vložit mezi všechny předchozí definované vrstvy.

Informace o tom, jak použít vlastní vazby k úpravě vazeb poskytovaných systémem, najdete v článku [jak: Přizpůsobení vazeb poskytovaných systémem](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [třídě customBinding – Element](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
