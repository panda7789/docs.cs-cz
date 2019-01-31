---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: faad93554954accd341a1fc2262251fbda61910c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254532"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="c57af-101">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="c57af-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="c57af-102">Definuje kodér binárních zpráv, který binárně kóduje zprávy služby Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="c57af-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="c57af-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c57af-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c57af-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="c57af-104">\<bindings></span></span>  
<span data-ttu-id="c57af-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c57af-105">\<customBinding></span></span>  
<span data-ttu-id="c57af-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="c57af-106">\<binding></span></span>  
<span data-ttu-id="c57af-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="c57af-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c57af-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c57af-108">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c57af-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c57af-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c57af-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c57af-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c57af-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c57af-111">Attributes</span></span>  
  
|<span data-ttu-id="c57af-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="c57af-112">Attribute</span></span>|<span data-ttu-id="c57af-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c57af-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c57af-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="c57af-114">maxReadPoolSize</span></span>|<span data-ttu-id="c57af-115">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="c57af-115">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="c57af-116">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="c57af-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="c57af-117">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="c57af-117">The default is 64.</span></span>|  
|<span data-ttu-id="c57af-118">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="c57af-118">maxSessionSize</span></span>|<span data-ttu-id="c57af-119">Celé kladné číslo nastavující velikost v bajtech, použité pro kódování vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c57af-119">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="c57af-120">Větší vyrovnávací paměť zvyšuje kódování rychlost na úkor velikost pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="c57af-120">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="c57af-121">Výchozí hodnota je hodnotu 2048.</span><span class="sxs-lookup"><span data-stu-id="c57af-121">The default is 2048.</span></span>|  
|<span data-ttu-id="c57af-122">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="c57af-122">maxWritePoolSize</span></span>|<span data-ttu-id="c57af-123">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="c57af-123">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="c57af-124">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="c57af-124">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="c57af-125">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="c57af-125">The default is 16.</span></span>|  
|<span data-ttu-id="c57af-126">messageVersion</span><span class="sxs-lookup"><span data-stu-id="c57af-126">messageVersion</span></span>|<span data-ttu-id="c57af-127">Určuje zprávu protokolu SOAP a WS-Addressing verze, které jsou používány nebo očekávání.</span><span class="sxs-lookup"><span data-stu-id="c57af-127">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c57af-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c57af-128">Child Elements</span></span>  
  
|<span data-ttu-id="c57af-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="c57af-129">Element</span></span>|<span data-ttu-id="c57af-130">Popis</span><span class="sxs-lookup"><span data-stu-id="c57af-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c57af-131">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="c57af-131">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="c57af-132">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="c57af-132">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c57af-133">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="c57af-133">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c57af-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c57af-134">Parent Elements</span></span>  
  
|<span data-ttu-id="c57af-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="c57af-135">Element</span></span>|<span data-ttu-id="c57af-136">Popis</span><span class="sxs-lookup"><span data-stu-id="c57af-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c57af-137">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="c57af-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c57af-138">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="c57af-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c57af-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c57af-139">Remarks</span></span>  
 <span data-ttu-id="c57af-140">Kódování je proces transformace zprávu do sekvence bajtů.</span><span class="sxs-lookup"><span data-stu-id="c57af-140">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="c57af-141">Dekódování je opačný proces.</span><span class="sxs-lookup"><span data-stu-id="c57af-141">Decoding is the reverse process.</span></span> <span data-ttu-id="c57af-142">Windows Communication Foundation (WCF) zahrnuje tři typy kódování zprávy protokolu SOAP: Text, binární soubor a mechanismus optimalizaci přenosu zprávu (MTOM).</span><span class="sxs-lookup"><span data-stu-id="c57af-142">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="c57af-143">`binaryMessageEncoding` Prvek Určuje binární formát .NET pro XML a má možností určení kódování znaků a verze protokolu SOAP a WS-Addressing má být použit.</span><span class="sxs-lookup"><span data-stu-id="c57af-143">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="c57af-144">Kodér binárních zpráv kóduje zprávy služby Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="c57af-144">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="c57af-145">Když toto kódování má za následek velmi rychlé zpracování přenos zpráv, vzájemná funkční spolupráce podle WS-\* standardů se ztratí.</span><span class="sxs-lookup"><span data-stu-id="c57af-145">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c57af-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="c57af-146">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="c57af-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c57af-147">See also</span></span>
- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="c57af-148">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="c57af-148">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="c57af-149">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="c57af-149">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="c57af-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="c57af-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c57af-151">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="c57af-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c57af-152">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="c57af-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c57af-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c57af-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
