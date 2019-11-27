---
title: <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
ms.openlocfilehash: 537cbd03e55615bcda2a0ab8e41a171e22a94344
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430854"
---
# <a name="nethttpbinding"></a><span data-ttu-id="e668b-101">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e668b-101">\<netHttpBinding></span></span>
<span data-ttu-id="e668b-102">Představuje vazbu, kterou může služba Windows Communication Foundation (WCF) použít ke konfiguraci a zpřístupnění koncových bodů, které mohou komunikovat přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="e668b-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTP.</span></span> <span data-ttu-id="e668b-103">Při použití se duplexní smlouvou budou použity webové sokety, jinak bude použit protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="e668b-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTP will be used.</span></span>  
  
<span data-ttu-id="e668b-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e668b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e668b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e668b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e668b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e668b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e668b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="e668b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e668b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e668b-108">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
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
</netHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="e668b-109">Typ</span><span class="sxs-lookup"><span data-stu-id="e668b-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e668b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e668b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e668b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e668b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e668b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e668b-112">Attributes</span></span>  
  
|<span data-ttu-id="e668b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e668b-113">Attribute</span></span>|<span data-ttu-id="e668b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e668b-114">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="e668b-115">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="e668b-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="e668b-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="e668b-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e668b-117">Tuto vlastnost lze použít při práci s webovými službami ASMX, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="e668b-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="e668b-118">Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="e668b-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="e668b-119">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="e668b-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="e668b-120">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="e668b-120">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e668b-121">Internetový prostředek je místní, pokud má místní adresu.</span><span class="sxs-lookup"><span data-stu-id="e668b-121">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="e668b-122">Místní adresa je jedna, která je ve stejném počítači, v místní síti LAN nebo intranetu a je identifikována syntakticky nedostatečným obdobím (.) jako v identifikátorech URI "http://webserver/" a "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="e668b-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="e668b-123">Nastavením tohoto atributu určíte, zda jsou koncové body nakonfigurované pomocí BasicHttpBinding používány při přístupu k místním prostředkům proxy server.</span><span class="sxs-lookup"><span data-stu-id="e668b-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="e668b-124">Pokud je tento atribut `true`, požadavky na místní internetové prostředky nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="e668b-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="e668b-125">Použijte název hostitele (nikoli localhost), pokud chcete, aby klienti procházeli prostřednictvím proxy serveru při komunikaci se službami ve stejném počítači, když je tento atribut nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="e668b-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="e668b-126">Pokud je tento atribut `false`, všechny požadavky internetu probíhají prostřednictvím proxy server.</span><span class="sxs-lookup"><span data-stu-id="e668b-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="e668b-127">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="e668b-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e668b-128">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e668b-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e668b-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e668b-129">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="e668b-130">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="e668b-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="e668b-131">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda se k dosažení služby při shodě s identifikátorem URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="e668b-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="e668b-132">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="e668b-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="e668b-133">Celočíselná hodnota, která určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu.</span><span class="sxs-lookup"><span data-stu-id="e668b-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="e668b-134">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="e668b-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="e668b-135">Správce vyrovnávací paměti minimalizuje náklady na používání vyrovnávacích pamětí pomocí fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="e668b-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="e668b-136">Vyrovnávací paměti jsou požadovány ke zpracování zpráv, když se dostanou z kanálu.</span><span class="sxs-lookup"><span data-stu-id="e668b-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="e668b-137">Pokud ve fondu vyrovnávací paměti není dostatek paměti pro zpracování zatížení zprávy, Správce vyrovnávací paměti musí přidělit další paměť z haldy CLR, což zvyšuje režii uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e668b-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="e668b-138">Rozsáhlá alokace z haldy uvolňování CLR je indikace, že velikost fondu vyrovnávací paměti je příliš malá a výkon lze zlepšit větším přidělením zvýšením limitu určeného tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="e668b-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="e668b-139">Celočíselná hodnota, která určuje maximální velikost vyrovnávací paměti v bajtech, která ukládá zprávy, když jsou zpracovávány pro koncový bod nakonfigurovaný pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="e668b-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="e668b-140">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="e668b-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="e668b-141">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček, pro zprávu, která se dá přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="e668b-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="e668b-142">Odesilatel obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="e668b-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="e668b-143">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="e668b-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e668b-144">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="e668b-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="e668b-145">Definuje kodér použitý ke kódování zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="e668b-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="e668b-146">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e668b-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e668b-147">-Text: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="e668b-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="e668b-148">-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).</span><span class="sxs-lookup"><span data-stu-id="e668b-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="e668b-149">Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="e668b-149">The default is Text.</span></span> <span data-ttu-id="e668b-150">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="e668b-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="e668b-151">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="e668b-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e668b-152">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="e668b-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e668b-153">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="e668b-153">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e668b-154">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e668b-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e668b-155">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="e668b-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e668b-156">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e668b-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e668b-157">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e668b-157">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="e668b-158">Identifikátor URI, který obsahuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="e668b-158">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="e668b-159">Pokud je `useSystemWebProxy` nastaveno na `true`, musí být toto nastavení `null`.</span><span class="sxs-lookup"><span data-stu-id="e668b-159">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="e668b-160">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="e668b-160">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e668b-161">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="e668b-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e668b-162">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e668b-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e668b-163">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="e668b-163">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e668b-164">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="e668b-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e668b-165">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e668b-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e668b-166">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e668b-166">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="e668b-167">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="e668b-167">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="e668b-168">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e668b-168">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e668b-169">-BigEndianUnicode: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="e668b-169">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="e668b-170">-Unicode: 16 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="e668b-170">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="e668b-171">-UTF8:8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="e668b-171">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="e668b-172">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="e668b-172">The default is UTF8.</span></span> <span data-ttu-id="e668b-173">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="e668b-173">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="e668b-174">Platná <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány v žádosti nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e668b-174">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="e668b-175">Logická hodnota určující, zda má být k dispozici automaticky konfigurovaný proxy server HTTP systému, je-li k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e668b-175">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="e668b-176">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="e668b-176">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="e668b-177">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e668b-177">Child Elements</span></span>  
  
|<span data-ttu-id="e668b-178">Prvek</span><span class="sxs-lookup"><span data-stu-id="e668b-178">Element</span></span>|<span data-ttu-id="e668b-179">Popis</span><span class="sxs-lookup"><span data-stu-id="e668b-179">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e668b-180">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="e668b-180">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="e668b-181">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="e668b-181">Defines the security settings for the binding.</span></span> <span data-ttu-id="e668b-182">Tento prvek je typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e668b-182">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="e668b-183">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e668b-183">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="e668b-184">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="e668b-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e668b-185">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e668b-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e668b-186">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e668b-186">Parent Elements</span></span>  
  
|<span data-ttu-id="e668b-187">Prvek</span><span class="sxs-lookup"><span data-stu-id="e668b-187">Element</span></span>|<span data-ttu-id="e668b-188">Popis</span><span class="sxs-lookup"><span data-stu-id="e668b-188">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e668b-189">vazby \<></span><span class="sxs-lookup"><span data-stu-id="e668b-189">\<bindings></span></span>](bindings.md)|<span data-ttu-id="e668b-190">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="e668b-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e668b-191">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e668b-191">Remarks</span></span>  
 <span data-ttu-id="e668b-192">NetHttpBinding používá protokol HTTP jako přenos pro posílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="e668b-192">The NetHttpBinding uses HTTP as the transport for sending messages.</span></span> <span data-ttu-id="e668b-193">Při použití se duplexní smlouvou budou použity webové sokety.</span><span class="sxs-lookup"><span data-stu-id="e668b-193">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="e668b-194">Při použití se smlouvou požadavek-odpověď NetHttpBinding se bude chovat jako BasicHttpBinding s binárním kodérem.</span><span class="sxs-lookup"><span data-stu-id="e668b-194">When used with a request-reply contract NetHttpBinding will behave like a BasicHttpBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="e668b-195">Zabezpečení je ve výchozím nastavení vypnuté, ale je možné ho přidat nastavením atributu Mode [\<zabezpečení >](security-of-basichttpbinding.md) podřízeného prvku na jinou hodnotu než `None`.</span><span class="sxs-lookup"><span data-stu-id="e668b-195">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="e668b-196">Ve výchozím nastavení používá kódování textové zprávy a kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e668b-196">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e668b-197">Příklad</span><span class="sxs-lookup"><span data-stu-id="e668b-197">Example</span></span>  
 <span data-ttu-id="e668b-198">Následující příklad ukazuje použití <xref:System.ServiceModel.NetHttpBinding>, které poskytuje komunikaci HTTP a maximální interoperabilitu s prvními a druhými webovými službami.</span><span class="sxs-lookup"><span data-stu-id="e668b-198">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="e668b-199">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="e668b-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="e668b-200">Typ vazby je určen pomocí atributu `binding` `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e668b-200">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="e668b-201">Pokud chcete nakonfigurovat základní vazbu a změnit některá její nastavení, je nutné definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="e668b-201">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="e668b-202">Koncový bod musí odkazovat na konfiguraci vazby podle názvu pomocí atributu `bindingConfiguration` `<endpoint>` elementu, jak je znázorněno v následujícím kódu konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="e668b-202">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
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
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="e668b-203">Příklad</span><span class="sxs-lookup"><span data-stu-id="e668b-203">Example</span></span>  
 <span data-ttu-id="e668b-204">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="e668b-204">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e668b-205">Funkčnost z předchozího příkladu se dá provést odebráním bindingConfiguration z adresy koncového bodu a názvu z vazby.</span><span class="sxs-lookup"><span data-stu-id="e668b-205">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
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
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="e668b-206">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e668b-206">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e668b-207">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e668b-207">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="e668b-208">Vazby</span><span class="sxs-lookup"><span data-stu-id="e668b-208">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e668b-209">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="e668b-209">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e668b-210">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e668b-210">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e668b-211">vazba \<></span><span class="sxs-lookup"><span data-stu-id="e668b-211">\<binding></span></span>](bindings.md)
