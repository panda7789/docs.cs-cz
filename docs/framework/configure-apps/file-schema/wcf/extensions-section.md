---
title: <extensions> Oddíl
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673001"
---
# <a name="extensions-section"></a><span data-ttu-id="4c563-102">\<Rozšíření > části</span><span class="sxs-lookup"><span data-stu-id="4c563-102">\<extensions> section</span></span>
<span data-ttu-id="4c563-103">Tento oddíl konfigurace obsahuje kolekci rozšíření, které umožňují uživateli vytvořit uživatelem definované vazby, chování a další aspekty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4c563-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="4c563-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4c563-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c563-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c563-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c563-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4c563-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4c563-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4c563-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c563-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="4c563-108">Attributes</span></span>  
 <span data-ttu-id="4c563-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="4c563-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4c563-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4c563-110">Child Elements</span></span>  
  
|<span data-ttu-id="4c563-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c563-111">Element</span></span>|<span data-ttu-id="4c563-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4c563-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c563-113">\<behaviorExtensions></span><span class="sxs-lookup"><span data-stu-id="4c563-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="4c563-114">Tato část obsahuje podřízené prvky, které určují chování rozšíření, které umožňují uživatelům přizpůsobit chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4c563-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="4c563-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="4c563-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="4c563-116">Tato část umožňuje používat vlastní prvek vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="4c563-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="4c563-117">\<bindingExtensions></span><span class="sxs-lookup"><span data-stu-id="4c563-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="4c563-118">Tato část obsahuje podřízené prvky, které určují rozšíření vazby, které umožňují uživateli upravit vazby.</span><span class="sxs-lookup"><span data-stu-id="4c563-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="4c563-119">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="4c563-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="4c563-120">Tato část obsahuje podřízené prvky, které se zaregistruje standardních koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="4c563-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c563-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4c563-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4c563-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c563-122">Element</span></span>|<span data-ttu-id="4c563-123">Popis</span><span class="sxs-lookup"><span data-stu-id="4c563-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c563-124">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4c563-124">system.ServiceModel</span></span>|<span data-ttu-id="4c563-125">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="4c563-125">The root element of all WCF configuration elements.</span></span>|
