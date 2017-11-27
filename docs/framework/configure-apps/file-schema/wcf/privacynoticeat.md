---
title: '&lt;privacyNoticeAt&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 46a27dcc35c01d25391c9224d4967937b0a02d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="73458-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="73458-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="73458-103">Reprezentuje element konfigurace, který určuje oznámení o ochraně osobních údajů použít v `wsFederationHttp` vazby.</span><span class="sxs-lookup"><span data-stu-id="73458-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="73458-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="73458-104">\<system.serviceModel></span></span>  
<span data-ttu-id="73458-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="73458-105">\<bindings></span></span>  
<span data-ttu-id="73458-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="73458-106">\<customBinding></span></span>  
<span data-ttu-id="73458-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="73458-107">\<binding></span></span>  
<span data-ttu-id="73458-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="73458-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73458-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73458-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="73458-110">Typ</span><span class="sxs-lookup"><span data-stu-id="73458-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73458-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="73458-111">Attributes and Elements</span></span>  
 <span data-ttu-id="73458-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="73458-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73458-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="73458-113">Attributes</span></span>  
  
|<span data-ttu-id="73458-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="73458-114">Attribute</span></span>|<span data-ttu-id="73458-115">Popis</span><span class="sxs-lookup"><span data-stu-id="73458-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="73458-116">Řetězec, který určuje identifikátor URI, ve kterém se nachází v oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="73458-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="73458-117">Celé číslo, které určuje verzi toto prohlášení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="73458-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73458-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="73458-118">Child Elements</span></span>  
 <span data-ttu-id="73458-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="73458-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73458-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="73458-120">Parent Elements</span></span>  
  
|<span data-ttu-id="73458-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="73458-121">Element</span></span>|<span data-ttu-id="73458-122">Popis</span><span class="sxs-lookup"><span data-stu-id="73458-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73458-123">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="73458-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="73458-124">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="73458-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73458-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="73458-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="73458-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="73458-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="73458-127">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="73458-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="73458-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="73458-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="73458-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="73458-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
