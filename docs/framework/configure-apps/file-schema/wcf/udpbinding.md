---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 7fa72d233d6489ab6a2c534f69c66a55a22d0f59
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74429830"
---
# \<udpBinding>
<span data-ttu-id="7ec4d-101">Prvek konfigurace, který slouží ke konfiguraci <xref:System.ServiceModel.UdpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-101">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="7ec4d-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ec4d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ec4d-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7ec4d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7ec4d-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ec4d-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="7ec4d-105">Attributes</span></span>  
  
|<span data-ttu-id="7ec4d-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="7ec4d-106">Attribute</span></span>|<span data-ttu-id="7ec4d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7ec4d-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7ec4d-108"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7ec4d-109">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7ec4d-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7ec4d-110">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-110">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="7ec4d-111">Celočíselná hodnota, která určuje duplicitní délku historie zprávy.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-111">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="7ec4d-112">Celočíselná hodnota, která určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-112">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="7ec4d-113">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-113">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="7ec4d-114">Celočíselná hodnota, která určuje maximální velikost vyrovnávací paměti v bajtech, která ukládá zprávy, když jsou zpracovávány pro koncový bod nakonfigurovaný pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-114">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="7ec4d-115">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-115">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="7ec4d-116">Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale nebyly dosud odebrány ze vstupní fronty pro jednotlivou instanci kanálu.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-116">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="7ec4d-117">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček, pro zprávu, která se dá přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-117">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7ec4d-118">Odesilatel obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-118">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="7ec4d-119">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-119">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7ec4d-120">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-120">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="7ec4d-121">Celočíselná hodnota, která určuje maximální počet znovu odeslaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-121">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="7ec4d-122">Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-122">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="7ec4d-123">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-123">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7ec4d-124">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-124">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7ec4d-125">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-125">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7ec4d-126">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ec4d-126">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7ec4d-127"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7ec4d-128">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7ec4d-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7ec4d-129">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-129">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7ec4d-130"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7ec4d-131">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7ec4d-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7ec4d-132">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-132">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7ec4d-133"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7ec4d-134">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7ec4d-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7ec4d-135">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-135">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="7ec4d-136">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-136">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7ec4d-137">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7ec4d-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7ec4d-138">-BigEndianUnicode: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-138">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="7ec4d-139">-Unicode: 16 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-139">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="7ec4d-140">-UTF8:8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="7ec4d-140">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="7ec4d-141">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-141">The default is UTF8.</span></span> <span data-ttu-id="7ec4d-142">Tento atribut je typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="7ec4d-142">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="7ec4d-143">Hodnota TimeSpan, která určuje dobu, po kterou má být tato vazba živá.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-143">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ec4d-144">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7ec4d-144">Child Elements</span></span>  
  
|<span data-ttu-id="7ec4d-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="7ec4d-145">Element</span></span>|<span data-ttu-id="7ec4d-146">Description</span><span class="sxs-lookup"><span data-stu-id="7ec4d-146">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="7ec4d-147">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-147">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7ec4d-148">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="7ec4d-148">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ec4d-149">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7ec4d-149">Parent Elements</span></span>  
  
|<span data-ttu-id="7ec4d-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="7ec4d-150">Element</span></span>|<span data-ttu-id="7ec4d-151">Description</span><span class="sxs-lookup"><span data-stu-id="7ec4d-151">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="7ec4d-152">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-152">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ec4d-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ec4d-153">Remarks</span></span>  
 <span data-ttu-id="7ec4d-154">UdpBinding umožňuje službám WCF komunikovat přes přenos UDP.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-154">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="7ec4d-155">Umožňuje výměnu zpráv typu "oheň a zapomenout", kde klient odesílá zprávu službě a neočekává zpětnou odezvu.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-155">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ec4d-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ec4d-156">Example</span></span>  
 <span data-ttu-id="7ec4d-157">Následující příklad ukazuje, jak konfigurovat <xref:System.ServiceModel.UdpBinding> pomocí `udpBinding` elementu <>.</span><span class="sxs-lookup"><span data-stu-id="7ec4d-157">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ec4d-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ec4d-158">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="7ec4d-159">Vazby</span><span class="sxs-lookup"><span data-stu-id="7ec4d-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7ec4d-160">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="7ec4d-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7ec4d-161">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7ec4d-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
