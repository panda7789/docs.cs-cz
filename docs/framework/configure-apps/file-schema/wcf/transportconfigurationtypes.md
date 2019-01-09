---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 5a51450d198ea395098f8a6a38d9104d0fe8538b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145468"
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="77d5f-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="77d5f-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="77d5f-103">Představuje kolekci elementů konfigurace, které určují typ konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="77d5f-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="77d5f-104">To umožňuje přidat vlastní protokoly WAS.</span><span class="sxs-lookup"><span data-stu-id="77d5f-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="77d5f-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="77d5f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="77d5f-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="77d5f-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="77d5f-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="77d5f-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d5f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77d5f-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77d5f-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="77d5f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="77d5f-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="77d5f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77d5f-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="77d5f-111">Attributes</span></span>  
  
|<span data-ttu-id="77d5f-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="77d5f-112">Attribute</span></span>|<span data-ttu-id="77d5f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="77d5f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77d5f-114">name</span><span class="sxs-lookup"><span data-stu-id="77d5f-114">name</span></span>|<span data-ttu-id="77d5f-115">Název přenosu</span><span class="sxs-lookup"><span data-stu-id="77d5f-115">The name of the transport</span></span>|  
|<span data-ttu-id="77d5f-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="77d5f-116">transportConfigurationType</span></span>|<span data-ttu-id="77d5f-117">Typ, který implementuje přenosu</span><span class="sxs-lookup"><span data-stu-id="77d5f-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77d5f-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="77d5f-118">Child Elements</span></span>  
  
|<span data-ttu-id="77d5f-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="77d5f-119">Element</span></span>|<span data-ttu-id="77d5f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="77d5f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77d5f-121">\<add></span><span class="sxs-lookup"><span data-stu-id="77d5f-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="77d5f-122">Přidá prvek konfigurace, který identifikuje typ konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="77d5f-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77d5f-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="77d5f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="77d5f-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="77d5f-124">Element</span></span>|<span data-ttu-id="77d5f-125">Popis</span><span class="sxs-lookup"><span data-stu-id="77d5f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77d5f-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="77d5f-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="77d5f-127">Definuje typ, který vytvoří instanci hostitelským prostředím služby pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="77d5f-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77d5f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="77d5f-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="77d5f-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="77d5f-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
