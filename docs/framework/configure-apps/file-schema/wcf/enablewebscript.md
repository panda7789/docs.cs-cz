---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 9c9bbb9ccc7879510ae3e2bee2fabd604fd52f65
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266647"
---
# <a name="enablewebscript"></a><span data-ttu-id="59ca0-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="59ca0-101">\<enableWebScript></span></span>
<span data-ttu-id="59ca0-102">Tento prvek umožňuje chování koncového bodu, který umožňuje využívat služby z webových stránek ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="59ca0-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="59ca0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="59ca0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="59ca0-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="59ca0-104">\<behaviors></span></span>  
<span data-ttu-id="59ca0-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="59ca0-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="59ca0-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="59ca0-106">\<behavior></span></span>  
<span data-ttu-id="59ca0-107">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="59ca0-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ca0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59ca0-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59ca0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59ca0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="59ca0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59ca0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59ca0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="59ca0-111">Attributes</span></span>  
 <span data-ttu-id="59ca0-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="59ca0-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59ca0-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59ca0-113">Child Elements</span></span>  
 <span data-ttu-id="59ca0-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="59ca0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59ca0-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59ca0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="59ca0-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="59ca0-116">Element</span></span>|<span data-ttu-id="59ca0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="59ca0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59ca0-118">\<behavior></span><span class="sxs-lookup"><span data-stu-id="59ca0-118">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="59ca0-119">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="59ca0-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ca0-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59ca0-120">Remarks</span></span>  
 <span data-ttu-id="59ca0-121">Toto chování byste měli použít pouze ve spojení s buď [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazbu, nebo [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) element vazby.</span><span class="sxs-lookup"><span data-stu-id="59ca0-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="59ca0-122">Další informace o tomto chování najdete v tématu <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="59ca0-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ca0-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59ca0-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="59ca0-124">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="59ca0-124">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="59ca0-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="59ca0-125">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
