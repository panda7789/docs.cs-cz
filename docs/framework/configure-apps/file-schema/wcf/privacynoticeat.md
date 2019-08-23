---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: f7349bf61082c5d8e5bd4249e01b8835a1861cb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934258"
---
# <a name="privacynoticeat"></a><span data-ttu-id="0c327-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="0c327-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="0c327-102">Představuje prvek konfigurace, který určuje oznámení o ochraně osobních údajů `wsFederationHttp` používané ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="0c327-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="0c327-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0c327-103">\<system.serviceModel></span></span>  
<span data-ttu-id="0c327-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="0c327-104">\<bindings></span></span>  
<span data-ttu-id="0c327-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0c327-105">\<customBinding></span></span>  
<span data-ttu-id="0c327-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="0c327-106">\<binding></span></span>  
<span data-ttu-id="0c327-107">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="0c327-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c327-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c327-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="0c327-109">type</span><span class="sxs-lookup"><span data-stu-id="0c327-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c327-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0c327-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c327-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0c327-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c327-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0c327-112">Attributes</span></span>  
  
|<span data-ttu-id="0c327-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0c327-113">Attribute</span></span>|<span data-ttu-id="0c327-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0c327-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="0c327-115">Řetězec určující identifikátor URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="0c327-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="0c327-116">Celé číslo, které určuje verzi tohoto oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="0c327-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c327-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0c327-117">Child Elements</span></span>  
 <span data-ttu-id="0c327-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="0c327-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c327-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0c327-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0c327-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="0c327-120">Element</span></span>|<span data-ttu-id="0c327-121">Popis</span><span class="sxs-lookup"><span data-stu-id="0c327-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c327-122">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="0c327-122">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="0c327-123">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="0c327-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c327-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c327-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0c327-125">Vazby</span><span class="sxs-lookup"><span data-stu-id="0c327-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0c327-126">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="0c327-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0c327-127">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="0c327-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="0c327-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0c327-128">\<customBinding></span></span>](custombinding.md)
