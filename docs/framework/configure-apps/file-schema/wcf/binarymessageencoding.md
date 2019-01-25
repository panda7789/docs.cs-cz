---
title: '&lt;binaryMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 7753340be01c407157d9a0576f31db4245c0b4f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672837"
---
# <a name="ltbinarymessageencodinggt"></a><span data-ttu-id="1b709-102">&lt;binaryMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="1b709-102">&lt;binaryMessageEncoding&gt;</span></span>
<span data-ttu-id="1b709-103">Definuje kodér binárních zpráv, který binárně kóduje zprávy služby Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="1b709-103">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="1b709-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1b709-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1b709-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="1b709-105">\<bindings></span></span>  
<span data-ttu-id="1b709-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1b709-106">\<customBinding></span></span>  
<span data-ttu-id="1b709-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="1b709-107">\<binding></span></span>  
<span data-ttu-id="1b709-108">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="1b709-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b709-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b709-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b709-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1b709-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1b709-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1b709-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b709-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1b709-112">Attributes</span></span>  
  
|<span data-ttu-id="1b709-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1b709-113">Attribute</span></span>|<span data-ttu-id="1b709-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1b709-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b709-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="1b709-115">maxReadPoolSize</span></span>|<span data-ttu-id="1b709-116">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="1b709-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="1b709-117">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="1b709-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="1b709-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="1b709-118">The default is 64.</span></span>|  
|<span data-ttu-id="1b709-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="1b709-119">maxSessionSize</span></span>|<span data-ttu-id="1b709-120">Celé kladné číslo nastavující velikost v bajtech, použité pro kódování vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1b709-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="1b709-121">Větší vyrovnávací paměť zvyšuje kódování rychlost na úkor velikost pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="1b709-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="1b709-122">Výchozí hodnota je hodnotu 2048.</span><span class="sxs-lookup"><span data-stu-id="1b709-122">The default is 2048.</span></span>|  
|<span data-ttu-id="1b709-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="1b709-123">maxWritePoolSize</span></span>|<span data-ttu-id="1b709-124">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="1b709-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="1b709-125">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="1b709-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="1b709-126">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="1b709-126">The default is 16.</span></span>|  
|<span data-ttu-id="1b709-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="1b709-127">messageVersion</span></span>|<span data-ttu-id="1b709-128">Určuje zprávu protokolu SOAP a WS-Addressing verze, které jsou používány nebo očekávání.</span><span class="sxs-lookup"><span data-stu-id="1b709-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b709-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1b709-129">Child Elements</span></span>  
  
|<span data-ttu-id="1b709-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b709-130">Element</span></span>|<span data-ttu-id="1b709-131">Popis</span><span class="sxs-lookup"><span data-stu-id="1b709-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b709-132">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="1b709-132">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="1b709-133">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="1b709-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1b709-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="1b709-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b709-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1b709-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1b709-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b709-136">Element</span></span>|<span data-ttu-id="1b709-137">Popis</span><span class="sxs-lookup"><span data-stu-id="1b709-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b709-138">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="1b709-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="1b709-139">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="1b709-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b709-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b709-140">Remarks</span></span>  
 <span data-ttu-id="1b709-141">Kódování je proces transformace zprávu do sekvence bajtů.</span><span class="sxs-lookup"><span data-stu-id="1b709-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="1b709-142">Dekódování je opačný proces.</span><span class="sxs-lookup"><span data-stu-id="1b709-142">Decoding is the reverse process.</span></span> <span data-ttu-id="1b709-143">Windows Communication Foundation (WCF) zahrnuje tři typy kódování zprávy protokolu SOAP: Text, binární soubor a mechanismus optimalizaci přenosu zprávu (MTOM).</span><span class="sxs-lookup"><span data-stu-id="1b709-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="1b709-144">`binaryMessageEncoding` Prvek Určuje binární formát .NET pro XML a má možností určení kódování znaků a verze protokolu SOAP a WS-Addressing má být použit.</span><span class="sxs-lookup"><span data-stu-id="1b709-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="1b709-145">Kodér binárních zpráv kóduje zprávy služby Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="1b709-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="1b709-146">Když toto kódování má za následek velmi rychlé zpracování přenos zpráv, vzájemná funkční spolupráce podle WS-\* standardů se ztratí.</span><span class="sxs-lookup"><span data-stu-id="1b709-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b709-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b709-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="1b709-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b709-148">See also</span></span>
- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="1b709-149">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="1b709-149">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="1b709-150">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="1b709-150">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="1b709-151">Vazby</span><span class="sxs-lookup"><span data-stu-id="1b709-151">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1b709-152">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="1b709-152">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1b709-153">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="1b709-153">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1b709-154">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1b709-154">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
