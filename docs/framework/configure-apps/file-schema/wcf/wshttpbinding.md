---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 81f0101ce1dc2195cfc2f556e38a8551f674d13b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941514"
---
# <a name="wshttpbinding"></a><span data-ttu-id="7d455-101">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7d455-101">\<wsHttpBinding></span></span>
<span data-ttu-id="7d455-102">Definuje bezpečnou, spolehlivou a interoperabilní vazbu, která je vhodná pro neduplexní kontrakty služeb.</span><span class="sxs-lookup"><span data-stu-id="7d455-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="7d455-103">Vazba implementuje následující specifikace: Protokol WS-Reliable pro zajištění spolehlivosti a WS-Security pro zabezpečení a ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="7d455-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="7d455-104">Přenos je HTTP a kódování zprávy je kódování text/XML.</span><span class="sxs-lookup"><span data-stu-id="7d455-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="7d455-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7d455-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="7d455-106">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="7d455-106">\<bindings></span></span>  
<span data-ttu-id="7d455-107">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7d455-107">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d455-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d455-108">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d455-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d455-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7d455-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7d455-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d455-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d455-111">Attributes</span></span>  
  
|<span data-ttu-id="7d455-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="7d455-112">Attribute</span></span>|<span data-ttu-id="7d455-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7d455-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d455-114">allowCookies</span><span class="sxs-lookup"><span data-stu-id="7d455-114">allowCookies</span></span>|<span data-ttu-id="7d455-115">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="7d455-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="7d455-116">Výchozí hodnota je false.</span><span class="sxs-lookup"><span data-stu-id="7d455-116">The default is false.</span></span><br /><br /> <span data-ttu-id="7d455-117">Tuto vlastnost lze použít při práci s webovými službami ASMX, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="7d455-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="7d455-118">Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="7d455-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="7d455-119">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="7d455-119">bypassProxyOnLocal</span></span>|<span data-ttu-id="7d455-120">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="7d455-120">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="7d455-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="7d455-121">The default is `false`.</span></span>|  
|<span data-ttu-id="7d455-122">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="7d455-122">closeTimeout</span></span>|<span data-ttu-id="7d455-123"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="7d455-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7d455-124">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7d455-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d455-125">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7d455-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7d455-126">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="7d455-126">hostnameComparisonMode</span></span>|<span data-ttu-id="7d455-127">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="7d455-127">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="7d455-128">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="7d455-128">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="7d455-129">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="7d455-129">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="7d455-130">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="7d455-130">maxBufferPoolSize</span></span>|<span data-ttu-id="7d455-131">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="7d455-131">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="7d455-132">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="7d455-132">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="7d455-133">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7d455-133">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="7d455-134">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="7d455-134">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="7d455-135">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="7d455-135">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="7d455-136">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="7d455-136">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="7d455-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="7d455-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="7d455-138">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="7d455-138">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7d455-139">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7d455-139">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="7d455-140">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="7d455-140">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7d455-141">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="7d455-141">The default is 65536.</span></span>|  
|<span data-ttu-id="7d455-142">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="7d455-142">messageEncoding</span></span>|<span data-ttu-id="7d455-143">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="7d455-143">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="7d455-144">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7d455-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7d455-145">Textové Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="7d455-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="7d455-146">Maximální Použijte kodér 1,0 (pro organizaci přenosu zpráv).</span><span class="sxs-lookup"><span data-stu-id="7d455-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="7d455-147">– Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="7d455-147">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="7d455-148">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="7d455-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="7d455-149">name</span><span class="sxs-lookup"><span data-stu-id="7d455-149">name</span></span>|<span data-ttu-id="7d455-150">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="7d455-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7d455-151">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="7d455-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7d455-152">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="7d455-152">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7d455-153">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d455-153">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="7d455-154">openTimeout</span><span class="sxs-lookup"><span data-stu-id="7d455-154">openTimeout</span></span>|<span data-ttu-id="7d455-155"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="7d455-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7d455-156">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7d455-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d455-157">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7d455-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7d455-158">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="7d455-158">proxyAddress</span></span>|<span data-ttu-id="7d455-159">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="7d455-159">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="7d455-160">Pokud `useSystemWebProxy` má `true`parametr hodnotu, musí být `null`toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="7d455-160">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="7d455-161">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="7d455-161">The default is `null`.</span></span>|  
|<span data-ttu-id="7d455-162">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="7d455-162">receiveTimeout</span></span>|<span data-ttu-id="7d455-163"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="7d455-163">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7d455-164">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7d455-164">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d455-165">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7d455-165">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7d455-166">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="7d455-166">sendTimeout</span></span>|<span data-ttu-id="7d455-167"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="7d455-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7d455-168">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7d455-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d455-169">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7d455-169">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7d455-170">textEncoding</span><span class="sxs-lookup"><span data-stu-id="7d455-170">textEncoding</span></span>|<span data-ttu-id="7d455-171">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="7d455-171">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7d455-172">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7d455-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7d455-173">- UnicodeFffeTextEncoding: Kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="7d455-173">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="7d455-174">- Utf16TextEncoding: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="7d455-174">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="7d455-175">- Utf8TextEncoding: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="7d455-175">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="7d455-176">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="7d455-176">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="7d455-177">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="7d455-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="7d455-178">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="7d455-178">transactionFlow</span></span>|<span data-ttu-id="7d455-179">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="7d455-179">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="7d455-180">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="7d455-180">The default is `false`.</span></span>|  
|<span data-ttu-id="7d455-181">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="7d455-181">useDefaultWebProxy</span></span>|<span data-ttu-id="7d455-182">Logická hodnota, která určuje, zda se používá automaticky konfigurovaný proxy server HTTP systému.</span><span class="sxs-lookup"><span data-stu-id="7d455-182">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="7d455-183">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="7d455-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d455-184">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d455-184">Child Elements</span></span>  
  
|<span data-ttu-id="7d455-185">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d455-185">Element</span></span>|<span data-ttu-id="7d455-186">Popis</span><span class="sxs-lookup"><span data-stu-id="7d455-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d455-187">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7d455-187">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="7d455-188">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7d455-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="7d455-189">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7d455-189">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="7d455-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7d455-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="7d455-191">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7d455-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7d455-192">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="7d455-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="7d455-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7d455-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="7d455-194">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="7d455-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d455-195">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7d455-195">Parent Elements</span></span>  
  
|<span data-ttu-id="7d455-196">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d455-196">Element</span></span>|<span data-ttu-id="7d455-197">Popis</span><span class="sxs-lookup"><span data-stu-id="7d455-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d455-198">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="7d455-198">\<bindings></span></span>](bindings.md)|<span data-ttu-id="7d455-199">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="7d455-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d455-200">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d455-200">Remarks</span></span>  
 <span data-ttu-id="7d455-201">Je podobná, `BasicHttpBinding` ale poskytuje více funkcí webové služby. `WSHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="7d455-201">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="7d455-202">Využívá přenos pomocí protokolu HTTP a poskytuje zabezpečení zpráv, jako BasicHttpBinding, ale také poskytuje transakce, spolehlivé zasílání zpráv a WS-Addressing, které jsou povoleny ve výchozím nastavení nebo k dispozici prostřednictvím jednoho nastavení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7d455-202">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d455-203">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d455-203">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="7d455-204">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d455-204">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="7d455-205">Vazby</span><span class="sxs-lookup"><span data-stu-id="7d455-205">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7d455-206">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="7d455-206">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7d455-207">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7d455-207">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7d455-208">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="7d455-208">\<binding></span></span>](../../../misc/binding.md)
