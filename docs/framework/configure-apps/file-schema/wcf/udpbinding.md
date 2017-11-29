---
title: '&lt;udpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8eb4d28885308c400c445ae71019373ec92ed27a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltudpbindinggt"></a><span data-ttu-id="06804-102">&lt;udpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="06804-102">&lt;udpBinding&gt;</span></span>
<span data-ttu-id="06804-103">Element konfigurace slouží ke konfiguraci <xref:System.ServiceModel.UdpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="06804-103">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="06804-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="06804-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="06804-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="06804-105">\<bindings></span></span>  
<span data-ttu-id="06804-106">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="06804-106">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06804-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06804-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06804-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="06804-108">Attributes and Elements</span></span>  
 <span data-ttu-id="06804-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="06804-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06804-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="06804-110">Attributes</span></span>  
  
|<span data-ttu-id="06804-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="06804-111">Attribute</span></span>|<span data-ttu-id="06804-112">Popis</span><span class="sxs-lookup"><span data-stu-id="06804-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="06804-113">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="06804-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="06804-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="06804-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="06804-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="06804-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="06804-116">Celočíselná hodnota, která určuje, jak dlouho historie duplicitní zpráva.</span><span class="sxs-lookup"><span data-stu-id="06804-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="06804-117">Celočíselná hodnota, která určuje maximální množství paměti přidělené pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu.</span><span class="sxs-lookup"><span data-stu-id="06804-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="06804-118">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="06804-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="06804-119">Celočíselná hodnota, která určuje maximální velikost v bajtech vyrovnávací paměti, která ukládá zprávy, když jsou zpracovávány pro koncovým bodem nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="06804-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="06804-120">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="06804-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="06804-121">Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale ještě nebyla odebrána z vstupní fronty pro instance jednotlivých kanálu.</span><span class="sxs-lookup"><span data-stu-id="06804-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="06804-122">Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která lze přijímat pomocí kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="06804-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="06804-123">Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je příliš velké vzhledem k příjemce.</span><span class="sxs-lookup"><span data-stu-id="06804-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="06804-124">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="06804-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="06804-125">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="06804-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="06804-126">Celočíselná hodnota, která určuje maximální počet opakování přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="06804-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="06804-127">Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="06804-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="06804-128">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="06804-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="06804-129">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="06804-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="06804-130">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="06804-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="06804-131">Kromě toho je tento název jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="06804-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="06804-132">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="06804-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="06804-133">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="06804-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="06804-134">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="06804-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="06804-135">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="06804-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="06804-136">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="06804-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="06804-137">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="06804-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="06804-138">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="06804-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="06804-139">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="06804-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="06804-140">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="06804-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="06804-141">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="06804-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="06804-142">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="06804-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="06804-143">Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="06804-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="06804-144">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="06804-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="06804-145">-BigEndianUnicode: Unicode BigEndian kódování.</span><span class="sxs-lookup"><span data-stu-id="06804-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="06804-146">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="06804-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="06804-147">-UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="06804-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="06804-148">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="06804-148">The default is UTF8.</span></span> <span data-ttu-id="06804-149">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="06804-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="06804-150">Hodnota časového rozpětí určující TTL pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="06804-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06804-151">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="06804-151">Child Elements</span></span>  
  
|<span data-ttu-id="06804-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="06804-152">Element</span></span>|<span data-ttu-id="06804-153">Popis</span><span class="sxs-lookup"><span data-stu-id="06804-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06804-154">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="06804-154">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="06804-155">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="06804-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="06804-156">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="06804-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06804-157">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="06804-157">Parent Elements</span></span>  
  
|<span data-ttu-id="06804-158">Prvek</span><span class="sxs-lookup"><span data-stu-id="06804-158">Element</span></span>|<span data-ttu-id="06804-159">Popis</span><span class="sxs-lookup"><span data-stu-id="06804-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06804-160">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="06804-160">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="06804-161">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="06804-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06804-162">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06804-162">Remarks</span></span>  
 <span data-ttu-id="06804-163">UdpBinding umožňuje službám WCF pro komunikaci pomocí přenosu UDP.</span><span class="sxs-lookup"><span data-stu-id="06804-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="06804-164">To umožňuje používat pro "fire a zapomněli" výměny zpráv kde klient odešle zprávu do služby a očekává žádná odpověď zpět.</span><span class="sxs-lookup"><span data-stu-id="06804-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06804-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="06804-165">Example</span></span>  
 <span data-ttu-id="06804-166">Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.UdpBinding> pomocí <`udpBinding`> elementu.</span><span class="sxs-lookup"><span data-stu-id="06804-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06804-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="06804-167">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="06804-168">Vazby</span><span class="sxs-lookup"><span data-stu-id="06804-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="06804-169">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="06804-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="06804-170">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="06804-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="06804-171">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="06804-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
