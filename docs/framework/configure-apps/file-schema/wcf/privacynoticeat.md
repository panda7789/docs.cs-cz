---
title: '&lt;privacyNoticeAt&gt;'
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 104b2b6399ea31273045e43be716947db110715d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147314"
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="a8ab1-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="a8ab1-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="a8ab1-103">Představuje prvek konfigurace, který určuje oznámení o ochraně osobních údajů používané `wsFederationHttp` vazby.</span><span class="sxs-lookup"><span data-stu-id="a8ab1-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="a8ab1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a8ab1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a8ab1-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a8ab1-105">\<bindings></span></span>  
<span data-ttu-id="a8ab1-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="a8ab1-106">\<customBinding></span></span>  
<span data-ttu-id="a8ab1-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a8ab1-107">\<binding></span></span>  
<span data-ttu-id="a8ab1-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="a8ab1-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ab1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8ab1-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="a8ab1-110">Typ</span><span class="sxs-lookup"><span data-stu-id="a8ab1-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8ab1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a8ab1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a8ab1-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a8ab1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8ab1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a8ab1-113">Attributes</span></span>  
  
|<span data-ttu-id="a8ab1-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a8ab1-114">Attribute</span></span>|<span data-ttu-id="a8ab1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a8ab1-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="a8ab1-116">Řetězec určující identifikátor URI, ve kterém je umístěno oznámení soukromí.</span><span class="sxs-lookup"><span data-stu-id="a8ab1-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="a8ab1-117">Celé číslo, které určuje verzi tohoto oznámení o soukromí.</span><span class="sxs-lookup"><span data-stu-id="a8ab1-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8ab1-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a8ab1-118">Child Elements</span></span>  
 <span data-ttu-id="a8ab1-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="a8ab1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8ab1-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a8ab1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a8ab1-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a8ab1-121">Element</span></span>|<span data-ttu-id="a8ab1-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a8ab1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8ab1-123">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a8ab1-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a8ab1-124">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="a8ab1-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8ab1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8ab1-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a8ab1-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="a8ab1-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a8ab1-127">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="a8ab1-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a8ab1-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a8ab1-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a8ab1-129">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="a8ab1-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
