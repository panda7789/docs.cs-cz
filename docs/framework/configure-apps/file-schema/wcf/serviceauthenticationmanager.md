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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2385b96460e0a3d53efb62054fb7da334ddd2d49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="2ecca-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="2ecca-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="2ecca-103">Poskytuje prvek konfigurace pracovního postupu, který stanoví platnosti přenosu, původce nebo zpráv na úrovni služby...</span><span class="sxs-lookup"><span data-stu-id="2ecca-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="2ecca-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2ecca-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2ecca-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2ecca-105">\<behaviors></span></span>  
<span data-ttu-id="2ecca-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2ecca-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2ecca-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2ecca-107">\<behavior></span></span>  
<span data-ttu-id="2ecca-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="2ecca-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ecca-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ecca-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ecca-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ecca-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2ecca-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ecca-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ecca-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ecca-112">Attributes</span></span>  
  
|<span data-ttu-id="2ecca-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2ecca-113">Attribute</span></span>|<span data-ttu-id="2ecca-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2ecca-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ecca-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="2ecca-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="2ecca-116">Řetězec, který určuje typ zásady ověřování pro aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="2ecca-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ecca-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ecca-117">Child Elements</span></span>  
 <span data-ttu-id="2ecca-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ecca-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ecca-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ecca-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2ecca-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ecca-120">Element</span></span>|<span data-ttu-id="2ecca-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2ecca-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ecca-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2ecca-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2ecca-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2ecca-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ecca-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ecca-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
