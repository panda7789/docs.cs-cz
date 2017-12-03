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
ms.openlocfilehash: 077878ae1746008532c3bee6b12913f98afc343f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="f89dc-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="f89dc-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="f89dc-103">Poskytuje prvek konfigurace pracovního postupu, který stanoví platnosti přenosu, původce nebo zpráv na úrovni služby...</span><span class="sxs-lookup"><span data-stu-id="f89dc-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="f89dc-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f89dc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f89dc-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f89dc-105">\<behaviors></span></span>  
<span data-ttu-id="f89dc-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f89dc-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f89dc-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f89dc-107">\<behavior></span></span>  
<span data-ttu-id="f89dc-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="f89dc-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f89dc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f89dc-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f89dc-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f89dc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f89dc-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f89dc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f89dc-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f89dc-112">Attributes</span></span>  
  
|<span data-ttu-id="f89dc-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f89dc-113">Attribute</span></span>|<span data-ttu-id="f89dc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f89dc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f89dc-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="f89dc-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="f89dc-116">Řetězec, který určuje typ zásady ověřování pro aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="f89dc-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f89dc-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f89dc-117">Child Elements</span></span>  
 <span data-ttu-id="f89dc-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="f89dc-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f89dc-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f89dc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f89dc-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="f89dc-120">Element</span></span>|<span data-ttu-id="f89dc-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f89dc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f89dc-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f89dc-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f89dc-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="f89dc-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f89dc-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f89dc-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
