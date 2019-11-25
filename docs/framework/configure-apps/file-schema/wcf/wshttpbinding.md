---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: a71ad2a2279eabbcf917df58d7bedec0e728f9e5
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140389"
---
# <a name="wshttpbinding"></a><span data-ttu-id="6a985-101">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6a985-101">\<wsHttpBinding></span></span>
<span data-ttu-id="6a985-102">Definuje bezpečnou, spolehlivou a interoperabilní vazbu, která je vhodná pro neduplexní kontrakty služeb.</span><span class="sxs-lookup"><span data-stu-id="6a985-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="6a985-103">Vazba implementuje následující specifikace: WS-Reliable Messaging pro spolehlivost a WS-Security pro zabezpečení a ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="6a985-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="6a985-104">Přenos je HTTP a kódování zprávy je kódování text/XML.</span><span class="sxs-lookup"><span data-stu-id="6a985-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
<span data-ttu-id="6a985-105">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6a985-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6a985-106">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6a985-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6a985-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6a985-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6a985-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="6a985-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a985-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a985-109">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
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
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a985-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6a985-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6a985-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6a985-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a985-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="6a985-112">Attributes</span></span>  
  
|<span data-ttu-id="6a985-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="6a985-113">Attribute</span></span>|<span data-ttu-id="6a985-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6a985-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a985-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="6a985-115">allowCookies</span></span>|<span data-ttu-id="6a985-116">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="6a985-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="6a985-117">Výchozí hodnota je false.</span><span class="sxs-lookup"><span data-stu-id="6a985-117">The default is false.</span></span><br /><br /> <span data-ttu-id="6a985-118">Tuto vlastnost lze použít při práci s webovými službami ASMX, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="6a985-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="6a985-119">Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="6a985-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="6a985-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="6a985-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="6a985-121">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="6a985-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="6a985-122">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="6a985-122">The default is `false`.</span></span>|  
|<span data-ttu-id="6a985-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="6a985-123">closeTimeout</span></span>|<span data-ttu-id="6a985-124">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="6a985-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6a985-125">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a985-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a985-126">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a985-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6a985-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="6a985-127">hostnameComparisonMode</span></span>|<span data-ttu-id="6a985-128">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="6a985-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="6a985-129">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda se k dosažení služby při shodě s identifikátorem URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="6a985-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="6a985-130">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="6a985-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="6a985-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6a985-131">maxBufferPoolSize</span></span>|<span data-ttu-id="6a985-132">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="6a985-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="6a985-133">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="6a985-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="6a985-134">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6a985-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="6a985-135">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="6a985-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="6a985-136">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="6a985-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="6a985-137">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="6a985-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="6a985-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6a985-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="6a985-139">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="6a985-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="6a985-140">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6a985-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="6a985-141">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="6a985-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6a985-142">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="6a985-142">The default is 65536.</span></span>|  
|<span data-ttu-id="6a985-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="6a985-143">messageEncoding</span></span>|<span data-ttu-id="6a985-144">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="6a985-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="6a985-145">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6a985-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6a985-146">-Text: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="6a985-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="6a985-147">-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).</span><span class="sxs-lookup"><span data-stu-id="6a985-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="6a985-148">– Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="6a985-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="6a985-149">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="6a985-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="6a985-150">name</span><span class="sxs-lookup"><span data-stu-id="6a985-150">name</span></span>|<span data-ttu-id="6a985-151">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="6a985-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6a985-152">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="6a985-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6a985-153">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="6a985-153">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6a985-154">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a985-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="6a985-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="6a985-155">openTimeout</span></span>|<span data-ttu-id="6a985-156">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="6a985-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6a985-157">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a985-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a985-158">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a985-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6a985-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="6a985-159">proxyAddress</span></span>|<span data-ttu-id="6a985-160">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="6a985-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="6a985-161">Pokud je `true``useSystemWebProxy`, musí být toto nastavení `null`.</span><span class="sxs-lookup"><span data-stu-id="6a985-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="6a985-162">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="6a985-162">The default is `null`.</span></span>|  
|<span data-ttu-id="6a985-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="6a985-163">receiveTimeout</span></span>|<span data-ttu-id="6a985-164">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="6a985-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6a985-165">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a985-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a985-166">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a985-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6a985-167">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="6a985-167">sendTimeout</span></span>|<span data-ttu-id="6a985-168">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="6a985-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6a985-169">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a985-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a985-170">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a985-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6a985-171">textEncoding</span><span class="sxs-lookup"><span data-stu-id="6a985-171">textEncoding</span></span>|<span data-ttu-id="6a985-172">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="6a985-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="6a985-173">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6a985-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6a985-174">-UnicodeFffeTextEncoding: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="6a985-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="6a985-175">-Utf16TextEncoding: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="6a985-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="6a985-176">-Utf8TextEncoding: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="6a985-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="6a985-177">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="6a985-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="6a985-178">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="6a985-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="6a985-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="6a985-179">transactionFlow</span></span>|<span data-ttu-id="6a985-180">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="6a985-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="6a985-181">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="6a985-181">The default is `false`.</span></span>|  
|<span data-ttu-id="6a985-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="6a985-182">useDefaultWebProxy</span></span>|<span data-ttu-id="6a985-183">Logická hodnota, která určuje, zda se používá automaticky konfigurovaný proxy server HTTP systému.</span><span class="sxs-lookup"><span data-stu-id="6a985-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="6a985-184">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="6a985-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a985-185">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6a985-185">Child Elements</span></span>  
  
|<span data-ttu-id="6a985-186">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a985-186">Element</span></span>|<span data-ttu-id="6a985-187">Popis</span><span class="sxs-lookup"><span data-stu-id="6a985-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a985-188">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="6a985-188">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="6a985-189">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="6a985-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="6a985-190">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="6a985-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="6a985-191">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a985-191">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="6a985-192">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="6a985-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6a985-193">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="6a985-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="6a985-194">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6a985-194">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="6a985-195">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="6a985-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a985-196">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6a985-196">Parent Elements</span></span>  
  
|<span data-ttu-id="6a985-197">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a985-197">Element</span></span>|<span data-ttu-id="6a985-198">Popis</span><span class="sxs-lookup"><span data-stu-id="6a985-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a985-199">vazby\<</span><span class="sxs-lookup"><span data-stu-id="6a985-199">\<bindings></span></span>](bindings.md)|<span data-ttu-id="6a985-200">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="6a985-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a985-201">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a985-201">Remarks</span></span>  
 <span data-ttu-id="6a985-202">`WSHttpBinding` je podobná `BasicHttpBinding`, ale poskytuje více funkcí webové služby.</span><span class="sxs-lookup"><span data-stu-id="6a985-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="6a985-203">Využívá přenos pomocí protokolu HTTP a poskytuje zabezpečení zpráv, jako BasicHttpBinding, ale také poskytuje transakce, spolehlivé zasílání zpráv a WS-Addressing, které jsou povoleny ve výchozím nastavení nebo k dispozici prostřednictvím jednoho nastavení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6a985-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a985-204">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a985-204">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
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
      </wsHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="6a985-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a985-205">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="6a985-206">Vazby</span><span class="sxs-lookup"><span data-stu-id="6a985-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6a985-207">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="6a985-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6a985-208">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6a985-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6a985-209">vazba \<</span><span class="sxs-lookup"><span data-stu-id="6a985-209">\<binding></span></span>](bindings.md)
