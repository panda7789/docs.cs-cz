---
title: '&lt;serviceAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b46df4f069259ae4bb2d2769e20c6ad9e6090c00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="a582b-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="a582b-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="a582b-103">Poskytuje prvek konfigurace pracovního postupu, který stanoví platnosti přenosu, původce nebo zpráv na úrovni služby...</span><span class="sxs-lookup"><span data-stu-id="a582b-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="a582b-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a582b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a582b-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a582b-105">\<behaviors></span></span>  
<span data-ttu-id="a582b-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a582b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a582b-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a582b-107">\<behavior></span></span>  
<span data-ttu-id="a582b-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="a582b-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a582b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a582b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a582b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a582b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a582b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a582b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a582b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a582b-112">Attributes</span></span>  
  
|<span data-ttu-id="a582b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a582b-113">Attribute</span></span>|<span data-ttu-id="a582b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a582b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a582b-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="a582b-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="a582b-116">Řetězec, který určuje typ zásady ověřování pro aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="a582b-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a582b-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a582b-117">Child Elements</span></span>  
 <span data-ttu-id="a582b-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="a582b-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a582b-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a582b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a582b-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a582b-120">Element</span></span>|<span data-ttu-id="a582b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a582b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a582b-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a582b-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a582b-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="a582b-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a582b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a582b-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
