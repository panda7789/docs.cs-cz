---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 560da96c50e99461d25c1fd65def2dc10c284470
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261666"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="2389e-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="2389e-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="2389e-102">Představuje kolekci elementů konfigurace, které určují typ konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="2389e-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="2389e-103">To umožňuje přidat vlastní protokoly WAS.</span><span class="sxs-lookup"><span data-stu-id="2389e-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="2389e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2389e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2389e-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="2389e-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="2389e-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="2389e-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2389e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2389e-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2389e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2389e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2389e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2389e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2389e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2389e-110">Attributes</span></span>  
  
|<span data-ttu-id="2389e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2389e-111">Attribute</span></span>|<span data-ttu-id="2389e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2389e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2389e-113">name</span><span class="sxs-lookup"><span data-stu-id="2389e-113">name</span></span>|<span data-ttu-id="2389e-114">Název přenosu</span><span class="sxs-lookup"><span data-stu-id="2389e-114">The name of the transport</span></span>|  
|<span data-ttu-id="2389e-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="2389e-115">transportConfigurationType</span></span>|<span data-ttu-id="2389e-116">Typ, který implementuje přenosu</span><span class="sxs-lookup"><span data-stu-id="2389e-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2389e-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2389e-117">Child Elements</span></span>  
  
|<span data-ttu-id="2389e-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="2389e-118">Element</span></span>|<span data-ttu-id="2389e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2389e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2389e-120">\<add></span><span class="sxs-lookup"><span data-stu-id="2389e-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="2389e-121">Přidá prvek konfigurace, který identifikuje typ konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="2389e-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2389e-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2389e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2389e-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="2389e-123">Element</span></span>|<span data-ttu-id="2389e-124">Popis</span><span class="sxs-lookup"><span data-stu-id="2389e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2389e-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="2389e-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="2389e-126">Definuje typ, který vytvoří instanci hostitelským prostředím služby pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="2389e-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2389e-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2389e-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="2389e-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="2389e-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
