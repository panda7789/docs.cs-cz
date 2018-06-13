---
title: '&lt;udpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 1d9535f60bca101e53b678da25915ac9afb41aab
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756212"
---
# <a name="ltudpbindinggt"></a><span data-ttu-id="133fb-102">&lt;udpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="133fb-102">&lt;udpBinding&gt;</span></span>
<span data-ttu-id="133fb-103">Element konfigurace slouží ke konfiguraci <xref:System.ServiceModel.UdpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="133fb-103">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="133fb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="133fb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="133fb-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="133fb-105">\<bindings></span></span>  
<span data-ttu-id="133fb-106">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="133fb-106">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="133fb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="133fb-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="133fb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="133fb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="133fb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="133fb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="133fb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="133fb-110">Attributes</span></span>  
  
|<span data-ttu-id="133fb-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="133fb-111">Attribute</span></span>|<span data-ttu-id="133fb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="133fb-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="133fb-113">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="133fb-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="133fb-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="133fb-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="133fb-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="133fb-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="133fb-116">Celočíselná hodnota, která určuje, jak dlouho historie duplicitní zpráva.</span><span class="sxs-lookup"><span data-stu-id="133fb-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="133fb-117">Celočíselná hodnota, která určuje maximální množství paměti přidělené pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu.</span><span class="sxs-lookup"><span data-stu-id="133fb-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="133fb-118">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="133fb-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="133fb-119">Celočíselná hodnota, která určuje maximální velikost v bajtech vyrovnávací paměti, která ukládá zprávy, když jsou zpracovávány pro koncovým bodem nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="133fb-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="133fb-120">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="133fb-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="133fb-121">Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale ještě nebyla odebrána z vstupní fronty pro instance jednotlivých kanálu.</span><span class="sxs-lookup"><span data-stu-id="133fb-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="133fb-122">Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která lze přijímat pomocí kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="133fb-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="133fb-123">Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je příliš velké vzhledem k příjemce.</span><span class="sxs-lookup"><span data-stu-id="133fb-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="133fb-124">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="133fb-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="133fb-125">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="133fb-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="133fb-126">Celočíselná hodnota, která určuje maximální počet opakování přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="133fb-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="133fb-127">Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="133fb-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="133fb-128">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="133fb-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="133fb-129">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="133fb-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="133fb-130">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="133fb-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="133fb-131">Kromě toho je tento název jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="133fb-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="133fb-132">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="133fb-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="133fb-133">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="133fb-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="133fb-134">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="133fb-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="133fb-135">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="133fb-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="133fb-136">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="133fb-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="133fb-137">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="133fb-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="133fb-138">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="133fb-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="133fb-139">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="133fb-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="133fb-140">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="133fb-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="133fb-141">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="133fb-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="133fb-142">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="133fb-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="133fb-143">Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="133fb-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="133fb-144">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="133fb-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="133fb-145">-BigEndianUnicode: Unicode BigEndian kódování.</span><span class="sxs-lookup"><span data-stu-id="133fb-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="133fb-146">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="133fb-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="133fb-147">-UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="133fb-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="133fb-148">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="133fb-148">The default is UTF8.</span></span> <span data-ttu-id="133fb-149">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="133fb-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="133fb-150">Hodnota časového rozpětí určující TTL pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="133fb-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="133fb-151">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="133fb-151">Child Elements</span></span>  
  
|<span data-ttu-id="133fb-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="133fb-152">Element</span></span>|<span data-ttu-id="133fb-153">Popis</span><span class="sxs-lookup"><span data-stu-id="133fb-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="133fb-154">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="133fb-154">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="133fb-155">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="133fb-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="133fb-156">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="133fb-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="133fb-157">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="133fb-157">Parent Elements</span></span>  
  
|<span data-ttu-id="133fb-158">Prvek</span><span class="sxs-lookup"><span data-stu-id="133fb-158">Element</span></span>|<span data-ttu-id="133fb-159">Popis</span><span class="sxs-lookup"><span data-stu-id="133fb-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="133fb-160">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="133fb-160">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="133fb-161">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="133fb-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="133fb-162">Poznámky</span><span class="sxs-lookup"><span data-stu-id="133fb-162">Remarks</span></span>  
 <span data-ttu-id="133fb-163">UdpBinding umožňuje službám WCF pro komunikaci pomocí přenosu UDP.</span><span class="sxs-lookup"><span data-stu-id="133fb-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="133fb-164">To umožňuje používat pro "fire a zapomněli" výměny zpráv kde klient odešle zprávu do služby a očekává žádná odpověď zpět.</span><span class="sxs-lookup"><span data-stu-id="133fb-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="133fb-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="133fb-165">Example</span></span>  
 <span data-ttu-id="133fb-166">Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.UdpBinding> pomocí <`udpBinding`> elementu.</span><span class="sxs-lookup"><span data-stu-id="133fb-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="133fb-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="133fb-167">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="133fb-168">Vazby</span><span class="sxs-lookup"><span data-stu-id="133fb-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="133fb-169">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="133fb-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="133fb-170">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="133fb-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="133fb-171">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="133fb-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
