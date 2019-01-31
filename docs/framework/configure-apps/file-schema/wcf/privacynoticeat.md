---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: b1de2a304a5dc4295497ea1f3b395240cb5ca9bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254910"
---
# <a name="privacynoticeat"></a><span data-ttu-id="2c9b8-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="2c9b8-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="2c9b8-102">Představuje prvek konfigurace, který určuje oznámení o ochraně osobních údajů používané `wsFederationHttp` vazby.</span><span class="sxs-lookup"><span data-stu-id="2c9b8-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="2c9b8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2c9b8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2c9b8-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="2c9b8-104">\<bindings></span></span>  
<span data-ttu-id="2c9b8-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2c9b8-105">\<customBinding></span></span>  
<span data-ttu-id="2c9b8-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2c9b8-106">\<binding></span></span>  
<span data-ttu-id="2c9b8-107">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="2c9b8-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c9b8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c9b8-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="2c9b8-109">Typ</span><span class="sxs-lookup"><span data-stu-id="2c9b8-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c9b8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2c9b8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2c9b8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2c9b8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c9b8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2c9b8-112">Attributes</span></span>  
  
|<span data-ttu-id="2c9b8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2c9b8-113">Attribute</span></span>|<span data-ttu-id="2c9b8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2c9b8-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="2c9b8-115">Řetězec určující identifikátor URI, ve kterém je umístěno oznámení soukromí.</span><span class="sxs-lookup"><span data-stu-id="2c9b8-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="2c9b8-116">Celé číslo, které určuje verzi tohoto oznámení o soukromí.</span><span class="sxs-lookup"><span data-stu-id="2c9b8-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c9b8-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2c9b8-117">Child Elements</span></span>  
 <span data-ttu-id="2c9b8-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="2c9b8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c9b8-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2c9b8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2c9b8-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c9b8-120">Element</span></span>|<span data-ttu-id="2c9b8-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2c9b8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c9b8-122">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2c9b8-122">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2c9b8-123">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="2c9b8-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c9b8-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c9b8-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2c9b8-125">Vazby</span><span class="sxs-lookup"><span data-stu-id="2c9b8-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="2c9b8-126">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="2c9b8-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2c9b8-127">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="2c9b8-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2c9b8-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2c9b8-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
