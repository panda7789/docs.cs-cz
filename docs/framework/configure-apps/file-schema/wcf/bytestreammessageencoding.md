---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 165bf4cd1c0c5c1a6adae91650d38984bc47ef6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="11fe0-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="11fe0-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="11fe0-103">Určuje zprávu, která kódování pomocí datového proudu bajtů, přičemž můžete určit kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="11fe0-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="11fe0-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="11fe0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="11fe0-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="11fe0-105">\<bindings></span></span>  
<span data-ttu-id="11fe0-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="11fe0-106">\<customBinding></span></span>  
<span data-ttu-id="11fe0-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="11fe0-107">\<binding></span></span>  
<span data-ttu-id="11fe0-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="11fe0-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11fe0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11fe0-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11fe0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11fe0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11fe0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11fe0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11fe0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="11fe0-112">Attributes</span></span>  
  
|<span data-ttu-id="11fe0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="11fe0-113">Attribute</span></span>|<span data-ttu-id="11fe0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="11fe0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11fe0-115">verze messageVersion</span><span class="sxs-lookup"><span data-stu-id="11fe0-115">messageVersion</span></span>|<span data-ttu-id="11fe0-116">Určuje verzi protokolu SOAP zprávy odeslané pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="11fe0-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="11fe0-117">Tuto vlastnost lze nastavit pouze na hodnotu verze zprávy <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="11fe0-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="11fe0-118">Kodér zpráv datového proudu bajtů nepodporuje žádné jiné verze zprávy.</span><span class="sxs-lookup"><span data-stu-id="11fe0-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="11fe0-119">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="11fe0-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11fe0-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11fe0-120">Child Elements</span></span>  
  
|<span data-ttu-id="11fe0-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="11fe0-121">Element</span></span>|<span data-ttu-id="11fe0-122">Popis</span><span class="sxs-lookup"><span data-stu-id="11fe0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11fe0-123">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="11fe0-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="11fe0-124">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="11fe0-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="11fe0-125">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="11fe0-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11fe0-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11fe0-126">Parent Elements</span></span>  
  
|<span data-ttu-id="11fe0-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="11fe0-127">Element</span></span>|<span data-ttu-id="11fe0-128">Popis</span><span class="sxs-lookup"><span data-stu-id="11fe0-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11fe0-129">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="11fe0-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="11fe0-130">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="11fe0-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11fe0-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="11fe0-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="11fe0-132">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="11fe0-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="11fe0-133">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="11fe0-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="11fe0-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="11fe0-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="11fe0-135">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="11fe0-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="11fe0-136">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="11fe0-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="11fe0-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="11fe0-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
