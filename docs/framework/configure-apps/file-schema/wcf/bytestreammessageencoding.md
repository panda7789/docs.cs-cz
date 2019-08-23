---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: b11f472c0e33003e50be4b45bb49196c64ecb70d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919722"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="959bb-101">\<byteStreamMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="959bb-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="959bb-102">Určuje kódování zprávy jako datový proud bajtů s možností určení kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="959bb-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="959bb-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="959bb-103">\<system.serviceModel></span></span>  
<span data-ttu-id="959bb-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="959bb-104">\<bindings></span></span>  
<span data-ttu-id="959bb-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="959bb-105">\<customBinding></span></span>  
<span data-ttu-id="959bb-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="959bb-106">\<binding></span></span>  
<span data-ttu-id="959bb-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="959bb-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="959bb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="959bb-108">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="959bb-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="959bb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="959bb-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="959bb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="959bb-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="959bb-111">Attributes</span></span>  
  
|<span data-ttu-id="959bb-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="959bb-112">Attribute</span></span>|<span data-ttu-id="959bb-113">Popis</span><span class="sxs-lookup"><span data-stu-id="959bb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="959bb-114">messageVersion</span><span class="sxs-lookup"><span data-stu-id="959bb-114">messageVersion</span></span>|<span data-ttu-id="959bb-115">Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="959bb-115">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="959bb-116">Tato vlastnost může být nastavena pouze na hodnotu <xref:System.ServiceModel.Channels.MessageVersion.None%2A>verze zprávy.</span><span class="sxs-lookup"><span data-stu-id="959bb-116">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="959bb-117">Kodér zpráv datového proudu bajtů nepodporuje žádné jiné verze zprávy.</span><span class="sxs-lookup"><span data-stu-id="959bb-117">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="959bb-118">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="959bb-118">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="959bb-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="959bb-119">Child Elements</span></span>  
  
|<span data-ttu-id="959bb-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="959bb-120">Element</span></span>|<span data-ttu-id="959bb-121">Popis</span><span class="sxs-lookup"><span data-stu-id="959bb-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="959bb-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="959bb-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="959bb-123">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="959bb-123">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="959bb-124">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="959bb-124">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="959bb-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="959bb-125">Parent Elements</span></span>  
  
|<span data-ttu-id="959bb-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="959bb-126">Element</span></span>|<span data-ttu-id="959bb-127">Popis</span><span class="sxs-lookup"><span data-stu-id="959bb-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="959bb-128">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="959bb-128">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="959bb-129">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="959bb-129">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="959bb-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="959bb-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="959bb-131">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="959bb-131">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="959bb-132">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="959bb-132">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="959bb-133">Vazby</span><span class="sxs-lookup"><span data-stu-id="959bb-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="959bb-134">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="959bb-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="959bb-135">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="959bb-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="959bb-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="959bb-136">\<customBinding></span></span>](custombinding.md)
