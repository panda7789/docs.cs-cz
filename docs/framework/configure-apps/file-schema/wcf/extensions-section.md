---
title: <extensions>section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 4c8b5fe6eef1863ee3f02cb761a3aac61406e446
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918973"
---
# <a name="extensions-section"></a><span data-ttu-id="59e5f-102">\<oddíl rozšíření ></span><span class="sxs-lookup"><span data-stu-id="59e5f-102">\<extensions> section</span></span>
<span data-ttu-id="59e5f-103">Tento oddíl konfigurace obsahuje kolekci rozšíření, která umožňují uživateli vytvořit uživatelsky definované vazby, chování a další aspekty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="59e5f-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="59e5f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="59e5f-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59e5f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59e5f-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59e5f-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59e5f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="59e5f-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59e5f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59e5f-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="59e5f-108">Attributes</span></span>  
 <span data-ttu-id="59e5f-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="59e5f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59e5f-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59e5f-110">Child Elements</span></span>  
  
|<span data-ttu-id="59e5f-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="59e5f-111">Element</span></span>|<span data-ttu-id="59e5f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="59e5f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59e5f-113">\<behaviorExtensions></span><span class="sxs-lookup"><span data-stu-id="59e5f-113">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="59e5f-114">Tato část obsahuje podřízené prvky, které určují rozšíření chování, které umožňuje uživateli přizpůsobit chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="59e5f-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="59e5f-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="59e5f-115">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="59e5f-116">Tato část umožňuje použití vlastního prvku vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="59e5f-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="59e5f-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="59e5f-117">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="59e5f-118">Tato část obsahuje podřízené prvky, které určují rozšíření vazby, které umožňuje uživateli přizpůsobit vazby.</span><span class="sxs-lookup"><span data-stu-id="59e5f-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="59e5f-119">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="59e5f-119">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="59e5f-120">Tato část obsahuje podřízené prvky, které registrují standardní koncové body.</span><span class="sxs-lookup"><span data-stu-id="59e5f-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59e5f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59e5f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="59e5f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="59e5f-122">Element</span></span>|<span data-ttu-id="59e5f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="59e5f-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59e5f-124">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="59e5f-124">system.ServiceModel</span></span>|<span data-ttu-id="59e5f-125">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="59e5f-125">The root element of all WCF configuration elements.</span></span>|
