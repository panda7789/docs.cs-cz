---
title: <extensions>section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855356"
---
# <a name="extensions-section"></a><span data-ttu-id="7cae5-102">\<oddíl rozšíření ></span><span class="sxs-lookup"><span data-stu-id="7cae5-102">\<extensions> section</span></span>
<span data-ttu-id="7cae5-103">Tento oddíl konfigurace obsahuje kolekci rozšíření, která umožňují uživateli vytvořit uživatelsky definované vazby, chování a další aspekty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="7cae5-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="7cae5-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7cae5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7cae5-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7cae5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7cae5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> rozšíření**</span><span class="sxs-lookup"><span data-stu-id="7cae5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cae5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cae5-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cae5-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7cae5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7cae5-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7cae5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cae5-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7cae5-110">Attributes</span></span>  
 <span data-ttu-id="7cae5-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="7cae5-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7cae5-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7cae5-112">Child Elements</span></span>  
  
|<span data-ttu-id="7cae5-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="7cae5-113">Element</span></span>|<span data-ttu-id="7cae5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7cae5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cae5-115">\<behaviorExtensions></span><span class="sxs-lookup"><span data-stu-id="7cae5-115">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="7cae5-116">Tato část obsahuje podřízené prvky, které určují rozšíření chování, které umožňuje uživateli přizpůsobit chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7cae5-116">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="7cae5-117">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="7cae5-117">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="7cae5-118">Tato část umožňuje použití vlastního prvku vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7cae5-118">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="7cae5-119">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="7cae5-119">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="7cae5-120">Tato část obsahuje podřízené prvky, které určují rozšíření vazby, které umožňuje uživateli přizpůsobit vazby.</span><span class="sxs-lookup"><span data-stu-id="7cae5-120">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="7cae5-121">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="7cae5-121">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="7cae5-122">Tato část obsahuje podřízené prvky, které registrují standardní koncové body.</span><span class="sxs-lookup"><span data-stu-id="7cae5-122">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7cae5-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7cae5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7cae5-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="7cae5-124">Element</span></span>|<span data-ttu-id="7cae5-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7cae5-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7cae5-126">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7cae5-126">system.ServiceModel</span></span>|<span data-ttu-id="7cae5-127">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="7cae5-127">The root element of all WCF configuration elements.</span></span>|
