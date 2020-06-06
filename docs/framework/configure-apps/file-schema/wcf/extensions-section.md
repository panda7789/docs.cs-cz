---
title: <extensions>section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855356"
---
# <a name="extensions-section"></a><span data-ttu-id="4d857-102">\<extensions>section</span><span class="sxs-lookup"><span data-stu-id="4d857-102">\<extensions> section</span></span>
<span data-ttu-id="4d857-103">Tento oddíl konfigurace obsahuje kolekci rozšíření, která umožňují uživateli vytvořit uživatelsky definované vazby, chování a další aspekty rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4d857-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="4d857-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d857-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d857-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4d857-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4d857-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4d857-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d857-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="4d857-107">Attributes</span></span>  
 <span data-ttu-id="4d857-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="4d857-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4d857-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d857-109">Child Elements</span></span>  
  
|<span data-ttu-id="4d857-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d857-110">Element</span></span>|<span data-ttu-id="4d857-111">Description</span><span class="sxs-lookup"><span data-stu-id="4d857-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="4d857-112">Tato část obsahuje podřízené prvky, které určují rozšíření chování, které umožňuje uživateli přizpůsobit chování služby nebo koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4d857-112">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="4d857-113">Tato část umožňuje použití vlastního prvku vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d857-113">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="4d857-114">Tato část obsahuje podřízené prvky, které určují rozšíření vazby, které umožňuje uživateli přizpůsobit vazby.</span><span class="sxs-lookup"><span data-stu-id="4d857-114">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="4d857-115">Tato část obsahuje podřízené prvky, které registrují standardní koncové body.</span><span class="sxs-lookup"><span data-stu-id="4d857-115">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d857-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4d857-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4d857-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d857-117">Element</span></span>|<span data-ttu-id="4d857-118">Description</span><span class="sxs-lookup"><span data-stu-id="4d857-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d857-119">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4d857-119">system.ServiceModel</span></span>|<span data-ttu-id="4d857-120">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4d857-120">The root element of all WCF configuration elements.</span></span>|
