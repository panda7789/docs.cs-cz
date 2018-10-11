---
title: '&lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 95af699592492d4abfdf7867e8a207db7490ccdf
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086827"
---
# <a name="ltws2007httpbindinggt"></a><span data-ttu-id="b1206-102">&lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="b1206-102">&lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="b1206-103">Definuje interoperabilní vazbu, která poskytuje podporu pro správné verze prvků <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, a <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="b1206-103">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="b1206-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b1206-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b1206-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b1206-105">\<bindings></span></span>  
<span data-ttu-id="b1206-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="b1206-106">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1206-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1206-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1206-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1206-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b1206-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1206-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1206-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1206-110">Attributes</span></span>  
  
|<span data-ttu-id="b1206-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b1206-111">Attribute</span></span>|<span data-ttu-id="b1206-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b1206-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="b1206-113">Hodnota, která určuje, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="b1206-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="b1206-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b1206-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b1206-115">Tuto vlastnost můžete použít, když pracujete s webovými službami ASP.NET (ASMX), které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="b1206-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="b1206-116">Tím se zajistí, že soubory cookie, které vrací na server se automaticky zkopírují do všechny budoucí požadavky za danou službu.</span><span class="sxs-lookup"><span data-stu-id="b1206-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="b1206-117">Hodnota, která označuje, zda obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="b1206-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="b1206-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b1206-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="b1206-119">A <xref:System.TimeSpan> hodnota, která určuje časový interval pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="b1206-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="b1206-120">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b1206-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b1206-121">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b1206-121">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="b1206-122">Určuje režim porovnání jména hostitele HTTP použitá k analýze Uniform Resource Identifier (identifikátory URI).</span><span class="sxs-lookup"><span data-stu-id="b1206-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="b1206-123">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="b1206-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b1206-124">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="b1206-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="b1206-125">Velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="b1206-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="b1206-126">Výchozí hodnota je 524,288 bajtů (512 x 1 024 jednotek).</span><span class="sxs-lookup"><span data-stu-id="b1206-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="b1206-127">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b1206-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="b1206-128">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladná, stejně jako uvolňování paměti pro vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b1206-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="b1206-129">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ji použít a vrátit do fondu, jakmile budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="b1206-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="b1206-130">Tím se vyhnete režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b1206-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="b1206-131">Maximální velikost v bajtech, včetně záhlaví, které můžou přijímat kanál nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b1206-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="b1206-132">Odesílatel zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b1206-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="b1206-133">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="b1206-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b1206-134">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="b1206-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="b1206-135">Definuje kodér pro kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="b1206-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="b1206-136">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="b1206-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b1206-137">-   `Text`: Použijte kodér textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="b1206-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="b1206-138">-   `Mtom`: Použijte kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="b1206-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="b1206-139">Výchozí hodnota je `Text`.</span><span class="sxs-lookup"><span data-stu-id="b1206-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="b1206-140">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="b1206-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="b1206-141">Název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="b1206-141">The configuration name of the binding.</span></span> <span data-ttu-id="b1206-142">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="b1206-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b1206-143">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="b1206-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b1206-144">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b1206-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="b1206-145">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="b1206-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b1206-146">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b1206-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b1206-147">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b1206-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="b1206-148">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="b1206-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="b1206-149">Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="b1206-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="b1206-150">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="b1206-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b1206-151">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="b1206-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b1206-152">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b1206-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b1206-153">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b1206-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b1206-154">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="b1206-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b1206-155">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b1206-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b1206-156">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b1206-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="b1206-157">Určuje znakovou sadu kódování pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="b1206-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="b1206-158">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="b1206-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b1206-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian kódování.</span><span class="sxs-lookup"><span data-stu-id="b1206-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="b1206-160">-   `Utf16TextEncoding`: kódování 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="b1206-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="b1206-161">-   `Utf8TextEncoding`: 8 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="b1206-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="b1206-162">Výchozí hodnota je `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="b1206-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="b1206-163">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b1206-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="b1206-164">Hodnota, která určuje, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="b1206-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="b1206-165">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b1206-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="b1206-166">Hodnota, která určuje, zda se používá v systému automaticky nakonfigurovaný proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="b1206-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="b1206-167">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="b1206-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1206-168">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1206-168">Child Elements</span></span>  
  
|<span data-ttu-id="b1206-169">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1206-169">Element</span></span>|<span data-ttu-id="b1206-170">Popis</span><span class="sxs-lookup"><span data-stu-id="b1206-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1206-171">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="b1206-171">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="b1206-172">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="b1206-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="b1206-173">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b1206-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="b1206-174">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="b1206-174">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="b1206-175">Definuje omezení složitosti zpráv SOAP, které může zpracovat nakonfigurované s touto vazbou koncové body.</span><span class="sxs-lookup"><span data-stu-id="b1206-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="b1206-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b1206-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="b1206-177">reliableSession</span><span class="sxs-lookup"><span data-stu-id="b1206-177">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="b1206-178">Určuje, zda jsou vytvořeny spolehlivé relace mezi koncovými body kanálu.</span><span class="sxs-lookup"><span data-stu-id="b1206-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1206-179">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1206-179">Parent Elements</span></span>  
  
|<span data-ttu-id="b1206-180">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1206-180">Element</span></span>|<span data-ttu-id="b1206-181">Popis</span><span class="sxs-lookup"><span data-stu-id="b1206-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1206-182">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b1206-182">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="b1206-183">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="b1206-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1206-184">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1206-184">Remarks</span></span>  
 <span data-ttu-id="b1206-185">`WS2007HttpBinding` Přidá vazeb poskytovaných systémem podobný `WSHttpBinding` , ale používá organizace pro rozvoj z strukturovaných informace standardy OASIS (Organization) standardní verze protokoly TransactionFlow, ReliableSession a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b1206-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="b1206-186">Při použití této vazby nejsou potřeba žádné změny k objektu modelu nebo výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="b1206-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1206-187">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1206-187">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1206-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1206-188">See Also</span></span>  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [<span data-ttu-id="b1206-189">Vazby</span><span class="sxs-lookup"><span data-stu-id="b1206-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b1206-190">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b1206-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b1206-191">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b1206-191">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="b1206-192">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="b1206-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
