---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 0b6f26c7b9e9d02b3ff20b53f42b09d671699ea5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919381"
---
# <a name="custombinding"></a><span data-ttu-id="2fc8c-101">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2fc8c-101">\<customBinding></span></span>

<span data-ttu-id="2fc8c-102">Poskytuje plnou kontrolu nad zásobníkem zpráv pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="2fc8c-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2fc8c-103">\<system.serviceModel></span></span>\
<span data-ttu-id="2fc8c-104">\<vazby > </span><span class="sxs-lookup"><span data-stu-id="2fc8c-104">\<bindings></span></span>\
<span data-ttu-id="2fc8c-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2fc8c-105">\<customBinding></span></span>

## <a name="syntax"></a><span data-ttu-id="2fc8c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fc8c-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="2fc8c-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2fc8c-107">Attributes and Elements</span></span>

<span data-ttu-id="2fc8c-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="2fc8c-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="2fc8c-109">Attributes</span></span>

|<span data-ttu-id="2fc8c-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="2fc8c-110">Attribute</span></span>|<span data-ttu-id="2fc8c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="2fc8c-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="2fc8c-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="2fc8c-112">closeTimeout</span></span>|<span data-ttu-id="2fc8c-113"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="2fc8c-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2fc8c-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-115">The default is 00:01:00.</span></span>|
|<span data-ttu-id="2fc8c-116">name</span><span class="sxs-lookup"><span data-stu-id="2fc8c-116">name</span></span>|<span data-ttu-id="2fc8c-117">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-117">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="2fc8c-118">Tato hodnota je uživatelem definovaný řetězec, který slouží jako identifikační řetězec pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-118">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="2fc8c-119">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2fc8c-120">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2fc8c-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="2fc8c-121">openTimeout</span><span class="sxs-lookup"><span data-stu-id="2fc8c-121">openTimeout</span></span>|<span data-ttu-id="2fc8c-122"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="2fc8c-123">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2fc8c-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="2fc8c-125">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="2fc8c-125">receiveTimeout</span></span>|<span data-ttu-id="2fc8c-126"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="2fc8c-127">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2fc8c-128">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-128">The default is 00:01:00.</span></span>|
|<span data-ttu-id="2fc8c-129">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="2fc8c-129">sendTimeout</span></span>|<span data-ttu-id="2fc8c-130"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="2fc8c-131">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2fc8c-132">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-132">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2fc8c-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2fc8c-133">Child Elements</span></span>

|<span data-ttu-id="2fc8c-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="2fc8c-134">Element</span></span>|<span data-ttu-id="2fc8c-135">Popis</span><span class="sxs-lookup"><span data-stu-id="2fc8c-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fc8c-136">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="2fc8c-136">\<compositeDuplex></span></span>](compositeduplex.md)|<span data-ttu-id="2fc8c-137">Určuje obousměrný způsob zasílání zpráv do vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-137">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="2fc8c-138">Používá se s přenosy, které nativně neumožňují duplexní komunikaci, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-138">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="2fc8c-139">Protokol TCP naopak umožňuje nativně duplexní komunikaci nativně a nevyžaduje použití tohoto elementu vazby, aby služba odesílala zprávy zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-139">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="2fc8c-140">Klient musí vystavit adresu, aby mohla služba vytvořit kontakt a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-140">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="2fc8c-141">Tato adresa klienta je poskytována `ClientBaseAddress` atributem.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-141">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="2fc8c-142">Tento prvek je typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-142">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="2fc8c-143">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="2fc8c-143">\<pnrpPeerResolver></span></span>](pnrppeerresolver.md)|<span data-ttu-id="2fc8c-144">Určuje překladač názvů partnerských uzlů PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="2fc8c-144">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="2fc8c-145">Tento prvek je typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-145">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="2fc8c-146">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="2fc8c-146">\<reliableSession></span></span>](reliablesession.md)|<span data-ttu-id="2fc8c-147">Určuje nastavení pro zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-147">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="2fc8c-148">Když se tento prvek přidá do vlastní vazby, může výsledný kanál podporovat pouze zajištění doručení právě jednou.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-148">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="2fc8c-149">Tento prvek je typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-149">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="2fc8c-150">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2fc8c-150">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="2fc8c-151">Určuje možnosti pro zabezpečení vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-151">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="2fc8c-152">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-152">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="2fc8c-153">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="2fc8c-153">\<sslStreamSecurity></span></span>](sslstreamsecurity.md)|<span data-ttu-id="2fc8c-154">Určuje nastavení zabezpečení pro vazbu streamu SSL.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-154">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="2fc8c-155">Tento prvek je typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-155">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="2fc8c-156">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="2fc8c-156">\<transactionFlow></span></span>](transactionflow.md)|<span data-ttu-id="2fc8c-157">Určuje, že vazba podporuje tok transakce a protokol, který má `transactionProtocol` atribut použít.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-157">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="2fc8c-158">Tento prvek je typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-158">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="2fc8c-159">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="2fc8c-159">\<windowsStreamSecurity></span></span>](windowsstreamsecurity.md)|<span data-ttu-id="2fc8c-160">Určuje možnosti pro zabezpečení streamování vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-160">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="2fc8c-161">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-161">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2fc8c-162">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2fc8c-162">Parent Elements</span></span>

|<span data-ttu-id="2fc8c-163">Prvek</span><span class="sxs-lookup"><span data-stu-id="2fc8c-163">Element</span></span>|<span data-ttu-id="2fc8c-164">Popis</span><span class="sxs-lookup"><span data-stu-id="2fc8c-164">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="2fc8c-165">vazby</span><span class="sxs-lookup"><span data-stu-id="2fc8c-165">bindings</span></span>|<span data-ttu-id="2fc8c-166">Obsahuje všechny vazby pro aplikace Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-166">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2fc8c-167">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fc8c-167">Remarks</span></span>

<span data-ttu-id="2fc8c-168">Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-168">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="2fc8c-169">Speciální vazby, které lze přizpůsobit, lze vytvořit přidáním elementů konfigurace pro konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-169">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="2fc8c-170">Uživatel může například zkombinovat `httpsTransport` oddíl, `reliableSession` oddíl a `security` oddíl a vytvořit tak spolehlivou a zabezpečenou vazbu založenou na protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-170">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="2fc8c-171">Jednotlivá vazba definuje zásobník zpráv zadáním elementů konfigurace pro prvky zásobníku v pořadí, v jakém se zobrazují v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-171">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="2fc8c-172">Každý prvek definuje a nakonfiguruje jeden prvek zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-172">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="2fc8c-173">V každé vlastní vazbě musí být jeden a jenom jeden transportní element.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-173">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="2fc8c-174">Bez tohoto elementu je zásobník pro zasílání zpráv neúplný.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-174">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="2fc8c-175">Pořadí, ve kterém se prvky zobrazí v zásobníku, protože se jedná o pořadí, ve kterém jsou operace pro zprávu aplikovány.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-175">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="2fc8c-176">Doporučené pořadí prvků zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="2fc8c-176">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="2fc8c-177">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="2fc8c-177">Transactions (optional)</span></span>

2. <span data-ttu-id="2fc8c-178">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="2fc8c-178">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="2fc8c-179">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="2fc8c-179">Security (optional)</span></span>

4. <span data-ttu-id="2fc8c-180">Přepravu</span><span class="sxs-lookup"><span data-stu-id="2fc8c-180">Transport</span></span>

5. <span data-ttu-id="2fc8c-181">Kodér (volitelné)</span><span class="sxs-lookup"><span data-stu-id="2fc8c-181">Encoder (optional)</span></span>

<span data-ttu-id="2fc8c-182">Vlastní vazbu použijte v případě, že jedna z vazeb poskytovaných systémem nesplňuje požadavky vaší služby.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-182">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="2fc8c-183">Vlastní vazbu můžete použít například k povolení použití nového přenosu nebo nového kodéru na koncovém bodu služby.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-183">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="2fc8c-184">Vlastní vazba je vytvořena pomocí jedné <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekce prvků vazby, které jsou "skládané" v určitém pořadí:</span><span class="sxs-lookup"><span data-stu-id="2fc8c-184">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="2fc8c-185">V horní části je volitelná <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> možnost, která umožňuje přesměrovat transakce.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-185">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="2fc8c-186">Další je volitelná <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> , která poskytuje mechanismus pro relaci a řazení, jak je definováno ve specifikaci WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-186">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="2fc8c-187">Tento pojem relace může přenášet propojení mezi zprostředkovateli SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-187">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="2fc8c-188">Další je volitelný prvek vazby zabezpečení, který poskytuje funkce zabezpečení jako autorizaci, ověřování, ochranu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-188">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="2fc8c-189">Pomocí Windows Communication Foundation (WCF) jsou k dispozici následující prvky vazby zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="2fc8c-189">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="2fc8c-190">Dále jsou nepovinné vzory zpráv určené prvky vazby:</span><span class="sxs-lookup"><span data-stu-id="2fc8c-190">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="2fc8c-191">Dále jsou k dispozici volitelné upgrady přenosu/prvky vazby pomocníků:</span><span class="sxs-lookup"><span data-stu-id="2fc8c-191">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="2fc8c-192">Další je povinný element vazby kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-192">Next is a required message encoding binding element.</span></span> <span data-ttu-id="2fc8c-193">Můžete použít vlastní přenos nebo použít jednu z následujících vazeb kódování zpráv:</span><span class="sxs-lookup"><span data-stu-id="2fc8c-193">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="2fc8c-194">V dolní části je požadovaný transportní prvek.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-194">At the bottom is a required transport element.</span></span> <span data-ttu-id="2fc8c-195">Můžete použít vlastní přenos nebo použít jeden z elementů vazby přenosu poskytovaných Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="2fc8c-195">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="2fc8c-196">Následující tabulka shrnuje možnosti pro každou vrstvu.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-196">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="2fc8c-197">Vrstva</span><span class="sxs-lookup"><span data-stu-id="2fc8c-197">Layer</span></span>|<span data-ttu-id="2fc8c-198">Možnosti</span><span class="sxs-lookup"><span data-stu-id="2fc8c-198">Options</span></span>|<span data-ttu-id="2fc8c-199">Požadováno</span><span class="sxs-lookup"><span data-stu-id="2fc8c-199">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="2fc8c-200">Tok transakce</span><span class="sxs-lookup"><span data-stu-id="2fc8c-200">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="2fc8c-201">Ne</span><span class="sxs-lookup"><span data-stu-id="2fc8c-201">No</span></span>|
|<span data-ttu-id="2fc8c-202">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="2fc8c-202">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="2fc8c-203">Ne</span><span class="sxs-lookup"><span data-stu-id="2fc8c-203">No</span></span>|
|<span data-ttu-id="2fc8c-204">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2fc8c-204">Security</span></span>|<span data-ttu-id="2fc8c-205">Symetrický, asymetrický, transportní úroveň</span><span class="sxs-lookup"><span data-stu-id="2fc8c-205">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="2fc8c-206">Ne</span><span class="sxs-lookup"><span data-stu-id="2fc8c-206">No</span></span>|
|<span data-ttu-id="2fc8c-207">Změna tvaru</span><span class="sxs-lookup"><span data-stu-id="2fc8c-207">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="2fc8c-208">Ne</span><span class="sxs-lookup"><span data-stu-id="2fc8c-208">No</span></span>|
|<span data-ttu-id="2fc8c-209">Upgrady přenosu</span><span class="sxs-lookup"><span data-stu-id="2fc8c-209">Transport Upgrades</span></span>|<span data-ttu-id="2fc8c-210">Datový proud SSL, Windows Stream, peer resolver</span><span class="sxs-lookup"><span data-stu-id="2fc8c-210">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="2fc8c-211">Ne</span><span class="sxs-lookup"><span data-stu-id="2fc8c-211">No</span></span>|
|<span data-ttu-id="2fc8c-212">Kódování</span><span class="sxs-lookup"><span data-stu-id="2fc8c-212">Encoding</span></span>|<span data-ttu-id="2fc8c-213">Text, binární, MTOM, vlastní</span><span class="sxs-lookup"><span data-stu-id="2fc8c-213">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="2fc8c-214">Ano</span><span class="sxs-lookup"><span data-stu-id="2fc8c-214">Yes</span></span>|
|<span data-ttu-id="2fc8c-215">Přepravu</span><span class="sxs-lookup"><span data-stu-id="2fc8c-215">Transport</span></span>|<span data-ttu-id="2fc8c-216">TCP, pojmenované kanály, HTTP, HTTPS, charakter služby MSMQ, vlastní</span><span class="sxs-lookup"><span data-stu-id="2fc8c-216">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="2fc8c-217">Ano</span><span class="sxs-lookup"><span data-stu-id="2fc8c-217">Yes</span></span>|

<span data-ttu-id="2fc8c-218">Kromě toho můžete definovat vlastní prvky vazby a vkládat je mezi kteroukoli z předchozích definovaných vrstev.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-218">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="2fc8c-219">Diskuzi o tom, jak používat vlastní vazbu k úpravě vazby poskytované systémem, najdete v tématu [How to: Přizpůsobení vazby](../../../wcf/extending/how-to-customize-a-system-provided-binding.md)poskytnuté systémem.</span><span class="sxs-lookup"><span data-stu-id="2fc8c-219">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2fc8c-220">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fc8c-220">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2fc8c-221">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="2fc8c-221">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="2fc8c-222">Vazby</span><span class="sxs-lookup"><span data-stu-id="2fc8c-222">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2fc8c-223">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="2fc8c-223">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2fc8c-224">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="2fc8c-224">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2fc8c-225">Element customBinding</span><span class="sxs-lookup"><span data-stu-id="2fc8c-225">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="2fc8c-226">Vazby</span><span class="sxs-lookup"><span data-stu-id="2fc8c-226">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2fc8c-227">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="2fc8c-227">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2fc8c-228">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2fc8c-228">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
