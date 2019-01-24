---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 7869737f1e3d8c7a9ba569991ead6f7f759e6c58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616885"
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="390d0-102">&lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="390d0-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="390d0-103">Zabezpečená a interoperabilní vazbu, která je odvozena z [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a podporuje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="390d0-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="390d0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="390d0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="390d0-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="390d0-105">\<bindings></span></span>  
<span data-ttu-id="390d0-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="390d0-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="390d0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="390d0-107">Syntax</span></span>  
  
```xml  
<ws2007FederationHttpBinding>
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
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
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
</ws2007FederationHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="390d0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="390d0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="390d0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="390d0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="390d0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="390d0-110">Attributes</span></span>  
  
|<span data-ttu-id="390d0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="390d0-111">Attribute</span></span>|<span data-ttu-id="390d0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="390d0-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="390d0-113">Hodnota, která označuje, zda obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="390d0-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="390d0-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="390d0-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="390d0-115">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="390d0-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="390d0-116">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="390d0-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="390d0-117">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="390d0-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="390d0-118">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="390d0-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="390d0-119">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="390d0-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="390d0-120">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="390d0-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="390d0-121">Velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="390d0-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="390d0-122">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="390d0-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="390d0-123">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="390d0-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="390d0-124">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="390d0-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="390d0-125">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="390d0-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="390d0-126">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="390d0-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="390d0-127">Maximální velikost v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="390d0-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="390d0-128">Odesílatel zprávy, která překračuje tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="390d0-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="390d0-129">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="390d0-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="390d0-130">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="390d0-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="390d0-131">Definuje kodér pro kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="390d0-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="390d0-132">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="390d0-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="390d0-133">-Text: Použijte kodér textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="390d0-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="390d0-134">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="390d0-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="390d0-135">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="390d0-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="390d0-136">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="390d0-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="390d0-137">Název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="390d0-137">The configuration name of the binding.</span></span> <span data-ttu-id="390d0-138">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="390d0-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="390d0-139">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="390d0-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="390d0-140">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="390d0-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="390d0-141">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="390d0-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="390d0-142">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="390d0-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="390d0-143">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="390d0-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="390d0-144">Identifikátor URI, ve kterém je umístěno oznámení soukromí.</span><span class="sxs-lookup"><span data-stu-id="390d0-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="390d0-145">Verze aktuálního oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="390d0-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="390d0-146">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="390d0-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="390d0-147">Pokud `useDefaultWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="390d0-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="390d0-148">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="390d0-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="390d0-149">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="390d0-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="390d0-150">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="390d0-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="390d0-151">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="390d0-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="390d0-152">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="390d0-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="390d0-153">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="390d0-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="390d0-154">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="390d0-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="390d0-155">Nastaví znakovou sadu kódování, které má být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="390d0-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="390d0-156">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="390d0-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="390d0-157">-BigEndianUnicode: Big Endian kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="390d0-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="390d0-158">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="390d0-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="390d0-159">-   UTF8: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="390d0-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="390d0-160">Použije se UTF8.</span><span class="sxs-lookup"><span data-stu-id="390d0-160">The default is UTF8.</span></span> <span data-ttu-id="390d0-161">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="390d0-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="390d0-162">Hodnota, která určuje, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="390d0-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="390d0-163">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="390d0-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="390d0-164">Hodnota, která označuje, zda se používá v systému automaticky nakonfigurovaný proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="390d0-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="390d0-165">Adresa proxy musí být `null` (to znamená, není nastavený) Pokud tento atribut je `true`.</span><span class="sxs-lookup"><span data-stu-id="390d0-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="390d0-166">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="390d0-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="390d0-167">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="390d0-167">Child Elements</span></span>  
  
|<span data-ttu-id="390d0-168">Prvek</span><span class="sxs-lookup"><span data-stu-id="390d0-168">Element</span></span>|<span data-ttu-id="390d0-169">Popis</span><span class="sxs-lookup"><span data-stu-id="390d0-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="390d0-170">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="390d0-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="390d0-171">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="390d0-171">Defines the security settings for the message.</span></span> <span data-ttu-id="390d0-172">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="390d0-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="390d0-173">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="390d0-173">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="390d0-174">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="390d0-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="390d0-175">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="390d0-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="390d0-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="390d0-176">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="390d0-177">Určuje, zda jsou vytvořeny spolehlivé relace mezi koncovými body kanálu.</span><span class="sxs-lookup"><span data-stu-id="390d0-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="390d0-178">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="390d0-178">Parent Elements</span></span>  
  
|<span data-ttu-id="390d0-179">Prvek</span><span class="sxs-lookup"><span data-stu-id="390d0-179">Element</span></span>|<span data-ttu-id="390d0-180">Popis</span><span class="sxs-lookup"><span data-stu-id="390d0-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="390d0-181">\<bindings></span><span class="sxs-lookup"><span data-stu-id="390d0-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="390d0-182">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="390d0-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="390d0-183">Poznámky</span><span class="sxs-lookup"><span data-stu-id="390d0-183">Remarks</span></span>  
 <span data-ttu-id="390d0-184">Federace se nachází taky možnost podělit identit napříč více podniky nebo vztah důvěryhodnosti domény pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="390d0-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="390d0-185">Protokol WS-Trust používá k mapování reprezentace identit z jednoho vztahu důvěryhodnosti domény na jiný.</span><span class="sxs-lookup"><span data-stu-id="390d0-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="390d0-186">Federované vazby HTTP podporuje zabezpečení protokolu SOAP, stejně jako ve smíšeném režimu zabezpečení, ale zabezpečení přenosu není podporováno.</span><span class="sxs-lookup"><span data-stu-id="390d0-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="390d0-187">Nakonfigurované s touto vazbou služby musíte použít přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="390d0-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="390d0-188">Další informace najdete v tématu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="390d0-188">For more information, see [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="390d0-189">Příklad</span><span class="sxs-lookup"><span data-stu-id="390d0-189">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="390d0-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="390d0-190">See also</span></span>
- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="390d0-191">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="390d0-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)
- [<span data-ttu-id="390d0-192">Vazby</span><span class="sxs-lookup"><span data-stu-id="390d0-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="390d0-193">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="390d0-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="390d0-194">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="390d0-194">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="390d0-195">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="390d0-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
