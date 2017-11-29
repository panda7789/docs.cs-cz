---
title: '&lt;enableWebScript&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfb6981947b457d5fdad59e96bdcd6937b9abd02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="bd2ef-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="bd2ef-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="bd2ef-103">Tento element umožňuje chování koncového bodu, který vám umožní využívat službu z webových stránek ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="bd2ef-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="bd2ef-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bd2ef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd2ef-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bd2ef-105">\<behaviors></span></span>  
<span data-ttu-id="bd2ef-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bd2ef-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="bd2ef-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bd2ef-107">\<behavior></span></span>  
<span data-ttu-id="bd2ef-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="bd2ef-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd2ef-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd2ef-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd2ef-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bd2ef-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd2ef-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bd2ef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd2ef-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="bd2ef-112">Attributes</span></span>  
 <span data-ttu-id="bd2ef-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="bd2ef-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bd2ef-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bd2ef-114">Child Elements</span></span>  
 <span data-ttu-id="bd2ef-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="bd2ef-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd2ef-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bd2ef-116">Parent Elements</span></span>  
  
|<span data-ttu-id="bd2ef-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="bd2ef-117">Element</span></span>|<span data-ttu-id="bd2ef-118">Popis</span><span class="sxs-lookup"><span data-stu-id="bd2ef-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd2ef-119">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bd2ef-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="bd2ef-120">Určuje sadu chování koncový bod.</span><span class="sxs-lookup"><span data-stu-id="bd2ef-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd2ef-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd2ef-121">Remarks</span></span>  
 <span data-ttu-id="bd2ef-122">Toto chování musí být použit pouze ve spojení s buď [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazba, nebo [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="bd2ef-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="bd2ef-123">Další informace o toto chování najdete v tématu <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="bd2ef-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd2ef-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd2ef-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="bd2ef-125">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="bd2ef-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="bd2ef-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="bd2ef-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
