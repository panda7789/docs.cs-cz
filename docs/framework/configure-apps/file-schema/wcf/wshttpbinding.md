---
title: <wsHttpBinding>
description: Definuje zabezpečenou, spolehlivou a interoperabilní vazbu HTTP vhodnou pro neduplexní kontrakty služeb, které implementují zasílání zpráv WS-Reliable a WS-Security.
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: d603f699145622cb1b70ecf99ea542572e841eac
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243981"
---
# \<wsHttpBinding>
<span data-ttu-id="e2ad3-102">Definuje bezpečnou, spolehlivou a interoperabilní vazbu, která je vhodná pro neduplexní kontrakty služeb.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="e2ad3-103">Vazba implementuje následující specifikace: WS-Reliable Messaging pro spolehlivost a WS-Security pro zabezpečení a ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="e2ad3-104">Přenos je HTTP a kódování zprávy je kódování text/XML.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="e2ad3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2ad3-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2ad3-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e2ad3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e2ad3-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2ad3-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="e2ad3-108">Attributes</span></span>  
  
|<span data-ttu-id="e2ad3-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="e2ad3-109">Attribute</span></span>|<span data-ttu-id="e2ad3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e2ad3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2ad3-111">allowCookies</span><span class="sxs-lookup"><span data-stu-id="e2ad3-111">allowCookies</span></span>|<span data-ttu-id="e2ad3-112">Logická hodnota určující, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-112">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="e2ad3-113">Výchozí hodnotou je hodnota false.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-113">The default is false.</span></span><br /><br /> <span data-ttu-id="e2ad3-114">Tuto vlastnost lze použít při práci s webovými službami ASMX, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-114">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="e2ad3-115">Tímto způsobem si můžete ověřit, že soubory cookie vrácené ze serveru se automaticky zkopírují do všech budoucích požadavků klientů pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-115">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="e2ad3-116">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="e2ad3-116">bypassProxyOnLocal</span></span>|<span data-ttu-id="e2ad3-117">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="e2ad3-118">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-118">The default is `false`.</span></span>|  
|<span data-ttu-id="e2ad3-119">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="e2ad3-119">closeTimeout</span></span>|<span data-ttu-id="e2ad3-120"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e2ad3-121">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="e2ad3-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e2ad3-122">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-122">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e2ad3-123">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="e2ad3-123">hostnameComparisonMode</span></span>|<span data-ttu-id="e2ad3-124">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-124">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="e2ad3-125">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode> , který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-125">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="e2ad3-126">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-126">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="e2ad3-127">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="e2ad3-127">maxBufferPoolSize</span></span>|<span data-ttu-id="e2ad3-128">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-128">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="e2ad3-129">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="e2ad3-129">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="e2ad3-130">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-130">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="e2ad3-131">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-131">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="e2ad3-132">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-132">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="e2ad3-133">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-133">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="e2ad3-134">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="e2ad3-134">maxReceivedMessageSize</span></span>|<span data-ttu-id="e2ad3-135">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-135">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="e2ad3-136">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="e2ad3-137">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e2ad3-138">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-138">The default is 65536.</span></span>|  
|<span data-ttu-id="e2ad3-139">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="e2ad3-139">messageEncoding</span></span>|<span data-ttu-id="e2ad3-140">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-140">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="e2ad3-141">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e2ad3-141">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e2ad3-142">-Text: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-142">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="e2ad3-143">-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).</span><span class="sxs-lookup"><span data-stu-id="e2ad3-143">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="e2ad3-144">– Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-144">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="e2ad3-145">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="e2ad3-145">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="e2ad3-146">name</span><span class="sxs-lookup"><span data-stu-id="e2ad3-146">name</span></span>|<span data-ttu-id="e2ad3-147">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e2ad3-148">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e2ad3-149">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-149">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e2ad3-150">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e2ad3-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="e2ad3-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="e2ad3-151">openTimeout</span></span>|<span data-ttu-id="e2ad3-152"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e2ad3-153">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="e2ad3-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e2ad3-154">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e2ad3-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="e2ad3-155">proxyAddress</span></span>|<span data-ttu-id="e2ad3-156">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="e2ad3-157">Pokud `useSystemWebProxy` má `true` parametr hodnotu, musí být toto nastavení `null` .</span><span class="sxs-lookup"><span data-stu-id="e2ad3-157">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="e2ad3-158">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-158">The default is `null`.</span></span>|  
|<span data-ttu-id="e2ad3-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="e2ad3-159">receiveTimeout</span></span>|<span data-ttu-id="e2ad3-160"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e2ad3-161">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="e2ad3-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e2ad3-162">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e2ad3-163">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="e2ad3-163">sendTimeout</span></span>|<span data-ttu-id="e2ad3-164"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e2ad3-165">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="e2ad3-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e2ad3-166">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e2ad3-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="e2ad3-167">textEncoding</span></span>|<span data-ttu-id="e2ad3-168">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-168">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="e2ad3-169">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e2ad3-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e2ad3-170">-UnicodeFffeTextEncoding: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-170">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="e2ad3-171">-Utf16TextEncoding: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-171">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="e2ad3-172">-Utf8TextEncoding: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-172">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="e2ad3-173">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-173">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="e2ad3-174">Tento atribut je typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="e2ad3-174">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="e2ad3-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="e2ad3-175">transactionFlow</span></span>|<span data-ttu-id="e2ad3-176">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="e2ad3-177">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-177">The default is `false`.</span></span>|  
|<span data-ttu-id="e2ad3-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="e2ad3-178">useDefaultWebProxy</span></span>|<span data-ttu-id="e2ad3-179">Logická hodnota, která určuje, zda se používá automaticky konfigurovaný proxy server HTTP systému.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-179">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="e2ad3-180">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-180">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2ad3-181">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e2ad3-181">Child Elements</span></span>  
  
|<span data-ttu-id="e2ad3-182">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2ad3-182">Element</span></span>|<span data-ttu-id="e2ad3-183">Description</span><span class="sxs-lookup"><span data-stu-id="e2ad3-183">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="e2ad3-184">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-184">Defines the security settings for the binding.</span></span> <span data-ttu-id="e2ad3-185">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="e2ad3-185">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="e2ad3-186">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-186">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e2ad3-187">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="e2ad3-187">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="e2ad3-188">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-188">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2ad3-189">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e2ad3-189">Parent Elements</span></span>  
  
|<span data-ttu-id="e2ad3-190">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2ad3-190">Element</span></span>|<span data-ttu-id="e2ad3-191">Description</span><span class="sxs-lookup"><span data-stu-id="e2ad3-191">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="e2ad3-192">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-192">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2ad3-193">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2ad3-193">Remarks</span></span>  
 <span data-ttu-id="e2ad3-194">`WSHttpBinding`Je podobná, `BasicHttpBinding` ale poskytuje více funkcí webové služby.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-194">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="e2ad3-195">Využívá přenos pomocí protokolu HTTP a poskytuje zabezpečení zpráv, jako BasicHttpBinding, ale také poskytuje transakce, spolehlivé zasílání zpráv a WS-Addressing, které jsou povoleny ve výchozím nastavení nebo k dispozici prostřednictvím jednoho nastavení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e2ad3-195">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2ad3-196">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2ad3-196">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e2ad3-197">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2ad3-197">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="e2ad3-198">Vazby</span><span class="sxs-lookup"><span data-stu-id="e2ad3-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e2ad3-199">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="e2ad3-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e2ad3-200">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e2ad3-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
