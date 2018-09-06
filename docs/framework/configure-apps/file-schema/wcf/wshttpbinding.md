---
title: '&lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 480e10b9667712fbd2a3ffa95e1373d72ee1a9df
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802830"
---
# <a name="ltwshttpbindinggt"></a><span data-ttu-id="5a03b-102">&lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5a03b-102">&lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="5a03b-103">Definuje bezpečné, spolehlivé a interoperabilní vazby vhodné pro neduplexní servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="5a03b-103">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="5a03b-104">Vazba implementuje následující specifikace: zasílání zpráv WS-Reliable spolehlivost a WS-Security pro ověřování a zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="5a03b-104">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="5a03b-105">Přenos HTTP a kódování zpráv je Text/XML kódování.</span><span class="sxs-lookup"><span data-stu-id="5a03b-105">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="5a03b-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5a03b-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a03b-107">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5a03b-107">\<bindings></span></span>  
<span data-ttu-id="5a03b-108">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5a03b-108">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a03b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a03b-109">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding   
        allowCookies="Boolean"  
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
          <message   
             algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                          clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
             establishSecurityContext="Boolean"  
             negotiateServiceCredential="Boolean" />  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a03b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a03b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a03b-111">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a03b-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a03b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a03b-112">Attributes</span></span>  
  
|<span data-ttu-id="5a03b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a03b-113">Attribute</span></span>|<span data-ttu-id="5a03b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5a03b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a03b-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="5a03b-115">allowCookies</span></span>|<span data-ttu-id="5a03b-116">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="5a03b-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="5a03b-117">Výchozí hodnota je false.</span><span class="sxs-lookup"><span data-stu-id="5a03b-117">The default is false.</span></span><br /><br /> <span data-ttu-id="5a03b-118">Tuto vlastnost můžete použít, když pracujete s ASMX webovými službami, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="5a03b-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="5a03b-119">Tímto způsobem máte jistotu, že soubory cookie vrácený ze serveru se automaticky zkopírují do všechny budoucí požadavky za danou službu.</span><span class="sxs-lookup"><span data-stu-id="5a03b-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="5a03b-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="5a03b-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="5a03b-121">Logická hodnota určující, zda obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="5a03b-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="5a03b-122">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="5a03b-122">The default is `false`.</span></span>|  
|<span data-ttu-id="5a03b-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="5a03b-123">closeTimeout</span></span>|<span data-ttu-id="5a03b-124">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="5a03b-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5a03b-125">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5a03b-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5a03b-126">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5a03b-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5a03b-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="5a03b-127">hostnameComparisonMode</span></span>|<span data-ttu-id="5a03b-128">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="5a03b-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="5a03b-129">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="5a03b-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="5a03b-130">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="5a03b-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="5a03b-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="5a03b-131">maxBufferPoolSize</span></span>|<span data-ttu-id="5a03b-132">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="5a03b-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="5a03b-133">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="5a03b-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="5a03b-134">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5a03b-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="5a03b-135">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="5a03b-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="5a03b-136">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="5a03b-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="5a03b-137">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5a03b-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="5a03b-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="5a03b-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="5a03b-139">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="5a03b-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="5a03b-140">Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5a03b-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="5a03b-141">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="5a03b-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="5a03b-142">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="5a03b-142">The default is 65536.</span></span>|  
|<span data-ttu-id="5a03b-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="5a03b-143">messageEncoding</span></span>|<span data-ttu-id="5a03b-144">Definuje kodér pro kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="5a03b-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="5a03b-145">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="5a03b-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5a03b-146">-Text: Použijte kodér textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="5a03b-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="5a03b-147">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="5a03b-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="5a03b-148">– Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="5a03b-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="5a03b-149">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="5a03b-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="5a03b-150">name</span><span class="sxs-lookup"><span data-stu-id="5a03b-150">name</span></span>|<span data-ttu-id="5a03b-151">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="5a03b-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5a03b-152">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="5a03b-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5a03b-153">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="5a03b-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5a03b-154">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5a03b-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="5a03b-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="5a03b-155">openTimeout</span></span>|<span data-ttu-id="5a03b-156">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="5a03b-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5a03b-157">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5a03b-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5a03b-158">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5a03b-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5a03b-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="5a03b-159">proxyAddress</span></span>|<span data-ttu-id="5a03b-160">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a03b-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="5a03b-161">Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="5a03b-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="5a03b-162">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="5a03b-162">The default is `null`.</span></span>|  
|<span data-ttu-id="5a03b-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="5a03b-163">receiveTimeout</span></span>|<span data-ttu-id="5a03b-164">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="5a03b-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5a03b-165">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5a03b-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5a03b-166">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5a03b-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5a03b-167">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="5a03b-167">sendTimeout</span></span>|<span data-ttu-id="5a03b-168">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="5a03b-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5a03b-169">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5a03b-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5a03b-170">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5a03b-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="5a03b-171">textEncoding</span><span class="sxs-lookup"><span data-stu-id="5a03b-171">textEncoding</span></span>|<span data-ttu-id="5a03b-172">Určuje znakovou sadu kódování pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="5a03b-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="5a03b-173">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="5a03b-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5a03b-174">-UnicodeFffeTextEncoding: BigEndian kódování Unicode kódování.</span><span class="sxs-lookup"><span data-stu-id="5a03b-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="5a03b-175">-Utf16TextEncoding: kódování 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="5a03b-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="5a03b-176">-Utf8TextEncoding: 8 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="5a03b-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="5a03b-177">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="5a03b-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="5a03b-178">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="5a03b-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="5a03b-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="5a03b-179">transactionFlow</span></span>|<span data-ttu-id="5a03b-180">Logická hodnota určující, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="5a03b-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="5a03b-181">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="5a03b-181">The default is `false`.</span></span>|  
|<span data-ttu-id="5a03b-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="5a03b-182">useDefaultWebProxy</span></span>|<span data-ttu-id="5a03b-183">Logická hodnota, která určuje, jestli se používá v systému automaticky nakonfigurovaný proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a03b-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="5a03b-184">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="5a03b-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a03b-185">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a03b-185">Child Elements</span></span>  
  
|<span data-ttu-id="5a03b-186">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a03b-186">Element</span></span>|<span data-ttu-id="5a03b-187">Popis</span><span class="sxs-lookup"><span data-stu-id="5a03b-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a03b-188">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="5a03b-188">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="5a03b-189">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="5a03b-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="5a03b-190">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="5a03b-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="5a03b-191">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="5a03b-191">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="5a03b-192">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="5a03b-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5a03b-193">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="5a03b-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="5a03b-194">reliableSession</span><span class="sxs-lookup"><span data-stu-id="5a03b-194">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="5a03b-195">Určuje, pokud jsou mezi koncovými body kanál navázat spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="5a03b-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a03b-196">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a03b-196">Parent Elements</span></span>  
  
|<span data-ttu-id="5a03b-197">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a03b-197">Element</span></span>|<span data-ttu-id="5a03b-198">Popis</span><span class="sxs-lookup"><span data-stu-id="5a03b-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a03b-199">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5a03b-199">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="5a03b-200">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="5a03b-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a03b-201">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a03b-201">Remarks</span></span>  
 <span data-ttu-id="5a03b-202">`WSHttpBinding` Je podobný `BasicHttpBinding` , ale poskytuje další funkce webové služby.</span><span class="sxs-lookup"><span data-stu-id="5a03b-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="5a03b-203">Používá přenos pomocí protokolu HTTP a poskytuje zabezpečení zpráv, stejně jako BasicHttpBinding, ale také poskytuje transakce, spolehlivé zasílání zpráv a WS-Addressing, buď povolená ve výchozím nastavení nebo jsou k dispozici nastavení jeden ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5a03b-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a03b-204">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a03b-204">Example</span></span>  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
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
  
## <a name="see-also"></a><span data-ttu-id="5a03b-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a03b-205">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement>  
 [<span data-ttu-id="5a03b-206">Vazby</span><span class="sxs-lookup"><span data-stu-id="5a03b-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5a03b-207">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5a03b-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5a03b-208">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="5a03b-208">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5a03b-209">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5a03b-209">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
