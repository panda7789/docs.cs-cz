---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739060"
---
# \<byteStreamMessageEncoding>
<span data-ttu-id="f287e-101">Určuje kódování zprávy jako datový proud bajtů s možností určení kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="f287e-101">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="f287e-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f287e-102">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f287e-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f287e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f287e-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f287e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f287e-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="f287e-105">Attributes</span></span>  
  
|<span data-ttu-id="f287e-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="f287e-106">Attribute</span></span>|<span data-ttu-id="f287e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f287e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f287e-108">messageVersion</span><span class="sxs-lookup"><span data-stu-id="f287e-108">messageVersion</span></span>|<span data-ttu-id="f287e-109">Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="f287e-109">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="f287e-110">Tato vlastnost může být nastavena pouze na hodnotu verze zprávy <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="f287e-110">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="f287e-111">Kodér zpráv datového proudu bajtů nepodporuje žádné jiné verze zprávy.</span><span class="sxs-lookup"><span data-stu-id="f287e-111">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="f287e-112">Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="f287e-112">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f287e-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f287e-113">Child Elements</span></span>  
  
|<span data-ttu-id="f287e-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="f287e-114">Element</span></span>|<span data-ttu-id="f287e-115">Description</span><span class="sxs-lookup"><span data-stu-id="f287e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="f287e-116">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="f287e-116">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f287e-117">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="f287e-117">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f287e-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f287e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f287e-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f287e-119">Element</span></span>|<span data-ttu-id="f287e-120">Description</span><span class="sxs-lookup"><span data-stu-id="f287e-120">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f287e-121">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="f287e-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f287e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f287e-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="f287e-123">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="f287e-123">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="f287e-124">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="f287e-124">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="f287e-125">Vazby</span><span class="sxs-lookup"><span data-stu-id="f287e-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f287e-126">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="f287e-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f287e-127">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="f287e-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
