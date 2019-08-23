---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: fe952dfe9ce51e23d1ba46975026799dfe8b5b39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915262"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="79b2c-101">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="79b2c-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="79b2c-102">Zabezpečená a interoperabilní vazba, která je odvozena z [ \<WSFederationHttpBinding >](wsfederationhttpbinding.md) a podporuje federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="79b2c-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <ws2007FederationHttpBinding>
```

## <a name="syntax"></a><span data-ttu-id="79b2c-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79b2c-103">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79b2c-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="79b2c-104">Attributes and Elements</span></span>

<span data-ttu-id="79b2c-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="79b2c-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="79b2c-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="79b2c-106">Attributes</span></span>

|<span data-ttu-id="79b2c-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="79b2c-107">Attribute</span></span>|<span data-ttu-id="79b2c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="79b2c-108">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="79b2c-109">Hodnota, která označuje, zda se má obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="79b2c-109">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="79b2c-110">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="79b2c-110">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="79b2c-111"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="79b2c-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="79b2c-112">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="79b2c-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="79b2c-113">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="79b2c-113">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="79b2c-114">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="79b2c-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="79b2c-115">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="79b2c-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="79b2c-116">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="79b2c-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="79b2c-117">Maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="79b2c-117">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="79b2c-118">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="79b2c-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="79b2c-119">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="79b2c-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="79b2c-120">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="79b2c-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="79b2c-121">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="79b2c-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="79b2c-122">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="79b2c-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="79b2c-123">Maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="79b2c-123">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="79b2c-124">Odesílatel zprávy, která překračuje toto omezení, obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="79b2c-124">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="79b2c-125">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="79b2c-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="79b2c-126">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="79b2c-126">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="79b2c-127">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="79b2c-127">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="79b2c-128">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="79b2c-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="79b2c-129">Textové Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="79b2c-129">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="79b2c-130">Maximální Použijte kodér 1,0 (pro organizaci přenosu zpráv).</span><span class="sxs-lookup"><span data-stu-id="79b2c-130">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="79b2c-131">Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="79b2c-131">The default is Text.</span></span><br /><br /> <span data-ttu-id="79b2c-132">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="79b2c-132">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="79b2c-133">Název konfigurace vazby</span><span class="sxs-lookup"><span data-stu-id="79b2c-133">The configuration name of the binding.</span></span> <span data-ttu-id="79b2c-134">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="79b2c-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="79b2c-135">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="79b2c-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="79b2c-136">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="79b2c-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="79b2c-137"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="79b2c-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="79b2c-138">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="79b2c-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="79b2c-139">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="79b2c-139">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="79b2c-140">Identifikátor URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="79b2c-140">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="79b2c-141">Verze aktuálního oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="79b2c-141">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="79b2c-142">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b2c-142">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="79b2c-143">Pokud `useDefaultWebProxy` má `true`parametr hodnotu, musí být `null`toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="79b2c-143">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="79b2c-144">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="79b2c-144">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="79b2c-145"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="79b2c-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="79b2c-146">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="79b2c-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="79b2c-147">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="79b2c-147">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="79b2c-148"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="79b2c-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="79b2c-149">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="79b2c-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="79b2c-150">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="79b2c-150">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="79b2c-151">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="79b2c-151">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="79b2c-152">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="79b2c-152">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="79b2c-153">- BigEndianUnicode: Kódování Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="79b2c-153">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="79b2c-154">Sady 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="79b2c-154">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="79b2c-155">-   UTF8: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="79b2c-155">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="79b2c-156">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="79b2c-156">The default is UTF8.</span></span> <span data-ttu-id="79b2c-157">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="79b2c-157">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="79b2c-158">Hodnota, která určuje, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="79b2c-158">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="79b2c-159">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="79b2c-159">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="79b2c-160">Hodnota, která označuje, zda je použit automaticky konfigurovaný proxy server HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b2c-160">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="79b2c-161">Adresa proxy serveru musí být `null` (tj. není nastavena), pokud je `true`tento atribut.</span><span class="sxs-lookup"><span data-stu-id="79b2c-161">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="79b2c-162">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="79b2c-162">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="79b2c-163">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="79b2c-163">Child Elements</span></span>

|<span data-ttu-id="79b2c-164">Prvek</span><span class="sxs-lookup"><span data-stu-id="79b2c-164">Element</span></span>|<span data-ttu-id="79b2c-165">Popis</span><span class="sxs-lookup"><span data-stu-id="79b2c-165">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79b2c-166">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="79b2c-166">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="79b2c-167">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="79b2c-167">Defines the security settings for the message.</span></span> <span data-ttu-id="79b2c-168">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="79b2c-168">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="79b2c-169">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="79b2c-169">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="79b2c-170">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="79b2c-170">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="79b2c-171">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="79b2c-171">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="79b2c-172">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="79b2c-172">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="79b2c-173">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="79b2c-173">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="79b2c-174">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="79b2c-174">Parent Elements</span></span>

|<span data-ttu-id="79b2c-175">Prvek</span><span class="sxs-lookup"><span data-stu-id="79b2c-175">Element</span></span>|<span data-ttu-id="79b2c-176">Popis</span><span class="sxs-lookup"><span data-stu-id="79b2c-176">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79b2c-177">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="79b2c-177">\<bindings></span></span>](bindings.md)|<span data-ttu-id="79b2c-178">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="79b2c-178">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="79b2c-179">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79b2c-179">Remarks</span></span>

<span data-ttu-id="79b2c-180">Federace je schopnost sdílet identity napříč několika společnostmi nebo důvěřovat doménám pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="79b2c-180">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="79b2c-181">Používá protokol WS-Trust k mapování reprezentace identity z jedné domény důvěryhodnosti na jinou.</span><span class="sxs-lookup"><span data-stu-id="79b2c-181">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="79b2c-182">Federační vazba protokolu HTTP podporuje zabezpečení SOAP i zabezpečení ve smíšeném režimu, ale nepodporuje zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="79b2c-182">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="79b2c-183">Služby nakonfigurované s touto vazbou musí používat přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b2c-183">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="79b2c-184">Další informace najdete v tématu [ \<WSFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="79b2c-184">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="79b2c-185">Příklad</span><span class="sxs-lookup"><span data-stu-id="79b2c-185">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="79b2c-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79b2c-186">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="79b2c-187">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="79b2c-187">\<wsFederationHttpBinding></span></span>](wsfederationhttpbinding.md)
- [<span data-ttu-id="79b2c-188">Vazby</span><span class="sxs-lookup"><span data-stu-id="79b2c-188">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="79b2c-189">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="79b2c-189">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="79b2c-190">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="79b2c-190">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="79b2c-191">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="79b2c-191">\<binding></span></span>](../../../misc/binding.md)
