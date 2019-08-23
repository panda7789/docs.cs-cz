---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e2fec2c2e5979b08ed0d832f636b3d0847b9a5dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915650"
---
# <a name="textmessageencoding"></a><span data-ttu-id="52334-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="52334-101">\<textMessageEncoding></span></span>
<span data-ttu-id="52334-102">Určuje kódování znaků a verze zprávy používané pro textové zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="52334-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="52334-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="52334-103">\<system.serviceModel></span></span>  
<span data-ttu-id="52334-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="52334-104">\<bindings></span></span>  
<span data-ttu-id="52334-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="52334-105">\<customBinding></span></span>  
<span data-ttu-id="52334-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="52334-106">\<binding></span></span>  
<span data-ttu-id="52334-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="52334-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52334-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52334-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52334-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="52334-109">Attributes and Elements</span></span>  
 <span data-ttu-id="52334-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="52334-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52334-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="52334-111">Attributes</span></span>  
  
|<span data-ttu-id="52334-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="52334-112">Attribute</span></span>|<span data-ttu-id="52334-113">Popis</span><span class="sxs-lookup"><span data-stu-id="52334-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52334-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="52334-114">maxReadPoolSize</span></span>|<span data-ttu-id="52334-115">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="52334-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="52334-116">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="52334-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="52334-117">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="52334-117">The default is 64.</span></span>|  
|<span data-ttu-id="52334-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="52334-118">maxWritePoolSize</span></span>|<span data-ttu-id="52334-119">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových zapisovačů.</span><span class="sxs-lookup"><span data-stu-id="52334-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="52334-120">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="52334-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="52334-121">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="52334-121">The default is 16.</span></span>|  
|<span data-ttu-id="52334-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="52334-122">messageVersion</span></span>|<span data-ttu-id="52334-123">Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="52334-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="52334-124">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="52334-124">Valid values are</span></span><br /><br /> <span data-ttu-id="52334-125">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="52334-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="52334-126">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="52334-126">-   Soap12Addressing10</span></span><br /><span data-ttu-id="52334-127">- Soap11</span><span class="sxs-lookup"><span data-stu-id="52334-127">-   Soap11</span></span><br /><span data-ttu-id="52334-128">- Soap12</span><span class="sxs-lookup"><span data-stu-id="52334-128">-  Soap12</span></span><br /><br /><span data-ttu-id="52334-129">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="52334-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="52334-130">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="52334-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="52334-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="52334-131">writeEncoding</span></span>|<span data-ttu-id="52334-132">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="52334-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="52334-133">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="52334-133">Valid values are</span></span><br /><br /> <span data-ttu-id="52334-134">- UnicodeFffeTextEncoding: Kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="52334-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="52334-135">- Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="52334-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="52334-136">- Utf8TextEncoding: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="52334-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="52334-137">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="52334-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="52334-138">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="52334-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52334-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="52334-139">Child Elements</span></span>  
  
|<span data-ttu-id="52334-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="52334-140">Element</span></span>|<span data-ttu-id="52334-141">Popis</span><span class="sxs-lookup"><span data-stu-id="52334-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52334-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="52334-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="52334-143">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="52334-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="52334-144">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="52334-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52334-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="52334-145">Parent Elements</span></span>  
  
|<span data-ttu-id="52334-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="52334-146">Element</span></span>|<span data-ttu-id="52334-147">Popis</span><span class="sxs-lookup"><span data-stu-id="52334-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52334-148">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="52334-148">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="52334-149">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="52334-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52334-150">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52334-150">Remarks</span></span>  
 <span data-ttu-id="52334-151">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="52334-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="52334-152">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="52334-152">Decoding is the reverse process.</span></span> <span data-ttu-id="52334-153">Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: Text, binární a mechanismus optimalizace přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="52334-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="52334-154">Kódování textu reprezentované `textMessageEncoding` prvkem je nejvíce interoperabilní, ale nejméně efektivní kodér pro zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="52334-154">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="52334-155">Kodér textu vytváří textovou zprávu na straně kabelu.</span><span class="sxs-lookup"><span data-stu-id="52334-155">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="52334-156">Zprávy vytvářené v tomto kodéru jsou vhodné pro interoperabilitu WS-\*.</span><span class="sxs-lookup"><span data-stu-id="52334-156">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="52334-157">Webové služby nebo klient webové služby můžou obecně pochopit text XML.</span><span class="sxs-lookup"><span data-stu-id="52334-157">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="52334-158">Přenos velkých bloků binárních dat jako textu je však nejefektivnější metodou pro kódování zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="52334-158">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52334-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="52334-159">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="52334-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52334-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="52334-161">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="52334-161">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="52334-162">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="52334-162">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="52334-163">Vazby</span><span class="sxs-lookup"><span data-stu-id="52334-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="52334-164">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="52334-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="52334-165">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="52334-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="52334-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="52334-166">\<customBinding></span></span>](custombinding.md)
