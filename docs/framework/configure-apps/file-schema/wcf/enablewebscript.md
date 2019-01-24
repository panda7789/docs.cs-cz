---
title: '&lt;enableWebScript&gt;'
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 1115b598776ca7d28698815974e06f3de57be598
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600099"
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="63299-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="63299-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="63299-103">Tento prvek umožňuje chování koncového bodu, který umožňuje využívat služby z webových stránek ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="63299-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="63299-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63299-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="63299-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="63299-105">\<behaviors></span></span>  
<span data-ttu-id="63299-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="63299-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="63299-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="63299-107">\<behavior></span></span>  
<span data-ttu-id="63299-108">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="63299-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63299-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63299-109">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63299-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="63299-110">Attributes and Elements</span></span>  
 <span data-ttu-id="63299-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="63299-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63299-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="63299-112">Attributes</span></span>  
 <span data-ttu-id="63299-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="63299-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63299-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="63299-114">Child Elements</span></span>  
 <span data-ttu-id="63299-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="63299-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63299-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="63299-116">Parent Elements</span></span>  
  
|<span data-ttu-id="63299-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="63299-117">Element</span></span>|<span data-ttu-id="63299-118">Popis</span><span class="sxs-lookup"><span data-stu-id="63299-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63299-119">\<behavior></span><span class="sxs-lookup"><span data-stu-id="63299-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="63299-120">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="63299-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63299-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63299-121">Remarks</span></span>  
 <span data-ttu-id="63299-122">Toto chování byste měli použít pouze ve spojení s buď [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazbu, nebo [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) element vazby.</span><span class="sxs-lookup"><span data-stu-id="63299-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="63299-123">Další informace o tomto chování najdete v tématu <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="63299-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63299-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63299-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="63299-125">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="63299-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="63299-126">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="63299-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
