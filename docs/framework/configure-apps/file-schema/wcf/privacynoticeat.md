---
title: '&lt;privacyNoticeAt&gt;'
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2914a3716b9e2adb6ebc47fd73ccee027a3b65da
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="09f1c-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="09f1c-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="09f1c-103">Reprezentuje element konfigurace, který určuje oznámení o ochraně osobních údajů použít v `wsFederationHttp` vazby.</span><span class="sxs-lookup"><span data-stu-id="09f1c-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="09f1c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="09f1c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="09f1c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="09f1c-105">\<bindings></span></span>  
<span data-ttu-id="09f1c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="09f1c-106">\<customBinding></span></span>  
<span data-ttu-id="09f1c-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="09f1c-107">\<binding></span></span>  
<span data-ttu-id="09f1c-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="09f1c-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09f1c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09f1c-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="09f1c-110">Typ</span><span class="sxs-lookup"><span data-stu-id="09f1c-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09f1c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="09f1c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="09f1c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="09f1c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09f1c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="09f1c-113">Attributes</span></span>  
  
|<span data-ttu-id="09f1c-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="09f1c-114">Attribute</span></span>|<span data-ttu-id="09f1c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="09f1c-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="09f1c-116">Řetězec, který určuje identifikátor URI, ve kterém se nachází v oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="09f1c-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="09f1c-117">Celé číslo, které určuje verzi toto prohlášení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="09f1c-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09f1c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="09f1c-118">Child Elements</span></span>  
 <span data-ttu-id="09f1c-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="09f1c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09f1c-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="09f1c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="09f1c-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="09f1c-121">Element</span></span>|<span data-ttu-id="09f1c-122">Popis</span><span class="sxs-lookup"><span data-stu-id="09f1c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09f1c-123">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="09f1c-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="09f1c-124">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="09f1c-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09f1c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="09f1c-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="09f1c-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="09f1c-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="09f1c-127">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="09f1c-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="09f1c-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="09f1c-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="09f1c-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="09f1c-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
