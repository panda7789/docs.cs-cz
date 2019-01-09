---
title: Oddíl &lt;extensions&gt;
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 92dd3c528290344d9537c51fccf7c13c74c1984a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145312"
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="f417f-102">Oddíl &lt;extensions&gt;</span><span class="sxs-lookup"><span data-stu-id="f417f-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="f417f-103">Tento oddíl konfigurace obsahuje kolekci rozšíření, které umožňují uživateli vytvořit uživatelem definované vazby, chování a další aspekty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f417f-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="f417f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f417f-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f417f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f417f-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f417f-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f417f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f417f-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f417f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f417f-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="f417f-108">Attributes</span></span>  
 <span data-ttu-id="f417f-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="f417f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f417f-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f417f-110">Child Elements</span></span>  
  
|<span data-ttu-id="f417f-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="f417f-111">Element</span></span>|<span data-ttu-id="f417f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f417f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f417f-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="f417f-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="f417f-114">Tato část obsahuje podřízené prvky, které určují chování rozšíření, které umožňují uživatelům přizpůsobit chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f417f-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="f417f-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="f417f-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="f417f-116">Tato část umožňuje používat vlastní prvek vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f417f-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="f417f-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="f417f-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="f417f-118">Tato část obsahuje podřízené prvky, které určují rozšíření vazby, které umožňují uživateli upravit vazby.</span><span class="sxs-lookup"><span data-stu-id="f417f-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="f417f-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="f417f-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="f417f-120">Tato část obsahuje podřízené prvky, které se zaregistruje standardních koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f417f-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f417f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f417f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f417f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="f417f-122">Element</span></span>|<span data-ttu-id="f417f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f417f-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f417f-124">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f417f-124">system.ServiceModel</span></span>|<span data-ttu-id="f417f-125">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="f417f-125">The root element of all WCF configuration elements.</span></span>|
