---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: bd38bf812e6d8d9e57d99bf1a5b77ebb776193a5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738836"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="b8893-101">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="b8893-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="b8893-102">Určuje kódování a správu verzí zpráv, které se používají pro zprávy založené na protokolu MTOM (přenosu zpráv SOAP).</span><span class="sxs-lookup"><span data-stu-id="b8893-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
<span data-ttu-id="b8893-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b8893-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b8893-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b8893-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b8893-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b8893-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b8893-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b8893-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b8893-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="b8893-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b8893-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mtomMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="b8893-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8893-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8893-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8893-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b8893-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b8893-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b8893-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8893-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b8893-112">Attributes</span></span>  
  
|<span data-ttu-id="b8893-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="b8893-113">Attribute</span></span>|<span data-ttu-id="b8893-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b8893-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8893-115">Třída</span><span class="sxs-lookup"><span data-stu-id="b8893-115">maxBufferSize</span></span>|<span data-ttu-id="b8893-116">Celé číslo, které určuje maximální velikost vyrovnávací paměti, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="b8893-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="b8893-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="b8893-117">maxReadPoolSize</span></span>|<span data-ttu-id="b8893-118">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="b8893-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="b8893-119">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="b8893-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b8893-120">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="b8893-120">The default is 64.</span></span>|  
|<span data-ttu-id="b8893-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="b8893-121">maxWritePoolSize</span></span>|<span data-ttu-id="b8893-122">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových zapisovačů.</span><span class="sxs-lookup"><span data-stu-id="b8893-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="b8893-123">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="b8893-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b8893-124">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="b8893-124">The default is 16.</span></span>|  
|<span data-ttu-id="b8893-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="b8893-125">messageVersion</span></span>|<span data-ttu-id="b8893-126">Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="b8893-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="b8893-127">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="b8893-127">Valid values are</span></span><br /><br /> <span data-ttu-id="b8893-128">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="b8893-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="b8893-129">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="b8893-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="b8893-130">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="b8893-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="b8893-131">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="b8893-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="b8893-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="b8893-132">writeEncoding</span></span>|<span data-ttu-id="b8893-133">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="b8893-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b8893-134">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="b8893-134">Valid values are</span></span><br /><br /> <span data-ttu-id="b8893-135">-UnicodeFffeTextEncoding: kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="b8893-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="b8893-136">-Utf16TextEncoding: kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="b8893-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="b8893-137">-Utf8TextEncoding: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="b8893-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b8893-138">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="b8893-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="b8893-139">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b8893-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8893-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b8893-140">Child Elements</span></span>  
  
|<span data-ttu-id="b8893-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="b8893-141">Element</span></span>|<span data-ttu-id="b8893-142">Popis</span><span class="sxs-lookup"><span data-stu-id="b8893-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8893-143">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b8893-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="b8893-144">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b8893-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b8893-145">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b8893-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8893-146">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b8893-146">Parent Elements</span></span>  
  
|<span data-ttu-id="b8893-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="b8893-147">Element</span></span>|<span data-ttu-id="b8893-148">Popis</span><span class="sxs-lookup"><span data-stu-id="b8893-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8893-149">vazba \<</span><span class="sxs-lookup"><span data-stu-id="b8893-149">\<binding></span></span>](bindings.md)|<span data-ttu-id="b8893-150">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="b8893-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8893-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8893-151">Remarks</span></span>  
 <span data-ttu-id="b8893-152">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="b8893-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="b8893-153">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="b8893-153">Decoding is the reverse process.</span></span> <span data-ttu-id="b8893-154">Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: text, binární a mechanismus pro optimalizaci přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="b8893-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="b8893-155">Element `MtomMessageEncoding` určuje kódování znaků a správu verzí zpráv a další nastavení používané pro zprávy pomocí kódování MTOM (Message reoptimization mechanism).</span><span class="sxs-lookup"><span data-stu-id="b8893-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="b8893-156">MTOM je efektivní technologie pro přenos binárních dat ve zprávách WCF.</span><span class="sxs-lookup"><span data-stu-id="b8893-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="b8893-157">Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitou a interoperabilitou.</span><span class="sxs-lookup"><span data-stu-id="b8893-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="b8893-158">Kódování MTOM přenáší většinu XML v textové podobě, ale optimalizuje velké bloky binárních dat jejich odesláním tak, jak jsou, bez konverze do jejich formátu kódovaného ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="b8893-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8893-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8893-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b8893-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8893-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="b8893-161">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="b8893-161">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="b8893-162">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="b8893-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="b8893-163">Vazby</span><span class="sxs-lookup"><span data-stu-id="b8893-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b8893-164">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="b8893-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b8893-165">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="b8893-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b8893-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b8893-166">\<customBinding></span></span>](custombinding.md)
