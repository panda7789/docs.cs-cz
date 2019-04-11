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
# <a name="custombinding"></a><span data-ttu-id="acad1-101">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="acad1-101">\<customBinding></span></span>

<span data-ttu-id="acad1-102">Poskytuje plnou kontrolu nad zásobníkem zpráv pro daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="acad1-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="acad1-103">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="acad1-103">\<system.serviceModel>\\</span></span>
<span data-ttu-id="acad1-104">\<vazby > \\</span><span class="sxs-lookup"><span data-stu-id="acad1-104">\<bindings>\\</span></span>
<span data-ttu-id="acad1-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="acad1-105">\<customBinding></span></span>

## <a name="syntax"></a><span data-ttu-id="acad1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acad1-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="acad1-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="acad1-107">Attributes and Elements</span></span>

<span data-ttu-id="acad1-108">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="acad1-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="acad1-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="acad1-109">Attributes</span></span>

|<span data-ttu-id="acad1-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="acad1-110">Attribute</span></span>|<span data-ttu-id="acad1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="acad1-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="acad1-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="acad1-112">closeTimeout</span></span>|<span data-ttu-id="acad1-113">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="acad1-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="acad1-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="acad1-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="acad1-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="acad1-115">The default is 00:01:00.</span></span>|
|<span data-ttu-id="acad1-116">name</span><span class="sxs-lookup"><span data-stu-id="acad1-116">name</span></span>|<span data-ttu-id="acad1-117">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="acad1-117">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="acad1-118">Tato hodnota je uživatelem definovaný řetězec, který funguje jako identifikační řetězec pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="acad1-118">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="acad1-119">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="acad1-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="acad1-120">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="acad1-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="acad1-121">openTimeout</span><span class="sxs-lookup"><span data-stu-id="acad1-121">openTimeout</span></span>|<span data-ttu-id="acad1-122">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="acad1-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="acad1-123">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="acad1-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="acad1-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="acad1-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="acad1-125">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="acad1-125">receiveTimeout</span></span>|<span data-ttu-id="acad1-126">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="acad1-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="acad1-127">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="acad1-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="acad1-128">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="acad1-128">The default is 00:01:00.</span></span>|
|<span data-ttu-id="acad1-129">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="acad1-129">sendTimeout</span></span>|<span data-ttu-id="acad1-130">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="acad1-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="acad1-131">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="acad1-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="acad1-132">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="acad1-132">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="acad1-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="acad1-133">Child Elements</span></span>

|<span data-ttu-id="acad1-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="acad1-134">Element</span></span>|<span data-ttu-id="acad1-135">Popis</span><span class="sxs-lookup"><span data-stu-id="acad1-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="acad1-136">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="acad1-136">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="acad1-137">Určuje obousměrný zasílání zpráv pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="acad1-137">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="acad1-138">Používá se s přenosy, které neumožňují duplexní komunikaci nativně, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="acad1-138">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="acad1-139">TCP, naopak umožňuje nativně duplexní komunikaci a nevyžaduje použití tohoto elementu vazby pro služby umožňující odesílání zpráv zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="acad1-139">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="acad1-140">Klient musí vystavit adresu pro službu kontaktovat a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="acad1-140">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="acad1-141">Tato adresa klienta poskytuje `ClientBaseAddress` atribut.</span><span class="sxs-lookup"><span data-stu-id="acad1-141">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="acad1-142">Tento prvek je typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="acad1-142">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="acad1-143">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="acad1-143">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="acad1-144">Určuje mechanismus rozpoznávání partnera název řešení protokolu PNRP (Peer Name).</span><span class="sxs-lookup"><span data-stu-id="acad1-144">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="acad1-145">Tento prvek je typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="acad1-145">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="acad1-146">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="acad1-146">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="acad1-147">Určuje nastavení pro zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="acad1-147">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="acad1-148">Pokud tento prvek přidán na vlastní vazby, výsledný kanálu může podporovat přesně-jednou záruky doručení.</span><span class="sxs-lookup"><span data-stu-id="acad1-148">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="acad1-149">Tento prvek je typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="acad1-149">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="acad1-150">\<security></span><span class="sxs-lookup"><span data-stu-id="acad1-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="acad1-151">Určuje možnosti pro zabezpečení vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="acad1-151">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="acad1-152">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="acad1-152">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="acad1-153">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="acad1-153">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="acad1-154">Určuje nastavení zabezpečení pro datový proud vazby SSL.</span><span class="sxs-lookup"><span data-stu-id="acad1-154">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="acad1-155">Tento prvek je typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="acad1-155">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="acad1-156">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="acad1-156">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="acad1-157">Určuje, že vazba podporuje tok transakcí a protokol, který se použije `transactionProtocol` atribut.</span><span class="sxs-lookup"><span data-stu-id="acad1-157">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="acad1-158">Tento prvek je typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="acad1-158">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="acad1-159">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="acad1-159">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="acad1-160">Určuje možnosti pro datový proud zabezpečení vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="acad1-160">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="acad1-161">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="acad1-161">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="acad1-162">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="acad1-162">Parent Elements</span></span>

|<span data-ttu-id="acad1-163">Prvek</span><span class="sxs-lookup"><span data-stu-id="acad1-163">Element</span></span>|<span data-ttu-id="acad1-164">Popis</span><span class="sxs-lookup"><span data-stu-id="acad1-164">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="acad1-165">vazby</span><span class="sxs-lookup"><span data-stu-id="acad1-165">bindings</span></span>|<span data-ttu-id="acad1-166">Obsahuje všechny vazby pro aplikace Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="acad1-166">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="acad1-167">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acad1-167">Remarks</span></span>

<span data-ttu-id="acad1-168">Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="acad1-168">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="acad1-169">Speciální míru vazby je možné vytvořit Moje Přidání elementů konfigurace pro konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="acad1-169">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="acad1-170">Například můžete kombinovat uživatele `httpsTransport` části `reliableSession` oddílu a `security` část, která vytvoří spolehlivou a zabezpečenou https na základě vazby.</span><span class="sxs-lookup"><span data-stu-id="acad1-170">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="acad1-171">Jednotlivé vazby definuje zásobníku zprávu zadáním elementů konfigurace pro zásobník prvky v pořadí, ve kterém se zobrazují v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="acad1-171">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="acad1-172">Každý prvek definuje a konfiguruje jeden prvek zásobníku.</span><span class="sxs-lookup"><span data-stu-id="acad1-172">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="acad1-173">Každá vlastní vazby musí být jeden a pouze jeden element přenosu.</span><span class="sxs-lookup"><span data-stu-id="acad1-173">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="acad1-174">Bez tohoto elementu je neúplný zásobníkem zpráv.</span><span class="sxs-lookup"><span data-stu-id="acad1-174">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="acad1-175">Je důležité pořadí, v jakém jsou prvky uvedeny v zásobníku, protože je pořadí použití operace u zprávy.</span><span class="sxs-lookup"><span data-stu-id="acad1-175">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="acad1-176">Doporučené pořadí elementů zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="acad1-176">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="acad1-177">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="acad1-177">Transactions (optional)</span></span>

2. <span data-ttu-id="acad1-178">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="acad1-178">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="acad1-179">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="acad1-179">Security (optional)</span></span>

4. <span data-ttu-id="acad1-180">Přenos</span><span class="sxs-lookup"><span data-stu-id="acad1-180">Transport</span></span>

5. <span data-ttu-id="acad1-181">Kodér (volitelné)</span><span class="sxs-lookup"><span data-stu-id="acad1-181">Encoder (optional)</span></span>

<span data-ttu-id="acad1-182">Použijte vlastní vazby, pokud jedna z vazeb poskytovaných systémem nesplňuje požadavky vaší služby.</span><span class="sxs-lookup"><span data-stu-id="acad1-182">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="acad1-183">Vlastní vazby může použít, například umožní použít nový přenos nebo nový kodér na koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="acad1-183">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="acad1-184">Vlastní vazby je vytvořená pomocí jedné z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekce vazby prvky, které jsou "skládaný" v určitém pořadí:</span><span class="sxs-lookup"><span data-stu-id="acad1-184">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="acad1-185">V horní části je volitelný <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , která umožňuje toku transakce.</span><span class="sxs-lookup"><span data-stu-id="acad1-185">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="acad1-186">Dále je volitelný <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> relaci a jak je definováno ve specifikaci WS-ReliableMessaging řazení mechanismus, který poskytuje.</span><span class="sxs-lookup"><span data-stu-id="acad1-186">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="acad1-187">Tento pojem relace můžete různé zprostředkovatele protokolu SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="acad1-187">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="acad1-188">Dále je element volitelný zabezpečení vazby, která poskytuje funkce zabezpečení, jako je ověřování, ověřování, ochrany a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="acad1-188">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="acad1-189">Následující elementy vazby zabezpečení jsou k dispozici ve Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="acad1-189">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="acad1-190">Dále jsou volitelné vzory zprávy určené elementů vazby:</span><span class="sxs-lookup"><span data-stu-id="acad1-190">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="acad1-191">Dále jsou upgrady/pomocné rutiny nepovinný přenosu elementů vazby:</span><span class="sxs-lookup"><span data-stu-id="acad1-191">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="acad1-192">Dále je element vazby kódování zprávy vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="acad1-192">Next is a required message encoding binding element.</span></span> <span data-ttu-id="acad1-193">Můžete použít vlastní přenos nebo použijte jednu z následujících vazby kódování zprávy:</span><span class="sxs-lookup"><span data-stu-id="acad1-193">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="acad1-194">V dolní části je prvek vyžaduje přenos.</span><span class="sxs-lookup"><span data-stu-id="acad1-194">At the bottom is a required transport element.</span></span> <span data-ttu-id="acad1-195">Můžete použít vlastní přenos nebo použijte jednu z přenosu, k dispozici ve Windows Communication Foundation (WCF) elementů vazby:</span><span class="sxs-lookup"><span data-stu-id="acad1-195">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="acad1-196">Následující tabulka shrnuje možnosti pro každou vrstvu.</span><span class="sxs-lookup"><span data-stu-id="acad1-196">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="acad1-197">Vrstva</span><span class="sxs-lookup"><span data-stu-id="acad1-197">Layer</span></span>|<span data-ttu-id="acad1-198">Možnosti</span><span class="sxs-lookup"><span data-stu-id="acad1-198">Options</span></span>|<span data-ttu-id="acad1-199">Požadováno</span><span class="sxs-lookup"><span data-stu-id="acad1-199">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="acad1-200">Tok transakcí</span><span class="sxs-lookup"><span data-stu-id="acad1-200">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="acad1-201">Ne</span><span class="sxs-lookup"><span data-stu-id="acad1-201">No</span></span>|
|<span data-ttu-id="acad1-202">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="acad1-202">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="acad1-203">Ne</span><span class="sxs-lookup"><span data-stu-id="acad1-203">No</span></span>|
|<span data-ttu-id="acad1-204">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="acad1-204">Security</span></span>|<span data-ttu-id="acad1-205">Symetrické, asymetrické, transportní vrstvy</span><span class="sxs-lookup"><span data-stu-id="acad1-205">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="acad1-206">Ne</span><span class="sxs-lookup"><span data-stu-id="acad1-206">No</span></span>|
|<span data-ttu-id="acad1-207">Změna tvaru</span><span class="sxs-lookup"><span data-stu-id="acad1-207">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="acad1-208">Ne</span><span class="sxs-lookup"><span data-stu-id="acad1-208">No</span></span>|
|<span data-ttu-id="acad1-209">Upgrady přenosu</span><span class="sxs-lookup"><span data-stu-id="acad1-209">Transport Upgrades</span></span>|<span data-ttu-id="acad1-210">Datového proudu protokolu SSL, datového proudu Windows, rozpoznávání partnera</span><span class="sxs-lookup"><span data-stu-id="acad1-210">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="acad1-211">Ne</span><span class="sxs-lookup"><span data-stu-id="acad1-211">No</span></span>|
|<span data-ttu-id="acad1-212">Kódování</span><span class="sxs-lookup"><span data-stu-id="acad1-212">Encoding</span></span>|<span data-ttu-id="acad1-213">Text, binární soubor, MTOM, vlastní</span><span class="sxs-lookup"><span data-stu-id="acad1-213">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="acad1-214">Ano</span><span class="sxs-lookup"><span data-stu-id="acad1-214">Yes</span></span>|
|<span data-ttu-id="acad1-215">Přenos</span><span class="sxs-lookup"><span data-stu-id="acad1-215">Transport</span></span>|<span data-ttu-id="acad1-216">Charakteristikami HTTP, HTTPS, TCP, pojmenovaných kanálů služby MSMQ, vlastní</span><span class="sxs-lookup"><span data-stu-id="acad1-216">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="acad1-217">Ano</span><span class="sxs-lookup"><span data-stu-id="acad1-217">Yes</span></span>|

<span data-ttu-id="acad1-218">Kromě toho můžete definovat vlastní elementy vazby a vložit mezi všechny předchozí definované vrstvy.</span><span class="sxs-lookup"><span data-stu-id="acad1-218">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="acad1-219">Informace o tom, jak použít vlastní vazby k úpravě vazeb poskytovaných systémem, najdete v článku [jak: Přizpůsobení vazeb poskytovaných systémem](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="acad1-219">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acad1-220">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acad1-220">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="acad1-221">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="acad1-221">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="acad1-222">Vazby</span><span class="sxs-lookup"><span data-stu-id="acad1-222">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="acad1-223">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="acad1-223">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="acad1-224">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="acad1-224">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="acad1-225">třídě customBinding – Element</span><span class="sxs-lookup"><span data-stu-id="acad1-225">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="acad1-226">Vazby</span><span class="sxs-lookup"><span data-stu-id="acad1-226">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="acad1-227">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="acad1-227">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="acad1-228">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="acad1-228">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
