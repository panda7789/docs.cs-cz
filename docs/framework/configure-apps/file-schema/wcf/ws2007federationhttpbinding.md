---
title: "&lt;– ws2007FederationHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28e4cc9189c144404bcfe2b7f8e255a74eef76c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="39f01-102">&lt;– ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="39f01-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="39f01-103">Zabezpečení a vzájemná spolupráce vazbu, která je odvozena z [ \<– wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a podporuje federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="39f01-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="39f01-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="39f01-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39f01-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="39f01-105">\<bindings></span></span>  
<span data-ttu-id="39f01-106">\<– ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="39f01-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f01-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39f01-107">Syntax</span></span>  
  
```xml  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
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
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39f01-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="39f01-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39f01-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="39f01-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39f01-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="39f01-110">Attributes</span></span>  
  
|<span data-ttu-id="39f01-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="39f01-111">Attribute</span></span>|<span data-ttu-id="39f01-112">Popis</span><span class="sxs-lookup"><span data-stu-id="39f01-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="39f01-113">Hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="39f01-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="39f01-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="39f01-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="39f01-115">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="39f01-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="39f01-116">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39f01-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39f01-117">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="39f01-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="39f01-118">Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="39f01-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="39f01-119">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="39f01-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="39f01-120">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.</span><span class="sxs-lookup"><span data-stu-id="39f01-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="39f01-121">Velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="39f01-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="39f01-122">Výchozí hodnota je 524,288 bajtů (512 * 1024).</span><span class="sxs-lookup"><span data-stu-id="39f01-122">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="39f01-123">Mnoho částí [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="39f01-123">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="39f01-124">Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="39f01-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="39f01-125">S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu.</span><span class="sxs-lookup"><span data-stu-id="39f01-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="39f01-126">Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="39f01-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="39f01-127">Maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="39f01-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="39f01-128">Odesílatel zprávu, která překračuje tento limit, obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="39f01-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="39f01-129">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="39f01-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="39f01-130">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="39f01-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="39f01-131">Definuje kodér použitá ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="39f01-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="39f01-132">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="39f01-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="39f01-133">-Text: Pomocí kodéru text zprávy.</span><span class="sxs-lookup"><span data-stu-id="39f01-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="39f01-134">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="39f01-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="39f01-135">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="39f01-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="39f01-136">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="39f01-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="39f01-137">Název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="39f01-137">The configuration name of the binding.</span></span> <span data-ttu-id="39f01-138">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="39f01-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="39f01-139">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="39f01-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="39f01-140">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="39f01-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="39f01-141">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="39f01-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="39f01-142">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39f01-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39f01-143">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="39f01-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="39f01-144">Identifikátor URI, ve kterém se nachází v oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="39f01-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="39f01-145">Verze aktuální informace o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="39f01-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="39f01-146">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="39f01-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="39f01-147">Pokud `useDefaultWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="39f01-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="39f01-148">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="39f01-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="39f01-149">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="39f01-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="39f01-150">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39f01-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39f01-151">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="39f01-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="39f01-152">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="39f01-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="39f01-153">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39f01-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39f01-154">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="39f01-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="39f01-155">Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="39f01-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="39f01-156">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="39f01-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="39f01-157">-BigEndianUnicode: Big Endian kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="39f01-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="39f01-158">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="39f01-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="39f01-159">-UTF8: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="39f01-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="39f01-160">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="39f01-160">The default is UTF8.</span></span> <span data-ttu-id="39f01-161">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="39f01-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="39f01-162">Hodnota, která určuje, zda vazby podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="39f01-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="39f01-163">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="39f01-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="39f01-164">Hodnota, která určuje, zda je použít server proxy protokolu HTTP pro automatickou konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="39f01-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="39f01-165">Adresa proxy serveru musí být `null` (to znamená, že není nastavena) Pokud tento atribut je `true`.</span><span class="sxs-lookup"><span data-stu-id="39f01-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="39f01-166">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="39f01-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39f01-167">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="39f01-167">Child Elements</span></span>  
  
|<span data-ttu-id="39f01-168">Prvek</span><span class="sxs-lookup"><span data-stu-id="39f01-168">Element</span></span>|<span data-ttu-id="39f01-169">Popis</span><span class="sxs-lookup"><span data-stu-id="39f01-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f01-170">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="39f01-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="39f01-171">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="39f01-171">Defines the security settings for the message.</span></span> <span data-ttu-id="39f01-172">Tento element je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="39f01-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="39f01-173">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="39f01-173">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="39f01-174">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="39f01-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="39f01-175">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="39f01-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="39f01-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="39f01-176">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="39f01-177">Určuje, zda jsou určeny spolehlivé relace mezi koncovými body kanálu.</span><span class="sxs-lookup"><span data-stu-id="39f01-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39f01-178">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="39f01-178">Parent Elements</span></span>  
  
|<span data-ttu-id="39f01-179">Prvek</span><span class="sxs-lookup"><span data-stu-id="39f01-179">Element</span></span>|<span data-ttu-id="39f01-180">Popis</span><span class="sxs-lookup"><span data-stu-id="39f01-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f01-181">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="39f01-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="39f01-182">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="39f01-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39f01-183">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39f01-183">Remarks</span></span>  
 <span data-ttu-id="39f01-184">Federace se nachází možnost identity sdílet mezi více podniky nebo vztahu důvěryhodnosti domény pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="39f01-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="39f01-185">Protokol WS-Trust používá k mapování reprezentace identity z jednom vztahu důvěryhodnosti domény do druhého.</span><span class="sxs-lookup"><span data-stu-id="39f01-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="39f01-186">Federované vazby HTTP podporuje zabezpečení protokolu SOAP, jakož i ve smíšeném režimu zabezpečení, ale nepodporuje zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="39f01-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="39f01-187">Nakonfigurované s touto vazbou služby musíte použít přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="39f01-187">Services configured with this binding must use the HTTP transport.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="39f01-188">[ \<– wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="39f01-188"> [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39f01-189">Příklad</span><span class="sxs-lookup"><span data-stu-id="39f01-189">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://www.contoso.com"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
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
  
## <a name="see-also"></a><span data-ttu-id="39f01-190">Viz také</span><span class="sxs-lookup"><span data-stu-id="39f01-190">See Also</span></span>  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>  
 [<span data-ttu-id="39f01-191">\<– wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="39f01-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
 [<span data-ttu-id="39f01-192">Vazby</span><span class="sxs-lookup"><span data-stu-id="39f01-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="39f01-193">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="39f01-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="39f01-194">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="39f01-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="39f01-195">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="39f01-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
