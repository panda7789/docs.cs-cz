---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 422de17f4c1b42579eadc16c7ec1a0037903d1a9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766943"
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="5ccd9-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="5ccd9-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="5ccd9-103">Představuje kolekci elementů konfigurace, které identifikují typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="5ccd9-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="5ccd9-104">Tímto lze přidat vlastní protokoly WAS.</span><span class="sxs-lookup"><span data-stu-id="5ccd9-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="5ccd9-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ccd9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ccd9-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="5ccd9-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="5ccd9-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="5ccd9-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ccd9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ccd9-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ccd9-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ccd9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5ccd9-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ccd9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ccd9-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ccd9-111">Attributes</span></span>  
  
|<span data-ttu-id="5ccd9-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="5ccd9-112">Attribute</span></span>|<span data-ttu-id="5ccd9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5ccd9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ccd9-114">name</span><span class="sxs-lookup"><span data-stu-id="5ccd9-114">name</span></span>|<span data-ttu-id="5ccd9-115">Název přenosu</span><span class="sxs-lookup"><span data-stu-id="5ccd9-115">The name of the transport</span></span>|  
|<span data-ttu-id="5ccd9-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="5ccd9-116">transportConfigurationType</span></span>|<span data-ttu-id="5ccd9-117">Typ, který implementuje přenosu</span><span class="sxs-lookup"><span data-stu-id="5ccd9-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ccd9-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ccd9-118">Child Elements</span></span>  
  
|<span data-ttu-id="5ccd9-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ccd9-119">Element</span></span>|<span data-ttu-id="5ccd9-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5ccd9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ccd9-121">\<add></span><span class="sxs-lookup"><span data-stu-id="5ccd9-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="5ccd9-122">Přidá prvek konfigurace, který vystihuje typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="5ccd9-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ccd9-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ccd9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5ccd9-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ccd9-124">Element</span></span>|<span data-ttu-id="5ccd9-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5ccd9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ccd9-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="5ccd9-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="5ccd9-127">Definuje typ, který vytvoří instanci služby hostování prostředí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="5ccd9-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ccd9-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ccd9-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="5ccd9-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="5ccd9-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
