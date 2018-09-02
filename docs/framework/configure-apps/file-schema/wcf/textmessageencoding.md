---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e684c21c0b1360a9b270214ebe7b3ad00b42657f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417792"
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="4245a-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="4245a-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="4245a-103">Určuje kódování znaků a verzování zprávy použité pro textově založené zprávy XML.</span><span class="sxs-lookup"><span data-stu-id="4245a-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="4245a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4245a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4245a-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4245a-105">\<bindings></span></span>  
<span data-ttu-id="4245a-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="4245a-106">\<customBinding></span></span>  
<span data-ttu-id="4245a-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="4245a-107">\<binding></span></span>  
<span data-ttu-id="4245a-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="4245a-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4245a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4245a-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4245a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4245a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4245a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4245a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4245a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4245a-112">Attributes</span></span>  
  
|<span data-ttu-id="4245a-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4245a-113">Attribute</span></span>|<span data-ttu-id="4245a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4245a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4245a-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4245a-115">maxReadPoolSize</span></span>|<span data-ttu-id="4245a-116">Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="4245a-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4245a-117">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="4245a-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4245a-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="4245a-118">The default is 64.</span></span>|  
|<span data-ttu-id="4245a-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4245a-119">maxWritePoolSize</span></span>|<span data-ttu-id="4245a-120">Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="4245a-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4245a-121">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="4245a-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4245a-122">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="4245a-122">The default is 16.</span></span>|  
|<span data-ttu-id="4245a-123">verze messageVersion</span><span class="sxs-lookup"><span data-stu-id="4245a-123">messageVersion</span></span>|<span data-ttu-id="4245a-124">Určuje verzi protokolu SOAP zprávy odesílané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="4245a-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="4245a-125">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="4245a-125">Valid values are</span></span><br /><br /> <span data-ttu-id="4245a-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="4245a-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="4245a-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="4245a-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="4245a-128">Výchozí hodnota je Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="4245a-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="4245a-129">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="4245a-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="4245a-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="4245a-130">writeEncoding</span></span>|<span data-ttu-id="4245a-131">Určuje znakovou sadu kódování pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="4245a-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4245a-132">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="4245a-132">Valid values are</span></span><br /><br /> <span data-ttu-id="4245a-133">-UnicodeFffeTextEncoding: Kódování BigEndian kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="4245a-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="4245a-134">-Utf16TextEncoding: Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="4245a-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="4245a-135">-Utf8TextEncoding: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="4245a-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4245a-136">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="4245a-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="4245a-137">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4245a-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4245a-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4245a-138">Child Elements</span></span>  
  
|<span data-ttu-id="4245a-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="4245a-139">Element</span></span>|<span data-ttu-id="4245a-140">Popis</span><span class="sxs-lookup"><span data-stu-id="4245a-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4245a-141">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="4245a-141">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="4245a-142">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="4245a-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4245a-143">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4245a-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4245a-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4245a-144">Parent Elements</span></span>  
  
|<span data-ttu-id="4245a-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="4245a-145">Element</span></span>|<span data-ttu-id="4245a-146">Popis</span><span class="sxs-lookup"><span data-stu-id="4245a-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4245a-147">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="4245a-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4245a-148">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="4245a-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4245a-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4245a-149">Remarks</span></span>  
 <span data-ttu-id="4245a-150">Kódování je proces transformace zprávu do sekvence bajtů.</span><span class="sxs-lookup"><span data-stu-id="4245a-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4245a-151">Dekódování je opačný proces.</span><span class="sxs-lookup"><span data-stu-id="4245a-151">Decoding is the reverse process.</span></span> <span data-ttu-id="4245a-152">Windows Communication Foundation (WCF) zahrnuje tři typy kódování zprávy protokolu SOAP: Text, binární soubor a zpráv přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4245a-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4245a-153">Kódování textu reprezentována `textMessageEncoding` prvek je interaktivní, ale nejméně efektivní kodéru zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="4245a-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="4245a-154">Kodér textu vytvoří textových zpráv na lince.</span><span class="sxs-lookup"><span data-stu-id="4245a-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="4245a-155">Zprávy vytvořené v tomto kodéru jsou vhodné pro WS-\* na základě spolupráce.</span><span class="sxs-lookup"><span data-stu-id="4245a-155">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="4245a-156">Webová služba nebo klient webové služby obecně by rozuměla textové XML.</span><span class="sxs-lookup"><span data-stu-id="4245a-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="4245a-157">Přenášení velkých bloků binárních dat jako text je však nejméně efektivní způsob pro kódování zpráv XML.</span><span class="sxs-lookup"><span data-stu-id="4245a-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4245a-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="4245a-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="4245a-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="4245a-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="4245a-160">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="4245a-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="4245a-161">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="4245a-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="4245a-162">Vazby</span><span class="sxs-lookup"><span data-stu-id="4245a-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4245a-163">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="4245a-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="4245a-164">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4245a-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="4245a-165">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="4245a-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
