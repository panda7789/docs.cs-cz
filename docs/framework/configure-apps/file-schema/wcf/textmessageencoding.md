---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: d67d623736f3cbf50568356132a74d2b234fdfd9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736216"
---
# \<textMessageEncoding>
<span data-ttu-id="d965b-101">Určuje kódování znaků a verze zprávy používané pro textové zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="d965b-101">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="d965b-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d965b-102">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d965b-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d965b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d965b-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d965b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d965b-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="d965b-105">Attributes</span></span>  
  
|<span data-ttu-id="d965b-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="d965b-106">Attribute</span></span>|<span data-ttu-id="d965b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d965b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d965b-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="d965b-108">maxReadPoolSize</span></span>|<span data-ttu-id="d965b-109">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="d965b-109">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="d965b-110">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="d965b-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="d965b-111">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="d965b-111">The default is 64.</span></span>|  
|<span data-ttu-id="d965b-112">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="d965b-112">maxWritePoolSize</span></span>|<span data-ttu-id="d965b-113">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových zapisovačů.</span><span class="sxs-lookup"><span data-stu-id="d965b-113">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="d965b-114">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="d965b-114">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="d965b-115">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="d965b-115">The default is 16.</span></span>|  
|<span data-ttu-id="d965b-116">messageVersion</span><span class="sxs-lookup"><span data-stu-id="d965b-116">messageVersion</span></span>|<span data-ttu-id="d965b-117">Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="d965b-117">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="d965b-118">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="d965b-118">Valid values are</span></span><br /><br /> <span data-ttu-id="d965b-119">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="d965b-119">-   Soap11Addressing10</span></span><br /><span data-ttu-id="d965b-120">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="d965b-120">-   Soap12Addressing10</span></span><br /><span data-ttu-id="d965b-121">- Soap11</span><span class="sxs-lookup"><span data-stu-id="d965b-121">-   Soap11</span></span><br /><span data-ttu-id="d965b-122">- Soap12</span><span class="sxs-lookup"><span data-stu-id="d965b-122">-  Soap12</span></span><br /><br /><span data-ttu-id="d965b-123">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="d965b-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="d965b-124">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="d965b-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="d965b-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="d965b-125">writeEncoding</span></span>|<span data-ttu-id="d965b-126">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="d965b-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="d965b-127">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="d965b-127">Valid values are</span></span><br /><br /> <span data-ttu-id="d965b-128">-UnicodeFffeTextEncoding: kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="d965b-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="d965b-129">-Utf16TextEncoding: kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="d965b-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="d965b-130">-Utf8TextEncoding: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="d965b-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="d965b-131">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="d965b-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="d965b-132">Tento atribut je typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="d965b-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d965b-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d965b-133">Child Elements</span></span>  
  
|<span data-ttu-id="d965b-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="d965b-134">Element</span></span>|<span data-ttu-id="d965b-135">Description</span><span class="sxs-lookup"><span data-stu-id="d965b-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="d965b-136">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="d965b-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d965b-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="d965b-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d965b-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d965b-138">Parent Elements</span></span>  
  
|<span data-ttu-id="d965b-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="d965b-139">Element</span></span>|<span data-ttu-id="d965b-140">Description</span><span class="sxs-lookup"><span data-stu-id="d965b-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d965b-141">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d965b-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d965b-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d965b-142">Remarks</span></span>  
 <span data-ttu-id="d965b-143">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="d965b-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="d965b-144">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="d965b-144">Decoding is the reverse process.</span></span> <span data-ttu-id="d965b-145">Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: text, binární a mechanismus pro optimalizaci přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="d965b-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="d965b-146">Kódování textu reprezentované `textMessageEncoding` prvkem je nejvíce interoperabilní, ale nejméně efektivní kodér pro zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="d965b-146">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="d965b-147">Kodér textu vytváří textovou zprávu na straně kabelu.</span><span class="sxs-lookup"><span data-stu-id="d965b-147">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="d965b-148">Zprávy vytvářené v tomto kodéru jsou vhodné pro interoperabilitu WS-\*.</span><span class="sxs-lookup"><span data-stu-id="d965b-148">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="d965b-149">Webové služby nebo klient webové služby můžou obecně pochopit text XML.</span><span class="sxs-lookup"><span data-stu-id="d965b-149">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="d965b-150">Přenos velkých bloků binárních dat jako textu je však nejefektivnější metodou pro kódování zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="d965b-150">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d965b-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="d965b-151">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="d965b-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="d965b-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="d965b-153">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="d965b-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="d965b-154">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="d965b-154">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="d965b-155">Vazby</span><span class="sxs-lookup"><span data-stu-id="d965b-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d965b-156">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="d965b-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d965b-157">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d965b-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
