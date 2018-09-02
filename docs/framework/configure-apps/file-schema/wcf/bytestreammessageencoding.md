---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 4b031bfb0d0979dc99df13c104a712d6dd771e8a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422971"
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="11048-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="11048-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="11048-103">Určuje kódování zprávy formou datového proudu bajtů s možností určení kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="11048-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="11048-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="11048-104">\<system.serviceModel></span></span>  
<span data-ttu-id="11048-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="11048-105">\<bindings></span></span>  
<span data-ttu-id="11048-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="11048-106">\<customBinding></span></span>  
<span data-ttu-id="11048-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="11048-107">\<binding></span></span>  
<span data-ttu-id="11048-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="11048-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11048-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11048-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11048-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11048-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11048-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11048-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11048-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="11048-112">Attributes</span></span>  
  
|<span data-ttu-id="11048-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="11048-113">Attribute</span></span>|<span data-ttu-id="11048-114">Popis</span><span class="sxs-lookup"><span data-stu-id="11048-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11048-115">verze messageVersion</span><span class="sxs-lookup"><span data-stu-id="11048-115">messageVersion</span></span>|<span data-ttu-id="11048-116">Určuje verzi protokolu SOAP zprávy odesílané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="11048-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="11048-117">Tuto vlastnost lze nastavit pouze na hodnotu verze zprávy <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="11048-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="11048-118">Kodér zprávy datového proudu bajtů nepodporuje žádné jiné verze zpráv.</span><span class="sxs-lookup"><span data-stu-id="11048-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="11048-119">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="11048-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11048-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11048-120">Child Elements</span></span>  
  
|<span data-ttu-id="11048-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="11048-121">Element</span></span>|<span data-ttu-id="11048-122">Popis</span><span class="sxs-lookup"><span data-stu-id="11048-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11048-123">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="11048-123">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="11048-124">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="11048-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="11048-125">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="11048-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11048-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11048-126">Parent Elements</span></span>  
  
|<span data-ttu-id="11048-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="11048-127">Element</span></span>|<span data-ttu-id="11048-128">Popis</span><span class="sxs-lookup"><span data-stu-id="11048-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11048-129">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="11048-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="11048-130">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="11048-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11048-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="11048-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="11048-132">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="11048-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="11048-133">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="11048-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="11048-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="11048-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="11048-135">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="11048-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="11048-136">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="11048-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="11048-137">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="11048-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
