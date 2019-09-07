---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: feefd7fe73363b5fe1ec5658c5dc339c3d6bac57
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398213"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="30736-101">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="30736-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="30736-102">Definuje binární kodér zpráv, který kóduje Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="30736-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
<span data-ttu-id="30736-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="30736-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="30736-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="30736-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="30736-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="30736-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="30736-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="30736-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="30736-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="30736-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="30736-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<binaryMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="30736-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30736-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30736-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30736-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="30736-110">Attributes and Elements</span></span>  
 <span data-ttu-id="30736-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="30736-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30736-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="30736-112">Attributes</span></span>  
  
|<span data-ttu-id="30736-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="30736-113">Attribute</span></span>|<span data-ttu-id="30736-114">Popis</span><span class="sxs-lookup"><span data-stu-id="30736-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30736-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="30736-115">maxReadPoolSize</span></span>|<span data-ttu-id="30736-116">Celé číslo, které určuje, kolik zpráv lze současně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="30736-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="30736-117">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="30736-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="30736-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="30736-118">The default is 64.</span></span>|  
|<span data-ttu-id="30736-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="30736-119">maxSessionSize</span></span>|<span data-ttu-id="30736-120">Kladné celé číslo, které nastavuje velikost vyrovnávací paměti v bajtech použité pro kódování.</span><span class="sxs-lookup"><span data-stu-id="30736-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="30736-121">Větší vyrovnávací paměť zvyšuje rychlost kódování na náklady na velikost pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="30736-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="30736-122">Výchozí hodnota je 2048.</span><span class="sxs-lookup"><span data-stu-id="30736-122">The default is 2048.</span></span>|  
|<span data-ttu-id="30736-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="30736-123">maxWritePoolSize</span></span>|<span data-ttu-id="30736-124">Celé číslo, které určuje, kolik zpráv lze odesílat souběžně bez přidělení nových zapisovačů.</span><span class="sxs-lookup"><span data-stu-id="30736-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="30736-125">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="30736-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="30736-126">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="30736-126">The default is 16.</span></span>|  
|<span data-ttu-id="30736-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="30736-127">messageVersion</span></span>|<span data-ttu-id="30736-128">Určuje zprávy SOAP a verze protokolu WS-Addressing, které se používají nebo očekávají.</span><span class="sxs-lookup"><span data-stu-id="30736-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30736-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="30736-129">Child Elements</span></span>  
  
|<span data-ttu-id="30736-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="30736-130">Element</span></span>|<span data-ttu-id="30736-131">Popis</span><span class="sxs-lookup"><span data-stu-id="30736-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30736-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30736-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="30736-133">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="30736-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="30736-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="30736-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30736-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="30736-135">Parent Elements</span></span>  
  
|<span data-ttu-id="30736-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="30736-136">Element</span></span>|<span data-ttu-id="30736-137">Popis</span><span class="sxs-lookup"><span data-stu-id="30736-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30736-138">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="30736-138">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="30736-139">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="30736-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30736-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30736-140">Remarks</span></span>  
 <span data-ttu-id="30736-141">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="30736-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="30736-142">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="30736-142">Decoding is the reverse process.</span></span> <span data-ttu-id="30736-143">Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: Text, binární a mechanismus optimalizace přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="30736-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="30736-144">`binaryMessageEncoding` Element určuje binární formát .NET pro XML a má možnosti pro zadání kódování znaků a verze SOAP a WS-Addressing, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="30736-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="30736-145">Kodér binární zprávy kóduje Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="30736-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="30736-146">I když toto kódování vede k velmi rychlému přenosu zpráv, vzájemná funkční spolupráce založená na standardech WS-\* bude ztracena.</span><span class="sxs-lookup"><span data-stu-id="30736-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30736-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="30736-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="30736-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30736-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="30736-149">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="30736-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="30736-150">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="30736-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="30736-151">Vazby</span><span class="sxs-lookup"><span data-stu-id="30736-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="30736-152">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="30736-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="30736-153">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="30736-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="30736-154">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="30736-154">\<customBinding></span></span>](custombinding.md)
