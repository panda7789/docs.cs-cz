---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 842f2acb3be03be8171bcf7312f230fc06754511
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84201047"
---
# \<netHttpsBinding>
<span data-ttu-id="5a5f0-101">Představuje vazbu, kterou může služba Windows Communication Foundation (WCF) použít ke konfiguraci a zpřístupnění koncových bodů, které mohou komunikovat přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-101">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="5a5f0-102">Při použití se duplexní smlouvou se použijí webové sokety, jinak se bude používat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-102">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netHttpsBinding>**  

## <a name="syntax"></a><span data-ttu-id="5a5f0-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a5f0-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="5a5f0-104">Typ</span><span class="sxs-lookup"><span data-stu-id="5a5f0-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a5f0-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a5f0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5a5f0-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a5f0-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a5f0-107">Attributes</span></span>  
  
|<span data-ttu-id="5a5f0-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a5f0-108">Attribute</span></span>|<span data-ttu-id="5a5f0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5a5f0-109">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="5a5f0-110">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-110">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="5a5f0-111">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-111">The default is `false`.</span></span><br /><br /> <span data-ttu-id="5a5f0-112">Tuto vlastnost lze použít při práci s webovými službami ASMX, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-112">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="5a5f0-113">Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-113">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="5a5f0-114">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="5a5f0-115">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="5a5f0-116">Internetový prostředek je místní, pokud má místní adresu.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-116">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="5a5f0-117">Místní adresa je jedna, která je ve stejném počítači, v místní síti LAN nebo intranetu a je označena syntakticky nedostatečným obdobím (.) jako v identifikátorech URI `http://webserver/` a `http://localhost/` .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-117">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs `http://webserver/` and `http://localhost/`.</span></span><br /><br /> <span data-ttu-id="5a5f0-118">Nastavením tohoto atributu určíte, zda jsou koncové body nakonfigurované pomocí BasicHttpBinding používány při přístupu k místním prostředkům proxy server.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-118">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="5a5f0-119">Pokud je tento atribut `true` , požadavky na místní prostředky sítě Internet nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-119">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="5a5f0-120">Použijte název hostitele (nikoli localhost), pokud chcete, aby klienti procházeli prostřednictvím proxy serveru při komunikaci se službami ve stejném počítači, na kterém je tento atribut nastavený `true` .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-120">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="5a5f0-121">Pokud je tento atribut `false` , všechny požadavky na Internet se provádí prostřednictvím proxy server.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-121">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="5a5f0-122"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5a5f0-123">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5a5f0-124">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-124">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="5a5f0-125">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-125">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="5a5f0-126">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode> , který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-126">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="5a5f0-127">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-127">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="5a5f0-128">Celočíselná hodnota, která určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-128">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="5a5f0-129">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-129">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="5a5f0-130">Správce vyrovnávací paměti minimalizuje náklady na používání vyrovnávacích pamětí pomocí fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-130">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="5a5f0-131">Vyrovnávací paměti jsou požadovány ke zpracování zpráv, když se dostanou z kanálu.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-131">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="5a5f0-132">Pokud ve fondu vyrovnávací paměti není dostatek paměti pro zpracování zatížení zprávy, Správce vyrovnávací paměti musí přidělit další paměť z haldy CLR, což zvyšuje režii uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-132">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="5a5f0-133">Rozsáhlá alokace z haldy uvolňování CLR je indikace, že velikost fondu vyrovnávací paměti je příliš malá a výkon lze zlepšit větším přidělením zvýšením limitu určeného tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-133">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="5a5f0-134">Celočíselná hodnota, která určuje maximální velikost vyrovnávací paměti v bajtech, která ukládá zprávy, když jsou zpracovávány pro koncový bod nakonfigurovaný pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-134">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="5a5f0-135">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-135">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="5a5f0-136">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček, pro zprávu, která se dá přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-136">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="5a5f0-137">Odesilatel obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-137">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="5a5f0-138">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-138">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="5a5f0-139">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-139">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="5a5f0-140">Definuje kodér použitý ke kódování zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-140">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="5a5f0-141">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="5a5f0-141">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5a5f0-142">-Text: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-142">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="5a5f0-143">-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).</span><span class="sxs-lookup"><span data-stu-id="5a5f0-143">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="5a5f0-144">Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-144">The default is Text.</span></span> <span data-ttu-id="5a5f0-145">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-145">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="5a5f0-146">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5a5f0-147">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5a5f0-148">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-148">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5a5f0-149">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5a5f0-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="5a5f0-150"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5a5f0-151">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5a5f0-152">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-152">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="5a5f0-153">Identifikátor URI, který obsahuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-153">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="5a5f0-154">Pokud `useSystemWebProxy` je parametr nastaven na hodnotu `true` , musí být toto nastavení `null` .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-154">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="5a5f0-155">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-155">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="5a5f0-156"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5a5f0-157">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5a5f0-158">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-158">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="5a5f0-159"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5a5f0-160">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5a5f0-161">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-161">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="5a5f0-162">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-162">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="5a5f0-163">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="5a5f0-163">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5a5f0-164">-BigEndianUnicode: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-164">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="5a5f0-165">-Unicode: 16 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-165">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="5a5f0-166">-UTF8:8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="5a5f0-166">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="5a5f0-167">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-167">The default is UTF8.</span></span> <span data-ttu-id="5a5f0-168">Tento atribut je typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-168">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="5a5f0-169">Platná <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány v žádosti nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-169">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="5a5f0-170">Logická hodnota určující, zda má být k dispozici automaticky konfigurovaný proxy server HTTP systému, je-li k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-170">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="5a5f0-171">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-171">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="5a5f0-172">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a5f0-172">Child Elements</span></span>  
  
|<span data-ttu-id="5a5f0-173">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a5f0-173">Element</span></span>|<span data-ttu-id="5a5f0-174">Description</span><span class="sxs-lookup"><span data-stu-id="5a5f0-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="5a5f0-175">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-175">Defines the security settings for the binding.</span></span> <span data-ttu-id="5a5f0-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-176">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="5a5f0-177">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-177">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5a5f0-178">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-178">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a5f0-179">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a5f0-179">Parent Elements</span></span>  
  
|<span data-ttu-id="5a5f0-180">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a5f0-180">Element</span></span>|<span data-ttu-id="5a5f0-181">Description</span><span class="sxs-lookup"><span data-stu-id="5a5f0-181">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="5a5f0-182">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a5f0-183">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a5f0-183">Remarks</span></span>  
 <span data-ttu-id="5a5f0-184">NetHttpsBinding jako přenos pro posílání zpráv používá protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-184">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="5a5f0-185">Při použití se duplexní smlouvou budou použity webové sokety.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-185">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="5a5f0-186">Při použití se smlouvou požadavek-odpověď NetHttpsBinding se bude chovat jako BasicHttpsBinding s binárním kodérem.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-186">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="5a5f0-187">Zabezpečení je ve výchozím nastavení vypnuté, ale je možné ho přidat nastavením atributu Mode [\<security>](security-of-basichttpbinding.md) podřízeného prvku na jinou hodnotu než `None` .</span><span class="sxs-lookup"><span data-stu-id="5a5f0-187">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="5a5f0-188">Ve výchozím nastavení používá kódování textové zprávy a kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-188">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5f0-189">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a5f0-189">Example</span></span>  
 <span data-ttu-id="5a5f0-190">Následující příklad ukazuje použití <xref:System.ServiceModel.NetHttpBinding> , které poskytuje komunikaci pomocí protokolu HTTPS a maximální interoperabilitu s prvními a druhými webovými službami.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-190">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="5a5f0-191">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-191">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="5a5f0-192">Typ vazby je určen pomocí `binding` atributu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-192">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="5a5f0-193">Pokud chcete nakonfigurovat základní vazbu a změnit některá její nastavení, je nutné definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-193">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="5a5f0-194">Koncový bod musí odkazovat na konfiguraci vazby podle názvu pomocí `bindingConfiguration` atributu `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-194">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5a5f0-195">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a5f0-195">Example</span></span>  
 <span data-ttu-id="5a5f0-196">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-196">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5a5f0-197">Funkčnost z předchozího příkladu se dá provést odebráním bindingConfiguration z adresy koncového bodu a názvu z vazby.</span><span class="sxs-lookup"><span data-stu-id="5a5f0-197">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
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
  
 <span data-ttu-id="5a5f0-198">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5a5f0-198">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5f0-199">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a5f0-199">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="5a5f0-200">Vazby</span><span class="sxs-lookup"><span data-stu-id="5a5f0-200">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5a5f0-201">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5a5f0-201">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5a5f0-202">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5a5f0-202">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
