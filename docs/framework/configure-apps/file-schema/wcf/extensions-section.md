---
title: "Oddíl &lt;extensions&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a564b85609ca289f382789844d4e78252bb66482
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="4b5d3-102">Oddíl &lt;extensions&gt;</span><span class="sxs-lookup"><span data-stu-id="4b5d3-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="4b5d3-103">Tento konfigurační oddíl obsahuje kolekci rozšíření, která uživateli umožňuje vytvořit uživatelem definované vazby, chování a dalších aspektů rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4b5d3-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="4b5d3-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4b5d3-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b5d3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b5d3-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b5d3-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4b5d3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4b5d3-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4b5d3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b5d3-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="4b5d3-108">Attributes</span></span>  
 <span data-ttu-id="4b5d3-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="4b5d3-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4b5d3-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4b5d3-110">Child Elements</span></span>  
  
|<span data-ttu-id="4b5d3-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b5d3-111">Element</span></span>|<span data-ttu-id="4b5d3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4b5d3-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b5d3-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="4b5d3-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="4b5d3-114">Tato část obsahuje podřízené elementy, které určují chování rozšíření, která uživateli umožňuje přizpůsobit chování služba nebo koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4b5d3-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="4b5d3-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="4b5d3-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="4b5d3-116">Tato část umožňuje použití vlastní vazby element z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="4b5d3-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="4b5d3-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="4b5d3-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="4b5d3-118">Tato část obsahuje podřízené elementy, které určují vazby rozšíření, které umožňují uživateli upravit vazby.</span><span class="sxs-lookup"><span data-stu-id="4b5d3-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="4b5d3-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="4b5d3-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="4b5d3-120">Tato část obsahuje podřízené prvky, které zaregistruje standardní koncové body.</span><span class="sxs-lookup"><span data-stu-id="4b5d3-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b5d3-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b5d3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4b5d3-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b5d3-122">Element</span></span>|<span data-ttu-id="4b5d3-123">Popis</span><span class="sxs-lookup"><span data-stu-id="4b5d3-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b5d3-124">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4b5d3-124">system.ServiceModel</span></span>|<span data-ttu-id="4b5d3-125">Kořenový element všechny konfigurační prvky WCF.</span><span class="sxs-lookup"><span data-stu-id="4b5d3-125">The root element of all WCF configuration elements.</span></span>|
