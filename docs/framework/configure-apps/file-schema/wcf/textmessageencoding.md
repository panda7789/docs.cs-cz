---
title: '&lt;textMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b5ce6d658822a8c4600a3cde09bfb9cb57886ee6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="a778e-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="a778e-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="a778e-103">Určuje kódování znaků a zprávy Správa verzí slouží pro textové zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="a778e-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="a778e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a778e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a778e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a778e-105">\<bindings></span></span>  
<span data-ttu-id="a778e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a778e-106">\<customBinding></span></span>  
<span data-ttu-id="a778e-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a778e-107">\<binding></span></span>  
<span data-ttu-id="a778e-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="a778e-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a778e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a778e-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a778e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a778e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a778e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a778e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a778e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a778e-112">Attributes</span></span>  
  
|<span data-ttu-id="a778e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a778e-113">Attribute</span></span>|<span data-ttu-id="a778e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a778e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a778e-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="a778e-115">maxReadPoolSize</span></span>|<span data-ttu-id="a778e-116">Celé číslo, které určuje, kolik zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="a778e-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="a778e-117">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="a778e-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a778e-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="a778e-118">The default is 64.</span></span>|  
|<span data-ttu-id="a778e-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="a778e-119">maxWritePoolSize</span></span>|<span data-ttu-id="a778e-120">Celé číslo, které určuje, kolik zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="a778e-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="a778e-121">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="a778e-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a778e-122">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="a778e-122">The default is 16.</span></span>|  
|<span data-ttu-id="a778e-123">verze messageVersion</span><span class="sxs-lookup"><span data-stu-id="a778e-123">messageVersion</span></span>|<span data-ttu-id="a778e-124">Určuje verzi protokolu SOAP zprávy odeslané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="a778e-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="a778e-125">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="a778e-125">Valid values are</span></span><br /><br /> <span data-ttu-id="a778e-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="a778e-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="a778e-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="a778e-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="a778e-128">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="a778e-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="a778e-129">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="a778e-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="a778e-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="a778e-130">writeEncoding</span></span>|<span data-ttu-id="a778e-131">Určuje znakovou sadu kódování má být použit pro generování zpráv v rámci vazby.</span><span class="sxs-lookup"><span data-stu-id="a778e-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a778e-132">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="a778e-132">Valid values are</span></span><br /><br /> <span data-ttu-id="a778e-133">-UnicodeFffeTextEncoding: Unicode BigEndian kódování</span><span class="sxs-lookup"><span data-stu-id="a778e-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="a778e-134">-Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="a778e-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="a778e-135">-Utf8TextEncoding: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="a778e-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a778e-136">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="a778e-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="a778e-137">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a778e-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a778e-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a778e-138">Child Elements</span></span>  
  
|<span data-ttu-id="a778e-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="a778e-139">Element</span></span>|<span data-ttu-id="a778e-140">Popis</span><span class="sxs-lookup"><span data-stu-id="a778e-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a778e-141">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="a778e-141">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="a778e-142">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="a778e-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a778e-143">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a778e-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a778e-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a778e-144">Parent Elements</span></span>  
  
|<span data-ttu-id="a778e-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="a778e-145">Element</span></span>|<span data-ttu-id="a778e-146">Popis</span><span class="sxs-lookup"><span data-stu-id="a778e-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a778e-147">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a778e-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a778e-148">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="a778e-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a778e-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a778e-149">Remarks</span></span>  
 <span data-ttu-id="a778e-150">Proces transformace zprávu do pořadí bajtů kódování je.</span><span class="sxs-lookup"><span data-stu-id="a778e-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="a778e-151">Dekódování je zpětné proces.</span><span class="sxs-lookup"><span data-stu-id="a778e-151">Decoding is the reverse process.</span></span> <span data-ttu-id="a778e-152">Windows Communication Foundation (WCF) zahrnuje tři typy kódování pro protokolu SOAP zprávy: Text, Binary a zpráva přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="a778e-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="a778e-153">Kódování textu reprezentována `textMessageEncoding` element je interaktivní, ale alespoň efektivní kodéru zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="a778e-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="a778e-154">Kodér textu vytvoří textové zprávy v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="a778e-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="a778e-155">Zprávy vyprodukované tento kodér jsou vhodné pro WS-* na základě zprostředkovatel komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="a778e-155">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="a778e-156">Webová služba nebo klient webové služby lze obecně pochopit textovou XML.</span><span class="sxs-lookup"><span data-stu-id="a778e-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="a778e-157">Přenos velkých bloků binárních dat jako text se ale alespoň efektivní metodu pro kódování zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="a778e-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a778e-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="a778e-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="a778e-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="a778e-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="a778e-160">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="a778e-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="a778e-161">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="a778e-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="a778e-162">Vazby</span><span class="sxs-lookup"><span data-stu-id="a778e-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a778e-163">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="a778e-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a778e-164">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a778e-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a778e-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a778e-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
