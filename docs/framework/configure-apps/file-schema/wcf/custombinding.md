---
title: '&lt;customBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 267bf183e40c8647959e97ae479d78cfe41367b2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustombindinggt"></a>&lt;customBinding&gt;
Poskytuje plnou kontrolu nad zasílání zpráv zásobníku pro uživatele.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<customBinding>  
    <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
       <compositeDuplex clientBaseAddress="Uri"/>  
       <reliableSession acknowledgementInterval="TimeSpan"  
           advancedFlowControl="Boolean"   
           bufferedMessagesQuota="Integer"  
           inactivityTimeout="TimeSpan"  
           maxPendingChannels="Integer"  
           maxRetryCount="Integer"   
           ordered="Boolean" />  
       <pnrpPeerResolver />  
       <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
       <sslStreamSecurity requireClientCertificate="Boolean" />  
              <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
       <security   
          defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
  
<security   
      defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
<security   
   defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
   <GenericIssuedTokenParameters>   
      <LocalIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"  
        keySize="Integer"  
        tokenType="String" />  
     <IssuedTokenParametersEndpointAddress address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
     <IssuedTokenClient localIssuerChannelBehaviors="String"  
        cacheIssuedTokens="Boolean"  
        maxIssuedTokenCachingTime="TimeSpan"  
        keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />  
     <IssuedTokenClientBehavior issuerAddress="String"  
        behaviorConfiguration="String" />  
     <IssuedTokenClientBehavior address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
   </GenericIssuedTokenParameters>   
</security>  
</binding>  
</customBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Intervalu|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|name|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota je řetězec definovaný uživatelem, který funguje jako identifikační řetězec pro vlastní vazby. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|receiveTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|sendTimeout|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<compositeDuplex >](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|Určuje obousměrný zasílání zpráv na vlastní vazby. Používá se s přenosy, které neumožňují duplexní komunikace nativně, například HTTP. TCP, naopak umožňuje duplexní komunikace nativně a nevyžaduje použití tohoto elementu vazby pro službu k odesílání zpráv zpět do klienta.<br /><br /> Klient musí vystavit adresu pro službu, aby kontaktovat a navázat připojení. Tato adresa klienta poskytuje `ClientBaseAddress` atribut.<br /><br /> Tento element je typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.|  
|[\<pnrpPeerResolver >](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|Určuje název překladač sdílené řešení protokolu PNRP (Peer Name). Tento element je typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.|  
|[\<reliableSession >](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|Určuje nastavení pro WS-spolehlivé zasílání zpráv. Pokud tento element je přidat do vlastní vazby, výsledná kanál může podporovat přesně-jednou záruky doručení. Tento element je typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Určuje možnosti zabezpečení vlastní vazby. Tento element je typu <xref:System.ServiceModel.Configuration.SecurityElement>.|  
|[\<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|Určuje nastavení zabezpečení pro vazbu SSL datového proudu. Tento element je typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.|  
|[\<transactionFlow >](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|Určuje, že vazba podporuje toku transakcí a protokol, který se použije `transactionProtocol` atribut. Tento element je typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.|  
|[\<windowsStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|Určuje možnosti pro streamování zabezpečení vlastních vazeb. Tento element je typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazby|Obsahuje všechny vazby pro aplikace Windows Communication Foundation.|  
  
## <a name="remarks"></a>Poznámky  
 Vlastní vazby poskytují plnou kontrolu nad zásobníku zasílání zpráv WCF. Speciální šité na míru vazeb se dá vytvořit Moje přidávání konfigurační prvky pro konkrétní entity. Například můžete kombinovat uživatele `httpsTransport` části `reliableSession` části a `security` oddílu pro vytvoření spolehlivou a zabezpečenou https na základě vazby.  
  
 Jednotlivé vazby definuje zásobníku zprávu zadáním konfigurační prvky pro prvky zásobníku v pořadí, ve kterém se objeví v zásobníku. Každý prvek definuje a konfiguruje jeden element zásobníku. Každý vlastní vazby musí být pouze jeden element přenosu. Bez tohoto elementu je nekompletní zasílání zpráv zásobníku.  
  
 Pořadí, ve kterém elementy zobrazují v zásobníku důležitý, protože je pořadí, ve kterém jsou použity operace ke zprávě. Doporučené pořadí elementů zásobníku je následující:  
  
1.  Transakce (volitelné)  
  
2.  Spolehlivé zasílání zpráv (volitelné)  
  
3.  Zabezpečení (volitelné)  
  
4.  Přenos  
  
5.  Kodér (volitelné)  
  
 Použijte vlastní vazby, pokud jeden z vazby poskytované systémem nesplňuje požadavky vaší služby. Vlastní vazby bylo možné použít, například povolení použití nový přenos nebo nové kodér na koncový bod služby.  
  
 Vlastní vazby je vytvořený pomocí jedné z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekce elementů, které jsou "skládaný" v určitém pořadí vazby:  
  
-   V horní části je volitelný <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> umožňuje toku transakcí.  
  
-   Dále je volitelný <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> relaci a jak jsou definovány ve specifikaci WS-ReliableMessaging řazení mechanismus, který poskytuje. Tato představu o relaci můžete křížová zprostředkovatele protokolu SOAP a přenosu.  
  
-   Dále je element vazby volitelné zabezpečení, který poskytuje funkce zabezpečení, jako je ověřování, ověřování, ochrana a důvěrnost. Jsou poskytovány následující prvky vazby zabezpečení [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   Dále jsou volitelné zpráva vzory určené elementů vazby:  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   Dále jsou volitelné přenosu upgrady nebo pomocné prvky vazeb:  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Dále je požadované zpráva kódování prvku vazby. Můžete použít vlastní přenos nebo použijte jednu z kódování vazby následující zpráva:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   V dolní části je element požadované přenosu. Můžete použít vlastní přenos nebo použijte jeden z elementů poskytované vazby přenosu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 Následující tabulka shrnuje možnosti pro jednotlivé úrovně.  
  
|Vrstva|Možnosti|Požadováno|  
|-----------|-------------|--------------|  
|Tok transakcí|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Ne|  
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Ne|  
|Zabezpečení|Symetrické, asymetrické, transportní vrstvy|Ne|  
|Změna tvaru|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|Ne|  
|Upgrady přenosu|Datový proud protokolu SSL, Windows datového proudu, sdílené překladač|Ne|  
|Kódování|Text, binární, MTOM, vlastní|Ano|  
|Přenos|TCP, pojmenované kanály protokolu HTTP, HTTPS, typů služby MSMQ, vlastní|Ano|  
  
 Kromě toho můžete definovat vlastní prvky vazby a vložte je mezi některé z předchozích definované vrstvy.  
  
 Informace o tom, jak používat vlastní vázání na Upravit vazby poskytované systémem, naleznete v [postupy: přizpůsobení vazbu System-Provided](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
1.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [customBinding – Element](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
