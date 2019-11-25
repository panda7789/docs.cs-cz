---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: cdaaacf0dfa75209d001f6e8d6ac7175816048aa
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140795"
---
# <a name="custombinding"></a><span data-ttu-id="83a94-101">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="83a94-101">\<customBinding></span></span>

<span data-ttu-id="83a94-102">Poskytuje plnou kontrolu nad zásobníkem zpráv pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="83a94-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="83a94-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="83a94-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="83a94-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="83a94-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="83a94-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="83a94-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="83a94-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customBinding >**</span><span class="sxs-lookup"><span data-stu-id="83a94-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="83a94-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83a94-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="83a94-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="83a94-108">Attributes and Elements</span></span>

<span data-ttu-id="83a94-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="83a94-109">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="83a94-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="83a94-110">Attributes</span></span>

|<span data-ttu-id="83a94-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="83a94-111">Attribute</span></span>|<span data-ttu-id="83a94-112">Popis</span><span class="sxs-lookup"><span data-stu-id="83a94-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="83a94-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="83a94-113">closeTimeout</span></span>|<span data-ttu-id="83a94-114">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="83a94-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="83a94-115">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="83a94-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="83a94-116">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="83a94-116">The default is 00:01:00.</span></span>|
|<span data-ttu-id="83a94-117">name</span><span class="sxs-lookup"><span data-stu-id="83a94-117">name</span></span>|<span data-ttu-id="83a94-118">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="83a94-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="83a94-119">Tato hodnota je uživatelem definovaný řetězec, který slouží jako identifikační řetězec pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="83a94-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="83a94-120">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="83a94-120">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="83a94-121">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="83a94-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="83a94-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="83a94-122">openTimeout</span></span>|<span data-ttu-id="83a94-123">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="83a94-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="83a94-124">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="83a94-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="83a94-125">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="83a94-125">The default is 00:01:00.</span></span>|
|<span data-ttu-id="83a94-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="83a94-126">receiveTimeout</span></span>|<span data-ttu-id="83a94-127">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="83a94-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="83a94-128">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="83a94-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="83a94-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="83a94-129">The default is 00:01:00.</span></span>|
|<span data-ttu-id="83a94-130">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="83a94-130">sendTimeout</span></span>|<span data-ttu-id="83a94-131">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="83a94-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="83a94-132">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="83a94-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="83a94-133">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="83a94-133">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="83a94-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="83a94-134">Child Elements</span></span>

|<span data-ttu-id="83a94-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="83a94-135">Element</span></span>|<span data-ttu-id="83a94-136">Popis</span><span class="sxs-lookup"><span data-stu-id="83a94-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83a94-137">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="83a94-137">\<compositeDuplex></span></span>](compositeduplex.md)|<span data-ttu-id="83a94-138">Určuje obousměrný způsob zasílání zpráv do vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="83a94-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="83a94-139">Používá se s přenosy, které nativně neumožňují duplexní komunikaci, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="83a94-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="83a94-140">Protokol TCP naopak umožňuje nativně duplexní komunikaci nativně a nevyžaduje použití tohoto elementu vazby, aby služba odesílala zprávy zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="83a94-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="83a94-141">Klient musí vystavit adresu, aby mohla služba vytvořit kontakt a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="83a94-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="83a94-142">Tato adresa klienta je poskytována atributem `ClientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="83a94-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="83a94-143">Tento prvek je typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="83a94-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="83a94-144">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="83a94-144">\<pnrpPeerResolver></span></span>](pnrppeerresolver.md)|<span data-ttu-id="83a94-145">Určuje překladač názvů partnerských uzlů PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="83a94-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="83a94-146">Tento prvek je typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="83a94-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="83a94-147">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="83a94-147">\<reliableSession></span></span>](reliablesession.md)|<span data-ttu-id="83a94-148">Určuje nastavení pro zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="83a94-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="83a94-149">Když se tento prvek přidá do vlastní vazby, může výsledný kanál podporovat pouze zajištění doručení právě jednou.</span><span class="sxs-lookup"><span data-stu-id="83a94-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="83a94-150">Tento prvek je typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="83a94-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="83a94-151">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="83a94-151">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="83a94-152">Určuje možnosti pro zabezpečení vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="83a94-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="83a94-153">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="83a94-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="83a94-154">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="83a94-154">\<sslStreamSecurity></span></span>](sslstreamsecurity.md)|<span data-ttu-id="83a94-155">Určuje nastavení zabezpečení pro vazbu streamu SSL.</span><span class="sxs-lookup"><span data-stu-id="83a94-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="83a94-156">Tento prvek je typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="83a94-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="83a94-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="83a94-157">\<transactionFlow></span></span>](transactionflow.md)|<span data-ttu-id="83a94-158">Určuje, že vazba podporuje tok transakce a protokol, který má atribut `transactionProtocol` použít.</span><span class="sxs-lookup"><span data-stu-id="83a94-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="83a94-159">Tento prvek je typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="83a94-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="83a94-160">\<zabezpečení windowsstreamsecurity ></span><span class="sxs-lookup"><span data-stu-id="83a94-160">\<windowsStreamSecurity></span></span>](windowsstreamsecurity.md)|<span data-ttu-id="83a94-161">Určuje možnosti pro zabezpečení streamování vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="83a94-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="83a94-162">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="83a94-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="83a94-163">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="83a94-163">Parent Elements</span></span>

|<span data-ttu-id="83a94-164">Prvek</span><span class="sxs-lookup"><span data-stu-id="83a94-164">Element</span></span>|<span data-ttu-id="83a94-165">Popis</span><span class="sxs-lookup"><span data-stu-id="83a94-165">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="83a94-166">vazby</span><span class="sxs-lookup"><span data-stu-id="83a94-166">bindings</span></span>|<span data-ttu-id="83a94-167">Obsahuje všechny vazby pro aplikace Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="83a94-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="83a94-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83a94-168">Remarks</span></span>

<span data-ttu-id="83a94-169">Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="83a94-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="83a94-170">Speciální vazby, které lze přizpůsobit, lze vytvořit přidáním elementů konfigurace pro konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="83a94-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="83a94-171">Uživatel může například kombinovat oddíl `httpsTransport`, `reliableSession` oddíl a `security` oddíl a vytvořit tak spolehlivou a zabezpečenou vazbu založenou na protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="83a94-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="83a94-172">Jednotlivá vazba definuje zásobník zpráv zadáním elementů konfigurace pro prvky zásobníku v pořadí, v jakém se zobrazují v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="83a94-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="83a94-173">Každý prvek definuje a nakonfiguruje jeden prvek zásobníku.</span><span class="sxs-lookup"><span data-stu-id="83a94-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="83a94-174">V každé vlastní vazbě musí být jeden a jenom jeden transportní element.</span><span class="sxs-lookup"><span data-stu-id="83a94-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="83a94-175">Bez tohoto elementu je zásobník pro zasílání zpráv neúplný.</span><span class="sxs-lookup"><span data-stu-id="83a94-175">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="83a94-176">Pořadí, ve kterém se prvky zobrazí v zásobníku, protože se jedná o pořadí, ve kterém jsou operace pro zprávu aplikovány.</span><span class="sxs-lookup"><span data-stu-id="83a94-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="83a94-177">Doporučené pořadí prvků zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="83a94-177">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="83a94-178">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="83a94-178">Transactions (optional)</span></span>

2. <span data-ttu-id="83a94-179">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="83a94-179">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="83a94-180">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="83a94-180">Security (optional)</span></span>

4. <span data-ttu-id="83a94-181">Přepravu</span><span class="sxs-lookup"><span data-stu-id="83a94-181">Transport</span></span>

5. <span data-ttu-id="83a94-182">Kodér (volitelné)</span><span class="sxs-lookup"><span data-stu-id="83a94-182">Encoder (optional)</span></span>

<span data-ttu-id="83a94-183">Vlastní vazbu použijte v případě, že jedna z vazeb poskytovaných systémem nesplňuje požadavky vaší služby.</span><span class="sxs-lookup"><span data-stu-id="83a94-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="83a94-184">Vlastní vazbu můžete použít například k povolení použití nového přenosu nebo nového kodéru na koncovém bodu služby.</span><span class="sxs-lookup"><span data-stu-id="83a94-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="83a94-185">Vlastní vazba je vytvořena pomocí jedné z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekce prvků vazby, které jsou "skládané" v určitém pořadí:</span><span class="sxs-lookup"><span data-stu-id="83a94-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="83a94-186">V horní části je volitelná <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, která umožňuje přesměrovat transakce.</span><span class="sxs-lookup"><span data-stu-id="83a94-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="83a94-187">Dále je volitelná <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>, která poskytuje mechanismus pro relaci a řazení, jak je definováno ve specifikaci WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="83a94-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="83a94-188">Tento pojem relace může přenášet propojení mezi zprostředkovateli SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="83a94-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="83a94-189">Další je volitelný prvek vazby zabezpečení, který poskytuje funkce zabezpečení jako autorizaci, ověřování, ochranu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="83a94-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="83a94-190">Pomocí Windows Communication Foundation (WCF) jsou k dispozici následující prvky vazby zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="83a94-190">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="83a94-191">Dále jsou nepovinné vzory zpráv určené prvky vazby:</span><span class="sxs-lookup"><span data-stu-id="83a94-191">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="83a94-192">Dále jsou k dispozici volitelné upgrady přenosu/prvky vazby pomocníků:</span><span class="sxs-lookup"><span data-stu-id="83a94-192">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="83a94-193">Další je povinný element vazby kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="83a94-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="83a94-194">Můžete použít vlastní přenos nebo použít jednu z následujících vazeb kódování zpráv:</span><span class="sxs-lookup"><span data-stu-id="83a94-194">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="83a94-195">V dolní části je požadovaný transportní prvek.</span><span class="sxs-lookup"><span data-stu-id="83a94-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="83a94-196">Můžete použít vlastní přenos nebo použít jeden z elementů vazby přenosu poskytovaných Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="83a94-196">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="83a94-197">Následující tabulka shrnuje možnosti pro každou vrstvu.</span><span class="sxs-lookup"><span data-stu-id="83a94-197">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="83a94-198">Vrstvení</span><span class="sxs-lookup"><span data-stu-id="83a94-198">Layer</span></span>|<span data-ttu-id="83a94-199">Možnosti</span><span class="sxs-lookup"><span data-stu-id="83a94-199">Options</span></span>|<span data-ttu-id="83a94-200">Požadováno</span><span class="sxs-lookup"><span data-stu-id="83a94-200">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="83a94-201">Tok transakce</span><span class="sxs-lookup"><span data-stu-id="83a94-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="83a94-202">Ne</span><span class="sxs-lookup"><span data-stu-id="83a94-202">No</span></span>|
|<span data-ttu-id="83a94-203">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="83a94-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="83a94-204">Ne</span><span class="sxs-lookup"><span data-stu-id="83a94-204">No</span></span>|
|<span data-ttu-id="83a94-205">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="83a94-205">Security</span></span>|<span data-ttu-id="83a94-206">Symetrický, asymetrický, transportní úroveň</span><span class="sxs-lookup"><span data-stu-id="83a94-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="83a94-207">Ne</span><span class="sxs-lookup"><span data-stu-id="83a94-207">No</span></span>|
|<span data-ttu-id="83a94-208">Změna tvaru</span><span class="sxs-lookup"><span data-stu-id="83a94-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="83a94-209">Ne</span><span class="sxs-lookup"><span data-stu-id="83a94-209">No</span></span>|
|<span data-ttu-id="83a94-210">Upgrady přenosu</span><span class="sxs-lookup"><span data-stu-id="83a94-210">Transport Upgrades</span></span>|<span data-ttu-id="83a94-211">Datový proud SSL, Windows Stream, peer resolver</span><span class="sxs-lookup"><span data-stu-id="83a94-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="83a94-212">Ne</span><span class="sxs-lookup"><span data-stu-id="83a94-212">No</span></span>|
|<span data-ttu-id="83a94-213">Kódování</span><span class="sxs-lookup"><span data-stu-id="83a94-213">Encoding</span></span>|<span data-ttu-id="83a94-214">Text, binární, MTOM, vlastní</span><span class="sxs-lookup"><span data-stu-id="83a94-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="83a94-215">Ano</span><span class="sxs-lookup"><span data-stu-id="83a94-215">Yes</span></span>|
|<span data-ttu-id="83a94-216">Přepravu</span><span class="sxs-lookup"><span data-stu-id="83a94-216">Transport</span></span>|<span data-ttu-id="83a94-217">TCP, pojmenované kanály, HTTP, HTTPS, charakter služby MSMQ, vlastní</span><span class="sxs-lookup"><span data-stu-id="83a94-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="83a94-218">Ano</span><span class="sxs-lookup"><span data-stu-id="83a94-218">Yes</span></span>|

<span data-ttu-id="83a94-219">Kromě toho můžete definovat vlastní prvky vazby a vkládat je mezi kteroukoli z předchozích definovaných vrstev.</span><span class="sxs-lookup"><span data-stu-id="83a94-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="83a94-220">Diskuzi o tom, jak používat vlastní vazbu k úpravě vazby zadané systémem, najdete v tématu [How to: Customizing a bindingd a System-dodaná](../../../wcf/extending/how-to-customize-a-system-provided-binding.md)vazba.</span><span class="sxs-lookup"><span data-stu-id="83a94-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83a94-221">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83a94-221">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="83a94-222">vazba \<</span><span class="sxs-lookup"><span data-stu-id="83a94-222">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="83a94-223">Vazby</span><span class="sxs-lookup"><span data-stu-id="83a94-223">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="83a94-224">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="83a94-224">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="83a94-225">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="83a94-225">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="83a94-226">Element customBinding</span><span class="sxs-lookup"><span data-stu-id="83a94-226">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="83a94-227">Vazby</span><span class="sxs-lookup"><span data-stu-id="83a94-227">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="83a94-228">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="83a94-228">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="83a94-229">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="83a94-229">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
