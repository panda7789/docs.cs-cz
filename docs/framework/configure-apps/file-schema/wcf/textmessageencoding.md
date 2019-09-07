---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 1494cee0e412bebc6637ad73354f7c91dc636e15
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399436"
---
# <a name="textmessageencoding"></a><span data-ttu-id="43664-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="43664-101">\<textMessageEncoding></span></span>
<span data-ttu-id="43664-102">Určuje kódování znaků a verze zprávy používané pro textové zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="43664-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
<span data-ttu-id="43664-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="43664-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43664-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="43664-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="43664-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="43664-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="43664-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="43664-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="43664-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="43664-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="43664-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<textMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="43664-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43664-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43664-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43664-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43664-110">Attributes and Elements</span></span>  
 <span data-ttu-id="43664-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43664-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43664-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="43664-112">Attributes</span></span>  
  
|<span data-ttu-id="43664-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="43664-113">Attribute</span></span>|<span data-ttu-id="43664-114">Popis</span><span class="sxs-lookup"><span data-stu-id="43664-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43664-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="43664-115">maxReadPoolSize</span></span>|<span data-ttu-id="43664-116">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="43664-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="43664-117">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="43664-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="43664-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="43664-118">The default is 64.</span></span>|  
|<span data-ttu-id="43664-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="43664-119">maxWritePoolSize</span></span>|<span data-ttu-id="43664-120">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových zapisovačů.</span><span class="sxs-lookup"><span data-stu-id="43664-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="43664-121">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="43664-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="43664-122">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="43664-122">The default is 16.</span></span>|  
|<span data-ttu-id="43664-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="43664-123">messageVersion</span></span>|<span data-ttu-id="43664-124">Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="43664-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="43664-125">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="43664-125">Valid values are</span></span><br /><br /> <span data-ttu-id="43664-126">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="43664-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="43664-127">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="43664-127">-   Soap12Addressing10</span></span><br /><span data-ttu-id="43664-128">- Soap11</span><span class="sxs-lookup"><span data-stu-id="43664-128">-   Soap11</span></span><br /><span data-ttu-id="43664-129">- Soap12</span><span class="sxs-lookup"><span data-stu-id="43664-129">-  Soap12</span></span><br /><br /><span data-ttu-id="43664-130">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="43664-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="43664-131">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="43664-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="43664-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="43664-132">writeEncoding</span></span>|<span data-ttu-id="43664-133">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="43664-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="43664-134">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="43664-134">Valid values are</span></span><br /><br /> <span data-ttu-id="43664-135">- UnicodeFffeTextEncoding: Kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="43664-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="43664-136">- Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="43664-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="43664-137">- Utf8TextEncoding: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="43664-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="43664-138">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="43664-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="43664-139">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="43664-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43664-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43664-140">Child Elements</span></span>  
  
|<span data-ttu-id="43664-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="43664-141">Element</span></span>|<span data-ttu-id="43664-142">Popis</span><span class="sxs-lookup"><span data-stu-id="43664-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43664-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="43664-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="43664-144">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="43664-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="43664-145">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="43664-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43664-146">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43664-146">Parent Elements</span></span>  
  
|<span data-ttu-id="43664-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="43664-147">Element</span></span>|<span data-ttu-id="43664-148">Popis</span><span class="sxs-lookup"><span data-stu-id="43664-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43664-149">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="43664-149">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="43664-150">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="43664-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43664-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43664-151">Remarks</span></span>  
 <span data-ttu-id="43664-152">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="43664-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="43664-153">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="43664-153">Decoding is the reverse process.</span></span> <span data-ttu-id="43664-154">Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: Text, binární a mechanismus optimalizace přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="43664-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="43664-155">Kódování textu reprezentované `textMessageEncoding` prvkem je nejvíce interoperabilní, ale nejméně efektivní kodér pro zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="43664-155">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="43664-156">Kodér textu vytváří textovou zprávu na straně kabelu.</span><span class="sxs-lookup"><span data-stu-id="43664-156">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="43664-157">Zprávy vytvářené v tomto kodéru jsou vhodné pro interoperabilitu WS-\*.</span><span class="sxs-lookup"><span data-stu-id="43664-157">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="43664-158">Webové služby nebo klient webové služby můžou obecně pochopit text XML.</span><span class="sxs-lookup"><span data-stu-id="43664-158">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="43664-159">Přenos velkých bloků binárních dat jako textu je však nejefektivnější metodou pro kódování zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="43664-159">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43664-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="43664-160">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="43664-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43664-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="43664-162">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="43664-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="43664-163">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="43664-163">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="43664-164">Vazby</span><span class="sxs-lookup"><span data-stu-id="43664-164">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="43664-165">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="43664-165">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="43664-166">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="43664-166">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="43664-167">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="43664-167">\<customBinding></span></span>](custombinding.md)
