---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 92ae3dc10e0ae734a3113e22f175f4d010ca55b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541856"
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="fb7df-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="fb7df-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="fb7df-103">Určuje kódování zprávy formou datového proudu bajtů s možností určení kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="fb7df-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="fb7df-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fb7df-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fb7df-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="fb7df-105">\<bindings></span></span>  
<span data-ttu-id="fb7df-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fb7df-106">\<customBinding></span></span>  
<span data-ttu-id="fb7df-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="fb7df-107">\<binding></span></span>  
<span data-ttu-id="fb7df-108">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="fb7df-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb7df-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb7df-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb7df-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fb7df-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fb7df-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fb7df-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb7df-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="fb7df-112">Attributes</span></span>  
  
|<span data-ttu-id="fb7df-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="fb7df-113">Attribute</span></span>|<span data-ttu-id="fb7df-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fb7df-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb7df-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="fb7df-115">messageVersion</span></span>|<span data-ttu-id="fb7df-116">Určuje verzi protokolu SOAP zprávy odesílané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="fb7df-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="fb7df-117">Tuto vlastnost lze nastavit pouze na hodnotu verze zprávy <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="fb7df-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="fb7df-118">Kodér zprávy datového proudu bajtů nepodporuje žádné jiné verze zpráv.</span><span class="sxs-lookup"><span data-stu-id="fb7df-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="fb7df-119">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="fb7df-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb7df-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fb7df-120">Child Elements</span></span>  
  
|<span data-ttu-id="fb7df-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="fb7df-121">Element</span></span>|<span data-ttu-id="fb7df-122">Popis</span><span class="sxs-lookup"><span data-stu-id="fb7df-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb7df-123">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="fb7df-123">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="fb7df-124">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="fb7df-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="fb7df-125">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="fb7df-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb7df-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fb7df-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fb7df-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="fb7df-127">Element</span></span>|<span data-ttu-id="fb7df-128">Popis</span><span class="sxs-lookup"><span data-stu-id="fb7df-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb7df-129">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="fb7df-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="fb7df-130">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="fb7df-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb7df-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb7df-131">See also</span></span>
- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="fb7df-132">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="fb7df-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="fb7df-133">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="fb7df-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="fb7df-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="fb7df-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="fb7df-135">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="fb7df-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fb7df-136">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="fb7df-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="fb7df-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fb7df-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
