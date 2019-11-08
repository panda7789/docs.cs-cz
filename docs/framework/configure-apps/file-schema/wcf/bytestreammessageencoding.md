---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739060"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="f0bad-101">\<byteStreamMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="f0bad-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="f0bad-102">Určuje kódování zprávy jako datový proud bajtů s možností určení kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="f0bad-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
<span data-ttu-id="f0bad-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f0bad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f0bad-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="f0bad-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f0bad-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f0bad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f0bad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f0bad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="f0bad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="f0bad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f0bad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<byteStreamMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="f0bad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0bad-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0bad-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0bad-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f0bad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f0bad-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f0bad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0bad-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f0bad-112">Attributes</span></span>  
  
|<span data-ttu-id="f0bad-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f0bad-113">Attribute</span></span>|<span data-ttu-id="f0bad-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f0bad-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0bad-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="f0bad-115">messageVersion</span></span>|<span data-ttu-id="f0bad-116">Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="f0bad-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="f0bad-117">Tato vlastnost může být nastavena pouze na hodnotu verze zprávy <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0bad-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="f0bad-118">Kodér zpráv datového proudu bajtů nepodporuje žádné jiné verze zprávy.</span><span class="sxs-lookup"><span data-stu-id="f0bad-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="f0bad-119">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="f0bad-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0bad-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f0bad-120">Child Elements</span></span>  
  
|<span data-ttu-id="f0bad-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f0bad-121">Element</span></span>|<span data-ttu-id="f0bad-122">Popis</span><span class="sxs-lookup"><span data-stu-id="f0bad-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0bad-123">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0bad-123">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="f0bad-124">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="f0bad-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f0bad-125">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f0bad-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0bad-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f0bad-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f0bad-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="f0bad-127">Element</span></span>|<span data-ttu-id="f0bad-128">Popis</span><span class="sxs-lookup"><span data-stu-id="f0bad-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0bad-129">vazba \<</span><span class="sxs-lookup"><span data-stu-id="f0bad-129">\<binding></span></span>](bindings.md)|<span data-ttu-id="f0bad-130">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="f0bad-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0bad-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0bad-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="f0bad-132">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="f0bad-132">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="f0bad-133">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="f0bad-133">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="f0bad-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="f0bad-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f0bad-135">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="f0bad-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f0bad-136">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="f0bad-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f0bad-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f0bad-137">\<customBinding></span></span>](custombinding.md)
