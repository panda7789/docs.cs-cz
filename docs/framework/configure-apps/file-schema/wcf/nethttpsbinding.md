---
title: '&lt;netHttpsBinding&gt;'
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: fb279321cccc325700ac18697d484da20c685c9d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751305"
---
# <a name="ltnethttpsbindinggt"></a><span data-ttu-id="34ee0-102">&lt;netHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="34ee0-102">&lt;netHttpsBinding&gt;</span></span>
<span data-ttu-id="34ee0-103">Představuje vazbu služby Windows Communication Foundation (WCF) můžete použít ke konfiguraci a vystavit koncové body, které mohou komunikovat přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="34ee0-103">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="34ee0-104">Při použití s duplexního kontraktu, webové sokety se bude používat, v opačném případě se použije protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="34ee0-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="34ee0-105">Kořenový Element</span><span class="sxs-lookup"><span data-stu-id="34ee0-105">Root Element</span></span>  
<span data-ttu-id="34ee0-106">Další prvek</span><span class="sxs-lookup"><span data-stu-id="34ee0-106">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34ee0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34ee0-107">Syntax</span></span>  

```xml
<netHttpsBinding>  
  <binding allowCookies="Boolean"  
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
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                 realm="string" />  
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" 
               clientCredentialType="UserName/Certificate"/>  
    </security>  
    <readerQuotas maxArrayLength="Integer" 
                  maxBytesPerRead="Integer" 
                  maxDepth="Integer" 
                  maxNameTableCharCount="Integer" 
                  maxStringContentLength="Integer" />  
  </binding>  
</netHttpsBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="34ee0-108">Typ</span><span class="sxs-lookup"><span data-stu-id="34ee0-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34ee0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="34ee0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="34ee0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="34ee0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34ee0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="34ee0-111">Attributes</span></span>  
  
|<span data-ttu-id="34ee0-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="34ee0-112">Attribute</span></span>|<span data-ttu-id="34ee0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="34ee0-113">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="34ee0-114">Logická hodnota, která určuje, zda klient přijímá soubory cookie a rozšiřuje je na dalších požadavků.</span><span class="sxs-lookup"><span data-stu-id="34ee0-114">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="34ee0-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="34ee0-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="34ee0-116">Tuto vlastnost lze použít při používání ASMX webové služby, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="34ee0-116">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="34ee0-117">Tímto způsobem mohou být jisti, že soubory cookie, kterou vrátil server se automaticky zkopírují do všechny budoucí požadavky pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="34ee0-117">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="34ee0-118">Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="34ee0-118">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="34ee0-119">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="34ee0-119">The default is `false`.</span></span><br /><br /> <span data-ttu-id="34ee0-120">Internetových prostředků je místní, pokud má místní adresy.</span><span class="sxs-lookup"><span data-stu-id="34ee0-120">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="34ee0-121">Místní adresa je ten, který je na stejném počítači, místní síti LAN nebo intranetu a identifikuje, syntakticky, absenci tečkou (.) jako identifikátory URI "http://webserver/"a"http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="34ee0-121">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="34ee0-122">Nastavení tento atribut určuje, zda koncové body nakonfigurované BasicHttpBinding používat proxy server při přístupu k místním prostředkům.</span><span class="sxs-lookup"><span data-stu-id="34ee0-122">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="34ee0-123">Pokud tento atribut je `true`, požadavky k místním prostředkům Internetu Nepoužívat proxy server.</span><span class="sxs-lookup"><span data-stu-id="34ee0-123">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="34ee0-124">Použijte název hostitele (místo localhost), pokud chcete klientům jít přes proxy server při posuzování ke službám ve stejném počítači, když tento atribut je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="34ee0-124">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="34ee0-125">Když tento atribut je `false`, jsou vytvářeny všechny požadavky Internetu prostřednictvím proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="34ee0-125">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="34ee0-126">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="34ee0-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="34ee0-127">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="34ee0-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="34ee0-128">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="34ee0-128">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="34ee0-129">Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="34ee0-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="34ee0-130">Tento atribut je typu `HostnameComparisonMode`, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="34ee0-130">This attribute is of type `HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="34ee0-131">Výchozí hodnota je `StrongWildcard`, který ignoruje název hostitele se shodují.</span><span class="sxs-lookup"><span data-stu-id="34ee0-131">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="34ee0-132">Celočíselná hodnota, která určuje maximální množství paměti přidělené pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu.</span><span class="sxs-lookup"><span data-stu-id="34ee0-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="34ee0-133">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="34ee0-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="34ee0-134">Správci vyrovnávacích minimalizuje náklady na používání vyrovnávací paměti pomocí fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="34ee0-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="34ee0-135">Vyrovnávací paměti se vyžadují zpracování zpráv službou, při které pocházejí z kanálu.</span><span class="sxs-lookup"><span data-stu-id="34ee0-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="34ee0-136">Pokud ve fondu vyrovnávací paměti při zpracování zprávy zatížení není dostatek paměti, musí správce vyrovnávací paměť přidělit další paměť z haldy CLR, což zvyšuje režii kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="34ee0-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="34ee0-137">Rozsáhlé přidělení z paměti haldy CLR je jako ukazatel toho, že je příliš malá velikost fondu vyrovnávací paměti a že výkon lze zvýšit pomocí větší přidělení zvýšením limit určený tento atribut.</span><span class="sxs-lookup"><span data-stu-id="34ee0-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="34ee0-138">Celočíselná hodnota, která určuje maximální velikost v bajtech vyrovnávací paměti, která ukládá zprávy, když jsou zpracovávány pro koncovým bodem nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="34ee0-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="34ee0-139">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="34ee0-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="34ee0-140">Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která lze přijímat pomocí kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="34ee0-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="34ee0-141">Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je příliš velké vzhledem k příjemce.</span><span class="sxs-lookup"><span data-stu-id="34ee0-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="34ee0-142">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="34ee0-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="34ee0-143">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="34ee0-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="34ee0-144">Definuje kodér použitá ke kódování zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="34ee0-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="34ee0-145">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="34ee0-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="34ee0-146">-Text: Pomocí kodéru text zprávy.</span><span class="sxs-lookup"><span data-stu-id="34ee0-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="34ee0-147">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="34ee0-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="34ee0-148">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="34ee0-148">The default is Text.</span></span> <span data-ttu-id="34ee0-149">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="34ee0-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="34ee0-150">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="34ee0-151">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="34ee0-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="34ee0-152">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="34ee0-153">Kromě toho je tento název jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="34ee0-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="34ee0-154">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="34ee0-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="34ee0-155">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="34ee0-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="34ee0-156">Určuje obor názvů XML vazby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="34ee0-157">Výchozí hodnota je "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="34ee0-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="34ee0-158">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="34ee0-159">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="34ee0-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="34ee0-160">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="34ee0-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="34ee0-161">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="34ee0-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="34ee0-162">Identifikátor URI, který obsahuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="34ee0-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="34ee0-163">Pokud `useSystemWebProxy` je nastaven na `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="34ee0-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="34ee0-164">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="34ee0-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="34ee0-165">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="34ee0-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="34ee0-166">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="34ee0-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="34ee0-167">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="34ee0-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="34ee0-168">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="34ee0-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="34ee0-169">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="34ee0-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="34ee0-170">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="34ee0-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="34ee0-171">Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="34ee0-172">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="34ee0-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="34ee0-173">-BigEndianUnicode: Unicode BigEndian kódování.</span><span class="sxs-lookup"><span data-stu-id="34ee0-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="34ee0-174">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="34ee0-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="34ee0-175">-UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="34ee0-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="34ee0-176">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="34ee0-176">The default is UTF8.</span></span> <span data-ttu-id="34ee0-177">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="34ee0-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="34ee0-178">Platná <xref:System.ServiceModel.TransferMode> hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu na požadavek nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="34ee0-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="34ee0-179">Logická hodnota, která určuje, zda má být použita automatické konfigurace proxy serveru HTTP systému, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="34ee0-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="34ee0-180">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="34ee0-180">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="34ee0-181">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="34ee0-181">Child Elements</span></span>  
  
|<span data-ttu-id="34ee0-182">Prvek</span><span class="sxs-lookup"><span data-stu-id="34ee0-182">Element</span></span>|<span data-ttu-id="34ee0-183">Popis</span><span class="sxs-lookup"><span data-stu-id="34ee0-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34ee0-184">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="34ee0-184">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="34ee0-185">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="34ee0-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="34ee0-186">Tento element je typu <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="34ee0-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[<span data-ttu-id="34ee0-187">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="34ee0-187">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="34ee0-188">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="34ee0-189">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="34ee0-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34ee0-190">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="34ee0-190">Parent Elements</span></span>  
  
|<span data-ttu-id="34ee0-191">Prvek</span><span class="sxs-lookup"><span data-stu-id="34ee0-191">Element</span></span>|<span data-ttu-id="34ee0-192">Popis</span><span class="sxs-lookup"><span data-stu-id="34ee0-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34ee0-193">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="34ee0-193">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="34ee0-194">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34ee0-195">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34ee0-195">Remarks</span></span>  
 <span data-ttu-id="34ee0-196">NetHttpsBinding využívá protokol HTTPS jako přenosu pro odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="34ee0-196">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="34ee0-197">Při použití s duplexního kontraktu, použije se Websocket.</span><span class="sxs-lookup"><span data-stu-id="34ee0-197">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="34ee0-198">Při použití s kontraktu požadavku a odpovědi, které NetHttpsBinding budou chovat jako BasicHttpsBinding pomocí binární kodéru.</span><span class="sxs-lookup"><span data-stu-id="34ee0-198">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="34ee0-199">Zabezpečení je ve výchozím nastavení vypnuté, ale můžete přidat nastavení atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) podřízený element hodnotu jinou než `None`.</span><span class="sxs-lookup"><span data-stu-id="34ee0-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="34ee0-200">"Text" kódování a UTF-8 text zprávy kódování ve výchozím nastavení používá.</span><span class="sxs-lookup"><span data-stu-id="34ee0-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34ee0-201">Příklad</span><span class="sxs-lookup"><span data-stu-id="34ee0-201">Example</span></span>  
 <span data-ttu-id="34ee0-202">Následující příklad ukazuje použití <xref:System.ServiceModel.NetHttpBinding> , poskytuje HTTPS komunikace a maximální vzájemnou funkční spolupráci s první - a second - generation webové služby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-202">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="34ee0-203">Vazba je zadána v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="34ee0-204">Typ vazby je zadán pomocí `binding` atribut `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="34ee0-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="34ee0-205">Pokud chcete nakonfigurovat základní vazby a některá z jeho nastavení změnit, je nutné definovat Konfigurace vazeb.</span><span class="sxs-lookup"><span data-stu-id="34ee0-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="34ee0-206">Koncový bod musí odkazovat Konfigurace vazeb podle názvu pomocí `bindingConfiguration` atribut `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace pro službu.</span><span class="sxs-lookup"><span data-stu-id="34ee0-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpsBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpsBinding>  
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
               useDefaultWebProxy="true">  
        <security mode="None" />  
      </binding>  
    </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="34ee0-207">Příklad</span><span class="sxs-lookup"><span data-stu-id="34ee0-207">Example</span></span>  
 <span data-ttu-id="34ee0-208">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="34ee0-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="34ee0-209">Funkce z předchozího příkladu můžete provést bindingConfiguration odebráním adresa koncového bodu a název frm vazby.</span><span class="sxs-lookup"><span data-stu-id="34ee0-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpsBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpsBinding>  
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
     </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="34ee0-210">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="34ee0-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ee0-211">Viz také</span><span class="sxs-lookup"><span data-stu-id="34ee0-211">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="34ee0-212">Vazby</span><span class="sxs-lookup"><span data-stu-id="34ee0-212">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="34ee0-213">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="34ee0-213">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="34ee0-214">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="34ee0-214">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="34ee0-215">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="34ee0-215">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
