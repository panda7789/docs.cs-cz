---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400390"
---
# \<enableWebScript>
<span data-ttu-id="c2773-101">Tento prvek umožňuje chování koncového bodu, které umožňuje využívání služby z webových stránek ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="c2773-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="c2773-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2773-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2773-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c2773-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c2773-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c2773-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2773-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="c2773-105">Attributes</span></span>  
 <span data-ttu-id="c2773-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2773-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c2773-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c2773-107">Child Elements</span></span>  
 <span data-ttu-id="c2773-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2773-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2773-109">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c2773-109">Parent Elements</span></span>  
  
|<span data-ttu-id="c2773-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2773-110">Element</span></span>|<span data-ttu-id="c2773-111">Description</span><span class="sxs-lookup"><span data-stu-id="c2773-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c2773-112">Určuje sadu chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c2773-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2773-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2773-113">Remarks</span></span>  
 <span data-ttu-id="c2773-114">Toto chování by se mělo použít pouze ve spojení se [\<webHttpBinding>](webhttpbinding.md) standardní vazbou nebo [\<webMessageEncoding>](webmessageencoding.md) prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="c2773-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="c2773-115">Další informace o tomto chování najdete v tématu <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> .</span><span class="sxs-lookup"><span data-stu-id="c2773-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2773-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2773-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="c2773-117">Integrace jazyka AJAX a podpora JSON</span><span class="sxs-lookup"><span data-stu-id="c2773-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
