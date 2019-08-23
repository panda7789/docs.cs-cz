---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 65488c34931f6d7c424ece58a4855e746ea455bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936413"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="66842-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="66842-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="66842-102">Poskytuje prvek konfigurace pracovního postupu, který na úrovni služby stanovuje platnost přenosu, zprávy nebo původce.</span><span class="sxs-lookup"><span data-stu-id="66842-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="66842-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="66842-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="66842-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="66842-104">\<behaviors></span></span>  
<span data-ttu-id="66842-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="66842-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="66842-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="66842-106">\<behavior></span></span>  
<span data-ttu-id="66842-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="66842-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66842-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66842-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66842-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="66842-109">Attributes and Elements</span></span>  
 <span data-ttu-id="66842-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="66842-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66842-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="66842-111">Attributes</span></span>  
  
|<span data-ttu-id="66842-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="66842-112">Attribute</span></span>|<span data-ttu-id="66842-113">Popis</span><span class="sxs-lookup"><span data-stu-id="66842-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66842-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="66842-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="66842-115">Řetězec, který určuje typ zásad ověřování pro aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="66842-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66842-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="66842-116">Child Elements</span></span>  
 <span data-ttu-id="66842-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="66842-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66842-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="66842-118">Parent Elements</span></span>  
  
|<span data-ttu-id="66842-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="66842-119">Element</span></span>|<span data-ttu-id="66842-120">Popis</span><span class="sxs-lookup"><span data-stu-id="66842-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66842-121">\<> chování</span><span class="sxs-lookup"><span data-stu-id="66842-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="66842-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="66842-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66842-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66842-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
