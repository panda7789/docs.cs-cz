---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: ce9f282ea1101befe3bf99762efa61e9b47b74cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109899"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="adc77-101">\<byteStreamMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="adc77-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="adc77-102">Určuje kódování zprávy formou datového proudu bajtů s možností určení kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="adc77-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="adc77-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="adc77-103">\<system.serviceModel></span></span>  
<span data-ttu-id="adc77-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="adc77-104">\<bindings></span></span>  
<span data-ttu-id="adc77-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="adc77-105">\<customBinding></span></span>  
<span data-ttu-id="adc77-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="adc77-106">\<binding></span></span>  
<span data-ttu-id="adc77-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="adc77-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc77-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adc77-108">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adc77-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="adc77-109">Attributes and Elements</span></span>  
 <span data-ttu-id="adc77-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="adc77-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adc77-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="adc77-111">Attributes</span></span>  
  
|<span data-ttu-id="adc77-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="adc77-112">Attribute</span></span>|<span data-ttu-id="adc77-113">Popis</span><span class="sxs-lookup"><span data-stu-id="adc77-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adc77-114">messageVersion</span><span class="sxs-lookup"><span data-stu-id="adc77-114">messageVersion</span></span>|<span data-ttu-id="adc77-115">Určuje verzi protokolu SOAP zprávy odesílané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="adc77-115">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="adc77-116">Tuto vlastnost lze nastavit pouze na hodnotu verze zprávy <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="adc77-116">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="adc77-117">Kodér zprávy datového proudu bajtů nepodporuje žádné jiné verze zpráv.</span><span class="sxs-lookup"><span data-stu-id="adc77-117">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="adc77-118">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="adc77-118">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adc77-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="adc77-119">Child Elements</span></span>  
  
|<span data-ttu-id="adc77-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="adc77-120">Element</span></span>|<span data-ttu-id="adc77-121">Popis</span><span class="sxs-lookup"><span data-stu-id="adc77-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adc77-122">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="adc77-122">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="adc77-123">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="adc77-123">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="adc77-124">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="adc77-124">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adc77-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="adc77-125">Parent Elements</span></span>  
  
|<span data-ttu-id="adc77-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="adc77-126">Element</span></span>|<span data-ttu-id="adc77-127">Popis</span><span class="sxs-lookup"><span data-stu-id="adc77-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adc77-128">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="adc77-128">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="adc77-129">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="adc77-129">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="adc77-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adc77-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="adc77-131">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="adc77-131">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="adc77-132">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="adc77-132">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="adc77-133">Vazby</span><span class="sxs-lookup"><span data-stu-id="adc77-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="adc77-134">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="adc77-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="adc77-135">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="adc77-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="adc77-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="adc77-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
