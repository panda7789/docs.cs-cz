---
title: '&lt;mtomMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 25990e5583ba1daca378af40e7e56953c95b4a66
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746813"
---
# <a name="ltmtommessageencodinggt"></a><span data-ttu-id="c6e74-102">&lt;mtomMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="c6e74-102">&lt;mtomMessageEncoding&gt;</span></span>
<span data-ttu-id="c6e74-103">Určuje kódování a zpráva Správa verzí pro zprávy protokolu SOAP zprávy přenosu optimalizace mechanismus (MTOM) na základě.</span><span class="sxs-lookup"><span data-stu-id="c6e74-103">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="c6e74-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c6e74-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c6e74-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="c6e74-105">\<bindings></span></span>  
<span data-ttu-id="c6e74-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c6e74-106">\<customBinding></span></span>  
<span data-ttu-id="c6e74-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="c6e74-107">\<binding></span></span>  
<span data-ttu-id="c6e74-108">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="c6e74-108">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e74-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6e74-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6e74-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c6e74-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c6e74-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c6e74-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6e74-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c6e74-112">Attributes</span></span>  
  
|<span data-ttu-id="c6e74-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c6e74-113">Attribute</span></span>|<span data-ttu-id="c6e74-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c6e74-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6e74-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="c6e74-115">maxBufferSize</span></span>|<span data-ttu-id="c6e74-116">Celé číslo, které určuje maximální velikost vyrovnávací paměti, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="c6e74-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="c6e74-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="c6e74-117">maxReadPoolSize</span></span>|<span data-ttu-id="c6e74-118">Celé číslo, které určuje, kolik zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="c6e74-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="c6e74-119">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="c6e74-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="c6e74-120">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="c6e74-120">The default is 64.</span></span>|  
|<span data-ttu-id="c6e74-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="c6e74-121">maxWritePoolSize</span></span>|<span data-ttu-id="c6e74-122">Celé číslo, které určuje, kolik zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="c6e74-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="c6e74-123">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="c6e74-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="c6e74-124">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="c6e74-124">The default is 16.</span></span>|  
|<span data-ttu-id="c6e74-125">verze messageVersion</span><span class="sxs-lookup"><span data-stu-id="c6e74-125">messageVersion</span></span>|<span data-ttu-id="c6e74-126">Určuje verzi protokolu SOAP zprávy odeslané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="c6e74-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="c6e74-127">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="c6e74-127">Valid values are</span></span><br /><br /> <span data-ttu-id="c6e74-128">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="c6e74-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="c6e74-129">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="c6e74-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="c6e74-130">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="c6e74-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="c6e74-131">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="c6e74-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="c6e74-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="c6e74-132">writeEncoding</span></span>|<span data-ttu-id="c6e74-133">Určuje znakovou sadu kódování má být použit pro generování zpráv v rámci vazby.</span><span class="sxs-lookup"><span data-stu-id="c6e74-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="c6e74-134">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="c6e74-134">Valid values are</span></span><br /><br /> <span data-ttu-id="c6e74-135">-UnicodeFffeTextEncoding: Unicode BigEndian kódování</span><span class="sxs-lookup"><span data-stu-id="c6e74-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="c6e74-136">-Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="c6e74-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="c6e74-137">-Utf8TextEncoding: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="c6e74-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="c6e74-138">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="c6e74-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="c6e74-139">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="c6e74-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6e74-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c6e74-140">Child Elements</span></span>  
  
|<span data-ttu-id="c6e74-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6e74-141">Element</span></span>|<span data-ttu-id="c6e74-142">Popis</span><span class="sxs-lookup"><span data-stu-id="c6e74-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6e74-143">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="c6e74-143">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="c6e74-144">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="c6e74-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c6e74-145">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="c6e74-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6e74-146">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c6e74-146">Parent Elements</span></span>  
  
|<span data-ttu-id="c6e74-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6e74-147">Element</span></span>|<span data-ttu-id="c6e74-148">Popis</span><span class="sxs-lookup"><span data-stu-id="c6e74-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6e74-149">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="c6e74-149">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c6e74-150">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="c6e74-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6e74-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6e74-151">Remarks</span></span>  
 <span data-ttu-id="c6e74-152">Proces transformace zprávu do pořadí bajtů kódování je.</span><span class="sxs-lookup"><span data-stu-id="c6e74-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="c6e74-153">Dekódování je zpětné proces.</span><span class="sxs-lookup"><span data-stu-id="c6e74-153">Decoding is the reverse process.</span></span> <span data-ttu-id="c6e74-154">Windows Communication Foundation (WCF) zahrnuje tři typy kódování pro protokolu SOAP zprávy: Text, Binary a zpráva přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="c6e74-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="c6e74-155">`MtomMessageEncoding` Element určuje Správa verzí pro kódování a zpráva znak a další nastavení pro zprávy pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="c6e74-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="c6e74-156">MTOM je technologie efektivní přenosu zpráv binární data v zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="c6e74-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="c6e74-157">Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitu a vzájemná funkční spolupráce.</span><span class="sxs-lookup"><span data-stu-id="c6e74-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="c6e74-158">Kódování MTOM přenáší většina XML v textové podobě, ale optimalizuje velkých bloků binárních dat tím, že je jako přenosu-je, bez převod na jejich formátu s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="c6e74-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6e74-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6e74-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6e74-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6e74-160">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [<span data-ttu-id="c6e74-161">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="c6e74-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="c6e74-162">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="c6e74-162">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="c6e74-163">Vazby</span><span class="sxs-lookup"><span data-stu-id="c6e74-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c6e74-164">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="c6e74-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c6e74-165">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="c6e74-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c6e74-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c6e74-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
