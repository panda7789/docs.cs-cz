---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: ab8dca7f7065d7c174e38ad3a88ea15e39351bed
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202048"
---
# \<basicHttpBinding>
<span data-ttu-id="9d531-101">Představuje vazbu, kterou může služba Windows Communication Foundation (WCF) použít ke konfiguraci a zpřístupnění koncových bodů, které mohou komunikovat s webovými službami a klienty na bázi ASMX a dalšími službami, které odpovídají profilu WS-I Basic Profile 1,1.</span><span class="sxs-lookup"><span data-stu-id="9d531-101">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="9d531-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d531-102">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d531-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9d531-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9d531-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9d531-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d531-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d531-105">Attributes</span></span>  
  
|<span data-ttu-id="9d531-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="9d531-106">Attribute</span></span>|<span data-ttu-id="9d531-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9d531-107">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="9d531-108">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="9d531-108">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="9d531-109">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="9d531-109">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9d531-110">Tuto vlastnost lze použít při práci s webovými službami ASMX, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="9d531-110">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="9d531-111">Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="9d531-111">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="9d531-112">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="9d531-112">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="9d531-113">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="9d531-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9d531-114">Internetový prostředek je místní, pokud má místní adresu.</span><span class="sxs-lookup"><span data-stu-id="9d531-114">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="9d531-115">Místní adresa je jedna, která je ve stejném počítači, v místní síti LAN nebo intranetu a je označena syntakticky nedostatečným obdobím (.) jako v identifikátorech URI `http://webserver/` a `http://localhost/` .</span><span class="sxs-lookup"><span data-stu-id="9d531-115">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs `http://webserver/` and `http://localhost/`.</span></span><br /><br /> <span data-ttu-id="9d531-116">Nastavením tohoto atributu určíte, zda jsou koncové body nakonfigurované pomocí BasicHttpBinding používány při přístupu k místním prostředkům proxy server.</span><span class="sxs-lookup"><span data-stu-id="9d531-116">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="9d531-117">Pokud je tento atribut `true` , požadavky na místní prostředky sítě Internet nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="9d531-117">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="9d531-118">Použijte název hostitele (nikoli localhost), pokud chcete, aby klienti procházeli prostřednictvím proxy serveru při komunikaci se službami ve stejném počítači, na kterém je tento atribut nastavený `true` .</span><span class="sxs-lookup"><span data-stu-id="9d531-118">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="9d531-119">Pokud je tento atribut `false` , všechny požadavky na Internet se provádí prostřednictvím proxy server.</span><span class="sxs-lookup"><span data-stu-id="9d531-119">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="9d531-120"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="9d531-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9d531-121">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="9d531-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9d531-122">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9d531-122">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="9d531-123">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="9d531-123">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="9d531-124">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode> , který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="9d531-124">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="9d531-125">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="9d531-125">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="9d531-126">Celočíselná hodnota, která určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu.</span><span class="sxs-lookup"><span data-stu-id="9d531-126">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="9d531-127">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="9d531-127">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="9d531-128">Správce vyrovnávací paměti minimalizuje náklady na používání vyrovnávacích pamětí pomocí fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="9d531-128">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="9d531-129">Vyrovnávací paměti jsou požadovány ke zpracování zpráv, když se dostanou z kanálu.</span><span class="sxs-lookup"><span data-stu-id="9d531-129">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="9d531-130">Pokud ve fondu vyrovnávací paměti není dostatek paměti pro zpracování zatížení zprávy, Správce vyrovnávací paměti musí přidělit další paměť z haldy CLR, což zvyšuje režii uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9d531-130">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="9d531-131">Rozsáhlá alokace z haldy uvolňování CLR je indikace, že velikost fondu vyrovnávací paměti je příliš malá a výkon lze zlepšit větším přidělením zvýšením limitu určeného tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="9d531-131">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="9d531-132">Celočíselná hodnota, která určuje maximální velikost vyrovnávací paměti v bajtech, která ukládá zprávy, když jsou zpracovávány pro koncový bod nakonfigurovaný pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="9d531-132">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="9d531-133">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="9d531-133">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="9d531-134">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček, pro zprávu, která se dá přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="9d531-134">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9d531-135">Odesilatel obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="9d531-135">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="9d531-136">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="9d531-136">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9d531-137">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="9d531-137">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="9d531-138">Definuje kodér použitý ke kódování zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="9d531-138">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="9d531-139">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="9d531-139">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9d531-140">-Text: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="9d531-140">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="9d531-141">-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).</span><span class="sxs-lookup"><span data-stu-id="9d531-141">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="9d531-142">Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="9d531-142">The default is Text.</span></span> <span data-ttu-id="9d531-143">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="9d531-143">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="9d531-144">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="9d531-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9d531-145">Tato hodnota by měla být jedinečná mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="9d531-145">This value should be unique among bindings of the same type.</span></span> <span data-ttu-id="9d531-146">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="9d531-146">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9d531-147">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9d531-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="9d531-148"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="9d531-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9d531-149">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="9d531-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9d531-150">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9d531-150">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="9d531-151">Identifikátor URI, který obsahuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="9d531-151">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="9d531-152">Pokud `useSystemWebProxy` je parametr nastaven na hodnotu `true` , musí být toto nastavení `null` .</span><span class="sxs-lookup"><span data-stu-id="9d531-152">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="9d531-153">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="9d531-153">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="9d531-154"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="9d531-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9d531-155">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="9d531-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9d531-156">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9d531-156">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="9d531-157"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="9d531-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9d531-158">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="9d531-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9d531-159">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9d531-159">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="9d531-160">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="9d531-160">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9d531-161">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="9d531-161">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9d531-162">-BigEndianUnicode: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="9d531-162">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="9d531-163">-Unicode: 16 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="9d531-163">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="9d531-164">-UTF8:8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="9d531-164">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="9d531-165">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="9d531-165">The default is UTF8.</span></span> <span data-ttu-id="9d531-166">Tento atribut je typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="9d531-166">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="9d531-167">Platná <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány v žádosti nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9d531-167">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="9d531-168">Logická hodnota určující, zda má být k dispozici automaticky konfigurovaný proxy server HTTP systému, je-li k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9d531-168">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="9d531-169">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="9d531-169">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d531-170">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9d531-170">Child Elements</span></span>  
  
|<span data-ttu-id="9d531-171">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d531-171">Element</span></span>|<span data-ttu-id="9d531-172">Popis</span><span class="sxs-lookup"><span data-stu-id="9d531-172">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="9d531-173">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="9d531-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="9d531-174">Tento prvek je typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="9d531-174">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="9d531-175">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="9d531-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9d531-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="9d531-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d531-177">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9d531-177">Parent Elements</span></span>  
  
|<span data-ttu-id="9d531-178">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d531-178">Element</span></span>|<span data-ttu-id="9d531-179">Popis</span><span class="sxs-lookup"><span data-stu-id="9d531-179">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="9d531-180">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="9d531-180">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d531-181">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d531-181">Remarks</span></span>  
 <span data-ttu-id="9d531-182">BasicHttpBinding používá protokol HTTP jako přenos pro posílání zpráv SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="9d531-182">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="9d531-183">Služba může tuto vazbu použít k vystavování koncových bodů, které odpovídají normě WS-I BP 1,1, například k tomu, že spotřebovávají klienti ASMX.</span><span class="sxs-lookup"><span data-stu-id="9d531-183">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="9d531-184">Podobně může klient použít BasicHttpBinding ke komunikaci se službami, které zveřejňují koncové body, které jsou v souladu s WS-I BP 1,1, jako jsou webové služby nebo služby nakonfigurované s BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="9d531-184">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="9d531-185">Zabezpečení je ve výchozím nastavení vypnuté, ale je možné ho přidat nastavením atributu Mode [\<security>](security-of-basichttpbinding.md) podřízeného prvku na jinou hodnotu než `None` .</span><span class="sxs-lookup"><span data-stu-id="9d531-185">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="9d531-186">Ve výchozím nastavení používá kódování textové zprávy a kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9d531-186">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d531-187">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d531-187">Example</span></span>  
 <span data-ttu-id="9d531-188">Následující příklad ukazuje použití <xref:System.ServiceModel.BasicHttpBinding> , které poskytuje komunikaci HTTP a maximální interoperabilitu s prvními a druhými webovými službami.</span><span class="sxs-lookup"><span data-stu-id="9d531-188">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="9d531-189">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="9d531-189">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="9d531-190">Typ vazby je určen pomocí `binding` atributu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9d531-190">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="9d531-191">Pokud chcete nakonfigurovat základní vazbu a změnit některá její nastavení, je nutné definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="9d531-191">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="9d531-192">Koncový bod musí odkazovat na konfiguraci vazby podle názvu pomocí `bindingConfiguration` atributu `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="9d531-192">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="9d531-193">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d531-193">Example</span></span>  
 <span data-ttu-id="9d531-194">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="9d531-194">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9d531-195">Funkčnost z předchozího příkladu se dá provést odebráním bindingConfiguration z adresy koncového bodu a názvu z vazby.</span><span class="sxs-lookup"><span data-stu-id="9d531-195">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
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
  
 <span data-ttu-id="9d531-196">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9d531-196">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d531-197">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d531-197">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="9d531-198">Vazby</span><span class="sxs-lookup"><span data-stu-id="9d531-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9d531-199">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="9d531-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9d531-200">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9d531-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
