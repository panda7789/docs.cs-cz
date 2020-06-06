---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 0a77c791d55c6009cf59d5a4b15f3b2a63b7ccf9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140470"
---
# \<wsFederationHttpBinding>

<span data-ttu-id="bda30-101">Definuje vazbu, která podporuje WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="bda30-101">Defines a binding that supports WS-Federation.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**  

## <a name="syntax"></a><span data-ttu-id="bda30-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bda30-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="bda30-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bda30-103">Attributes and Elements</span></span>

<span data-ttu-id="bda30-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bda30-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bda30-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="bda30-105">Attributes</span></span>

|<span data-ttu-id="bda30-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="bda30-106">Attribute</span></span>|<span data-ttu-id="bda30-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bda30-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="bda30-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="bda30-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="bda30-109">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="bda30-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="bda30-110">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="bda30-110">The default is `false`.</span></span>|
|<span data-ttu-id="bda30-111">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="bda30-111">closeTimeout</span></span>|<span data-ttu-id="bda30-112"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="bda30-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bda30-113">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bda30-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bda30-114">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bda30-114">The default is 00:01:00.</span></span>|
|<span data-ttu-id="bda30-115">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="bda30-115">hostnameComparisonMode</span></span>|<span data-ttu-id="bda30-116">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="bda30-116">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="bda30-117">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode> , který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="bda30-117">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="bda30-118">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="bda30-118">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="bda30-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="bda30-119">maxBufferPoolSize</span></span>|<span data-ttu-id="bda30-120">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="bda30-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="bda30-121">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="bda30-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="bda30-122">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bda30-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="bda30-123">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="bda30-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="bda30-124">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="bda30-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="bda30-125">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="bda30-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="bda30-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="bda30-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="bda30-127">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="bda30-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="bda30-128">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="bda30-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="bda30-129">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="bda30-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="bda30-130">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="bda30-130">The default is 65536.</span></span>|
|<span data-ttu-id="bda30-131">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="bda30-131">messageEncoding</span></span>|<span data-ttu-id="bda30-132">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="bda30-132">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="bda30-133">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="bda30-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bda30-134">-Text: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="bda30-134">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="bda30-135">-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).</span><span class="sxs-lookup"><span data-stu-id="bda30-135">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="bda30-136">Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="bda30-136">The default is Text.</span></span><br /><br /> <span data-ttu-id="bda30-137">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="bda30-137">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="bda30-138">name</span><span class="sxs-lookup"><span data-stu-id="bda30-138">name</span></span>|<span data-ttu-id="bda30-139">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="bda30-139">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bda30-140">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="bda30-140">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bda30-141">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="bda30-141">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bda30-142">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bda30-142">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="bda30-143">openTimeout</span><span class="sxs-lookup"><span data-stu-id="bda30-143">openTimeout</span></span>|<span data-ttu-id="bda30-144"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="bda30-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bda30-145">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bda30-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bda30-146">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bda30-146">The default is 00:01:00.</span></span>|
|<span data-ttu-id="bda30-147">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="bda30-147">privacyNoticeAt</span></span>|<span data-ttu-id="bda30-148">Řetězec, který určuje identifikátor URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="bda30-148">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="bda30-149">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="bda30-149">privacyNoticeVersion</span></span>|<span data-ttu-id="bda30-150">Celé číslo, které určuje verzi stávajícího oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="bda30-150">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="bda30-151">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="bda30-151">proxyAddress</span></span>|<span data-ttu-id="bda30-152">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="bda30-152">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="bda30-153">Pokud `useDefaultWebProxy` má `true` parametr hodnotu, musí být toto nastavení `null` .</span><span class="sxs-lookup"><span data-stu-id="bda30-153">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="bda30-154">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="bda30-154">The default is `null`.</span></span>|
|<span data-ttu-id="bda30-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="bda30-155">receiveTimeout</span></span>|<span data-ttu-id="bda30-156"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="bda30-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bda30-157">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bda30-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bda30-158">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="bda30-158">The default is 00:10:00.</span></span>|
|<span data-ttu-id="bda30-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="bda30-159">sendTimeout</span></span>|<span data-ttu-id="bda30-160"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="bda30-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bda30-161">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="bda30-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bda30-162">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bda30-162">The default is 00:01:00.</span></span>|
|<span data-ttu-id="bda30-163">textEncoding</span><span class="sxs-lookup"><span data-stu-id="bda30-163">textEncoding</span></span>|<span data-ttu-id="bda30-164">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="bda30-164">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="bda30-165">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="bda30-165">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bda30-166">-BigEndianUnicode: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="bda30-166">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="bda30-167">-Unicode: 16 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="bda30-167">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="bda30-168">-UTF8:8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="bda30-168">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="bda30-169">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="bda30-169">The default is UTF8.</span></span> <span data-ttu-id="bda30-170">Tento atribut je typu <xref:System.Text.Encoding> ..</span><span class="sxs-lookup"><span data-stu-id="bda30-170">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="bda30-171">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="bda30-171">transactionFlow</span></span>|<span data-ttu-id="bda30-172">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="bda30-172">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="bda30-173">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="bda30-173">The default is `false`.</span></span>|
|<span data-ttu-id="bda30-174">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="bda30-174">useDefaultWebProxy</span></span>|<span data-ttu-id="bda30-175">Logická hodnota, která označuje, zda je použit automaticky konfigurovaný proxy server HTTP.</span><span class="sxs-lookup"><span data-stu-id="bda30-175">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="bda30-176">Adresa proxy serveru musí být `null` (tj. není nastavena), pokud je tento atribut `true` .</span><span class="sxs-lookup"><span data-stu-id="bda30-176">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="bda30-177">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="bda30-177">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bda30-178">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bda30-178">Child Elements</span></span>

|<span data-ttu-id="bda30-179">Prvek</span><span class="sxs-lookup"><span data-stu-id="bda30-179">Element</span></span>|<span data-ttu-id="bda30-180">Description</span><span class="sxs-lookup"><span data-stu-id="bda30-180">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="bda30-181">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="bda30-181">Defines the security settings for the message.</span></span> <span data-ttu-id="bda30-182">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="bda30-182">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="bda30-183">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="bda30-183">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="bda30-184">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="bda30-184">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="bda30-185">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="bda30-185">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bda30-186">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bda30-186">Parent Elements</span></span>

|<span data-ttu-id="bda30-187">Prvek</span><span class="sxs-lookup"><span data-stu-id="bda30-187">Element</span></span>|<span data-ttu-id="bda30-188">Description</span><span class="sxs-lookup"><span data-stu-id="bda30-188">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="bda30-189">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="bda30-189">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bda30-190">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bda30-190">Remarks</span></span>

<span data-ttu-id="bda30-191">Federace je schopnost sdílet identity v různých systémech pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="bda30-191">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="bda30-192">Tyto identity můžou odkazovat na uživatele nebo na počítače.</span><span class="sxs-lookup"><span data-stu-id="bda30-192">These identities can refer to users or to machines.</span></span> <span data-ttu-id="bda30-193">Federované HTTP podporuje zabezpečení SOAP i zabezpečení ve smíšeném režimu, ale nepodporuje výhradně použití zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="bda30-193">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="bda30-194">Tato vazba poskytuje podporu Windows Communication Foundation (WCF) pro protokol WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="bda30-194">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="bda30-195">Služby nakonfigurované s touto vazbou musí používat přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="bda30-195">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="bda30-196">Vazby se skládají z zásobníku prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="bda30-196">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="bda30-197">Zásobník prvků vazby v</span><span class="sxs-lookup"><span data-stu-id="bda30-197">The stack of binding elements in</span></span>

<span data-ttu-id="bda30-198">`wsFederationHttpBinding`je stejná jako ta, která je obsažena v`wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="bda30-198">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="bda30-199">Když [\<security>](security-of-wsfederationhttpbinding.md) je nastavená na výchozí hodnotu <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> .</span><span class="sxs-lookup"><span data-stu-id="bda30-199">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="bda30-200">`wsFederationHttpBinding`Řídí podrobné informace o nastavení zabezpečení zpráv v [\<message>](message-element-of-wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="bda30-200">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="bda30-201">Všimněte si, že [\<security>](security-of-wsfederationhttpbinding.md) element poskytuje přístup získat pouze v případě, že zabezpečení, které je použito vazbou, nelze změnit poté, co je vytvořena vazba.</span><span class="sxs-lookup"><span data-stu-id="bda30-201">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="bda30-202">`wsFederationHttpBinding`Poskytuje také atribut privacyNoticeAt pro nastavení a načtení identifikátoru URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="bda30-202">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="bda30-203">Zachování zabezpečení zásad je obzvláště důležité ve federačních scénářích.</span><span class="sxs-lookup"><span data-stu-id="bda30-203">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="bda30-204">Doporučením je použití určité formy zabezpečení, jako je například HTTPS, k ochraně zásad před uživateli se zlými úmysly.</span><span class="sxs-lookup"><span data-stu-id="bda30-204">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="bda30-205">V federačních scénářích využívajících tuto vazbu může zásada služby potenciálně mít důležité informace, jako je klíč, který se má použít k šifrování vydaného tokenu (SAML), typu deklarací, které mají být do tokenu vloženy, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="bda30-205">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="bda30-206">Pokud je tato zásada úmyslně poškozená, útočník by mohl najít klíč vydaného tokenu, který vede k dalšímu falšování, zpřístupnění informací a k dalšímu škodlivému chování.</span><span class="sxs-lookup"><span data-stu-id="bda30-206">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="bda30-207">Aby k tomu nedocházelo, musí být zásada zabezpečená (například pomocí HTTPS) ze služby.</span><span class="sxs-lookup"><span data-stu-id="bda30-207">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="bda30-208">Další informace o této vazbě naleznete v tématu [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bda30-208">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="bda30-209">Příklad</span><span class="sxs-lookup"><span data-stu-id="bda30-209">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bda30-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="bda30-210">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="bda30-211">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="bda30-211">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="bda30-212">Vazby</span><span class="sxs-lookup"><span data-stu-id="bda30-212">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bda30-213">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="bda30-213">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bda30-214">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bda30-214">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
