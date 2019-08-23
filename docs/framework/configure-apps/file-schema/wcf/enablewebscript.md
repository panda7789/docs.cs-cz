---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 123f58ee3d77bf605db21fa0d9537b3196d56468
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919118"
---
# <a name="enablewebscript"></a><span data-ttu-id="c6ebd-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="c6ebd-101">\<enableWebScript></span></span>
<span data-ttu-id="c6ebd-102">Tento prvek umožňuje chování koncového bodu, které umožňuje využívání služby z webových stránek ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="c6ebd-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="c6ebd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c6ebd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c6ebd-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="c6ebd-104">\<behaviors></span></span>  
<span data-ttu-id="c6ebd-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c6ebd-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="c6ebd-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="c6ebd-106">\<behavior></span></span>  
<span data-ttu-id="c6ebd-107">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="c6ebd-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ebd-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6ebd-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6ebd-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c6ebd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c6ebd-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c6ebd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6ebd-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c6ebd-111">Attributes</span></span>  
 <span data-ttu-id="c6ebd-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="c6ebd-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6ebd-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c6ebd-113">Child Elements</span></span>  
 <span data-ttu-id="c6ebd-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="c6ebd-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6ebd-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c6ebd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c6ebd-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6ebd-116">Element</span></span>|<span data-ttu-id="c6ebd-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c6ebd-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6ebd-118">\<> chování</span><span class="sxs-lookup"><span data-stu-id="c6ebd-118">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c6ebd-119">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c6ebd-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6ebd-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6ebd-120">Remarks</span></span>  
 <span data-ttu-id="c6ebd-121">Toto chování by se mělo použít pouze ve spojení s [ \<WebHttpBinding >](webhttpbinding.md) standardní [ \<](webmessageencoding.md) vazbou nebo prvkem vazby webMessageEncoding >.</span><span class="sxs-lookup"><span data-stu-id="c6ebd-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="c6ebd-122">Další informace o tomto chování najdete v tématu <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="c6ebd-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ebd-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6ebd-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="c6ebd-124">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="c6ebd-124">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="c6ebd-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="c6ebd-125">\<webHttp></span></span>](webhttp.md)
