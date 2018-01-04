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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f43462ac42c59407ae90f2d342a445a688e1b26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltudpbindinggt"></a><span data-ttu-id="7bd23-102">&lt;udpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="7bd23-102">&lt;udpBinding&gt;</span></span>
<span data-ttu-id="7bd23-103">Element konfigurace slouží ke konfiguraci <xref:System.ServiceModel.UdpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="7bd23-103">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="7bd23-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7bd23-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7bd23-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7bd23-105">\<bindings></span></span>  
<span data-ttu-id="7bd23-106">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="7bd23-106">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd23-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bd23-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bd23-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7bd23-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7bd23-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7bd23-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bd23-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7bd23-110">Attributes</span></span>  
  
|<span data-ttu-id="7bd23-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="7bd23-111">Attribute</span></span>|<span data-ttu-id="7bd23-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7bd23-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7bd23-113">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="7bd23-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7bd23-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7bd23-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7bd23-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7bd23-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="7bd23-116">Celočíselná hodnota, která určuje, jak dlouho historie duplicitní zpráva.</span><span class="sxs-lookup"><span data-stu-id="7bd23-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="7bd23-117">Celočíselná hodnota, která určuje maximální množství paměti přidělené pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu.</span><span class="sxs-lookup"><span data-stu-id="7bd23-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="7bd23-118">Výchozí hodnota je 524288 (0x80000) bajtů.</span><span class="sxs-lookup"><span data-stu-id="7bd23-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="7bd23-119">Celočíselná hodnota, která určuje maximální velikost v bajtech vyrovnávací paměti, která ukládá zprávy, když jsou zpracovávány pro koncovým bodem nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7bd23-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="7bd23-120">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7bd23-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="7bd23-121">Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale ještě nebyla odebrána z vstupní fronty pro instance jednotlivých kanálu.</span><span class="sxs-lookup"><span data-stu-id="7bd23-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="7bd23-122">Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která lze přijímat pomocí kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7bd23-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7bd23-123">Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je příliš velké vzhledem k příjemce.</span><span class="sxs-lookup"><span data-stu-id="7bd23-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="7bd23-124">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="7bd23-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7bd23-125">Výchozí hodnota je 65 536 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7bd23-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="7bd23-126">Celočíselná hodnota, která určuje maximální počet opakování přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="7bd23-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="7bd23-127">Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="7bd23-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="7bd23-128">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="7bd23-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7bd23-129">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7bd23-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7bd23-130">Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby.</span><span class="sxs-lookup"><span data-stu-id="7bd23-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="7bd23-131">Kromě toho je tento název jedinečný mezi vazby stejného typu.</span><span class="sxs-lookup"><span data-stu-id="7bd23-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="7bd23-132">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="7bd23-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7bd23-133">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7bd23-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7bd23-134">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="7bd23-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7bd23-135">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7bd23-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7bd23-136">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7bd23-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7bd23-137">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="7bd23-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7bd23-138">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7bd23-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7bd23-139">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="7bd23-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7bd23-140">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="7bd23-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7bd23-141">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7bd23-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7bd23-142">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7bd23-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="7bd23-143">Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="7bd23-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7bd23-144">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="7bd23-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7bd23-145">-BigEndianUnicode: Unicode BigEndian kódování.</span><span class="sxs-lookup"><span data-stu-id="7bd23-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="7bd23-146">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="7bd23-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="7bd23-147">-UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="7bd23-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="7bd23-148">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="7bd23-148">The default is UTF8.</span></span> <span data-ttu-id="7bd23-149">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="7bd23-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="7bd23-150">Hodnota časového rozpětí určující TTL pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7bd23-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bd23-151">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7bd23-151">Child Elements</span></span>  
  
|<span data-ttu-id="7bd23-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="7bd23-152">Element</span></span>|<span data-ttu-id="7bd23-153">Popis</span><span class="sxs-lookup"><span data-stu-id="7bd23-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bd23-154">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="7bd23-154">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="7bd23-155">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="7bd23-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7bd23-156">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="7bd23-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7bd23-157">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7bd23-157">Parent Elements</span></span>  
  
|<span data-ttu-id="7bd23-158">Prvek</span><span class="sxs-lookup"><span data-stu-id="7bd23-158">Element</span></span>|<span data-ttu-id="7bd23-159">Popis</span><span class="sxs-lookup"><span data-stu-id="7bd23-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bd23-160">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7bd23-160">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="7bd23-161">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="7bd23-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bd23-162">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bd23-162">Remarks</span></span>  
 <span data-ttu-id="7bd23-163">UdpBinding umožňuje službám WCF pro komunikaci pomocí přenosu UDP.</span><span class="sxs-lookup"><span data-stu-id="7bd23-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="7bd23-164">To umožňuje používat pro "fire a zapomněli" výměny zpráv kde klient odešle zprávu do služby a očekává žádná odpověď zpět.</span><span class="sxs-lookup"><span data-stu-id="7bd23-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bd23-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="7bd23-165">Example</span></span>  
 <span data-ttu-id="7bd23-166">Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.UdpBinding> pomocí <`udpBinding`> elementu.</span><span class="sxs-lookup"><span data-stu-id="7bd23-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7bd23-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bd23-167">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="7bd23-168">Vazby</span><span class="sxs-lookup"><span data-stu-id="7bd23-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7bd23-169">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="7bd23-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7bd23-170">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="7bd23-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="7bd23-171">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="7bd23-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
