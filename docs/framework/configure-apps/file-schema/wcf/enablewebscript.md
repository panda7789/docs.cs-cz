---
title: '&lt;enableWebScript&gt;'
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b14923c1b9a80bcd1c47db0e4fad6a6224b95329
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="95989-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="95989-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="95989-103">Tento element umožňuje chování koncového bodu, který vám umožní využívat službu z webových stránek ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="95989-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="95989-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="95989-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="95989-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="95989-105">\<behaviors></span></span>  
<span data-ttu-id="95989-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="95989-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="95989-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="95989-107">\<behavior></span></span>  
<span data-ttu-id="95989-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="95989-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95989-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95989-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95989-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="95989-110">Attributes and Elements</span></span>  
 <span data-ttu-id="95989-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="95989-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95989-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="95989-112">Attributes</span></span>  
 <span data-ttu-id="95989-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="95989-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="95989-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="95989-114">Child Elements</span></span>  
 <span data-ttu-id="95989-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="95989-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95989-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="95989-116">Parent Elements</span></span>  
  
|<span data-ttu-id="95989-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="95989-117">Element</span></span>|<span data-ttu-id="95989-118">Popis</span><span class="sxs-lookup"><span data-stu-id="95989-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95989-119">\<chování ></span><span class="sxs-lookup"><span data-stu-id="95989-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="95989-120">Určuje sadu chování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="95989-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95989-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95989-121">Remarks</span></span>  
 <span data-ttu-id="95989-122">Toto chování musí být použit pouze ve spojení s buď [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazba, nebo [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="95989-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="95989-123">Další informace o toto chování najdete v tématu <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="95989-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95989-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="95989-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="95989-125">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="95989-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="95989-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="95989-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
