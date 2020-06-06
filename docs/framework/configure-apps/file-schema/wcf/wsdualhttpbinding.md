---
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 01360ae8288b3cb7374597ad77935f634eb0a519
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139282"
---
# \<wsDualHttpBinding>
<span data-ttu-id="7b8c9-101">Definuje bezpečnou, spolehlivou a interoperabilní vazbu, která je vhodná pro duplexní kontrakty služeb nebo komunikace prostřednictvím zprostředkovatelů SOAP.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-101">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsDualHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="7b8c9-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b8c9-102">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
          closeTimeout="TimeSpan"
          openTimeout="TimeSpan"
          receiveTimeout="TimeSpan"
          sendTimeout="TimeSpan"
          bypassProxyOnLocal="Boolean"
          clientBaseAddress="URI"
          transactionFlow="Boolean"
          hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
          maxBufferPoolSize="integer"
          maxReceivedMessageSize="Integer"
          messageEncoding="Text/Mtom"
          proxyAddress="URI"
          textEncoding="Unicode/BigEndianUnicode/UTF8"
          useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan" />
    <security mode="None/Message">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b8c9-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7b8c9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7b8c9-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b8c9-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b8c9-105">Attributes</span></span>  
  
|<span data-ttu-id="7b8c9-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b8c9-106">Attribute</span></span>|<span data-ttu-id="7b8c9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7b8c9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b8c9-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="7b8c9-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="7b8c9-109">Logická hodnota, která označuje, zda se má pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="7b8c9-110">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-110">The default is `false`.</span></span>|  
|<span data-ttu-id="7b8c9-111">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="7b8c9-111">clientBaseAddress</span></span>|<span data-ttu-id="7b8c9-112">Identifikátor URI, který nastaví základní adresu, na kterou klient naslouchá, aby zprávy odpovědí od služby.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-112">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="7b8c9-113">Je-li tento parametr zadán, použije se k naslouchání Tato adresa (plus pro channelGUID).</span><span class="sxs-lookup"><span data-stu-id="7b8c9-113">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="7b8c9-114">Pokud hodnota není zadána, bude základní adresa klienta generována způsobem, který je specifický pro přenos.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-114">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="7b8c9-115">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-115">The default is `null`.</span></span>|  
|<span data-ttu-id="7b8c9-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="7b8c9-116">closeTimeout</span></span>|<span data-ttu-id="7b8c9-117"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7b8c9-118">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b8c9-119">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7b8c9-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="7b8c9-120">hostnameComparisonMode</span></span>|<span data-ttu-id="7b8c9-121">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="7b8c9-122">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode> , který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="7b8c9-123">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="7b8c9-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="7b8c9-124">maxBufferPoolSize</span></span>|<span data-ttu-id="7b8c9-125">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="7b8c9-126">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="7b8c9-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="7b8c9-127">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="7b8c9-128">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="7b8c9-129">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="7b8c9-130">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="7b8c9-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="7b8c9-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="7b8c9-132">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7b8c9-133">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="7b8c9-134">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7b8c9-135">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-135">The default is 65536.</span></span>|  
|<span data-ttu-id="7b8c9-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="7b8c9-136">messageEncoding</span></span>|<span data-ttu-id="7b8c9-137">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="7b8c9-138">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7b8c9-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7b8c9-139">-Text: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="7b8c9-140">-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).</span><span class="sxs-lookup"><span data-stu-id="7b8c9-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="7b8c9-141">– Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-141">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="7b8c9-142">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="7b8c9-143">name</span><span class="sxs-lookup"><span data-stu-id="7b8c9-143">name</span></span>|<span data-ttu-id="7b8c9-144">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7b8c9-145">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7b8c9-146">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-146">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7b8c9-147">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7b8c9-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="7b8c9-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="7b8c9-148">openTimeout</span></span>|<span data-ttu-id="7b8c9-149"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7b8c9-150">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b8c9-151">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7b8c9-152">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="7b8c9-152">proxyAddress</span></span>|<span data-ttu-id="7b8c9-153">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-153">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="7b8c9-154">Pokud `useDefaultWebProxy` má `true` parametr hodnotu, musí být toto nastavení `null` .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-154">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="7b8c9-155">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-155">The default is `null`.</span></span>|  
|<span data-ttu-id="7b8c9-156">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="7b8c9-156">receiveTimeout</span></span>|<span data-ttu-id="7b8c9-157"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7b8c9-158">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b8c9-159">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-159">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7b8c9-160">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="7b8c9-160">sendTimeout</span></span>|<span data-ttu-id="7b8c9-161"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7b8c9-162">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b8c9-163">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-163">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7b8c9-164">textEncoding</span><span class="sxs-lookup"><span data-stu-id="7b8c9-164">textEncoding</span></span>|<span data-ttu-id="7b8c9-165">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7b8c9-166">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7b8c9-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7b8c9-167">-BigEndianUnicode: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="7b8c9-168">-Unicode: 16 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="7b8c9-169">-UTF8:8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="7b8c9-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="7b8c9-170">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-170">The default is UTF8.</span></span> <span data-ttu-id="7b8c9-171">Tento atribut je typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-171">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="7b8c9-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="7b8c9-172">transactionFlow</span></span>|<span data-ttu-id="7b8c9-173">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="7b8c9-174">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-174">The default is `false`.</span></span>|  
|<span data-ttu-id="7b8c9-175">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="7b8c9-175">useDefaultWebProxy</span></span>|<span data-ttu-id="7b8c9-176">Logická hodnota, která označuje, zda je použit automaticky konfigurovaný proxy server HTTP.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-176">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="7b8c9-177">Adresa proxy serveru musí být `null` (tj. není nastavena), pokud je tento atribut `true` .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-177">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="7b8c9-178">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-178">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b8c9-179">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7b8c9-179">Child Elements</span></span>  
  
|<span data-ttu-id="7b8c9-180">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b8c9-180">Element</span></span>|<span data-ttu-id="7b8c9-181">Description</span><span class="sxs-lookup"><span data-stu-id="7b8c9-181">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|<span data-ttu-id="7b8c9-182">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-182">Defines the security settings for the binding.</span></span> <span data-ttu-id="7b8c9-183">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-183">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="7b8c9-184">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7b8c9-185">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="7b8c9-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="7b8c9-186">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-186">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b8c9-187">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b8c9-187">Parent Elements</span></span>  
  
|<span data-ttu-id="7b8c9-188">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b8c9-188">Element</span></span>|<span data-ttu-id="7b8c9-189">Description</span><span class="sxs-lookup"><span data-stu-id="7b8c9-189">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="7b8c9-190">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b8c9-191">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b8c9-191">Remarks</span></span>  
 <span data-ttu-id="7b8c9-192">`WSDualHttpBinding`Poskytuje stejnou podporu protokolů webové služby jako `WSHttpBinding` , ale pro použití s meziduplexní kontrakty.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-192">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="7b8c9-193">`WSDualHttpBinding`podporuje pouze zabezpečení SOAP a vyžaduje spolehlivé zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-193">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="7b8c9-194">Tato vazba vyžaduje, aby měl klient veřejný identifikátor URI, který pro službu poskytuje koncový bod zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-194">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="7b8c9-195">Tato vlastnost je k dispozici v `clientBaseAddress` atributu.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-195">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="7b8c9-196">Duální vazba zpřístupňuje IP adresu klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-196">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="7b8c9-197">Klient by měl použít zabezpečení, aby zajistil, že se připojí pouze ke službám, kterým důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-197">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="7b8c9-198">Tato vazba se dá použít ke spolehlivé komunikaci prostřednictvím jednoho nebo více zprostředkovatelů SOAP.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-198">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="7b8c9-199">Ve výchozím nastavení tato vazba generuje zásobník modulu runtime s WS-ReliableMessaging pro spolehlivost, WS-Security pro zabezpečení a ověřování zpráv, HTTP pro doručování zpráv a kódování textu/XML.</span><span class="sxs-lookup"><span data-stu-id="7b8c9-199">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b8c9-200">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b8c9-200">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 clientBaseAddress="http://localhost:8001/client/"
                 transactionFlow="true"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00" />
          <security mode="None">
            <message clientCredentialType="None"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128" />
          </security>
        </binding>
      </wsDualHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="7b8c9-201">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b8c9-201">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [<span data-ttu-id="7b8c9-202">Vazby</span><span class="sxs-lookup"><span data-stu-id="7b8c9-202">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7b8c9-203">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="7b8c9-203">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7b8c9-204">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7b8c9-204">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
