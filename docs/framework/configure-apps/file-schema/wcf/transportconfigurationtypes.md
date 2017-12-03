---
title: '&lt;transportConfigurationTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa136f75fda4a87171a8ca3e369e7cb8621ac398
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="6caca-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="6caca-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="6caca-103">Představuje kolekci elementů konfigurace, které identifikují typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="6caca-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="6caca-104">Tímto lze přidat vlastní protokoly WAS.</span><span class="sxs-lookup"><span data-stu-id="6caca-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="6caca-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6caca-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6caca-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="6caca-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="6caca-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="6caca-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6caca-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6caca-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6caca-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6caca-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6caca-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6caca-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6caca-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6caca-111">Attributes</span></span>  
  
|<span data-ttu-id="6caca-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6caca-112">Attribute</span></span>|<span data-ttu-id="6caca-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6caca-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6caca-114">name</span><span class="sxs-lookup"><span data-stu-id="6caca-114">name</span></span>|<span data-ttu-id="6caca-115">Název přenosu</span><span class="sxs-lookup"><span data-stu-id="6caca-115">The name of the transport</span></span>|  
|<span data-ttu-id="6caca-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="6caca-116">transportConfigurationType</span></span>|<span data-ttu-id="6caca-117">Typ, který implementuje přenosu</span><span class="sxs-lookup"><span data-stu-id="6caca-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6caca-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6caca-118">Child Elements</span></span>  
  
|<span data-ttu-id="6caca-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="6caca-119">Element</span></span>|<span data-ttu-id="6caca-120">Popis</span><span class="sxs-lookup"><span data-stu-id="6caca-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6caca-121">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="6caca-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="6caca-122">Přidá prvek konfigurace, který vystihuje typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="6caca-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6caca-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6caca-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6caca-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="6caca-124">Element</span></span>|<span data-ttu-id="6caca-125">Popis</span><span class="sxs-lookup"><span data-stu-id="6caca-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6caca-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="6caca-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="6caca-127">Definuje typ, který vytvoří instanci služby hostování prostředí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="6caca-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6caca-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6caca-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="6caca-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="6caca-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
