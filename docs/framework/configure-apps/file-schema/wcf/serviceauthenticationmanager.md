---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 3456ffa952372b014d579b5c420f7c44222fdad5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145351"
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="cd44b-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="cd44b-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="cd44b-103">Poskytuje pracovní postup konfigurace element, který vytváří platnosti přenosu, původce nebo zpráv na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="cd44b-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="cd44b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cd44b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cd44b-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="cd44b-105">\<behaviors></span></span>  
<span data-ttu-id="cd44b-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cd44b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cd44b-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="cd44b-107">\<behavior></span></span>  
<span data-ttu-id="cd44b-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="cd44b-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd44b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd44b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd44b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cd44b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cd44b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cd44b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd44b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cd44b-112">Attributes</span></span>  
  
|<span data-ttu-id="cd44b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="cd44b-113">Attribute</span></span>|<span data-ttu-id="cd44b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cd44b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd44b-115">Typ serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="cd44b-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="cd44b-116">Řetězec, který určuje typ zásady ověřování pro aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="cd44b-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd44b-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cd44b-117">Child Elements</span></span>  
 <span data-ttu-id="cd44b-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="cd44b-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd44b-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cd44b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cd44b-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="cd44b-120">Element</span></span>|<span data-ttu-id="cd44b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="cd44b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd44b-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="cd44b-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cd44b-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="cd44b-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd44b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd44b-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
