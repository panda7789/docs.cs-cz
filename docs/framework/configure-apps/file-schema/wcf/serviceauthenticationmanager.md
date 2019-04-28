---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 0940248364488bb38a329c5e461d72463c574e74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670375"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="c31ff-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="c31ff-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="c31ff-102">Poskytuje pracovní postup konfigurace element, který vytváří platnosti přenosu, původce nebo zpráv na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="c31ff-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="c31ff-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c31ff-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c31ff-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c31ff-104">\<behaviors></span></span>  
<span data-ttu-id="c31ff-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c31ff-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c31ff-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c31ff-106">\<behavior></span></span>  
<span data-ttu-id="c31ff-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="c31ff-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c31ff-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c31ff-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c31ff-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c31ff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c31ff-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c31ff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c31ff-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c31ff-111">Attributes</span></span>  
  
|<span data-ttu-id="c31ff-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="c31ff-112">Attribute</span></span>|<span data-ttu-id="c31ff-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c31ff-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c31ff-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="c31ff-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="c31ff-115">Řetězec, který určuje typ zásady ověřování pro aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="c31ff-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c31ff-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c31ff-116">Child Elements</span></span>  
 <span data-ttu-id="c31ff-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="c31ff-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c31ff-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c31ff-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c31ff-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="c31ff-119">Element</span></span>|<span data-ttu-id="c31ff-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c31ff-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c31ff-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c31ff-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c31ff-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="c31ff-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c31ff-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c31ff-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
