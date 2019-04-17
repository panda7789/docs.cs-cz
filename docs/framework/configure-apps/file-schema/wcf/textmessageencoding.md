---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e6e6d1907d89a09a72594a836f2192e9ad9c4290
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614113"
---
# <a name="textmessageencoding"></a><span data-ttu-id="6b839-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="6b839-101">\<textMessageEncoding></span></span>
<span data-ttu-id="6b839-102">Určuje kódování znaků a verzování zprávy použité pro textově založené zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="6b839-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="6b839-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6b839-103">\<system.serviceModel></span></span>  
<span data-ttu-id="6b839-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="6b839-104">\<bindings></span></span>  
<span data-ttu-id="6b839-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6b839-105">\<customBinding></span></span>  
<span data-ttu-id="6b839-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="6b839-106">\<binding></span></span>  
<span data-ttu-id="6b839-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="6b839-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b839-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b839-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b839-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6b839-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6b839-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6b839-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b839-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6b839-111">Attributes</span></span>  
  
|<span data-ttu-id="6b839-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b839-112">Attribute</span></span>|<span data-ttu-id="6b839-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6b839-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b839-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="6b839-114">maxReadPoolSize</span></span>|<span data-ttu-id="6b839-115">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="6b839-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="6b839-116">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="6b839-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="6b839-117">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="6b839-117">The default is 64.</span></span>|  
|<span data-ttu-id="6b839-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="6b839-118">maxWritePoolSize</span></span>|<span data-ttu-id="6b839-119">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="6b839-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="6b839-120">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="6b839-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="6b839-121">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="6b839-121">The default is 16.</span></span>|  
|<span data-ttu-id="6b839-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="6b839-122">messageVersion</span></span>|<span data-ttu-id="6b839-123">Určuje verzi protokolu SOAP zprávy odesílané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="6b839-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="6b839-124">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="6b839-124">Valid values are</span></span><br /><br /> <span data-ttu-id="6b839-125">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="6b839-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="6b839-126">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="6b839-126">-   Soap12Addressing10</span></span><br /><span data-ttu-id="6b839-127">-Soap11</span><span class="sxs-lookup"><span data-stu-id="6b839-127">-   Soap11</span></span><br /><span data-ttu-id="6b839-128">-Soap12</span><span class="sxs-lookup"><span data-stu-id="6b839-128">-  Soap12</span></span><br /><br /><span data-ttu-id="6b839-129">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="6b839-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="6b839-130">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="6b839-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="6b839-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="6b839-131">writeEncoding</span></span>|<span data-ttu-id="6b839-132">Určuje znakovou sadu kódování pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="6b839-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="6b839-133">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="6b839-133">Valid values are</span></span><br /><br /> <span data-ttu-id="6b839-134">-UnicodeFffeTextEncoding: Kódování Unicode BigEndian kódování</span><span class="sxs-lookup"><span data-stu-id="6b839-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="6b839-135">-Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="6b839-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="6b839-136">-Utf8TextEncoding: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="6b839-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="6b839-137">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="6b839-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="6b839-138">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="6b839-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b839-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6b839-139">Child Elements</span></span>  
  
|<span data-ttu-id="6b839-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="6b839-140">Element</span></span>|<span data-ttu-id="6b839-141">Popis</span><span class="sxs-lookup"><span data-stu-id="6b839-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b839-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6b839-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="6b839-143">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="6b839-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6b839-144">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="6b839-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b839-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6b839-145">Parent Elements</span></span>  
  
|<span data-ttu-id="6b839-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="6b839-146">Element</span></span>|<span data-ttu-id="6b839-147">Popis</span><span class="sxs-lookup"><span data-stu-id="6b839-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b839-148">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="6b839-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6b839-149">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="6b839-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b839-150">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b839-150">Remarks</span></span>  
 <span data-ttu-id="6b839-151">Kódování je proces transformace zprávu do sekvence bajtů.</span><span class="sxs-lookup"><span data-stu-id="6b839-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="6b839-152">Dekódování je opačný proces.</span><span class="sxs-lookup"><span data-stu-id="6b839-152">Decoding is the reverse process.</span></span> <span data-ttu-id="6b839-153">Windows Communication Foundation (WCF) zahrnuje tři typy kódování zprávy protokolu SOAP: Text, binární soubor a mechanismus optimalizaci přenosu zprávu (MTOM).</span><span class="sxs-lookup"><span data-stu-id="6b839-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="6b839-154">Kódování textu reprezentována `textMessageEncoding` prvek je interaktivní, ale nejméně efektivní kodéru zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="6b839-154">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="6b839-155">Kodér textu vytvoří textových zpráv na lince.</span><span class="sxs-lookup"><span data-stu-id="6b839-155">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="6b839-156">Zprávy vytvořené v tomto kodéru jsou vhodné pro WS-\* na základě spolupráce.</span><span class="sxs-lookup"><span data-stu-id="6b839-156">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="6b839-157">Webová služba nebo klient webové služby obecně by rozuměla textové XML.</span><span class="sxs-lookup"><span data-stu-id="6b839-157">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="6b839-158">Přenášení velkých bloků binárních dat jako text je však nejméně efektivní způsob pro kódování zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="6b839-158">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b839-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b839-159">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="6b839-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b839-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="6b839-161">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="6b839-161">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="6b839-162">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="6b839-162">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="6b839-163">Vazby</span><span class="sxs-lookup"><span data-stu-id="6b839-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="6b839-164">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="6b839-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6b839-165">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="6b839-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="6b839-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6b839-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
