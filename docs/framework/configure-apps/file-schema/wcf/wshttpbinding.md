---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: d22065abcb04209ebd1ad51b41bfc9167af6d4c9
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758973"
---
# <a name="wshttpbinding"></a><span data-ttu-id="061d5-101">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="061d5-101">\<wsHttpBinding></span></span>
<span data-ttu-id="061d5-102">Definuje bezpečné, spolehlivé a interoperabilní vazby vhodné pro neduplexní servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="061d5-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="061d5-103">Vazba implementuje následující specifikace: Posílání WS-Reliable spolehlivost a WS-Security pro ověřování a zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="061d5-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="061d5-104">Přenos HTTP a kódování zpráv je Text/XML kódování.</span><span class="sxs-lookup"><span data-stu-id="061d5-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="061d5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="061d5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="061d5-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="061d5-106">\<bindings></span></span>  
<span data-ttu-id="061d5-107">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="061d5-107">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="061d5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="061d5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="061d5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="061d5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="061d5-110">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="061d5-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="061d5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="061d5-111">Attributes</span></span>  
  
|<span data-ttu-id="061d5-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="061d5-112">Attribute</span></span>|<span data-ttu-id="061d5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="061d5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="061d5-114">allowCookies</span><span class="sxs-lookup"><span data-stu-id="061d5-114">allowCookies</span></span>|<span data-ttu-id="061d5-115">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="061d5-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="061d5-116">Výchozí hodnota je false.</span><span class="sxs-lookup"><span data-stu-id="061d5-116">The default is false.</span></span><br /><br /> <span data-ttu-id="061d5-117">Tuto vlastnost můžete použít, když pracujete s ASMX webovými službami, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="061d5-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="061d5-118">Tímto způsobem máte jistotu, že soubory cookie vrácený ze serveru se automaticky zkopírují do všechny budoucí požadavky za danou službu.</span><span class="sxs-lookup"><span data-stu-id="061d5-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="061d5-119">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="061d5-119">bypassProxyOnLocal</span></span>|<span data-ttu-id="061d5-120">Logická hodnota určující, zda obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="061d5-120">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="061d5-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="061d5-121">The default is `false`.</span></span>|  
|<span data-ttu-id="061d5-122">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="061d5-122">closeTimeout</span></span>|<span data-ttu-id="061d5-123">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="061d5-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="061d5-124">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="061d5-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="061d5-125">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="061d5-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="061d5-126">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="061d5-126">hostnameComparisonMode</span></span>|<span data-ttu-id="061d5-127">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="061d5-127">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="061d5-128">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="061d5-128">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="061d5-129">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="061d5-129">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="061d5-130">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="061d5-130">maxBufferPoolSize</span></span>|<span data-ttu-id="061d5-131">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="061d5-131">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="061d5-132">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="061d5-132">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="061d5-133">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="061d5-133">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="061d5-134">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="061d5-134">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="061d5-135">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="061d5-135">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="061d5-136">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="061d5-136">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="061d5-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="061d5-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="061d5-138">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="061d5-138">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="061d5-139">Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="061d5-139">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="061d5-140">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="061d5-140">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="061d5-141">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="061d5-141">The default is 65536.</span></span>|  
|<span data-ttu-id="061d5-142">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="061d5-142">messageEncoding</span></span>|<span data-ttu-id="061d5-143">Definuje kodér pro kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="061d5-143">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="061d5-144">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="061d5-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="061d5-145">-Text: Použijte kodér textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="061d5-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="061d5-146">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="061d5-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="061d5-147">– Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="061d5-147">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="061d5-148">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="061d5-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="061d5-149">name</span><span class="sxs-lookup"><span data-stu-id="061d5-149">name</span></span>|<span data-ttu-id="061d5-150">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="061d5-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="061d5-151">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="061d5-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="061d5-152">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="061d5-152">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="061d5-153">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="061d5-153">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="061d5-154">openTimeout</span><span class="sxs-lookup"><span data-stu-id="061d5-154">openTimeout</span></span>|<span data-ttu-id="061d5-155">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="061d5-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="061d5-156">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="061d5-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="061d5-157">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="061d5-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="061d5-158">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="061d5-158">proxyAddress</span></span>|<span data-ttu-id="061d5-159">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="061d5-159">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="061d5-160">Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="061d5-160">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="061d5-161">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="061d5-161">The default is `null`.</span></span>|  
|<span data-ttu-id="061d5-162">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="061d5-162">receiveTimeout</span></span>|<span data-ttu-id="061d5-163">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="061d5-163">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="061d5-164">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="061d5-164">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="061d5-165">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="061d5-165">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="061d5-166">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="061d5-166">sendTimeout</span></span>|<span data-ttu-id="061d5-167">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="061d5-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="061d5-168">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="061d5-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="061d5-169">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="061d5-169">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="061d5-170">textEncoding</span><span class="sxs-lookup"><span data-stu-id="061d5-170">textEncoding</span></span>|<span data-ttu-id="061d5-171">Určuje znakovou sadu kódování pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="061d5-171">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="061d5-172">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="061d5-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="061d5-173">-UnicodeFffeTextEncoding: Kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="061d5-173">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="061d5-174">-Utf16TextEncoding: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="061d5-174">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="061d5-175">-Utf8TextEncoding: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="061d5-175">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="061d5-176">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="061d5-176">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="061d5-177">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="061d5-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="061d5-178">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="061d5-178">transactionFlow</span></span>|<span data-ttu-id="061d5-179">Logická hodnota určující, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="061d5-179">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="061d5-180">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="061d5-180">The default is `false`.</span></span>|  
|<span data-ttu-id="061d5-181">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="061d5-181">useDefaultWebProxy</span></span>|<span data-ttu-id="061d5-182">Logická hodnota, která určuje, jestli se používá v systému automaticky nakonfigurovaný proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="061d5-182">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="061d5-183">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="061d5-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="061d5-184">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="061d5-184">Child Elements</span></span>  
  
|<span data-ttu-id="061d5-185">Prvek</span><span class="sxs-lookup"><span data-stu-id="061d5-185">Element</span></span>|<span data-ttu-id="061d5-186">Popis</span><span class="sxs-lookup"><span data-stu-id="061d5-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="061d5-187">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="061d5-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="061d5-188">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="061d5-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="061d5-189">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="061d5-189">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="061d5-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="061d5-190">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="061d5-191">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="061d5-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="061d5-192">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="061d5-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="061d5-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="061d5-193">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="061d5-194">Určuje, pokud jsou mezi koncovými body kanál navázat spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="061d5-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="061d5-195">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="061d5-195">Parent Elements</span></span>  
  
|<span data-ttu-id="061d5-196">Prvek</span><span class="sxs-lookup"><span data-stu-id="061d5-196">Element</span></span>|<span data-ttu-id="061d5-197">Popis</span><span class="sxs-lookup"><span data-stu-id="061d5-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="061d5-198">\<bindings></span><span class="sxs-lookup"><span data-stu-id="061d5-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="061d5-199">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="061d5-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="061d5-200">Poznámky</span><span class="sxs-lookup"><span data-stu-id="061d5-200">Remarks</span></span>  
 <span data-ttu-id="061d5-201">`WSHttpBinding` Je podobný `BasicHttpBinding` , ale poskytuje další funkce webové služby.</span><span class="sxs-lookup"><span data-stu-id="061d5-201">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="061d5-202">Používá přenos pomocí protokolu HTTP a poskytuje zabezpečení zpráv, stejně jako BasicHttpBinding, ale také poskytuje transakce, spolehlivé zasílání zpráv a WS-Addressing, buď povolená ve výchozím nastavení nebo jsou k dispozici nastavení jeden ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="061d5-202">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="061d5-203">Příklad</span><span class="sxs-lookup"><span data-stu-id="061d5-203">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="061d5-204">Viz také:</span><span class="sxs-lookup"><span data-stu-id="061d5-204">See also</span></span>
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="061d5-205">Vazby</span><span class="sxs-lookup"><span data-stu-id="061d5-205">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="061d5-206">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="061d5-206">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="061d5-207">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="061d5-207">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="061d5-208">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="061d5-208">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
