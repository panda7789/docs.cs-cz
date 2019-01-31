---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: be0a11c71083c713042ab572cb78fbae27d52912
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277690"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="540b6-101">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="540b6-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="540b6-102">Určuje kódování a správu verzí zpráv protokolu SOAP zprávy přenosu optimalizace mechanismus (MTOM) na základě zpráv.</span><span class="sxs-lookup"><span data-stu-id="540b6-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="540b6-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="540b6-103">\<system.serviceModel></span></span>  
<span data-ttu-id="540b6-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="540b6-104">\<bindings></span></span>  
<span data-ttu-id="540b6-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="540b6-105">\<customBinding></span></span>  
<span data-ttu-id="540b6-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="540b6-106">\<binding></span></span>  
<span data-ttu-id="540b6-107">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="540b6-107">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="540b6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="540b6-108">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="540b6-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="540b6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="540b6-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="540b6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="540b6-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="540b6-111">Attributes</span></span>  
  
|<span data-ttu-id="540b6-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="540b6-112">Attribute</span></span>|<span data-ttu-id="540b6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="540b6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="540b6-114">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="540b6-114">maxBufferSize</span></span>|<span data-ttu-id="540b6-115">Celé číslo, které určuje maximální velikost vyrovnávací paměti, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="540b6-115">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="540b6-116">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="540b6-116">maxReadPoolSize</span></span>|<span data-ttu-id="540b6-117">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="540b6-117">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="540b6-118">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="540b6-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="540b6-119">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="540b6-119">The default is 64.</span></span>|  
|<span data-ttu-id="540b6-120">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="540b6-120">maxWritePoolSize</span></span>|<span data-ttu-id="540b6-121">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="540b6-121">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="540b6-122">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="540b6-122">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="540b6-123">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="540b6-123">The default is 16.</span></span>|  
|<span data-ttu-id="540b6-124">messageVersion</span><span class="sxs-lookup"><span data-stu-id="540b6-124">messageVersion</span></span>|<span data-ttu-id="540b6-125">Určuje verzi protokolu SOAP zprávy odesílané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="540b6-125">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="540b6-126">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="540b6-126">Valid values are</span></span><br /><br /> <span data-ttu-id="540b6-127">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="540b6-127">-   Soap11Addressing1</span></span><br /><span data-ttu-id="540b6-128">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="540b6-128">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="540b6-129">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="540b6-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="540b6-130">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="540b6-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="540b6-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="540b6-131">writeEncoding</span></span>|<span data-ttu-id="540b6-132">Určuje znakovou sadu kódování pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="540b6-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="540b6-133">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="540b6-133">Valid values are</span></span><br /><br /> <span data-ttu-id="540b6-134">-UnicodeFffeTextEncoding: Kódování Unicode BigEndian kódování</span><span class="sxs-lookup"><span data-stu-id="540b6-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="540b6-135">-Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="540b6-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="540b6-136">-Utf8TextEncoding: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="540b6-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="540b6-137">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="540b6-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="540b6-138">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="540b6-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="540b6-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="540b6-139">Child Elements</span></span>  
  
|<span data-ttu-id="540b6-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="540b6-140">Element</span></span>|<span data-ttu-id="540b6-141">Popis</span><span class="sxs-lookup"><span data-stu-id="540b6-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="540b6-142">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="540b6-142">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="540b6-143">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="540b6-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="540b6-144">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="540b6-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="540b6-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="540b6-145">Parent Elements</span></span>  
  
|<span data-ttu-id="540b6-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="540b6-146">Element</span></span>|<span data-ttu-id="540b6-147">Popis</span><span class="sxs-lookup"><span data-stu-id="540b6-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="540b6-148">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="540b6-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="540b6-149">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="540b6-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="540b6-150">Poznámky</span><span class="sxs-lookup"><span data-stu-id="540b6-150">Remarks</span></span>  
 <span data-ttu-id="540b6-151">Kódování je proces transformace zprávu do sekvence bajtů.</span><span class="sxs-lookup"><span data-stu-id="540b6-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="540b6-152">Dekódování je opačný proces.</span><span class="sxs-lookup"><span data-stu-id="540b6-152">Decoding is the reverse process.</span></span> <span data-ttu-id="540b6-153">Windows Communication Foundation (WCF) zahrnuje tři typy kódování zprávy protokolu SOAP: Text, binární soubor a mechanismus optimalizaci přenosu zprávu (MTOM).</span><span class="sxs-lookup"><span data-stu-id="540b6-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="540b6-154">`MtomMessageEncoding` Prvek určuje na znak kódování a správu verzí zpráv a další nastavení pro zprávy pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="540b6-154">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="540b6-155">MTOM je efektivní technologie pro přenos zpráv WCF binární data.</span><span class="sxs-lookup"><span data-stu-id="540b6-155">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="540b6-156">Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitu a vzájemná funkční spolupráce.</span><span class="sxs-lookup"><span data-stu-id="540b6-156">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="540b6-157">Kódování MTOM přenáší většina XML v textové formě, ale optimalizuje velkých bloků binárních dat jako ušetřený přenosem-je, bez převodu na jejich formát kódování base64.</span><span class="sxs-lookup"><span data-stu-id="540b6-157">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="540b6-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="540b6-158">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="540b6-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="540b6-159">See also</span></span>
- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="540b6-160">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="540b6-160">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="540b6-161">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="540b6-161">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="540b6-162">Vazby</span><span class="sxs-lookup"><span data-stu-id="540b6-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="540b6-163">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="540b6-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="540b6-164">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="540b6-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="540b6-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="540b6-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
