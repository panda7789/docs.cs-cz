---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 743eaa281fef233ddc2e8af5cee890bd10ce0963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941190"
---
# <a name="udpbinding"></a><span data-ttu-id="b279d-101">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="b279d-101">\<udpBinding></span></span>
<span data-ttu-id="b279d-102">Prvek konfigurace, který slouží ke konfiguraci <xref:System.ServiceModel.UdpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="b279d-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="b279d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b279d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b279d-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="b279d-104">\<bindings></span></span>  
<span data-ttu-id="b279d-105">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="b279d-105">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b279d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b279d-106">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b279d-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b279d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b279d-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b279d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b279d-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b279d-109">Attributes</span></span>  
  
|<span data-ttu-id="b279d-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="b279d-110">Attribute</span></span>|<span data-ttu-id="b279d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b279d-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="b279d-112"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="b279d-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b279d-113">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b279d-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b279d-114">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b279d-114">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="b279d-115">Celočíselná hodnota, která určuje duplicitní délku historie zprávy.</span><span class="sxs-lookup"><span data-stu-id="b279d-115">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="b279d-116">Celočíselná hodnota, která určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu.</span><span class="sxs-lookup"><span data-stu-id="b279d-116">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="b279d-117">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="b279d-117">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="b279d-118">Celočíselná hodnota, která určuje maximální velikost vyrovnávací paměti v bajtech, která ukládá zprávy, když jsou zpracovávány pro koncový bod nakonfigurovaný pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="b279d-118">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="b279d-119">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="b279d-119">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="b279d-120">Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale nebyly dosud odebrány ze vstupní fronty pro jednotlivou instanci kanálu.</span><span class="sxs-lookup"><span data-stu-id="b279d-120">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="b279d-121">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček, pro zprávu, která se dá přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="b279d-121">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="b279d-122">Odesilatel obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="b279d-122">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="b279d-123">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="b279d-123">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b279d-124">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="b279d-124">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="b279d-125">Celočíselná hodnota, která určuje maximální počet znovu odeslaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="b279d-125">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="b279d-126">Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="b279d-126">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="b279d-127">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="b279d-127">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b279d-128">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="b279d-128">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b279d-129">Každá vazba má `name` atribut a `namespace` , který společně jednoznačně identifikuje v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="b279d-129">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="b279d-130">Kromě toho je tento název jedinečný mezi vazbami stejného typu.</span><span class="sxs-lookup"><span data-stu-id="b279d-130">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="b279d-131">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="b279d-131">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b279d-132">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b279d-132">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="b279d-133"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="b279d-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b279d-134">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b279d-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b279d-135">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b279d-135">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b279d-136"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="b279d-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b279d-137">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b279d-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b279d-138">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="b279d-138">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b279d-139"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="b279d-139">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b279d-140">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b279d-140">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b279d-141">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b279d-141">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="b279d-142">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="b279d-142">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b279d-143">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="b279d-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b279d-144">- BigEndianUnicode: Kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="b279d-144">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="b279d-145">Sady 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="b279d-145">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="b279d-146">-   UTF8: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="b279d-146">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b279d-147">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="b279d-147">The default is UTF8.</span></span> <span data-ttu-id="b279d-148">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b279d-148">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="b279d-149">Hodnota TimeSpan, která určuje dobu, po kterou má být tato vazba živá.</span><span class="sxs-lookup"><span data-stu-id="b279d-149">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b279d-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b279d-150">Child Elements</span></span>  
  
|<span data-ttu-id="b279d-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="b279d-151">Element</span></span>|<span data-ttu-id="b279d-152">Popis</span><span class="sxs-lookup"><span data-stu-id="b279d-152">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b279d-153">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b279d-153">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="b279d-154">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b279d-154">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b279d-155">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b279d-155">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b279d-156">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b279d-156">Parent Elements</span></span>  
  
|<span data-ttu-id="b279d-157">Prvek</span><span class="sxs-lookup"><span data-stu-id="b279d-157">Element</span></span>|<span data-ttu-id="b279d-158">Popis</span><span class="sxs-lookup"><span data-stu-id="b279d-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b279d-159">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="b279d-159">\<bindings></span></span>](bindings.md)|<span data-ttu-id="b279d-160">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="b279d-160">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b279d-161">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b279d-161">Remarks</span></span>  
 <span data-ttu-id="b279d-162">UdpBinding umožňuje službám WCF komunikovat přes přenos UDP.</span><span class="sxs-lookup"><span data-stu-id="b279d-162">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="b279d-163">Umožňuje výměnu zpráv typu "oheň a zapomenout", kde klient odesílá zprávu službě a neočekává zpětnou odezvu.</span><span class="sxs-lookup"><span data-stu-id="b279d-163">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b279d-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="b279d-164">Example</span></span>  
 <span data-ttu-id="b279d-165">Následující příklad ukazuje, jak konfigurovat <xref:System.ServiceModel.UdpBinding> pomocí elementu <`udpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="b279d-165">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="b279d-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b279d-166">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="b279d-167">Vazby</span><span class="sxs-lookup"><span data-stu-id="b279d-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b279d-168">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b279d-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b279d-169">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b279d-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b279d-170">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="b279d-170">\<binding></span></span>](../../../misc/binding.md)
