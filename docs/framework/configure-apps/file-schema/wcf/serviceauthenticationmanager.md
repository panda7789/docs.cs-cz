---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 7708dd8a572dd24c2852410b1781fce2807efab9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263482"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="df1a2-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="df1a2-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="df1a2-102">Poskytuje pracovní postup konfigurace element, který vytváří platnosti přenosu, původce nebo zpráv na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="df1a2-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="df1a2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="df1a2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="df1a2-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="df1a2-104">\<behaviors></span></span>  
<span data-ttu-id="df1a2-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="df1a2-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="df1a2-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="df1a2-106">\<behavior></span></span>  
<span data-ttu-id="df1a2-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="df1a2-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df1a2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df1a2-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df1a2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="df1a2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="df1a2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="df1a2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df1a2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="df1a2-111">Attributes</span></span>  
  
|<span data-ttu-id="df1a2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="df1a2-112">Attribute</span></span>|<span data-ttu-id="df1a2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="df1a2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df1a2-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="df1a2-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="df1a2-115">Řetězec, který určuje typ zásady ověřování pro aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="df1a2-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df1a2-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="df1a2-116">Child Elements</span></span>  
 <span data-ttu-id="df1a2-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="df1a2-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df1a2-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="df1a2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="df1a2-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="df1a2-119">Element</span></span>|<span data-ttu-id="df1a2-120">Popis</span><span class="sxs-lookup"><span data-stu-id="df1a2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df1a2-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="df1a2-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="df1a2-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="df1a2-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df1a2-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df1a2-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
