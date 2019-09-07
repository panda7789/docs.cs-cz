---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 0f0dc3ebe34ea45c1b464ff4fe437694ff4761f0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399063"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="19702-101">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="19702-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="19702-102">Definuje interoperabilní vazbu, která poskytuje podporu pro správné verze <xref:System.ServiceModel.WSHttpBinding.Security%2A>prvků, <xref:System.ServiceModel.ReliableSession>a <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> vazby.</span><span class="sxs-lookup"><span data-stu-id="19702-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
<span data-ttu-id="19702-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="19702-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="19702-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="19702-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="19702-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="19702-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="19702-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007HttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="19702-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19702-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19702-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19702-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="19702-108">Attributes and Elements</span></span>  
 <span data-ttu-id="19702-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="19702-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19702-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="19702-110">Attributes</span></span>  
  
|<span data-ttu-id="19702-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="19702-111">Attribute</span></span>|<span data-ttu-id="19702-112">Popis</span><span class="sxs-lookup"><span data-stu-id="19702-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="19702-113">Hodnota, která určuje, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="19702-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="19702-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="19702-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="19702-115">Tuto vlastnost můžete použít při práci s ASP.NET webovými službami (ASMX), které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="19702-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="19702-116">Tím se zajistí, že soubory cookie, které server vrátí, se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="19702-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="19702-117">Hodnota, která označuje, zda se má obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="19702-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="19702-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="19702-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="19702-119"><xref:System.TimeSpan> Hodnota, která určuje časový interval pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="19702-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="19702-120">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="19702-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19702-121">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19702-121">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="19702-122">Určuje režim porovnání názvů hostitelů HTTP, který se používá k analýze identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="19702-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="19702-123">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="19702-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="19702-124">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="19702-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="19702-125">Maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="19702-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="19702-126">Výchozí hodnota je 524 288 bajtů (512 × 1 024).</span><span class="sxs-lookup"><span data-stu-id="19702-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="19702-127">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="19702-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="19702-128">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné, stejně jako uvolňování paměti pro vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="19702-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="19702-129">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a po dokončení vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="19702-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="19702-130">Tím se vyhnete režie při vytváření a ničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="19702-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="19702-131">Maximální velikost zprávy (v bajtech), která je v bajtech nakonfigurovaná pomocí této vazby, může získat.</span><span class="sxs-lookup"><span data-stu-id="19702-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="19702-132">Odesílatel zprávy překračující toto omezení obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="19702-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="19702-133">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="19702-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="19702-134">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="19702-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="19702-135">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="19702-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="19702-136">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="19702-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="19702-137">-   `Text`: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="19702-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="19702-138">-   `Mtom`: Použijte kodér 1,0 (pro organizaci přenosu zpráv).</span><span class="sxs-lookup"><span data-stu-id="19702-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="19702-139">Výchozí hodnota je `Text`.</span><span class="sxs-lookup"><span data-stu-id="19702-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="19702-140">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="19702-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="19702-141">Název konfigurace vazby</span><span class="sxs-lookup"><span data-stu-id="19702-141">The configuration name of the binding.</span></span> <span data-ttu-id="19702-142">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="19702-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="19702-143">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="19702-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="19702-144">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="19702-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="19702-145"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="19702-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="19702-146">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="19702-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19702-147">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19702-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="19702-148">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="19702-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="19702-149">Pokud `useSystemWebProxy` má `true`parametr hodnotu, musí být `null`toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="19702-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="19702-150">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="19702-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="19702-151"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="19702-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="19702-152">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="19702-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19702-153">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19702-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="19702-154"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="19702-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="19702-155">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="19702-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="19702-156">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="19702-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="19702-157">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="19702-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="19702-158">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="19702-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="19702-159">-   `UnicodeFffeTextEncoding`: Kódování Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="19702-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="19702-160">-   `Utf16TextEncoding`: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="19702-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="19702-161">-   `Utf8TextEncoding`: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="19702-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="19702-162">Výchozí hodnota je `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="19702-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="19702-163">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="19702-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="19702-164">Hodnota, která určuje, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="19702-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="19702-165">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="19702-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="19702-166">Hodnota, která určuje, zda je použit automaticky konfigurovaný proxy server HTTP.</span><span class="sxs-lookup"><span data-stu-id="19702-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="19702-167">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="19702-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19702-168">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="19702-168">Child Elements</span></span>  
  
|<span data-ttu-id="19702-169">Prvek</span><span class="sxs-lookup"><span data-stu-id="19702-169">Element</span></span>|<span data-ttu-id="19702-170">Popis</span><span class="sxs-lookup"><span data-stu-id="19702-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19702-171">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="19702-171">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="19702-172">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="19702-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="19702-173">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="19702-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="19702-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="19702-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="19702-175">Definuje omezení složitosti zpráv SOAP, které mohou koncových bodů nakonfigurovaných pomocí této vazby zpracovat.</span><span class="sxs-lookup"><span data-stu-id="19702-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="19702-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="19702-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="19702-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="19702-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="19702-178">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="19702-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19702-179">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="19702-179">Parent Elements</span></span>  
  
|<span data-ttu-id="19702-180">Prvek</span><span class="sxs-lookup"><span data-stu-id="19702-180">Element</span></span>|<span data-ttu-id="19702-181">Popis</span><span class="sxs-lookup"><span data-stu-id="19702-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19702-182">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="19702-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="19702-183">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="19702-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19702-184">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19702-184">Remarks</span></span>  
 <span data-ttu-id="19702-185">Přidá vazbu poskytnutou systémem, která `WSHttpBinding` je podobná, ale používá organizaci ke zvyšování standardních verzí Oasis (Structured Information Standards) pro ReliableSession, zabezpečení a TransactionFlow protokoly. `WS2007HttpBinding`</span><span class="sxs-lookup"><span data-stu-id="19702-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="19702-186">Při použití této vazby nejsou vyžadovány žádné změny v objektovém modelu ani výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="19702-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19702-187">Příklad</span><span class="sxs-lookup"><span data-stu-id="19702-187">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19702-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19702-188">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="19702-189">Vazby</span><span class="sxs-lookup"><span data-stu-id="19702-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="19702-190">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="19702-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="19702-191">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="19702-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="19702-192">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="19702-192">\<binding></span></span>](../../../misc/binding.md)
