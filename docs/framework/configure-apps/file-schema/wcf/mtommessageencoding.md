---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: bd38bf812e6d8d9e57d99bf1a5b77ebb776193a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738836"
---
# \<mtomMessageEncoding>
<span data-ttu-id="74b72-101">Určuje kódování a správu verzí zpráv, které se používají pro zprávy založené na protokolu MTOM (přenosu zpráv SOAP).</span><span class="sxs-lookup"><span data-stu-id="74b72-101">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="74b72-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74b72-102">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74b72-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74b72-103">Attributes and Elements</span></span>  
 <span data-ttu-id="74b72-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74b72-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74b72-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="74b72-105">Attributes</span></span>  
  
|<span data-ttu-id="74b72-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="74b72-106">Attribute</span></span>|<span data-ttu-id="74b72-107">Popis</span><span class="sxs-lookup"><span data-stu-id="74b72-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74b72-108">Třída</span><span class="sxs-lookup"><span data-stu-id="74b72-108">maxBufferSize</span></span>|<span data-ttu-id="74b72-109">Celé číslo, které určuje maximální velikost vyrovnávací paměti, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="74b72-109">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="74b72-110">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="74b72-110">maxReadPoolSize</span></span>|<span data-ttu-id="74b72-111">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="74b72-111">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="74b72-112">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="74b72-112">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="74b72-113">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="74b72-113">The default is 64.</span></span>|  
|<span data-ttu-id="74b72-114">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="74b72-114">maxWritePoolSize</span></span>|<span data-ttu-id="74b72-115">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových zapisovačů.</span><span class="sxs-lookup"><span data-stu-id="74b72-115">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="74b72-116">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="74b72-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="74b72-117">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="74b72-117">The default is 16.</span></span>|  
|<span data-ttu-id="74b72-118">messageVersion</span><span class="sxs-lookup"><span data-stu-id="74b72-118">messageVersion</span></span>|<span data-ttu-id="74b72-119">Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="74b72-119">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="74b72-120">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="74b72-120">Valid values are</span></span><br /><br /> <span data-ttu-id="74b72-121">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="74b72-121">-   Soap11Addressing1</span></span><br /><span data-ttu-id="74b72-122">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="74b72-122">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="74b72-123">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="74b72-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="74b72-124">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="74b72-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="74b72-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="74b72-125">writeEncoding</span></span>|<span data-ttu-id="74b72-126">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="74b72-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="74b72-127">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="74b72-127">Valid values are</span></span><br /><br /> <span data-ttu-id="74b72-128">-UnicodeFffeTextEncoding: kódování Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="74b72-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="74b72-129">-Utf16TextEncoding: kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="74b72-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="74b72-130">-Utf8TextEncoding: 8bitové kódování</span><span class="sxs-lookup"><span data-stu-id="74b72-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="74b72-131">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="74b72-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="74b72-132">Tento atribut je typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="74b72-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74b72-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74b72-133">Child Elements</span></span>  
  
|<span data-ttu-id="74b72-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="74b72-134">Element</span></span>|<span data-ttu-id="74b72-135">Description</span><span class="sxs-lookup"><span data-stu-id="74b72-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="74b72-136">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="74b72-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="74b72-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="74b72-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74b72-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74b72-138">Parent Elements</span></span>  
  
|<span data-ttu-id="74b72-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="74b72-139">Element</span></span>|<span data-ttu-id="74b72-140">Description</span><span class="sxs-lookup"><span data-stu-id="74b72-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="74b72-141">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="74b72-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74b72-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74b72-142">Remarks</span></span>  
 <span data-ttu-id="74b72-143">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="74b72-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="74b72-144">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="74b72-144">Decoding is the reverse process.</span></span> <span data-ttu-id="74b72-145">Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: text, binární a mechanismus pro optimalizaci přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="74b72-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="74b72-146">`MtomMessageEncoding`Prvek určuje kódování znaků a správu verzí zpráv a další nastavení používané pro zprávy pomocí kódování MTOM (Message Reoptimization mechanism).</span><span class="sxs-lookup"><span data-stu-id="74b72-146">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="74b72-147">MTOM je efektivní technologie pro přenos binárních dat ve zprávách WCF.</span><span class="sxs-lookup"><span data-stu-id="74b72-147">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="74b72-148">Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitou a interoperabilitou.</span><span class="sxs-lookup"><span data-stu-id="74b72-148">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="74b72-149">Kódování MTOM přenáší většinu XML v textové podobě, ale optimalizuje velké bloky binárních dat jejich odesláním tak, jak jsou, bez konverze do jejich formátu kódovaného ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="74b72-149">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74b72-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="74b72-150">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="74b72-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="74b72-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="74b72-152">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="74b72-152">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="74b72-153">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="74b72-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="74b72-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="74b72-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="74b72-155">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="74b72-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="74b72-156">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="74b72-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
