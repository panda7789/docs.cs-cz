---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: afe0479d9cbf6d754b309c18e23d3a479870177c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739082"
---
# \<binaryMessageEncoding>
<span data-ttu-id="4a656-101">Definuje binární kodér zpráv, který kóduje Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="4a656-101">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="4a656-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a656-102">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a656-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4a656-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4a656-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4a656-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a656-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a656-105">Attributes</span></span>  
  
|<span data-ttu-id="4a656-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="4a656-106">Attribute</span></span>|<span data-ttu-id="4a656-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4a656-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a656-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4a656-108">maxReadPoolSize</span></span>|<span data-ttu-id="4a656-109">Celé číslo, které určuje, kolik zpráv lze současně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="4a656-109">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4a656-110">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="4a656-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4a656-111">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="4a656-111">The default is 64.</span></span>|  
|<span data-ttu-id="4a656-112">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="4a656-112">maxSessionSize</span></span>|<span data-ttu-id="4a656-113">Kladné celé číslo, které nastavuje velikost vyrovnávací paměti v bajtech použité pro kódování.</span><span class="sxs-lookup"><span data-stu-id="4a656-113">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="4a656-114">Větší vyrovnávací paměť zvyšuje rychlost kódování na náklady na velikost pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="4a656-114">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="4a656-115">Výchozí hodnota je 2048.</span><span class="sxs-lookup"><span data-stu-id="4a656-115">The default is 2048.</span></span>|  
|<span data-ttu-id="4a656-116">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4a656-116">maxWritePoolSize</span></span>|<span data-ttu-id="4a656-117">Celé číslo, které určuje, kolik zpráv lze odesílat souběžně bez přidělení nových zapisovačů.</span><span class="sxs-lookup"><span data-stu-id="4a656-117">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4a656-118">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="4a656-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4a656-119">Výchozí hodnota je 16.</span><span class="sxs-lookup"><span data-stu-id="4a656-119">The default is 16.</span></span>|  
|<span data-ttu-id="4a656-120">messageVersion</span><span class="sxs-lookup"><span data-stu-id="4a656-120">messageVersion</span></span>|<span data-ttu-id="4a656-121">Určuje zprávy SOAP a verze protokolu WS-Addressing, které se používají nebo očekávají.</span><span class="sxs-lookup"><span data-stu-id="4a656-121">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a656-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4a656-122">Child Elements</span></span>  
  
|<span data-ttu-id="4a656-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a656-123">Element</span></span>|<span data-ttu-id="4a656-124">Description</span><span class="sxs-lookup"><span data-stu-id="4a656-124">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="4a656-125">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="4a656-125">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4a656-126">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="4a656-126">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a656-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4a656-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4a656-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a656-128">Element</span></span>|<span data-ttu-id="4a656-129">Description</span><span class="sxs-lookup"><span data-stu-id="4a656-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="4a656-130">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="4a656-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a656-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a656-131">Remarks</span></span>  
 <span data-ttu-id="4a656-132">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="4a656-132">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4a656-133">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="4a656-133">Decoding is the reverse process.</span></span> <span data-ttu-id="4a656-134">Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: text, binární a mechanismus pro optimalizaci přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4a656-134">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4a656-135">`binaryMessageEncoding`Element určuje binární formát .NET pro XML a má možnosti pro zadání kódování znaků a verze SOAP a WS-Addressing, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="4a656-135">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="4a656-136">Kodér binární zprávy kóduje Windows Communication Foundation (WCF) v binárním souboru na lince.</span><span class="sxs-lookup"><span data-stu-id="4a656-136">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="4a656-137">I když toto kódování vede k velmi rychlému přenosu zpráv, vzájemná funkční spolupráce založená na standardech WS-\* bude ztracena.</span><span class="sxs-lookup"><span data-stu-id="4a656-137">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a656-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a656-138">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="4a656-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a656-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="4a656-140">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="4a656-140">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="4a656-141">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="4a656-141">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="4a656-142">Vazby</span><span class="sxs-lookup"><span data-stu-id="4a656-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4a656-143">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="4a656-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4a656-144">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4a656-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
