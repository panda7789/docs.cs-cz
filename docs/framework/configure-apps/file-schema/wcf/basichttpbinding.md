---
title: '&lt;BasicHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: cde75b44f30d445a00007dac617b898ea5dcb254
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511241"
---
# <a name="ltbasichttpbindinggt"></a><span data-ttu-id="b0bb5-102">&lt;BasicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="b0bb5-102">&lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="b0bb5-103">Představuje vazbu, která služby Windows Communication Foundation (WCF) můžete použít ke konfiguraci a zpřístupňují koncové body, které jsou schopny komunikovat s asmx webovými službami a klienty a dalším službám, které odpovídají WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-103">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="b0bb5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b0bb5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b0bb5-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b0bb5-105">\<bindings></span></span>  
<span data-ttu-id="b0bb5-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b0bb5-106">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0bb5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0bb5-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
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
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0bb5-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b0bb5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b0bb5-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0bb5-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b0bb5-110">Attributes</span></span>  
  
|<span data-ttu-id="b0bb5-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b0bb5-111">Attribute</span></span>|<span data-ttu-id="b0bb5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b0bb5-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="b0bb5-113">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="b0bb5-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b0bb5-115">Tuto vlastnost můžete použít, když pracujete s ASMX webovými službami, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="b0bb5-116">Tímto způsobem máte jistotu, že soubory cookie vrácený ze serveru se automaticky zkopírují do všechny budoucí požadavky za danou službu.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="b0bb5-117">Logická hodnota určující, zda obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="b0bb5-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b0bb5-119">Je místní, pokud má místní adresu internetového zdroji.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="b0bb5-120">Místní adresa je ten, který je na stejném počítači, místní síti LAN nebo intranetu a identifikuje, syntakticky, absenci tečkou (.) jako identifikátory URI "http://webserver/" a "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="b0bb5-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="b0bb5-121">Nastavení tohoto atributu určuje, zda se BasicHttpBinding nakonfigurované koncové body používat proxy server při přístupu k místním prostředkům.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="b0bb5-122">Pokud tento atribut je `true`, požadavky na místní internetové prostředky Nepoužívat proxy server.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="b0bb5-123">Název hostitele (místo místního hostitele), pokud chcete klientům přejít přes proxy server, když mluvíme ke službám ve stejném počítači, když tento atribut je nastaven na použití `true`.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="b0bb5-124">Pokud tento atribut je `false`, všechny požadavky na Internetu se provádějí přes proxy server.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="b0bb5-125">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b0bb5-126">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b0bb5-127">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-127">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="b0bb5-128">Určuje verzi modulu protokolu SOAP, která se používá pro zprávy zpracovávané touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-128">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="b0bb5-129">Jediná platná hodnota je Soap11.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-129">The only valid value is Soap11.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="b0bb5-130">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="b0bb5-131">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b0bb5-132">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="b0bb5-133">Celočíselná hodnota, která určuje maximální množství paměti přidělené správci vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu pamětí.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="b0bb5-134">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="b0bb5-135">Správce vyrovnávací paměti minimalizuje náklady na použití vyrovnávací paměti pomocí fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="b0bb5-136">Vyrovnávací paměti jsou potřeba ke zpracování zpráv ve službě, když pocházejí z kanálu.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="b0bb5-137">Pokud ve fondu vyrovnávací paměti pro zpracování zátěže zpráva není dostatek paměti, musí správce vyrovnávací paměti přidělit další paměti z haldy CLR, což zvyšuje úroveň režie uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="b0bb5-138">Rozsáhlé přidělení v haldě uvolňování paměti modulu CLR slouží jako ukazatel toho, že je příliš malá velikost fondu vyrovnávací paměti a že výkon lze zvýšit pomocí větší přidělení zvýšením limit specifikovaný pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="b0bb5-139">Celočíselná hodnota, která určuje maximální velikost v bajtech, vyrovnávací paměti, která ukládá zprávy při jejich zpracování pro koncovým bodem nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="b0bb5-140">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="b0bb5-141">Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="b0bb5-142">Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je moc velká pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="b0bb5-143">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b0bb5-144">Výchozí hodnota je 65 536 bajty.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="b0bb5-145">Definuje kodér použít ke kódování zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="b0bb5-146">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="b0bb5-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b0bb5-147">-Text: Použijte kodér textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="b0bb5-148">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="b0bb5-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="b0bb5-149">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-149">The default is Text.</span></span> <span data-ttu-id="b0bb5-150">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="b0bb5-151">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b0bb5-152">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b0bb5-153">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="b0bb5-154">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="b0bb5-155">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b0bb5-156">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b0bb5-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="b0bb5-157">Určuje obor názvů XML vazby.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="b0bb5-158">Výchozí hodnota je " http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="b0bb5-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="b0bb5-159">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="b0bb5-160">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b0bb5-161">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b0bb5-162">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="b0bb5-163">Identifikátor URI, který obsahuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="b0bb5-164">Pokud `useSystemWebProxy` je nastavena na `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="b0bb5-165">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b0bb5-166">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b0bb5-167">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b0bb5-168">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b0bb5-169">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b0bb5-170">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b0bb5-171">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="b0bb5-172">Nastaví znakovou sadu kódování, které má být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b0bb5-173">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="b0bb5-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b0bb5-174">-BigEndianUnicode: BigEndian kódování Unicode kódování.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="b0bb5-175">-Unicode: kódování 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="b0bb5-176">– UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="b0bb5-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b0bb5-177">Použije se UTF8.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-177">The default is UTF8.</span></span> <span data-ttu-id="b0bb5-178">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="b0bb5-179">Platný <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu na požadavku nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="b0bb5-180">Logická hodnota, která určuje, zda má být použita automaticky nakonfigurovaný proxy HTTP systému, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="b0bb5-181">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0bb5-182">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b0bb5-182">Child Elements</span></span>  
  
|<span data-ttu-id="b0bb5-183">Prvek</span><span class="sxs-lookup"><span data-stu-id="b0bb5-183">Element</span></span>|<span data-ttu-id="b0bb5-184">Popis</span><span class="sxs-lookup"><span data-stu-id="b0bb5-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0bb5-185">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="b0bb5-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="b0bb5-186">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="b0bb5-187">Tento prvek je typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-187">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="b0bb5-188">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="b0bb5-188">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="b0bb5-189">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b0bb5-190">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0bb5-191">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b0bb5-191">Parent Elements</span></span>  
  
|<span data-ttu-id="b0bb5-192">Prvek</span><span class="sxs-lookup"><span data-stu-id="b0bb5-192">Element</span></span>|<span data-ttu-id="b0bb5-193">Popis</span><span class="sxs-lookup"><span data-stu-id="b0bb5-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0bb5-194">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b0bb5-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="b0bb5-195">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0bb5-196">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0bb5-196">Remarks</span></span>  
 <span data-ttu-id="b0bb5-197">BasicHttpBinding používá protokol HTTP jako přenosu pro odesílání zpráv SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-197">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="b0bb5-198">Služby můžete použít tuto vazbu k zpřístupňují koncové body, které odpovídají WS-I BP 1.1, jako jsou ty, které využívají ASMX klientů.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-198">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="b0bb5-199">Podobně může klient používat BasicHttpBinding komunikace se službami vystavení koncové body, které odpovídají WS-I BP 1.1, jako je například ASMX webové služby nebo služeb nakonfigurovanou BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-199">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="b0bb5-200">Zabezpečení je ve výchozím nastavení vypnuta, ale je možné přidat nastavení atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) podřízený element hodnotu jinou než `None`.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="b0bb5-201">"Text" kódování a UTF-8 text zprávy kódování ve výchozím nastavení používá.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0bb5-202">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bb5-202">Example</span></span>  
 <span data-ttu-id="b0bb5-203">Následující příklad ukazuje použití <xref:System.ServiceModel.BasicHttpBinding> poskytující HTTP komunikace a maximální vzájemná funkční spolupráce s první – a second - generation webové služby.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-203">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="b0bb5-204">Vazba je zadán v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="b0bb5-205">Typ vazby je určen pomocí `binding` atribut `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="b0bb5-206">Pokud chcete nakonfigurovat základní vazby a některé z nastavení změnit, je potřeba definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="b0bb5-207">Koncový bod musí odkazovat konfigurace vazby podle názvu pomocí `bindingConfiguration` atribut `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace pro službu.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
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
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="b0bb5-208">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0bb5-208">Example</span></span>  
 <span data-ttu-id="b0bb5-209">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b0bb5-210">Funkce z předchozího příkladu dosáhnete tak, že odeberete bindingConfiguration z adresy koncového bodu a frm název vazby.</span><span class="sxs-lookup"><span data-stu-id="b0bb5-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
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
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b0bb5-211">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b0bb5-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0bb5-212">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0bb5-212">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="b0bb5-213">Vazby</span><span class="sxs-lookup"><span data-stu-id="b0bb5-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b0bb5-214">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b0bb5-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b0bb5-215">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="b0bb5-215">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b0bb5-216">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="b0bb5-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
