---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400390"
---
# <a name="enablewebscript"></a><span data-ttu-id="740a5-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="740a5-101">\<enableWebScript></span></span>
<span data-ttu-id="740a5-102">Tento prvek umožňuje chování koncového bodu, které umožňuje využívání služby z webových stránek ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="740a5-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
<span data-ttu-id="740a5-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="740a5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="740a5-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="740a5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="740a5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="740a5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="740a5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="740a5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="740a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="740a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="740a5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<enableWebScript >**</span><span class="sxs-lookup"><span data-stu-id="740a5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="740a5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="740a5-109">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="740a5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="740a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="740a5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="740a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="740a5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="740a5-112">Attributes</span></span>  
 <span data-ttu-id="740a5-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="740a5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="740a5-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="740a5-114">Child Elements</span></span>  
 <span data-ttu-id="740a5-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="740a5-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="740a5-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="740a5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="740a5-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="740a5-117">Element</span></span>|<span data-ttu-id="740a5-118">Popis</span><span class="sxs-lookup"><span data-stu-id="740a5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="740a5-119">\<> chování</span><span class="sxs-lookup"><span data-stu-id="740a5-119">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="740a5-120">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="740a5-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="740a5-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="740a5-121">Remarks</span></span>  
 <span data-ttu-id="740a5-122">Toto chování by se mělo použít pouze ve spojení s [ \<WebHttpBinding >](webhttpbinding.md) standardní [ \<](webmessageencoding.md) vazbou nebo prvkem vazby webMessageEncoding >.</span><span class="sxs-lookup"><span data-stu-id="740a5-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="740a5-123">Další informace o tomto chování najdete v tématu <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="740a5-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="740a5-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="740a5-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="740a5-125">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="740a5-125">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="740a5-126">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="740a5-126">\<webHttp></span></span>](webhttp.md)
