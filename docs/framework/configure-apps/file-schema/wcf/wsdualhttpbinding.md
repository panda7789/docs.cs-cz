---
title: '&lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a49b534ba22f4ac422eb26885388e24594b49afd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltwsdualhttpbindinggt"></a><span data-ttu-id="4d794-102">&lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="4d794-102">&lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="4d794-103">Definuje vazbu zabezpečené, spolehlivé a vzájemná spolupráce, který je vhodný pro služby duplexní kontrakty nebo komunikaci prostřednictvím protokolu SOAP zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="4d794-103">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="4d794-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4d794-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4d794-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4d794-105">\<bindings></span></span>  
<span data-ttu-id="4d794-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4d794-106">\<wsDualHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d794-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d794-107">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>  
        <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        bypassProxyOnLocal="Boolean"  
        clientBaseAddress="URI"  
        transactionFlow="Boolean"   
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
        proxyAddress="URI"  
  
textEncoding="Unicode/BigEndianUnicode/UTF8"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan" />  
        <security mode="None/Message">  
           <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                negotiateServiceCredential="Boolean"  
                    algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
                </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsDualHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d794-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4d794-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4d794-109">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d794-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d794-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="4d794-110">Attributes</span></span>  
  
|<span data-ttu-id="4d794-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="4d794-111">Attribute</span></span>|<span data-ttu-id="4d794-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4d794-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d794-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="4d794-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="4d794-114">Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="4d794-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="4d794-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="4d794-115">The default is `false`.</span></span>|  
|<span data-ttu-id="4d794-116">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="4d794-116">clientBaseAddress</span></span>|<span data-ttu-id="4d794-117">Identifikátor URI, který nastaví základní adresu, která klient naslouchá odpovědí na zprávy ze služby.</span><span class="sxs-lookup"><span data-stu-id="4d794-117">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="4d794-118">-Li zadána, tato adresa (plus za channelGUID) se používá k naslouchání.</span><span class="sxs-lookup"><span data-stu-id="4d794-118">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="4d794-119">Pokud hodnotu nezadáte, vygeneruje se způsobem specifické pro přenos základní adresu klienta.</span><span class="sxs-lookup"><span data-stu-id="4d794-119">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="4d794-120">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="4d794-120">The default is `null`.</span></span>|  
|<span data-ttu-id="4d794-121">Intervalu</span><span class="sxs-lookup"><span data-stu-id="4d794-121">closeTimeout</span></span>|<span data-ttu-id="4d794-122">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="4d794-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4d794-123">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4d794-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4d794-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4d794-124">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4d794-125">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="4d794-125">hostnameComparisonMode</span></span>|<span data-ttu-id="4d794-126">Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="4d794-126">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="4d794-127">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="4d794-127">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="4d794-128">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.</span><span class="sxs-lookup"><span data-stu-id="4d794-128">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="4d794-129">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4d794-129">maxBufferPoolSize</span></span>|<span data-ttu-id="4d794-130">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="4d794-130">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="4d794-131">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="4d794-131">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="4d794-132">Mnoho části služby Windows Communication Foundation (WCF) pomocí vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4d794-132">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="4d794-133">Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="4d794-133">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4d794-134">S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu.</span><span class="sxs-lookup"><span data-stu-id="4d794-134">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4d794-135">Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4d794-135">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="4d794-136">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4d794-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="4d794-137">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="4d794-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4d794-138">Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4d794-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="4d794-139">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="4d794-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4d794-140">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="4d794-140">The default is 65536.</span></span>|  
|<span data-ttu-id="4d794-141">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="4d794-141">messageEncoding</span></span>|<span data-ttu-id="4d794-142">Definuje kodér použitá ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d794-142">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="4d794-143">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="4d794-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4d794-144">-Text: Pomocí kodéru text zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d794-144">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="4d794-145">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4d794-145">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="4d794-146">-Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="4d794-146">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="4d794-147">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="4d794-147">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="4d794-148">name</span><span class="sxs-lookup"><span data-stu-id="4d794-148">name</span></span>|<span data-ttu-id="4d794-149">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="4d794-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4d794-150">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="4d794-150">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4d794-151">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="4d794-151">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4d794-152">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4d794-152">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="4d794-153">openTimeout</span><span class="sxs-lookup"><span data-stu-id="4d794-153">openTimeout</span></span>|<span data-ttu-id="4d794-154">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="4d794-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4d794-155">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4d794-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4d794-156">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4d794-156">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4d794-157">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="4d794-157">proxyAddress</span></span>|<span data-ttu-id="4d794-158">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="4d794-158">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="4d794-159">Pokud `useDefaultWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="4d794-159">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="4d794-160">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="4d794-160">The default is `null`.</span></span>|  
|<span data-ttu-id="4d794-161">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="4d794-161">receiveTimeout</span></span>|<span data-ttu-id="4d794-162">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="4d794-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4d794-163">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4d794-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4d794-164">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4d794-164">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4d794-165">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="4d794-165">sendTimeout</span></span>|<span data-ttu-id="4d794-166">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="4d794-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4d794-167">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4d794-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4d794-168">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4d794-168">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4d794-169">textEncoding</span><span class="sxs-lookup"><span data-stu-id="4d794-169">textEncoding</span></span>|<span data-ttu-id="4d794-170">Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="4d794-170">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4d794-171">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="4d794-171">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4d794-172">-BigEndianUnicode: Unicode BigEndian kódování.</span><span class="sxs-lookup"><span data-stu-id="4d794-172">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="4d794-173">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="4d794-173">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="4d794-174">-UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="4d794-174">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4d794-175">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="4d794-175">The default is UTF8.</span></span> <span data-ttu-id="4d794-176">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4d794-176">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="4d794-177">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="4d794-177">transactionFlow</span></span>|<span data-ttu-id="4d794-178">Logická hodnota, která určuje, zda vazby podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="4d794-178">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="4d794-179">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="4d794-179">The default is `false`.</span></span>|  
|<span data-ttu-id="4d794-180">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="4d794-180">useDefaultWebProxy</span></span>|<span data-ttu-id="4d794-181">Logická hodnota, která určuje, zda je použít server proxy protokolu HTTP pro automatickou konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="4d794-181">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="4d794-182">Adresa proxy serveru musí být `null` (to znamená, že není nastavena) Pokud tento atribut je `true`.</span><span class="sxs-lookup"><span data-stu-id="4d794-182">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="4d794-183">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="4d794-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d794-184">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d794-184">Child Elements</span></span>  
  
|<span data-ttu-id="4d794-185">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d794-185">Element</span></span>|<span data-ttu-id="4d794-186">Popis</span><span class="sxs-lookup"><span data-stu-id="4d794-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d794-187">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="4d794-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|<span data-ttu-id="4d794-188">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="4d794-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="4d794-189">Tento element je typu <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4d794-189">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="4d794-190">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="4d794-190">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="4d794-191">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="4d794-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4d794-192">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4d794-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="4d794-193">reliableSession</span><span class="sxs-lookup"><span data-stu-id="4d794-193">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="4d794-194">Určuje, pokud jsou určeny spolehlivé relace mezi koncovými body kanálu.</span><span class="sxs-lookup"><span data-stu-id="4d794-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d794-195">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4d794-195">Parent Elements</span></span>  
  
|<span data-ttu-id="4d794-196">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d794-196">Element</span></span>|<span data-ttu-id="4d794-197">Popis</span><span class="sxs-lookup"><span data-stu-id="4d794-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d794-198">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4d794-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="4d794-199">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="4d794-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d794-200">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d794-200">Remarks</span></span>  
 <span data-ttu-id="4d794-201">`WSDualHttpBinding` Poskytuje stejné podporu pro webové služby protokoly, jako `WSHttpBinding`, ale pro použití s duplexní kontrakty.</span><span class="sxs-lookup"><span data-stu-id="4d794-201">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="4d794-202">`WSDualHttpBinding`pouze podporuje zabezpečení protokolu SOAP a vyžaduje spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="4d794-202">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="4d794-203">Tato vazba vyžaduje, aby klient veřejné identifikátor URI, který poskytuje koncový bod zpětného volání pro službu.</span><span class="sxs-lookup"><span data-stu-id="4d794-203">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="4d794-204">To zajišťuje `clientBaseAddress` atribut.</span><span class="sxs-lookup"><span data-stu-id="4d794-204">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="4d794-205">Duální vazbu zpřístupní IP adresu klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="4d794-205">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="4d794-206">Klient musí použít zabezpečení zajistit, že pouze připojení k službám ho vztahy důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="4d794-206">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="4d794-207">Tato vazba umožňuje spolehlivě komunikovat prostřednictvím jednoho nebo více zprostředkovatelů protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4d794-207">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="4d794-208">Ve výchozím nastavení, vygeneruje tuto vazbu runtime zásobníku pomocí protokolu WS-ReliableMessaging pro spolehlivost, WS-zabezpečení pro zabezpečení zpráv a ověřování protokolu HTTP pro doručování zpráv a kódování zpráv Text/XML.</span><span class="sxs-lookup"><span data-stu-id="4d794-208">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d794-209">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d794-209">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsDualHttpBinding>  
    <binding   
        closeTimeout="00:00:10"  
        openTimeout="00:00:20"   
        receiveTimeout="00:00:30"  
        sendTimeout="00:00:40"  
        bypassProxyOnLocal="false"   
        clientBaseAddress="http://localhost:8001/client/"  
        transactionFlow="true"   
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="utf-16"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" />  
        <security mode="None">  
            <message clientCredentialType="None"  
                negotiateServiceCredential="false"  
                algorithmSuite="Aes128" />  
        </security>  
    </binding>  
</wsDualHttpBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d794-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d794-210">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>  
 [<span data-ttu-id="4d794-211">Vazby</span><span class="sxs-lookup"><span data-stu-id="4d794-211">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4d794-212">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="4d794-212">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="4d794-213">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="4d794-213">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="4d794-214">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="4d794-214">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
