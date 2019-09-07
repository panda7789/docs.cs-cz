---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 624b52c0618362f48063c8f7e7c53c5a68d7de8f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400032"
---
# <a name="privacynoticeat"></a><span data-ttu-id="f771d-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="f771d-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="f771d-102">Představuje prvek konfigurace, který určuje oznámení o ochraně osobních údajů `wsFederationHttp` používané ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="f771d-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
<span data-ttu-id="f771d-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f771d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f771d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f771d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f771d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f771d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f771d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f771d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="f771d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="f771d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f771d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<privacyNotice >**</span><span class="sxs-lookup"><span data-stu-id="f771d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f771d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f771d-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="f771d-110">type</span><span class="sxs-lookup"><span data-stu-id="f771d-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f771d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f771d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f771d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f771d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f771d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f771d-113">Attributes</span></span>  
  
|<span data-ttu-id="f771d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="f771d-114">Attribute</span></span>|<span data-ttu-id="f771d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f771d-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="f771d-116">Řetězec určující identifikátor URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="f771d-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="f771d-117">Celé číslo, které určuje verzi tohoto oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="f771d-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f771d-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f771d-118">Child Elements</span></span>  
 <span data-ttu-id="f771d-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="f771d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f771d-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f771d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f771d-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f771d-121">Element</span></span>|<span data-ttu-id="f771d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="f771d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f771d-123">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="f771d-123">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="f771d-124">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="f771d-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f771d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f771d-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f771d-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="f771d-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f771d-127">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="f771d-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f771d-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="f771d-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f771d-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f771d-129">\<customBinding></span></span>](custombinding.md)
