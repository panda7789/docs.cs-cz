---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: bfd2147a8e772848fc98cab7a875a51bdb53b5cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941159"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="b14e2-101">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="b14e2-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="b14e2-102">Představuje kolekci elementů konfigurace, které identifikují typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="b14e2-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="b14e2-103">Dá se použít k přidání vlastních protokolů.</span><span class="sxs-lookup"><span data-stu-id="b14e2-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="b14e2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b14e2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b14e2-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="b14e2-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="b14e2-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="b14e2-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b14e2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b14e2-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b14e2-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b14e2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b14e2-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b14e2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b14e2-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b14e2-110">Attributes</span></span>  
  
|<span data-ttu-id="b14e2-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b14e2-111">Attribute</span></span>|<span data-ttu-id="b14e2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b14e2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b14e2-113">name</span><span class="sxs-lookup"><span data-stu-id="b14e2-113">name</span></span>|<span data-ttu-id="b14e2-114">Název přenosu</span><span class="sxs-lookup"><span data-stu-id="b14e2-114">The name of the transport</span></span>|  
|<span data-ttu-id="b14e2-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="b14e2-115">transportConfigurationType</span></span>|<span data-ttu-id="b14e2-116">Typ, který implementuje přenos</span><span class="sxs-lookup"><span data-stu-id="b14e2-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b14e2-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b14e2-117">Child Elements</span></span>  
  
|<span data-ttu-id="b14e2-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="b14e2-118">Element</span></span>|<span data-ttu-id="b14e2-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b14e2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b14e2-120">\<add></span><span class="sxs-lookup"><span data-stu-id="b14e2-120">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="b14e2-121">Přidá prvek konfigurace, který identifikuje typ konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="b14e2-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b14e2-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b14e2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b14e2-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="b14e2-123">Element</span></span>|<span data-ttu-id="b14e2-124">Popis</span><span class="sxs-lookup"><span data-stu-id="b14e2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b14e2-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="b14e2-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="b14e2-126">Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="b14e2-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b14e2-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b14e2-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="b14e2-128">Hostování</span><span class="sxs-lookup"><span data-stu-id="b14e2-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
