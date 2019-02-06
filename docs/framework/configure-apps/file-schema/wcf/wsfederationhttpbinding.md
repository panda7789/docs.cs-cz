---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 834f2830d4b9ab33b65b39c772790e8d45e4b111
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759642"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="580c5-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="580c5-101">\<wsFederationHttpBinding></span></span>
<span data-ttu-id="580c5-102">Definuje vazbu, která podporuje WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="580c5-102">Defines a binding that supports WS-Federation.</span></span>  
  
 <span data-ttu-id="580c5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="580c5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="580c5-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="580c5-104">\<bindings></span></span>  
<span data-ttu-id="580c5-105">wsFederationBinding – element</span><span class="sxs-lookup"><span data-stu-id="580c5-105">wsFederationBinding element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="580c5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="580c5-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="580c5-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="580c5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="580c5-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="580c5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="580c5-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="580c5-109">Attributes</span></span>  
  
|<span data-ttu-id="580c5-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="580c5-110">Attribute</span></span>|<span data-ttu-id="580c5-111">Popis</span><span class="sxs-lookup"><span data-stu-id="580c5-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="580c5-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="580c5-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="580c5-113">Logická hodnota určující, zda obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="580c5-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="580c5-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="580c5-114">The default is `false`.</span></span>|  
|<span data-ttu-id="580c5-115">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="580c5-115">closeTimeout</span></span>|<span data-ttu-id="580c5-116">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="580c5-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="580c5-117">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="580c5-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="580c5-118">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="580c5-118">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="580c5-119">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="580c5-119">hostnameComparisonMode</span></span>|<span data-ttu-id="580c5-120">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="580c5-120">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="580c5-121">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="580c5-121">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="580c5-122">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="580c5-122">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="580c5-123">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="580c5-123">maxBufferPoolSize</span></span>|<span data-ttu-id="580c5-124">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="580c5-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="580c5-125">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="580c5-125">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="580c5-126">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="580c5-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="580c5-127">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="580c5-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="580c5-128">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="580c5-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="580c5-129">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="580c5-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="580c5-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="580c5-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="580c5-131">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="580c5-131">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="580c5-132">Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="580c5-132">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="580c5-133">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="580c5-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="580c5-134">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="580c5-134">The default is 65536.</span></span>|  
|<span data-ttu-id="580c5-135">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="580c5-135">messageEncoding</span></span>|<span data-ttu-id="580c5-136">Definuje kodér pro kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="580c5-136">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="580c5-137">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="580c5-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="580c5-138">-Text: Použijte kodér textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="580c5-138">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="580c5-139">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="580c5-139">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="580c5-140">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="580c5-140">The default is Text.</span></span><br /><br /> <span data-ttu-id="580c5-141">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="580c5-141">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="580c5-142">name</span><span class="sxs-lookup"><span data-stu-id="580c5-142">name</span></span>|<span data-ttu-id="580c5-143">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="580c5-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="580c5-144">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="580c5-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="580c5-145">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="580c5-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="580c5-146">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="580c5-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="580c5-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="580c5-147">openTimeout</span></span>|<span data-ttu-id="580c5-148">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="580c5-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="580c5-149">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="580c5-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="580c5-150">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="580c5-150">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="580c5-151">privactyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="580c5-151">privactyNoticeAt</span></span>|<span data-ttu-id="580c5-152">Řetězec určující identifikátor URI, ve kterém je umístěno oznámení soukromí.</span><span class="sxs-lookup"><span data-stu-id="580c5-152">A String that specifies a URI at which the privacy notice is located.</span></span>|  
|<span data-ttu-id="580c5-153">privactyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="580c5-153">privactyNoticeVersion</span></span>|<span data-ttu-id="580c5-154">Celé číslo, které určuje verzi aktuální oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="580c5-154">An integer that specifies the version of the current privacy notice.</span></span>|  
|<span data-ttu-id="580c5-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="580c5-155">proxyAddress</span></span>|<span data-ttu-id="580c5-156">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="580c5-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="580c5-157">Pokud `useDefaultWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="580c5-157">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="580c5-158">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="580c5-158">The default is `null`.</span></span>|  
|<span data-ttu-id="580c5-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="580c5-159">receiveTimeout</span></span>|<span data-ttu-id="580c5-160">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="580c5-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="580c5-161">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="580c5-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="580c5-162">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="580c5-162">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="580c5-163">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="580c5-163">sendTimeout</span></span>|<span data-ttu-id="580c5-164">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="580c5-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="580c5-165">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="580c5-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="580c5-166">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="580c5-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="580c5-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="580c5-167">textEncoding</span></span>|<span data-ttu-id="580c5-168">Nastaví znakovou sadu kódování, které má být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="580c5-168">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="580c5-169">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="580c5-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="580c5-170">-BigEndianUnicode: Kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="580c5-170">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="580c5-171">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="580c5-171">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="580c5-172">-   UTF8: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="580c5-172">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="580c5-173">Použije se UTF8.</span><span class="sxs-lookup"><span data-stu-id="580c5-173">The default is UTF8.</span></span> <span data-ttu-id="580c5-174">Tento atribut je typu <xref:System.Text.Encoding>...</span><span class="sxs-lookup"><span data-stu-id="580c5-174">This attribute is of type <xref:System.Text.Encoding>..</span></span>|  
|<span data-ttu-id="580c5-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="580c5-175">transactionFlow</span></span>|<span data-ttu-id="580c5-176">Logická hodnota určující, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="580c5-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="580c5-177">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="580c5-177">The default is `false`.</span></span>|  
|<span data-ttu-id="580c5-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="580c5-178">useDefaultWebProxy</span></span>|<span data-ttu-id="580c5-179">Logická hodnota, která určuje, jestli se používá v systému automaticky nakonfigurovaný proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="580c5-179">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="580c5-180">Adresa proxy musí být `null` (to znamená, není nastavený) Pokud tento atribut je `true`.</span><span class="sxs-lookup"><span data-stu-id="580c5-180">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="580c5-181">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="580c5-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="580c5-182">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="580c5-182">Child Elements</span></span>  
  
|<span data-ttu-id="580c5-183">Prvek</span><span class="sxs-lookup"><span data-stu-id="580c5-183">Element</span></span>|<span data-ttu-id="580c5-184">Popis</span><span class="sxs-lookup"><span data-stu-id="580c5-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="580c5-185">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="580c5-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="580c5-186">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="580c5-186">Defines the security settings for the message.</span></span> <span data-ttu-id="580c5-187">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="580c5-187">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="580c5-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="580c5-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="580c5-189">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="580c5-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="580c5-190">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="580c5-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="580c5-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="580c5-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="580c5-192">Určuje, pokud jsou mezi koncovými body kanál navázat spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="580c5-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="580c5-193">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="580c5-193">Parent Elements</span></span>  
  
|<span data-ttu-id="580c5-194">Prvek</span><span class="sxs-lookup"><span data-stu-id="580c5-194">Element</span></span>|<span data-ttu-id="580c5-195">Popis</span><span class="sxs-lookup"><span data-stu-id="580c5-195">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="580c5-196">\<bindings></span><span class="sxs-lookup"><span data-stu-id="580c5-196">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="580c5-197">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="580c5-197">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="580c5-198">Poznámky</span><span class="sxs-lookup"><span data-stu-id="580c5-198">Remarks</span></span>  
 <span data-ttu-id="580c5-199">Federace se nachází taky možnost podělit identity mezi různými systémy pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="580c5-199">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="580c5-200">Pro uživatele nebo počítače mohou odkazovat tyto identity.</span><span class="sxs-lookup"><span data-stu-id="580c5-200">These identities can refer to users or to machines.</span></span> <span data-ttu-id="580c5-201">Federované HTTP podporuje zabezpečení protokolu SOAP, stejně jako ve smíšeném režimu zabezpečení, ale nepodporuje výhradně pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="580c5-201">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="580c5-202">Tato vazba poskytuje podporu Windows Communication Foundation (WCF) pro protokol WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="580c5-202">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="580c5-203">Nakonfigurované s touto vazbou služby musíte použít přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="580c5-203">Services configured with this binding must use the HTTP transport.</span></span>  
  
 <span data-ttu-id="580c5-204">Vazby se skládají z více elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="580c5-204">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="580c5-205">Sadu elementů v vazby</span><span class="sxs-lookup"><span data-stu-id="580c5-205">The stack of binding elements in</span></span>  
  
 <span data-ttu-id="580c5-206">`wsFederationHttpBinding` je stejný jako součástí `wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="580c5-206">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>  
  
 <span data-ttu-id="580c5-207">Když [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) je nastavena na výchozí hodnotu <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="580c5-207">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>  
  
 <span data-ttu-id="580c5-208">`wsFederationHttpBinding` Řídí podrobnosti o nastavení zabezpečení zpráv v [ \<zpráva >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="580c5-208">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="580c5-209">Všimněte si, [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element poskytuje přístup jen zabezpečení použité vazbou nelze změnit po vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="580c5-209">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>  
  
 <span data-ttu-id="580c5-210">`wsFederationHttpBinding` Také obsahuje atribut privactyNoticeAt k nastavení a načtení identifikátoru URI, ve kterém je umístěno oznámení soukromí.</span><span class="sxs-lookup"><span data-stu-id="580c5-210">The `wsFederationHttpBinding` also provides a privactyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>  
  
 <span data-ttu-id="580c5-211">Zásady zabezpečení je zvlášť důležité při scénářích s federací.</span><span class="sxs-lookup"><span data-stu-id="580c5-211">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="580c5-212">Doporučujeme použít nějaký způsob zabezpečení, jako je například HTTPS, zásady ochrany před uživateli se zlými úmysly.</span><span class="sxs-lookup"><span data-stu-id="580c5-212">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>  
  
 <span data-ttu-id="580c5-213">Ve scénářích s federací používá tuto vazbu potenciálně zásady služby obsahuje důležité informace, jako je klíč používat zašifrování vydaný token (SAML), typ deklarace identity v tokenu, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="580c5-213">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="580c5-214">Pokud je tato zásada manipulováno, může útočník zjistit klíče vydaného tokenu, což vede k další manipulaci, zpřístupnění informací a dalšího škodlivého chování.</span><span class="sxs-lookup"><span data-stu-id="580c5-214">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="580c5-215">K tomu nedocházelo, musí být získány bezpečně (například pomocí protokolu HTTPS) zásady ze služby.</span><span class="sxs-lookup"><span data-stu-id="580c5-215">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>  
  
 <span data-ttu-id="580c5-216">Další informace pro tuto vazbu, naleznete v tématu [jak: Vytvoření instance WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="580c5-216">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="580c5-217">Příklad</span><span class="sxs-lookup"><span data-stu-id="580c5-217">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="580c5-218">Viz také:</span><span class="sxs-lookup"><span data-stu-id="580c5-218">See also</span></span>
- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="580c5-219">Postupy: Vytvoření instance WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="580c5-219">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="580c5-220">Vazby</span><span class="sxs-lookup"><span data-stu-id="580c5-220">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="580c5-221">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="580c5-221">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="580c5-222">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="580c5-222">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="580c5-223">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="580c5-223">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
