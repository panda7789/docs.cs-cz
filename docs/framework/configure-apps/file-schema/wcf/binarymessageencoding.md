---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 9b6b74200c807e6523ed3f7250945040bd12658d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919797"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="e8aca-101">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="e8aca-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="e8aca-102">Definuje binární kodér zpráv, který kóduje Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="e8aca-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="e8aca-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e8aca-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e8aca-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="e8aca-104">\<bindings></span></span>  
<span data-ttu-id="e8aca-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e8aca-105">\<customBinding></span></span>  
<span data-ttu-id="e8aca-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="e8aca-106">\<binding></span></span>  
<span data-ttu-id="e8aca-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="e8aca-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8aca-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8aca-108">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8aca-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e8aca-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e8aca-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e8aca-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8aca-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e8aca-111">Attributes</span></span>  
  
|<span data-ttu-id="e8aca-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e8aca-112">Attribute</span></span>|<span data-ttu-id="e8aca-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e8aca-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8aca-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="e8aca-114">maxReadPoolSize</span></span>|<span data-ttu-id="e8aca-115">Celé číslo, které určuje, kolik zpráv lze současně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="e8aca-115">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="e8aca-116">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="e8aca-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="e8aca-117">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="e8aca-117">The default is 64.</span></span>|  
|<span data-ttu-id="e8aca-118">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="e8aca-118">maxSessionSize</span></span>|<span data-ttu-id="e8aca-119">Kladné celé číslo, které nastavuje velikost vyrovnávací paměti v bajtech použité pro kódování.</span><span class="sxs-lookup"><span data-stu-id="e8aca-119">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="e8aca-120">Větší vyrovnávací paměť zvyšuje rychlost kódování na náklady na velikost pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="e8aca-120">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="e8aca-121">Výchozí hodnota je 2048.</span><span class="sxs-lookup"><span data-stu-id="e8aca-121">The default is 2048.</span></span>|  
|<span data-ttu-id="e8aca-122">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="e8aca-122">maxWritePoolSize</span></span>|<span data-ttu-id="e8aca-123">Celé číslo, které určuje, kolik zpráv lze odesílat souběžně bez přidělení nových zapisovačů.</span><span class="sxs-lookup"><span data-stu-id="e8aca-123">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="e8aca-124">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="e8aca-124">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="e8aca-125">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="e8aca-125">The default is 16.</span></span>|  
|<span data-ttu-id="e8aca-126">messageVersion</span><span class="sxs-lookup"><span data-stu-id="e8aca-126">messageVersion</span></span>|<span data-ttu-id="e8aca-127">Určuje zprávy SOAP a verze protokolu WS-Addressing, které se používají nebo očekávají.</span><span class="sxs-lookup"><span data-stu-id="e8aca-127">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8aca-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e8aca-128">Child Elements</span></span>  
  
|<span data-ttu-id="e8aca-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8aca-129">Element</span></span>|<span data-ttu-id="e8aca-130">Popis</span><span class="sxs-lookup"><span data-stu-id="e8aca-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8aca-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e8aca-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="e8aca-132">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="e8aca-132">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e8aca-133">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e8aca-133">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8aca-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e8aca-134">Parent Elements</span></span>  
  
|<span data-ttu-id="e8aca-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8aca-135">Element</span></span>|<span data-ttu-id="e8aca-136">Popis</span><span class="sxs-lookup"><span data-stu-id="e8aca-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8aca-137">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="e8aca-137">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e8aca-138">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="e8aca-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8aca-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8aca-139">Remarks</span></span>  
 <span data-ttu-id="e8aca-140">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="e8aca-140">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="e8aca-141">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="e8aca-141">Decoding is the reverse process.</span></span> <span data-ttu-id="e8aca-142">Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: Text, binární a mechanismus optimalizace přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="e8aca-142">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="e8aca-143">`binaryMessageEncoding` Element určuje binární formát .NET pro XML a má možnosti pro zadání kódování znaků a verze SOAP a WS-Addressing, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="e8aca-143">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="e8aca-144">Kodér binární zprávy kóduje Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="e8aca-144">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="e8aca-145">I když toto kódování vede k velmi rychlému přenosu zpráv, vzájemná funkční spolupráce založená na standardech WS-\* bude ztracena.</span><span class="sxs-lookup"><span data-stu-id="e8aca-145">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8aca-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8aca-146">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="e8aca-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8aca-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="e8aca-148">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="e8aca-148">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="e8aca-149">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="e8aca-149">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="e8aca-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="e8aca-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e8aca-151">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="e8aca-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e8aca-152">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="e8aca-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e8aca-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e8aca-153">\<customBinding></span></span>](custombinding.md)
