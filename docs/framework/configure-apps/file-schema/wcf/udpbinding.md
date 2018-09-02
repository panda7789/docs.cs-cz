---
title: '&lt;udpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: e17919ead6d6f7656c39d18b0ce1817c18da524a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421678"
---
# <a name="ltudpbindinggt"></a><span data-ttu-id="32684-102">&lt;udpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="32684-102">&lt;udpBinding&gt;</span></span>
<span data-ttu-id="32684-103">Konfigurace element, který se používá ke konfiguraci <xref:System.ServiceModel.UdpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="32684-103">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="32684-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="32684-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32684-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="32684-105">\<bindings></span></span>  
<span data-ttu-id="32684-106">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="32684-106">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32684-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32684-107">Syntax</span></span>  
  
```xml  
<udpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       duplicateMessageHistoryLength="Integer"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"       maxPendingMessagesTotalSize="Integer"  
       maxReceivedMessageSize="Integer"       maxRetransmitCount="Integer"  
       multicastInterfaceId="Integer"  
              name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       timeToLive="TimeSpan">  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32684-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="32684-108">Attributes and Elements</span></span>  
 <span data-ttu-id="32684-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="32684-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32684-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="32684-110">Attributes</span></span>  
  
|<span data-ttu-id="32684-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="32684-111">Attribute</span></span>|<span data-ttu-id="32684-112">Popis</span><span class="sxs-lookup"><span data-stu-id="32684-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="32684-113">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="32684-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="32684-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="32684-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="32684-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="32684-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="32684-116">Celočíselná hodnota, která určuje délku historie duplicitní zprávy.</span><span class="sxs-lookup"><span data-stu-id="32684-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="32684-117">Celočíselná hodnota, která určuje maximální množství paměti přidělené správci vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu pamětí.</span><span class="sxs-lookup"><span data-stu-id="32684-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="32684-118">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="32684-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="32684-119">Celočíselná hodnota, která určuje maximální velikost v bajtech, vyrovnávací paměti, která ukládá zprávy při jejich zpracování pro koncovým bodem nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="32684-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="32684-120">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="32684-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="32684-121">Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale ještě nebyla odebrána ze vstupní fronty pro instance jednotlivých kanálů.</span><span class="sxs-lookup"><span data-stu-id="32684-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="32684-122">Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="32684-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="32684-123">Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je moc velká pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="32684-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="32684-124">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="32684-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="32684-125">Výchozí hodnota je 65 536 bajty.</span><span class="sxs-lookup"><span data-stu-id="32684-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="32684-126">Celočíselná hodnota, která určuje maximální počet opakování přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="32684-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="32684-127">Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="32684-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="32684-128">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="32684-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="32684-129">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="32684-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="32684-130">Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="32684-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="32684-131">Kromě toho tento název je jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="32684-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="32684-132">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="32684-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="32684-133">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="32684-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="32684-134">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="32684-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="32684-135">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="32684-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="32684-136">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="32684-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="32684-137">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="32684-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="32684-138">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="32684-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="32684-139">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="32684-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="32684-140">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="32684-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="32684-141">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="32684-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="32684-142">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="32684-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="32684-143">Nastaví znakovou sadu kódování, které má být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="32684-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="32684-144">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="32684-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="32684-145">-BigEndianUnicode: BigEndian kódování Unicode kódování.</span><span class="sxs-lookup"><span data-stu-id="32684-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="32684-146">-Unicode: kódování 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="32684-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="32684-147">– UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="32684-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="32684-148">Použije se UTF8.</span><span class="sxs-lookup"><span data-stu-id="32684-148">The default is UTF8.</span></span> <span data-ttu-id="32684-149">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="32684-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="32684-150">Časový interval hodnotu, která určuje time to live pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="32684-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32684-151">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="32684-151">Child Elements</span></span>  
  
|<span data-ttu-id="32684-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="32684-152">Element</span></span>|<span data-ttu-id="32684-153">Popis</span><span class="sxs-lookup"><span data-stu-id="32684-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32684-154">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="32684-154">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="32684-155">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="32684-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="32684-156">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="32684-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32684-157">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="32684-157">Parent Elements</span></span>  
  
|<span data-ttu-id="32684-158">Prvek</span><span class="sxs-lookup"><span data-stu-id="32684-158">Element</span></span>|<span data-ttu-id="32684-159">Popis</span><span class="sxs-lookup"><span data-stu-id="32684-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32684-160">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="32684-160">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="32684-161">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="32684-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32684-162">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32684-162">Remarks</span></span>  
 <span data-ttu-id="32684-163">UdpBinding umožňuje služeb WCF pro komunikaci pomocí přenosu UDP.</span><span class="sxs-lookup"><span data-stu-id="32684-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="32684-164">Umožňuje "vypal a zapomeň" výměny zpráv kde klient odešle zprávu službě a očekává, že žádná odpověď zpět.</span><span class="sxs-lookup"><span data-stu-id="32684-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32684-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="32684-165">Example</span></span>  
 <span data-ttu-id="32684-166">Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.UdpBinding> pomocí <`udpBinding`> element.</span><span class="sxs-lookup"><span data-stu-id="32684-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
                   timeToLive="00:10:00"  
          <readerQuotas/>   
        </binding>  
      </udpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32684-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="32684-167">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="32684-168">Vazby</span><span class="sxs-lookup"><span data-stu-id="32684-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="32684-169">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="32684-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="32684-170">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="32684-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="32684-171">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="32684-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
