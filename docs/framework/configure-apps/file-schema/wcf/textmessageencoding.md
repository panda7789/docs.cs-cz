---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 640cf8fce766f7107e297143e061f4f60d9f263d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="b7fac-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="b7fac-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="b7fac-103">Určuje kódování znaků a zprávy Správa verzí slouží pro textové zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="b7fac-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="b7fac-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b7fac-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b7fac-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b7fac-105">\<bindings></span></span>  
<span data-ttu-id="b7fac-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b7fac-106">\<customBinding></span></span>  
<span data-ttu-id="b7fac-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="b7fac-107">\<binding></span></span>  
<span data-ttu-id="b7fac-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="b7fac-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fac-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7fac-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7fac-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b7fac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7fac-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b7fac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7fac-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b7fac-112">Attributes</span></span>  
  
|<span data-ttu-id="b7fac-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="b7fac-113">Attribute</span></span>|<span data-ttu-id="b7fac-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b7fac-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7fac-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="b7fac-115">maxReadPoolSize</span></span>|<span data-ttu-id="b7fac-116">Celé číslo, které určuje, kolik zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="b7fac-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="b7fac-117">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="b7fac-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b7fac-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="b7fac-118">The default is 64.</span></span>|  
|<span data-ttu-id="b7fac-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="b7fac-119">maxWritePoolSize</span></span>|<span data-ttu-id="b7fac-120">Celé číslo, které určuje, kolik zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="b7fac-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="b7fac-121">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="b7fac-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b7fac-122">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="b7fac-122">The default is 16.</span></span>|  
|<span data-ttu-id="b7fac-123">verze messageVersion</span><span class="sxs-lookup"><span data-stu-id="b7fac-123">messageVersion</span></span>|<span data-ttu-id="b7fac-124">Určuje verzi protokolu SOAP zprávy odeslané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="b7fac-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="b7fac-125">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="b7fac-125">Valid values are</span></span><br /><br /> <span data-ttu-id="b7fac-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="b7fac-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="b7fac-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="b7fac-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="b7fac-128">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="b7fac-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="b7fac-129">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="b7fac-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="b7fac-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="b7fac-130">writeEncoding</span></span>|<span data-ttu-id="b7fac-131">Určuje znakovou sadu kódování má být použit pro generování zpráv v rámci vazby.</span><span class="sxs-lookup"><span data-stu-id="b7fac-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b7fac-132">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="b7fac-132">Valid values are</span></span><br /><br /> <span data-ttu-id="b7fac-133">-UnicodeFffeTextEncoding: Unicode BigEndian kódování</span><span class="sxs-lookup"><span data-stu-id="b7fac-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="b7fac-134">-Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="b7fac-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="b7fac-135">-Utf8TextEncoding: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="b7fac-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b7fac-136">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="b7fac-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="b7fac-137">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b7fac-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7fac-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b7fac-138">Child Elements</span></span>  
  
|<span data-ttu-id="b7fac-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="b7fac-139">Element</span></span>|<span data-ttu-id="b7fac-140">Popis</span><span class="sxs-lookup"><span data-stu-id="b7fac-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7fac-141">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="b7fac-141">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="b7fac-142">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="b7fac-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b7fac-143">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b7fac-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7fac-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b7fac-144">Parent Elements</span></span>  
  
|<span data-ttu-id="b7fac-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="b7fac-145">Element</span></span>|<span data-ttu-id="b7fac-146">Popis</span><span class="sxs-lookup"><span data-stu-id="b7fac-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7fac-147">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="b7fac-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b7fac-148">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="b7fac-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7fac-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7fac-149">Remarks</span></span>  
 <span data-ttu-id="b7fac-150">Proces transformace zprávu do pořadí bajtů kódování je.</span><span class="sxs-lookup"><span data-stu-id="b7fac-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="b7fac-151">Dekódování je zpětné proces.</span><span class="sxs-lookup"><span data-stu-id="b7fac-151">Decoding is the reverse process.</span></span> <span data-ttu-id="b7fac-152">Windows Communication Foundation (WCF) zahrnuje tři typy kódování pro protokolu SOAP zprávy: Text, Binary a zpráva přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="b7fac-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="b7fac-153">Kódování textu reprezentována `textMessageEncoding` element je interaktivní, ale alespoň efektivní kodéru zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="b7fac-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="b7fac-154">Kodér textu vytvoří textové zprávy v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="b7fac-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="b7fac-155">Zprávy vyprodukované tento kodér jsou vhodné pro WS-\* na základě zprostředkovatel komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="b7fac-155">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="b7fac-156">Webová služba nebo klient webové služby lze obecně pochopit textovou XML.</span><span class="sxs-lookup"><span data-stu-id="b7fac-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="b7fac-157">Přenos velkých bloků binárních dat jako text se ale alespoň efektivní metodu pro kódování zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="b7fac-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7fac-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7fac-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7fac-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7fac-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="b7fac-160">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="b7fac-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="b7fac-161">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="b7fac-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="b7fac-162">Vazby</span><span class="sxs-lookup"><span data-stu-id="b7fac-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b7fac-163">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="b7fac-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b7fac-164">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="b7fac-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b7fac-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b7fac-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
