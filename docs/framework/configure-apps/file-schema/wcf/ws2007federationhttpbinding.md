---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 20ba643fddbac8a488e5457f0195cc253d4d23f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139312"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="efd64-101">Zabezpečená a interoperabilní vazba, která je odvozena z [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) a podporuje federované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="efd64-101">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="efd64-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efd64-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="efd64-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="efd64-103">Attributes and Elements</span></span>

<span data-ttu-id="efd64-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="efd64-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="efd64-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="efd64-105">Attributes</span></span>

|<span data-ttu-id="efd64-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="efd64-106">Attribute</span></span>|<span data-ttu-id="efd64-107">Popis</span><span class="sxs-lookup"><span data-stu-id="efd64-107">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="efd64-108">Hodnota, která označuje, zda se má obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="efd64-108">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="efd64-109">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="efd64-109">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="efd64-110"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="efd64-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="efd64-111">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="efd64-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="efd64-112">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="efd64-112">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="efd64-113">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="efd64-113">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="efd64-114">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode> , který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="efd64-114">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="efd64-115">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="efd64-115">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="efd64-116">Maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="efd64-116">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="efd64-117">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="efd64-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="efd64-118">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="efd64-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="efd64-119">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="efd64-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="efd64-120">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="efd64-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="efd64-121">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="efd64-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="efd64-122">Maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="efd64-122">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="efd64-123">Odesílatel zprávy, která překračuje toto omezení, obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="efd64-123">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="efd64-124">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="efd64-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="efd64-125">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="efd64-125">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="efd64-126">Definuje kodér použitý ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="efd64-126">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="efd64-127">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="efd64-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="efd64-128">-Text: Použijte kodér textové zprávy.</span><span class="sxs-lookup"><span data-stu-id="efd64-128">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="efd64-129">-MTOM: Použijte kodér 1,0 (Message Transmission Organization mechanism).</span><span class="sxs-lookup"><span data-stu-id="efd64-129">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="efd64-130">Výchozí hodnota je text.</span><span class="sxs-lookup"><span data-stu-id="efd64-130">The default is Text.</span></span><br /><br /> <span data-ttu-id="efd64-131">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="efd64-131">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="efd64-132">Název konfigurace vazby</span><span class="sxs-lookup"><span data-stu-id="efd64-132">The configuration name of the binding.</span></span> <span data-ttu-id="efd64-133">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="efd64-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="efd64-134">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="efd64-134">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="efd64-135">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="efd64-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="efd64-136"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="efd64-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="efd64-137">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="efd64-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="efd64-138">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="efd64-138">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="efd64-139">Identifikátor URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="efd64-139">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="efd64-140">Verze aktuálního oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="efd64-140">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="efd64-141">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="efd64-141">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="efd64-142">Pokud `useDefaultWebProxy` má `true` parametr hodnotu, musí být toto nastavení `null` .</span><span class="sxs-lookup"><span data-stu-id="efd64-142">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="efd64-143">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="efd64-143">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="efd64-144"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="efd64-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="efd64-145">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="efd64-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="efd64-146">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="efd64-146">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="efd64-147"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="efd64-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="efd64-148">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="efd64-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="efd64-149">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="efd64-149">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="efd64-150">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="efd64-150">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="efd64-151">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="efd64-151">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="efd64-152">-BigEndianUnicode: kódování Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="efd64-152">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="efd64-153">-Unicode: 16 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="efd64-153">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="efd64-154">-UTF8:8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="efd64-154">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="efd64-155">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="efd64-155">The default is UTF8.</span></span> <span data-ttu-id="efd64-156">Tento atribut je typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="efd64-156">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="efd64-157">Hodnota, která určuje, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="efd64-157">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="efd64-158">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="efd64-158">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="efd64-159">Hodnota, která označuje, zda je použit automaticky konfigurovaný proxy server HTTP.</span><span class="sxs-lookup"><span data-stu-id="efd64-159">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="efd64-160">Adresa proxy serveru musí být `null` (tj. není nastavena), pokud je tento atribut `true` .</span><span class="sxs-lookup"><span data-stu-id="efd64-160">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="efd64-161">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="efd64-161">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="efd64-162">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="efd64-162">Child Elements</span></span>

|<span data-ttu-id="efd64-163">Prvek</span><span class="sxs-lookup"><span data-stu-id="efd64-163">Element</span></span>|<span data-ttu-id="efd64-164">Description</span><span class="sxs-lookup"><span data-stu-id="efd64-164">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="efd64-165">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="efd64-165">Defines the security settings for the message.</span></span> <span data-ttu-id="efd64-166">Tento prvek je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="efd64-166">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="efd64-167">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="efd64-167">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="efd64-168">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="efd64-168">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="efd64-169">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="efd64-169">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="efd64-170">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="efd64-170">Parent Elements</span></span>

|<span data-ttu-id="efd64-171">Prvek</span><span class="sxs-lookup"><span data-stu-id="efd64-171">Element</span></span>|<span data-ttu-id="efd64-172">Description</span><span class="sxs-lookup"><span data-stu-id="efd64-172">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="efd64-173">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="efd64-173">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="efd64-174">Poznámky</span><span class="sxs-lookup"><span data-stu-id="efd64-174">Remarks</span></span>

<span data-ttu-id="efd64-175">Federace je schopnost sdílet identity napříč několika společnostmi nebo důvěřovat doménám pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="efd64-175">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="efd64-176">Používá protokol WS-Trust k mapování reprezentace identity z jedné domény důvěryhodnosti na jinou.</span><span class="sxs-lookup"><span data-stu-id="efd64-176">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="efd64-177">Federační vazba protokolu HTTP podporuje zabezpečení SOAP i zabezpečení ve smíšeném režimu, ale nepodporuje zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="efd64-177">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="efd64-178">Služby nakonfigurované s touto vazbou musí používat přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="efd64-178">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="efd64-179">Další informace najdete v tématu [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="efd64-179">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="efd64-180">Příklad</span><span class="sxs-lookup"><span data-stu-id="efd64-180">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="efd64-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="efd64-181">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="efd64-182">Vazby</span><span class="sxs-lookup"><span data-stu-id="efd64-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="efd64-183">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="efd64-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="efd64-184">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="efd64-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
