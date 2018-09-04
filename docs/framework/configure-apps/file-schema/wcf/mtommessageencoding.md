---
title: '&lt;mtomMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 380aa162d2bb55ac968bdd057a4bb45b2ea6abfe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43660687"
---
# <a name="ltmtommessageencodinggt"></a><span data-ttu-id="8c86e-102">&lt;mtomMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="8c86e-102">&lt;mtomMessageEncoding&gt;</span></span>
<span data-ttu-id="8c86e-103">Určuje kódování a správu verzí zpráv protokolu SOAP zprávy přenosu optimalizace mechanismus (MTOM) na základě zpráv.</span><span class="sxs-lookup"><span data-stu-id="8c86e-103">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="8c86e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8c86e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8c86e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="8c86e-105">\<bindings></span></span>  
<span data-ttu-id="8c86e-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="8c86e-106">\<customBinding></span></span>  
<span data-ttu-id="8c86e-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8c86e-107">\<binding></span></span>  
<span data-ttu-id="8c86e-108">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="8c86e-108">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c86e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c86e-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c86e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8c86e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8c86e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8c86e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c86e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="8c86e-112">Attributes</span></span>  
  
|<span data-ttu-id="8c86e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="8c86e-113">Attribute</span></span>|<span data-ttu-id="8c86e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8c86e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c86e-115">Třída maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="8c86e-115">maxBufferSize</span></span>|<span data-ttu-id="8c86e-116">Celé číslo, které určuje maximální velikost vyrovnávací paměti, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="8c86e-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="8c86e-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8c86e-117">maxReadPoolSize</span></span>|<span data-ttu-id="8c86e-118">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="8c86e-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="8c86e-119">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="8c86e-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8c86e-120">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="8c86e-120">The default is 64.</span></span>|  
|<span data-ttu-id="8c86e-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8c86e-121">maxWritePoolSize</span></span>|<span data-ttu-id="8c86e-122">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="8c86e-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="8c86e-123">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="8c86e-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8c86e-124">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="8c86e-124">The default is 16.</span></span>|  
|<span data-ttu-id="8c86e-125">verze messageVersion</span><span class="sxs-lookup"><span data-stu-id="8c86e-125">messageVersion</span></span>|<span data-ttu-id="8c86e-126">Určuje verzi protokolu SOAP zprávy odesílané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="8c86e-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="8c86e-127">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="8c86e-127">Valid values are</span></span><br /><br /> <span data-ttu-id="8c86e-128">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="8c86e-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="8c86e-129">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="8c86e-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="8c86e-130">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="8c86e-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="8c86e-131">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="8c86e-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="8c86e-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="8c86e-132">writeEncoding</span></span>|<span data-ttu-id="8c86e-133">Určuje znakovou sadu kódování pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="8c86e-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="8c86e-134">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="8c86e-134">Valid values are</span></span><br /><br /> <span data-ttu-id="8c86e-135">-UnicodeFffeTextEncoding: Kódování BigEndian kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="8c86e-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="8c86e-136">-Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="8c86e-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="8c86e-137">-Utf8TextEncoding: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="8c86e-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="8c86e-138">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="8c86e-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="8c86e-139">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="8c86e-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c86e-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8c86e-140">Child Elements</span></span>  
  
|<span data-ttu-id="8c86e-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c86e-141">Element</span></span>|<span data-ttu-id="8c86e-142">Popis</span><span class="sxs-lookup"><span data-stu-id="8c86e-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c86e-143">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="8c86e-143">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="8c86e-144">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="8c86e-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8c86e-145">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="8c86e-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c86e-146">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8c86e-146">Parent Elements</span></span>  
  
|<span data-ttu-id="8c86e-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c86e-147">Element</span></span>|<span data-ttu-id="8c86e-148">Popis</span><span class="sxs-lookup"><span data-stu-id="8c86e-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c86e-149">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8c86e-149">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8c86e-150">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="8c86e-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c86e-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c86e-151">Remarks</span></span>  
 <span data-ttu-id="8c86e-152">Kódování je proces transformace zprávu do sekvence bajtů.</span><span class="sxs-lookup"><span data-stu-id="8c86e-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="8c86e-153">Dekódování je opačný proces.</span><span class="sxs-lookup"><span data-stu-id="8c86e-153">Decoding is the reverse process.</span></span> <span data-ttu-id="8c86e-154">Windows Communication Foundation (WCF) zahrnuje tři typy kódování zprávy protokolu SOAP: Text, binární soubor a zpráv přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="8c86e-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="8c86e-155">`MtomMessageEncoding` Prvek určuje na znak kódování a správu verzí zpráv a další nastavení pro zprávy pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="8c86e-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="8c86e-156">MTOM je efektivní technologie pro přenos zpráv WCF binární data.</span><span class="sxs-lookup"><span data-stu-id="8c86e-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="8c86e-157">Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitu a vzájemná funkční spolupráce.</span><span class="sxs-lookup"><span data-stu-id="8c86e-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="8c86e-158">Kódování MTOM přenáší většina XML v textové formě, ale optimalizuje velkých bloků binárních dat jako ušetřený přenosem-je, bez převodu na jejich formát kódování base64.</span><span class="sxs-lookup"><span data-stu-id="8c86e-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c86e-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c86e-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c86e-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c86e-160">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [<span data-ttu-id="8c86e-161">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="8c86e-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="8c86e-162">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="8c86e-162">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="8c86e-163">Vazby</span><span class="sxs-lookup"><span data-stu-id="8c86e-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8c86e-164">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="8c86e-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="8c86e-165">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="8c86e-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8c86e-166">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="8c86e-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
