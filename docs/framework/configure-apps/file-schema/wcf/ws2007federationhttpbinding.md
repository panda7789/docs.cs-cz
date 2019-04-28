---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: e6215465acbf9bb94298d282d15f8735a0e20c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673079"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="08a34-101">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="08a34-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="08a34-102">Zabezpečená a interoperabilní vazbu, která je odvozena z [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a podporuje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="08a34-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <ws2007FederationHttpBinding>
```

## <a name="syntax"></a><span data-ttu-id="08a34-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08a34-103">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="08a34-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="08a34-104">Attributes and Elements</span></span>

<span data-ttu-id="08a34-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="08a34-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="08a34-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="08a34-106">Attributes</span></span>

|<span data-ttu-id="08a34-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="08a34-107">Attribute</span></span>|<span data-ttu-id="08a34-108">Popis</span><span class="sxs-lookup"><span data-stu-id="08a34-108">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="08a34-109">Hodnota, která označuje, zda obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="08a34-109">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="08a34-110">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="08a34-110">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="08a34-111">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="08a34-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="08a34-112">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="08a34-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08a34-113">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="08a34-113">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="08a34-114">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="08a34-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="08a34-115">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="08a34-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="08a34-116">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="08a34-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="08a34-117">Velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="08a34-117">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="08a34-118">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="08a34-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="08a34-119">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="08a34-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="08a34-120">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="08a34-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="08a34-121">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="08a34-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="08a34-122">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="08a34-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="08a34-123">Maximální velikost v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="08a34-123">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="08a34-124">Odesílatel zprávy, která překračuje tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="08a34-124">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="08a34-125">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="08a34-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="08a34-126">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="08a34-126">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="08a34-127">Definuje kodér pro kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="08a34-127">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="08a34-128">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="08a34-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="08a34-129">-Text: Použijte kodér textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="08a34-129">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="08a34-130">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="08a34-130">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="08a34-131">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="08a34-131">The default is Text.</span></span><br /><br /> <span data-ttu-id="08a34-132">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="08a34-132">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="08a34-133">Název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="08a34-133">The configuration name of the binding.</span></span> <span data-ttu-id="08a34-134">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="08a34-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="08a34-135">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="08a34-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="08a34-136">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="08a34-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="08a34-137">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="08a34-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="08a34-138">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="08a34-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08a34-139">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="08a34-139">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="08a34-140">Identifikátor URI, ve kterém je umístěno oznámení soukromí.</span><span class="sxs-lookup"><span data-stu-id="08a34-140">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="08a34-141">Verze aktuálního oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="08a34-141">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="08a34-142">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="08a34-142">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="08a34-143">Pokud `useDefaultWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="08a34-143">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="08a34-144">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="08a34-144">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="08a34-145">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="08a34-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="08a34-146">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="08a34-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08a34-147">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="08a34-147">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="08a34-148">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="08a34-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="08a34-149">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="08a34-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08a34-150">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="08a34-150">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="08a34-151">Nastaví znakovou sadu kódování, které má být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="08a34-151">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="08a34-152">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="08a34-152">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="08a34-153">-BigEndianUnicode: Big Endian kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="08a34-153">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="08a34-154">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="08a34-154">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="08a34-155">-   UTF8: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="08a34-155">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="08a34-156">Použije se UTF8.</span><span class="sxs-lookup"><span data-stu-id="08a34-156">The default is UTF8.</span></span> <span data-ttu-id="08a34-157">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="08a34-157">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="08a34-158">Hodnota, která určuje, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="08a34-158">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="08a34-159">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="08a34-159">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="08a34-160">Hodnota, která označuje, zda se používá v systému automaticky nakonfigurovaný proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="08a34-160">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="08a34-161">Adresa proxy musí být `null` (to znamená, není nastavený) Pokud tento atribut je `true`.</span><span class="sxs-lookup"><span data-stu-id="08a34-161">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="08a34-162">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="08a34-162">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="08a34-163">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="08a34-163">Child Elements</span></span>

|<span data-ttu-id="08a34-164">Prvek</span><span class="sxs-lookup"><span data-stu-id="08a34-164">Element</span></span>|<span data-ttu-id="08a34-165">Popis</span><span class="sxs-lookup"><span data-stu-id="08a34-165">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08a34-166">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="08a34-166">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="08a34-167">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="08a34-167">Defines the security settings for the message.</span></span> <span data-ttu-id="08a34-168">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="08a34-168">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="08a34-169">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="08a34-169">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="08a34-170">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="08a34-170">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="08a34-171">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="08a34-171">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="08a34-172">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="08a34-172">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="08a34-173">Určuje, zda jsou vytvořeny spolehlivé relace mezi koncovými body kanálu.</span><span class="sxs-lookup"><span data-stu-id="08a34-173">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="08a34-174">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="08a34-174">Parent Elements</span></span>

|<span data-ttu-id="08a34-175">Prvek</span><span class="sxs-lookup"><span data-stu-id="08a34-175">Element</span></span>|<span data-ttu-id="08a34-176">Popis</span><span class="sxs-lookup"><span data-stu-id="08a34-176">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08a34-177">\<bindings></span><span class="sxs-lookup"><span data-stu-id="08a34-177">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="08a34-178">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="08a34-178">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="08a34-179">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08a34-179">Remarks</span></span>

<span data-ttu-id="08a34-180">Federace se nachází taky možnost podělit identit napříč více podniky nebo vztah důvěryhodnosti domény pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="08a34-180">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="08a34-181">Protokol WS-Trust používá k mapování reprezentace identit z jednoho vztahu důvěryhodnosti domény na jiný.</span><span class="sxs-lookup"><span data-stu-id="08a34-181">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="08a34-182">Federované vazby HTTP podporuje zabezpečení protokolu SOAP, stejně jako ve smíšeném režimu zabezpečení, ale zabezpečení přenosu není podporováno.</span><span class="sxs-lookup"><span data-stu-id="08a34-182">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="08a34-183">Nakonfigurované s touto vazbou služby musíte použít přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="08a34-183">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="08a34-184">Další informace najdete v tématu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="08a34-184">For more information, see [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="08a34-185">Příklad</span><span class="sxs-lookup"><span data-stu-id="08a34-185">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="08a34-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08a34-186">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="08a34-187">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="08a34-187">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)
- [<span data-ttu-id="08a34-188">Vazby</span><span class="sxs-lookup"><span data-stu-id="08a34-188">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="08a34-189">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="08a34-189">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="08a34-190">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="08a34-190">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="08a34-191">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="08a34-191">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
