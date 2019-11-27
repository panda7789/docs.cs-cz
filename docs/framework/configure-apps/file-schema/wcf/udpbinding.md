---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 7fa72d233d6489ab6a2c534f69c66a55a22d0f59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429830"
---
# <a name="udpbinding"></a><span data-ttu-id="a0e83-101">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="a0e83-101">\<udpBinding></span></span>
<span data-ttu-id="a0e83-102">Prvek konfigurace, který slouží ke konfiguraci vazby <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="a0e83-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
<span data-ttu-id="a0e83-103">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0e83-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a0e83-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a0e83-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a0e83-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a0e83-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a0e83-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpBinding >**</span><span class="sxs-lookup"><span data-stu-id="a0e83-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e83-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0e83-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0e83-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a0e83-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a0e83-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a0e83-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0e83-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a0e83-110">Attributes</span></span>  
  
|<span data-ttu-id="a0e83-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a0e83-111">Attribute</span></span>|<span data-ttu-id="a0e83-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a0e83-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="a0e83-113">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="a0e83-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a0e83-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a0e83-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a0e83-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a0e83-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="a0e83-116">Celočíselná hodnota, která určuje duplicitní délku historie zprávy.</span><span class="sxs-lookup"><span data-stu-id="a0e83-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="a0e83-117">Celočíselná hodnota, která určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu.</span><span class="sxs-lookup"><span data-stu-id="a0e83-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="a0e83-118">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="a0e83-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="a0e83-119">Celočíselná hodnota, která určuje maximální velikost vyrovnávací paměti v bajtech, která ukládá zprávy, když jsou zpracovávány pro koncový bod nakonfigurovaný pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="a0e83-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="a0e83-120">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="a0e83-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="a0e83-121">Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale nebyly dosud odebrány ze vstupní fronty pro jednotlivou instanci kanálu.</span><span class="sxs-lookup"><span data-stu-id="a0e83-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="a0e83-122">Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček, pro zprávu, která se dá přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="a0e83-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="a0e83-123">Odesilatel obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká.</span><span class="sxs-lookup"><span data-stu-id="a0e83-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="a0e83-124">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="a0e83-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a0e83-125">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="a0e83-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="a0e83-126">Celočíselná hodnota, která určuje maximální počet znovu odeslaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="a0e83-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="a0e83-127">Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="a0e83-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="a0e83-128">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="a0e83-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a0e83-129">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="a0e83-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a0e83-130">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="a0e83-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a0e83-131">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a0e83-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="a0e83-132">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="a0e83-132">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a0e83-133">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a0e83-133">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a0e83-134">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a0e83-134">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a0e83-135">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="a0e83-135">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a0e83-136">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a0e83-136">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a0e83-137">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a0e83-137">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="a0e83-138">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="a0e83-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a0e83-139">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a0e83-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a0e83-140">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a0e83-140">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="a0e83-141">Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="a0e83-141">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a0e83-142">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="a0e83-142">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a0e83-143">-BigEndianUnicode: kódování Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="a0e83-143">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="a0e83-144">-Unicode: 16 bitů kódování.</span><span class="sxs-lookup"><span data-stu-id="a0e83-144">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="a0e83-145">-UTF8:8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="a0e83-145">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a0e83-146">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="a0e83-146">The default is UTF8.</span></span> <span data-ttu-id="a0e83-147">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a0e83-147">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="a0e83-148">Hodnota TimeSpan, která určuje dobu, po kterou má být tato vazba živá.</span><span class="sxs-lookup"><span data-stu-id="a0e83-148">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0e83-149">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a0e83-149">Child Elements</span></span>  
  
|<span data-ttu-id="a0e83-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0e83-150">Element</span></span>|<span data-ttu-id="a0e83-151">Popis</span><span class="sxs-lookup"><span data-stu-id="a0e83-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0e83-152">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0e83-152">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="a0e83-153">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="a0e83-153">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a0e83-154">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a0e83-154">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0e83-155">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a0e83-155">Parent Elements</span></span>  
  
|<span data-ttu-id="a0e83-156">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0e83-156">Element</span></span>|<span data-ttu-id="a0e83-157">Popis</span><span class="sxs-lookup"><span data-stu-id="a0e83-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0e83-158">vazby \<></span><span class="sxs-lookup"><span data-stu-id="a0e83-158">\<bindings></span></span>](bindings.md)|<span data-ttu-id="a0e83-159">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="a0e83-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0e83-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0e83-160">Remarks</span></span>  
 <span data-ttu-id="a0e83-161">UdpBinding umožňuje službám WCF komunikovat přes přenos UDP.</span><span class="sxs-lookup"><span data-stu-id="a0e83-161">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="a0e83-162">Umožňuje výměnu zpráv typu "oheň a zapomenout", kde klient odesílá zprávu službě a neočekává zpětnou odezvu.</span><span class="sxs-lookup"><span data-stu-id="a0e83-162">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0e83-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0e83-163">Example</span></span>  
 <span data-ttu-id="a0e83-164">Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.UdpBinding> pomocí elementu <`udpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="a0e83-164">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0e83-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0e83-165">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="a0e83-166">Vazby</span><span class="sxs-lookup"><span data-stu-id="a0e83-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a0e83-167">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="a0e83-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a0e83-168">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a0e83-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a0e83-169">vazba \<></span><span class="sxs-lookup"><span data-stu-id="a0e83-169">\<binding></span></span>](bindings.md)
