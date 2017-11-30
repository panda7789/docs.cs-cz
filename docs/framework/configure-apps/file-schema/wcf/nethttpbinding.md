---
title: '&lt;netHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7054102af46badc46ee7f987355cfce36860c6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltnethttpbindinggt"></a><span data-ttu-id="9c418-102">&lt;netHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="9c418-102">&lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="9c418-103">Představuje vazbu, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby můžete použít ke konfiguraci a vystavit koncové body, které mohou komunikovat prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c418-103">Represents a binding that a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service can use to configure and expose endpoints that are able to communicate over HTTP.</span></span> <span data-ttu-id="9c418-104">Při použití s duplexního kontraktu, webové sokety se bude používat, v opačném případě se použije protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c418-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTP will be used.</span></span>  
  
 <span data-ttu-id="9c418-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9c418-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9c418-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="9c418-106">\<bindings></span></span>  
<span data-ttu-id="9c418-107">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9c418-107">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c418-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c418-108">Syntax</span></span>  

```xml  
<netHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Binary/Text/Mtom"  
       name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
              textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message   
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                            clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</netHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="9c418-109">Typ</span><span class="sxs-lookup"><span data-stu-id="9c418-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c418-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9c418-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9c418-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9c418-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c418-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="9c418-112">Attributes</span></span>  
  
|<span data-ttu-id="9c418-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="9c418-113">Attribute</span></span>|<span data-ttu-id="9c418-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9c418-114">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="9c418-115">Logická hodnota, která určuje, zda klient přijímá soubory cookie a rozšiřuje je na dalších požadavků.</span><span class="sxs-lookup"><span data-stu-id="9c418-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="9c418-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="9c418-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9c418-117">Tuto vlastnost lze použít při používání ASMX webové služby, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="9c418-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="9c418-118">Tímto způsobem mohou být jisti, že soubory cookie, kterou vrátil server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="9c418-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="9c418-119">Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="9c418-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="9c418-120">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="9c418-120">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9c418-121">Internetových prostředků je místní, pokud má místní adresy.</span><span class="sxs-lookup"><span data-stu-id="9c418-121">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="9c418-122">Místní adresa je ten, který je na stejném počítači, místní síti LAN nebo intranetu a identifikuje, syntakticky, absenci tečkou (.) jako identifikátory URI "http://webserver/" a "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="9c418-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="9c418-123">Nastavení tento atribut určuje, zda koncové body nakonfigurované BasicHttpBinding používat proxy server při přístupu k místním prostředkům.</span><span class="sxs-lookup"><span data-stu-id="9c418-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="9c418-124">Pokud tento atribut je `true`, požadavky k místním prostředkům Internetu Nepoužívat proxy server.</span><span class="sxs-lookup"><span data-stu-id="9c418-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="9c418-125">Použijte název hostitele (místo localhost), pokud chcete klientům jít přes proxy server při posuzování ke službám ve stejném počítači, když tento atribut je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="9c418-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="9c418-126">Když tento atribut je `false`, jsou vytvářeny všechny požadavky Internetu prostřednictvím proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="9c418-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="9c418-127">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="9c418-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9c418-128">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9c418-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9c418-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9c418-129">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="9c418-130">Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="9c418-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="9c418-131">Tento atribut je typu `System.ServiceModel.HostnameComparisonMode`, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="9c418-131">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="9c418-132">Výchozí hodnota je `StrongWildcard`>, který ignoruje název hostitele se shodují.</span><span class="sxs-lookup"><span data-stu-id="9c418-132">The default value is `StrongWildcard`>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="9c418-133">Celočíselná hodnota, která určuje maximální množství paměti přidělené pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu.</span><span class="sxs-lookup"><span data-stu-id="9c418-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="9c418-134">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="9c418-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="9c418-135">Správci vyrovnávacích minimalizuje náklady na používání vyrovnávací paměti pomocí fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9c418-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="9c418-136">Vyrovnávací paměti se vyžadují zpracování zpráv službou, při které pocházejí z kanálu.</span><span class="sxs-lookup"><span data-stu-id="9c418-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="9c418-137">Pokud ve fondu vyrovnávací paměti při zpracování zprávy zatížení není dostatek paměti, musí správce vyrovnávací paměť přidělit další paměť z haldy CLR, což zvyšuje režii kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="9c418-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="9c418-138">Rozsáhlé přidělení z paměti haldy CLR je jako ukazatel toho, že je příliš malá velikost fondu vyrovnávací paměti a že výkon lze zvýšit pomocí větší přidělení zvýšením limit určený tento atribut.</span><span class="sxs-lookup"><span data-stu-id="9c418-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="9c418-139">Celočíselná hodnota, která určuje maximální velikost v bajtech vyrovnávací paměti, která ukládá zprávy, když jsou zpracovávány pro koncovým bodem nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="9c418-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="9c418-140">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="9c418-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="9c418-141">Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která lze přijímat pomocí kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="9c418-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9c418-142">Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je příliš velké vzhledem k příjemce.</span><span class="sxs-lookup"><span data-stu-id="9c418-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="9c418-143">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="9c418-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9c418-144">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="9c418-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="9c418-145">Definuje kodér použitá ke kódování zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9c418-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="9c418-146">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="9c418-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9c418-147">-Text: Pomocí kodéru text zprávy.</span><span class="sxs-lookup"><span data-stu-id="9c418-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="9c418-148">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="9c418-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="9c418-149">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="9c418-149">The default is Text.</span></span> <span data-ttu-id="9c418-150">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="9c418-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="9c418-151">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="9c418-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9c418-152">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="9c418-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9c418-153">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="9c418-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="9c418-154">Kromě toho je tento název jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="9c418-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="9c418-155">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="9c418-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9c418-156">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9c418-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="9c418-157">Určuje obor názvů XML vazby.</span><span class="sxs-lookup"><span data-stu-id="9c418-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="9c418-158">Výchozí hodnota je "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="9c418-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="9c418-159">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="9c418-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="9c418-160">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="9c418-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9c418-161">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9c418-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9c418-162">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9c418-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="9c418-163">Identifikátor URI, který obsahuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c418-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="9c418-164">Pokud `useSystemWebProxy` je nastaven na `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="9c418-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="9c418-165">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="9c418-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="9c418-166">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="9c418-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9c418-167">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9c418-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9c418-168">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9c418-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="9c418-169">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="9c418-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9c418-170">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9c418-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9c418-171">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9c418-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="9c418-172">Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="9c418-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9c418-173">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="9c418-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9c418-174">-BigEndianUnicode: Unicode BigEndian kódování.</span><span class="sxs-lookup"><span data-stu-id="9c418-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="9c418-175">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="9c418-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="9c418-176">-UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="9c418-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="9c418-177">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="9c418-177">The default is UTF8.</span></span> <span data-ttu-id="9c418-178">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="9c418-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="9c418-179">Platná <xref:System.ServiceModel.TransferMode> hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu na požadavek nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="9c418-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="9c418-180">Logická hodnota, která určuje, zda má být použita automatické konfigurace proxy serveru HTTP systému, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9c418-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="9c418-181">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="9c418-181">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="9c418-182">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9c418-182">Child Elements</span></span>  
  
|<span data-ttu-id="9c418-183">Prvek</span><span class="sxs-lookup"><span data-stu-id="9c418-183">Element</span></span>|<span data-ttu-id="9c418-184">Popis</span><span class="sxs-lookup"><span data-stu-id="9c418-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c418-185">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="9c418-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="9c418-186">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="9c418-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="9c418-187">Tento element je typu `NetHttpSecurityElement`.</span><span class="sxs-lookup"><span data-stu-id="9c418-187">This element is of type `NetHttpSecurityElement`.</span></span>|  
|[<span data-ttu-id="9c418-188">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="9c418-188">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="9c418-189">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="9c418-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9c418-190">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="9c418-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c418-191">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9c418-191">Parent Elements</span></span>  
  
|<span data-ttu-id="9c418-192">Prvek</span><span class="sxs-lookup"><span data-stu-id="9c418-192">Element</span></span>|<span data-ttu-id="9c418-193">Popis</span><span class="sxs-lookup"><span data-stu-id="9c418-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c418-194">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="9c418-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="9c418-195">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="9c418-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c418-196">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c418-196">Remarks</span></span>  
 <span data-ttu-id="9c418-197">Vazeb NetHttpBinding využívá protokol HTTP jako přenosu pro odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="9c418-197">The NetHttpBinding uses HTTP as the transport for sending messages.</span></span> <span data-ttu-id="9c418-198">Při použití s duplexního kontraktu, použije se Websocket.</span><span class="sxs-lookup"><span data-stu-id="9c418-198">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="9c418-199">Při použití s kontraktu požadavku a odpovědi, které NetHttpBinding budou chovat jako BasicHttpBinding pomocí binární kodéru.</span><span class="sxs-lookup"><span data-stu-id="9c418-199">When used with a request-reply contract NetHttpBinding will behave like a BasicHttpBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="9c418-200">Zabezpečení je ve výchozím nastavení vypnuté, ale můžete přidat nastavení atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) podřízený element hodnotu jinou než `None`.</span><span class="sxs-lookup"><span data-stu-id="9c418-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="9c418-201">"Text" kódování a UTF-8 text zprávy kódování ve výchozím nastavení používá.</span><span class="sxs-lookup"><span data-stu-id="9c418-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c418-202">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c418-202">Example</span></span>  
 <span data-ttu-id="9c418-203">Následující příklad ukazuje použití <xref:System.ServiceModel.NetHttpBinding> , poskytuje HTTP komunikace a maximální vzájemnou funkční spolupráci s první - a second - generation webové služby.</span><span class="sxs-lookup"><span data-stu-id="9c418-203">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="9c418-204">Vazba je zadána v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="9c418-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="9c418-205">Typ vazby je zadán pomocí `binding` atribut `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9c418-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="9c418-206">Pokud chcete nakonfigurovat základní vazby a některá z jeho nastavení změnit, je nutné definovat Konfigurace vazeb.</span><span class="sxs-lookup"><span data-stu-id="9c418-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="9c418-207">Koncový bod musí odkazovat Konfigurace vazeb podle názvu pomocí `bindingConfiguration` atribut `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace pro službu.</span><span class="sxs-lookup"><span data-stu-id="9c418-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpBinding>  
        <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="9c418-208">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c418-208">Example</span></span>  
 <span data-ttu-id="9c418-209">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="9c418-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9c418-210">Funkce z předchozího příkladu můžete provést bindingConfiguration odebráním adresa koncového bodu a název frm vazby.</span><span class="sxs-lookup"><span data-stu-id="9c418-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9c418-211">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9c418-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c418-212">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c418-212">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="9c418-213">Vazby</span><span class="sxs-lookup"><span data-stu-id="9c418-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9c418-214">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="9c418-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="9c418-215">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="9c418-215">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="9c418-216">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="9c418-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
