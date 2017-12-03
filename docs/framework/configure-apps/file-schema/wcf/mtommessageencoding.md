---
title: '&lt;mtomMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3dda3e6691339541019b270c6759a864726815b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltmtommessageencodinggt"></a><span data-ttu-id="4414b-102">&lt;mtomMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="4414b-102">&lt;mtomMessageEncoding&gt;</span></span>
<span data-ttu-id="4414b-103">Určuje kódování a zpráva Správa verzí pro zprávy protokolu SOAP zprávy přenosu optimalizace mechanismus (MTOM) na základě.</span><span class="sxs-lookup"><span data-stu-id="4414b-103">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="4414b-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4414b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4414b-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4414b-105">\<bindings></span></span>  
<span data-ttu-id="4414b-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4414b-106">\<customBinding></span></span>  
<span data-ttu-id="4414b-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="4414b-107">\<binding></span></span>  
<span data-ttu-id="4414b-108">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="4414b-108">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4414b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4414b-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4414b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4414b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4414b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4414b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4414b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4414b-112">Attributes</span></span>  
  
|<span data-ttu-id="4414b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4414b-113">Attribute</span></span>|<span data-ttu-id="4414b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4414b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4414b-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="4414b-115">maxBufferSize</span></span>|<span data-ttu-id="4414b-116">Celé číslo, které určuje maximální velikost vyrovnávací paměti, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="4414b-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="4414b-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4414b-117">maxReadPoolSize</span></span>|<span data-ttu-id="4414b-118">Celé číslo, které určuje, kolik zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="4414b-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4414b-119">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="4414b-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4414b-120">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="4414b-120">The default is 64.</span></span>|  
|<span data-ttu-id="4414b-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4414b-121">maxWritePoolSize</span></span>|<span data-ttu-id="4414b-122">Celé číslo, které určuje, kolik zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="4414b-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4414b-123">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="4414b-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4414b-124">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="4414b-124">The default is 16.</span></span>|  
|<span data-ttu-id="4414b-125">verze messageVersion</span><span class="sxs-lookup"><span data-stu-id="4414b-125">messageVersion</span></span>|<span data-ttu-id="4414b-126">Určuje verzi protokolu SOAP zprávy odeslané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="4414b-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="4414b-127">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="4414b-127">Valid values are</span></span><br /><br /> <span data-ttu-id="4414b-128">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="4414b-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="4414b-129">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="4414b-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="4414b-130">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="4414b-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="4414b-131">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="4414b-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="4414b-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="4414b-132">writeEncoding</span></span>|<span data-ttu-id="4414b-133">Určuje znakovou sadu kódování má být použit pro generování zpráv v rámci vazby.</span><span class="sxs-lookup"><span data-stu-id="4414b-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4414b-134">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="4414b-134">Valid values are</span></span><br /><br /> <span data-ttu-id="4414b-135">-UnicodeFffeTextEncoding: Unicode BigEndian kódování</span><span class="sxs-lookup"><span data-stu-id="4414b-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="4414b-136">-Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="4414b-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="4414b-137">-Utf8TextEncoding: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="4414b-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4414b-138">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="4414b-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="4414b-139">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4414b-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4414b-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4414b-140">Child Elements</span></span>  
  
|<span data-ttu-id="4414b-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="4414b-141">Element</span></span>|<span data-ttu-id="4414b-142">Popis</span><span class="sxs-lookup"><span data-stu-id="4414b-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4414b-143">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="4414b-143">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="4414b-144">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="4414b-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4414b-145">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4414b-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4414b-146">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4414b-146">Parent Elements</span></span>  
  
|<span data-ttu-id="4414b-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="4414b-147">Element</span></span>|<span data-ttu-id="4414b-148">Popis</span><span class="sxs-lookup"><span data-stu-id="4414b-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4414b-149">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="4414b-149">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4414b-150">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="4414b-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4414b-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4414b-151">Remarks</span></span>  
 <span data-ttu-id="4414b-152">Proces transformace zprávu do pořadí bajtů kódování je.</span><span class="sxs-lookup"><span data-stu-id="4414b-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4414b-153">Dekódování je zpětné proces.</span><span class="sxs-lookup"><span data-stu-id="4414b-153">Decoding is the reverse process.</span></span> <span data-ttu-id="4414b-154">Windows Communication Foundation (WCF) zahrnuje tři typy kódování pro protokolu SOAP zprávy: Text, Binary a zpráva přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4414b-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4414b-155">`MtomMessageEncoding` Element určuje Správa verzí pro kódování a zpráva znak a další nastavení pro zprávy pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4414b-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="4414b-156">MTOM je technologie efektivní přenosu zpráv binární data v zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="4414b-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="4414b-157">Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitu a vzájemná funkční spolupráce.</span><span class="sxs-lookup"><span data-stu-id="4414b-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="4414b-158">Kódování MTOM přenáší většina XML v textové podobě, ale optimalizuje velkých bloků binárních dat tím, že je jako přenosu-je, bez převod na jejich formátu s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="4414b-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4414b-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="4414b-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="4414b-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="4414b-160">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [<span data-ttu-id="4414b-161">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="4414b-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="4414b-162">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="4414b-162">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="4414b-163">Vazby</span><span class="sxs-lookup"><span data-stu-id="4414b-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4414b-164">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="4414b-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="4414b-165">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4414b-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="4414b-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4414b-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
