---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 70a124fda5bc0e52e1271716f7e2166b7717b49a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933188"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="3c357-101">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="3c357-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="3c357-102">Určuje kódování a správu verzí zpráv, které se používají pro zprávy založené na protokolu MTOM (přenosu zpráv SOAP).</span><span class="sxs-lookup"><span data-stu-id="3c357-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="3c357-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3c357-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3c357-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="3c357-104">\<bindings></span></span>  
<span data-ttu-id="3c357-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3c357-105">\<customBinding></span></span>  
<span data-ttu-id="3c357-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="3c357-106">\<binding></span></span>  
<span data-ttu-id="3c357-107">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="3c357-107">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c357-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c357-108">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c357-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3c357-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3c357-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3c357-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c357-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3c357-111">Attributes</span></span>  
  
|<span data-ttu-id="3c357-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="3c357-112">Attribute</span></span>|<span data-ttu-id="3c357-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3c357-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c357-114">Třída</span><span class="sxs-lookup"><span data-stu-id="3c357-114">maxBufferSize</span></span>|<span data-ttu-id="3c357-115">Celé číslo, které určuje maximální velikost vyrovnávací paměti, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="3c357-115">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="3c357-116">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="3c357-116">maxReadPoolSize</span></span>|<span data-ttu-id="3c357-117">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="3c357-117">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="3c357-118">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="3c357-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3c357-119">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="3c357-119">The default is 64.</span></span>|  
|<span data-ttu-id="3c357-120">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="3c357-120">maxWritePoolSize</span></span>|<span data-ttu-id="3c357-121">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových zapisovačů.</span><span class="sxs-lookup"><span data-stu-id="3c357-121">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="3c357-122">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="3c357-122">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3c357-123">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="3c357-123">The default is 16.</span></span>|  
|<span data-ttu-id="3c357-124">messageVersion</span><span class="sxs-lookup"><span data-stu-id="3c357-124">messageVersion</span></span>|<span data-ttu-id="3c357-125">Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="3c357-125">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="3c357-126">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="3c357-126">Valid values are</span></span><br /><br /> <span data-ttu-id="3c357-127">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="3c357-127">-   Soap11Addressing1</span></span><br /><span data-ttu-id="3c357-128">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="3c357-128">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="3c357-129">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="3c357-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="3c357-130">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="3c357-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="3c357-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="3c357-131">writeEncoding</span></span>|<span data-ttu-id="3c357-132">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="3c357-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="3c357-133">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="3c357-133">Valid values are</span></span><br /><br /> <span data-ttu-id="3c357-134">- UnicodeFffeTextEncoding: Kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="3c357-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="3c357-135">- Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="3c357-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="3c357-136">- Utf8TextEncoding: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="3c357-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="3c357-137">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="3c357-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="3c357-138">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="3c357-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c357-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3c357-139">Child Elements</span></span>  
  
|<span data-ttu-id="3c357-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="3c357-140">Element</span></span>|<span data-ttu-id="3c357-141">Popis</span><span class="sxs-lookup"><span data-stu-id="3c357-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c357-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3c357-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="3c357-143">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="3c357-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3c357-144">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="3c357-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c357-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3c357-145">Parent Elements</span></span>  
  
|<span data-ttu-id="3c357-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="3c357-146">Element</span></span>|<span data-ttu-id="3c357-147">Popis</span><span class="sxs-lookup"><span data-stu-id="3c357-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c357-148">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="3c357-148">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="3c357-149">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="3c357-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c357-150">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c357-150">Remarks</span></span>  
 <span data-ttu-id="3c357-151">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="3c357-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="3c357-152">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="3c357-152">Decoding is the reverse process.</span></span> <span data-ttu-id="3c357-153">Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: Text, binární a mechanismus optimalizace přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="3c357-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="3c357-154">`MtomMessageEncoding` Prvek určuje kódování znaků a správu verzí zpráv a další nastavení používané pro zprávy pomocí kódování MTOM (Message reoptimization mechanism).</span><span class="sxs-lookup"><span data-stu-id="3c357-154">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="3c357-155">MTOM je efektivní technologie pro přenos binárních dat ve zprávách WCF.</span><span class="sxs-lookup"><span data-stu-id="3c357-155">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="3c357-156">Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitou a interoperabilitou.</span><span class="sxs-lookup"><span data-stu-id="3c357-156">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="3c357-157">Kódování MTOM přenáší většinu XML v textové podobě, ale optimalizuje velké bloky binárních dat jejich odesláním tak, jak jsou, bez konverze do jejich formátu kódovaného ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="3c357-157">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c357-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c357-158">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="3c357-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c357-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="3c357-160">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="3c357-160">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="3c357-161">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="3c357-161">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="3c357-162">Vazby</span><span class="sxs-lookup"><span data-stu-id="3c357-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3c357-163">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="3c357-163">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3c357-164">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="3c357-164">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3c357-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3c357-165">\<customBinding></span></span>](custombinding.md)
