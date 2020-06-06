---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: cdaaacf0dfa75209d001f6e8d6ac7175816048aa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140795"
---
# \<customBinding>

<span data-ttu-id="d6eb9-101">Poskytuje plnou kontrolu nad zásobníkem zpráv pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-101">Provides full control over the messaging stack for the user.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**  

## <a name="syntax"></a><span data-ttu-id="d6eb9-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6eb9-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="d6eb9-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6eb9-103">Attributes and Elements</span></span>

<span data-ttu-id="d6eb9-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-104">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="d6eb9-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6eb9-105">Attributes</span></span>

|<span data-ttu-id="d6eb9-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6eb9-106">Attribute</span></span>|<span data-ttu-id="d6eb9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d6eb9-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="d6eb9-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="d6eb9-108">closeTimeout</span></span>|<span data-ttu-id="d6eb9-109"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d6eb9-110">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d6eb9-111">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-111">The default is 00:01:00.</span></span>|
|<span data-ttu-id="d6eb9-112">name</span><span class="sxs-lookup"><span data-stu-id="d6eb9-112">name</span></span>|<span data-ttu-id="d6eb9-113">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-113">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d6eb9-114">Tato hodnota je uživatelem definovaný řetězec, který slouží jako identifikační řetězec pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-114">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="d6eb9-115">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-115">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d6eb9-116">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d6eb9-116">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="d6eb9-117">openTimeout</span><span class="sxs-lookup"><span data-stu-id="d6eb9-117">openTimeout</span></span>|<span data-ttu-id="d6eb9-118"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d6eb9-119">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d6eb9-120">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-120">The default is 00:01:00.</span></span>|
|<span data-ttu-id="d6eb9-121">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="d6eb9-121">receiveTimeout</span></span>|<span data-ttu-id="d6eb9-122"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d6eb9-123">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d6eb9-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="d6eb9-125">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="d6eb9-125">sendTimeout</span></span>|<span data-ttu-id="d6eb9-126"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d6eb9-127">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d6eb9-128">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-128">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d6eb9-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6eb9-129">Child Elements</span></span>

|<span data-ttu-id="d6eb9-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6eb9-130">Element</span></span>|<span data-ttu-id="d6eb9-131">Description</span><span class="sxs-lookup"><span data-stu-id="d6eb9-131">Description</span></span>|
|-------------|-----------------|
|[\<compositeDuplex>](compositeduplex.md)|<span data-ttu-id="d6eb9-132">Určuje obousměrný způsob zasílání zpráv do vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-132">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="d6eb9-133">Používá se s přenosy, které nativně neumožňují duplexní komunikaci, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-133">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="d6eb9-134">Protokol TCP naopak umožňuje nativně duplexní komunikaci nativně a nevyžaduje použití tohoto elementu vazby, aby služba odesílala zprávy zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-134">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="d6eb9-135">Klient musí vystavit adresu, aby mohla služba vytvořit kontakt a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-135">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="d6eb9-136">Tato adresa klienta je poskytována `ClientBaseAddress` atributem.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-136">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="d6eb9-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-137">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[\<pnrpPeerResolver>](pnrppeerresolver.md)|<span data-ttu-id="d6eb9-138">Určuje překladač názvů partnerských uzlů PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="d6eb9-138">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="d6eb9-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-139">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[\<reliableSession>](reliablesession.md)|<span data-ttu-id="d6eb9-140">Určuje nastavení pro zasílání zpráv WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-140">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="d6eb9-141">Když se tento prvek přidá do vlastní vazby, může výsledný kanál podporovat pouze zajištění doručení právě jednou.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-141">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="d6eb9-142">Tento prvek je typu <xref:System.ServiceModel.Configuration.ReliableSessionElement> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-142">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="d6eb9-143">Určuje možnosti pro zabezpečení vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-143">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="d6eb9-144">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-144">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[\<sslStreamSecurity>](sslstreamsecurity.md)|<span data-ttu-id="d6eb9-145">Určuje nastavení zabezpečení pro vazbu streamu SSL.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-145">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="d6eb9-146">Tento prvek je typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-146">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[\<transactionFlow>](transactionflow.md)|<span data-ttu-id="d6eb9-147">Určuje, že vazba podporuje tok transakce a protokol, který má `transactionProtocol` atribut použít.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-147">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="d6eb9-148">Tento prvek je typu <xref:System.ServiceModel.Configuration.TransactionFlowElement> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-148">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[\<windowsStreamSecurity>](windowsstreamsecurity.md)|<span data-ttu-id="d6eb9-149">Určuje možnosti pro zabezpečení streamování vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-149">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="d6eb9-150">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="d6eb9-150">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d6eb9-151">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6eb9-151">Parent Elements</span></span>

|<span data-ttu-id="d6eb9-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6eb9-152">Element</span></span>|<span data-ttu-id="d6eb9-153">Description</span><span class="sxs-lookup"><span data-stu-id="d6eb9-153">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="d6eb9-154">vazby</span><span class="sxs-lookup"><span data-stu-id="d6eb9-154">bindings</span></span>|<span data-ttu-id="d6eb9-155">Obsahuje všechny vazby pro aplikace Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-155">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d6eb9-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6eb9-156">Remarks</span></span>

<span data-ttu-id="d6eb9-157">Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-157">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="d6eb9-158">Speciální vazby, které lze přizpůsobit, lze vytvořit přidáním elementů konfigurace pro konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-158">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="d6eb9-159">Uživatel může například zkombinovat `httpsTransport` oddíl, `reliableSession` oddíl a `security` oddíl a vytvořit tak spolehlivou a zabezpečenou vazbu založenou na protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-159">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="d6eb9-160">Jednotlivá vazba definuje zásobník zpráv zadáním elementů konfigurace pro prvky zásobníku v pořadí, v jakém se zobrazují v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-160">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="d6eb9-161">Každý prvek definuje a nakonfiguruje jeden prvek zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-161">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="d6eb9-162">V každé vlastní vazbě musí být jeden a jenom jeden transportní element.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-162">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="d6eb9-163">Bez tohoto elementu je zásobník pro zasílání zpráv neúplný.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-163">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="d6eb9-164">Pořadí, ve kterém se prvky zobrazí v zásobníku, protože se jedná o pořadí, ve kterém jsou operace pro zprávu aplikovány.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-164">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="d6eb9-165">Doporučené pořadí prvků zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="d6eb9-165">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="d6eb9-166">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="d6eb9-166">Transactions (optional)</span></span>

2. <span data-ttu-id="d6eb9-167">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="d6eb9-167">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="d6eb9-168">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="d6eb9-168">Security (optional)</span></span>

4. <span data-ttu-id="d6eb9-169">Přenos</span><span class="sxs-lookup"><span data-stu-id="d6eb9-169">Transport</span></span>

5. <span data-ttu-id="d6eb9-170">Kodér (volitelné)</span><span class="sxs-lookup"><span data-stu-id="d6eb9-170">Encoder (optional)</span></span>

<span data-ttu-id="d6eb9-171">Vlastní vazbu použijte v případě, že jedna z vazeb poskytovaných systémem nesplňuje požadavky vaší služby.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-171">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="d6eb9-172">Vlastní vazbu můžete použít například k povolení použití nového přenosu nebo nového kodéru na koncovém bodu služby.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-172">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="d6eb9-173">Vlastní vazba je vytvořena pomocí jedné z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> kolekce prvků vazby, které jsou "skládané" v určitém pořadí:</span><span class="sxs-lookup"><span data-stu-id="d6eb9-173">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="d6eb9-174">V horní části je volitelná možnost <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , která umožňuje přesměrovat transakce.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-174">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="d6eb9-175">Další je volitelná <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> , která poskytuje mechanismus pro relaci a řazení, jak je definováno ve specifikaci WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-175">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="d6eb9-176">Tento pojem relace může přenášet propojení mezi zprostředkovateli SOAP a přenosu.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-176">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="d6eb9-177">Další je volitelný prvek vazby zabezpečení, který poskytuje funkce zabezpečení jako autorizaci, ověřování, ochranu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-177">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="d6eb9-178">Pomocí Windows Communication Foundation (WCF) jsou k dispozici následující prvky vazby zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="d6eb9-178">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="d6eb9-179">Dále jsou nepovinné vzory zpráv určené prvky vazby:</span><span class="sxs-lookup"><span data-stu-id="d6eb9-179">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="d6eb9-180">Dále jsou k dispozici volitelné upgrady přenosu/prvky vazby pomocníků:</span><span class="sxs-lookup"><span data-stu-id="d6eb9-180">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="d6eb9-181">Další je povinný element vazby kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-181">Next is a required message encoding binding element.</span></span> <span data-ttu-id="d6eb9-182">Můžete použít vlastní přenos nebo použít jednu z následujících vazeb kódování zpráv:</span><span class="sxs-lookup"><span data-stu-id="d6eb9-182">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="d6eb9-183">V dolní části je požadovaný transportní prvek.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-183">At the bottom is a required transport element.</span></span> <span data-ttu-id="d6eb9-184">Můžete použít vlastní přenos nebo použít jeden z elementů vazby přenosu poskytovaných Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="d6eb9-184">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="d6eb9-185">Následující tabulka shrnuje možnosti pro každou vrstvu.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-185">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="d6eb9-186">Vrstva</span><span class="sxs-lookup"><span data-stu-id="d6eb9-186">Layer</span></span>|<span data-ttu-id="d6eb9-187">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d6eb9-187">Options</span></span>|<span data-ttu-id="d6eb9-188">Vyžadováno</span><span class="sxs-lookup"><span data-stu-id="d6eb9-188">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="d6eb9-189">Tok transakce</span><span class="sxs-lookup"><span data-stu-id="d6eb9-189">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="d6eb9-190">No</span><span class="sxs-lookup"><span data-stu-id="d6eb9-190">No</span></span>|
|<span data-ttu-id="d6eb9-191">Spolehlivost</span><span class="sxs-lookup"><span data-stu-id="d6eb9-191">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="d6eb9-192">No</span><span class="sxs-lookup"><span data-stu-id="d6eb9-192">No</span></span>|
|<span data-ttu-id="d6eb9-193">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d6eb9-193">Security</span></span>|<span data-ttu-id="d6eb9-194">Symetrický, asymetrický, transportní úroveň</span><span class="sxs-lookup"><span data-stu-id="d6eb9-194">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="d6eb9-195">No</span><span class="sxs-lookup"><span data-stu-id="d6eb9-195">No</span></span>|
|<span data-ttu-id="d6eb9-196">Změna tvaru</span><span class="sxs-lookup"><span data-stu-id="d6eb9-196">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="d6eb9-197">No</span><span class="sxs-lookup"><span data-stu-id="d6eb9-197">No</span></span>|
|<span data-ttu-id="d6eb9-198">Upgrady přenosu</span><span class="sxs-lookup"><span data-stu-id="d6eb9-198">Transport Upgrades</span></span>|<span data-ttu-id="d6eb9-199">Datový proud SSL, Windows Stream, peer resolver</span><span class="sxs-lookup"><span data-stu-id="d6eb9-199">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="d6eb9-200">No</span><span class="sxs-lookup"><span data-stu-id="d6eb9-200">No</span></span>|
|<span data-ttu-id="d6eb9-201">Kódování</span><span class="sxs-lookup"><span data-stu-id="d6eb9-201">Encoding</span></span>|<span data-ttu-id="d6eb9-202">Text, binární, MTOM, vlastní</span><span class="sxs-lookup"><span data-stu-id="d6eb9-202">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="d6eb9-203">Yes</span><span class="sxs-lookup"><span data-stu-id="d6eb9-203">Yes</span></span>|
|<span data-ttu-id="d6eb9-204">Přenos</span><span class="sxs-lookup"><span data-stu-id="d6eb9-204">Transport</span></span>|<span data-ttu-id="d6eb9-205">TCP, pojmenované kanály, HTTP, HTTPS, charakter služby MSMQ, vlastní</span><span class="sxs-lookup"><span data-stu-id="d6eb9-205">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="d6eb9-206">Yes</span><span class="sxs-lookup"><span data-stu-id="d6eb9-206">Yes</span></span>|

<span data-ttu-id="d6eb9-207">Kromě toho můžete definovat vlastní prvky vazby a vkládat je mezi kteroukoli z předchozích definovaných vrstev.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-207">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="d6eb9-208">Diskuzi o tom, jak používat vlastní vazbu k úpravě vazby zadané systémem, najdete v tématu [How to: Customizing a bindingd a System-dodaná](../../../wcf/extending/how-to-customize-a-system-provided-binding.md)vazba.</span><span class="sxs-lookup"><span data-stu-id="d6eb9-208">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6eb9-209">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6eb9-209">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="d6eb9-210">Vazby</span><span class="sxs-lookup"><span data-stu-id="d6eb9-210">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d6eb9-211">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="d6eb9-211">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d6eb9-212">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d6eb9-212">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d6eb9-213">Element customBinding</span><span class="sxs-lookup"><span data-stu-id="d6eb9-213">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="d6eb9-214">Vazby</span><span class="sxs-lookup"><span data-stu-id="d6eb9-214">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d6eb9-215">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="d6eb9-215">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d6eb9-216">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d6eb9-216">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
