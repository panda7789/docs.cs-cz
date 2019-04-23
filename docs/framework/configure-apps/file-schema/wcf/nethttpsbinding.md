---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 400444c0346b47d86ad799d4f8f2e7531b74a94c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195225"
---
# <a name="nethttpsbinding"></a><span data-ttu-id="6a771-101">\<netHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="6a771-101">\<netHttpsBinding></span></span>
<span data-ttu-id="6a771-102">Představuje vazbu, která služby Windows Communication Foundation (WCF) můžete použít ke konfiguraci a zpřístupňují koncové body, které jsou schopné komunikovat přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6a771-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="6a771-103">Při použití s duplexní kontrakt, se použije webové sokety, jinak se použije protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6a771-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="6a771-104">Kořenový Element</span><span class="sxs-lookup"><span data-stu-id="6a771-104">Root Element</span></span>  
<span data-ttu-id="6a771-105">Další prvek</span><span class="sxs-lookup"><span data-stu-id="6a771-105">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a771-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a771-106">Syntax</span></span>  
  
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
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpsBinding>
```  
  
## <a name="type"></a><span data-ttu-id="6a771-107">Type</span><span class="sxs-lookup"><span data-stu-id="6a771-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a771-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6a771-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6a771-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6a771-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a771-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="6a771-110">Attributes</span></span>  
  
|<span data-ttu-id="6a771-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="6a771-111">Attribute</span></span>|<span data-ttu-id="6a771-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6a771-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="6a771-113">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="6a771-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="6a771-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="6a771-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="6a771-115">Tuto vlastnost můžete použít, když pracujete s ASMX webovými službami, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="6a771-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="6a771-116">Tímto způsobem máte jistotu, že soubory cookie vrácený ze serveru se automaticky zkopírují do všechny budoucí požadavky za danou službu.</span><span class="sxs-lookup"><span data-stu-id="6a771-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="6a771-117">Logická hodnota určující, zda obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="6a771-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="6a771-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="6a771-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="6a771-119">Je místní, pokud má místní adresu internetového zdroji.</span><span class="sxs-lookup"><span data-stu-id="6a771-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="6a771-120">Místní adresa je ten, který je na stejném počítači, místní síti LAN nebo intranetu a identifikuje, syntakticky, absenci tečkou (.) jako identifikátory URI "http://webserver/" a "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="6a771-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="6a771-121">Nastavení tohoto atributu určuje, zda se BasicHttpBinding nakonfigurované koncové body používat proxy server při přístupu k místním prostředkům.</span><span class="sxs-lookup"><span data-stu-id="6a771-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="6a771-122">Pokud tento atribut je `true`, požadavky na místní internetové prostředky Nepoužívat proxy server.</span><span class="sxs-lookup"><span data-stu-id="6a771-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="6a771-123">Název hostitele (místo místního hostitele), pokud chcete klientům přejít přes proxy server, když mluvíme ke službám ve stejném počítači, když tento atribut je nastaven na použití `true`.</span><span class="sxs-lookup"><span data-stu-id="6a771-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="6a771-124">Pokud tento atribut je `false`, všechny požadavky na Internetu se provádějí přes proxy server.</span><span class="sxs-lookup"><span data-stu-id="6a771-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="6a771-125">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="6a771-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6a771-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a771-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a771-127">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a771-127">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="6a771-128">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="6a771-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="6a771-129">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="6a771-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="6a771-130">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="6a771-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="6a771-131">Celočíselná hodnota, která určuje maximální množství paměti přidělené správci vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu pamětí.</span><span class="sxs-lookup"><span data-stu-id="6a771-131">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="6a771-132">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="6a771-132">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="6a771-133">Správce vyrovnávací paměti minimalizuje náklady na použití vyrovnávací paměti pomocí fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6a771-133">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="6a771-134">Vyrovnávací paměti jsou potřeba ke zpracování zpráv ve službě, když pocházejí z kanálu.</span><span class="sxs-lookup"><span data-stu-id="6a771-134">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="6a771-135">Pokud ve fondu vyrovnávací paměti pro zpracování zátěže zpráva není dostatek paměti, musí správce vyrovnávací paměti přidělit další paměti z haldy CLR, což zvyšuje úroveň režie uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6a771-135">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="6a771-136">Rozsáhlé přidělení v haldě uvolňování paměti modulu CLR slouží jako ukazatel toho, že je příliš malá velikost fondu vyrovnávací paměti a že výkon lze zvýšit pomocí větší přidělení zvýšením limit specifikovaný pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="6a771-136">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="6a771-137">Celočíselná hodnota, která určuje maximální velikost v bajtech, vyrovnávací paměti, která ukládá zprávy při jejich zpracování pro koncovým bodem nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="6a771-137">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="6a771-138">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="6a771-138">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="6a771-139">Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="6a771-139">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="6a771-140">Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je moc velká pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="6a771-140">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="6a771-141">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="6a771-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6a771-142">Výchozí hodnota je 65 536 bajty.</span><span class="sxs-lookup"><span data-stu-id="6a771-142">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="6a771-143">Definuje kodér použít ke kódování zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6a771-143">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="6a771-144">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="6a771-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6a771-145">-Text: Použijte kodér textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="6a771-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="6a771-146">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="6a771-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="6a771-147">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="6a771-147">The default is Text.</span></span> <span data-ttu-id="6a771-148">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="6a771-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="6a771-149">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="6a771-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6a771-150">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="6a771-150">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6a771-151">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="6a771-151">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="6a771-152">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="6a771-152">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="6a771-153">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="6a771-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6a771-154">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a771-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="6a771-155">Určuje obor názvů XML vazby.</span><span class="sxs-lookup"><span data-stu-id="6a771-155">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="6a771-156">Výchozí hodnota je "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="6a771-156">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="6a771-157">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="6a771-157">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="6a771-158">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="6a771-158">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6a771-159">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a771-159">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a771-160">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a771-160">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="6a771-161">Identifikátor URI, který obsahuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="6a771-161">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="6a771-162">Pokud `useSystemWebProxy` je nastavena na `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="6a771-162">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="6a771-163">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="6a771-163">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6a771-164">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="6a771-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6a771-165">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a771-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a771-166">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="6a771-166">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="6a771-167">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="6a771-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6a771-168">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a771-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a771-169">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a771-169">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="6a771-170">Nastaví znakovou sadu kódování, které má být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="6a771-170">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="6a771-171">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="6a771-171">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6a771-172">-BigEndianUnicode: Kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="6a771-172">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="6a771-173">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="6a771-173">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="6a771-174">-   UTF8: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="6a771-174">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="6a771-175">Použije se UTF8.</span><span class="sxs-lookup"><span data-stu-id="6a771-175">The default is UTF8.</span></span> <span data-ttu-id="6a771-176">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="6a771-176">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="6a771-177">Platný <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu na požadavku nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="6a771-177">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="6a771-178">Logická hodnota, která určuje, zda má být použita automaticky nakonfigurovaný proxy HTTP systému, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6a771-178">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="6a771-179">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="6a771-179">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="6a771-180">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6a771-180">Child Elements</span></span>  
  
|<span data-ttu-id="6a771-181">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a771-181">Element</span></span>|<span data-ttu-id="6a771-182">Popis</span><span class="sxs-lookup"><span data-stu-id="6a771-182">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a771-183">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="6a771-183">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="6a771-184">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="6a771-184">Defines the security settings for the binding.</span></span> <span data-ttu-id="6a771-185">Tento prvek je typu <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="6a771-185">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|<span data-ttu-id="6a771-186">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a771-186">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="6a771-187">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="6a771-187">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6a771-188">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="6a771-188">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a771-189">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6a771-189">Parent Elements</span></span>  
  
|<span data-ttu-id="6a771-190">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a771-190">Element</span></span>|<span data-ttu-id="6a771-191">Popis</span><span class="sxs-lookup"><span data-stu-id="6a771-191">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a771-192">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6a771-192">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="6a771-193">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="6a771-193">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a771-194">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a771-194">Remarks</span></span>  
 <span data-ttu-id="6a771-195">NetHttpsBinding používá protokol HTTPS k přenosu pro odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="6a771-195">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="6a771-196">Při použití s duplexní kontrakt, použije se webové sokety.</span><span class="sxs-lookup"><span data-stu-id="6a771-196">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="6a771-197">Při použití s kontraktem požadavek odpověď, kterou NetHttpsBinding se chovají jako BasicHttpsBinding pomocí binárního kodéru.</span><span class="sxs-lookup"><span data-stu-id="6a771-197">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="6a771-198">Zabezpečení je ve výchozím nastavení vypnuta, ale je možné přidat nastavení atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) podřízený element hodnotu jinou než `None`.</span><span class="sxs-lookup"><span data-stu-id="6a771-198">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="6a771-199">"Text" kódování a UTF-8 text zprávy kódování ve výchozím nastavení používá.</span><span class="sxs-lookup"><span data-stu-id="6a771-199">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a771-200">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a771-200">Example</span></span>  
 <span data-ttu-id="6a771-201">Následující příklad ukazuje použití <xref:System.ServiceModel.NetHttpBinding> poskytující HTTPS komunikace a maximální vzájemná funkční spolupráce s první – a second - generation webové služby.</span><span class="sxs-lookup"><span data-stu-id="6a771-201">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="6a771-202">Vazba je zadán v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="6a771-202">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="6a771-203">Typ vazby je určen pomocí `binding` atribut `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6a771-203">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="6a771-204">Pokud chcete nakonfigurovat základní vazby a některé z nastavení změnit, je potřeba definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="6a771-204">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="6a771-205">Koncový bod musí odkazovat konfigurace vazby podle názvu pomocí `bindingConfiguration` atribut `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace pro službu.</span><span class="sxs-lookup"><span data-stu-id="6a771-205">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="6a771-206">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a771-206">Example</span></span>  
 <span data-ttu-id="6a771-207">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="6a771-207">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6a771-208">Funkce z předchozího příkladu dosáhnete tak, že odeberete bindingConfiguration z adresy koncového bodu a název z vazby.</span><span class="sxs-lookup"><span data-stu-id="6a771-208">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding hostNameComparisonMode="StrongWildcard"
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
  
 <span data-ttu-id="6a771-209">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a771-209">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a771-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a771-210">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="6a771-211">Vazby</span><span class="sxs-lookup"><span data-stu-id="6a771-211">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="6a771-212">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="6a771-212">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6a771-213">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6a771-213">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6a771-214">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="6a771-214">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
