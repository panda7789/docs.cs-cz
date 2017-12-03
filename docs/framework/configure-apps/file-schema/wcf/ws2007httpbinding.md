---
title: "&lt;– ws2007HttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6af846937556968067d89a279e595374cce99ae4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltws2007httpbindinggt"></a><span data-ttu-id="53ffe-102">&lt;– ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="53ffe-102">&lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="53ffe-103">Definuje vazbu umožňuje vzájemnou spolupráci, která poskytuje podporu pro správné verze <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, a <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="53ffe-103">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="53ffe-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="53ffe-104">\<system.serviceModel></span></span>  
<span data-ttu-id="53ffe-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="53ffe-105">\<bindings></span></span>  
<span data-ttu-id="53ffe-106">\<– ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="53ffe-106">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ffe-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53ffe-107">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>  
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
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53ffe-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53ffe-108">Attributes and Elements</span></span>  
 <span data-ttu-id="53ffe-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53ffe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53ffe-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="53ffe-110">Attributes</span></span>  
  
|<span data-ttu-id="53ffe-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="53ffe-111">Attribute</span></span>|<span data-ttu-id="53ffe-112">Popis</span><span class="sxs-lookup"><span data-stu-id="53ffe-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="53ffe-113">Hodnota, která určuje, jestli klient přijímá soubory cookie a rozšiřuje je na dalších požadavků.</span><span class="sxs-lookup"><span data-stu-id="53ffe-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="53ffe-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="53ffe-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="53ffe-115">Pokud při práci s ASP.NET – webové služby (ASMX), které používají soubory cookie, můžete tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="53ffe-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="53ffe-116">Tím se zajistí, že soubory cookie, které vrací na server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="53ffe-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="53ffe-117">Hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="53ffe-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="53ffe-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="53ffe-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="53ffe-119">A <xref:System.TimeSpan> hodnotu, která určuje časový interval pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="53ffe-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="53ffe-120">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="53ffe-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="53ffe-121">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="53ffe-121">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="53ffe-122">Určuje režim porovnání hostname HTTP použitá k analýze identifikátory Uniform Resource (Identifier).</span><span class="sxs-lookup"><span data-stu-id="53ffe-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="53ffe-123">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="53ffe-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="53ffe-124">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.</span><span class="sxs-lookup"><span data-stu-id="53ffe-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="53ffe-125">Velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="53ffe-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="53ffe-126">Výchozí hodnota je 524,288 bajtů (512 × 1 024 jednotek).</span><span class="sxs-lookup"><span data-stu-id="53ffe-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="53ffe-127">Mnoho částí [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="53ffe-127">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="53ffe-128">Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je náročné, jako je uvolňování paměti pro vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="53ffe-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="53ffe-129">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu.</span><span class="sxs-lookup"><span data-stu-id="53ffe-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="53ffe-130">Tím je zabráněno režijní náklady v vytváření a zničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="53ffe-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="53ffe-131">Maximální velikost zprávy, v bajtech, včetně hlavičky, které jsou konfigurovány pomocí této vazby kanál může přijímat.</span><span class="sxs-lookup"><span data-stu-id="53ffe-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="53ffe-132">Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="53ffe-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="53ffe-133">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="53ffe-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="53ffe-134">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="53ffe-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="53ffe-135">Definuje kodér použitá ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="53ffe-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="53ffe-136">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="53ffe-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="53ffe-137">-   `Text`: Pomocí kodéru text zprávy.</span><span class="sxs-lookup"><span data-stu-id="53ffe-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="53ffe-138">-   `Mtom`: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="53ffe-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="53ffe-139">Výchozí hodnota je `Text`.</span><span class="sxs-lookup"><span data-stu-id="53ffe-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="53ffe-140">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="53ffe-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="53ffe-141">Název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="53ffe-141">The configuration name of the binding.</span></span> <span data-ttu-id="53ffe-142">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="53ffe-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="53ffe-143">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="53ffe-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="53ffe-144">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="53ffe-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="53ffe-145">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="53ffe-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="53ffe-146">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="53ffe-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="53ffe-147">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="53ffe-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="53ffe-148">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="53ffe-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="53ffe-149">Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="53ffe-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="53ffe-150">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="53ffe-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="53ffe-151">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="53ffe-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="53ffe-152">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="53ffe-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="53ffe-153">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="53ffe-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="53ffe-154">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="53ffe-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="53ffe-155">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="53ffe-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="53ffe-156">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="53ffe-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="53ffe-157">Určuje znakovou sadu kódování použité pro generování zpráv v rámci vazby.</span><span class="sxs-lookup"><span data-stu-id="53ffe-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="53ffe-158">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="53ffe-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="53ffe-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian kódování.</span><span class="sxs-lookup"><span data-stu-id="53ffe-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="53ffe-160">-   `Utf16TextEncoding`: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="53ffe-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="53ffe-161">-   `Utf8TextEncoding`: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="53ffe-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="53ffe-162">Výchozí hodnota je `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="53ffe-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="53ffe-163">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="53ffe-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="53ffe-164">Hodnota, která určuje, zda vazby podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="53ffe-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="53ffe-165">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="53ffe-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="53ffe-166">Hodnota, která určuje, jestli je použít server proxy protokolu HTTP pro automatickou konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="53ffe-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="53ffe-167">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="53ffe-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53ffe-168">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53ffe-168">Child Elements</span></span>  
  
|<span data-ttu-id="53ffe-169">Prvek</span><span class="sxs-lookup"><span data-stu-id="53ffe-169">Element</span></span>|<span data-ttu-id="53ffe-170">Popis</span><span class="sxs-lookup"><span data-stu-id="53ffe-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53ffe-171">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="53ffe-171">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="53ffe-172">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="53ffe-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="53ffe-173">Tento element je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="53ffe-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="53ffe-174">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="53ffe-174">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="53ffe-175">Definuje omezení na složitosti protokolu SOAP zprávy, které může zpracovat koncových bodů s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="53ffe-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="53ffe-176">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="53ffe-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="53ffe-177">reliableSession</span><span class="sxs-lookup"><span data-stu-id="53ffe-177">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="53ffe-178">Určuje, zda jsou určeny spolehlivé relace mezi koncovými body kanálu.</span><span class="sxs-lookup"><span data-stu-id="53ffe-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53ffe-179">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53ffe-179">Parent Elements</span></span>  
  
|<span data-ttu-id="53ffe-180">Prvek</span><span class="sxs-lookup"><span data-stu-id="53ffe-180">Element</span></span>|<span data-ttu-id="53ffe-181">Popis</span><span class="sxs-lookup"><span data-stu-id="53ffe-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53ffe-182">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="53ffe-182">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="53ffe-183">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="53ffe-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53ffe-184">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53ffe-184">Remarks</span></span>  
 <span data-ttu-id="53ffe-185">`WS2007HttpBinding` Přidá poskytované systémem vazbu podobná `WSHttpBinding` ale používá organizace pro standardní verze protokoly ReliableSession, zabezpečení a TransactionFlow rozvoj z strukturovaných informace standardy (OASIS).</span><span class="sxs-lookup"><span data-stu-id="53ffe-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="53ffe-186">Při použití této vazbě je potřeba žádné změny objektu modelu, nebo výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="53ffe-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53ffe-187">Příklad</span><span class="sxs-lookup"><span data-stu-id="53ffe-187">Example</span></span>  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
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
                    proxyAddress="http://www.contoso.com"  
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
           </ws2007HttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53ffe-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="53ffe-188">See Also</span></span>  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [<span data-ttu-id="53ffe-189">Vazby</span><span class="sxs-lookup"><span data-stu-id="53ffe-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="53ffe-190">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="53ffe-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="53ffe-191">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="53ffe-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="53ffe-192">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="53ffe-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
