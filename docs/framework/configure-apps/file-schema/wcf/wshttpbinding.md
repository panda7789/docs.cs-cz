---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 33c1d8ed0240d737f2b5f56b889cc2f31d88d018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735618"
---
# <a name="wshttpbinding"></a><span data-ttu-id="bc9bf-101">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="bc9bf-101">\<wsHttpBinding></span></span>
<span data-ttu-id="bc9bf-102">Definuje bezpečnou, spolehlivou a interoperabilní vazbu, která je vhodná pro neduplexní kontrakty služeb.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="bc9bf-103">Vazba implementuje následující specifikace: WS-Reliable Messaging pro spolehlivost a WS-Security pro zabezpečení a ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="bc9bf-104">Přenos je HTTP a kódování zprávy je kódování text/XML.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
<span data-ttu-id="bc9bf-105">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bc9bf-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc9bf-106">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="bc9bf-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bc9bf-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bc9bf-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bc9bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="bc9bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc9bf-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc9bf-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc9bf-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bc9bf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bc9bf-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc9bf-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="bc9bf-112">Attributes</span></span>  
  
|<span data-ttu-id="bc9bf-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="bc9bf-113">Attribute</span></span>|<span data-ttu-id="bc9bf-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bc9bf-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc9bf-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="bc9bf-115">allowCookies</span></span>|<span data-ttu-id="bc9bf-116">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="bc9bf-117">Výchozí hodnota je false.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-117">The default is false.</span></span><br /><br /> <span data-ttu-id="bc9bf-118">Tuto vlastnost lze použít při práci s webovými službami ASMX, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="bc9bf-119">Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="bc9bf-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="bc9bf-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="bc9bf-121">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="bc9bf-122">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-122">The default is `false`.</span></span>|  
|<span data-ttu-id="bc9bf-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="bc9bf-123">closeTimeout</span></span>|<span data-ttu-id="bc9bf-124">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bc9bf-125">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc9bf-126">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="bc9bf-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="bc9bf-127">hostnameComparisonMode</span></span>|<span data-ttu-id="bc9bf-128">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="bc9bf-129">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda se k dosažení služby při shodě s identifikátorem URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="bc9bf-130">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="bc9bf-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="bc9bf-131">maxBufferPoolSize</span></span>|<span data-ttu-id="bc9bf-132">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="bc9bf-133">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="bc9bf-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="bc9bf-134">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="bc9bf-135">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="bc9bf-136">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="bc9bf-137">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="bc9bf-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="bc9bf-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="bc9bf-139">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="bc9bf-140">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="bc9bf-141">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="bc9bf-142">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-142">The default is 65536.</span></span>|  
|<span data-ttu-id="bc9bf-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="bc9bf-143">messageEncoding</span></span>|<span data-ttu-id="bc9bf-144">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="bc9bf-145">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="bc9bf-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bc9bf-146">-Text: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="bc9bf-147">-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).</span><span class="sxs-lookup"><span data-stu-id="bc9bf-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="bc9bf-148">– Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="bc9bf-149">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="bc9bf-150">name</span><span class="sxs-lookup"><span data-stu-id="bc9bf-150">name</span></span>|<span data-ttu-id="bc9bf-151">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bc9bf-152">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bc9bf-153">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bc9bf-154">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bc9bf-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="bc9bf-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="bc9bf-155">openTimeout</span></span>|<span data-ttu-id="bc9bf-156">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bc9bf-157">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc9bf-158">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="bc9bf-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="bc9bf-159">proxyAddress</span></span>|<span data-ttu-id="bc9bf-160">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="bc9bf-161">Pokud je `true``useSystemWebProxy`, musí být toto nastavení `null`.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="bc9bf-162">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-162">The default is `null`.</span></span>|  
|<span data-ttu-id="bc9bf-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="bc9bf-163">receiveTimeout</span></span>|<span data-ttu-id="bc9bf-164">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bc9bf-165">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc9bf-166">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="bc9bf-167">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="bc9bf-167">sendTimeout</span></span>|<span data-ttu-id="bc9bf-168">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bc9bf-169">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc9bf-170">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="bc9bf-171">textEncoding</span><span class="sxs-lookup"><span data-stu-id="bc9bf-171">textEncoding</span></span>|<span data-ttu-id="bc9bf-172">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="bc9bf-173">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="bc9bf-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bc9bf-174">-UnicodeFffeTextEncoding: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="bc9bf-175">-Utf16TextEncoding: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="bc9bf-176">-Utf8TextEncoding: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="bc9bf-177">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="bc9bf-178">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="bc9bf-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="bc9bf-179">transactionFlow</span></span>|<span data-ttu-id="bc9bf-180">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="bc9bf-181">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-181">The default is `false`.</span></span>|  
|<span data-ttu-id="bc9bf-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="bc9bf-182">useDefaultWebProxy</span></span>|<span data-ttu-id="bc9bf-183">Logická hodnota, která určuje, zda se používá automaticky konfigurovaný proxy server HTTP systému.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="bc9bf-184">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc9bf-185">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bc9bf-185">Child Elements</span></span>  
  
|<span data-ttu-id="bc9bf-186">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc9bf-186">Element</span></span>|<span data-ttu-id="bc9bf-187">Popis</span><span class="sxs-lookup"><span data-stu-id="bc9bf-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc9bf-188">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="bc9bf-188">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="bc9bf-189">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="bc9bf-190">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="bc9bf-191">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bc9bf-191">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="bc9bf-192">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="bc9bf-193">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="bc9bf-194">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bc9bf-194">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="bc9bf-195">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc9bf-196">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bc9bf-196">Parent Elements</span></span>  
  
|<span data-ttu-id="bc9bf-197">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc9bf-197">Element</span></span>|<span data-ttu-id="bc9bf-198">Popis</span><span class="sxs-lookup"><span data-stu-id="bc9bf-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc9bf-199">vazby\<</span><span class="sxs-lookup"><span data-stu-id="bc9bf-199">\<bindings></span></span>](bindings.md)|<span data-ttu-id="bc9bf-200">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc9bf-201">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc9bf-201">Remarks</span></span>  
 <span data-ttu-id="bc9bf-202">`WSHttpBinding` je podobná `BasicHttpBinding`, ale poskytuje více funkcí webové služby.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="bc9bf-203">Využívá přenos pomocí protokolu HTTP a poskytuje zabezpečení zpráv, jako BasicHttpBinding, ale také poskytuje transakce, spolehlivé zasílání zpráv a WS-Addressing, které jsou povoleny ve výchozím nastavení nebo k dispozici prostřednictvím jednoho nastavení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bc9bf-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc9bf-204">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc9bf-204">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc9bf-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc9bf-205">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="bc9bf-206">Vazby</span><span class="sxs-lookup"><span data-stu-id="bc9bf-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bc9bf-207">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="bc9bf-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bc9bf-208">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bc9bf-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bc9bf-209">vazba \<</span><span class="sxs-lookup"><span data-stu-id="bc9bf-209">\<binding></span></span>](bindings.md)
