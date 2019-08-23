---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: 2ae8a9d2ad7bf3607394e65570b8961fd2d58606
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919885"
---
# <a name="basichttpbinding"></a><span data-ttu-id="4b61a-101">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4b61a-101">\<basicHttpBinding></span></span>
<span data-ttu-id="4b61a-102">Představuje vazbu, kterou může služba Windows Communication Foundation (WCF) použít ke konfiguraci a zpřístupnění koncových bodů, které mohou komunikovat s webovými službami a klienty na bázi ASMX a dalšími službami, které odpovídají profilu WS-I Basic Profile 1,1.</span><span class="sxs-lookup"><span data-stu-id="4b61a-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="4b61a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4b61a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b61a-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="4b61a-104">\<bindings></span></span>  
<span data-ttu-id="4b61a-105">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4b61a-105">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b61a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b61a-106">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           envelopeVersion="None/Soap11/Soap12"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
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
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b61a-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4b61a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4b61a-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4b61a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b61a-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="4b61a-109">Attributes</span></span>  
  
|<span data-ttu-id="4b61a-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="4b61a-110">Attribute</span></span>|<span data-ttu-id="4b61a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="4b61a-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="4b61a-112">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="4b61a-112">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="4b61a-113">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="4b61a-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="4b61a-114">Tuto vlastnost lze použít při práci s webovými službami ASMX, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="4b61a-114">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="4b61a-115">Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="4b61a-115">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="4b61a-116">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="4b61a-116">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="4b61a-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="4b61a-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="4b61a-118">Internetový prostředek je místní, pokud má místní adresu.</span><span class="sxs-lookup"><span data-stu-id="4b61a-118">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="4b61a-119">Místní adresa je ten, který je na stejném počítači, místní síti LAN nebo intranetu a identifikuje, syntakticky, absenci tečkou (.) jako identifikátory URI "http://webserver/" a "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="4b61a-119">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="4b61a-120">Nastavením tohoto atributu určíte, zda jsou koncové body nakonfigurované pomocí BasicHttpBinding používány při přístupu k místním prostředkům proxy server.</span><span class="sxs-lookup"><span data-stu-id="4b61a-120">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="4b61a-121">Pokud je `true`tento atribut, požadavky na místní prostředky sítě Internet nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="4b61a-121">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="4b61a-122">Použijte název hostitele (nikoli localhost), pokud chcete, aby klienti procházeli prostřednictvím proxy serveru při komunikaci se službami ve stejném počítači, na `true`kterém je tento atribut nastavený.</span><span class="sxs-lookup"><span data-stu-id="4b61a-122">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="4b61a-123">Pokud je `false`tento atribut, všechny požadavky na Internet se provádí prostřednictvím proxy server.</span><span class="sxs-lookup"><span data-stu-id="4b61a-123">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="4b61a-124"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="4b61a-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4b61a-125">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4b61a-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4b61a-126">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4b61a-126">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="4b61a-127">Určuje verzi protokolu SOAP, která se používá pro zprávy zpracovávané touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="4b61a-127">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="4b61a-128">Jediná platná hodnota je Soap11.</span><span class="sxs-lookup"><span data-stu-id="4b61a-128">The only valid value is Soap11.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="4b61a-129">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="4b61a-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="4b61a-130">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="4b61a-130">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="4b61a-131">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="4b61a-131">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="4b61a-132">Celočíselná hodnota, která určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b61a-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="4b61a-133">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="4b61a-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="4b61a-134">Správce vyrovnávací paměti minimalizuje náklady na používání vyrovnávacích pamětí pomocí fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="4b61a-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="4b61a-135">Vyrovnávací paměti jsou požadovány ke zpracování zpráv, když se dostanou z kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b61a-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="4b61a-136">Pokud ve fondu vyrovnávací paměti není dostatek paměti pro zpracování zatížení zprávy, Správce vyrovnávací paměti musí přidělit další paměť z haldy CLR, což zvyšuje režii uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4b61a-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="4b61a-137">Rozsáhlá alokace z haldy uvolňování CLR je indikace, že velikost fondu vyrovnávací paměti je příliš malá a výkon lze zlepšit větším přidělením zvýšením limitu určeného tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="4b61a-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="4b61a-138">Celočíselná hodnota, která určuje maximální velikost vyrovnávací paměti v bajtech, která ukládá zprávy, když jsou zpracovávány pro koncový bod nakonfigurovaný pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="4b61a-139">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="4b61a-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="4b61a-140">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček, pro zprávu, která se dá přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4b61a-141">Odesilatel obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="4b61a-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="4b61a-142">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="4b61a-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4b61a-143">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="4b61a-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="4b61a-144">Definuje kodér použitý ke kódování zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="4b61a-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="4b61a-145">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="4b61a-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4b61a-146">Textové Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b61a-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="4b61a-147">Maximální Použijte kodér 1,0 (pro organizaci přenosu zpráv).</span><span class="sxs-lookup"><span data-stu-id="4b61a-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="4b61a-148">Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="4b61a-148">The default is Text.</span></span> <span data-ttu-id="4b61a-149">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="4b61a-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="4b61a-150">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4b61a-151">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4b61a-152">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="4b61a-153">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="4b61a-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="4b61a-154">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="4b61a-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4b61a-155">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4b61a-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="4b61a-156">Určuje obor názvů XML vazby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="4b61a-157">Výchozí hodnota je "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="4b61a-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="4b61a-158">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="4b61a-159"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="4b61a-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4b61a-160">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4b61a-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4b61a-161">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4b61a-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="4b61a-162">Identifikátor URI, který obsahuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b61a-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="4b61a-163">Pokud `useSystemWebProxy` je parametr nastaven `true`na hodnotu, musí být `null`toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="4b61a-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="4b61a-164">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="4b61a-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="4b61a-165"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="4b61a-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4b61a-166">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4b61a-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4b61a-167">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="4b61a-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="4b61a-168"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="4b61a-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4b61a-169">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4b61a-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4b61a-170">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4b61a-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="4b61a-171">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="4b61a-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4b61a-172">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="4b61a-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4b61a-173">- BigEndianUnicode: Kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="4b61a-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="4b61a-174">Sady 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="4b61a-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="4b61a-175">-   UTF8: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="4b61a-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4b61a-176">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="4b61a-176">The default is UTF8.</span></span> <span data-ttu-id="4b61a-177">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4b61a-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="4b61a-178">Platná <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány v žádosti nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4b61a-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="4b61a-179">Logická hodnota určující, zda má být k dispozici automaticky konfigurovaný proxy server HTTP systému, je-li k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4b61a-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="4b61a-180">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="4b61a-180">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b61a-181">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4b61a-181">Child Elements</span></span>  
  
|<span data-ttu-id="4b61a-182">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b61a-182">Element</span></span>|<span data-ttu-id="4b61a-183">Popis</span><span class="sxs-lookup"><span data-stu-id="4b61a-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b61a-184">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4b61a-184">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="4b61a-185">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="4b61a-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="4b61a-186">Tento prvek je typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4b61a-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="4b61a-187">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b61a-187">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="4b61a-188">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="4b61a-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4b61a-189">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4b61a-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b61a-190">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b61a-190">Parent Elements</span></span>  
  
|<span data-ttu-id="4b61a-191">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b61a-191">Element</span></span>|<span data-ttu-id="4b61a-192">Popis</span><span class="sxs-lookup"><span data-stu-id="4b61a-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b61a-193">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="4b61a-193">\<bindings></span></span>](bindings.md)|<span data-ttu-id="4b61a-194">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="4b61a-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b61a-195">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b61a-195">Remarks</span></span>  
 <span data-ttu-id="4b61a-196">BasicHttpBinding používá protokol HTTP jako přenos pro posílání zpráv SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="4b61a-196">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="4b61a-197">Služba může tuto vazbu použít k vystavování koncových bodů, které odpovídají normě WS-I BP 1,1, například k tomu, že spotřebovávají klienti ASMX.</span><span class="sxs-lookup"><span data-stu-id="4b61a-197">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="4b61a-198">Podobně může klient použít BasicHttpBinding ke komunikaci se službami, které zveřejňují koncové body, které jsou v souladu s WS-I BP 1,1, jako jsou webové služby nebo služby nakonfigurované s BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="4b61a-198">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="4b61a-199">Zabezpečení je ve výchozím nastavení vypnuté, ale je možné ho přidat nastavením atributu `None` [ \<](security-of-basichttpbinding.md) Mode podřízeného prvku Security > na jinou hodnotu než.</span><span class="sxs-lookup"><span data-stu-id="4b61a-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="4b61a-200">Ve výchozím nastavení používá kódování textové zprávy a kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4b61a-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b61a-201">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b61a-201">Example</span></span>  
 <span data-ttu-id="4b61a-202">Následující příklad ukazuje použití <xref:System.ServiceModel.BasicHttpBinding> , které poskytuje komunikaci HTTP a maximální interoperabilitu s prvními a druhými webovými službami.</span><span class="sxs-lookup"><span data-stu-id="4b61a-202">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="4b61a-203">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="4b61a-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="4b61a-204">Typ vazby je určen pomocí `binding` atributu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="4b61a-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="4b61a-205">Pokud chcete nakonfigurovat základní vazbu a změnit některá její nastavení, je nutné definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="4b61a-206">Koncový bod musí odkazovat na konfiguraci vazby podle názvu pomocí `bindingConfiguration` atributu `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="4b61a-207">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b61a-207">Example</span></span>  
 <span data-ttu-id="4b61a-208">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="4b61a-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4b61a-209">Funkčnost z předchozího příkladu se dá provést odebráním bindingConfiguration z adresy koncového bodu a názvu z vazby.</span><span class="sxs-lookup"><span data-stu-id="4b61a-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="4b61a-210">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4b61a-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b61a-211">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b61a-211">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="4b61a-212">Vazby</span><span class="sxs-lookup"><span data-stu-id="4b61a-212">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4b61a-213">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="4b61a-213">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4b61a-214">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4b61a-214">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4b61a-215">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="4b61a-215">\<binding></span></span>](../../../misc/binding.md)
