---
title: '&lt;wsHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cf154f94b61e114e1ce379d27d5960987253344
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltwshttpbindinggt"></a><span data-ttu-id="a25e6-102">&lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a25e6-102">&lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="a25e6-103">Definuje vhodný pro služby bez duplexní kontrakty vazbu bezpečné, spolehlivé a umožňuje vzájemnou spolupráci.</span><span class="sxs-lookup"><span data-stu-id="a25e6-103">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="a25e6-104">Vazba implementuje tyto specifikace: WS-spolehlivé zasílání zpráv spolehlivost a WS-zabezpečení pro zabezpečení zpráv a ověřování.</span><span class="sxs-lookup"><span data-stu-id="a25e6-104">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="a25e6-105">Přenos protokolu HTTP a kódování zpráv je Text/XML kódování.</span><span class="sxs-lookup"><span data-stu-id="a25e6-105">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="a25e6-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a25e6-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="a25e6-107">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a25e6-107">\<bindings></span></span>  
<span data-ttu-id="a25e6-108">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a25e6-108">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a25e6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a25e6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a25e6-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a25e6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a25e6-111">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a25e6-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a25e6-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a25e6-112">Attributes</span></span>  
  
|<span data-ttu-id="a25e6-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a25e6-113">Attribute</span></span>|<span data-ttu-id="a25e6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a25e6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a25e6-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="a25e6-115">allowCookies</span></span>|<span data-ttu-id="a25e6-116">Logická hodnota, která určuje, zda klient přijímá soubory cookie a rozšiřuje je na dalších požadavků.</span><span class="sxs-lookup"><span data-stu-id="a25e6-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="a25e6-117">Výchozí hodnota je false.</span><span class="sxs-lookup"><span data-stu-id="a25e6-117">The default is false.</span></span><br /><br /> <span data-ttu-id="a25e6-118">Tuto vlastnost lze použít při používání ASMX webové služby, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="a25e6-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="a25e6-119">Tímto způsobem mohou být jisti, že soubory cookie, kterou vrátil server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="a25e6-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="a25e6-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="a25e6-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="a25e6-121">Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="a25e6-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="a25e6-122">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a25e6-122">The default is `false`.</span></span>|  
|<span data-ttu-id="a25e6-123">Intervalu</span><span class="sxs-lookup"><span data-stu-id="a25e6-123">closeTimeout</span></span>|<span data-ttu-id="a25e6-124">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="a25e6-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a25e6-125">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a25e6-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a25e6-126">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a25e6-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a25e6-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a25e6-127">hostnameComparisonMode</span></span>|<span data-ttu-id="a25e6-128">Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="a25e6-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="a25e6-129">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="a25e6-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="a25e6-130">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.</span><span class="sxs-lookup"><span data-stu-id="a25e6-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="a25e6-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a25e6-131">maxBufferPoolSize</span></span>|<span data-ttu-id="a25e6-132">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="a25e6-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="a25e6-133">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="a25e6-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="a25e6-134">Mnoho části služby Windows Communication Foundation (WCF) pomocí vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a25e6-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="a25e6-135">Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="a25e6-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="a25e6-136">S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu.</span><span class="sxs-lookup"><span data-stu-id="a25e6-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="a25e6-137">Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a25e6-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="a25e6-138">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a25e6-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="a25e6-139">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="a25e6-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="a25e6-140">Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a25e6-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="a25e6-141">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="a25e6-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a25e6-142">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="a25e6-142">The default is 65536.</span></span>|  
|<span data-ttu-id="a25e6-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="a25e6-143">messageEncoding</span></span>|<span data-ttu-id="a25e6-144">Definuje kodér použitá ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="a25e6-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="a25e6-145">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="a25e6-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a25e6-146">-Text: Pomocí kodéru text zprávy.</span><span class="sxs-lookup"><span data-stu-id="a25e6-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="a25e6-147">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="a25e6-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="a25e6-148">-Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="a25e6-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="a25e6-149">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="a25e6-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="a25e6-150">name</span><span class="sxs-lookup"><span data-stu-id="a25e6-150">name</span></span>|<span data-ttu-id="a25e6-151">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="a25e6-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a25e6-152">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="a25e6-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a25e6-153">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="a25e6-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a25e6-154">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a25e6-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="a25e6-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="a25e6-155">openTimeout</span></span>|<span data-ttu-id="a25e6-156">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="a25e6-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a25e6-157">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a25e6-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a25e6-158">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a25e6-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a25e6-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="a25e6-159">proxyAddress</span></span>|<span data-ttu-id="a25e6-160">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="a25e6-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="a25e6-161">Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="a25e6-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="a25e6-162">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="a25e6-162">The default is `null`.</span></span>|  
|<span data-ttu-id="a25e6-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="a25e6-163">receiveTimeout</span></span>|<span data-ttu-id="a25e6-164">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="a25e6-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a25e6-165">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a25e6-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a25e6-166">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a25e6-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a25e6-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="a25e6-167">sendTimeout</span></span>|<span data-ttu-id="a25e6-168">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="a25e6-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a25e6-169">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a25e6-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a25e6-170">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a25e6-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a25e6-171">textEncoding</span><span class="sxs-lookup"><span data-stu-id="a25e6-171">textEncoding</span></span>|<span data-ttu-id="a25e6-172">Určuje znakovou sadu kódování má být použit pro generování zpráv v rámci vazby.</span><span class="sxs-lookup"><span data-stu-id="a25e6-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a25e6-173">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="a25e6-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a25e6-174">-UnicodeFffeTextEncoding: Unicode BigEndian kódování.</span><span class="sxs-lookup"><span data-stu-id="a25e6-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="a25e6-175">-Utf16TextEncoding: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="a25e6-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="a25e6-176">-Utf8TextEncoding: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="a25e6-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="a25e6-177">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="a25e6-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="a25e6-178">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a25e6-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="a25e6-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="a25e6-179">transactionFlow</span></span>|<span data-ttu-id="a25e6-180">Logická hodnota, která určuje, zda vazby podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="a25e6-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="a25e6-181">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a25e6-181">The default is `false`.</span></span>|  
|<span data-ttu-id="a25e6-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="a25e6-182">useDefaultWebProxy</span></span>|<span data-ttu-id="a25e6-183">Logická hodnota, která určuje, jestli je použít server proxy protokolu HTTP pro automatickou konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="a25e6-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="a25e6-184">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="a25e6-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a25e6-185">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a25e6-185">Child Elements</span></span>  
  
|<span data-ttu-id="a25e6-186">Prvek</span><span class="sxs-lookup"><span data-stu-id="a25e6-186">Element</span></span>|<span data-ttu-id="a25e6-187">Popis</span><span class="sxs-lookup"><span data-stu-id="a25e6-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a25e6-188">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="a25e6-188">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="a25e6-189">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="a25e6-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="a25e6-190">Tento element je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a25e6-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="a25e6-191">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="a25e6-191">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="a25e6-192">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="a25e6-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a25e6-193">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a25e6-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="a25e6-194">reliableSession</span><span class="sxs-lookup"><span data-stu-id="a25e6-194">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="a25e6-195">Určuje, pokud jsou určeny spolehlivé relace mezi koncovými body kanálu.</span><span class="sxs-lookup"><span data-stu-id="a25e6-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a25e6-196">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a25e6-196">Parent Elements</span></span>  
  
|<span data-ttu-id="a25e6-197">Prvek</span><span class="sxs-lookup"><span data-stu-id="a25e6-197">Element</span></span>|<span data-ttu-id="a25e6-198">Popis</span><span class="sxs-lookup"><span data-stu-id="a25e6-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a25e6-199">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a25e6-199">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="a25e6-200">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="a25e6-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a25e6-201">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a25e6-201">Remarks</span></span>  
 <span data-ttu-id="a25e6-202">`WSHttpBinding` Je podobná `BasicHttpBinding` , ale poskytuje další funkce, webové služby.</span><span class="sxs-lookup"><span data-stu-id="a25e6-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="a25e6-203">Pomocí přenosového protokolu HTTP a poskytuje zabezpečení zpráv, jak to dělá BasicHttpBinding, ale také poskytuje transakce, spolehlivého zasílání zpráv a WS-Addressing, buď povolen ve výchozím nastavení, nebo dostupné prostřednictvím nastavení jeden ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a25e6-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a25e6-204">Příklad</span><span class="sxs-lookup"><span data-stu-id="a25e6-204">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a25e6-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="a25e6-205">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement>  
 [<span data-ttu-id="a25e6-206">Vazby</span><span class="sxs-lookup"><span data-stu-id="a25e6-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a25e6-207">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="a25e6-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a25e6-208">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="a25e6-208">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a25e6-209">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a25e6-209">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
