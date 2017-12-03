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
# <a name="ltcustombindinggt"></a><span data-ttu-id="42844-102">&lt;customBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="42844-102">&lt;customBinding&gt;</span></span>
<span data-ttu-id="42844-103">Poskytuje plnou kontrolu nad zasílání zpráv zásobníku pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="42844-103">Provides full control over the messaging stack for the user.</span></span>  
  
 <span data-ttu-id="42844-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="42844-104">\<system.serviceModel></span></span>  
<span data-ttu-id="42844-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="42844-105">\<bindings></span></span>  
<span data-ttu-id="42844-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="42844-106">\<customBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42844-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42844-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42844-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="42844-108">Attributes and Elements</span></span>  
 <span data-ttu-id="42844-109">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="42844-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42844-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="42844-110">Attributes</span></span>  
  
|<span data-ttu-id="42844-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="42844-111">Attribute</span></span>|<span data-ttu-id="42844-112">Popis</span><span class="sxs-lookup"><span data-stu-id="42844-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42844-113">Intervalu</span><span class="sxs-lookup"><span data-stu-id="42844-113">closeTimeout</span></span>|<span data-ttu-id="42844-114">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="42844-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="42844-115">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="42844-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="42844-116">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="42844-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="42844-117">name</span><span class="sxs-lookup"><span data-stu-id="42844-117">name</span></span>|<span data-ttu-id="42844-118">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="42844-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="42844-119">Tato hodnota je řetězec definovaný uživatelem, který funguje jako identifikační řetězec pro vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="42844-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="42844-120">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="42844-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="42844-121">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="42844-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="42844-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="42844-122">openTimeout</span></span>|<span data-ttu-id="42844-123">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="42844-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="42844-124">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="42844-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="42844-125">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="42844-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="42844-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="42844-126">receiveTimeout</span></span>|<span data-ttu-id="42844-127">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="42844-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="42844-128">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="42844-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="42844-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="42844-129">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="42844-130">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="42844-130">sendTimeout</span></span>|<span data-ttu-id="42844-131">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="42844-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="42844-132">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="42844-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="42844-133">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="42844-133">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42844-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="42844-134">Child Elements</span></span>  
  
|<span data-ttu-id="42844-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="42844-135">Element</span></span>|<span data-ttu-id="42844-136">Popis</span><span class="sxs-lookup"><span data-stu-id="42844-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42844-137">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="42844-137">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="42844-138">Určuje obousměrný zasílání zpráv na vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="42844-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="42844-139">Používá se s přenosy, které neumožňují duplexní komunikace nativně, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="42844-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="42844-140">TCP, naopak umožňuje duplexní komunikace nativně a nevyžaduje použití tohoto elementu vazby pro službu k odesílání zpráv zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="42844-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="42844-141">Klient musí vystavit adresu pro službu, aby kontaktovat a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="42844-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="42844-142">Tato adresa klienta poskytuje `ClientBaseAddress` atribut.</span><span class="sxs-lookup"><span data-stu-id="42844-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="42844-143">Tento element je typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="42844-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|  
|[<span data-ttu-id="42844-144">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="42844-144">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="42844-145">Určuje název překladač sdílené řešení protokolu PNRP (Peer Name).</span><span class="sxs-lookup"><span data-stu-id="42844-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="42844-146">Tento element je typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="42844-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|  
|[<span data-ttu-id="42844-147">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="42844-147">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="42844-148">Určuje nastavení pro WS-spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="42844-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="42844-149">Pokud tento element je přidat do vlastní vazby, výsledná kanál může podporovat přesně-jednou záruky doručení.</span><span class="sxs-lookup"><span data-stu-id="42844-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="42844-150">Tento element je typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="42844-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|  
|[<span data-ttu-id="42844-151">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="42844-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="42844-152">Určuje možnosti zabezpečení vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="42844-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="42844-153">Tento element je typu <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="42844-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|  
|[<span data-ttu-id="42844-154">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="42844-154">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="42844-155">Určuje nastavení zabezpečení pro vazbu SSL datového proudu.</span><span class="sxs-lookup"><span data-stu-id="42844-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="42844-156">Tento element je typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="42844-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|  
|[<span data-ttu-id="42844-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="42844-157">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="42844-158">Určuje, že vazba podporuje toku transakcí a protokol, který se použije `transactionProtocol` atribut.</span><span class="sxs-lookup"><span data-stu-id="42844-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="42844-159">Tento element je typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="42844-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|  
|[<span data-ttu-id="42844-160">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="42844-160">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="42844-161">Určuje možnosti pro streamování zabezpečení vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="42844-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="42844-162">Tento element je typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="42844-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42844-163">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="42844-163">Parent Elements</span></span>  
  
|<span data-ttu-id="42844-164">Prvek</span><span class="sxs-lookup"><span data-stu-id="42844-164">Element</span></span>|<span data-ttu-id="42844-165">Popis</span><span class="sxs-lookup"><span data-stu-id="42844-165">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42844-166">vazby</span><span class="sxs-lookup"><span data-stu-id="42844-166">bindings</span></span>|<span data-ttu-id="42844-167">Obsahuje všechny vazby pro aplikace Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="42844-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42844-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42844-168">Remarks</span></span>  
 <span data-ttu-id="42844-169">Vlastní vazby poskytují plnou kontrolu nad zásobníku zasílání zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="42844-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="42844-170">Speciální šité na míru vazeb se dá vytvořit Moje přidávání konfigurační prvky pro konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="42844-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="42844-171">Například můžete kombinovat uživatele `httpsTransport` části `reliableSession` části a `security` oddílu pro vytvoření spolehlivou a zabezpečenou https na základě vazby.</span><span class="sxs-lookup"><span data-stu-id="42844-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>  
  
 <span data-ttu-id="42844-172">Jednotlivé vazby definuje zásobníku zprávu zadáním konfigurační prvky pro prvky zásobníku v pořadí, ve kterém se objeví v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="42844-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="42844-173">Každý prvek definuje a konfiguruje jeden element zásobníku.</span><span class="sxs-lookup"><span data-stu-id="42844-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="42844-174">Každý vlastní vazby musí být pouze jeden element přenosu.</span><span class="sxs-lookup"><span data-stu-id="42844-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="42844-175">Bez tohoto elementu je nekompletní zasílání zpráv zásobníku.</span><span class="sxs-lookup"><span data-stu-id="42844-175">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="42844-176">Pořadí, ve kterém elementy zobrazují v zásobníku důležitý, protože je pořadí, ve kterém jsou použity operace ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="42844-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="42844-177">Doporučené pořadí elementů zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="42844-177">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="42844-178">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="42844-178">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="42844-179">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="42844-179">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="42844-180">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="42844-180">Security (optional)</span></span>  
  
4.  <span data-ttu-id="42844-181">Přenos</span><span class="sxs-lookup"><span data-stu-id="42844-181">Transport</span></span>  
  
5.  <span data-ttu-id="42844-182">Kodér (volitelné)</span><span class="sxs-lookup"><span data-stu-id="42844-182">Encoder (optional)</span></span>  
  
 <span data-ttu-id="42844-183">Použijte vlastní vazby, pokud jeden z vazby poskytované systémem nesplňuje požadavky vaší služby.</span><span class="sxs-lookup"><span data-stu-id="42844-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="42844-184">Vlastní vazby bylo možné použít, například povolení použití nový přenos nebo nové kodér na koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="42844-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>  
  
 <span data-ttu-id="42844-185">Vlastní vazby je vytvořený pomocí jedné z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekce elementů, které jsou "skládaný" v určitém pořadí vazby:</span><span class="sxs-lookup"><span data-stu-id="42844-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="42844-186">V horní části je volitelný <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> umožňuje toku transakcí.</span><span class="sxs-lookup"><span data-stu-id="42844-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="42844-187">Dále je volitelný <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> relaci a jak jsou definovány ve specifikaci WS-ReliableMessaging řazení mechanismus, který poskytuje.</span><span class="sxs-lookup"><span data-stu-id="42844-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="42844-188">Tato představu o relaci můžete křížová zprostředkovatele protokolu SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="42844-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="42844-189">Dále je element vazby volitelné zabezpečení, který poskytuje funkce zabezpečení, jako je ověřování, ověřování, ochrana a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="42844-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="42844-190">Jsou poskytovány následující prvky vazby zabezpečení [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="42844-190">The following security binding elements are provided by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   <span data-ttu-id="42844-191">Dále jsou volitelné zpráva vzory určené elementů vazby:</span><span class="sxs-lookup"><span data-stu-id="42844-191">Next are the optional message-patterns specified by binding elements:</span></span>  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   <span data-ttu-id="42844-192">Dále jsou volitelné přenosu upgrady nebo pomocné prvky vazeb:</span><span class="sxs-lookup"><span data-stu-id="42844-192">Next are the optional transport upgrades/helpers binding elements:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="42844-193">Dále je požadované zpráva kódování prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="42844-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="42844-194">Můžete použít vlastní přenos nebo použijte jednu z kódování vazby následující zpráva:</span><span class="sxs-lookup"><span data-stu-id="42844-194">You can use your own transport or use one of the following message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   <span data-ttu-id="42844-195">V dolní části je element požadované přenosu.</span><span class="sxs-lookup"><span data-stu-id="42844-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="42844-196">Můžete použít vlastní přenos nebo použijte jeden z elementů poskytované vazby přenosu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="42844-196">You can use your own transport or use one of transport binding elements provided by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 <span data-ttu-id="42844-197">Následující tabulka shrnuje možnosti pro jednotlivé úrovně.</span><span class="sxs-lookup"><span data-stu-id="42844-197">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="42844-198">Vrstva</span><span class="sxs-lookup"><span data-stu-id="42844-198">Layer</span></span>|<span data-ttu-id="42844-199">Možnosti</span><span class="sxs-lookup"><span data-stu-id="42844-199">Options</span></span>|<span data-ttu-id="42844-200">Požadováno</span><span class="sxs-lookup"><span data-stu-id="42844-200">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="42844-201">Tok transakcí</span><span class="sxs-lookup"><span data-stu-id="42844-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="42844-202">Ne</span><span class="sxs-lookup"><span data-stu-id="42844-202">No</span></span>|  
|<span data-ttu-id="42844-203">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="42844-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="42844-204">Ne</span><span class="sxs-lookup"><span data-stu-id="42844-204">No</span></span>|  
|<span data-ttu-id="42844-205">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42844-205">Security</span></span>|<span data-ttu-id="42844-206">Symetrické, asymetrické, transportní vrstvy</span><span class="sxs-lookup"><span data-stu-id="42844-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="42844-207">Ne</span><span class="sxs-lookup"><span data-stu-id="42844-207">No</span></span>|  
|<span data-ttu-id="42844-208">Změna tvaru</span><span class="sxs-lookup"><span data-stu-id="42844-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="42844-209">Ne</span><span class="sxs-lookup"><span data-stu-id="42844-209">No</span></span>|  
|<span data-ttu-id="42844-210">Upgrady přenosu</span><span class="sxs-lookup"><span data-stu-id="42844-210">Transport Upgrades</span></span>|<span data-ttu-id="42844-211">Datový proud protokolu SSL, Windows datového proudu, sdílené překladač</span><span class="sxs-lookup"><span data-stu-id="42844-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="42844-212">Ne</span><span class="sxs-lookup"><span data-stu-id="42844-212">No</span></span>|  
|<span data-ttu-id="42844-213">Kódování</span><span class="sxs-lookup"><span data-stu-id="42844-213">Encoding</span></span>|<span data-ttu-id="42844-214">Text, binární, MTOM, vlastní</span><span class="sxs-lookup"><span data-stu-id="42844-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="42844-215">Ano</span><span class="sxs-lookup"><span data-stu-id="42844-215">Yes</span></span>|  
|<span data-ttu-id="42844-216">Přenos</span><span class="sxs-lookup"><span data-stu-id="42844-216">Transport</span></span>|<span data-ttu-id="42844-217">TCP, pojmenované kanály protokolu HTTP, HTTPS, typů služby MSMQ, vlastní</span><span class="sxs-lookup"><span data-stu-id="42844-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="42844-218">Ano</span><span class="sxs-lookup"><span data-stu-id="42844-218">Yes</span></span>|  
  
 <span data-ttu-id="42844-219">Kromě toho můžete definovat vlastní prvky vazby a vložte je mezi některé z předchozích definované vrstvy.</span><span class="sxs-lookup"><span data-stu-id="42844-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
 <span data-ttu-id="42844-220">Informace o tom, jak používat vlastní vázání na Upravit vazby poskytované systémem, naleznete v [postupy: přizpůsobení vazbu System-Provided](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="42844-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
1.  
  
## <a name="see-also"></a><span data-ttu-id="42844-221">Viz také</span><span class="sxs-lookup"><span data-stu-id="42844-221">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="42844-222">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="42844-222">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="42844-223">Vazby</span><span class="sxs-lookup"><span data-stu-id="42844-223">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="42844-224">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="42844-224">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="42844-225">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="42844-225">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="42844-226">customBinding – Element</span><span class="sxs-lookup"><span data-stu-id="42844-226">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="42844-227">Vazby</span><span class="sxs-lookup"><span data-stu-id="42844-227">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="42844-228">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="42844-228">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="42844-229">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="42844-229">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
