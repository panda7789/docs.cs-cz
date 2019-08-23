---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 3c4edc17fd669fbe23ec38ff26a61e867c04c561
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915072"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="c4110-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c4110-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="c4110-102">Definuje vazbu, která podporuje WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="c4110-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="c4110-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c4110-103">\<system.ServiceModel></span></span>\
<span data-ttu-id="c4110-104">\<vazby > </span><span class="sxs-lookup"><span data-stu-id="c4110-104">\<bindings></span></span>\
<span data-ttu-id="c4110-105">wsFederationBinding – element</span><span class="sxs-lookup"><span data-stu-id="c4110-105">wsFederationBinding element</span></span>

## <a name="syntax"></a><span data-ttu-id="c4110-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4110-106">Syntax</span></span>

```xml
<wsFederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsFederationBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4110-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c4110-107">Attributes and Elements</span></span>

<span data-ttu-id="c4110-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c4110-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4110-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="c4110-109">Attributes</span></span>

|<span data-ttu-id="c4110-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="c4110-110">Attribute</span></span>|<span data-ttu-id="c4110-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c4110-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c4110-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="c4110-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="c4110-113">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="c4110-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="c4110-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="c4110-114">The default is `false`.</span></span>|
|<span data-ttu-id="c4110-115">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="c4110-115">closeTimeout</span></span>|<span data-ttu-id="c4110-116"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="c4110-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c4110-117">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c4110-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c4110-118">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c4110-118">The default is 00:01:00.</span></span>|
|<span data-ttu-id="c4110-119">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c4110-119">hostnameComparisonMode</span></span>|<span data-ttu-id="c4110-120">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="c4110-120">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="c4110-121">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="c4110-121">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="c4110-122">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="c4110-122">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="c4110-123">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c4110-123">maxBufferPoolSize</span></span>|<span data-ttu-id="c4110-124">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="c4110-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="c4110-125">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="c4110-125">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="c4110-126">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c4110-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="c4110-127">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="c4110-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="c4110-128">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="c4110-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="c4110-129">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="c4110-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="c4110-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c4110-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="c4110-131">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="c4110-131">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="c4110-132">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c4110-132">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="c4110-133">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="c4110-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="c4110-134">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="c4110-134">The default is 65536.</span></span>|
|<span data-ttu-id="c4110-135">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="c4110-135">messageEncoding</span></span>|<span data-ttu-id="c4110-136">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="c4110-136">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="c4110-137">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="c4110-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c4110-138">Textové Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c4110-138">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="c4110-139">Maximální Použijte kodér 1,0 (pro organizaci přenosu zpráv).</span><span class="sxs-lookup"><span data-stu-id="c4110-139">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="c4110-140">Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="c4110-140">The default is Text.</span></span><br /><br /> <span data-ttu-id="c4110-141">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="c4110-141">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="c4110-142">name</span><span class="sxs-lookup"><span data-stu-id="c4110-142">name</span></span>|<span data-ttu-id="c4110-143">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="c4110-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="c4110-144">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="c4110-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c4110-145">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="c4110-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c4110-146">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c4110-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="c4110-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="c4110-147">openTimeout</span></span>|<span data-ttu-id="c4110-148"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="c4110-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c4110-149">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c4110-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c4110-150">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c4110-150">The default is 00:01:00.</span></span>|
|<span data-ttu-id="c4110-151">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="c4110-151">privacyNoticeAt</span></span>|<span data-ttu-id="c4110-152">Řetězec, který určuje identifikátor URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="c4110-152">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="c4110-153">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="c4110-153">privacyNoticeVersion</span></span>|<span data-ttu-id="c4110-154">Celé číslo, které určuje verzi stávajícího oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="c4110-154">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="c4110-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="c4110-155">proxyAddress</span></span>|<span data-ttu-id="c4110-156">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="c4110-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="c4110-157">Pokud `useDefaultWebProxy` má `true`parametr hodnotu, musí být `null`toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="c4110-157">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="c4110-158">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="c4110-158">The default is `null`.</span></span>|
|<span data-ttu-id="c4110-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="c4110-159">receiveTimeout</span></span>|<span data-ttu-id="c4110-160"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="c4110-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c4110-161">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c4110-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c4110-162">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="c4110-162">The default is 00:10:00.</span></span>|
|<span data-ttu-id="c4110-163">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="c4110-163">sendTimeout</span></span>|<span data-ttu-id="c4110-164"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="c4110-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c4110-165">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c4110-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c4110-166">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c4110-166">The default is 00:01:00.</span></span>|
|<span data-ttu-id="c4110-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="c4110-167">textEncoding</span></span>|<span data-ttu-id="c4110-168">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="c4110-168">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="c4110-169">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="c4110-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c4110-170">- BigEndianUnicode: Kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="c4110-170">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="c4110-171">Sady 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="c4110-171">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="c4110-172">-   UTF8: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="c4110-172">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="c4110-173">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="c4110-173">The default is UTF8.</span></span> <span data-ttu-id="c4110-174">Tento atribut je typu <xref:System.Text.Encoding>..</span><span class="sxs-lookup"><span data-stu-id="c4110-174">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="c4110-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="c4110-175">transactionFlow</span></span>|<span data-ttu-id="c4110-176">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="c4110-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="c4110-177">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="c4110-177">The default is `false`.</span></span>|
|<span data-ttu-id="c4110-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="c4110-178">useDefaultWebProxy</span></span>|<span data-ttu-id="c4110-179">Logická hodnota, která označuje, zda je použit automaticky konfigurovaný proxy server HTTP.</span><span class="sxs-lookup"><span data-stu-id="c4110-179">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="c4110-180">Adresa proxy serveru musí být `null` (tj. není nastavena), pokud je `true`tento atribut.</span><span class="sxs-lookup"><span data-stu-id="c4110-180">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="c4110-181">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="c4110-181">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c4110-182">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c4110-182">Child Elements</span></span>

|<span data-ttu-id="c4110-183">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4110-183">Element</span></span>|<span data-ttu-id="c4110-184">Popis</span><span class="sxs-lookup"><span data-stu-id="c4110-184">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4110-185">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c4110-185">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="c4110-186">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="c4110-186">Defines the security settings for the message.</span></span> <span data-ttu-id="c4110-187">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="c4110-187">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="c4110-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c4110-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="c4110-189">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="c4110-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c4110-190">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="c4110-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="c4110-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c4110-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="c4110-192">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="c4110-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c4110-193">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c4110-193">Parent Elements</span></span>

|<span data-ttu-id="c4110-194">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4110-194">Element</span></span>|<span data-ttu-id="c4110-195">Popis</span><span class="sxs-lookup"><span data-stu-id="c4110-195">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4110-196">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="c4110-196">\<bindings></span></span>](bindings.md)|<span data-ttu-id="c4110-197">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="c4110-197">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4110-198">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4110-198">Remarks</span></span>

<span data-ttu-id="c4110-199">Federace je schopnost sdílet identity v různých systémech pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="c4110-199">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="c4110-200">Tyto identity můžou odkazovat na uživatele nebo na počítače.</span><span class="sxs-lookup"><span data-stu-id="c4110-200">These identities can refer to users or to machines.</span></span> <span data-ttu-id="c4110-201">Federované HTTP podporuje zabezpečení SOAP i zabezpečení ve smíšeném režimu, ale nepodporuje výhradně použití zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="c4110-201">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="c4110-202">Tato vazba poskytuje podporu Windows Communication Foundation (WCF) pro protokol WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="c4110-202">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="c4110-203">Služby nakonfigurované s touto vazbou musí používat přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="c4110-203">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="c4110-204">Vazby se skládají z zásobníku prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="c4110-204">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="c4110-205">Zásobník prvků vazby v</span><span class="sxs-lookup"><span data-stu-id="c4110-205">The stack of binding elements in</span></span>

<span data-ttu-id="c4110-206">`wsFederationHttpBinding`je stejná jako ta, která je obsažena v`wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="c4110-206">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="c4110-207"><xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>Pokud [ \<je zabezpečení >](security-of-wsfederationhttpbinding.md) nastaveno na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4110-207">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="c4110-208">Určuje podrobnosti o nastavení zabezpečení zpráv ve [ \<zprávě >.](message-element-of-wsfederationhttpbinding.md) `wsFederationHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="c4110-208">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="c4110-209">Všimněte si, že [ \<element Security >](security-of-wsfederationhttpbinding.md) poskytuje přístup pouze v případě, že zabezpečení, které je použito vazbou, nelze změnit po vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="c4110-209">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="c4110-210">Poskytuje `wsFederationHttpBinding` také atribut privacyNoticeAt pro nastavení a načtení identifikátoru URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="c4110-210">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="c4110-211">Zachování zabezpečení zásad je obzvláště důležité ve federačních scénářích.</span><span class="sxs-lookup"><span data-stu-id="c4110-211">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="c4110-212">Doporučením je použití určité formy zabezpečení, jako je například HTTPS, k ochraně zásad před uživateli se zlými úmysly.</span><span class="sxs-lookup"><span data-stu-id="c4110-212">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="c4110-213">V federačních scénářích využívajících tuto vazbu může zásada služby potenciálně mít důležité informace, jako je klíč, který se má použít k šifrování vydaného tokenu (SAML), typu deklarací, které mají být do tokenu vloženy, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c4110-213">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="c4110-214">Pokud je tato zásada úmyslně poškozená, útočník by mohl najít klíč vydaného tokenu, který vede k dalšímu falšování, zpřístupnění informací a k dalšímu škodlivému chování.</span><span class="sxs-lookup"><span data-stu-id="c4110-214">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="c4110-215">Aby k tomu nedocházelo, musí být zásada zabezpečená (například pomocí HTTPS) ze služby.</span><span class="sxs-lookup"><span data-stu-id="c4110-215">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="c4110-216">Další informace o této vazbě naleznete v [tématu How to: Vytvořte WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c4110-216">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="c4110-217">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4110-217">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="saml"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </wsFederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c4110-218">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4110-218">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="c4110-219">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c4110-219">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="c4110-220">Vazby</span><span class="sxs-lookup"><span data-stu-id="c4110-220">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c4110-221">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="c4110-221">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c4110-222">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c4110-222">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c4110-223">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="c4110-223">\<binding></span></span>](../../../misc/binding.md)
