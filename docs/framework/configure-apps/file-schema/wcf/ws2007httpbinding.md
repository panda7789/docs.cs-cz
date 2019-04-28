---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 9caba8dfc848a2463b1fa482ccaf55288d96af29
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670323"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="cdb56-101">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="cdb56-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="cdb56-102">Definuje interoperabilní vazbu, která poskytuje podporu pro správné verze prvků <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, a <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="cdb56-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="cdb56-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cdb56-103">\<system.serviceModel></span></span>  
<span data-ttu-id="cdb56-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="cdb56-104">\<bindings></span></span>  
<span data-ttu-id="cdb56-105">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="cdb56-105">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb56-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdb56-106">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>
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
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdb56-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cdb56-107">Attributes and Elements</span></span>  
 <span data-ttu-id="cdb56-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cdb56-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdb56-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="cdb56-109">Attributes</span></span>  
  
|<span data-ttu-id="cdb56-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="cdb56-110">Attribute</span></span>|<span data-ttu-id="cdb56-111">Popis</span><span class="sxs-lookup"><span data-stu-id="cdb56-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="cdb56-112">Hodnota, která určuje, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="cdb56-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="cdb56-113">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="cdb56-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="cdb56-114">Tuto vlastnost můžete použít, když pracujete s webovými službami ASP.NET (ASMX), které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="cdb56-114">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="cdb56-115">Tím se zajistí, že soubory cookie, které vrací na server se automaticky zkopírují do všechny budoucí požadavky za danou službu.</span><span class="sxs-lookup"><span data-stu-id="cdb56-115">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="cdb56-116">Hodnota, která označuje, zda obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="cdb56-116">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="cdb56-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="cdb56-117">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="cdb56-118">A <xref:System.TimeSpan> hodnota, která určuje časový interval pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="cdb56-118">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="cdb56-119">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cdb56-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cdb56-120">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cdb56-120">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="cdb56-121">Určuje režim porovnání jména hostitele HTTP použitá k analýze Uniform Resource Identifier (identifikátory URI).</span><span class="sxs-lookup"><span data-stu-id="cdb56-121">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="cdb56-122">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="cdb56-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="cdb56-123">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="cdb56-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="cdb56-124">Velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="cdb56-124">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="cdb56-125">Výchozí hodnota je 524,288 bajtů (512 x 1 024 jednotek).</span><span class="sxs-lookup"><span data-stu-id="cdb56-125">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="cdb56-126">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cdb56-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="cdb56-127">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladná, stejně jako uvolňování paměti pro vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cdb56-127">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="cdb56-128">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ji použít a vrátit do fondu, jakmile budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="cdb56-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="cdb56-129">Tím se vyhnete režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cdb56-129">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="cdb56-130">Maximální velikost v bajtech, včetně záhlaví, které můžou přijímat kanál nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="cdb56-130">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="cdb56-131">Odesílatel zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="cdb56-131">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="cdb56-132">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="cdb56-132">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="cdb56-133">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="cdb56-133">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="cdb56-134">Definuje kodér pro kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="cdb56-134">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="cdb56-135">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="cdb56-135">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cdb56-136">-   `Text`: Použijte kodér textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="cdb56-136">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="cdb56-137">-   `Mtom`: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="cdb56-137">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="cdb56-138">Výchozí hodnota je `Text`.</span><span class="sxs-lookup"><span data-stu-id="cdb56-138">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="cdb56-139">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="cdb56-139">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="cdb56-140">Název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="cdb56-140">The configuration name of the binding.</span></span> <span data-ttu-id="cdb56-141">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="cdb56-141">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="cdb56-142">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="cdb56-142">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="cdb56-143">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="cdb56-143">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="cdb56-144">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="cdb56-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="cdb56-145">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cdb56-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cdb56-146">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cdb56-146">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="cdb56-147">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="cdb56-147">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="cdb56-148">Pokud `useSystemWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="cdb56-148">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="cdb56-149">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="cdb56-149">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="cdb56-150">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="cdb56-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="cdb56-151">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cdb56-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cdb56-152">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cdb56-152">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="cdb56-153">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="cdb56-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="cdb56-154">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cdb56-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cdb56-155">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cdb56-155">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="cdb56-156">Určuje znakovou sadu kódování pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="cdb56-156">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="cdb56-157">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="cdb56-157">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cdb56-158">-   `UnicodeFffeTextEncoding`: Big Endian kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="cdb56-158">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="cdb56-159">-   `Utf16TextEncoding`: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="cdb56-159">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="cdb56-160">-   `Utf8TextEncoding`: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="cdb56-160">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="cdb56-161">Výchozí hodnota je `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="cdb56-161">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="cdb56-162">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="cdb56-162">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="cdb56-163">Hodnota, která určuje, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="cdb56-163">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="cdb56-164">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="cdb56-164">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="cdb56-165">Hodnota, která určuje, zda se používá v systému automaticky nakonfigurovaný proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="cdb56-165">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="cdb56-166">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="cdb56-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdb56-167">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cdb56-167">Child Elements</span></span>  
  
|<span data-ttu-id="cdb56-168">Prvek</span><span class="sxs-lookup"><span data-stu-id="cdb56-168">Element</span></span>|<span data-ttu-id="cdb56-169">Popis</span><span class="sxs-lookup"><span data-stu-id="cdb56-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdb56-170">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="cdb56-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="cdb56-171">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="cdb56-171">Defines the security settings for the binding.</span></span> <span data-ttu-id="cdb56-172">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="cdb56-172">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="cdb56-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cdb56-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="cdb56-174">Definuje omezení složitosti zpráv SOAP, které může zpracovat nakonfigurované s touto vazbou koncové body.</span><span class="sxs-lookup"><span data-stu-id="cdb56-174">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="cdb56-175">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="cdb56-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="cdb56-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="cdb56-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="cdb56-177">Určuje, zda jsou vytvořeny spolehlivé relace mezi koncovými body kanálu.</span><span class="sxs-lookup"><span data-stu-id="cdb56-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdb56-178">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cdb56-178">Parent Elements</span></span>  
  
|<span data-ttu-id="cdb56-179">Prvek</span><span class="sxs-lookup"><span data-stu-id="cdb56-179">Element</span></span>|<span data-ttu-id="cdb56-180">Popis</span><span class="sxs-lookup"><span data-stu-id="cdb56-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdb56-181">\<bindings></span><span class="sxs-lookup"><span data-stu-id="cdb56-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="cdb56-182">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="cdb56-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdb56-183">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cdb56-183">Remarks</span></span>  
 <span data-ttu-id="cdb56-184">`WS2007HttpBinding` Přidá vazeb poskytovaných systémem podobný `WSHttpBinding` , ale používá organizace pro rozvoj z strukturovaných informace standardy OASIS (Organization) standardní verze protokoly TransactionFlow, ReliableSession a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cdb56-184">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="cdb56-185">Při použití této vazby nejsou potřeba žádné změny k objektu modelu nebo výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="cdb56-185">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdb56-186">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdb56-186">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
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
  
## <a name="see-also"></a><span data-ttu-id="cdb56-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdb56-187">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="cdb56-188">Vazby</span><span class="sxs-lookup"><span data-stu-id="cdb56-188">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="cdb56-189">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="cdb56-189">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cdb56-190">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="cdb56-190">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="cdb56-191">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="cdb56-191">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
